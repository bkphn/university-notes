## Tablice
Tablicą jednowymiarową nazywamy zbiór zmiennych określonego typu, uporządkowany według indeksu oznaczającego numer w zbiorze. Każda tablica ma zadeklarowany rozmiar, a więc wyznaczone miejsce w pamięci. Dla tablicy n-elementowej zmiennych typu `int`, zajęte zostanie dokładnie $n \cdot \mathtt{sizeof(int)}$. W trakcie działania programu, raz zadeklarowana wartość nie może ulec zmianie. 

Umiejscowienie tablicy w pamięci jest połączone ze wskaźnikiem, który wskazuje na jej początek. Każda tablica jest indeksowana od $0$ do $n-1$, a każdy numer nazywany jest indeksem. Tablice dwuwymiarowe to tablica tablic, co oznacza grupowanie jednego elementu typu w formie macierzy. Tablice dwuwymiarowe mają dwa indeksy. Raz zadeklarowany rozmiar tablicy nie może być zmieniony. Gdy istnieje konieczność zwiększenia rozmiaru tablicy możliwa jest relokacja pamięci.
## Stosy
Stosem nazywamy dynamiczną strukturę liniowo uporządkowanych danych, w której mamy dostęp jedynie do ostatniego elementu nazywanego **wierzchołkiem stosu**. Zapisywanie i pobieranie danych jest wykonywane za pomocą strategii **Last In - First Out** (LIFO). 

Stosy skojarzyć można ze stertą książek, z którą jedyne co możemy zrobić to położyć na szczycie nową książkę lub zdjąć jedną z góry. Wyróżniamy kilka operacji, za pomocą których możemy sprawdzić lub zmienić stan stosu:
* `isEmpty()` – Sprawdza czy stos jest pusty.
* `size()` – Zwraca ilość elementów w stosie.
* `isFull()` – Sprawdza czy stos jest pełen.
* `push(x)` – Dodaje element x na szczyt stosu.
* `pop()` – Zwraca element znajdujący się na szczycie stosu i go usuwa.
* `peek()` – Zwraca element na szczycie stosu (bez usuwania go).
## Kolejki
Kolejką nazywamy dynamiczną strukturę liniowo uporządkowanych danych, w której mamy dostęp do elementów na początku i na końcu. Możemy usuwać elementy z początku kolejki, a dodawać na końcu za pomocą strategii **First In - First Out** (FIFO).

Podobnie jak stos, kolejka ma pewną pojemność. Jednakże przepełnienie nie powoduje problemów – nadwymiarowy element jest wstawiany w miejsce najwcześniejszego. Poprawna implementacja kolejki powinna zawierać ostrzeżenie o przepełnieniu.

Implementacja tej struktury danych korzysta z buforu cyklicznego. Technicznie, taki bufor jest implementowany jako tablica z dwoma wskaźnikami lub zmiennymi indeksującymi. Pierwszy z indeksów nazywany jest indeksem odczytu, a drugi indeksem zapisu. W przypadku dostępu do danej zmiennej, odpowiedni indeks zwiększany jest o 1. Jeżeli indeks osiągnie maksimum, czyli wskaże na ostatni element, jest on przesuwany na miejsce pierwszego.

Implementacja kolejki w języku Python:
```python
class FIFO:
    def __init__(self, size):
        self.size = size
        self.t = [None for i in range(size)]
        self.top = -1
        self.head = -1
        self.tail = -1
```

Podobnie jak w przypadku stosu, kolejki również mają własne operacje:
* `isEmpty()` – Sprawdza czy kolejka jest pusta.
* `isFull()` – Sprawdza czy kolejka jest pełna.
* `enqueue()` – Dodaje nowy element na koniec kolejki, a jeżeli ta jest pełna to zwraca błąd.
* `dequeue()` – Usuwa element z kolejki, a jeżeli ta jest pusta to zwraca błąd.
* `peek()` – Zwraca element na początku kolejki (bez usuwania go).
* `size()` – Zwraca ilość elementów w kolejce.
## Kolejka priorytetowa
Kolejka priorytetowa zakłada, że każdy element ma swój priorytet, względem którego jest ustawiony. Im wyższy priorytet, tym bliżej początku kolejki. Każdy element posiada dodatkową wartość nazywaną kluczem. Klucz odpowiada za ważność tego elementu. Umiejscowienie danego elementu w kolejce zależy od klucza, a więc dodatkowo będzie potrzebny mechanizm przeszukiwania lub sortowania według kluczy. 

Kolejki priorytetowe powszechnie stosuje się w szeregowaniu procesów w jądrach systemowych bądź symulatorach. Rozpatrując dane w postaci bitów, operacje dodawania czy zwracania danego elementu będziemy mieli do czynienia ze złożonością $\mathcal{O}(\sqrt{\log_2 n})$.
## Listy
Listą nazywamy dynamiczną strukturę liniowo uporządkowanych danych, w której mamy dostęp do każdego z elementów, ponieważ każdemu rekordowi odpowiada pole zawierające adres kolejnego rekordu listy. Odnośnik do pierwszego rekordu nazywamy korzeniem listy, a wskaźnik ostatniego elementu jest pusty. Możemy wyróżnić następujące rodzaje list:
* **Listy jednokierunkowe**: Każdy element posiada wskaźnik do swojego następnika. Przeszukiwanie zaczyna się od korzenia i jest przeprowadzane w jednym kierunku.
* **Listy dwukierunkowe**: Każdy element posiada wskaźnik zarówno do swojego poprzednika, jak i następnika, co pozwala na przeprowadzanie przeszukiwania w obu kierunkach.
* **Listy cykliczne**: Pierwszy element listy jest następnikiem ostatniego, dzięki czemu tworzy się cykl. Listy cykliczne mogą być jednokierunkowe albo dwukierunkowe.
- **Listy z wartownikiem**: Lista, która zawiera dodatkowy element zwany wartownikiem, który jest niewidoczny dla programisty stosującego tę strukturę. Wspomniany obiekt występuje w pustej liście.

**Implementacja listy**:
Listę możemy zaimplementować na jeden z dwóch sposobów:
* **Implementacja tablicowa**: Konstrukcja opiera się na stworzeniu tablicy elementów i mechanizmie dodawania/usuwania elementu. Dodawanie elementów polega na wstawieniu go na koniec tablicy. W przypadku dodania elementu do środka należy przesunąć wszystkie elementy o jedno pole dalej i w powstałe miejsce wstawić nowy. W przypadku usuwania i-tego elementu, wszystkie na kolejnych pozycjach przesuwamy.
* **Implementacja wskaźnikowa**: Każdy element posiada wskaźnik do innego elementu zadanego typu. Jeśli dodawanie elementu jest na końcu listy wskaźnik z końca ustawia się na nowym elemencie. Jeśli dodawanie jest wewnątrz listy należy ustawić obiekt pod zadany wskaźnik. Usuwanie elementów polega na zastosowaniu tymczasowego elementu, wskazuje on na usuwany element, a wskaźnik poprzednika przemieszczamy do następnika. Po przesunięciu zwalniamy pamięć.
## Notacja Polska i Odwrotna Notacja Polska
Operandami nazywamy argumenty operatora, czyli elementy, na których wykonywane są działania (liczby, zmienne). Notacją **infiksową** nazywamy sposób notacji wyrażeń algebraicznych, w których operator umieszczamy pomiędzy operandami: $a+b$.

**Notacja Polska** (NP) jest notacją **prefiksową**, w której operator znajduje się przed operandami: $+ a\text{ }b$. W Notacji Polskiej nie stosuje się nawiasów, co jest rozwiązaniem upraszczającym obliczenia.

**Odwrotna Notacja Polska** (ONP) jest przeciwieństwem Notacji Polskiej, gdzie operator umieszczamy za operandami, jest to przykład notacji **postfiksowej**: $a\ b\ +$. Podobnie jak w NP, w ONP nie stosuje się nawiasów, co jest rozwiązaniem upraszczającym obliczenia. ONP możemy często spotkać w kompilatorach języków wyższego rzędu. ONP wykorzystuje stosy do przechowywania wyników pośrednich podczas obliczania wartości danego wyrażenia oraz do przechowywania nawiasów oraz operatorów podczas konwersji notacji infiksowej na postfiksową.

Implementacja konwersji w języku Python:
```python
def check_if_operator(char: str):
    d = {'+': (1, 1), '-': (2, 1), '*': (3, 2), '/': (2, 2), '^': (3, 3), '(': 0, ')': 4}
    is_operator = char in d
    return is_operator, 1 if not is_operator else d[char]

def convert_to_postfix(raw_expr: str):
    expr = raw_expr.strip('').split('')
    result = ""
    stack = []
    for symbol in expr:
        data = check_if_operator(symbol)
        if data[0]:
            if symbol == '(':
                stack.append((symbol, data[1]))
            elif symbol == ')':
                while len(stack) > 0 and stack[len(stack) - 1][0] != '(':
                    result += str(stack.pop()[0]) + ' '
                stack.pop()
            else:
                while len(stack) > 0 and stack[len(stack) - 1][1] > data[1]:
                    result += str(stack.pop()[0]) + ' '
                stack.append((symbol, data[1]))
        else:
            result += symbol + ' '
    while len(stack) > 0:
        result += str(stack.pop()[0]) + ' '
    return result.rstrip('')

def check_for_arguments_amount(char: str):
    d = {'+': 2, '-': 2, '*': 2, '/': 2, '^': 2}
    return d[char] if char in d else 0

def convert_to_infix(raw_expr: str):
    expr = raw_expr.strip('').split('')
    stack = []
    for symbol in expr:
        n = check_for_arguments_amount(symbol)
        if n == 0:
            stack.append(symbol)
        elif n == 2:
            x = stack.pop()
            y = stack.pop()
            stack.append(f"({y} {symbol} {x})")
    return stack[0]
```