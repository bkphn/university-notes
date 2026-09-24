## Równanie różniczkowe niejednorodne
Równanie różniczkowe niejednorodne to równanie postaci $y' + f(x)y = h(x)$, którego nie da się uporządkować tak jak równania o zmiennych rozdzielonych.
* **CORN** – Całka Ogólna Równania Niejednorodnego
* **CORJ** – Całka Ogólna Równania Jednorodnego
* **CSRN** – Całka Szczególna Równania Niejednorodnego
## Metoda uzmienniania stałej
Pierwszym sposobem jest uzmiennianie stałej: na początku liczymy CORJ, następnie uzmienniamy i wyznaczamy stałą oraz podstawiamy ją do równania.

> [!abstract] Schemat rozwiązania
> 1. **Uporządkować elementy**, by otrzymać równanie, gdzie wszystkie funkcje zawierające $y$ będą po jednej stronie: $y' + f(x) \cdot y = h(x)$.
> 2. **Podstawiając pod $h(x)$ liczbę 0**, tworzymy równanie o zmiennych rozdzielonych: $y' + f(x) \cdot y = 0$.
> 3. **Z tego równania wyznaczamy $y$** (CORJ): $y = F(x) \cdot c$.
> 4. **Uzmienniamy stałą**, czyli ze stałej $c$ tworzymy funkcję zależną od $x$, $c(x)$: $y = F(x) \cdot c(x)$.
> 5. **Obliczamy pochodną $y'$**, potrzebną do podstawienia pod równanie wyjściowe: $y' = F'(x) \cdot c(x) + F(x) \cdot c'(x)$.
> 6. **Podstawiamy wyznaczone $y, y'$** pod równanie początkowe: $y' + f(x) \cdot y = h(x) \implies (F'(x) \cdot c(x) + F(x) \cdot c'(x)) + f(x) \cdot (F(x) \cdot c(x)) = h(x)$.
> 7. **Upraszczamy równanie** – jeżeli wszystko zrobiliśmy dobrze, to $c(x)$ powinno nam się skrócić: $c'(x) \cdot F(x) = h(x)$.
> 8. **Wyznaczamy funkcję pierwotną $c(x)$**: $c'(x) = \frac{h(x)}{F(x)} \implies c(x) = \int \frac{h(x)}{F(x)} \, dx \implies c(x) = H(x) + C$.
> 9. **Podstawiamy funkcję $c(x)$** pod równanie $y$ z punktu 4 (tam gdzie uzmienniliśmy $c$): $y = F(x) \cdot (H(x) + C)$.
## Metoda przewidywań
Drugim sposobem jest metoda przewidywań. Jest ona prostsza od metody uzmienniania stałej, jednak nie w każdym przypadku możliwe jest jej zastosowanie. Rozwiązaniem takiego równania jest CORN, którą wyznaczamy następująco:
$$ \text{CORN} = \text{CORJ} + \text{CSRN} $$
W zależności od tego, jaką funkcję niezależną od $y$ mamy w równaniu, nasza CSRN będzie wyglądała inaczej. Dla równania $y' + f(x) \cdot y = h(x)$ mamy:

| Funkcja                                           | Przewidywana CSRN                                 | Uwagi                                                                                            |
| :------------------------------------------------ | :------------------------------------------------ | :----------------------------------------------------------------------------------------------- |
| Wielomian $n$-tego stopnia zmiennej $x$           | Inny wielomian $n$-tego stopnia zmiennej $x$      | Jeżeli rozwiązanie nie zadziała, to próbujemy $\text{CSRN} = y \cdot x$                          |
| W postaci $a e^{bx}$                              | W postaci $A \cdot e^{bx}$                        | Jeżeli rozwiązanie nie zadziała, to próbujemy $\text{CSRN} = y \cdot x$                          |
| $l \cdot \sin(\omega x) + b \cdot \cos(\omega x)$ | $A \cdot \sin(\omega x) + B \cdot \cos(\omega x)$ | Współczynniki $a$ lub $b$ mogą być równe 0, wtedy i tak CSRN będzie się składać z dwóch funkcji. |
| Suma powyższych $h(x)$                            | Suma powyższych CSRN                              |                                                                                                  |

> [!abstract] Schemat rozwiązania
> 1. **Uporządkować elementy**, by otrzymać równanie, gdzie wszystkie funkcje zawierające $y$ będą po jednej stronie: $y' + f(x) \cdot y = h(x)$.
> 2. **Obliczamy CORJ**, przyrównując lewą stronę do zera: $y' + f(x) \cdot y = 0$.
> 3. **Z tego równania wyznaczamy $y$**, czyli naszą CORJ: $\text{CORJ} = y_1 = F(x) \cdot c$.
> 4. **Metodą przewidywań przewidujemy**, jak będzie wyglądała CSRN dla $h(x)$, np. $y = Ax + B$.
> 5. **Obliczamy pochodną $y'$**, potrzebną do wyznaczenia skalarów $A, B$: $y' = A$.
> 6. **Podstawiamy do równania** i za pomocą układu równań wyznaczamy wartości $A, B$.
> 7. **Podstawiamy wartości $A, B$**, by uzyskać CSRN: $\text{CSRN} = y_2 = A_1x + B_1$.
> 8. **Wyznaczamy CORN** – rozwiązanie naszego zadania: $\text{CORN} = \text{CORJ} + \text{CSRN} = y_1 + y_2 \implies y = C \cdot F(x) + A_1x + B_1$.

> [!example] Przykład
> Oblicz $y' - y = x + e^x$:
> 1. $y' - y = x + e^x$
> 2. **CORJ**: $y' - y = 0 \implies y' = y \implies \frac{dy}{dx} = y \implies \int \frac{1}{y} \, dy = \int dx \implies \ln|y| = x + c \implies y = e^x \cdot e^c \implies y = ce^x$
> 3. **CSRN**: Dla $h(x) = x + e^x$ przewidujemy rozwiązanie. Ponieważ $e^x$ występuje już w CORJ, próbujemy z czynnikiem $x$: $y = Ax + B + Cxe^x$.
> 4. Po zróżnicowaniu $y' = A + Cxe^x + Ce^x$ i podstawieniu do równania wyjściowego otrzymujemy układ dla współczynników:
>    $$ \begin{cases} A - B = 0 \implies A = -1, B = -1 \\ Ce^x = e^x \implies C = 1 \\ -Ax = x \implies A = -1 \end{cases} $$
>    Co daje szczególną całkę: $y = xe^x - x - 1$.
> 5. **CORN**: $y = ce^x + xe^x - x - 1$.
## Równania różniczkowe skalarne wyższych rzędów
Równanie różniczkowe wyższych rzędów to liniowe równanie skalarne o następującej postaci:
$$ y^{(n)} + a_{n-1} \cdot y^{(n-1)} + \dots + a_2 \cdot y'' + a_1 \cdot y' + a_0 \cdot y = h(x) $$
gdzie $a_n$ to skalary, a $h$ jest funkcją $x$.

Każde równanie różniczkowe skalarne $n$-tego rzędu posiada dokładnie $n$ pierwiastków, a wzór ogólny na CORJ wygląda następująco:
$$ y = C_1 e^{r_1 x} + C_2 e^{r_2 x} + \dots + C_n e^{r_n x} $$
Jednak jeżeli mamy do czynienia z pierwiastkami dwukrotnymi, trzykrotnymi itd., to każdy element zawierający taki pierwiastek mnożymy przez $x$. Jeżeli więc mamy równanie IV rzędu i $r_1 = r_2 = r_3$, to:
$$ y = C_1 e^{r_1 x} + C_2 x e^{r_2 x} + C_3 x^2 e^{r_3 x} + C_4 e^{r_4 x} $$

Jeżeli $r \in \mathbb{C}$ (pierwiastki zespolone), zakładając, że $r_1 = a + bi$ oraz $r_2 = a - bi$, możemy rozbić wzór ogólny na postać trygonometryczną:
$$ y = C_1 e^{(a+bi)x} + C_2 e^{(a-bi)x} = C_1 e^{ax} \sin(bx) + C_2 e^{ax} \cos(bx) $$

> [!abstract] Schemat rozwiązywania równań wyższych rzędów
> 1. **Uporządkować elementy**, by otrzymać równanie, gdzie wszystkie funkcje zawierające $y$ będą po jednej stronie.
> 2. **Przekształcając lewą stronę równania na wielomian**, obliczamy pierwiastki równania: $r^n + a_{n-1}r^{n-1} + \dots + a_1r + a_0 = 0 \iff r_n, r_{n-1}, \dots, r_1$.
> 3. **Wyznaczamy CORJ**, podstawiając pierwiastki pod wzór ogólny.
> 4. **Metodą przewidywań** wyznaczamy CSRN dla $h(x)$.
> 5. **Obliczamy pochodne** potrzebne do podstawienia pod wzór wyjściowy.
> 6. **Podstawiamy pod $h(x)$** i wyznaczamy współczynniki za pomocą układu równań.
> 7. **Podstawiamy wartości**, by uzyskać CSRN.
> 8. **Wyznaczamy CORN**: $\text{CORN} = \text{CORJ} + \text{CSRN}$.
> 9. **Obliczamy pochodne CORN** w celu podstawienia warunków początkowych.
> 10. **Podstawiając warunki początkowe**, tworzymy układ równań i wyznaczamy stałe $c_1, \dots, c_n$.
> 11. **Podstawiamy wyznaczone stałe** pod CORN.