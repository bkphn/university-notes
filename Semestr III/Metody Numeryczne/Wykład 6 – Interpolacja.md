## Sformułowanie zagadnienia
Dane jest $n+1$ różnych punktów $x_0, x_1, \dots, x_n$ z przedziału $[a, b]$; punkty te nazywamy węzłami interpolacji. Niech będą znane wartości pewnej funkcji $f$ w tych węzłach: $y_0 = f(x_0), \dots, y_n = f(x_n)$.

Zadanie interpolacji polega na wyznaczeniu funkcji $F$ (z zadanej klasy), której wykres będzie przechodził przez punkty $(x_0, y_0), \dots, (x_n, y_n)$. Funkcję $F$ nazywamy funkcją interpolacyjną. Najczęściej poszukuje się jej w postaci wielomianu algebraicznego, wielomianu trygonometrycznego lub funkcji sklejanej (splajnu).
## Interpolacja wielomianowa
Poszukujemy wielomianu $W_n(x) = a_0 + a_1x + \dots + a_nx^n$ stopnia co najwyżej $n$, spełniającego warunki $W_n(x_i) = y_i$ dla $i \in \{0, 1, \dots, n\}$.
Istnieje dokładnie jeden taki wielomian. Współczynniki $a_i$ można wyznaczyć z układu równań $\mathbf{Xa} = \mathbf{y}$, gdzie:
$$ \mathbf{X} = \begin{bmatrix} x_0^0=1 & \dots & x_0^n \\ \vdots & \vdots & \vdots \\ x_n^0=1 & \dots & x_n^n \end{bmatrix}, \quad \mathbf{a} = \begin{bmatrix} a_0 \\ \vdots \\ a_n \end{bmatrix}, \quad \mathbf{y} = \begin{bmatrix} y_0 \\ \vdots \\ y_n \end{bmatrix} $$
Z twierdzenia Cramera układ ten ma jednoznaczne rozwiązanie, a współczynniki oblicza się ze wzoru:
$$ a_i = \frac{1}{\det \mathbf{X}} \sum_{j=0}^n y_j D_{ji} $$
gdzie $D_{ji}$ to kolejne dopełnienia algebraiczne elementów $x_{ij}$.
## Wzór interpolacyjny Lagrange'a
Zamiast rozwiązywać układ równań, wielomian interpolacyjny można zapisać w postaci:
$$ W_n(x) = \sum_{i=0}^n y_i \Phi_i(x) $$
Wielomiany $\Phi_i$ stopnia co najwyżej $n$ muszą spełniać warunek $\Phi_i(x_j) = \delta_{ij}$ (gdzie $\delta_{ij} = 1$ dla $i=j$ oraz $0$ dla $i \ne j$). 
Po odpowiednich przekształceniach wzór na $\Phi_i$ przyjmuje postać:
$$ \Phi_i(x) = \prod_{k \in \{0, \dots, n\} \setminus \{i\}} \frac{x - x_k}{x_i - x_k} $$

**Oszacowanie błędu interpolacji:**
$$ R_n(x) = |f(x) - W_n(x)| \le \frac{M_{n+1}}{(n+1)!} |\omega_n(x)| $$
gdzie $M_{n+1} = \sup_{t \in [a, b]} |f^{(n+1)}(t)|$ oraz $\omega_n(x) = \prod_{i=0}^n (x - x_i)$.

> [!abstract] Algorytm interpolacji Lagrange'a
> 0. **Dane**
>    - Węzły $\{x_0, \dots, x_n\}$
>    - Wartości $\{y_0, \dots, y_n\}$
> 1. **Dla $i \in \{0, 1, \dots, n\}$ wyznaczamy $\Phi_i$**
>    - $\Phi_i(x) = \prod_{k \in \{0, \dots, n\} \setminus \{i\}} \frac{x - x_k}{x_i - x_k}$
> 2. **Wyznaczamy $W_n(x)$**
>    - $W_n(x) = \sum_{i=0}^n y_i \Phi_i(x)$
> 3. **Wynik**
>    - $W_n(x) = y_0\Phi_0(x) + \dots + y_n\Phi_n(x)$
## Interpolacja splajnami (funkcjami sklejanymi)
Przez $\Delta_n$ oznaczamy podział odcinka $[a, b]$ wyznaczony przez $n+1$ punktów: $a = x_0 < x_1 < \dots < x_{n-1} < x_n = b$.
Funkcję $S: [a, b] \rightarrow \mathbb{R}$ nazywamy splajnem stopnia $m$, jeżeli:
* jest wielomianem stopnia co najwyżej $m$ na każdym z podprzedziałów $[x_i, x_{i+1}]$,
* $S \in C^{m-1}[a, b]$ (jest ciągła wraz z pochodnymi aż do rzędu $m-1$ w całym przedziale).

Na podprzedziale splajn $S(x)$ dany jest przez $m+1$ współczynników. Wymaga to dodatkowych $m-1$ równań na końcach przedziału (np. znajomości wartości pochodnych). Najczęściej używa się **splajnów sześciennych (stopnia trzeciego)** ze względu na optymalny kompromis między gładkością a nakładem pracy komputera.
## Splajny sześcienne
Splajn $S \in \mathcal{S}_3(\Delta_n)$ dla całego przedziału $[a, b]$ można opisać uniwersalnym wzorem:
$$ S(x) = a_0 + a_1x + a_2x^2 + a_3x^3 + \beta_1(x-x_1)_+^3 + \dots + \beta_{n-1}(x-x_{n-1})_+^3 $$
gdzie funkcja „uciętej potęgi” definiowana jest jako:
$$ (x-x_i)_+^3 = \begin{cases} 0, & x \le x_i \\ (x-x_i)^3, & x > x_i \end{cases} $$

Warunki interpolacyjne $S(x_i) = y_i$ dają nam układ $n+1$ równań, a niewiadomych mamy $n+3$. Dwa brakujące równania ustala się jako warunki brzegowe, najczęściej na drugie pochodne. Jeżeli przyjmiemy $S''(x_0) = S''(x_n) = 0$, mówimy o **splajnie naturalnym**.

> [!abstract] Algorytm wyznaczania splajnu sześciennego
> 0. **Dane**
>    - Argumenty $\{x_0, \dots, x_n\}$
>    - Wartości $\{y_0, \dots, y_n\}$
>    - Wartości pochodnych brzegowych (przyjmujemy $S''(x_0) = S''(x_n) = 0$, jeśli nie podano inaczej)
> 1. **Wyznaczenie splajnu**
>    - Wzór ogólny na sumę członów $(x-x_i)_+^3$
> 2. **Wyznaczenie pochodnych splajnu**
>    - Wyznaczamy odpowiednio równania na pierwszą lub drugą pochodną funkcji uciętej potęgi
> 3. **Budujemy układ równań**
>    - Równania na węzły wewnętrzne: $S(x_i) = y_i$
>    - Równania na węzły brzegowe: $S^{(p)}(x_i) = s^{(p)}(x_i)$
> 4. **Rozwiązujemy układ równań**
>    - Wyliczamy współczynniki $a_k$ oraz $\beta_k$
> 5. **Wynik**
>    - Postać ostateczna z wyliczonymi stałymi
### Wyznaczanie splajnów sześciennych przez wartości drugich pochodnych
Splajn sześcienny możemy również konstruować z podziałem na lokalne funkcje $S_i(x)$ na przedziałach $[x_i, x_{i+1}]$. 
Oznaczmy $z_i = S''(x_i)$ oraz $h_i = x_{i+1} - x_i$. Z postaci drugiej pochodnej po dwukrotnym scałkowaniu i uwzględnieniu warunków interpolacyjnych, otrzymujemy:
$$ S_i(x) = \frac{z_i}{6h_i}(x_{i+1} - x)^3 + \frac{z_{i+1}}{6h_i}(x - x_i)^3 + \left(\frac{y_{i+1}}{h_i} - \frac{z_{i+1}h_i}{6}\right)(x - x_i) + \left(\frac{y_i}{h_i} - \frac{z_ih_i}{6}\right)(x_{i+1} - x) $$
Wartości $z_i$ należy wyznaczyć z układu trójdiagonalnego $\mathbf{U}\mathbf{z} = \mathbf{v}$.

> [!abstract] Algorytm wyznaczania splajnów przez drugie pochodne
> 0. **Dane**
>    - Argumenty $\{x_0, \dots, x_n\}$
>    - Wartości $\{y_0, \dots, y_n\}$
> 1. **Wyznaczenie wartości początkowych**
>    - $h_0 = x_1 - x_0$
>    - $b_0 = \frac{6}{h_0}(y_1 - y_0)$
> 2. **Dla $i \in \{1, \dots, n-1\}$ liczymy:**
>    - $h_i = x_{i+1} - x_i$
>    - $b_i = \frac{6}{h_i}(y_{i+1} - y_i)$
>    - $u_i = 2(h_i + h_{i-1})$
>    - $v_i = b_i - b_{i-1}$
> 3. **Budujemy układ równań**
>    - Konstruujemy trójdiagonalną macierz $\mathbf{U}$ ze stałymi $u_i$ i $h_i$
>    - Konstruujemy wektory $\mathbf{z}$ oraz $\mathbf{v}$
> 4. **Rozwiązujemy układ równań $\mathbf{U}\mathbf{z} = \mathbf{v}$**
> 5. **Dla $i \in \{0, 1, \dots, n-1\}$ wyznaczamy splajny**
>    - Podstawiamy wyliczone $z_i$ do wzoru na $S_i(x)$
> 6. **Wynik**
>    - Kompletna funkcja sklejana $S(x)$ złożona z lokalnych $S_i(x)$

