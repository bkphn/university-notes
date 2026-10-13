## Liczby całkowite
Literał `-314` reprezentuje ujemną liczbę całkowitą.

``` python
-314
```

`type()` zwraca typ obiektu; dla liczby całkowitej jest to `int`.

``` python
type(-314)
```

Liczby całkowite reprezentowane są przy pomocy 32 lub 64 bitów (`sys.maxsize`), jednakże przy przekroczeniu tego zakresu Python przechodzi na *bigint*:

`import sys` udostępnia moduł systemowy, a `sys.maxsize` pokazuje największy typowy indeks platformy, nie maksymalną wartość typu `int`.

``` python
import sys
sys.maxsize
```

Operator `**` wykonuje potęgowanie. Python obsługuje liczby całkowite o dowolnie dużej precyzji, ograniczonej dostępną pamięcią.

``` python
2**4140
```

## Systemy liczbowe
Prefiksy `0b`, `0o` i `0x` oznaczają odpowiednio zapis binarny, ósemkowy i szesnastkowy. Każdy literał ma typ `int`.

``` python
0b11, 0o37, 0x13A
```

## Metody `is_integer`
Metoda `float.is_integer()` sprawdza, czy wartość zmiennoprzecinkowa jest matematycznie całkowita.

``` python
(3.0).is_integer()
```

Dla `3.14` metoda `is_integer()` zwraca `False`, ponieważ liczba ma niezerową część ułamkową.

``` python
(3.14).is_integer()
```

**Liczby zmiennoprzecinkowe** są reprezentowane przy użyciu 64 bitów, co oznacza, że mają one pewne ograniczenia.

Literał `-3.14` jest liczbą zmiennoprzecinkową.

``` python
-3.14
```

`type()` pozwala sprawdzić, że literał dziesiętny ma typ `float`.

``` python
type(-3.14)
```

## Notacji naukowa
Litera `e` oznacza notację wykładniczą: `-0.0314e2` to `-0.0314 × 10²`.

``` python
-0.0314e2
```

## Liczby zespolone
Jednostkę urojoną zapisujemy w Pythonie jako `j` – wyrażenie ma typ zespolony.

``` python
1-1j
```

`type()` rozpoznaje liczbę zespoloną jako `complex`.

``` python
type(1-1j)
```

Można zamiast `j` użyć `J`:

W zapisie liczb zespolonych można używać zarówno małego `j`, jak i wielkiego `J`.

``` python
1-1J
```

Atrybut `.real` pobiera część rzeczywistą liczby zespolonej.

``` python
(1+2j).real
```

Atrybut `.imag` pobiera współczynnik części urojonej liczby zespolonej.

``` python
(1+2j).imag
```

## `conjugate`
Sprzężenie do liczby zespolonej

Metoda `.conjugate()` zwraca sprzężenie zespolone, czyli zmienia znak części urojonej.

``` python
(1+2j).conjugate()
```

`dir(complex)` pokazuje nazwy atrybutów i metod dostępnych dla liczb zespolonych.

``` python
dir(complex)
```

## Dodawanie i odejmowanie
Operatory `+` i `-` służą do dodawania i odejmowania; mieszanie `int` i `float` może dać wynik `float`.

``` python
314 + 3.14 - 31.4
```

Dodawanie i odejmowanie liczb zespolonych działa osobno na częściach rzeczywistych i urojonych.

``` python
(1 + 1j) - (1 - 1j)
```

## Mnożenie i dzielenie
Operator `*` mnoży liczby całkowite.

``` python
3 * 14
```

Mnożenie liczby całkowitej przez `float` daje zwykle wynik typu `float`.

``` python
3 * 14.0
```

Mnożenie liczb zespolonych uwzględnia tożsamość `j*j == -1`.

``` python
(1 + 1j) * (1 - 1j)
```

Operator `/` w Pythonie 3 wykonuje dzielenie rzeczywiste i zwraca `float` także dla dwóch `int`.

``` python
12 / 3
```

Dzielenie `/` nie obcina części ułamkowej.

``` python
14 / 3
```

Operator `/` obsługuje także dzielenie liczb zespolonych.

``` python
(1 + 1j) / (1 - 1j)
```

## Dzielenie całkowitoliczbowe
Operator `//` oblicza iloraz zaokrąglony w dół (dzielenie z podłogą).

``` python
14 // 3
```

`//` działa również dla `float`; wynik pozostaje typu `float`.

``` python
3 // 1.4
```

## Reszta z dzielenia
Operator `%` oblicza resztę z dzielenia.

``` python
14 % 3
```

Operator `%` działa również na liczbach zmiennoprzecinkowych; wynik może podlegać błędom reprezentacji.

``` python
3 % 1.4
```

## Potęgowanie
Operator `**` wykonuje potęgowanie.

``` python
2 ** 10
```

Potęgowanie ma wyższy priorytet niż jednoargumentowy minus: `-2 ** 10` to `-(2 ** 10)`.

``` python
-2 ** 10
```

Operator `**` pozwala także podnosić liczby zespolone do potęgi.

``` python
(1 + 1j) ** 2
```

W wynikiach (nie)odpowiednich działań arytmetycznych możemy uzyskać nieskończoność (`inf`) lub nie-liczby (`nan`). Te drugie otrzymujemy w przypadku symboli nieoznaczonych, tj. $\frac{0}{0},\ \frac{\pm\infty}{\pm\infty},\ 0 \cdot\ \infty,\ \infty - \infty$.

Bardzo duży literał zmiennoprzecinkowy może zostać reprezentowany jako `inf` (nieskończoność).

``` python
2.0e1000 * 10
```

Działania z `inf`, w szczególności `inf / inf`, mogą dać `nan` (wartość nieokreśloną).

``` python
2.0e1000 * 10 / 2.0e1000 * 10
```

Liczby zmiennoprzecinkowe są przechowywane przez komputer w notacji binarnej. Dlatego np. otrzymujemy:

`format(0.1, ".30f")` wyświetla 30 cyfr po przecinku, uwidaczniając przybliżenie binarnej reprezentacji `float`.

``` python
format(0.1, ".30f")
```

## Wartości logiczne
Wartości logiczne, czyli `True` i `False` otrzymujemy w wyniku testu.

`type(True)` identyfikuje typ logiczny `bool`.

``` python
type(True)
```

## Konwersja typów

Za pomocą funkcji `int()`, `float()`, `complex()` i `bool()` możemy jeden typ liczbowy przekształcić na drugi:

`int()` konwertuje `float` na liczbę całkowitą, obcinając część ułamkową w kierunku zera.

``` python
int(3.14)
```

`int("11", 2)` interpretuje tekst `11` jako liczbę zapisaną w systemie dwójkowym.

``` python
int("11", 2)
```

`float()` przekształca liczbę całkowitą na zmiennoprzecinkową.

``` python
float(314)
```

`complex(x)` tworzy liczbę zespoloną o części rzeczywistej `x` i zerowej części urojonej.

``` python
complex(3.14)
```

`complex(x, y)` tworzy liczbę `x + yj`.

``` python
complex(3.14, 2.71)
```

`bool(1)` zwraca `True`: niezerowe liczby są prawdziwe w kontekście logicznym.

``` python
bool(1)
```

`bool(0)` zwraca `False`.

``` python
bool(0)
```

`bool()` dla niezerowego `float` zwraca `True`.

``` python
bool(3.14)
```

## Ważne stałe matematyczne
W bibliotekach typu `math` czy `numpy` dostępne są inne ważne stałe matematyczne:

`import` ładuje moduły `math` i `numpy`; atrybut `.pi` udostępnia przybliżenie liczby $\pi$.

``` python
import math
import numpy
print(math.pi, numpy.pi)
```

Stała `.e` z `math` lub `numpy` jest przybliżeniem liczby Eulera $e$.

``` python
print(math.e, numpy.e)
```

## Zmienne
Python jest językiem dynamicznie typowanym, tzn. nie deklarujemy wcześnej tworzonych zmiennych. 

Zmienne tworzymy za pomocą operatora przypisania (`=`) i w każdym momencie możemy zmienić zarówno typ jak i wartość zmiennej.

Przypisanie `x = 2` wiąże nazwę `x` z obiektem typu `int`; `type(x)` bada jego typ.

``` python
x = 2
type(x)
```

Kolejne przypisanie `x = 3.14` wiąże tę samą nazwę z obiektem typu `float`.

``` python
x = 3.14
type(x)
```

Przypisanie wielokrotne `x, y = y, x` zamienia wartości bez ręcznego używania zmiennej tymczasowej.

``` python
x, y = y, x
print(x, y)
```

## Operatory łączone

Operatory `+=`, `/=` i `**=` aktualizują zmienne odpowiednio przez dodanie, podzielenie i potęgowanie.

``` python
x = 1
y = 2
z = 3
x += 1
y /= 2
z **= 2
print(x, y, z)
```

W Pythonie nie ma popularnego w innych językach programowania operatora inkrementacji `++` i dekrementacji `--`.

## Funkcje wbudowane
`abs()` zwraca wartość bezwzględną liczby rzeczywistej.

``` python
x = -3.14
print( abs(x) )
```

Dla liczby zespolonej `abs()` oblicza moduł (długość wektora na płaszczyźnie zespolonej).

``` python
x = 1 + 1j
print( abs(x) )
```

`round(x)` zaokrągla do najbliższej liczby całkowitej; szczegóły połówek zależą od reguły „do parzystej”.

``` python
x = 3.14
print( round(x) )
```

`round(x, 1)` zaokrągla do jednego miejsca po przecinku.

``` python
x = 3.14
print( round(x, 1) )
```

`min()` zwraca najmniejszy z podanych elementów.

``` python
min(5,4,6,2,0)
```

`max()` zwraca największy z podanych elementów.

``` python
max(5,4,6,2,0)
```

`sum()` dodaje elementy iterowalnej kolekcji, np. listy.

``` python
sum([1,2,3])
```

## Operatory relacyjne
Operatory relacyjne, czyli operatory służace do porównywania wartości danych obiektów:

Operator `==` sprawdza równość wartości, a nie tożsamość obiektów.

``` python
1 == 1
```

Operator `!=` sprawdza nierówność wartości.

``` python
1 != 1
```

Można również stosować tzw. łańcuchy relacji:

Zapis `1 < 2 < 3` sprawdza oba porównania w jednym łańcuchu.

``` python
1 < 2 < 3
```

Łańcuch porównań jest prawdziwy tylko wtedy, gdy wszystkie jego relacje są spełnione.

``` python
1 < 2 < 1
```

Istnieje również operator `is`, który sprawdza, czy dwa obiekty są identyczne:

Operator `is` testuje tożsamość obiektów; nie używa się go do porównywania wartości liczb (tu może pojawić się ostrzeżenie).

``` python
1 is 1
```

`is` odróżnia tożsamość od równości: `1` i `1.0` mogą być równe wartościowo, ale nie są tym samym obiektem.

``` python
1 is 1.0
```

`is not` sprawdza, czy wyrażenia wskazują różne obiekty.

``` python
1 is not 1.0
```

## Operatory logiczne
Operatory logiczne są w Pythonie rerezentowane poprzez `and` i `or`. Zaprzeczenie otrzymujemy za pomocą operatora `not`.

Operator `or` daje wynik logicznego „lub” i stosuje obliczanie skrócone.

``` python
True or 1 < 1
```

Operator `and` daje wynik logicznego „i” i stosuje obliczanie skrócone.

``` python
True and 1 < 1
```

Operator `not` neguje wartość logiczną warunku.

``` python
True and not 1 < 1
```

## Łańcuchy znaków
Łańcuchy tworzymy przy użyciu `" "` lub `' '`.

Ciąg znaków (`str`) można zapisać w cudzysłowie.

``` python
"ala ma pythona"
```

Cudzysłowy różnych rodzajów pozwalają umieścić apostrofy wewnątrz tekstu.

``` python
"ala ma pythona o imieniu 'Snakey'"
```

## Cięcie łańcucha
Wycinek `[0:3]` pobiera znaki od indeksu `0` do `2` (koniec jest wyłączny).

``` python
"ala ma pythona"[0:3]
```

Pominięty początek wycinka oznacza indeks `0`.

``` python
"ala ma pythona"[:3]
```

Ujemny indeks `-1` odnosi się do ostatniego znaku; `[:-1]` pomija go.

``` python
"ala ma pythona"[:-1]
```

Trzeci parametr wycinka wyznacza krok: `[: :2]` pobiera co drugi znak.

``` python
"ala ma pythona"[::2]
```

Napisy mogą byc również wielowierszowe - stosujemy wtedy `"""` lub `'''`. Takie napisy mogą zostać wykorzystane do tworzenia komentarzy blokowych.

Potrójne cudzysłowy umożliwiają tworzenie wielowierszowego napisu.

``` python
"""
ala
ma
pythona
"""
```

## Konkatenacja
Napisy łączymy ze sobą za pomocą operatora `+`:

Operator `+` skleja ciągi znaków w nowy napis.

``` python
"ala" + " ma " + "pythona"
```

Napisy można również mnożyć stosując operator $\ast$

Operator `*` powiela napis podaną liczbę razy.

``` python
"ala" * 3
```

Różne typy możemy przekształcić na napis za pomocą metody `str()`:

`str()` zwraca tekstową reprezentację podanej wartości.

``` python
str(3.14)
```

Napisy można ze soba porównywać za pomocą łańcucha relacyjnego w przyporządku leksykograficznym:

Porównania napisów są leksykograficzne, według wartości znaków Unicode.

``` python
"a" < "ab" < "b" < "ba" < "bb"
```

Przegląd operacji dostępnych dla napisów jest nastepujący:

`dir(str)` wyświetla dostępne atrybuty i metody klasy `str`.

``` python
dir(str)
```

`len()` zwraca długość napisu w znakach (punktach kodowych Unicode).

``` python
len("ala")
```
Metoda `.lower()` zwraca napis zamieniony na małe litery.

``` python
"Ala Ma Pythona".lower()
```

Metoda `.count()` zlicza niepokrywające się wystąpienia podciągu.

``` python
"ala i alan mają pythona".count('al')
```

`.split("ma")` dzieli napis w miejscach wystąpień podanego separatora.

``` python
"ala ma pythona \n ala".split("ma")
```

`.replace(stary, nowy)` tworzy napis z zastąpionymi fragmentami.

``` python
"ala ma pythona".replace("pythona", "kota")
```

## Formatowanie łańcuchów
Metoda `.format()` podstawia argumenty w pola `{}`.

``` python
"ala ma {} pythony i {} koty".format(2,3)
```

**F-string** `f" "` osadza wartości wyrażeń w napisie.

``` python
f"ala ma {2} pythony i {3} koty"
```

## Wyświetlanie i pobieranie danych
`print()` wypisuje tekst; samo użycie nazwy `lancuch` w notebooku wyświetla reprezentację wyniku ostatniego wyrażenia.

``` python
lancuch = "ala ma pythona"
print(lancuch)
lancuch
```

`input()` odczytuje tekst od użytkownika; `format()` wstawia odczytaną wartość do komunikatu.

``` python
imie = input()
print("Twoje imię to {}".format(imie))
```

## Instrukcje sterujące

### Warunek `if`
``` python
if warunek_1:
    # blok instrukcji 1
elif warunek_2:
    # blok instrukcji 2
elif warunek_3:
    # blok instrukcji 3
else:
    # blok instrukcji 4
```

Instrukcja `if` ... `else` wybiera blok na podstawie warunku

``` python
x = 1
if x // 2 * 2 == x:
    print("liczba parzysta")
else:
    print("liczba nieparzysta")
```

Jedno instrukcyjny blok `if` lub `else` można umieścić w tej samej linii po dwukropku.

``` python
x = 2
if x // 2 * 2 == x: print("liczba parzysta")
else: print("liczba nieparzysta")
```

Łańcuch `if` `elif` `else` wybiera pierwszy spełniony przedział godzinowy; `or` łączy warunki dla nocy.

``` python
godzina = 14
if 22 <= godzina <= 24 or 0 <= godzina < 6:
    print("noc")
elif 6 <= godzina < 12:
    print("rano")
elif godzina == 12:
    print("południe")
elif 12 < godzina <= 16:
    print("popołudnie")
elif 16 < godzina < 22:
    print("wieczór")
else:
    print("podałeś złą wartość")
```

## Pętla `while`
``` python
while warunek:
    # blok instrukcji
```

Pętla `while` powtarza instrukcje, dopóki warunek jest prawdziwy; `x += 1` zapobiega nieskończonemu powtarzaniu.

``` python
x = 1
while x < 9:
    print(x)
    x += 1
```

### Pętla `for`
```python
for obiekt in obiekt_iterowalny:
    # blok instrukcji
```

`range(5)` tworzy sekwencję wartości `0, 1, 2, 3, 4`, po której iteruje `for`.

``` python
for x in range(5):
    print(x)
```

`range(1, 5)` rozpoczyna zakres od `1`; wartość końcowa `5` jest wyłączona.

``` python
for x in range(1, 5):
    print(x)
```

`range(1, 5, 2)` używa kroku `2`.

``` python
for x in range(1, 5, 2):
    print(x)
```

Pętla `for` może przechodzić kolejno po znakach napisu.

``` python
for x in "ala ma pythona":
    print(x)
```

## Słowa kluczowe `break` i `continue`
`break` natychmiast kończy pętlę po napotkaniu pierwszej spacji.

``` python
for litera in 'ala ma pythona':     
    if litera == ' ':
        break
    print(litera)
```

`continue` pomija pozostałe instrukcje bieżącej iteracji, tutaj nie wypisuje litery `h`.

``` python
for litera in 'ala ma pythona':     
    if litera == 'h':
        continue
    print(litera)
```

## Listy
Lista `[ ]` może przechowywać elementy różnych typów; `print()` wypisuje jej zawartość.

``` python
lista_1 = [1, 2, 3, "ala", "ma"]
print(lista_1)
```

Pętla `for` iteruje bezpośrednio po elementach listy.

``` python
for i in lista_1:
    print(i)
```

## Metody związane z listami
`dir(list)` pozwala sprawdzić dostępne metody list.

``` python
dir(list)
```

Operator `+` łączy dwie listy, tworząc nową.

``` python
lista_1 = [1, 2, 3, "ala", "ma"]
lista_2 = ["pythona", "i", "kota"]

lista_3 = lista_1 + lista_2

print(lista_3)
```


Operator `*` powtarza elementy listy wskazaną liczbę razy.

``` python
lista_3 = lista_1 * 2
print(lista_3)
```

`.append()` dodaje pojedynczy element na końcu istniejącej listy.

``` python
lista_1.append("pythona")
print(lista_1)
```

`.remove()` usuwa pierwsze wystąpienie wskazanej wartości.

``` python
lista_1.remove(3)
print(lista_1)
```

`.insert(indeks, wartość)` wstawia element przed podaną pozycją.

``` python
lista_1.insert(2,3)
print(lista_1)
```

`.index(wartość)` zwraca indeks pierwszego wystąpienia elementu.

``` python
lista_1.index(3)
```

`.count(wartość)` zlicza wystąpienia elementu w liście.

``` python
lista_1.count(3)
```

`.pop(indeks)` usuwa i zwraca wskazany element, a `.pop()` usuwa ostatni.

``` python
lista_1.pop(2)
lista_1.pop()
print(lista_1)
```

`.sort()` sortuje listę w miejscu, domyślnie rosnąco.

``` python
lista_2 = [4, 3, 2, 1, 0]

lista_2.sort()
print(lista_2)
```

`.reverse()` odwraca kolejność elementów listy w miejscu.

``` python
lista_2.reverse()
print(lista_2)
```

`.extend()` dołącza elementy innej kolekcji do istniejącej listy.

``` python
lista_1.extend(lista_2)

print(lista_1)
```

`.copy()` tworzy płytką kopię listy (zagnieżdżone obiekty nie są kopiowane rekurencyjnie).

``` python
lista_3 = lista_2.copy()
print(lista_3)
```

## Krotka
W przeciwieństwie do listy krotki nie można modyfikować.

Krotka `( )` jest uporządkowaną, niemodyfikowalną sekwencją.

``` python
krotka_1 = (1, 2, 3, 'ala', 'ma')

print(krotka_1)
```

Indeksowanie `[3]` zwraca czwarty element krotki.

``` python
krotka_1[3]
```

Końcowy przecinek po pojedynczym elemencie tworzy krotkę jednoelementową.

``` python
krotka_2 = "ala",

print(krotka_2[0])
```

## Operacje na krotkach
Operator `+` tworzy nową krotkę przez konkatenację dwóch krotek.

``` python
krotka_1 = (1, 2, 3, 'ala', 'ma')
krotka_2 = ("pythona", "i", "kota")

krotka_3 = krotka_1 + krotka_2
print(krotka_3)
```

Operator `*` powiela elementy krotki.

``` python
krotka_3 = krotka_1 * 2

print(krotka_3)
```

Pętla `for` iteruje po elementach krotki.

``` python
for i in krotka_3:
    print(i)
```

`list(krotka)` tworzy listę z elementów krotki.

``` python
krotka = (1, 2, 3, 'ala', 'ma')
lista = list(krotka)

print(lista)
```

`tuple(lista)` tworzy krotkę z elementów listy.

``` python
lista = [1, 2, 3, 'ala', 'ma']
krotka = tuple(lista)

print(krotka)
```

`del` usuwa powiązania nazw; próba użycia usuniętej nazwy `lista` zgłosi `NameError`.

``` python
del lista
del krotka

print(lista)
```

## Słownik
Jest to zbiór par `klucz:wartość`, gdzie `klucz` musi być unikatowy.

Słownik `{klucz: wartość}` przechowuje pary; klucze muszą być unikalne.

``` python
slownik = {"Imię":"Ala", "Wiek":20}

print(slownik)
```

Indeksowanie słownika `slownik["Imię"]` pobiera wartość przypisaną wskazanemu kluczowi.

``` python
slownik["Imię"]
```

Przypisanie przez `slownik["Zwierze"] = ` dodaje nową parę klucz–wartość.

``` python
slownik["Zwierze"] = "python"

print(slownik)
```

## Operacje na słownikach
`dir(dict)` wypisuje dostępne metody słowników.

``` python
dir(dict)
```

`.keys()` zwraca dynamiczny widok kluczy słownika.

``` python
slownik = {'Imię': 'Ala', 'Wiek': 20, 'Zwierze': 'python'}

slownik.keys()
```

Po widoku `.keys()` można iterować w pętli `for`.

``` python
lista = slownik.keys()

for i in lista:
    print(i)
```

`.values()` zwraca widok wartości słownika.

``` python
slownik = {'Imię': 'Ala', 'Wiek': 20, 'Zwierze': 'python'}

slownik.values()
```

`list()` zamienia widok wartości słownika na listę; `for` wypisuje każdy element.

``` python
lista = list(slownik.values())

for i in lista:
    print(i)
```

`.items()` zwraca widok par `(klucz, wartość)`.

``` python
slownik = {'Imię': 'Ala', 'Wiek': 20, 'Zwierze': 'python'}

slownik.items()
```

Pętla `for x, y in dictionary.items()` rozpakowuje każdą parę na dwie zmienne.

``` python
for x, y in slownik.items():
    print(x, y)
```

`del slownik[klucz]` usuwa wybraną parę ze słownika.

``` python
del slownik['Zwierze']

for x, y in slownik.items():
    print(x, y)
```

## Zbiory
Struktura danych, która jest nieuporządkowana i nieindeksowana.

Zbiór `set` usuwa duplikaty; kolejność wyświetlania elementów nie jest gwarantowana.

``` python
zbior = {"ala", "ma", "pythona", "ala"}

print(zbior)
```

`.add()` dodaje pojedynczy element do zbioru.

``` python
zbior.add("alan")
print(zbior)
```

`.update()` dodaje do zbioru wszystkie elementy podanej kolekcji.

``` python
zbior.update(["ma", "kota"])
print(zbior)
```

`.remove()` usuwa element ze zbioru; brak elementu spowoduje `KeyError`.

``` python
zbior.remove("kota")
print(zbior)
```

`dir(set)` wypisuje metody dostępne dla zbiorów.

``` python
dir(set)
```

## Funkcje
Funkcje tworzymy w następujący sposób:
+ używamy słowa kluczowego `def`
+ podajemy nazwę funkcji zakończoną `():`
+ tworzymy wcięty blok instrukcji zakończony instrukcją `return`

``` python
def funkcja():
    # blok instrukcji
    return wyrażenie
```
+ Wewnątrz `()` mogą znajdować się parametry, które domyślnie mają swój porządek
``` python
def funkcja(parametr_1, parametr_2):
    # blok instrukcji
    return wyrażenie
```

Funkcję wywołujemy poprzez użycie jej nazwy z odpowiednim zestawem parametrów.

`def` definiuje funkcję; `print()` wyświetla argument, a `return` bez wartości kończy funkcję i zwraca `None`.

``` python
def funkcja(parametr):
    print(parametr)
    return 

funkcja(1)
```

Pierwszym poleceniem `blok instrukcji` może być docstring, który będzie informował co dana funkcja robi. Wywołanie tej informacji uzyskamy za pomocą polecenia `help(funkcja)`.

Napis bezpośrednio pod nagłówkiem `def` jest docstringiem; `help()` wyświetla dokumentację funkcji.

``` python
def funkcja(parametr):
    "wyświetla wartość parametru"
    print(parametr)
    return 

help(funkcja)
```

Argumenty do funkcji są przekazywane przez **referencję**, tzn. zmieniając wartość zmiennej wewnątrz funkcji, zmieniamy również wartość tej zmienej poza funkcją.

Wywołanie `.append()` modyfikuje przekazaną listę w miejscu, więc zmianę widać też poza funkcją.

``` python
napis = ["ala ma pythona"]

def funkcja(parametr):
    parametr.append("ala ma psa")
    print(parametr)
    return

funkcja(napis)
print(napis) 
```

## Argumenty funkcji
Argumenty funkcji mogą być następujących rodzanów:
1. **Argumenty obowiązkowe**: Tyle ile zostało zadeklarowanych parametrów w definicji funkcji musi później zostać przekazanych w odpowiedniej kolejności przy jej wywołaniu.
2. **Argumenty słowa-kluczowe**: Przy wywołaniu funkcji można podać pary `parametr=argument`. Wtedy nie musi być zachowana zdefiniowana kolejność argumentów.
3. **Argumenty domyślne**: Argument domyślny przyjmuje przy definicji pewną domyślną wartość. Może zostać pominięty przy wywołaniu funkcji (o ile jest ostatnim argumentem).
4. **Argumenty zmiennej długości**: Prócz argumentów podanych wprost w definicji funkcji, można okreslić dodatkową zmienną listę argumentów. Taką listę dodajemy na samym końcu deklarowanych argumentów i poprzedzamy ją symbolem `*`.

## Funkcje `lambda`
Takie funkcje definiujemy za pomocą słowa kluczowego `lambda`, a nie `def`. 
+ Przyjmują one dowolną ilość argumentów, ale zwracają tylko jedno wyrażenie. 
+ Nie mogą bezpośrednio drukować argumentów. 

Ich definicja jest nastepująca:
``` python
nazwa_funkcji = lambda arg_1, ..., arg_n : wyrażenie
```

`lambda` tworzy krótką funkcję anonimową, która oblicza jedno wyrażenie.

``` python
funkcja = lambda parametr_1, parametr_2 : parametr_1 + parametr_2
print(funkcja("ala", " ma pythona"))
```

Funkcja może zwracać funkcję `lambda`, która pamięta argument funkcji zewnętrznej (domknięcie).

``` python
def funkcja(arg):
    return lambda a : a + arg

fun_1 = funkcja(" ma pythona")
print(fun_1("ala"))
```

## Zasięg zmiennych
Zmienne mogą być **lokalne** bądź **globalne**.
* Zmienna lokalna jest zdefiniowana wewnątrz bloku funkcji i jest tylko w nim dostepna
* Zmienna globalna jest dostepna z każdego poziomu

Przypisanie wewnątrz funkcji tworzy lokalną nazwę `napis`, niezależną od nazwy globalnej.

``` python
napis = "ala ma pythona"

def lubieKoty():
    napis = "ala ma kota"
    return napis

print(lubieKoty())
print(napis)
```

Funkcja może również modyfikować zmienną globalną. Wystarczy oddać słowo kluczowe `global` przez nazwą zmiennej.

Deklaracja `global napis` pozwala przypisać nową wartość nazwie z zakresu globalnego.

``` python
napis = "ala ma pythona"

def lubieKoty():
    global napis 
    napis = "ala ma kota"
    return napis

print(lubieKoty())
print(napis)
```

## Wyrażenia listowe
Wyrażenia listowe pozwalają na przekształcenie jednej listy w drugą.

Wyrażenie listowe `[i * 2 for i in x]` tworzy nową listę, podwajając elementy.

``` python
x = [1, 2, 3]
y = [i*2 for i in x]
print(y)
```

`range(len(x))` wytwarza indeksy listy; `x[i]` pobiera kolejne wartości do podwojenia.

``` python
x = [1, 2, 3]
y = [x[i]*2 for i in range(len(x))]
print(y)
```

Warunek `if` wewnątrz wyrażenia listowego filtruje elementy, tutaj pozostawia tylko parzyste.

``` python
x = [1, 2, 3]
y = [x[i]*2 for i in range(len(x)) if x[i] % 2 == 0]
print(y)
```

## Wyrażenia generujące
Wyrażenie w nawiasach okrągłych tworzy generator, który oblicza kolejne wartości na żądanie.

``` python
podwojone = (x * 2 for x in range(5))
podwojone
```

Metoda `.__next__()` pobiera kolejny element generatora; po wyczerpaniu rzucany jest `StopIteration`.

``` python
podwojone.__next__()
```

Wbudowane `next(generator)` pobiera następną wartość generatora.

``` python
next(podwojone)
```

## Moduły Pythona
Moduły pozwalają na grupowanie funkcji w jedna zwartą paczkę. 
Moduły dołączamy do skryptu za pomocą słowa kluczowego `import`.

``` python
import moduł_1, moduł_2,..., moduł_n
```
Interpreter szuka w zaimportowanego modułu w zadeklarowanej ścieżce. Domyślna ścieżka to katalog roboczy skryptu.

Dowolną funkcję z zaimportowanego modułu używamy w natępujący sposób

``` python
moduł.funkcja
```

Czasami wygodniej jest stosować **alias** do modułu zamiast pełnej nazwy, np. zamiast stosować `matplotlib.pyplot` za każdym razem, gdy chcemy użyć chociażby funkcji `plot` można użyć aliasa `plt` w następujący sposób
``` python
import matplotlib.pyplot as plt
```

Aby zaimportować wybrane funkcje z modułu wykorzystujemy następujący schemat
``` python
from moduł import funkcja_1, ..., funkcja_n
```

Wtedy aby użyć tej funkcji wystarczy w skrypcie dodać `sin(argument)` zamiast `math.sin(argument)`.

Aby zaimportować wszystkie funkcje z modułu wykorzystujemy następujący schemat
```
from moduł import *
```

`from math import *`

Wtedy aby użyć funkcji `sin` i `cos` wystarczy wpisać `sin(argument)` i `cos(argument)`.

Interpreter w pierwszej kolejności szuka modułu w katalogu roboczym. Jeśli tam go nie ma, to kolejno przeszukiwanymi katalogami są te z zmiennej środowiskowej `PYTHONPATH`.

Zawartość modułu (lista funkcji) można zobaczyć za pomocą polecenia `dir(moduł)`.

`import math` ładuje moduł, a `dir(math)` wyświetla jego nazwy, w tym funkcje i stałe.

``` python
import math
dir(math)
```

## Operacje na plikach
`f = open(plik, tryb)`

|  Tryb  |                    Opis                     |
| :----: | :-----------------------------------------: |
| `'r'`  |                odczyt pliku                 |
| `'w'`  |          zapis do pliku, nadpisuje          |
| `'r+'` |            zapis i odczyt pliku             |
| `'a'`  |              dopisuje do pliku              |
| `'b'`  |      zapis i odczyt w trybie binarnym       |
|  `x`   | tworzy plik, zwraca błąd jeśli już istnieje |

`open("plik.txt", "r")` otwiera istniejący plik tekstowy do odczytu; brak pliku powoduje `FileNotFoundError`.

``` python
f = open("plik.txt", "r")
```

Iteracja `for` po obiekcie pliku odczytuje kolejne wiersze; `print()` dodaje własny znak końca linii.

``` python
for i in f:
    print(i)
```

|    Metoda    |              Opis              |
| :----------: | :----------------------------: |
|   `read()`   |   czyta całą zawartość pliku   |
| `readline()` | czyta pojedyńczą linię w pliku |

Tryb `"rt"` oznacza odczyt tekstowy; `.read()` pobiera całą zawartość pliku.

``` python
f = open("plik.txt", "rt")
print(f.read())
```

Zamknięcie pliku: `f.close()`

Konstrukcja `with open( ) as f` automatycznie zamyka plik po wyjściu z bloku; `.read()` odczytuje zawartość.

``` python
with open('plik.txt') as f:
    read_data = f.read()
read_data
```
