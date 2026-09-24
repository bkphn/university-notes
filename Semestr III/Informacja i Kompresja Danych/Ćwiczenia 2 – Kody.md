## Arytmetyka Modulo
Niech $a, b \in \mathbb{Z}$ oraz $n \in \mathbb{N}, n \ge 2$. Mówimy, że liczba $a$ dzieli liczbę $b$, jeżeli istnieje taka liczba $k \in \mathbb{Z}$, że $b = a \cdot k$ (co oznaczamy jako $a \mid b$).

Mówimy, że $a$ i $b$ przystają (są kongruentne) modulo $n$, jeżeli $n \mid (a - b)$, co zapisujemy jako: $$a \equiv b \pmod n \iff n \mid (a - b)$$
## Kod PESEL
Numer PESEL (Powszechny Elektroniczny System Ewidencji Ludności) to unikalny numer identyfikacyjny nadawany osobom urodzonym w Polsce. Ma postać: 
$$x_1x_2x_3x_4x_5x_6x_7x_8x_9x_{10}x_{11}$$
**Struktura kodu PESEL:**
* $x_1x_2$ – rok urodzenia
* $x_3x_4 + N$ – miesiąc urodzenia wraz z przesunięciem $N$ zależnym od stulecia:
	  * **1800–1899:** $N = 80$
	  * **1900–1999:** $N = 0$
	  * **2000–2099:** $N = 20$
	  * **2100–2199:** $N = 40$
	  * **2200–2299:** $N = 60$
* $x_5x_6$ – dzień urodzenia
* $x_7x_8x_9$ – numer porządkowy
* $x_{10}$ – płeć (nieparzyste: 1, 3, 5, 7, 9 – mężczyzna; parzyste: 0, 2, 4, 6, 8 – kobieta)
* $x_{11}$ – symbol kontrolny

Dla każdego poprawnego numeru PESEL zachodzi warunek:
$$(x_1 + 3x_2 + 7x_3 + 9x_4 + x_5 + 3x_6 + 7x_7 + 9x_8 + x_9 + 3x_{10} + x_{11}) \equiv 0 \pmod{10}$$

> [!example] Sprawdzenie poprawności numeru PESEL
> Sprawdzamy numer 98231152731:
> 1. Suma kontrolna: 
>    $9 + 3\cdot 8 + 7\cdot 2 + 9\cdot 3 + 1 + 3\cdot 1 + 7\cdot 5 + 9\cdot 2 + 7 + 3\cdot 3 + 1 = 148$.
> 2. Sprawdzenie modulo: 
>    $148 \not\equiv 0 \pmod{10}$ $\implies$ podany numer **nie jest** numerem PESEL.
## Kody kreskowe (EAN-13)
Kody kreskowe są graficzną reprezentacją informacji poprzez kombinację ciemnych i jasnych linii. Kody kreskowe przeznaczone są dla skanerów elektronicznych, które pozwalają na uzyskiwanie z nich informacji. Jednym z najpowszechniejszych standardów jest EAN-13 o postaci:
$$ x_1x_2x_3 - x_4x_5x_6x_7 - x_8x_9x_{10}x_{11}x_{12} - x_{13} $$
* $x_1x_2x_3$ – kod państwa (np. Polska to 590, Węgry 599, Chiny 690-699).
* $x_4x_5x_6x_7$ – kod producenta.
* $x_8x_9x_{10}x_{11}x_{12}$ – kod artykułu.
* $x_{13}$ – cyfra kontrolna.

> [!abstract] Algorytm sprawdzania poprawności kodu EAN-13
> 1. **Sumujemy cyfry na parzystych pozycjach**: $P = \sum_{i=1}^6 x_{2i}$.
> 2. **Sumujemy cyfry na nieparzystych pozycjach** (oprócz cyfry kontrolnej): $N = \sum_{i=1}^6 x_{2i-1}$.
> 3. **Obliczamy sumę**: $3 \cdot P + N$.
> 4. **Wyznaczamy resztę z dzielenia**: $x \equiv (3P + N) \pmod{10}$.
> 5. **Obliczamy różnicę**: $10 - x$.
> 6. **Wynik**: Jeśli otrzymana wartość jest równa cyfrze kontrolnej ($10 - x = x_{13}$), to kod jest poprawny.
## Kod ISBN (International Standard Book Number)
Globalny standard identyfikacji książek. Wersje 13-cyfrowe wprowadzono od 2006 roku, natomiast starsze kody miały 10 cyfr ($x_1x_2\dots x_{10}$).
* Pierwsze cyfry (np. $x_1\dots x_5$) oznaczają kraj lub obszar językowy (np. Polska to `83`, Francja `2`, Niemcy `3`).
* Ostatnia cyfra to suma kontrolna, gdzie $x_{10} \in \{0, 1, \dots, 9, \text{X}\}$.

Aby sprawdzić poprawność 10-znakowego kodu ISBN, należy zweryfikować warunek:
$$ \sum_{i=1}^{10} i \cdot x_i \equiv 0 \pmod{11} $$