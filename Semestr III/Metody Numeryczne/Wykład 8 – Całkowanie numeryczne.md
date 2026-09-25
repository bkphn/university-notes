## Sformułowanie zagadnienia
Wyznaczenie funkcji pierwotnej często jest bardzo trudne lub wręcz niemożliwe. Ponadto, jeśli funkcja podcałkowa jest znana tylko w wybranych punktach przedziału całkowania, pojęcie funkcji pierwotnej traci sens, co wymusza obliczanie przybliżonej wartości całki.

Przybliżenie całki wzorem:

$$\int_a^b f(x)dx \approx \sum_{j=0}^n A_j f(x_j)$$

nazywamy kwadraturą, liczby $x_0, \dots, x_n$ nazywamy węzłami kwadratury, natomiast liczby $A_0, \dots, A_n$ współczynnikami kwadratury.

## Proste kwadratury Newtona-Cotesa
Kwadratury te uzyskuje się, całkując wielomian interpolacyjny (np. Lagrange'a) zastępujący funkcję podcałkową $f$ w węzłach równoodległych na przedziale $[a, b]$.
Węzły $x_i = a + ih$, gdzie $h = \frac{b-a}{n}$.

Po całkowaniu wielomianu $W_n(x)$ otrzymuje się równanie:

$$\int_a^b W_n(x)dx = h \cdot \sum_{i=0}^n f(x_i) \cdot \alpha_i$$

Współczynniki $\alpha_i$ nie zależą od granic całkowania ani od funkcji $f$, lecz jedynie od stopnia wielomianu $n$. 

Ponieważ $\alpha_i$ to liczby wymierne, wprowadza się liczbę $r \in \mathbb{Q}$ oraz współczynniki całkowitoliczbowe $\sigma_i = r \alpha_i$. 
Ostateczny wzór przybliżonej całki wynosi:

$$I = \begin{cases} \frac{b-a}{r} \cdot f(x_0) \cdot \sigma_0, & n=0 \\ \frac{b-a}{n \cdot r} \cdot \sum_{i=0}^n f(x_i) \cdot \sigma_i, & n \ge 1 \end{cases}$$

Błąd metody (prostej) wyraża wzór:

$$E_n = h^{p+1}K \cdot f^{(p)}(\xi)$$

Dla obliczenia najgorszego przypadku błędu przyjmuje się $\sup_{x \in [a, b]} |f^{(p)}(x)|$.

### Tabela kwadratur Newtona-Cotesa
| $n$ | $\sigma_i$                      | $n \cdot r$ | Błąd $E_n$                           | Nazwa metody            |
| :-- | :------------------------------ | :---------- | :----------------------------------- | :---------------------- |
| $0$ | $1$                             |             | $h^2 \frac{1}{2} f'(\xi)$            | wzór prostokątów        |
| $1$ | $1, 1$                          | $2$         | $h^3 \frac{1}{12} f''(\xi)$          | wzór trapezów           |
| $2$ | $1, 4, 1$                       | $6$         | $h^5 \frac{1}{90} f^{(4)}(\xi)$      | wzór Simpsona (parabol) |
| $3$ | $1, 3, 3, 1$                    | $8$         | $h^5 \frac{3}{80} f^{(4)}(\xi)$      | wzór trzech-ósmych      |
| $4$ | $7, 32, 12, 32, 7$              | $90$        | $h^7 \frac{8}{945} f^{(6)}(\xi)$     | wzór Milne'a            |
| $5$ | $19, 75, 50, 50, 75, 19$        | $288$       | $h^7 \frac{275}{12096} f^{(6)}(\xi)$ |                         |
| $6$ | $41, 216, 27, 272, 27, 216, 41$ | $840$       | $h^9 \frac{9}{1400} f^{(8)}(\xi)$    | wzór Weddle'a           |

> [!abstract] Algorytm metody prostych kwadratur Newtona-Cotesa
> 0. **Dane**
>    - Granice całkowania $a, b$
>    - Funkcja całkowana $f(x)$
>    - Rodzaj metody
> 1. **Inicjalizacja zmiennych**
>    - Odczytujemy $n, nr, \sigma_i$
>    - $h = \frac{b-a}{n}$
>    - $x_i = a + ih$, oraz wartości $f(x_i)$
> 2. **Obliczamy przybliżoną wartość całki**
>    - Podstawiamy do ogólnego wzoru na $I$
> 3. **Odczytujemy wzór na błąd $E_n$ z tabeli**
> 4. **Obliczamy p-tą pochodną funkcji oraz błąd $E_n$**
>    - Szukamy supremum modułu pochodnej na przedziale
> 5. **Wynik**
>    - $I \pm E_n$

## Złożone kwadratury Newtona-Cotesa
Ponieważ błąd metody zależy od $h$, stosowanie prostej kwadratury na dużym przedziale daje duży błąd. Dzieli się więc przedział $[a, b]$ na $m=kn$ mniejszych podprzedziałów o długości $\Delta x = \frac{b-a}{m}$ i na każdym z nich z osobna stosuje metodę (gdzie $k$ to krotność stosowania kwadratury stopnia $n$).

Wzór na całkę przybiera formę:

$$I \approx \frac{\Delta x}{r} \cdot \sum_{i=0}^m \overline{\sigma}_i \cdot f(x_i)$$

**Konkretne przypadki błędu $R$ i współczynników $\overline{\sigma}_i$:**
* **Złożony wzór prostokątów:** 
  $R \le \frac{(b-a)^2}{2m} M$, $\overline{\sigma}_i \in \{1, \dots, 1, 0\}$
* **Złożony wzór trapezów:** 
  $R \le \frac{(b-a)^3}{12m^2} M$, $\overline{\sigma}_i = 1$ na brzegach, $2$ wewnątrz
* **Złożony wzór Simpsona:** 
  $R \le \frac{(b-a)^5}{180m^4} M$, dla $M = \sup |f^{(4)}(x)|$, współczynniki $\sigma_{i}$ układają się w sekwencję $1, 4, 2, 4, 2 \dots 1$

> [!abstract] Algorytm metody złożonych kwadratur Newtona-Cotesa
> 0. **Dane**
>    - Granice całkowania $a, b$, funkcja $f(x)$, krotność $k$, rodzaj metody
> 1. **Inicjalizacja zmiennych**
>    - Z tabeli: $n, r, \sigma_i$
>    - $\Delta x = \frac{b-a}{m}$
>    - $x_i = a + i \cdot \Delta x$, $f(x_i)$, $\overline{\sigma}_i$
> 2. **Obliczamy przybliżoną wartość całki**
>    - $I \approx \frac{\Delta x}{r} \sum \overline{\sigma}_i f(x_i)$
> 3. **Odczytujemy wzór na błąd $R$**
> 4. **Obliczamy wartość $M$ i błąd $R$ dla najgorszego przypadku**
> 5. **Wynik**
>    - $I \pm R$

## Kwadratury Gaussa
Całkę postaci $\int_a^b w(x)f(x)dx$ (gdzie $w(x)>0$) przybliża się sumą $\sum_{i=1}^n w_i f(x_i)$.
Współczynniki $w_i$ (wagi) i węzły $x_i$ dobiera się tak, aby błąd przybliżenia znikał dla wielomianu najwyższego możliwego stopnia. Kwadratura rzędu $r$ jest dokładna dla wielomianów stopnia $\le r$. Kwadraturę uzyskującą najwyższy możliwy rząd nazywamy **kwadraturą Gaussa**.

Węzły $x_i$ są zerami $n$-tego wielomianu ortogonalnego (dla wagi $w(x) \equiv 1$ są to **wielomiany Legendre'a**).

Kwadraturę na przedziale $[-1, 1]$ z wagą $w(x) \equiv 1$ zadają ustalone w tabeli wartości węzłów i wag (np. dla $n=2$: $x_i = \pm \frac{1}{\sqrt{3}}$, $w_1=w_2=1$).

Dla innych przedziałów stosuje się zamianę zmiennych:

$$t = \frac{b-a}{2}x + \frac{a+b}{2} \Rightarrow dt = \frac{b-a}{2}dx$$

Wtedy całka przyjmuje postać:

$$\int_a^b f(t)dt = \frac{b-a}{2} \int_{-1}^1 g(x)dx, \quad \text{gdzie } g(x) = f\left(\frac{b-a}{2}x + \frac{a+b}{2}\right)$$

> [!abstract] Algorytm kwadratur Gaussa
> 0. **Dane**
>    - Granice całkowania $a, b$, funkcja $f(x)$
> 1. **Inicjalizacja zmiennych**
>    - Odczytujemy rząd $r$
>    - $n = \frac{r+1}{2}$
>    - $t = \frac{b-a}{2}x + \frac{a+b}{2}$, $dt = t'dx$
>    - Z tabeli pobieramy węzły $x_i$ i wagi $w_i$ dla danego $n$
> 2. **Podstawiamy $t, dt$ pod całkę i wyznaczamy $g(x)$**
>    - $I = \alpha \int_{-1}^1 g(x)dx$ (gdzie $\alpha = \frac{b-a}{2}$)
> 3. **Obliczamy sumę**
>    - $S(f) = \alpha \sum_{i=1}^n w_i g(x_i)$
> 4. **Wynik**
>    - $I \approx S(f)$
