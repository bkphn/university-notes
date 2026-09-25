## Potęgi kroczące
Niech $m\in\mathbb{N}$.
**Dolną silnią** nazywamy wyrażenie w postaci:

$$x^\underline{m}=x\cdot(x-1)\cdot(x-2)\cdot\dots\cdot(x-m+1)$$

co czytamy jako $x$ *do* $m$-tej ubywającej.

**Górną silnią** nazywamy wyrażenie w postaci:

$$x^\overline{m}=x\cdot(x+1)\cdot (x+2)\cdot\dots \cdot(x+m-1)$$

Co czytamy jako $x$ do $m$-tej przybywającej.

> [!example] Przykłady
> $$
> \begin{align*}
> 5^{\underline{3}} &= 5 \cdot 4 \cdot 3 = 60 \\
> 5^{\overline{3}} &= 5 \cdot 6 \cdot 7 = 210 \\
> 4^{\underline{5}} &= 4 \cdot 3 \cdot 2 \cdot 1 \cdot 0 = 0
> \end{align*}
> $$
>

W uogólnieniu możemy zauważyć, że:

$$n!=n^\underline{n}=1^\overline{n}$$

Potęg kroczących możemy także używać do zapisu wielomianów:

$$x^\underline{3}=x\cdot (x−1)\cdot (x−2)=x^3−3x^2+2x$$

$$x^\overline{3}=x\cdot (x+1)\cdot (x+1)=x^3+3x^2+2x$$

## Liczby podzbiorowe Stirlinga
Podziałem skończonego zbioru $S$ nazywamy rodzinę parami rozłącznych podzbiorów $S_1,S_2,\dots,S_k$  zbioru $S$ taką, że:

$$S_1\cup S_2\cup \dots\cup S_k=S$$

Liczbę sposobów podziału $n$-elementowego zbioru na $k$ niepustych podzbiorów nazywamy **liczbą Stirlinga II rodzaju**, bądź **liczbą podzbiorową Stirlinga**. Oznaczamy ją jako $\left\{ \begin{matrix} n \\ k \end{matrix} \right\}$ i czytamy $k$ *podzbiorów* $n$.

> [!example] Wyznaczanie $\begin{Bmatrix} 4 \\ 2 \end{Bmatrix}$
> Przyjmijmy czteroelementowy zbiór $\{a, b, c, d\}$.
> 
> Cztery elementy możemy podzielić na rozłączne podzbiory na dwa sposoby: utworzyć grupy 1- i 3-elementowe albo dwie grupy 2-elementowe.
>
> $$4 = 1 + 3 = 2 + 2$$
>
> **Podział 1 + 3:** 
> $\{\{a\}, \{b, c, d\}\}, \quad \{\{b\}, \{a, c, d\}\}, \quad \{\{c\}, \{a, b, d\}\}, \quad \{\{d\}, \{a, b, c\}\}$
> 
> **Podział 2 + 2:** 
> $\{\{a, b\}, \{c, d\}\}, \quad \{\{a, c\}, \{b, d\}\}, \quad \{\{a, d\}, \{b, c\}\}$
> 
> Sumując wszystkie możliwe podziały, otrzymujemy:
>
> $$\begin{Bmatrix} 4 \\ 2 \end{Bmatrix} = 4 + 3 = 7$$
>

Dla małych $k$ wyrażenie $\left\{\begin{matrix} n \\ k \end{matrix} \right\}$ przyjmuje wartości:
- Dla $n=0$

$$\left\{\begin{matrix} 0 \\ k \end{matrix} \right\}=0, \qquad\forall_{k\in\mathbb{Z}}$$

- Dla $k<0$

$$\left\{\begin{matrix} n \\ k \end{matrix} \right\}=0, \qquad \forall_{k\in\mathbb{Z}}$$

- Dla $k=0$

$$\left\{\begin{matrix} n \\ 0 \end{matrix} \right\}=0, \qquad \forall_{n\in\mathbb{N}}$$

- Dla $k=1$

$$\left\{\begin{matrix} n \\ 1 \end{matrix} \right\}=1, \qquad \forall_{n\in\mathbb{N}_{+}}$$

- Dla $k=2$

$$\left\{\begin{matrix} n \\ 2 \end{matrix} \right\}=\left\{\begin{matrix} n-1 \\ k-1 \end{matrix} \right\}+k\cdot\left\{\begin{matrix} n-1 \\ k \end{matrix} \right\}$$

Dla $n>0$ zachodzi zależność rekurencyjna:

$$\left\{\begin{matrix} n \\ k \end{matrix} \right\}=\left\{\begin{matrix} n-1 \\ k-1 \end{matrix} \right\}+k\cdot\left\{\begin{matrix} n-1 \\ k \end{matrix} \right\}$$

## Liczby cykliczne Stirlinga
Cyklem nazywamy cykliczne ustawienie elementów danego zbioru. Przykładowo jednym z cykli zbioru $\{A,B,C,D\}$ jest cykl $A\rightarrow D\rightarrow B\rightarrow C$, co zapisujemy jako $[A,D,B,C]$. Oczywiście prawdziwa jest równość:

$$[A,D,B,C]=[D,B,C,A]=[B,C,A,D]=[C,A,D,B]$$

Liczbę sposobów na rozmieszczenie $n$ elementów w $k$ rozłącznych cyklach zapisujemy jako $\left[\begin{matrix} n \\ k \end{matrix} \right]$ i czytamy jako $k$ *cykli* $n$.

> [!example] Wyznaczanie $\begin{bmatrix} 4 \\ 2 \end{bmatrix}$
> Przyjmijmy czteroelementowy zbiór $\{a, b, c, d\}$.
> 
> Szukamy permutacji rozkładających się na dokładnie 2 rozłączne cykle. Możemy wyznaczyć następujące cykle zbioru $\{a, b, c, d\}$:
> 
> **Podział na cykle o długości 1 i 3:**
> $[a][b, c, d]$, $\quad [b][a, c, d]$, $\quad [c][a, b, d]$, $\quad [d][a, b, c]$
> $[a][b, d, c]$, $\quad [b][a, d, c]$, $\quad [c][a, d, b]$, $\quad [d][a, c, b]$
> 
> **Podział na cykle o długości 2 i 2:**
> $[a, b][c, d]$, $\quad [a, c][b, d]$, $\quad [a, d][b, c]$
> 
> Sumując wszystkie możliwe układy, otrzymujemy:
>
> $$\begin{bmatrix} 4 \\ 2 \end{bmatrix} = 11$$
>

Dla małych $k$ wyrażenie $\left[\begin{matrix} n \\ k \end{matrix} \right]$ przyjmuje wartości:
- Dla $n,k=0$

$$\left[\begin{matrix} 0 \\ 0 \end{matrix} \right]=1$$

- Dla $n=0$

$$\left[\begin{matrix} 0 \\ k \end{matrix} \right]=0, \qquad \forall_{k\in\mathbb{Z}\setminus\set{0}}$$

- Dla $k<0$

$$\left[\begin{matrix} n \\ k \end{matrix} \right]=0, \qquad \forall_{n\in\mathbb{N}}$$

- Dla $k=0$

$$\left[\begin{matrix} n \\ 0 \end{matrix} \right]=0 , \qquad\forall_{n\in\mathbb{N}_{+}}$$

- Dla $k=1$

$$\left[\begin{matrix} n \\ 1 \end{matrix} \right]=\frac{n!}{n}=(n-1)!, \qquad \forall_{n\in\mathbb{N}_{+}}$$

Dla $n>0$ zachodzi zależność rekurencyjna:

$$\left[\begin{matrix} n \\ k \end{matrix} \right]=\left[\begin{matrix} n-1 \\ k-1 \end{matrix} \right]+(n-1)\left[\begin{matrix} n-1 \\ k \end{matrix} \right]$$

## Trójkąty Strilinga
Na bazie liczb Stirlinga możemy utworzyć tzw. trójkąty Stirlinga w sposób analogiczny do trójkąta Pascala.

**Trójkąt Stirlinga dla podzbiorów**
![[Pasted image 20260905190842.png|284]]

**Trójkąt Stirlinga dla cykli**
![[Pasted image 20260905190857.png|285]]

Aby ręcznie stworzyć trójkąty Stirlinga można posłużyć się następującymi regułami:
- **Trójkąt Stirlinga dla cykli**: Aby utworzy element w wierszu $m$ należy dodać do siebie dwie wartości powyżej, przy czym ta prawa powinna być pomnożona przez $(m−1)$.

- **Trójkąt Stirlinga dla podzbiorów**: Aby utworzy element w wierszu $m$ należy dodać do siebie dwie wartości powyżej, przy czym ta prawa powinna być pomnożona przez indeks, który wyznaczamy numerując kolejne elementy wiersza od $0$, zaczynając od prawej strony.

Trójkąty Stirlinga (podobnie jak trójkąt Pascala) można wykorzystywać do wyznaczania współczynników w pewnym wielomianie.

Liczbę $x^n$ możemy wyrazić jako:

$$x^n=\sum_{k=0}^n\left\{\begin{matrix} n \\ k \end{matrix} \right\}x^\underline{k}$$

Wielomian $x^\overline{n}$ możemy wyrazić jako:

$$x^\overline{n}=\sum_{k=0}^n\left[\begin{matrix} n \\ k \end{matrix} \right]x^k$$

> [!example] Wyznacz $x^4$ i $x^{\overline{4}}$ korzystając z trójkątów Stirlinga
> **1. Czwarty rząd dla podzbiorów: 0, 1, 7, 6, 1**
>
> $$
> \begin{align*}
> x^4 &= \sum_{k=0}^4 \begin{Bmatrix} 4 \\ k \end{Bmatrix} x^{\underline{k}} = 0 \cdot x^{\underline{0}} + 1 \cdot x^{\underline{1}} + 7 \cdot x^{\underline{2}} + 6 \cdot x^{\underline{3}} + 1 \cdot x^{\underline{4}} = x^{\underline{1}} + 7x^{\underline{2}} + 6x^{\underline{3}} + x^{\underline{4}}
> \end{align*}
> $$
>
> **2. Czwarty rząd dla cykli: 0, 6, 11, 6, 1**
>
> $$
> \begin{align*}
> x^{\overline{4}} &= \sum_{k=0}^4 \begin{bmatrix} 4 \\ k \end{bmatrix} x^k = 0 \cdot x^0 + 6 \cdot x^1 + 11 \cdot x^2 + 6 \cdot x^3 + 1 \cdot x^4 = 6x + 11x^2 + 6x^3 + x^4
> \end{align*}
> $$
>

## Zależności między liczbami Stirlinga
Zauważmy, że $\left[\begin{matrix} n \\ k \end{matrix} \right]$ oznacza liczbę permutacji $n$ obiektów, które zawierają dokładnie $k$ cykli. Zatem aby otrzymać liczbę wszystkich permutacji $n$ obiektów, można zsumować wyrażenia $\left[\begin{matrix} n \\ k \end{matrix} \right]$ dla wszystkich $k$:

$$\sum_{k=0}^n \left[\begin{matrix} n \\ k \end{matrix} \right]=n!$$

Z kolei sumując wszystkie liczby $\left\{\begin{matrix} n \\ k \end{matrix} \right\}$ zliczamy po kolei podziały zbioru $n$-elementowego na $0, 1, \dots,n$ bloków. Wynik ten daje nam liczbę wszystkich możliwych podziałów zbioru $n$-elementowego. Taką liczbę nazywamy liczbą Bella i oznaczamy jako $B_n$:

$$\sum_{k=0}^n\left\{\begin{matrix} n \\ k \end{matrix} \right\}=B_{n}$$

Możemy zauważyć, że liczba cykli musi być co najmniej równa liczbe podzbiorów, zachodzi więc:

$$\left\{\begin{matrix} n \\ k \end{matrix} \right\}\leq\left[\begin{matrix} n \\ k \end{matrix} \right]$$

Zachodzą także tzw. **wzory inwersji**:

$$\sum_{k=m}^n \left[\begin{matrix} n \\ k \end{matrix} \right]\left\{\begin{matrix} n \\ k \end{matrix} \right\}(-1)^{n-k}=\sum_{k=m}^n\left\{\begin{matrix} n \\ k \end{matrix} \right\}\left[\begin{matrix} n \\ k \end{matrix} \right](-1)^{n-k}=0$$

## Liczby Bella
Liczby służące do zliczania możliwych podziałów nazywamy **liczbami szczególnymi**, póki co poznaliśmy trzy liczby szczególne:
- $\left(\begin{matrix} n \\ k \end{matrix} \right)$ – liczba $k$-elementowych podzbiorów $n$-elementowego zbioru.
- $\left[\begin{matrix} n \\ k \end{matrix} \right]$ – liczba podziałów $n$-elementowego zbioru na $k$ niepustych podzbiorów.
- $\left\{\begin{matrix} n \\ k \end{matrix} \right\}$ – liczba permutacji $n$-elementowego zbioru zawierającego $k$ cykli.

Kolejną z liczb szczególnych jest tzw. liczba Bella oznaczana jako $B_n$, oznacza ona liczbę możliwych podziałów zbioru $\{1,2,\dots,n\}$. 
- $B_0=1$, ponieważ $\emptyset  \rightarrow \{\emptyset\}$
- $B_1=1$, ponieważ $\{1\}\rightarrow \{1\}$
- $B_2=2$, ponieważ $\{1, 2\}\rightarrow \{\{1, 2\}\},  \{\{1\}, \{2\}\}$
- $B_3=5$, ponieważ: $\{1,2,3\}\rightarrow \{\{1,2,3\}\}, \{\{1\},\{2,3\}\}, \{\{2\}, \{1,3\}\},\{\{3\},\{1,2\}\},\{\{1\},\{2\},\{3\}\}$
	$\vdots$

Liczby Bella spełniają wzór rekurencyjny:

$$B_{n+1}=\sum_{k=0}^n\binom{n}{k}B_{k}$$

oraz tzw. wzór Dobińskiego:

$$B_{n}=\frac{1}{e}\sum_{k=0}^n \frac{k^n}{k!}$$

## Hipoteza Zaremby
Prostym ułamkiem łańcuchowym nazywamy ułamek nieskracalny przedstawiony w postaci:

$$a_{0}+\frac{1}{a_{1}+\frac{1}{a_{2}+\frac{1}{a_{3}+\frac{1}{\ddots+\frac{1}{a_{n}}}}}}$$

Zasada jest taka, że doprowadzamy ułamek do takiej postaci, by w każdym z liczników występowała tylko liczba $1$. Powyższy ułamek zapisujemy w skrócie w postaci:

$$[0; a_{1}, a_{2}, \dots, a_{n}]$$

Wartość $x$ w zapisie $[x;a_1,\dots,a_k ]$ oznacza, że do ułamka dodajemy pewną stałą $x$.

Sformułowana w 1971 roku przez polskiego matematyka Stanisława Zarembę jr. hipoteza głosi, że istnieje pewna stała liczba całkowita $\mathcal{M}\in\mathbb{N}$ taka że dla każdej liczby całkowitej $q\geq2$ można znaleźć liczbę całkowitą $p>1$ (taką, że $\gcd(p,q)=1$), dla której w rozwinięciu ułamka $\frac{p}{q}$ w prosty ułamek łańcuchowy wszystkie jego mianowniki są mniejsze bądź równe $\mathcal{M}$: 

$$\exists_{\mathcal{M}\in\mathbb{N}} : \forall_{n\in\mathbb{N}} \quad a(n)\leq\mathcal{M}$$

Największy mianownik rozwinięcia o najmniejszym największym mianowniku będziemy umieszczać w ciągu $a(n)$.

> [!example] Rozwiń liczby $\frac{p}{8}$ do postaci prostego ułamka łańcuchowego
> $$
> \begin{align*}
> \frac{3}{8} &= 0 + \frac{1}{2 + \frac{1}{1 + \frac{1}{2}}} = [0; 2, 1, 2] \\[10pt]
> \frac{5}{8} &= \frac{1}{1 + \frac{1}{1 + \frac{1}{1 + \frac{1}{2}}}} = [0; 1, 1, 1, 2] \\[10pt]
> \frac{7}{8} &= \frac{1}{1 + \frac{1}{7}} = [0; 1, 7]
> \end{align*}
> $$
>

Powyższy przykład pokazuje, że dla $p=3, 5$ (nie sprawdzamy $p=1$ bo jest to trywialnie $[0;1]$) największy element rozwinięcia jest równy $2$, możemy zapisać więc, że $a(8)=2$. Hipoteza Zaremby jest wciąż nieudowodniona, jednak wielu matematyków postuluje, że jest ona prawdziwa dla $a(n)\leq \mathcal{M}=5$.

11 maja 2026 roku na stronie arXiv pojawiła się publikacja chińskiego matematyka Xin Zhanga, która ostatecznie potwierdza prawdziwość hipotezy Zaremby. Zhang osadzając równanie w przestrzeni $\text{SL}_{2}(\mathbb{Z}_{q})$ udowodnił, że istnieje globalna stała $\mathcal{M}$ ograniczająca z góry ułamki łańcuchowe, jego metoda nie pozwala jednak na wyznaczenie dokładnej wartości więc pytanie czy $\mathcal{M}=5$ wciąż pozostaje otwarte.

## Hipoteza Pawlika
Dr Pawlik wraz z dr Pleszczyńskim przetestowali hipotezę Zaremby dla $n\leq10^7$, uzyskali oni wyniki:
- $a(n)=5$ w 3 przypadkach $n\in\{6, 54, 150\}$
- $a(n)=4$ w $\sim30$ przypadkach.

W reszcie przypadków $a(n)=3\lor a(n)=2$. Z czasem liczba wystąpień liczby $2$ zaczynała dominować nad $3$, na podstawie tej obserwacji dr Pawlik wysnuł hipotezę, że $a(n)=3$ zachodzi w skończonej liczbie przypadków.

Podobna Hipoteza została wcześniej postawiona przez Douglasa Hensleya, który w swoim artykule naukowym stwierdził, że stała $\mathcal{M}=2$ jest wystarczającym ograniczeniem dla wystarczająco dużych liczb pierwszych $q$.

