## Podstawowe twierdzenia
> [!danger] Twierdzenie Bolzano-Cauchy'ego
> Jeśli funkcja $f:[a, b] \to \mathbb{R}$ jest ciągła w przedziale domkniętym $[a, b]$ oraz $f(a) \cdot f(b) < 0$, to w przedziale $(a, b)$ znajduje się co najmniej jeden pierwiastek równania $f(x) = 0$.

>[!danger] Twierdzenie o przedziale izolacji pierwiastka
>Jeśli funkcja $f$ spełnia założenia twierdzenia Bolzano-Cauchy'ego oraz jest ściśle monotoniczna (jej pochodna ma stały znak), to w przedziale $(a, b)$ istnieje dokładnie jeden pierwiastek równania $f(x) = 0$.

## Metoda bisekcji
Metoda polega na podziale przedziału $[a, b]$ na połowy i wybieraniu tej części, w której funkcja zmienia znak. 
* Wyznaczamy środek przedziału: $m_1 = \frac{a+b}{2}$.
* Jeśli $f(m_1) = 0$, to $m_1$ jest szukanym pierwiastkiem.
* Jeśli nie, z przedziałów $[a, m_1]$ i $[m_1, b]$ wybieramy ten, którego skrajne punkty mają różne znaki wartości funkcji ($\operatorname{sgn} n \neq \operatorname{sgn} m$).

Kolejne długości przedziałów dążą do zera:

$$|b_n - a_n| = \frac{1}{2^n}|b_0 - a_0|$$

Ciąg środków $m_n$ jest zbieżny do szukanego pierwiastka $\xi$. 
**Szybkość metody:** Jest to metoda wolna. W każdym kroku zyskujemy jedną cyfrę dwójkową, a jedną cyfrę dziesiętną zyskuje się średnio co 3.3 kroki (ponieważ $\frac{1}{10} \approx \frac{1}{2^{3.3}}$).

> [!abstract] Algorytm metody bisekcji
> 1. **Dane**
>    - funkcja $f$
>    - przedział $(a, b)$
>    - dokładność $\varepsilon$
> 2. **Podstawienie**
>    $\overline{a}=a$
>    $\overline{b}=b$
> 3. **Liczymy środek przedziału**
>    $m=\frac{\overline{a}+\overline{b}}{2}$
> 4. **Tak długo jak** $|\overline{b}-\overline{a}|\ge 2\varepsilon$ **liczymy:**
>    - Jeśli $f(m)=0$, to rozwiązaniem jest $m$
>    - Jeśli $f(\overline{a})\cdot f(m)<0$, to podstawiamy $\overline{b}=m$
>    - Jeśli $f(m)\cdot f(\overline{b})<0$, to podstawiamy $\overline{a}=m$
>    - Liczymy $m=\frac{\overline{a}+\overline{b}}{2}$
> 5. **Wynik**
>    Wynikiem jest $m$

## Metoda regula falsi (fałszywego położenia)
Metoda ta wymaga, by funkcja $f$ miała dokładnie jeden pierwiastek w przedziale $(a, b)$, różne znaki na końcach oraz była klasy $C^2$ ze stałym znakiem pierwszej i drugiej pochodnej. Przez punkty krańcowe wykresu prowadzona jest cięciwa.

Punkt przecięcia cięciwy z osią OX wyznacza kolejne przybliżenie:

$$x_1 = a - \frac{f(a)(b-a)}{f(b)-f(a)}$$

Ogólny wzór metody (gdzie $\overline{x}$ to stały koniec przedziału):

$$x_{k+1} = x_k - \frac{f(x_k)}{f(\overline{x}) - f(x_k)}(\overline{x} - x_k)$$

> [!abstract] Algorytm metody regula falsi
> 1. **Dane**
>    - funkcja $f$
>    - przedział $(a, b)$
>    - punkt stały $\overline{x}$
>    - dokładność $\varepsilon$
> 2. **Podstawienie** $x_n$
>    $x_{n}=a$ jeśli $\overline{x}=a$
>    $x_{n}=b$ jeśli $\overline{x}=b$
> 3. **Podstawiamy** $x_s$
>    $x_{s}=\overline{x}$
> 4. **Tak długo jak $|x_{n}-x_{s}|>\varepsilon$:**
>    $x_{s}=x_{n}$
>    $x_{n}=x_{s}-\frac{f(x_{s})}{f(\overline{x})-f(x_{s})}(\overline{x}-x_{s})$
> 5. **Wynik**
>    Wynikiem jest $x_{n}$

## Metoda Newtona (metoda stycznych)
Wymaga tych samych założeń co regula falsi ($f \in C^2$, stałe znaki pochodnych, zmiana znaku na krańcach przedziału). Zamiast cięciwy, korzystamy ze stycznej do wykresu poprowadzonej w punkcie, dla którego funkcja ma ten sam znak co jej druga pochodna.

Wzór iteracyjny metody Newtona uzyskuje się z równania stycznej po przyrównaniu $y$ do zera:

$$x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}$$

> [!abstract] Algorytm metody Newtona
> 1. **Dane**
>    - funkcja $f$
>    - punkt $x_{0}$
>    - dokładność $\varepsilon$
> 2. **Podstawienie** $x_s, x_n$
>    $x_{s}=x_{0}+2\varepsilon$
>    $x_{n}=x_{0}$
> 3. **Tak długo jak $|x_{n}-x_{s}|>\varepsilon$:**
>    $x_{s}=x_{n}$
>    $x_{n}=x_{s}-\frac{f(x_{s})}{f'(x_{s})}$
> 4. **Wynik**
>    Wynikiem jest $x_{n}$
>    ---

## Układy równań nieliniowych i Macierz Jacobiego
Dla wektora funkcji $\mathbf{f}:\mathbb{R}^n \to \mathbb{R}^m$, macierzą Jacobiego ($\mathbf{J_f}$) nazywamy macierz składającą się z pochodnych cząstkowych:

$$\mathbf{J_f} =  \left[\frac{\partial f_i}{\partial x_j} \right]$$

Wyznacznik tej macierzy to Jakobian ($\det \mathbf{J_f}$).

### Metoda Newtona dla układów równań
Rozwiązując układ $\mathbf{f(x) = \vec{0}}$, kolejne przybliżenia $\mathbf{x}^{i+1}$ wyznaczamy ze wzoru:

$$\mathbf{x}^{i+1} = \mathbf{x}^i - \mathbf{J_f}^{-1}(\mathbf{x}^i) \cdot \mathbf{f}(\mathbf{x}^i)$$

## Metoda iteracji prostej
Równanie zapisujemy w postaci $x = \varphi(x)$. Metoda jest zbieżna dla dowolnego $x_0 \in [a, b]$, jeśli w przedziale izolacji pierwiastka spełniony jest warunek:

$$|\varphi'(x)| \le M < 1$$

Oszacowanie błędu wyraża się wzorem:

$$|\xi - x_k| \le M^k(b - a)$$

> [!example] Wyznacz przybliżone rozwiązanie równania: $1.5x^3 - 240x + 500 = 0$ dla $x\in[0,7]$
> 1. **Przekształcamy otrzymując**:
>    $x=x+\lambda(1.5x^3 - 240x + 500)$
>    $\varphi(x)=x+\lambda(1.5x^3 - 240x + 500)$
> 2. **Liczymy pochodną**
>    $\varphi'(x)=1+\lambda(4.5x^2 - 240)$
> 3. **Rozwiązujemy nierówność**
>    $|1+\lambda(4.5x^2 - 240)|<1$
>    $-2<\lambda(4.5x^2 - 240)<0$
> 4. **Sprawdzamy** $\lambda$
>    $x\in[0,7] \Rightarrow 4.5x^2 - 240 < 0 \Rightarrow \lambda > 0$
> 5. **Wybieramy najmniej korzystną sytuację** $(x=0)$
>    $4.5x^2 - 240 > -2|_{x=0} \Rightarrow -240\lambda > -2 \Rightarrow \lambda\in(0, \frac{1}{120})$
> 6. **Przekształcamy równanie**
>    $x=x+\lambda(1.5x^3 - 240x + 500)|_{\lambda=\frac{1}{120}} \Rightarrow x=x+\frac{1}{250}(1.5x^3 - 240x + 500)$
>    $x=0.006x^3 + 0.04x + 2$
> 7. **Obliczamy** $x_i$
>    $x_{0}=1$
>    $x_{1}=2.046$
>    $x_{2}=2.13323$
>    $x_{3}=2.14357$

