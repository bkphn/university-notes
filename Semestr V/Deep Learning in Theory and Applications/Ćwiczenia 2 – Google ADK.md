## Google's Agent Development Kit
**Google's Agent Development Kit** (Google ADK) to framework służący do budowania, ewaluacji i wdrażania inteligentnych agentów AI. W przeciwieństwie do samodzielnych modeli językowych zajmujących się jedynie generowaniem i predykcją tekstu, agenci potrafią korzystać z narzędzi, zapamiętywać kontekst oraz współpracować ze sobą. Pakiet ten ułatwia tworzenie systemów wieloagentowych (ang. *multi-agent orchestration*), gdzie zadania są przekazywane pomiędzy wyspecjalizowanymi jednostkami.

## Definiowanie agenta
Podstawowym elementem systemu w środowisku ADK jest klasa `LlmAgent`. Reprezentuje ona pojedynczego agenta opartego na architekturze LLM, który analizuje zapytania i decyduje o kolejnych krokach.

Przy jego definicji podajemy najważniejsze atrybuty:
- `name` – unikalna nazwa agenta w systemie.
- `model` – wskazanie konkretnego modelu, np. `gemini-3.1-flash-lite`.
- `description` – krótki opis ułatwiający innym agentom zrozumienie przeznaczenia danego modułu.
- `instruction` – instrukcja systemowa (ang. *system prompt*), określająca zachowanie agenta i zasady.

``` python
from google.adk.agents import LlmAgent

capital_agent = LlmAgent(
    name="capital_agent",
    model="gemini-3.1-flash-lite",
    description="Retrieves the capital city of a country...",
    instruction="You are an agent that provides the capital city...",
    tools=[get_capital_city],
    output_key="city"
)
```

## Wywoływanie funkcji
Podobnie jak podczas bezpośredniej komunikacji z API LLM, agenci zbudowani w ADK mogą wywoływać zdefiniowane wcześniej funkcje i korzystać z zewnętrznych narzędzi. Funkcja jest przekazywana w argumencie `tools`. Agent automatycznie decyduje, kiedy z niej skorzystać (tzw. *function call*), ekstrahuje niezbędne parametry z zapytania użytkownika, a uzyskany z niej wynik wykorzystuje do ostatecznej odpowiedzi.


## Strukturyzacja wyjścia
Jeśli proces wymaga zwrócenia ustrukturyzowanych danych zamiast zwykłego tekstu, stosuje się bibliotekę `pydantic`. Pozwala ona stworzyć schemat dziedziczący po `BaseModel`, który precyzuje listę zmiennych i ich opisy. Utworzony format przypisuje się do agenta za pomocą parametru `output_schema`.

``` python
from pydantic import BaseModel, Field
from typing import List

class Landmark(BaseModel):
    name: str = Field(description="Name of the landmark")
    description: str = Field(description="Description of the landmark")

class LandmarkList(BaseModel):
    landmarks: List[Landmark] = Field(description="List of landmarks")
```

## Koordynacja systemów wieloagentowych
Do realizacji skomplikowanych zadań wykorzystuje się **koordynatora**. Jest to oddzielny `LlmAgent`, któremu przekazuje się listę innych agentów w parametrze `sub_agents`. Koordynator nie wykonuje zadań bezpośrednio, ale funkcjonuje jako wirtualny pomost – analizuje intencję użytkownika i decyduje o przekazaniu sterowania.

``` python
coordinator_agent = LlmAgent(
    name="coordinator_agent",
    model="gemini-3.1-flash-lite",
    description="Co-ordinates the other agents",
    instruction="""
    You are a coordinator agent.
    Provide greetings or generic responses to user.
  
    1. Any specific question related to the capital of a country forward to `capital_agent`
    2. Any specific question related to landmarks of a city forward to `landmark_agent`
    3. When user wants to write a story about city or landmarks, call the following agents sequentially `capital_agent` -> `landmark_agent` -> `story_agent`.
  
    If capital or landmark are not given, do not introduce yourself ask the related subagent.
  
    Beside greetings and specific queries, do not respond to the user and just return "It's put of my scope".
    """,
    sub_agents=[capital_agent, landmark_agent, story_agent],
)
```
## Uruchamianie
Agent do działania potrzebuje środowiska wykonawczego. Kod wykorzystuje dwa główne elementy:
- **InMemorySessionService**: Służy do przechowywania historii konwersacji, stanu i metadanych bezpośrednio w pamięci podręcznej przypisanej do konkretnego `session_id` oraz `user_id`.
- **Runner**: Zarządza pełnym cyklem życia agentów oraz pozwala na asynchroniczne odpytywanie i streamowanie wyników (np. za pomocą zdarzeń, z których wyłuskiwane są wywołania funkcji lub finalny wygenerowany tekst).

``` python
APP_NAME = "story_teller"
USER_ID = "user_1"
SESSION_ID = "session_1"
  
session_service = InMemorySessionService()
  
session = await session_service.create_session(
    app_name=APP_NAME,
    user_id=USER_ID,
    session_id=SESSION_ID,
)
  
print("Session Created")
  
runner = Runner(
    agent=coordinator_agent,
    app_name=APP_NAME,
    session_service=session_service,
)
  
print("Runner Created")
```

```python
async def call_agent(query: str, runner: Runner, user_id: str, session_id: str) -> str:
    content = types.Content(
        role="user",
        parts=[types.Part(text=query)],
    )
  
    final_response_text = "Agent faced an issue and did not generate a response."
  
    async for event in runner.run_async(
        user_id=user_id,
        session_id=session_id,
        new_message=content,
    ):
        if event.content and event.content.parts:
            for i, part in enumerate(event.content.parts):
                if part.function_call:
                    print(f"Part {i} (Function Call): {part.function_call}")
                if part.text:
                    print(f"Part {i} (Text): {part.text}")
  
        if event.is_final_response():
            if event.content and event.content.parts:
                for part in event.content.parts:
                    if part.text:
                        final_response_text = part.text
                        break
            break
  
    return final_response_text
```

Końcowe wywołanie prezentuje się następująco:
``` python
user_prompt = "Write a short story about the capital of Poland."

final_response = await call_agent(user_prompt, runner, USER_ID, SESSION_ID)

print(final_response)
```