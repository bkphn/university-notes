## Zmienne losowe
Zmienną losową nazywamy funkcję $\xi(\omega)$, która dla dowolnego elementarnego $\omega\in\Omega$ przyporządkowuje jej liczbę rzeczywistą, $\xi:\Omega\rightarrow\mathbb{R}$. Zmienną losową w skrócie oznaczamy symbolem $\xi$.

Aby funkcja $\xi$ byłą zmienną losową spełniony musi być warunek:

$$\{\omega :\xi(\omega)<x\}\in \mathcal{U},  \quad \forall_{x\in\mathbb{R}}$$

## Dystrybuanta zmiennej losowej
Funkcję $F_\xi(x)$ nazywamy dystrybuantą zmiennej losowej $\xi$. Dystrybuantę możemy oznaczać także skrótowo jako $F(x)$, definiujemy ją wzorem:

$$F(x)=P(\{\omega: \xi(\omega)<x\})=P(\xi<x)$$

Niech doświadczenie $S$ będzie jednokrotnym rzutem monetą, $\Omega=\{O, R\}$. Jako $\sigma$-algebrę przyjmujemy zbiór $\mathcal{U}=\{\emptyset, O, R, \Omega\}$. Przyjmijmy, że $\xi(O)=a, \xi(R)=b$, gdzie $a<b$.

Możemy powiedzieć, że:

$$\set{\omega: \xi(\omega)<x}=\begin{cases}
\emptyset, \quad x\leq a \\
O, \quad a<x \leq b \\
O,R, \quad b<x
\end{cases}$$

Tak określona funkcja $\xi(\omega)$ jest zmienną losową. Wyznaczmy jej dystrybuantę:
1. $x\leq a$

$$F(x)=P(\xi(\omega)<x)=P(\emptyset)=0$$

2. $a<x\leq b$

$$F(x)=P(\xi(\omega)<x)=P(\xi(\omega)=a)=P(O)=\frac{1}{2}$$

3. $b<x$

$$F(x)=P(\xi(\omega)<x)=P(\{\xi(\omega)=a\}\cup\{\xi(\omega)=b\})=P(O)+P(R)=1$$

Ostatecznie:

$$F(x)=\begin{cases}
0, \quad x\leq a \\
\frac{1}{2}, \quad a<x\leq b \\
1, \quad b<x
\end{cases}$$

## Własności dystrybuant
Dystrybuanta $F(x)$ spełnia następujące własności nazywane koniecznymi i dostatecznymi warunkami dla dystrybuant:
- **Monotoniczność**

$$x<y\implies F(x)\leq F(y)$$

- **Granice w nieskończonościach**

$$\lim_{x\rightarrow -\infty} F(x)=0$$

$$\lim_{ x \to \infty } F(x)=1$$

- **Lewostronna ciągłość**

$$\lim_{x\rightarrow x^-_{0}} F(x)=F(x_{0})$$

- **Prawdopodobieństwo przedziału**

$$P(\xi\in[a,b))=F(b)-F(a)$$

## Atomy dystrybuant
Mówimy, że dystrybuanta $F(x)$ posiada w punkcie $x_0$ **atom** o wielkości $p$ jeżeli w tym punkcie dystrybuanta posiada skok o długości $p$. Skok $p$ możemy obliczyć ze wzoru:

$$p=F(x_0+0)−F(x_0)$$

gdzie:

$$F(x_0+0)=\lim_{x\rightarrow x_0^+}⁡F(x)$$

Niech dystrybuanta $F_\xi(x)$ posiada atom o wielkości $p$ w punkcie $x_0$, wtedy:

$$P(ξ=x_0 )=p$$

## Typy dystrybuant
Możemy wyróżnić cztery różne typy dystrybuant, na zajęciach poznamy trzy z nich:
- **Dystrybuanta typu dyskretnego**: Dystrybuanta $F(x)$ jest dystrybuantą dyskretną, jeżeli dla dowolnego skończonego bądź przeliczalnego zbioru $\{x_1,x_2,\dots\}$ zachodzi:

$$\sum_{i=1}^\infty P(\xi=x_{i})=1$$

- **Dystrybuanta typu ciągłego**: Dystrybuanta $F(x)$ jest dystrybuantą ciągłą, gdy $F(x)$ jest funkcją ciągłą oraz zachodzi warunek:

$$P(\xi=x)=0, \quad \forall_{x\in\mathbb{R}}$$

- **Dystrybuanta typu absolutnie ciągłego**: Dystrybuanta $F(x)$ jest dystrybuantą absolutnie ciągłą, gdy jesteśmy w stanie ją przedstawić w postaci:

$$F(x)=\int_{-\infty}^x f(v)dv$$

Funkcję $f(v)$ nazywamy gęstością dystrybuanty.

## Twierdzenie Jordana
Niech $F_d$ oznacza dystrybuantę dyskretną, a $F_c$ dystrybuantę ciągłą. Dana jest liczba $0\leq p<1$, wtedy zachodzi twierdzenie Jordana.

>[!danger] Twierdzenie Jordana
> Każda dystrybuanta może być jednoznacznie przedstawiona w postaci:
>
> $$F(x)=p\cdot F_d (x)+(1−p)\cdot F_c (x)$$
>

## Gęstość dystrybuanty
Gęstością dystrybuanty nazywamy pochodną funkcji $F'(x)=f(x)$.

Jeżeli dystrybuanta jest typu absolutnie ciągłego, to możemy ją zapisać w postaci:

$$F(x)=\int_{-\infty}^x f(v) dv$$

Gęstość dystrybuanty spełnia następujące własności:
- $F(\infty)=\int_{-\infty}^\infty f(v) dv=1$
- $f(v)\geq 0$
- $\frac{dF}{dx}=f(v)$

Korzystając z gęstości możemy wyznaczyć prawdopodobieństwo dla $\xi\in[a,b]$:

$$P(\xi\in[a,b])=\int_{a}^b f(v) dv$$

A także dla dowolnego $\xi\in A$:

$$P(\xi\in A)=\int_{A} f(v) dv$$

## Charakterystyki liczbowe
Zmienne losowe $\xi,\eta$ nazywamy niezależnymi jeśli dla dowolnych $x,y\in\mathbb{R}$:

$$P(\xi<x, \eta<y)=P(\xi<x)P(\eta <y)$$

## Rozkłady
Rozkładem zmiennej losowej $\xi$ nazywamy miarę, która każdej możliwej do przyjęcia wartości przypisuje precyzyjną szansę na jej wystąpienie.

Możemy wyróżnić następujące rozkłady zmiennych losowych:
- **Rozkład zero-jedynkowy**: Mówimy, że zmienna losowa $\xi$ ma rozkład zero-jedynkowy, jeśli:

$$P(0)=p\geq0, \quad P(1)=q\geq0, \quad p+q=1$$

- **Rozkład geometryczny**: Mówimy, że zmienna losowa $\xi$ ma rozkład geometryczny, jeśli:

$$P(k)=p^k q=p^k (1−p), \quad P(n+k \mid \xi≥k)=P(n)$$

- **Rozkład Bernoullego**: Mówimy, że zmienna losowa $\xi$ ma rozkład Bernoullego (dwumianowy), jeśli:

$$P(k)=C_n^k p^k (1−p)^{n−k}$$

- **Rozkład Poissona**: Mówimy, że zmienna losowa $\xi$ ma rozkład Poissona z parametrem $\lambda$, jeśli:

$$P(k)=\frac{\lambda^k}{k!}\cdot e^{-\lambda}$$

- **Rozkład jednostajny**: Rozkładem jednostajnym albo prostokątnym nazywamy rozkład, którego gęstość określa wzór:

$$f(x)=\begin{cases}
\frac{1}{b-a}, \quad x\in [a,b] \\
0, \quad x\notin[a,b]
\end{cases}, \qquad F(x)=\begin{cases}
0, \quad x<a \\
\frac{x-a}{b-a}, \quad x\in[a,b] \\
1, \quad b<x
\end{cases}$$![[Pasted image 20260921231602.png|259]]

- **Rozkład wykładniczy**: Mówimy, że zmienna losowa $\xi$ ma rozkład wykładniczy o parametrze $\lambda$, jeśli jej gęstość jest funkcją postaci:

$$f(x)=\begin{cases}
\lambda e^{-\lambda x}, \quad x\geq 0 \\
0, \quad x<0 \\
\end{cases}, \qquad P(\xi>x+y \mid \xi>y)=P(\xi>x)$$![[Pasted image 20260921231744.png|253]]

- **Rozkład Gaussa**: Mówimy, że zmienna losowa $\xi$ ma rozkład Gaussa (normalny) o parametrach $m\in \mathbb{R}, \sigma>0$, jeśli jej gęstość jest funkcją postaci:

$$f(x)=\frac{e^{-\frac{(x-m)^2}{2\sigma}}}{\sigma \sqrt{ 2\pi }}$$

![[Pasted image 20260921231925.png|255]]
Fakt, że zmienna losowa $\xi$ ma rozkład Gaussa o parametrach $m,\sigma$ będziemy oznaczać jako:

$$\xi\in\mathcal{N}(m,\sigma^2)$$

innym często spotykanym oznaczeniem jest $\xi \sim \mathcal{N}(m,\sigma^2 )$.

Krzywą opisaną równaniem $y(x)=Ae^{-B(x-C)^2}$ nazywamy **krzywą Gaussa**. Rozkład Gaussa powszechnie stosuje się m.in. w analizowaniu i przewidywaniu postępowania pandemii.

- **Rozkład standardowy normalny**: Jeżeli $\xi\in \mathcal{N}(0, 1)$ to mówimy, że $\xi$ ma standardowy rozkład normalny, w tym przypadku dystrybuatnę oznaczmy symbolem $\Phi$ zamiast $F$, a gęstość $\varphi$ zamiast $f$.

$$\varphi(x)=\frac{e^{-\frac{x^2}{2}}}{\sqrt{ 2\pi }}, \qquad \Phi(x)=\int_{-\infty}^x \varphi(v)dv$$

![[Pasted image 20260921232440.png|276]]
