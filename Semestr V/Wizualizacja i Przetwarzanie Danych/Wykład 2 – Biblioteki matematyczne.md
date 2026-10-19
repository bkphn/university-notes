## Stałe matematyczne
W bibliotece `math` możemy korzystać z następujących stałych matematycznych:
- `pi` – $\pi$.
- `e` – $e$.
- `tau` – $\tau = 2\pi$.
- `inf` – nieskończoność numeryczna, `float('inf')`.
- `nan` – `NaN`, `float('nan')`.

## Funkcje numeryczne
Z `math` możemy zaimplementować następujące funkcje numeryczne:
- `ceil(x)` – działa jak tradycyjny sufit.
- `copysign(x,y)` – zwraca moduł liczby `x` ze znakiem liczby `y`.
- `fabs(x)` – działa jak tradycyjny moduł.
- `factorial(x)` – zwraca `x!`.
- `floor(x)` – działa jak tradycyjna podłoga.
- `fmod(x,y)` – zwraca $x\text{ mod }y$, zalecana przy floatach.
- `frexp(x)` – zwraca parę (mantysa, cecha), tj. $x=m\cdot 2 ^{c}$.
- `fsum(iterable_obj)` – zwraca sumę obiektu iterowalnego.
- `gcd(x,y)` – zwraca $\text{nwd}(x,y)$.
- `isclose(x,y, rel_tol=1e-09, abs_tol=0.0)` – sprawdza, czy `x` i `y` są bliskie, zgodnie z zadaną tolerancją; np. `isclose(2, 2.00000001)=False`, `isclose(2, 2.000000001)=True`.`
- `isfinite(x)` – zwraca `True` jeśli `x` nie jest nieskończonością albo `NaN`.
- `isinf(x)` – zwraca `True` jeśli `x` jest $\pm$ nieskończonością.
- `isnan(x)` – zwraca `True` jeśli x jest `NaN`.
- `ldexp(x,i)` – zwraca $y=x2^i$, odwrotność funkcji `frexp(y)`.
- `modf(x)` – zwraca parę (część ułamkowa, część całkowita).

## Funkcje analityczne
Z biblioteki `math` możemy implementować następujące funkcje analityczne:
- `exp(x)` – zwraca $e^x$.
- `expm1(x)` – zwraca $e^x-1$, przydatna dla małych wartości $x$.
- `log(x,b)` – zwraca $\log_{b}x$, domyślnie $b=e$.
- `log2(x)` – zwraca $\log_2 x$.
- `log10(x)` – zwraca $\log_{10} x$.
- `pow(x,y)` – zwraca $x^y$.
- `sqrt(x)` – zwraca $\sqrt{x}$.
- `acos(x)` – zwraca $\arccos{x}$.
- `asin(x)` – zwraca $\arcsin{x}$.
- `atan(x)` – zwraca $\arctan{x}$.
- `cos(x)` – zwraca $\cos{x}$.
- `degrees(x)` – zamienia radiany na stopnie.
- `hypot(x,y)` – zwraca moduł liczby zespolonej $x+iy$.
- `radians(x)` – zamienia stopnie na radiany.
- `sin(x)` – zwraca $\sin{x}$.
- `tan(x)` – zwraca $\tan{x}$.
- `acosh(x)` – zwraca $\text{acosh}x$.
- `asinh(x)` – zwraca $\text{asinh}x$.
- `atanh(x)` – zwraca $\text{atanh}x$.
- `cosh(x)` – zwraca $\text{cosh}x$.
- `tanh(x)` – zwraca $\text{tanh}x$.
- `erf(x)` – funkcja błędu, $\mathrm{erf}(x) = \frac{2}{\sqrt{\pi}}\int\limits_0^x e^{-t^2} dt$.
- `erfc(x)` – uzupełniająca funkcja błędu, $\mathrm{erfc}(x) = 1-\mathrm{erf}(x)$.
- `gamma(x)` – funkcja Gamma, $\Gamma(z) = \int_0^{\infty} t^{z-1}e^{-t}dt$ dla $\mathfrak{R}(z) > 0$.

## Generowanie liczb całkowitych
Liczby pseudolosowe możemy generować z wykorzystaniem biblioteki `random`:
- `randint(a, b)` – zwraca wartość całkowitą z przedziału $[a,b]$.
- `randrange(a, b, krok)` – zwraca wartość całkowitą od `a` (włącznie) do `b` (wyłącznie), z podanym krokiem.
- `random()` – zwraca wartość z przedziału $[0,1]$.
- `uniform(a, b)` – zwraca wartość z przedziału $[a,b]$.
- `triangular(a, b, moda)` – zwraca wartość z przedziału $[a,b]$ z modą w punkcie `moda`.
- `expovariate(lambda)` – zwraca wartość z rozkładu wykładniczego z $\lambda$ = `lambda`.
- `gauss(srednia, odchylenie)` – zwraca wartość z rozkładu normalnego z odpowiednią `średnią` i `odchyleniem`.
- `paretovariate(alpha)` – zwraca wartość z rozkładu Pareto z parametrem kształtu `alpha`.
- `weibullvariate(alpha, beta)` – zwraca wartość z rozkładu Weibulla z parametrem skali = `alpha` i parametrem kształtu = `beta`.

## Losowanie elementów kolekcji
Możemy wykorzystać bibliotekę `random` do losowania elementu z kolekcji:
- `choice(zbiór)` – zwraca wartość z podanego `zbioru`.
- `choices(zbiór, wagi, k=1)` – zwraca `k` wartości z powtórzeniami ze zbioru z uzględnieniem wag
- `shuffle(zbiór)` – permutuje elementy zbioru.
- `sample(zbiór, k)` – zwraca `k` elementów bez powtórzeń ze zbioru.

## Tablice i macierze NumPy
`np.array()` tworzy jednowymiarową tablicę NumPy z podanych elementów; `import numpy as np` nadaje bibliotece alias `np`.

``` python
import numpy as np

lista = np.array([1, 2, 3, 4, 5])

print(lista)
```

Tablica NumPy przechowuje elementy o wspólnym typie danych; obecność `3.14` powoduje konwersję liczb całkowitych do `float`.

``` python
print(np.array([3.14, 2, 3, 4, 5]))
```

Zagnieżdżone listy przekazane do `np.array()` tworzą tablicę dwuwymiarową (macierz).

``` python
macierz = np.array([[1, 2], [3, 4]])

print(macierz)
```

Wyrażenie listowe z `range()` buduje kolejne wiersze macierzy o rozmiarze `3 × 3`.

``` python
macierz = np.array([range(i, i + 3) for i in [1, 4, 7]])

print(macierz)
```

W notebooku porównujemy czas wykonywania operacji na listach i tablicach NumPy za pomocą `%timeit` (komenda środowiska IPython).

Magiczna komenda Jupytera `%timeit` mierzy czas wykonania. Porównujemy listę z `math.sin()` z wektorowym `np.sin()`; `-n` ustala liczbę wykonań, a `-r` liczbę powtórzeń pomiaru.

``` python
import math

%timeit -n 1 -r 3 [math.sin(i) for i in range(10**6)]
%timeit -n 1 -r 3 np.sin(np.arange(10**6))
```

`%timeit` porównuje zwiększanie elementów listy przez wyrażenie listowe z operacją wektorową `np.arange(...) + 1`.

``` python
%timeit -n 1 -r 3 [i+1 for i in range(10**6)]
%timeit -n 1 -r 3 np.arange(10**6) + 1
```

Do tworzenia tablic o zadanych wartościach służą `zeros()`, `ones()` i `full()`.

`np.zeros()`, `np.ones()` i `np.full()` tworzą tablice wypełnione odpowiednio zerami, jedynkami i wskazaną wartością.

``` python
macierz_1 = np.zeros(10)
macierz_2 = np.ones(10)
macierz_3 = np.full(10, 3.14)

print(macierz_1)
print(macierz_2)
print(macierz_3)
```

Argument określający kształt, np. `(2, 3)`, tworzy macierz; `dtype` wymusza typ elementów. `dtype=int` dla `3.14` obcina część ułamkową.

``` python
macierz_1 = np.zeros((2,3), dtype=int)
macierz_2 = np.ones((3,2), dtype=bool)
macierz_3 = np.full((3,3), 3.14, dtype=int)

print(macierz_1)
print(macierz_2)
print(macierz_3)
```

Do generowania uporządkowanych wartości służą `arange()` i `linspace()`.

`np.arange(start, stop, step)` generuje wartości od `start` do wartości mniejszej niż `stop`, ze wskazanym krokiem.

``` python
wektor = np.arange(0, 10, 2)

print(wektor)
```

`np.linspace(0, 1, 10)` zwraca 10 równomiernie rozmieszczonych wartości z przedziału od 0 do 1, wraz z końcem przedziału.

``` python
wektor = np.linspace(0, 1, 10)

print(wektor)
```

`endpoint=False` wyłącza koniec przedziału z wartości generowanych przez `np.linspace()`.

``` python
wektor = np.linspace(0, 1, 10, endpoint=False)

print(wektor)
```

Macierz jednostkową można utworzyć funkcją `eye()`.

`np.eye(3)` tworzy macierz jednostkową `3 × 3` – jedynki na przekątnej głównej i zera poza nią.

``` python
macierz = np.eye(3)

print(macierz)
```

## Atrybuty tablic
Atrybuty `ndim`, `shape` i `size` zwracają kolejno liczbę wymiarów, kształt tablicy i łączną liczbę jej elementów.

``` python
macierz = np.array([range(i, i + 3) for i in [1, 4, 7]])

print(macierz)
print(macierz.ndim)
print(macierz.shape)
print(macierz.size)
```

## Indeksowanie tablic
`np.array()` tworzy macierz, którą następnie wyświetla `print()`.

``` python
macierz = np.array([range(i, i + 3) for i in [1, 4, 7]])

print(macierz)
```

Indeks `macierz[0]` pobiera pierwszy wiersz macierzy.

``` python
print(macierz[0])
```

Zapis `macierz[0, 0]` pobiera element z pierwszego wiersza i pierwszej kolumny.

``` python
print(macierz[0, 0])
```

Zapis `macierz[0][0]` również pobiera pierwszy element pierwszego wiersza, lecz wykonuje dwa kolejne indeksowania.

``` python
print(macierz[0][0])
```

Ujemny indeks `-1` oznacza ostatni wiersz macierzy.

``` python
print(macierz[-1])
```

Zapis `macierz[0, -1]` zwraca ostatni element pierwszego wiersza.

``` python
print(macierz[0, -1])
```

## Wycinki tablic
`np.arange(10)` tworzy wektor wartości od `0` do `9`; przypisanie `wektor = x = ...` wiąże obie nazwy z tą samą tablicą.

``` python
wektor = x = np.arange(10)

print(wektor)
```

Wycinek `[:7]` pobiera elementy od indeksu `0` do `6`.

``` python
print(wektor[:7])
```

Wycinek `[7:]` pobiera elementy od indeksu `7` do końca tablicy.

``` python
print(wektor[7:])
```

Wycinek `[1:7]` wybiera elementy o indeksach od `1` do `6`.

``` python
print(wektor[1:7])
```

Wycinek `[1:7:2]` wybiera elementy od indeksu `1` do `6` z krokiem `2`.

``` python
print(wektor[1:7:2])
```

Ujemny krok `[: :-1]` odwraca kolejność elementów wektora.

``` python
print(wektor[::-1])
```

Indeksowanie `[:2, :2]` wybiera podmacierz złożoną z pierwszych dwóch wierszy i kolumn.

``` python
macierz = np.array([range(i, i + 3) for i in [1, 4, 7]])

print(macierz[:2, :2])
```

Wycinek `[: :-1, : :-1]` odwraca kolejność zarówno wierszy, jak i kolumn.

``` python
print(macierz[::-1, ::-1])
```

Zapis `[:2, : :2]` wybiera pierwsze dwa wiersze i co drugą kolumnę.

``` python
print(macierz[:2, ::2])
```

Zapis `[:, 0]` wybiera całą pierwszą kolumnę macierzy.

``` python
print(macierz[:, 0])
```

## Modyfikowanie elementów
Przypisanie `macierz[0, 0] = -1` zmienia element tablicy w miejscu.

``` python
macierz[0,0] = -1

print(macierz)
```

## Kopiowanie tablic
Metoda `.copy()` tworzy niezależną kopię danych; modyfikacja oryginalnej macierzy nie zmienia kopii.

``` python
macierz_1 = np.array([range(i, i + 3) for i in [1, 4, 7]])
macierz_2 = macierz_1.copy()

macierz_1[0,0] = -1

print(macierz_1)
print(macierz_2)
```

## Zmiana kształtu tablic
Metoda `.reshape(3, 3)` zmienia kształt dziewięcioelementowej tablicy na macierz `3 × 3`.

``` python
import numpy as np

macierz = np.arange(1, 10).reshape(3, 3)

print(macierz)
```

`.flatten()` zwraca spłaszczoną, jednowymiarową kopię macierzy.

``` python
macierz_1 = macierz.flatten()
macierz_1
```

`np.arange(1, 10)` tworzy jednowymiarową tablicę liczb od `1` do `9`.

``` python
macierz = np.arange(1, 10)
print(macierz)
```

`.reshape((9, 1))` przekształca dziewięć elementów w macierz kolumnową o dziewięciu wierszach.

``` python
macierz = np.arange(1, 10).reshape((9, 1))

print(macierz)
```

## Maskowanie logiczne
`np.arange(100).reshape(10, 10)` tworzy macierz `10 × 10` z liczbami od `0` do `99`.

``` python
macierz = np.arange(100).reshape(10,10)
macierz
```

Porównania `(macierz > 30) & (macierz < 51)` tworzą maskę logiczną; `macierz[m]` zwraca elementy spełniające oba warunki.

``` python
m = (macierz > 30) & (macierz < 51)
macierz[m]
```

## Łączenie tablic
`np.concatenate()` łączy tablice wzdłuż istniejącej osi; w tym przykładzie tworzy jeden dłuższy wektor.

``` python
macierz_1 = np.array([1, 2, 3])
macierz_2 = np.array([4, 5, 6])

macierz_3 = np.concatenate([macierz_1, macierz_2])
print(macierz_3)
```

## Dzielenie tablic
`np.split(macierz, [2, 6])` dzieli tablicę w indeksach `2` i `6` na trzy części.

``` python
macierz = np.arange(9)
macierz_1, macierz_2, macierz_3 = np.split(macierz, [2, 6])
print(macierz_1)
print(macierz_2)
print(macierz_3)
```

## Operacje na tablicach
## Operacje na skalarach
Działania `+`, `-`, `*`, `/`, `**`, `%` i `//` z wartością skalarną są wykonywane element po elemencie.

``` python
macierz = np.arange(4).reshape((2,2))

print("macierz     =", macierz)
print("macierz + 2 =", macierz + 2)
print("macierz - 2 =", macierz - 2)
print("macierz * 2 =", macierz * 2)
print("macierz / 2 =", macierz / 2)
print("macierz ** 2 =", macierz ** 2)
print("macierz % 2 =", macierz % 2)
print("macierz // 2 =", macierz // 2)
```

Wyrażenie `-(2 * macierz - 1) ** 2` wykonuje operacje na wszystkich elementach tablicy, zgodnie z priorytetami operatorów.

``` python
macierz_1 = -(2 * macierz - 1) ** 2

print(macierz)
print(macierz_1)
```

`np.sin()` oblicza sinus każdego elementu przekazanej sekwencji; argumenty są interpretowane w radianach.

``` python
np.sin([1,2,3,4])
```

Odpowiedniki operacji arytmetycznych to:
- `+`: `np.add()`
- `-`: `np.subtract()`
- zmiana znaku: `np.negative()`
- `*`: `np.multiply()`
- `/`: `np.divide()`
- `//`: `np.floor_divide()`
- `**`: `np.power()`
- `%`: `np.mod()`

`np.abs()` oblicza wartość bezwzględną każdego elementu tablicy.

``` python
macierz = np.array([-1, 2])

print(np.abs(macierz))
```

Dla liczb zespolonych `np.abs()` zwraca moduł liczby zespolonej, czyli jej odległość od zera na płaszczyźnie zespolonej.

``` python
macierz = np.array([-1 + 1j, 1 - 1J])

print(np.abs(macierz))
```

## Operacje na macierzach
`np.array_equal()` sprawdza, czy dwie tablice mają taki sam kształt i jednakowe elementy; argumentem może też być lista zagnieżdżona.

``` python
macierz_1 = np.eye(2)
macierz_2 = [[1,0], [0,1]]
np.array_equal(macierz_1,macierz_2)
```

Dodawanie `macierz_1 + macierz_2` wykonuje się element po elemencie, a nie według mnożenia macierzowego.

``` python
macierz_1 = np.arange(4).reshape((2,2))
macierz_2 = np.eye(2)

print("macierz_1=\n", macierz_1, '\nmacierz_2=\n', macierz_2, '\nmacierz_1 + macierz_2=\n', macierz_1 + macierz_2 )
```

`np.dot(macierz_1, macierz_2)` oblicza iloczyn macierzowy dla tablic dwuwymiarowych.

``` python
macierz_1 = np.arange(4).reshape((2,2))
macierz_2 = np.eye(2)

print("macierz_1=\n", macierz_1, '\nmacierz_2=\n', 
      macierz_2, '\nmacierz_1 * macierz_2=\n', np.dot(macierz_1, macierz_2) )
```

Operator `@` oznacza mnożenie macierzowe i w tym przykładzie odpowiada `np.dot()`.

``` python
macierz_1 = np.arange(4).reshape((2,2))
macierz_2 = np.eye(2)

print("macierz_1=\n", macierz_1, '\nmacierz_2=\n', 
      macierz_2, '\nmacierz_1 * macierz_2=\n', macierz_1@macierz_2 )
```

`np.trace()` zwraca ślad macierzy, czyli sumę elementów jej przekątnej głównej.

``` python
macierz = np.arange(4).reshape((2,2))

print(macierz)
print(np.trace(macierz))
```

## Odczyt danych tekstowych
`StringIO` udostępnia napis jako obiekt plikowy, a `np.genfromtxt()` odczytuje wartości liczbowe rozdzielone przecinkami.

``` python
from io import StringIO

dane = u"1, 2, 3\n4, 5, 6"
np.genfromtxt(StringIO(dane), delimiter=",")
```

## Algebra liniowa – `numpy.linalg`
`numpy.linalg.matrix_power()` oblicza potęgę macierzy w sensie mnożenia macierzowego; wynik porównujemy z `np.dot(macierz, macierz)`.

``` python
import numpy.linalg as lg

macierz = np.arange(4).reshape((2,2))

macierz_kw = lg.matrix_power(macierz, 2)

print(macierz_kw)
print(np.dot(macierz, macierz))
```

`numpy.linalg.eig()` oblicza wartości własne i odpowiadające im wektory własne macierzy.

``` python
macierz = [[1,0], [0,2]]

wartości_własne = lg.eig(macierz)

print(wartości_własne)
```

`numpy.linalg.det()` oblicza wyznacznik macierzy kwadratowej.

``` python
macierz = [[1,0], [0,2]]
print(macierz)
wyznacznik = lg.det(macierz)

print(wyznacznik)
```

`numpy.linalg.matrix_rank()` oblicza rząd macierzy; przykłady pokazują macierz pełnego rzędu i macierz o rzędzie mniejszym.

``` python
macierz_1 = [[1,0], [0,2]]
macierz_2 = [[1,0], [1,0]]

print(lg.matrix_rank(macierz_1))
print(lg.matrix_rank(macierz_2))
```

`numpy.linalg.inv()` zwraca macierz odwrotną, a `np.dot()` pozwala sprawdzić, czy ich iloczyn jest numerycznie bliski macierzy jednostkowej.

``` python
macierz = np.arange(4).reshape((2,2))

odwrotna = lg.inv(macierz)

print(odwrotna)
print(np.dot(macierz, odwrotna))
```

`numpy.linalg.solve(A, b)` rozwiązuje układ równań liniowych `Ax = b`.

``` python
A = [[1,2],[-1,1]]
b = [-1, -2]

rozwiązanie = lg.solve(A,b)

print(rozwiązanie)
```

## Statystyka opisowa – NumPy
`np.mean()` oblicza średnią arytmetyczną elementów listy.

``` python
A = list(range(4))

print(A)

średnia = np.mean(A)
print(średnia)
```

`np.mean()` bez parametru `axis` oblicza średnią ze wszystkich elementów macierzy.

``` python
A = np.arange(4).reshape((2,2))

print(A)

średnia = np.mean(A)
print(średnia)
```

`axis=0` oznacza redukcję po wierszach: otrzymujemy osobną średnią dla każdej kolumny.

``` python
średnia_1 = np.mean(A, axis=0)
print(średnia_1)
```

`axis=1` oznacza redukcję po kolumnach: otrzymujemy osobną średnią dla każdego wiersza.

``` python
średnia_2 = np.mean(A, axis=1)
print(średnia_2)
```

`np.std()` oblicza odchylenie standardowe; domyślnie korzysta z dzielnika `N` (`ddof=0`).

``` python
A = list(range(4))

print(A)

std = np.std(A)
print(std)
```

`np.std()` bez `axis` oblicza odchylenie standardowe wszystkich elementów macierzy.

``` python
A = np.arange(4).reshape((2,2))

print(A)

std = np.std(A)
print(std)
```

`np.std(A, axis=0)` zwraca odchylenia standardowe obliczone dla każdej kolumny.

``` python
std_1 = np.std(A, axis=0)
print(std_1)
```

`np.std(A, axis=1)` zwraca odchylenia standardowe obliczone dla każdego wiersza.

``` python
std_2 = np.std(A, axis=1)
print(std_2)
```

`np.var()` oblicza wariancję; domyślnie korzysta z dzielnika `N` (`ddof=0`).

``` python
A = list(range(4))

print(A)

wariancja = np.var(A)
print(wariancja)
```

`np.var()` bez `axis` oblicza wariancję ze wszystkich wartości macierzy.

``` python
A = np.arange(4).reshape((2,2))

print(A)

wariancja = np.var(A)
print(wariancja)
```

`np.var(A, axis=0)` oblicza wariancję osobno dla każdej kolumny.

``` python
wariancja_1 = np.var(A, axis=0)
print(wariancja_1)
```

`np.var(A, axis=1)` oblicza wariancję osobno dla każdego wiersza.

``` python
wariancja_2 = np.var(A, axis=1)
print(wariancja_2)
```

`np.median()` wyznacza medianę elementów listy.

``` python
A = list(range(5))

print(A)

mediana = np.median(A)
print(mediana)
```

`np.median()` bez `axis` wyznacza medianę ze wszystkich elementów macierzy.

``` python
A = np.arange(4).reshape((2,2))

print(A)

mediana = np.median(A)
print(mediana)
```

`np.median(A, axis=0)` zwraca mediany dla poszczególnych kolumn.

``` python
mediana_1 = np.median(A, axis=0)
print(mediana_1)
```

`np.median(A, axis=1)` zwraca mediany dla poszczególnych wierszy.

``` python
mediana_2 = np.median(A, axis=1)
print(mediana_2)
```

## Liczby pseudolosowe – `numpy.random`
`np.random.randint(-10, 10, (2, 2))` generuje macierz `2 × 2` pseudolosowych liczb całkowitych od `-10` do `9`.

``` python
macierz = np.random.randint(-10,10, (2, 2))
macierz
```

`np.random.randint(-10, 10, 10)` generuje wektor dziesięciu pseudolosowych liczb całkowitych od `-10` do `9`.

``` python
macierz = np.random.randint(-10,10, 10)
macierz
```

Rozkład normalny pozwala generować wartości wokół zadanej średniej, z określonym odchyleniem standardowym.

`np.random.normal(avg, std, 10)` generuje dziesięć pseudolosowych wartości z rozkładu normalnego o średniej `avg` i odchyleniu standardowym `std`.

``` python
avg, std = 0, 1 
s = np.random.normal(avg, std, 10)
```
