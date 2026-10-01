## Duży Model Językowy
**Duży Model Językowy** (ang. *Large Language Model* ) LLM to zaawansowany system sztucznej inteligencji, najczęściej oparty na architekturze sieci neuronowych typu Transformer, wytrenowany na ogromnych zbiorach danych tekstowych w celu rozumienia, przetwarzania i generowania języka naturalnego.

Kluczowe mechanizmy i cechy:
- **Predykcja i modelowanie języka**: Fundamentalnym zadaniem tych modeli jest analiza kontekstu i statystyczne przewidywanie, jaka sekwencja słów, czy wręcz pojedynczy znak, powinna wystąpić jako następna.
- **Skala**: Termin *Large* odnosi się do dwóch aspektów. Po pierwsze, modele te posiadają od miliardów do setek miliardów parametrów wewnętrznych (połączeń w sieci neuronowej), które decydują o kształcie generowanych odpowiedzi. Po drugie, ich faza treningowa wymaga przetworzenia niemal całego tekstu dostępnego w publicznym internecie – od artykułów na Wikipedii, przez publikacje naukowe, aż po kod źródłowy.
- **Przetwarzanie Języka Naturalnego** (NLP): Dzięki treningowi na zróżnicowanych danych modele zyskały wszechstronność wykraczającą poza proste generowanie tekstu. Potrafią tłumaczyć języki, podsumowywać dokumenty, pisać kod programistyczny, a także przeprowadzać zaawansowane operacje logiczne.

## Interfejs Programowania Aplikacji
**Interfejs Programowania Aplikacji** (ang. *Application Programming Interface*) API to zestaw reguł, protokołów i narzędzi informatycznych, które umożliwiają różnym aplikacjom, systemom komputerowym lub komponentom oprogramowania wzajemną komunikację i wymianę danych.

API działa jako wirtualny pomost, który pozwala dwóm niezależnym systemom porozumiewać się ze sobą. Aplikacja wysyłająca żądanie nie musi rozumieć wewnętrznego kodu ani architektury systemu docelowego, z którym wchodzi w interakcję. Głównym celem API jest uproszczenie pracy programistów poprzez ukrycie złożoności wewnętrznej systemów. Zamiast pisać kod od podstaw dla każdej operacji (np. autoryzacji płatności, wyrenderowania mapy), deweloper korzysta z gotowego interfejsu, który zapewnia jednolity dostęp do zdefiniowanych procesów lub zasobów danych.

## Łączenie się z Google Gemini
Aby połączyć się z Google Gemini za pomocą API w Pythonie należy skorzystać z biblioteki `google.generativeai`, bądź jej nowszej wersji `google.genai`. Po wygenerowaniu klucza API przypisujemy go do zmiennej `api_key` i konfigurujemy nasz model.
``` python
import google.generativeai as genai

api_key = "[tu wstaw klucz API]"
genai.configure(api_key=api_key)
```
Możemy zdefiniować `system_prompt` i ustawić go jako instrukcję przy wyborze modelu.
``` python
system_prompt = "Respond in Polish"
model = genai.GenerativeModel("gemini-3.5-flash-lite", system_instruction=system_prompt)
```
Aby komunikować się z LLM-em przesyłamy mu `user_prompt` i tworzymy odpowiedź za pomocą `generate_content`.
```python
while True:
	user_prompt = input()
	if user_prompt == "quit":
		break
	
	response = model.generate_content(user_prompt, generation_config=genai.GenerationConfig(temperature = 2.0))

print(response.text)
```
Argument `temperature` odpowiada za oryginalność modelu. Dla `temperature = 0.0` model działa w pełni deterministycznie, co powoduje, że dostajemy za każdym razem tą samą odpowiedź. Im wyższa wartość argumentu `temperature` tym bardziej losowa będzie odpowiedź modelu.

## Dostosowywanie wyjścia
Przy komunikacji z modelem często przydatne jest zdefiniowanie szablonu wyjścia, możemy to zrobić za pomocą prompta:
``` python
  
user_prompt = """List a few popular cooking recipes.
  
Use this JSON schema:
Recipe = {'name': str, 'ingerdients': [str], 'instructions': [str]}
Return: list[Recipe]
"""

response = model.generate_content(user_prompt)

print(response.text)
```

Innym rozwiązaniem jest wykorzystanie biblioteki `pydantic`:
``` python
from pydantic import BaseModel

class Recipe(BaseModel):
    name: str
    ingredients: list[str]
    instructions: list[str]
  
response = client.models.generate_content(model="gemini-3.5-flash-lite", contents="List a few popular cooking recipes.",
config={"response_mime_type": "application/json",
"response_schema": list[Recipe],},)

print(response.text)
```

## Wywoływanie funkcji
Za pomocą LLM-ów możemy wywoływać zdefiniowane wcześniej funkcje. Poniżej przykład dla funkcji `set_light_values`, która przyjmuje argumenty `brightness` i `temperature`. W odróżnieniu do poprzednich przykładów korzystamy tutaj z nowszej biblioteki `google.genai`, zamiast `google.generativeai`.

``` python
from google import genai
from google.genai import types
  
client = genai.Client(api_key="[tu wstaw klucz API]")

def set_light_values(brightness: int, temperature: str):
    """Set the brightness and color temperature of a room light.

    Args:
        brightness: Light level from 0 to 100.
        temperature: Color temperatures of the light fixtures.
                     It can be 'daylight', 'cool' or 'warm'.

    Returns:
        A dictionary containing the set brightness and color temperature.
    """

    print(f"[function call] Setting light to brightness {brightness} and color temperature {temperature}.")
    return {"brightness": brightness, "temperature": temperature}

config = types.GenerateContentConfig(tools=[set_light_values],)
chat = client.chats.create(
    model="gemini-3.5-flash-lite",
    config=config)

response = chat.send_message("Make my room relaxing, you decide")

print(response.text)
```
