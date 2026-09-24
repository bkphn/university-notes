## Pole pod wykresem
Dzieląc figurę powstałą pod wykresem na małe odcinki, jesteśmy w stanie policzyć jej pole jako sumę wszystkich takich mniejszych pól. Każdy taki odcinek kończy się w punkcie $(x_k, 0)$, więc kolejne długości podstawy takich figur są równe $x_k - x_{k-1}$. Korzystając ze wzoru na sumę, jesteśmy w stanie wyznaczyć przybliżone pole: $$ \sum_{k=1}^{n} (x_k - x_{k-1}) \cdot f(t_k), \quad t_k \in \langle x_{k-1}, x_k \rangle $$Dzieląc taki wykres na nieskończenie małe kawałki, jesteśmy w stanie wyznaczyć dokładne pole takiej figury. Sumę tych wszystkich kawałków wyznacza całka oznaczona z funkcji $f$ po określonym przedziale: $$ \int_{a}^{b} f(x) \, dx $$
## Funkcja signum
Funkcja signum jest funkcją zwracającą wartość $1$ dla argumentów dodatnich, wartość $-1$ dla ujemnych argumentów oraz wartość $0$ dla argumentu równego $0$.
$$ \operatorname{sgn}(x) = \begin{cases} -1, & x < 0 \\ 0, & x = 0 \\ 1, & x > 0 \end{cases} $$

> [!example] Przykład obliczeniowy
> Oblicz całkę oznaczoną z przedziału $\langle -1, 1 \rangle$ funkcji signum:
> $$ \int_{-1}^{1} \operatorname{sgn}(x) \, dx = \int_{-1}^{0} \operatorname{sgn}(x) \, dx + \int_{0}^{1} \operatorname{sgn}(x) \, dx = \int_{-1}^{0} -1 \, dx + \int_{0}^{1} 1 \, dx = [-x]_{-1}^{0} + [x]_0^1 = [-1 + 0] + [0 + 1] = -1 + 1 = 0 $$
> Przykład ten pokazuje, że funkcja nie musi być ciągła, by była całkowalna, jednak ilość punktów ciągłości musi być policzalna.
## Operacje na całkach oznaczonych
$$\int_{a}^{b} (f(x) + g(x)) \, dx = \int_{a}^{b} f(x) \, dx + \int_{a}^{b} g(x) \, dx$$
$$\int_{a}^{b} r \cdot f(x) \, dx = r \cdot \int_{a}^{b} f(x) \, dx$$
$$\int_{a}^{c} f(x) \, dx = \int_{a}^{b} f(x) \, dx + \int_{b}^{c} f(x) \, dx, \quad a < b < c$$
## Wzór Newtona-Leibniza
Podstawowe twierdzenie rachunku całkowego mówi, że jeżeli funkcja $f: \langle a, b \rangle \to \mathbb{R}$ jest ciągła, to $G(x) = \int_{a}^{x} f(t) \, dt$ ma pochodną i $G'(x) = f(x)$. Z tego wynika wzór Newtona-Leibniza, który mówi o tym, że:
$$ \int_{a}^{b} f(x) \, dx = F(b) - F(a), \quad F' = f $$
## Całkowanie przez podstawienie
Podobnie jak całki nieoznaczone, oznaczone też możemy całkować przez podstawienie, trzeba jednak pamiętać o zmianie zakresu całki:
$$ \int_{a}^{b} \varphi(x) \cdot f(\varphi'(x)) \, dx = \int_{\varphi(a)}^{\varphi(b)} f(t) \, dt $$

> [!example] Przykład
> Oblicz całkę oznaczoną z przedziału $(0, 2)$ funkcji $x \cdot \cos(x^2)$.
> $$ \int_{0}^{2} \cos(x)x \, dx = \begin{vmatrix} t = x^2 \\ dt = 2x \, dx \\ x = 0 \implies t = 0 \\ x = 2 \implies t = 4 \end{vmatrix} = \int_{2}^{4} \cos(t) \cdot \frac{1}{2} \, dt = \dots $$
> $$ \int_{0}^{2} \frac{\varphi'(x)}{2} \cdot \cos(\varphi(x)) \, dx = \int_{\varphi(2)}^{\varphi(2)} \cos(t) \, dt $$
> W tym wypadku $\varphi(x) = x^2$, $f(x) = \cos(x)$.
## Całkowanie przez części
Całkę oznaczoną możemy również całkować przez części w następujący sposób:
$$ \int_{a}^{b} u(x) \cdot v'(x) \, dx = \begin{bmatrix} u & v' \\ u' & v \end{bmatrix} = [u \cdot v]_a^b - \int_{a}^{b} u'(x) \cdot v(x) \, dx $$

> [!example] Przykład
> Oblicz całkę oznaczoną z przedziału $(0, \pi)$ funkcji $x^2 \cdot \sin x$.
> $$ \int_{0}^{\pi} x^2 \sin x \, dx = \begin{vmatrix} u(x) = x^2 & v'(x) = \sin x \\ u'(x) = 2x & v(x) = -\cos x \end{vmatrix} = [-x^2 \cos x]_0^\pi - \int_{0}^{\pi} -2x \cos x \, dx = \dots $$