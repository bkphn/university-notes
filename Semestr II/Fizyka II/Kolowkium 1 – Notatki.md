## Pomiar pośredni i prawo propagacji niepewności
W przypadku, gdy mamy do czynienia z pomiarem pośrednim (wyznaczanym z innych pomiarów), jego niepewność jest zależna od niepewności pomiarów składowych. 

Prawo propagacji niepewności opisuje się wzorem:
> $$ u(y) = \sqrt{\sum_{i=1}^{n} \left[\frac{\partial y}{\partial x_i} \cdot u(x_i)\right]^2} $$
Gdzie $x_i$ to $i$-ty pomiar bezpośredni, $u(x_i)$ to niepewność tego pomiaru, a $n$ to ilość pomiarów pośrednich. W zadaniu liczymy pochodne po kolejnych pomiarach bezpośrednich, mnożymy przez ich niepewność i sumujemy.

> [!example] Przykład obliczenia niepewności $u(E)$
> Dla wzoru $E = \frac{4L}{\pi a d^2}$ i znanych niepewności $u(d), u(L), u(a)$:
> $$ u(E) = \sqrt{\left[\frac{\partial E}{\partial d} \cdot u(d)\right]^2 + \left[\frac{\partial E}{\partial L} \cdot u(L)\right]^2 + \left[\frac{\partial E}{\partial a} \cdot u(a)\right]^2} $$
> Obliczone pochodne cząstkowe:
> * $\frac{\partial E}{\partial d} = \frac{\partial}{\partial d}\left(\frac{4L}{\pi a} \cdot \frac{1}{d^2}\right) = \frac{4L}{\pi a} \cdot \frac{-2}{d^3} = -\frac{8L}{\pi a d^3}$
> * $\frac{\partial E}{\partial L} = \frac{\partial}{\partial L}\left(\frac{4}{\pi a d^2} L\right) = \frac{4}{\pi a d^2}$
> * $\frac{\partial E}{\partial a} = \frac{\partial}{\partial a}\left(\frac{4L}{\pi d^2} \cdot \frac{1}{a}\right) = \frac{4L}{\pi d^2} \cdot \frac{-1}{a^2} = -\frac{4L}{\pi a^2 d^2}$
## Przydatne pochodne

| Funkcja             | Pochodna                               |
| :------------------ | :------------------------------------- |
| $c$ (stała)         | $0$                                    |
| $x$                 | $1$                                    |
| $x^n$               | $n \cdot x^{n-1}$                      |
| $c \cdot f(x)$      | $c \cdot f'(x)$                        |
| $\sin x$            | $\cos x$                               |
| $\cos x$            | $-\sin x$                              |
| $\frac{1}{x}$       | $-\frac{1}{x^2}$                       |
| $\sqrt{x}$          | $\frac{1}{2\sqrt{x}}$                  |
| $a^x$               | $a^x \cdot \ln a$                      |
| $\frac{f(x)}{g(x)}$ | $\frac{f'(x)g(x) - f(x)g'(x)}{g^2(x)}$ |
| $f(x) \cdot g(x)$   | $f'(x)g(x) + f(x)g'(x)$                |
## Zapis wyników końcowych z niepewnościami
Znając wyniki pomiarów wraz z niepewnościami, musimy zapisać wynik w jednym z odpowiednich formatów:
* **Format symboliczny:** $T = 1.2867\text{ s}; \, u(T) = 0.0035\text{ s}$
* **Format skrócony:** $T = 1.2867(35)\text{ s}$
* **Notacja naukowa lub wykładnicza** (dla bardzo dużych lub bardzo małych liczb):
  * Zapis naukowy: $T = 12867(35)\text{E}5\text{ s}$
  * Zapis wykładniczy: $T = 12867(25) \cdot 10^5\text{ s}$
## Test zgodności
Należy dokonać testu zgodności dla dwóch wartości (jedna z nich może być zmierzona, bądź odczytana z tabeli).
### 1. Zgodność z wartością dokładną
Wartości uważamy za zgodne, jeśli spełniony jest warunek:
$$ |x - x_0| < U(x) $$
Gdzie $x$ to wartość zmierzona, $x_0$ to wartość dokładna, a $U(x)$ to niepewność rozszerzona definiowana wzorem $U(x) = 2 \cdot u(x)$.
### 2. Zgodność dwóch zmierzonych wartości
Wartości uważamy za zgodne, jeśli spełniony jest warunek:
$$ |x_1 - x_2| < U(x_1 - x_2) $$
Gdzie $x_1, x_2$ to wartości zmierzone, a $U(x_1 - x_2)$ to niepewność rozszerzona definiowana wzorem:
$$ U(x_1 - x_2) = 2 \cdot \sqrt{u^2(x_1) + u^2(x_2)} $$
> [!example] Ocena zgodności prędkości dźwięku $v_1, v_2$
> Dane:
> $$ v_1 = 343.5\frac{\text{m}}{\text{s}}, \, u(v_1) = 1.5\frac{\text{m}}{\text{s}}, \quad v_2 = 339.4\frac{\text{m}}{\text{s}}, \, u(v_2) = 2.2\frac{\text{m}}{\text{s}} $$
> Sprawdzamy warunek zgodności:
> $$ |v_1 - v_2| < U(v_1 - v_2) $$
> $$ |343.5 - 339.4| < 2 \cdot \sqrt{(1.5)^2 + (2.2)^2} $$
> $$ 4.1 < 5.3254\dots $$
> Wartości są zgodne.
