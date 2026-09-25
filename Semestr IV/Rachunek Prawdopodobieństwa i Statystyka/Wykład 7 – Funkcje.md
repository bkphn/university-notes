## Funkcje charakterystyczne
**Funkcją charakterystyczną** zmiennej losowej $\xi$ nazywamy funkcję $\varphi$ o wartościach zespolonych:

$$\varphi_{\xi}(t)=\mathbb{E}[e^{it\xi}]=\int_{-\infty}^\infty e^{itx} f_{\xi}(x)dx$$

gdzie $i^2=-1, t\in\mathbb{R}$. Funkcja charakterystyczna pozwala na przeniesienie obliczeń na zmiennych losowych do ciała liczb zespolonych, co często upraszcza obliczenia.

Funkcję charakterystyczną możemy rozwinąć do postaci:

$$\varphi_{x}(t)=\int_{-\infty}^\infty \cos tx+f_{\xi}(x)dx+i\int_{-\infty}^\infty\sin tx+f_{\xi}(x)dx$$

## Własności funkcji charakterystycznych
Dla dowolnych niezależnych zmiennych losowych $\xi,\eta$ oraz zmiennych rzeczywistych $a,b$ zachodzą poniższe własności:
- $\varphi_\xi(0)=1$
- $|\varphi_\xi  (t)|\leq1$
- $\varphi_{a\xi +b} (t)=e^{itb} \varphi_\xi  (at)$
- $\varphi_{\xi +\eta} (t)=\varphi_\xi  (t) \varphi_\eta (t)$

Jeśli $\xi \in \mathcal{N}(m, \sigma^2 )$ to gęstość $f_\xi(x)=\frac{1}{\sqrt{ 2\pi}\sigma}\cdot e^{-\frac{(x-m)^2}{2\sigma^2}}$, funkcja charakterystyczna rozkładu normalnego $\mathcal{N}(m,\sigma^2 )$ wynosi:

$$\varphi_{\xi}(t)=e^{itm-\frac{\sigma^2t^2}{2}}$$

## Twierdzenie o jednoznaczności

>[!danger] Twierdzenie o jednoznaczności
> Każdej funkcji charakterystycznej $\varphi$ odpowiada tylko jedna dystrybuatna $F$.

Z powyższego twierdzenia wynika, że jeżeli $\xi _1\in \mathcal{N}(m_1,\sigma_1^2 ), \xi _2\in \mathcal{N}(m_2,\sigma_2^2 )$ i $\xi _1,\xi _2$ są niezależne, to $\xi _1+\xi _2\in \mathcal{N}(m_1+m_2,  \sigma_1^2+\sigma_1^2 )$.

Co można uogólnić do twierdzenia, że dla niezależnych zmiennych losowych $\xi _k\in \mathcal{N}(m_k,\sigma_k^2 )$ gdzie $k∈\{1, 2,\dots, n\}$ to dla dowolnych $a_k$ zachodzi:

$$\sum_{k=1}^n a_{k}\xi_{k}\in \mathcal{N}(M,\Sigma), \qquad M=\sum_{k=1}^n a_{k}m_{k}, \quad \Sigma=\sum_{k=1}^n a_{k}^2\sigma_{k}^2$$

## Funkcje tworzące
Jeżeli zmienna losowa $\xi$ jest taka, że $\sum_{k=-\infty}^\infty P(\xi=k)=1$, czyli funkcja $\xi \in\mathbb{Z}$ to funkcją tworzącą bądź funkcją generującą zmiennej losowej $\xi$ nazywamy funkcję:

$$G_{\xi}(z)=\mathbb{E}[z^\xi]=\sum_{k=-\infty}^\infty z^kP(\xi=k), \qquad|z|=1$$

Prowadzący do oznaczania funkcji tworzącej używa zapisu $P_\xi$ zamiast $G_\xi$ jednak aby uniknąć kolizji oznaczeń z prawdpodobieństwem $P$ będę trzymał się europejskiego zapisu $G_\xi$.

Funkcja tworząca dla dowolnych całkowitych $k,n\in\mathbb{Z}$ oraz niezależnych zmiennych losowych $\xi ,\eta$ spełnia własności:
- $G(1)=1$
- $|G(z)\leq 1|,\quad  |z|=1$
- $G_{k\xi +n} (z)=z^n G_\xi  (z^k )$
- $G_{\xi +\eta} (z)=G_\xi  (z) G_\eta  (z), \quad |z|=1$

## Zbieżność zmiennych losowych
Mówimy, że ciąg $x_n$ jest zbieżny do $x\in(−\infty,\infty)$, jeżeli dla dowolnego $\varepsilon>0$ istnieje $n(\varepsilon)\in\mathbb{N}$ taka, że $|x_n−x|\leq\varepsilon$ dla wszystkich $n\geq n(\varepsilon)$.

O zbieżności zmiennych losowych, mówimy gdy spełniona jest własność:

$$\xi_{n}\rightarrow\xi\implies P(\xi_{n}\in A)\rightarrow P(\xi\in A)$$

W odróżnieniu do zmiennych rzeczywistych, w zmiennych losowych możemy wyróżnić parę rozdzajów zbieżności:
- **Zbieżność prawie na pewno**: Ciąg zmiennych losowych $\xi_n$ nazywamy zbieżnym prawie na pewno (z prawdopodobieństwem $1$) do zmiennej losowej $\xi$ , jeżeli:

$$\lim_{ n \to \infty } \xi_{n}(\omega)=\xi(\omega), \qquad \omega\in\Omega$$

Zbieżność tą będziemy oznaczać jako:

$$\xi_n \xrightarrow[n \to \infty]{\text{p.n.}} \xi$$

- **Zbieżność według prawdopodobieństwa**: Mówimy, że ciąg zmiennych losowych $\xi_n$ jest zbieżny do $\xi$ według prawdopodobieństwa, jeżeli dla każdego $\varepsilon>0$ spełniony jest warunek:

$$\lim_{ n \to \infty } P(|\xi_{n}-\xi|>\varepsilon)=0$$

Zbieżność tą będziemy oznaczać jako:

$$\xi_n \xrightarrow[n \to \infty]{P} \xi$$

- **Zbieżność średniokwadratowa**: Mówimy, że ciąg $\xi_n$ jest zbieżny średniokwadratowo do $\xi$, jeżeli spełniony jest warunek:

$$\mathbb{E}[\xi_{n}-\xi]^2\rightarrow 0$$

Zbieżność tą będziemy oznaczać jako:

$$\xi_n \xrightarrow[n \to \infty]{\text{ś.k.}} \xi$$

- **Zbieżność słaba**: Mówimy, że ciąg $\xi_n$ jest zbieżny słabo (według rozkładu) do $\xi$, jeżeli spełniony jest warunek:

$$P(\xi_{\eta}<x)\rightarrow P(\xi), \qquad F_{\xi_{n}}(x)\rightarrow F(x)$$

Zbieżność tą będziemy oznaczać jako:

$$\xi_n \xRightarrow[n \to \infty]{}\xi$$

## Twierdzenia o zbieżności

>[!danger] Lemat o zbieżności stałej
> Niech $C$ będzie stałą. Jeżeli $\xi _n→\xi =C$, to zachodzi:
>
> $$\left(\xi_n \xrightarrow[n \to \infty]{P} \xi \right) \iff \left(\xi_n \xRightarrow[n \to \infty]{}\xi\right)$$
>

>[!danger] Twierdzenie o ciągłym odwzorowaniu
> Niech $\xi_n \xrightarrow[n \to \infty]{P} \xi$ . Jeżeli funkcja $f(x)$ jest ciągła, to:
>
> $$f(\xi_n) \xrightarrow[n \to \infty]{P} f(\xi)$$
>

>[!danger] Twierdzenie Lévy'ego o ciągłości
> Niech $\xi_{n}$ będzie ciągiem zmiennych losowych, a $\varphi_{n}(t)$ odpowiadającym im ciągiem funkcji charakterystycznych. Jeżeli dla każdego $t \in \mathbb{R}$ istnieje granica punktowa:
>
> $$\lim_{n \to \infty} \varphi_n(t) = \varphi(t)$$
>
> oraz funkcja graniczna $\varphi(t)$ jest ciągła w punkcie $t = 0$, to $\varphi(t)$ jest funkcją charakterystyczną pewnej zmiennej losowej $\xi$, a ciąg zmiennych losowych $\xi_n$ jest zbieżny według rozkładu (słabo) do zmiennej $\xi$.

