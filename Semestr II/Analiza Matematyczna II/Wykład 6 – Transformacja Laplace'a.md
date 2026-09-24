## Oryginał
Funkcję $f: \mathbb{R} \to \mathbb{R}$ nazywamy oryginałem, gdy:
* $f$ jest kawałkami ciągła i monotoniczna (istnieje skończenie wiele przerw).
* $f(x) = 0$ dla $x < 0$.
* $f$ jest rzędu wykładniczego, czyli $|f(x)| \le M \cdot e^{\lambda \cdot x}$ dla $x \ge 0$ (inaczej mówiąc, funkcja rośnie wolniej niż dowolna funkcja w postaci $M \cdot e^{\lambda \cdot x}$).
## Transformacja Laplace'a
Transformacja Laplace'a jest przekształceniem funkcji czasu $f(t)$ (stąd zasada, że $f(x) = 0$ dla $x < 0$, czas zawsze liczymy od 0) na funkcję zespoloną $F(s)$, gdzie $s \in \mathbb{C}$.

Niech $f: \mathbb{R} \to \mathbb{R}(\mathbb{C})$ będzie oryginałem. Transformatą Laplace'a funkcji $f$ dla argumentu $s \in \mathbb{C}$ nazywamy:
$$ \mathcal{L}[f](s) = \int_{0}^{\infty} f(t) \cdot e^{-st} \, dt $$

> [!example] Wyprowadzenie transformaty Laplace'a dla funkcji $f(x) = \begin{cases} 1, & x \ge 0 \\ 0, & x < 0 \end{cases}$
> $$ \mathcal{L}[f] = \int_{0}^{\infty} 1 \cdot e^{-sx} \, dx = \lim_{A \to \infty} \int_{0}^{A} e^{-sx} \, dx = \lim_{A \to \infty} \left[-\frac{1}{s} \cdot e^{-sx}\right]_{0}^{A} = $$
> $$ = \lim_{A \to \infty} \left[-\frac{e^{-sA}}{s} + \frac{e^0}{s}\right] = \lim_{A \to \infty} \left[-\frac{1}{e^{sA}s} + \frac{1}{s}\right] = \frac{1}{s}, \quad \text{dla } \mathfrak{R}(s) > 0 $$

Chcąc wyprowadzić transformatę Laplace'a funkcji $f$, często odgórnie zakłada się, że funkcja $f$ jest funkcją czasu:
$$ f(x) = \begin{cases} h(x), & x \ge 0 \\ 0, & x < 0 \end{cases} $$
## Tabela transformat Laplace'a

| Funkcja           | Transformata $\mathcal{L}$             |
| :---------------- | :------------------------------------- |
| $y(x)$            | $Y(s)$                                 |
| $\delta(x)$       | $1$                                    |
| $1(x)$            | $\frac{1}{s}$                          |
| $x^n$             | $\frac{n!}{s^{n+1}}$                   |
| $e^{ax} x^n$      | $\frac{n!}{(s-a)^{n+1}}$               |
| $e^{ax}$          | $\frac{1}{s-a}$                        |
| $\sin(bx)$        | $\frac{b}{s^2 + b^2}$                  |
| $\cos(bx)$        | $\frac{s}{s^2 + b^2}$                  |
| $e^{ax} \sin(bx)$ | $\frac{b}{(s-a)^2 + b^2}$              |
| $e^{ax} \cos(bx)$ | $\frac{s-a}{(s-a)^2 + b^2}$            |
| $f'(x)$           | $s \cdot \mathcal{L}[f(x)] - f(0^{+})$ |
## Funkcje specjalne
* **Funkcja wskaźnikowa:** Funkcja $\mathbb{1}(t)$ jest funkcją wskaźnikową:
  $$ \mathbb{1}_A(t) = \begin{cases} 1, & t \in A \\ 0, & t \notin A \end{cases} $$
  Dla transformat Laplace'a przyjmujemy, że $A = [0, \infty)$, więc $\mathbb{1}(t) = \begin{cases} 1, & t \ge 0 \\ 0, & t < 0 \end{cases}$.
* **Delta Diraca:** $\delta(t)$ jest reprezentacją nieskończenie krótkiego impulsu o całkowitej powierzchni równej 1:
  $$ \int_{-\infty}^{\infty} \delta(t) \, dt = 1 \land \delta(t) = \begin{cases} 0, & t \neq 0 \\ \infty, & t = 0 \end{cases} $$

## Własności transformat Laplace'a
* **Pochodne:**  $$ \mathcal{L}[f'(t)] = s \cdot \mathcal{L}[f(t)] - f(0^{+}) $$
  *(Ponieważ: $\mathcal{L}[f'(t)] = \int_{0}^{\infty} f'(t)e^{-st} \, dt = [f(t) \cdot e^{-st} - \int f(t)e^{-st} \cdot (-s) \, dt]_0^\infty = -f(0^{+}) + s\mathcal{L}[f(t)]$)*.
* **Liniowość:**   $$ \mathcal{L}[\alpha f(t) + \beta g(t)] = \alpha \mathcal{L}[f(t)] + \beta \mathcal{L}[g(t)] $$
## Odwrotna transformacja Laplace'a
Transformatą odwrotną do transformaty Laplace'a jest transformata $\mathcal{L}^{-1}$, opisywana wzorem:
$$ \mathcal{L}^{-1}[F(s)](t) = \frac{1}{2\pi i} \int_{c-\infty i}^{c+\infty i} F(s)e^{st} \, ds, \quad t > 0 $$
## Zastosowania transformacji Laplace'a
Transformacja Laplace'a pozwala na szybsze i skuteczniejsze obliczanie problemów Cauchy'ego (równań różniczkowych z warunkami początkowymi).

> [!example] Przykład zastosowania
> Oblicz $y' + y = 1$ z warunkiem początkowym $y(0) = 2$:
> 1. Obustronnie nakładamy transformatę: $\mathcal{L}[y' + y] = \mathcal{L}[1]$
> 2. Korzystamy z liniowości: $\mathcal{L}[y'] + \mathcal{L}[y] = \mathcal{L}[1]$
> 3. Podstawiamy własność pochodnej: $s\mathcal{L}[y] - y(0) + \mathcal{L}[y] = \frac{1}{s}$
> 4. Podstawiamy warunek początkowy $y(0) = 2$ oraz oznaczamy $Y(s) = \mathcal{L}[y]$:
>    $$ s \cdot Y(s) - 2 + Y(s) = \frac{1}{s} $$
> 5. Wyznaczamy $Y(s)$:
>    $$ Y(s)(s + 1) = \frac{1}{s} + 2 \implies Y(s) = \frac{1 + 2s}{s(s+1)} $$
> 6. Rozkładamy na ułamki proste i dopasowujemy transformaty odwrotne:
>    $$ Y(s) = \frac{s + s + 1}{s(s+1)} = \frac{1}{s+1} + \frac{1}{s} = \mathcal{L}[e^{-x}] + \mathcal{L}[\mathbb{1}(x)] $$
> 7. Otrzymujemy rozwiązanie:
>    $$ y = e^{-x} + 1 $$