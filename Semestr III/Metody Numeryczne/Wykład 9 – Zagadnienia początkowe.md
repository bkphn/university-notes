## Sformułowanie zagadnienia
Równaniem różniczkowym zwyczajnym nazywamy równanie, w którym szukana funkcja jednej zmiennej występuje pod znakiem pochodnej. W najprostszym przypadku rozważamy równanie pierwszego rzędu postaci $y'(x) = f(x, y)$.

Na ogół istnieje nieskończenie wiele rozwiązań. Za pomocą dodatkowego warunku początkowego (warunku Cauchy'ego) $y(x_0) = y_0$, wybieramy jedno szczególne rozwiązanie. 

Zatem zagadnienie początkowe definiujemy jako:
$$ \begin{cases} y' = f(x, y), \\ y(x_0) = y_0 \end{cases} \quad x \in (x_0, b) $$

W metodach numerycznych budujemy siatkę równomierną:
$$ S = \{x_i : x_i = x_0 + ih\} $$
gdzie $i \in \{0, 1, \dots, n\}$ oraz $h = \frac{b - x_0}{n}$.

Zamiast rozwiązania dokładnego $y(x_i)$, dla zadanego węzła $x_i$ wyznaczamy wartość przybliżoną $\eta_i$.
## Metoda Eulera
Metoda Eulera to podstawowa metoda jednokrokowa (do obliczenia $\eta_{i+1}$ wymaga tylko znajomości $\eta_i$).

Bazuje na przybliżeniu pochodnej ilorazem różnicowym:
$$ y'(x_0) \approx \frac{y(x_0+h) - y(x_0)}{h} $$
Co pozwala zapisać zależność rekurencyjną:
$$ y(x_1) \approx y(x_0) + h \cdot f(x_0, y_0) $$

Ogólny wzór metody Eulera to:
$$ \begin{cases} \eta_0 = y_0 \\ \eta_{i+1} = \eta_i + h \cdot f(x_i, \eta_i) \\ x_{i+1} = x_i + h \end{cases} $$

> [!abstract] Algorytm metody Eulera
> 0. **Dane:**
>    - Funkcja $f = f(x, y)$
>    - Wartości $x_0, y_0$
>    - Liczba kroków $n$ i koniec przedziału $b$
> 1. **Wyznaczamy $h$:**
>    - $h = \frac{b - x_0}{n}$
> 2. **Podstawiamy $\eta_0$:**
>    - $\eta_0 = y_0$
> 3. **Dla $i \in \{0, 1, \dots, n-1\}$ liczymy:**
>    - $\eta_{i+1} = \eta_i + h \cdot f(x_i, \eta_i)$
>    - $x_{i+1} = x_i + h$
> 4. **Wynik:**
>    - Pary $(x_i, \eta_i)$ dla $i \in \{0, \dots, n\}$
## Metody rzędu drugiego
Metoda Eulera jest przykładem metody jednokrotnej (czyli do obliczenia $\eta_{i_+1}$ wykorzystujemy tylko jedną wartość $\eta_{i}$).

Niech $(x,y)$ będzie dowolnym punktem, a $z=z(t)$ będzie dokładnym rozwiązaniem zagadnienia początkowego:$$\begin{cases}z'=f(t,z)\\z(x)=y\end{cases}$$
Wówczas funkcja $\Delta$, dana wzorem:$$\Delta(x,y,h,f)=\begin{cases} \frac{z(x+h)-y}{h}, \quad h\neq 0  \\ f(x,y), \quad h=0\end{cases}$$przedstawia iloraz różnicowy rozwiązania dokładnego $z(t)$ zagadnienia początkowego dla kroku $h$. Funkcja $\Phi=\Phi(x,y,h,f)$ jest ilorazem różnicowym dla rozwiązania przybliżonego $\eta$ dla kroku $h$.

Błąd $\tau$, dany wzorem:
$$\tau=\Delta(x,y,h,f)-\Phi(x,y,h,f)$$
nazywamy lokalnym błędem dyskretyzacji. Wymagamy aby $\lim_{ h \to 0 }\tau=0$.

Przez $F_{n}(a,b)$ będziemy oznaczać zbiór funkcji $f$ dla których istnieją wszystkie pochodne cząstkowe aż do rzędu $N$ włącznie, są one ciągłe i ograniczone w pasie:
$$S=\set{(x,y) : x\in[a,b] \land y,a,b\in\mathbb{R}}$$
Będziemy mówić, że metoda jest rzędu $p$, jeśli spełniona jest równość asymptotyczna:
$$τ=\mathcal{O}(h^p)$$
Metody wyższych rzędów możemy otrzymać przyjmując funkcję:
$$\Phi(x,y,h,f)=a_{1}f(x,y)+a_{2}(x+p_{1}h,  y+p_{2}hf(x,y))$$
gdzie $a_{1},a_{2}$ muszą spełniać warunki:
$$\begin{cases}
a_{1}+a_{2}=1 \\
a_{2}p_{1}=\frac{1}{2} \\
a_{2}p_{2}=\frac{1}{2}
\end{cases}$$

Odpowiednio dobierając współczynniki $a_{1},a_{2}$ możemy uzyskać różne metody wyższych rzędów.
### Metoda Heuna
Otrzymujemy ją przyjmując $a_1 = a_2 = \frac{1}{2}$ oraz $p_1 = p_2 = 1$. Jest to metoda rzędu $p=2$.

Wzór ogólny:
$$ \begin{cases} \eta_0 = y_0 \\ \eta_{i+1} = \eta_i + \frac{h}{2} \left[ f(x_i, \eta_i) + f(x_{i+1}, \eta_i + h f(x_i, \eta_i)) \right] \\ x_{i+1} = x_i + h \end{cases} $$

> [!abstract] Algorytm metody Heuna
> 0. **Dane:**
>    - Funkcja $f$, wartości $x_0, y_0,n,b$
> 1. **Wyznaczamy $h$:**
>    - $h = \frac{b - x_0}{n}$
> 2. **Podstawiamy $\eta_0$:**
>    - $\eta_0 = y_0$
> 3. **Dla $i \in \{0, 1, \dots, n-1\}$ liczymy:**
>    - $x_{i+1} = x_i + h$
>    - $m_i = f(x_i, \eta_i)$
>    - $k_i = f(x_{i+1}, \eta_i + h m_i)$
>    - $\eta_{i+1} = \eta_i + \frac{h}{2}(m_i + k_i)$
> 4. **Wynik:**
>    - $(x_i, \eta_i)$

### Zmodyfikowana metoda Eulera
Otrzymujemy ją dobierając współczynniki tak, by $a_1 = 0, a_2 = 1, p_1 = p_2 = \frac{1}{2}$. Jest to również metoda drugiego rzędu.

Wzór ogólny:
$$ \begin{cases} \eta_0 = y_0 \\ \eta_{i+1} = \eta_i + h f(x_i + \frac{1}{2}h, \eta_i + \frac{1}{2}h f(x_i, \eta_i)) \\ x_{i+1} = x_i + h \end{cases} $$

> [!abstract] Algorytm zmodyfikowanej metody Eulera
> 0. **Dane:**
>    - Funkcja $f$, wartości $x_0, y_0,n,b$
> 1. **Wyznaczamy $h$:**
>    - $h = \frac{b - x_0}{n}$
> 2. **Podstawiamy $\eta_0$:**
>    - $\eta_0 = y_0$
> 3. **Dla $i \in \{0, 1, \dots, n-1\}$ liczymy:**
>    - $x_{i+1} = x_i + h$
>    - $m_i = f(x_i, \eta_i)$
>    - $k_i = f(x_i + \frac{1}{2}h, \eta_i + \frac{1}{2}h m_i)$
>    - $\eta_{i+1} = \eta_i + h \cdot k_i$
> 4. **Wynik:**
>    - $(x_i, \eta_i)$

