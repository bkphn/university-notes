## Całkowanie przez rozkład na ułamki proste
Całka, której mianownik jest iloczynem funkcji wymiernych, może być rozbita jako suma całek, co ułatwia operacje.

> [!example] Przykład rozkładu
> $$\int \frac{dx}{(x+1)(x-1)} = \int \frac{A}{x+1} \, dx + \int \frac{B}{x-1} \, dx$$
>
> $$A(x-1) + B(x+1) = 1 \implies Ax - A + Bx + B = 1 \implies (-A+B) + (A+B)x = 1$$
>
> Następnie porównujemy współczynniki przy tych samych potęgach:
>
> $$\begin{cases} -A + B = 1 \implies B = A + 1 \implies B = -\frac{1}{2} + 1 \implies B = \frac{1}{2} \\ A + B = 0 \implies A = -B \implies A = -A - 1 \implies 2A = -1 \implies A = -\frac{1}{2} \end{cases}$$
>

Dla mianowników z czynnikami kwadratowymi, np.:

$$\int \frac{1}{(x^2+1)(x-1)} \, dx = \int \frac{Ax+B}{x^2+1} \, dx + \int \frac{C}{x-1} \, dx$$

Należy pamiętać, że stopień wielomianu w liczniku musi być o jeden niższy niż stopień wielomianu w mianowniku.

## Całkowanie funkcji trygonometrycznych
Przy całkowaniu funkcji trygonometrycznych warto skorzystać z **podstawienia Weierstrassa**:

$$u = \mathrm{tg}\left(\frac{x}{2}\right)$$

Ze wzorów na funkcje trygonometryczne połowy kąta wiemy, że:
* $\sin(x) = \frac{2\mathrm{tg}\left(\frac{x}{2}\right)}{1+\mathrm{tg}^2\left(\frac{x}{2}\right)} = \frac{2u}{1+u^2}$
* $\cos(x) = \frac{1-\mathrm{tg}^2\left(\frac{x}{2}\right)}{1+\mathrm{tg}^2\left(\frac{x}{2}\right)} = \frac{1-u^2}{1+u^2}$

Różniczka $dx$ w tym podstawieniu wynosi:

$$dx = \frac{2 \, du}{1+u^2}$$

## Sposoby całkowania

### 1. Rozbijanie całki na sumę
Przykład przekształcenia algebraicznego wyrażenia podcałkowego:

$$\int \frac{1}{(x^2+1)^2} \, dx = \int \frac{x^2 + 1 - x^2}{(x^2+1)^2} \, dx = \int \left(\frac{x^2+1}{(x^2+1)^2} - \frac{x}{(x^2+1)^2}\right) dx$$

### 2. Dzielenie wielomianów
Gdy stopień licznika jest większy lub równy stopniu mianownika, stosujemy dzielenie wielomianów:

$$\int \frac{x^3}{x^3 - x^2 + x - 1} \, dx = \int \left(1 + \frac{x^2 - x + 1}{x^3 - x^2 + x - 1}\right) dx$$

*(Zgodnie z algorytmem dzielenia wielomianów: $\frac{x^3}{x^3 - x^2 + x - 1} = 1 \text{ reszta } x^2 - x + 1$)*.

### 3. Podstawianie z pierwiastkiem (podstawianie kwadratu)
Przykład całkowania wyrażeń niewymiernych z pierwiastkiem:

$$\int \frac{\sqrt{x}}{\sqrt{x}+1} \, dx = \begin{vmatrix} t = \sqrt{x} \\ t^2 = x \\ 2t \, dt = dx \end{vmatrix} = \int \frac{t}{t+1} \cdot 2t \, dt$$

### 4. Zaawansowane podstawienie pierwiastka wymiernego
Przykład obliczania całki z pierwiastkiem z funkcji wymiernej:

$$\int \sqrt{\frac{x+1}{x-1}} \, dx$$

Podstawiamy $t$ jako całe wyrażenie podpierwiastkowe:
* $t^2 = \frac{x+1}{x-1}$
* $t^2(x-1) = x + 1 \implies t^2x - t^2 = x + 1$
* $t^2x - x = t^2 + 1 \implies x(t^2 - 1) = t^2 + 1$
* $x = \frac{t^2+1}{t^2-1}$
* $dx = \frac{(t^2+1)'(t^2-1) - (t^2-1)'(t^2+1)}{(t^2-1)^2} \, dt = \frac{-4t}{(t^2-1)^2} \, dt$

Podstawiając do postaci całki:

$$\int t \cdot \frac{-4t}{(t^2-1)^2} \, dt = \dots$$

