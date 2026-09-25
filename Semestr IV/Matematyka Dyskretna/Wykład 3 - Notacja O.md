## Asymptotyka
Asymptotyką nazywamy badanie zachowania funkcji w przypadku gdy dąży ona do nieskończoności.

Jeżeli funkcje $f(n)$, $g(n)$, zachowują się w identyczny sposób, dla dużych $n$, to mówimy, że są asymptotycznie równe i zapisujemy jako $f(n) \sim g(n)$. Aby dwie funkcje były asymptotycznie równe granica ich ilorazu musi być równa $1$:

$$f(n)\sim g(n)\iff\lim_{n_ \to \infty} \frac{f(n)}{g(n)}=1$$

## Hierarchia funkcji
Niech $n\in\mathbb{N}$. Dla dowolnych liczb $\alpha,\beta$ takich, że $0\leq\alpha\leq\beta$ prawdziwa jest nierówność:
$n^\alpha \leq n^\beta$. Korzystając z tego faktu możemy udowodnić, że $n<2^n$, zależność tą w łatwy sposób można uogólnić do postaci $n^\alpha<2^n$. 

Logarytmując obustronnie nierówność $n^\alpha<2^n$ możemy udowonić, że $\log_{2}n^\alpha<n$. Łatwo możemy udowodnić, że $2^n<n!$, na podstawie czego, finalnie możemy wykazać, że $n!<n^n$. Wszystkie z powyższych nierówności zachodzą oczywiście dla wystarczająco dużych $n$. Mówimy wtedy o asymptotycznym wzroście funkcji. 

Z powyższych faktów możemy ułożyć hierarchię tempa wzrostu funkcji:

$$1<\log_\alpha n < \sqrt[n]{α}<n<n^\alpha<\alpha^n<n!<n^n<…$$

gdzie $\alpha\in\mathbb{N}$ jest stałą, a $n$ wystarczająco dużą liczbą naturalną.

## Notacja dużego $\mathcal{O}$
Niech $f,g$ będą funkcjami dyskretnymi (ciągami). Jeżeli dla dowolnie dużego argumentu funkcja $f_n$ rośnie nieszybciej niż funkcja $g_n$ to mówimy, że $f_n$ jest $\mathcal{O}$ od $g_n$ i zapisujemy to jako:

$$f_n=\mathcal{O}(g_n)$$

Ściśle rzecz ujmując warunek ten jest spełniony gdy możemy znaleźć taką stałą $C$, że od pewnego $n$

$$f_n=\mathcal{O}(g_n )\iff\exists_{C\in\mathbb{R}} :|f_n |<C⋅|g_n |$$

Notacja $\mathcal{O}$ służy do szacowania szybkości wzrostu rozpatrywanego ciągu poprzez porównanie jej z szybkością wzrostu prostszego ciągu.

> [!example] Wyznaczanie tempa wzrostu ciągu w notacji $\mathcal{O}$
> Wyznacz tempo wzrostu ciągu $a_n = 2n^5 + 9n^3 + 2026$.
> 
> Aby formalnie wykazać, że $a_n = \mathcal{O}(n^5)$, musimy udowodnić, że istnieje stała $c > 0$ oraz próg $n_0$, od którego dla każdego $n \ge n_0$ zachodzi nierówność $a_n \le c \cdot n^5$ [cite: 1.1.7]. 
> 
> Zakładając, że $n$ jest odpowiednio duże (np. $n \ge 6$, co sprawia, że $n^5 > 9n^3 + 2026$), możemy zastosować następujące oszacowanie:
>
> $$
> \begin{align*}
> a_n &= 2n^5 + 9n^3 + 2026 \\
> &\le 2n^5 + n^5 \\
> &= 3n^5 
> \end{align*}
> $$
>
> Ponieważ dla wszystkich $n \ge 6$ zachodzi $a_n \le 3n^5$, ostateczny wynik to:
>
> $$a_n = \mathcal{O}(n^5)$$
>

Warto zauważyć, że zgodnie z definicją dużego $\mathcal{O}$ nasz ciąg $f_n$ może mieć nieskończenie wiele ograniczeń górnych. Przykładowo dla powyższego ciągu $a_n=2n^5+9n^3+2026$ możemy powiedzieć, że: $a_n=\mathcal{O}(n^5 )$, ale równie prawdziwe będą równania:
- $a_n=\mathcal{O}(n!)$
- $a_n=\mathcal{O}(n^n )$
- $a_n=\mathcal{O}(n^6 )$
- $a_n=\mathcal{O}(2n^5 )$
	$\vdots$

Dobrym zwyczajem jest jednak wybieranie jak najmniejszego możliwego tempa wzrostu.

## Szereg harmoniczny
Ciąg $h_{n}$ sum kolejnych odwrotności liczb naturalnych nazywamy **ciągiem harmonicznym**, który definiujemy wzorem:

$$h_{n}=\sum_{i=1}^n \frac{1}{i}$$

Początkowe wyrazy ciągu harmonicznego to:

$$\frac{1}{1},\frac{3}{2},\frac{11}{6}, \frac{25}{12}, \frac{137}{60}, \frac{49}{20},\cdots$$

Szereg ten jest rozbieżny, możemy natomiast zbadać tempo jego wzrostu. Zauważmy, że $h_{2k}<k+1$ niech $n$ będzie liczbą ograniczoną kolejnymi potęgami dwójki $2^k<n≤2^{k+1}$.  Dla dostatecznie dużych $n$ zachodzi $\log_{2}n+2<\log_{2}n+\log_{2}n=2\log_{2}n$, na podstawie tego faktu, możemy powiedzieć, że:

$$h_{n}=\mathcal{O}(\log_{2}⁡n)$$

## Własności notacji $\mathcal{O}$
Dane są dwie funkcje dykretne $f_n,g_n$ oraz dowolna stała $C$. Możemy wtedy powiedzieć, że zachodzą poniższe własności:
1. Jeżeli $f_n=\mathcal{O}(a_n )$, to:

$$C\cdot f_n=\mathcal{O}(a_n )$$

2. $f_n=\mathcal{O}(a_n )$ i $g_n=\mathcal{O}(a_n )$, to:

$$f_n+g_n=caly(a_n )$$

3. Jeżeli $f_n=\mathcal{O}(a_n)$ i $g_n=\mathcal{O}(b_n )$, to:

$$f_n+g_n=\mathcal{O}(\max \set{|a_n|, |b_n|})$$

$$f_n\cdot g_n=\mathcal{O}(a_n\cdot b_n)$$

4. Jeżeli $a_n=\mathcal{O}(b_n )$ i $b_n=\mathcal{O}(c_n )$, to:

$$a_n=\mathcal{O}(c_n)$$

## Inne notacje
Notacja dużego $\mathcal{O}$ jest tą najczęściej stosowaną, jednak nie jest jedyną notacją asymptotyczną. Donald Knuth zaproponował spójną notację, gdzie oprócz dużego $\mathcal{O}$ możemy jeszcze wyróżnić notację dużej $\Omega$ oraz dużej $\Theta$. Istnieją także notacje małego $\omicron$ oraz małej $\omega$ zaproponowane przez Edmunda Landau.

Najpopularniejsze notacje asymptotyczne wraz z warunkami, które muszą zostać spełnione dla od n:
- **Notacja dużego $\mathcal{O}$**
	Mówi o górnym ograniczeniu tempa wzrostu danej funkcji. Wiemy, że funkcja $f_n$ będzie rosła nie szybciej niż $g_n$.

	$$f_n=\mathcal{O}(g_n )\iff \exists_{C\in\mathbb{R}}:|f_n |\leq C⋅|g_n |$$

- **Notacja dużej $\Omega$**
	Mówi o dolnym ograniczeniu tempa wzrostu danej funkcji. Wiemy, że funkcja $f_n$ będzie rosła nie wolniej niż $g_n$.

	$$f_n=\Omega(g_n )\iff\exists_{D\in\mathbb{R}}   :D\cdot|g_n |\leq|f_n|$$

- **Notacja dużej $\Theta$**
	Mówi o dokładnym tempie wzrostu danej funkcji. Wiemy, że funkcja $f_n$ będzie rosła tak samo szybko $g_n$.

	$$f_n=\Theta(g_n )\iff\exists_{C,D\in\mathbb{R}} : D\cdot|g_n |\leq|f_n|\leq C\cdot|g_n|$$

- **Notacja małego $\omicron$**
	W odróżnieniu do notacji wielkiego $\mathcal{O}$ notacja małego $\omicron$ wyklucza możliwość, że funkcja rośnie w tym samym tempie. Wiemy, że funkcja $f_n$ będzie rosła wolniej niż $g_n$.

	$$f_n=\omicron(g_n )\iff\forall_{C\in\mathbb{R}} :|f_n|<C\cdot|g_n|$$

- **Notacja małej $\omega$**
	Tak samo jak notacja małego $\omicron$, notacja małej $\omega$ wyklucza możliwość tego samego tempa wzrostu funkcji.

	$$f_n=\omega(g_n )\iff \forall_{D\in\mathbb{R}} :D\cdot|g_n |<|f_n |$$

