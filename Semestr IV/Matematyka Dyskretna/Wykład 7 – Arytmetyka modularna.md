## Arytmetyka modulularna
Niech $m\in\mathbb{N}_{+}\setminus\{1\}$  i $a,b\in\mathbb{Z}$. Mówimy, że $a$ przystaje do $b$ modulo $m$, jeżeli $a$ i $b$ mają taką samą resztę z dzielenia przez $m$, co zapisujemy jako:

$$a\equiv_{m} b$$

lub

$$a=b\mod{m}$$

Liczbę $m$ nazywamy **modułem**.

Możemy powiedzieć, że $a$ przystaje do $b$ modulo $m$ wtedy i tylko wtedy, gdy liczba $m$ dzieli różnicę liczb $a$ i $b$:

$$a\equiv_m b\iff m|(a−b)$$

## Klasy abstrakcji
Z definicji przystawania modulo $m$ wynika, że każda liczba całkowita przystaje modulo $m$ do dokładnie jednej liczby ze zbioru reszt z dzielenia przez $m$, czyli zbioru $\mathbb{Z}_m=\{0, 1, \cdots, m−1\}$  (zbiór $\mathbb{Z}_m$ formalnie oznacza się jako $\mathbb{Z}/m\mathbb{Z}$). Każda z tych reszt określa klasę abstrakcji relacji przystawania. Klasę abstrakcji liczby $a$ oznaczamy jako $[a]_m$ i definujemy jako:

$$[a]_m=\{a+km :k\in\mathbb{Z}\}$$

Na zbiorze $\mathbb{Z}_m$ klas abstrakcji relacji przystawania modulo $m$ definiujemy działania:
- **Suma modularna**

$$[a]_m +_m [b]_m=[a+b]_m$$

- **Iloczyn modularny**

$$[a]_m \cdot_m [b]_m=[a\cdot b]_m$$

Struktura $(\mathbb{Z}_m,+_m,  ⋅_m )$  tworzy pierścień przemienny z jedynką, którą nazywamy pierścieniem reszt modulo $m$.

## Równania modularne
Równanie $ax=b \mod{m}$ ma rozwiązanie w $\mathbb{Z}_{m}$ wtedy i tylko wtedy, gdy $\operatorname{NWD}(a,m)\vert b$.

Jeżeli $x_0$ jest rozwiązaniem równania $ax=b\mod{m}$, to liczba różnych rozwiązań tego równania w $\mathbb{Z}_m$ wynosi $\operatorname{NWD}(a,m)$ = a każde rozwiązanie ma postać:

$$x_{t}=x_{0}+_{m} \frac{t\cdot m}{\operatorname{NWD}(a,m)},\qquad t\in\{0, 1, \dots, \operatorname{NWD}(a,m)-1\}$$

Niech $a,b,c,d\in\mathbb{Z}$ i $m,k\in\mathbb{N}\setminus\{1\}$, relacja przystawania modulo $m$ spełnia własności:
- $a\equiv_m b\iff ak\equiv_{mk} bk$
- $a\equiv_m b\implies  ac\equiv_m bc$
- $ac\equiv_m bc \land  c\perp m\implies  a\equiv_m b$
- $a\equiv_{mk} b\implies  a\equiv_m b\land a\equiv_k b$
- $a\equiv_m b \land  a\equiv_k b  m\perp k\implies  a\equiv_{mk} b$

## Odwrotności modularne
Liczbę $a^{−1}$ w $\mathbb{Z}_m$ nazywamy odwrotnością modulo $m$ liczby $a$, liczba ta musi spełniać własność:

$$a^{−1} \cdot_m a\equiv_m 1$$

Równanie to jest oczywiście równaniem diofantycznym $xa=1 \mod{m}$. Wiemy, że rozwiązanie istnieje jeżeli $x\perp m$.

> [!example] Wyznaczanie $7^{-1}$ w $\mathbb{Z}_{15}$
> $$\begin{align*}
> 7^{-1} &= x\\
> 7x &\equiv_{15} 1 \quad / \cdot 2 \\
> 14x &\equiv_{15} 2 \\
> -1x &\equiv_{15} 2 \quad / \cdot (-1) \\
> x &\equiv_{15} -2 \\
> x &\equiv_{15} 13
> \end{align*}
> $$
>

## Twierdzenia
W analizie równań modularnych mogą pomóc następujące twierdzenia:
>[!danger] Twierdzenie Eulera
>Dla $a\in\mathbb{Z}$ i $m\in\mathbb{N}_+\setminus\{1\}$ takich, że $a\perp m$ zachodzi:
>
>$$a^{\varphi(m)}  \equiv_m 1$$
>

>[!danger] Małe twierdzenie Fermata
>Dla $a\in\mathbb{Z}$ i $p\in\mathbb{P}$ takich, że $a\perp p$ zachodzi:
>
>$$a^{p−1} \equiv_p 1$$
>

## Ostatnie cyfry
Chąc wyznaczyć ostatnią cyfrę pewnej liczby $a^b$ możemy zauważyć, że zadanie to jest równoznaczne z wyznaczeniem wartości $a^b \mod{10}$, analogicznie chcąc wyznaczyć $k$ ostatnich cyfr od końca liczby $a^b$ musielibyśmy wyznaczyć wartość $a^b \mod{10^k}$.

> [!example] Szukanie ostatniej cyfry potęgi
> **Znajdź ostatnią cyfrę liczby $7^{2022}$**
> 
> $$7^{2022} \equiv_{10} (7^2)^{1011} \equiv_{10} (49)^{1011} \equiv_{10} (-1)^{1011} \equiv_{10} -1 \equiv_{10} 9$$
>

## Algorytm szybkiego potęgowania modularnego
Algorytm szybkiego potęgowania modularnego służy do wyznaczania wartości $a^n$  w $\mathbb{Z}_m$  dla dużych wartości $m,n$. Polega on na iteracyjnym wyznaczaniu wartości modulo funkcji rekurencyjnej:

$$G(n)=\begin{cases}
a, \qquad n=1 \\
\left(G\left(\frac{n}{2} \right)\right)^2, \qquad n=2k \\
a\cdot\left(G\left(\frac{n-1}{2}\right)\right)^2, \qquad n=2k+1 \\
\end{cases}$$

Algorytm prezentuje się następująco:
>[!abstract] Algorytm szybkiego potęgowania modularnego
> 1. **Podstawiamy pod liczbę $w$**
>
> $$w\leftarrow a$$
>
> 2. **Wyznaczamy reprezentację binarną liczby $n$**
>
> $$n=(n_s n_{s−1}\dots n_1 n_0 )_{(2)}$$
>
> 3. **Dla każdego $i\in\{s−1, s−2, \dots,1, 0\}$:**
> 	- Jeżeli $n_i=0$: $\quad w\leftarrow w^2\mod{m}$
> 	- Jeżeli $n_i=1$: $\quad w\leftarrow w^2\cdot a \mod{m}$
> 4. **Wynik to liczba** $w$:
>
> $$a^n=w$$
>

> [!example] Wyznaczanie dwóch ostatnich cyfr potęgi algorytmem szybkiego potęgowania
> **Wyznacz dwie ostatnie cyfry liczby $7^{2022}$**
> 
> **1. Podstawiamy pod liczbę $w$**
>
> $$w \leftarrow 7$$
>
> **2. Wyznaczamy reprezentację binarną liczby $n$**
>
> $$2022 = 11111100110_{(2)}$$
>
> **3. Obliczamy kolejne wartości $w$**
> 
> | **Bit** | **Obliczenia** |
> | :---: | :--- |
> | **1** | $w \leftarrow 7$ |
> | **1** | $w \leftarrow 7^2 \cdot 7 = 343 \equiv_{100} 43$ |
> | **1** | $w \leftarrow 43^2 \cdot 7 = 12943 \equiv_{100} 43$ |
> | **1** | $w \leftarrow 43^2 \cdot 7 = 12943 \equiv_{100} 43$ |
> | **1** | $w \leftarrow 43^2 \cdot 7 = 12943 \equiv_{100} 43$ |
> | **1** | $w \leftarrow 43^2 \cdot 7 = 12943 \equiv_{100} 43$ |
> | **0** | $w \leftarrow 43^2 = 1849 \equiv_{100} 49$ |
> | **0** | $w \leftarrow 49^2 = 2401 \equiv_{100} 1$ |
> | **1** | $w \leftarrow 1^2 \cdot 7 = 7 \equiv_{100} 7$ |
> | **1** | $w \leftarrow 7^2 \cdot 7 = 343 \equiv_{100} 43$ |
> | **0** | $w \leftarrow 43^2 = 1849 \equiv_{100} 49$ |
> 
> **4. Wynik**
>
> $$7^{2022} \bmod 100 = 49$$
>

## Chińskie twierdzenie o resztach
Niech $m_1,m_2,\dots,m_n\in\mathbb{N}_+\setminus\{1\}$ będą parami względnie pierwsze oraz niech $r_1,r_2,\dots,r_n\in\mathbb{Z}$. Wtedy układ równań:

$$\begin{cases}
x \equiv_{m_1} r_1 \\
x \equiv_{m_2} r_2 \\
\vdots \\
x \equiv_{m_n} r_n
\end{cases}$$

ma dokładnie jedno rozwiązanie modulo $M=m_1\dots m_2\cdot \dots \cdot m_n$ postaci:

$$x=\sum_{i=1}^n N_i M_i$$

gdzie $M_i=\frac{M}{m_i}$ oraz $N_i$ jest rozwiązaniem równania $M_i N_i \equiv_{m_i} r_i$.

Oczywiście rozwiązania rozpatrywanego układu równań w zbiorze liczb całkowitych mają postać:

$$x=M_{t}+\sum_{i=1}^n N_{i}M_{i}, \qquad t\in\mathbb{Z}$$

> [!example] Wyznacz najmniejszą liczbę naturalną spełniającą układ
> $$
> \begin{cases}
> x \equiv_2 1 \\
> x \equiv_3 1 \\
> x \equiv_5 3
> \end{cases}
> $$
>
> $$
> \begin{align*}
> m_1 &= 2, \quad &m_2 &= 3, \quad &m_3 &= 5 \\
> r_1 &= 1, \quad &r_2 &= 1, \quad &r_3 &= 3
> \end{align*}
> $$
>
> $$
> \begin{align*}
> M &= 2 \cdot 3 \cdot 5 = 30 \\
> M_1 &= \frac{2 \cdot 3 \cdot 5}{2} = 15 \\
> M_2 &= \frac{2 \cdot 3 \cdot 5}{3} = 10 \\
> M_3 &= \frac{2 \cdot 3 \cdot 5}{5} = 6
> \end{align*}
> $$
>
> $$
> \begin{align*}
> 15 \cdot N_1 &\equiv_2 1 \Rightarrow N_1 = 1 \\
> 10 \cdot N_2 &\equiv_3 1 \Rightarrow N_2 = 1 \\
> 6 \cdot N_3 &\equiv_5 3 \Rightarrow N_3 = 3
> \end{align*}
> $$
>
> $$x = 1 \cdot 15 + 1 \cdot 10 + 3 \cdot 6 = 43 \equiv_{M=30} 13$$
>

## Złowrogie liczby
Złowrogą liczbą (ang. *evil number*) nazywamy dowolną liczbę naturalną $n$, w której zapisie binarnym występuje parzysta liczba jedynek. Liczby naturalne, w których zapisie występuje nieparzysta liczba jedynek nazywamy liczbami nienawistnymi (ang. *odious number*).

Matematycznie rzecz ujmując, mówimy że liczba $n$ jest złowroga, jeżeli spełnia warunek:

$$2 \vert w_{H}(n_{(2)})$$

gdzie $n_{(2)}$ oznacza binarną reprezentację liczby $n$, a $w_H$ jest wagą Hamminga.

Początkowe liczby złowrogie, to:

$$0, 3, 5, 6, 9, 10, 12, 15, 17, 18, 20, 23, 24, 27, 29, 30, 33, 34, 36, 39,\dots$$

## Ciąg Thuego-Morse'a
Ciąg Thuego-Morse'a jest binarnym ciągiem liczbowym wykorzystującym uzupełnienie binarne.
Ciąg ten oznaczamy jako $T_n$ i definiujemy rekurencyjnie:

$$T_{n}=\begin{cases}
0, \qquad n=0 \\
T_{n-1} \overline{T_n-1}, \quad n\geq 1
\end{cases}$$

Pierwsze wyrazy ciągu prezentują się następująco:
0. $T_0=0$
1. $T_1=0\overline{0}=01$
2. $T_2=01\overline{01}=0110$
3. $T_3=0110\overline{0110}=01101001$
4. $T_4=01101001\overline{01101001}=0110100110010110$
	$\vdots$

Wartość $T_{\infty}=\lim_{ n \to \infty } T_{n}$ nazywamy **słowem Thuego-Morse'a**.

$$T_\infty=0110100110010110100101100110100110010110011010010110100110010110\dots$$

Niech $t_i$ oznacza $i$-tą cyfrę słowa $T_\infty$. Dla dowolnego indeksu $i$ jeżeli $t_i=0$ to liczba $i$ jest liczbą złowrogą, natomiast jeżeli $t_i=1$, to liczba $i$ jest liczbą nienawistną.

