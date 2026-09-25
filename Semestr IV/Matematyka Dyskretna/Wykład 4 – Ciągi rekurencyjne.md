## Rekurencja
Rekurencja (łac. *recurrere*) to sposób definiowania procedur i funkcji polegający na umieszczeniu w jej treści odwołań do samej siebie.

W definicji rekurencyjnej podajemy jawnie pewną liczbę elementów, z których składa się dany obiekt, a następnie podajemy reguły definiowania pozostałych elementów przy pomocy elementów zdefiniowanych wcześniej.

## Funkcje rekurencyjne
Funkcja $f$ jest zdefiniowana rekurencyjnie, jeżeli:
- określono jawnie wartości dla pewnego zbioru argumentów funkcji,
- pozostałe wartości są definiowane za pomocą innych warunków początkowych oraz przeliczalnej liczbie zależności rekurencyjnych mają przeliczalną dziedzinę.

Podstawowe przykłady ciągów rekurencyjnych:
- **Silnia**

$$n=\begin{cases}
1, \qquad n=0 \\(n-1)!⋅n, \quad n \geq1
\end{cases}$$

- **Ciąg arytemtyczny**

$$a_{n}=\begin{cases}
a,\qquad n=0 \\ a_{n-1}+r, \quad n\geq 1
\end{cases}$$

-  **Ciąg geometryczny**

$$g_{n}=\begin{cases}
g, \qquad n=0 \\ g_{n-1}\cdot q, \quad n \geq 1
\end{cases}$$

## Ciąg Fibonacciego
Ciąg Fibonacciego, zaproponowany w 1202 roku przez Leonarda z Pizy określony był wzorem rekurencyjnym:

$$\begin{cases}
F_{0}=0 \\ F_{1}=1 \\ F_{n}=F_{n-2}+F_{n-1}, \qquad n\geq 0
\end{cases}$$

Początkowe wyrazy ciągu Fibonacciego wyglądają następująco:

$$0, 1, 1, 2, 3, 5, 8, 13, 21, 34, \dots$$

Ciąg Fibonacciego spełnia własności:
- $F_0+F_1+\dots+F_n=F_{n+2}−1$
- $F_0^2+F_1^2+\dots+F_n^2=F_n \cdot F_{n+1}$
- $F_{n+1} F_{n−1}=F_n^2+(−1)^n$
- $F_n^2+F_{n−1}^2=F_{2n−1}$
- $F_{n+1} F_m+F_n F_{m−1}=F_{m+n}$
- $\lim_{n\rightarrow \infty} \frac{F_{n+1}}{F_n}=\frac{1+\sqrt{5}}{2}=\varphi$

Ciąg ten w OEIS (*Online Encyclopedia of Integer Sequences*) jest opisany jako ciąg [ciąg A000045](https://oeis.org/A000045).

## Ciąg Catalana
Innym znanym ciągiem rekurencyjnym jest ciąg nazwany na cześć belgijskiego matematyka Eugène'a Catalana, ciąg ten definiuje się wzorem:

$$\begin{cases}
C_{0}=1 \\
C_{n}=\sum_{i=0}^{n-1} C_{i}C_{n-i-1}, \quad n\geq 1
\end{cases}$$

Początkowe wyrazy ciągu Catalana wyglądają następująco:

$$1, 1, 2, 5, 14, 42, 132, 429, 1430, 4862, \dots$$

Wzór jawny ciągu Catalana ma postać:

$$C_{n}=\binom{2n}{n}\frac{1}{n+1}$$

Ciąg ten w OEIS jest opisany jako ciąg [ciąg A000108](https://oeis.org/A000108).

## Funkcja 91 McCarthy'ego
Funkcja 91 McCarthy'ego nazywana czasem po prostu funkcją McCarthy'ego została zaproponowana w 1970 roku przez informatyka Johna McCarthy'ego. Funkcję tą definiuje się wzorem:

$$M(n)=\begin{cases}
M(M(n+11)), \quad 1\leq n<100 \\
n-10, \qquad n>100
\end{cases}$$

Początkowe wyrazy funkcji McCarthy'ego wyglądają następująco:

$$\underbrace{91, 91, \dots, 91, 91}_{\text{101 powtórzeń}}, 92, 93, 94, 95, 96, 97, 98, 99, 100, 101, \dots$$

Funkcja McMarthy'ego jest powszechnie stosowana przy analizie i testowaniu algorytmów. Najczęściej funkcję McCarthy'ego stosuje się do testowania czy kod jest wolny od błędów. Funkcja 91 jest testem dla automatów dowodzących, jeżeli uda się udowodnić, że dla każdego $n\leq100$ funkcja $M(n)=91$, to sugeruje, że kod jest pozbawiony błędów.

Ciąg ten w OEIS jest opisany jako ciąg [ciąg A103847](https://oeis.org/A103847).

## HAKMEM – Item 134
Sposób działania tego ciągu został umieszczony w informatycznym dokumencie HAKMEM, pod indeksem 134. Dokument ten zauważa ciekawą zależność między długością słowa, a kolejnymi liczbami. 

**Ciąg tworzymy następująco:** Niech $a_0$ będzie dowolną liczbą naturalną i niech $a_{n+1}$  będzie liczbą liter potrzebnych do zapisu liczby $a_n$ w języku angielskim. Przykładowo dla $a_0=33$ otrzymujemy:

$$33, 11, 6, 3, 5, 4, 4, 4, \dots$$

## Problem Collatza
Inną znaną funkcją określoną rekurencyjnie jest tzw. problem Collatza. Aby utworzyć ciąg Collatza wybieramy dowolną naturalną liczbę $a_0$. A kolejne wyrazy ciągu obliczamy ze wzoru rekurencyjnego:

$$a_{n+1}=\begin{cases}
\frac{1}{2}\cdot a_{n}, \qquad 2 \mid a_{n} \\
3a_{n}+1, \quad 2 \nmid a_{n}
\end{cases}$$

Problem Collatza polega na udowodnieniu bądź obaleniu tezy, że dla dowolnego $a_0\in\mathbb{N}$, ciąg ten zawsze wpadnie finalnie w cykl $[4,2,1]$. Jest to jeden z największych, nie rozwiązanych do tej pory problemów matematycznych. Przykładowo dla $a_0=12$ otrzymujemy ciąg:

$$12, 6, 3, 10, 5, 16, 8, 4, 2, 1, 4, 2, 1, 4, 2, 1, 4, 2, 1,\dots$$

## Zależności II rzędu
Jednorodną liniową zależnością rekurencyjnę II rzędu o stałych współczynnikach nazywamy zależność postaci:

$$a_{n}=Aa_{n-1}+Ba_{n-2}$$

gdzie $n\geq n_0$, $A,B\in\mathbb{C}, B\neq 0$.

**Równaniem charakterystycznym** dla $a_n=Aa_{n−1}+Ba_{n−2}$  nazywamy równanie w postaci:

$$r^2−Ar−B=0$$

Wielomian $r^2−Ar−B$ nazywamy wielomianem charakterystycznym zależności

$$a_n=Aa_{n−1}+Ba_{n−2}$$

Niech ciąg $a_n$ spełnia zależność rekurencyjną II rzędu.
- Jeśli równanie charakterystyczne ma dwa różne rozwiązania $r_1,r_2$, to:

$$a_n=C⋅r_1^n+D⋅r_2^n$$

- Jeśli równanie charakterystyczne ma jedno rozwiązanie $r_0$, to:

$$a_n=(C+Dn)⋅r_0^n$$

Aby wyznaczyć stałe $C,D$ musimy skorzystać z podstawienia warunków początkowych, zwyczajowo $a_0,a_1$.

## Zależności *k*-tego rzędu:
Jednorodną liniową zależnością rekurencyjną $k$-tego rzędu o stałych współczynnikach nazywamy zależność postaci:

$$a_n=A_1 a_{n−1}+A_2 a_{n−2}+\dots+A_k a_{n−k}$$

gdzie $n\geq n_0,   A_1,A_2,…,A_k\in\mathbb{C}, A_k\neq0$

**Równaniem charakterystycznym** dla $a_n=A_1 a_{n−1}+A_2 a_{n−2}+\dots+A_k a_{n−k}$  nazywamy równanie w postaci:

$$r^k−A_1 r^{k−1}−A_2 r^{k−2}−\dots−A_{k−1}r−A_k=0$$

Niech ciąg $a_n$ spełnia zależność rekurencyjną $k$-tego rzędu i niech $f(r)=(r−r_1 )^{m_1} (r−r_2 )^{m_2}\dots(r−r_s )^{m_s}$ będzie wielomianem charakterystycznym. Wówczas

$$a_n=(A_{1,1}+A_{1,2} n+\dots+A_{1,m_1} n^{m_1−1} ) r_1^n+…+(A_{s,1}+A_{s,2}n+\dots+A_{s,m_s} n^{m_s−1} ) r_s^n$$

 Aby wyznaczyć stałe $A_{i,j}$ możemy skorzystać z wartości początkowych.

