## Obliczanie pól figur opisanych funkcjami
Za pomocą całki jesteśmy w stanie policzyć pola figur opisanych funkcjami. Wzór wygląda następująco: $$ \int_{a}^{b} [f(x) - g(x)] \, dx $$gdzie:
* $f(x)$ – funkcja „górna”,
* $g(x)$ – funkcja „dolna”,
* $a$ – punkt rozpoczęcia figury,
* $b$ – punkt zakończenia figury.

> [!example] Przykład: Pole koła jednostkowego
> Górna połowa okręgu jest opisana za pomocą funkcji $f(x) = \sqrt{1-x^2}$. Aby opisać dolną połowę, dodajemy na początku minus: $f(x) = -\sqrt{1-x^2}$.
> Teraz wystarczy, że obliczymy całkę oznaczoną z przedziału $\langle -1, 1 \rangle$ z różnicy tych pól:
> $$ \int_{-1}^{1} [\sqrt{1-x^2} - (-\sqrt{1-x^2})] \, dx = 4\int_{0}^{1}\sqrt{1-x^2} \, dx = \begin{vmatrix} x = \sin t \\ dx = \cos t \, dt \\ x = 0 \implies t = 0 \\ x = 1 \implies t = \frac{\pi}{2} \end{vmatrix} = $$
> $$ = 4\int_{0}^{\frac{\pi}{2}} \cos^2 t \, dt = 4\int_{0}^{\frac{\pi}{2}} \frac{1 + \cos 2t}{2} \, dt = 4 \cdot \frac{\pi}{4} = \pi $$
## Parzystość funkcji
* Funkcję $f$ nazywamy **funkcją parzystą**, jeżeli $f(x) = f(-x)$. Licząc całkę z takiej funkcji, możemy stosować uproszczenia:
  $$ \int_{-a}^{a} f(x) \, dx = \int_{-a}^{0} f(x) \, dx + \int_{0}^{a} f(x) \, dx = 2 \cdot \int_{0}^{a} f(x) \, dx $$
* Funkcję $f$ nazywamy **funkcją nieparzystą**, jeżeli $-f(x) = f(-x)$.
## Długość krzywej
Aby obliczyć długość krzywej opisanej równaniem $f(x)$ w przedziale $(a, b)$, korzystamy ze wzoru:
$$ l = \int_{a}^{b} \sqrt{1 + [f'(x)]^2} \, dx $$
## Objętość bryły i pole powierzchni obrotowej
Aby obliczyć objętość bryły powstałej w wyniku obrotu krzywej $y = f(x)$ wokół osi $Ox$, korzystamy ze wzoru:
$$ V = \pi \cdot \int_{a}^{b} [f(x)]^2 \, dx $$

> [!example] Przykład: Objętość i pole powierzchni kuli
> Obracając funkcję $f(x) = \sqrt{1-x^2}$ dookoła osi $Ox$, otrzymujemy kulę.
> * **Objętość kuli:**
>   $$ V = \pi \int_{-1}^{1} (\sqrt{1-x^2})^2 \, dx = 2\pi \int_{0}^{1} (1 - x^2) \, dx = 2\pi \cdot \left[x - \frac{x^3}{3}\right]_0^1 = 2\pi \cdot \left(\frac{2}{3} - 0\right) = \frac{4}{3}\pi $$
> * **Pole powierzchni kuli:** Wykorzystujemy wzór na pole powierzchni bryły obrotowej $S = 2\pi \cdot \int_{a}^{b} f(x) \cdot \sqrt{1 + [f'(x)]^2} \, dx$:
>   $$ S = 2\pi \cdot \int_{-1}^{1} \sqrt{1-x^2} \cdot \sqrt{1 + \left((\sqrt{1-x^2})'\right)^2} \, dx = 4\pi \cdot \int_{0}^{1} \sqrt{1-x^2} \cdot \frac{1}{\sqrt{1-x^2}} \, dx = 4\pi \cdot [x]_0^1 = 4\pi $$
> 
> *Warto zapamiętać, że powyższy wzór opisuje pole powierzchni bocznej dla danej figury; chcąc obliczyć pole powierzchni całkowitej dla figur różnych od kuli i jej podobnych, należy dodać do wzoru pola podstaw (np. okręgów w punktach $a$ i $b$)*.
## Całki niewłaściwe
### Całka niewłaściwa II rodzaju
Jeżeli granice całkowania nie należą do dziedziny funkcji, to całkę taką nazywamy całką niewłaściwą II rodzaju. Licząc ją, musimy policzyć granicę, w której zmienna dąży do wartości wykluczonej z dziedziny:
* Niech $f: (a, b] \to \mathbb{R}$ (czyli $a \notin D_f$): $$ \int_{a}^{b} f(x) \, dx = \lim_{A \to a^{+}} \int_{A}^{b} f(x) \, dx $$
* Niech $f: [a, b) \to \mathbb{R}$ (czyli $b \notin D_f$): $$ \int_{a}^{b} f(x) \, dx = \lim_{B \to b^{-}} \int_{a}^{B} f(x) \, dx $$
> [!example] Przykład (długość łuku okręgu / obwód)
> Oblicz całkę z przedziału $\langle -1, 1 \rangle$ wzoru na obwód koła jednostkowego:
> $$ 2 \cdot \int_{-1}^{1} \sqrt{1 + \left((\sqrt{1-x^2})'\right)^2} \, dx = 4 \int_{0}^{1} \frac{1}{\sqrt{1-x^2}} \, dx = 4 [\arcsin 1 - \arcsin 0] = 4 \cdot \frac{\pi}{2} = 2\pi $$
> Dziedziną funkcji $\frac{1}{\sqrt{1-x^2}}$ jest przedział $(-1, 1)$, więc granice całkowania $a = -1$ oraz $b = 1$ nie należą do dziedziny ($a, b \notin D_f$) – mamy do czynienia z całką niewłaściwą II rodzaju.
### Całka niewłaściwa I rodzaju
Jeżeli któraś z granic całkowania jest nieskończona, to całkę taką nazywamy całką niewłaściwą I rodzaju. Podobnie jak w drugim rodzaju, liczymy granicę takiej całki:
* Niech $f: (a, \infty) \to \mathbb{R}$:
  $$ \int_{a}^{\infty} f(x) \, dx = \lim_{b \to \infty} \int_{a}^{b} f(x) \, dx $$
* Niech $f: (-\infty, b) \to \mathbb{R}$:
  $$ \int_{-\infty}^{b} f(x) \, dx = \lim_{a \to -\infty} \int_{a}^{b} f(x) \, dx $$

> [!example] Przykład
> Oblicz całkę oznaczoną z przedziału $(1, \infty)$ dla funkcji $\frac{1}{x^3}$:
> $$ \int_{1}^{\infty} \frac{1}{x^3} \, dx = \lim_{b \to \infty} \int_{1}^{b} x^{-3} \, dx = \lim_{b \to \infty} \left[\frac{x^{-2}}{-2}\right]_{1}^{b} = \lim_{b \to \infty} \left(\frac{1}{-2b^2} - \frac{1}{-2}\right) = 0 - \left(-\frac{1}{2}\right) = \frac{1}{2} $$