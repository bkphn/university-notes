## Iloczyn skalarny i ortogonalność funkcji
Iloczyn skalarny dwóch funkcji $f(x)$ i $g(x)$ zwraca pole pod wykresem iloczynu tych funkcji i definiujemy go wzorem:

$$\langle f, g \rangle = \int_{-\pi}^{\pi} f(x)g(x) \, dx$$

Mówimy, że funkcje $f(x)$ i $g(x)$ są **ortogonalne**, kiedy pole pod wykresem ich iloczynu wynosi zero, czyli $\langle f, g \rangle = 0$. Oznacza to, że funkcje te są „prostopadłe” do siebie w przestrzeni funkcji. Układ funkcji $(\sin 0x, \sin 1x, \sin 2x, \dots, \cos 0x, \cos 1x, \cos 2x, \dots)$ jest układem ortogonalnym. Zachodzi również:

$$\int_{-\pi}^{\pi} \sin mx \cdot \cos nx \, dx = 0, \quad m \neq n$$

## Szereg Fouriera
Szereg Fouriera to sposób rozbicia funkcji okresowej na sumę nieskończonej ilości funkcji sinus i cosinus. Szereg Fouriera ma postać:

$$f(x) \approx \frac{a_0}{2} + a_1 \cos x + b_1 \sin x + a_2 \cos 2x + b_2 \sin 2x + \dots$$

Co możemy uprościć do postaci:

$$f(x) \sim \frac{a_0}{2} + \sum_{n=1}^{\infty} [a_n \cos nx + b_n \sin nx]$$

### Współczynniki Fouriera
Współczynniki $a_n$ i $b_n$ nazywamy współczynnikami Fouriera, gdzie $a_n$ to współczynniki cosinusowe, a $b_n$ to współczynniki sinusowe. Obliczamy je ze wzorów:

 $$a_n = \frac{1}{\pi} \cdot \int_{-\pi}^{\pi} f(x) \cdot \cos nx \, dx$$

$$b_n = \frac{1}{\pi} \cdot \int_{-\pi}^{\pi} f(x) \cdot \sin nx \, dx$$

**Własności parzystości:**
* Jeżeli funkcja $f$ jest funkcją **parzystą**, czyli $f(x) = f(-x)$, to wtedy wszystkie współczynniki sinusowe $b_n$ są zerowe.
* Jeżeli funkcja $f$ jest funkcją **nieparzystą**, czyli $-f(x) = f(-x)$, to wtedy wszystkie współczynniki cosinusowe $a_n$ są zerowe.

Z tych stwierdzeń wynika, że jeżeli mamy do czynienia z funkcją parzystą, to jej rozkład Fouriera będzie się składał tylko z cosinusów, a jeżeli nieparzystą – będzie sumą sinusów.

## Twierdzenie Fejéra
Wiemy, że jeżeli $f$ jest ciągła, miejscami monotoniczna i okresowa, to funkcja $\frac{a_0}{2} + \sum_{n=1}^{\infty} [a_n \cos nx + b_n \sin nx]$ zbiega punktowo do $f(x)$ 

$$F_n(x) \to f(x)$$

Zbieżność punktowa $\rightarrow$ oznacza, że dla każdego $x$ każda kolejna suma przybliża nas coraz bardziej do funkcji $f(x)$, jednak dzieje się to nierównomiernie, w różnym tempie dla każdego $x$

> [!danger] Twierdzenie Fejéra
> Ciąg średnich arytmetycznych sum funkcji, zbiega **jednostajnie** $\rightrightarrows$ do funkcji $f$, czyli równomiernie i tak samo szybko dla każdego $x$:
>
> $$\frac{F_1(x) + F_2(x) + \dots + F_n(x)}{n} \rightrightarrows f(x)$$
>

## Przykłady przybliżania funkcji
Wykresy w materiałach pokazują kolejne kroki przybliżania funkcji moduł $f(x) = |x|$ dla $|x| \le \pi$ za pomocą sum częściowych szeregu Fouriera (zawierającego wyrazy z $\frac{\pi^2}{2\pi}$ oraz odpowiednie harmonijki cosinusowe, np. $\frac{-4 \cos x}{\pi}$, $\frac{-4 \cos 3x}{3^2 \pi}$). Ogólna postać tego rozwinięcia to:

$$g(x) = \frac{\pi}{2} - \frac{4}{\pi} \left(\frac{\cos x}{1^2} + \frac{\cos 3x}{3^2} + \dots\right)$$

> [!example] Rozwinięcie funkcji w szereg Fouriera
> Rozwiń funkcję w szereg Fouriera:
>
> $$f(x) = x, \quad |x| \le \pi$$
>
> 1. **Badamy parzystość:** $f(-x) = -x$, zatem funkcja jest nieparzysta, więc $\forall_{n \in \mathbb{N}} \, a_n = 0$.
> 2. **Obliczamy współczynniki $b_n$** przez całkowanie przez części:
>
>    $$b_n = \frac{1}{\pi} \int_{-\pi}^{\pi} x \cdot \sin nx \, dx = \frac{2}{\pi} \int_{0}^{\pi} x \cdot \sin nx \, dx$$
>
>    Podstawiając $u = x, v' = \sin nx$ oraz $u' = 1, v = -\frac{\cos nx}{n}$:
>
>    $$b_n = \frac{2}{\pi} \left[-\frac{x \cos nx}{n} - \int -\frac{\cos nx}{n} \, dx\right]_0^\pi = \frac{2}{n\pi} \left[-x \cos nx + \frac{\sin nx}{n}\right]_0^\pi$$
>
>    $$b_n = \frac{2}{\pi n} [-\pi \cos(n\pi) + 0 - 0 + 0] = \frac{-2 \cos(n\pi)}{n} = \frac{-2(-1)^n}{n}$$
>
> 3. **Zapisujemy ostateczny szereg** Fouriera dla funkcji $f(x) = x$:
>
>    $$f(x) = \sum_{n=1}^{\infty} b_n \cdot \sin nx = \sum_{n=1}^{\infty} \frac{-2(-1)^n \sin nx}{n}$$
>
