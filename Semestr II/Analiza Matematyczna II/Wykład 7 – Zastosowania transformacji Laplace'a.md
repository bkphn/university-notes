## Zastosowania transformacji Laplace'a
Transformacja Laplace'a pozwala na szybsze i skuteczniejsze obliczanie problemów Cauchy'ego (równań różniczkowych z warunkami początkowymi).

> [!example] Oblicz $y' + y = 1$ z warunkiem początkowym $y(0) = 2$
> $$y' + y = 1$$
> $$\mathcal{L}[y' + y] = \mathcal{L}[1]$$
> $$\mathcal{L}[y'] + \mathcal{L}[y] = \mathcal{L}[1]$$
> $$s\mathcal{L}[y] - y(0) + \mathcal{L}[y] = \mathcal{L}[1]$$
> $$s \cdot Y(s) - 2 + Y(s) = \frac{1}{s}$$
> $$Y(s)(s + 1) = \frac{1}{s} + 2$$
> $$Y(s) = \frac{1 + 2s}{s(s + 1)}$$
> $$Y(s) = \frac{s + s + 1}{s(s + 1)}$$
> $$Y(s) = \frac{1}{s + 1} + \frac{1}{s}$$
> $$Y(s) = \mathcal{L}[e^{-x}] + \mathcal{L}[\mathbb{1}(x)]$$
> $$\Downarrow$$
> $$y = e^{-x} + 1$$
## Przesunięcia w argumencie
Dla przesunięć w argumentach prawdziwe są następujące własności:
 $$\mathcal{L}[f(t - t_0) \cdot \mathbb{1}(t - t_0)](s) = \int_{t_0}^{\infty} f(t - t_0) e^{-st} \, dt = e^{-st_0} \cdot \mathcal{L}[f(t)](s)$$
$$\mathcal{L}[f(t)](s - s_0) = \int_{0}^{\infty} f(t) e^{-(s - s_0)t} \, dt = \mathcal{L}[e^{s_0 t} f(t)](s)$$

Wynika z nich bezpośrednio wzór na transformację odwrotną:
$$ \mathcal{L}^{-1}\left[\frac{1}{s-a}\right] = e^{at} $$
## Układy równań różniczkowych
Transformacje Laplace'a pozwalają nam również na skuteczne rozwiązywanie układów równań różniczkowych.

> [!example] Przykład rozwiązania układu
> Rozwiąż układ równań różniczkowych z warunkami początkowymi $y(0) = z(0) = 0$:
> $$ \begin{cases} y' = y + z + 1 \\ z' = -y + z \end{cases} $$
> 
> Po nałożeniu transformaty Laplace'a na oba równania układu otrzymujemy:
> $$ \begin{cases} s \cdot Y - 0 = Y + Z + \frac{1}{s} \implies Z = sY - Y - \frac{1}{s} \\ sZ = -Y + Z \implies s\left(sY - Y - \frac{1}{s}\right) = -Y + sY - Y - Y - \frac{1}{s} \implies Y = \frac{s-1}{s(s^2 - 2s + 2)} \end{cases} $$
> 
> Teraz obliczamy $Y(s)$ za pomocą rozkładu na ułamki proste:
> $$ Y = \frac{s-1}{s(s^2 - 2s + 2)} \implies Y = \frac{A}{s} + \frac{Bs+C}{s^2 - 2s + 2} $$
> 
> Podstawiamy do wspólnego mianownika i wyznaczamy współczynniki:
> $$ A(s^2 - 2s + 2) + (Bs + C)s = s - 1 $$
> $$ As^2 - 2As + 2A + Bs^2 + Cs = s - 1 $$
> 
> Porównując współczynniki przy odpowiednich potęgach $s$, otrzymujemy układ równań:
> $$ \begin{cases} A + B = 0 \implies B = \frac{1}{2} \\ -2A + C = 1 \implies C = 0 \\ 2A = -1 \implies A = -\frac{1}{2} \end{cases} $$
> 
> Rozbijamy $Y(s)$ na składniki łatwiejsze do odwrotnej transformacji:
> $$ Y = -\frac{1}{2} \cdot \frac{1}{s} + \frac{1}{2} \cdot \frac{s}{s^2 - 2s + 2} = -\frac{1}{2} \mathcal{L}(1) + \frac{1}{2} \cdot \frac{s - 1 + 1}{(s-1)^2 + 1} $$
> $$ Y = -\frac{1}{2} \mathcal{L}(\mathbb{1}) + \frac{1}{2} \mathcal{L}(e^x \cos x) + \frac{1}{2} \mathcal{L}(e^x \sin x) $$
> 
> Stąd otrzymujemy ostateczne rozwiązanie dla funkcji $y$:
> $$ y = -\frac{1}{2} + \frac{1}{2} e^x \cos x + \frac{1}{2} e^x \sin x $$
> 
> Korzystając z zależności $z = y' - y - 1$ wynikającej z przekształceń oraz pierwszego równania układu, wyznaczamy funkcję $z$:
> $$ z = \left(-\frac{1}{2} e^x \sin x + \frac{1}{2} e^x \cos x + \dots\right) - y - 1 \implies z = -\frac{1}{2} + \frac{1}{2} e^x \cos x - \frac{1}{2} e^x \sin x $$