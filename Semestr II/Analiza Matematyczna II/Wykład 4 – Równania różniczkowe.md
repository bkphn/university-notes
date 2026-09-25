## Równanie różniczkowe zwyczajne
Równaniem różniczkowym zwyczajnym nazywamy równanie o niewiadomej funkcji $y(x)$:

$$F(y, y', y'', \dots, y^{(n)}, x) = 0$$

Rząd równania różniczkowego to najwyższy rząd pochodnej w równaniu (odpowiednik stopnia wielomianu). 
* Rząd równania $y' \operatorname{ctg} x = \operatorname{tg} x$ jest równy 1.
* Rząd równania $y'' = y$ jest równy 2.

Aby obliczyć dane równanie różniczkowe, potrzebujemy znać samo równanie oraz wartość początkową (wartości funkcji i jej pochodnej w konkretnym punkcie). Ilość pierwiastków (rozwiązań) równania różniczkowego jest równa rzędowi tego równania:

$$F(y, y', y'', \dots, y^{(n)}, x) = 0 \implies p_1, p_2, \dots, p_n$$

Rozwiązaniem równania jest funkcja w postaci:

$$y^{(n)} = Ay_1(x) + By_2(x) + \dots + Ny_n(x)$$

## Równania różniczkowe I rzędu
Równaniem różniczkowym I rzędu nazywamy równanie w postaci:

$$y' + f(x) \cdot y = h(x)$$

gdzie $y$ jest funkcją zmiennej $x$.

## Równanie różniczkowe o zmiennych rozdzielonych
Równanie o zmiennych rozdzielonych to taki rodzaj równania I rzędu, w którym $x$ i $y$ można zapisać po dwóch stronach równania niezależnie od siebie. Ma ono postać:

$$y' = f(x) \cdot h(y)$$

> [!abstract] Schemat rozwiązania
> 1. **Uporządkować elementy**, by otrzymać dwie funkcje – jedną zależną od $x$, a drugą od $y$: $y' = f(x) \cdot h(y)$.
> 2. **Rozbić** $y'$ z postaci Lagrange'a do postaci Leibniza: $\frac{dy}{dx} = f(x) \cdot h(y)$.
> 3. **Pomnożyć przez mianownik**, aby uporządkować wyrazy: $\frac{1}{h(y)} \, dy = f(x) \, dx$.
> 4. **Obustronnie scałkować równanie**: $\int h(y)^{-1} \, dy = \int f(x) \, dx$.
> 5. **Otrzymać funkcje pierwotne wraz ze stałą** $c$: $H(y) = F(x) + c$.
> 6. **Wyznaczyć równanie** $y$: $y = H^{-1}[F(x) + c]$.
> 7. **Podstawić argument początkowy** $y(x_p) = x_1 \implies H^{-1}[F(x_p) + c] = x_1$.
> 8. **Wyznaczyć stałą** $c$ ($c = C$).
> 9. **Podstawić do równania** na $y$: $y = H^{-1}[F(x_p) + C]$.

> [!example] Przykład rozwiązania
> Rozwiąż równanie $y' = \frac{\operatorname{tg} y}{\operatorname{ctg} x}$ z warunkiem początkowym $y\left(\frac{\pi}{4}\right) = \frac{\pi}{4}$:
> 1. $y' = \operatorname{tg} y \cdot \frac{1}{\operatorname{ctg} x}$
> 2. $\frac{dy}{dx} = \operatorname{tg} y \cdot \operatorname{tg} x$
> 3. $\operatorname{ctg} y \, dy = \operatorname{tg} x \, dx$
> 4. $\int \frac{\cos y}{\sin y} \, dy = \int \frac{\sin x}{\cos x} \, dx$
> 5. $\ln|\sin y| = -\ln|\cos x| + c$
> 6. $e^{\ln|\sin y|} = e^{-\ln|\cos x|} \cdot e^c \implies \sin y = \frac{1}{\cos x} \cdot c \implies y = \arcsin\left(\frac{1}{\cos x} \cdot c\right)$
> 7. $y\left(\frac{\pi}{4}\right) = \frac{\pi}{4} \implies \frac{\pi}{4} = \arcsin\left(\frac{c}{\cos\frac{\pi}{4}}\right)$
> 8. $\sin\left(\frac{\pi}{4}\right) = \frac{c}{\cos\frac{\pi}{4}} \implies \frac{\sqrt{2}}{2} = \frac{2}{\sqrt{2}} \cdot C \implies C = \frac{1}{2}$
> 9. $y(x) = \arcsin\left(\frac{1}{\cos x} \cdot \frac{1}{2}\right)$

## Równanie różniczkowe niejednorodne
Równanie różniczkowe niejednorodne to równanie postaci $y' + f(x)y = h(x)$, którego nie da się uporządkować tak jak równania o zmiennych rozdzielonych.

> [!abstract] Schemat rozwiązania metodą uzmienniania stałej
> 1. **Uporządkować elementy**, by otrzymać równanie, gdzie wszystkie funkcje zawierające $y$ będą po jednej stronie: $y' + f(x) \cdot y = h(x)$.
> 2. **Utworzyć równanie jednorodne**, podstawiając pod $h(x)$ liczbę 0: $y' + f(x) \cdot y = 0$.
> 3. **Wyznaczyć** $y$ z tego równania: $y = F(x) \cdot c$.
> 4. **Uzmiennić stałą**, zamieniając $c$ na funkcję zależną od $x$ – $c(x)$: $y = F(x) \cdot c(x)$.
> 5. **Obliczyć pochodną** $y'$ potrzebną do podstawienia pod równanie wyjściowe: $y' = F'(x) \cdot c(x) + F(x) \cdot c'(x)$.
> 6. **Podstawić** wyznaczone $y$ oraz $y'$ pod równanie początkowe:
>
>    $$\color{red}{y'} + \color{green}{f(x)} \cdot \color{blue}{y} \color{black}{ = h(x)} \implies \color{red}{(F'(x) \cdot c(x) + F(x) \cdot c'(x))} + \color{green}{f(x)} \cdot \color{blue}{(F(x) \cdot c(x))} \color{black}{= h(x)}$$
>
> 7. **Uprościć równanie** (wyrażenia z $c(x)$ powinny się zredukować): $c'(x) \cdot F(x) = h(x)$.
> 8. **Wyznaczyć funkcję pierwotną** $c(x)$: $c'(x) = \frac{h(x)}{F(x)} \implies c(x) = \int \frac{h(x)}{F(x)} \, dx \implies c(x) = H(x) + C$.
> 9. **Podstawić funkcję** $c(x)$ pod równanie $y$ z punktu 4: $y = F(x) \cdot (H(x) + C)$.

> [!example] Przykład rozwiązania
> Rozwiąż równanie $y' = e^x - e^x y$ (to równanie można również potraktować jako równanie o zmiennych rozdzielonych):
> 1. $y' + e^x y = e^x$
> 2. $y' + e^x y = 0$
> 3. $\int \frac{1}{y} \, dy = \int -e^x \, dx \implies \ln|y| = -e^x + c \implies y = e^{-e^x} \cdot e^c \implies y = c \cdot e^{-e^x}$
> 4. $y = c(x) \cdot e^{-e^x}$
> 5. $y' = c'(x) \cdot e^{-e^x} + c(x) \cdot e^{-e^x} \cdot (-e^x)$
> 6. $c'(x) \cdot e^{-e^x} + c(x) \cdot e^{-e^x} \cdot (-e^x) + (e^x) \cdot c(x) \cdot e^{-e^x} = e^x$
> 7. $c'(x) \cdot e^{-e^x} = e^x$
> 8. $c'(x) = \frac{e^x}{e^{-e^x}} \implies c'(x) = e^x \cdot e^{e^x} \implies c(x) = \int e^x e^{e^x} \, dx \implies c(x) = e^{e^x} + c$
> 9. $y = c(x) \cdot e^{-e^x} \implies y = (e^{e^x} + C) \cdot e^{-e^x} \implies y = 1 + Ce^{-e^x}$
