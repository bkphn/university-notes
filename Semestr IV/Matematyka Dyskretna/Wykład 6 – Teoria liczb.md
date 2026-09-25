## Największy wspólny dzielnik
Niech $a,b\in\mathbb{Z}$ i niech przynajmniej jedna z nich jest różna od $0$. Liczbę naturalną $d$ nazywamy największym wspólnym dzielnikiem liczb $a,b$ gdy:

$$d|a\land d|b$$

Największy wspólny dzielnik liczb $a$ i $b$ oznaczamy jako $\mathrm{NWD}(a,b)$ innymi spotykanymi notacjami jest notacja amerykańska $\gcd⁡(a,b)$ bądź notacja nawiasowa $(a,b)$.

## Najmniejsza wspólna wielokrotność
Niech $a,b\in\mathbb{Z}\setminus\{0\}$. Liczbę $D$ nazywamy najmniejszą wspólną wielokrotnością liczb $a,b$, gdy:

$$a|D\land b|D$$

Najmniejszą wspólną wielokrotność liczb $a$ i $b$ oznaczamy jako $\mathrm{NWW}(a,b)$, innymi spotykanymi notacjami jest notacja amerykańska $\mathrm{lcm}(a,b)$ bądź notacja nawiasowa $[a,b]$.

## Własności NWW i NWD
Niech $a,b\in\mathbb{Z}\setminus\{0\}$ i $q\in \mathbb{Z}$, wtedy NWW oraz NWD spełnia następujące własności:

$$a\vert b\implies \mathrm{NWD}(a,b)=|a| \land\mathrm{NWW}(a,b)=|b|$$

$$\mathrm{NWD}(a,b)=\mathrm{NWD}(|a|,|b|)$$

$$\mathrm{NWW}(a,b)=\mathrm{NWW}(|a|,|b|)$$

$$\mathrm{NWD}(a,b)=\mathrm{NWD}(a-qb,b)$$

$$\mathrm{NWD}(a,b)\cdot\mathrm{NWW}(a,b)=|a\cdot b|$$

Niech $a=p_{1}^{\alpha_{1}}p_{2}^{\alpha_{2}}\dots p_{k}^{\alpha_k}$ oraz $b=p_{1}^{\beta_{1}}p_{2}^{\beta_{2}}\dots p_{k}^{\beta_{k}}$, wtedy:

$$\mathrm{NWD}(a,b)=p_1^{\min\{\alpha_{1},\beta_{1}\}}\cdot p_2^{\min\{\alpha_{2},\beta_{}\}}\cdot\dots\cdot p_k^{\min\{\alpha_{k},\beta_{k}\}}$$

$$\mathrm{NWW}(a,b)=p_1^{\max\{\alpha_{1},\beta_{1}\}}\cdot p_2^{\min\{\alpha_{2},\beta_{}\}}\cdot\dots\cdot p_k^{\min\{\alpha_{k},\beta_{k}\}}$$

## Przedziały
Niech $d$ będzie metryką, czyli funkcją przyporządkowującą odległość dwóm elementom $a,b$. Kulą otwartą nazywamy zbiór:

$$B(x_0,r)={x∈X :d(x_0,r)<r}$$

Na osi liczb rzeczywistych funkcję $d$ definiujemy jako $d(a,b)=|a−b|$. Przedział otwarty oznaczamy jako $(a,b)$ i definiujemy jako:

$$\forall_{x\in(a,b)} \exists_{r>0} : B(x,r)\subset(a,b)$$

Niech przedział od $a$ do $b$ będzie podzbiorem zbioru $X$. Przedział domknięty oznaczamy jako $[a,b]$ i definiujemy jako:

$$\forall_{x\in X\setminus[a,b]}\exists_{r>0} : B(x,r)\subset X\setminus[a,b]$$

Mówimy, że przedział $A\subset X$ jest otwarto-domknięty, jeżeli jest jednocześnie otwarty i domknięty. Przykładami zbiorów otwarto-domkniętych są zbiory $\emptyset$ oraz $\mathbb{R}$.

Warto zaznaczyć, że przedziały otwarto-domknięte to co innego niż przedziały jednostronnie domknięte.

## Niezmiennik
Niezmiennikiem nazywamy własność pewnej funkcji bądź algorytmu, która nie zmienia się niezależnie od przyjętych argumentów.

Przykładem niezmiennika NWD może być własność:

$$\mathrm{NWD}(a,b)=\mathrm{NWD}(a-qb,b)$$

Mówi nam ona, że mimo zmiany argumentu $a$ o liczbę $q\cdot b$ wartość funkcji NWD pozostaje niezmienna.

## Algorytm Euklidesa
Korzystając z algorytmu Euklidesa możemy zdecydowanie efektywniej wyznaczać największy wspólny dzielnik wybranych liczb. Niech $a,b\in\mathbb{N}$ i $a>b$.

Po podzieleniu z resztą $a$ przez $b$ dostajemy $q_1 b+r_1$. Jeżeli $r_1=0$ to $\mathrm{NWD}(a,b)=b$, jeżeli nie to dzielimy z resztą $r_1$ przez $b$ i otrzymujemy $b=q_2 r_1+r_2$. Procedurę powtarzamy do pewnego indeksu $n$ gdy $r_n\neq0$ oraz $r_{n+1}=0$. Wtedy $\mathrm{NWD}(a,b)=r_n$.

> [!example] Wyznaczanie NWD algorytmem Euklidesa
> Wyznacz $\text{NWD}(48, 180)$ stosując algorytm Euklidesa.
> 
> $$
> \begin{align*}
> 180 &= 3 \cdot 48 + 36 \\
> 48 &= 1 \cdot 36 + 12 \\
> 36 &= 3 \cdot 12 + 0
> \end{align*}
> $$
>
> Ostatnią niezerową resztą w powyższym algorytmie jest $12$, zatem:
>
> $$\text{NWD}(48, 180) = 12$$
>

Przekształcając równanie $\mathrm{NWW}(a,b)\cdot\mathrm{NWW}(a,b)=|ab|$ do postaci:

$$\mathrm{NWW}(a,b)=\frac{|a\cdot b|}{\mathrm{NWD}(a,b)}$$

Możemy wyznaczać NWW korzystając z algorytmu Euklidesa.

## Kombinacje liniowe
Dla dowolnych $\alpha,\beta\in\mathbb{Z}$ oraz $υ,\nu\in\mathbb{Z}$ wyrażenie w postaci $\alpha\upsilon+\beta\nu$ nazywamy kombinacją liniową $\alpha$ i $\beta$. Dla dowolnych $a,b\in\mathbb{Z}$ takich, że co najmniej jedna z nich jest różna od $0$, istnieją $u,v∈Z$ takie, że:

$$\mathrm{NWW}(a,b)=ua+vb$$

W powyższym przypadku $\mathrm{NWD}(a,b)$ jest najmniejszą możliwą dodatnią kombinacją liniową $a$ i $b$.

## Liczby pierwsze
Liczba $p\in\mathbb{N}$ jest liczbą pierwszą jeżeli ma dokładnie dwa dodatnie dzielniki. Zbiór wszystkich liczb pierwszych oznaczamy jako $\mathbb{P}=\{2, 3, 5, 7, 11, 13,\cdots\}$. Liczby naturalne większe od $1$, które nie są pierwsze nazywamy liczbami złożonymi.

Liczb pierwszych jest nieskończenie wiele. Udowodnić to można m.in. stosując liczący sobie około 2500 lat dowód opublikowany przez Euklidesa w księdze *Elementy*.

Załóżmy nie wprost, że teza twierdzenia jest fałszywa, tj. zbiór liczb pierwszych jest skończony.

$$\exists_{n\in\mathbb{N}} :\mathbb{P}=\{p_1,p_2,…,p_n \}$$

Niech $P$ będzie następnikiem iloczynu wszystkich elementów powyższego zbioru:

$$P=1+\prod_{i=1}^n p_{i}$$

Zauważmy, że dzieląc liczbę $P$ przez dowolną liczbę $p_i$ dostajemy resztę $1$, zatem liczba $P$ nie jest podzielna przez żadną liczbę pierwszą – uzyskaliśmy sprzeczność.

Z powyższego wzoru nie wynika jednakowoż, że liczba $P$ jest liczbą pierwszą, dowód Euklidesa mówi nam jedynie, że jej czynniki są większe od liczby $p_n$. Przykładowo:

$$2⋅3⋅5⋅7⋅11⋅13+1=59⋅509\not\in\mathbb{P}$$

## Liczby Euklidesa
Liczbami Euklidesa nazywamy następniki iloczynów początkowych $n$ liczb pierwszych. Ciąg ten możemy zdefiniować wzorem:

$$E_{n}=1+\prod_{i=1}^n p_{i}$$

Początkowe wyrazy ciągu $E_n$, to:

$$3, 7, 11, 211, 2311, 30031, 510511, \dots$$

Do dzisiaj nie wiadomo czy jest nieskończenie wiele liczb pierwszych Euklidesa oraz czy każda liczba Euklidesa jest bezkwadratowa.

Liczbą bezkwadratową nazywamy liczbę $E=p_1^{\alpha_1}\cdot p_2^{\alpha_2}\cdot\dots\cdot p_k^{\alpha_k}$, gdzie $\alpha_i\in\{0, 1\}$.

## Liczby bliźniacze
Liczbami bliźniaczymi nazywamy dwie kolejne liczby pierwsze $p_n,p_{n+1}\in\mathbb{P}$ takie, że:

$$p_{n+1}−p_n=2$$

Do dzisiaj nie wiadomo, czy liczb pierwszych bliźniaczych jest nieskończenie wiele. Wiemy jedynie, że nie istnieje trójka liczb $p_{n−1}, p_n,p_{n+1}\in\mathbb{P}$ takie, że pary $(p_{n−1},p_n)$ oraz $(p_n, p_{n+1})$ są jednocześnie bliźniacze.

Początkowe liczby bliźniacze, to pary:

$$(3, 5), (5, 7), (11, 13), (17, 19), (29, 31), (41, 43), (59, 61), (71, 73),(101, 103),\dots$$

## Podstawowe twierdzenie arytmetyki

>[!danger] Podstawowe twierdzenie arytmetyki mówi
> Każdą liczbę całkowitą dodatnią można przedstawić jako iloczyn liczb pierwszych. Przedstawienie takie jest jednoznaczne z dokładnością do kolejności czynników.

Z powyższego twierdzenia wynika, że każda liczba naturalna $n>1$ może być jednoznacznie zapisana jako:

$$n=q_1^{\alpha_1}\cdot q_2^{\alpha_2}\cdot\dots\cdot q_k^{α_k}$$

gdzie $q_i\in\mathbb{P}$ a $\alpha_i\in\mathbb{N}$.

Powyższy iloczyn nazywamy **postacią kanoniczną** liczby $n$.

## Funkcja $\varphi$-Eulera
Liczby całkowite $a,b$ nazywamy względnie pierwszymi, gdy $\mathrm{NWD}(a,b)=1$. Fakt ten oznaczamy jako $a\perp b$. Przykładowo zachodzi relacja:

$$\frac{a}{\mathrm{NWD}(a,b)}\perp \frac{b}{\mathrm{NWD}(a,b)}$$

Dla każdej liczby $n\in\mathbb{N}+\setminus\{1\}$ określamy liczbę $\varphi(n)$ jako liczbę dodatnich liczb całkowitych mniejszych od $n$ i względnie pierwszych z $n$:

$$\varphi(n)=|\{1\leq k<n : k \perp n\}|$$

Funkcję $\varphi$ nazywamy funkcją $\varphi$-Eulera bądź **tocjentem**, a wyrażenie $\varphi(n)$ czytamy jako tocjent od $n$.

Dla dowolnej liczby pierwszej $p$ i liczby całkowitej $a$, zachodzi:
- $\varphi(p)=p−1$
- $\varphi(p^\alpha )=p^\alpha \left( 1-\frac{1}{p} \right)$

Jeżeli $a\perp b$, to

$$\varphi(ab)=\varphi(a)\varphi(b)$$

Z dwóch powyższych twierdzeń wynika, że jeżeli $p_1^{\alpha_1}\cdot p_2^{\alpha_2}\cdot\dots\cdot p_k^{\alpha_k}$ jest postacią kanoniczną liczby $n$ to:

$$\varphi(n)=n\cdot\prod_{i=1}^k\left(1-\frac{1}{p_{i}}\right)$$

## Współczynniki rozkładu silni
Niech $\alpha_p(x)$ oznacza największą potęgę liczby pierwszej $p$ dzielącej $x$. Wtedy dla każdej dodatniej liczby całkowitej $n$ zachodzi:

$$\alpha_{p}(n!)=\sum_{k=1}^\infty \left\lfloor \frac{n}{p^k}\right\rfloor$$

> [!example] Wyznaczanie największej potęgi liczby dzielącej silnię
> Wyznacz największą potęgę liczby $3$ dzielącą liczbę $100!$.
> 
> Wykorzystujemy w tym celu **wzór Legendre'a**:
>
> $$
> \begin{align*}
> \alpha_3 (100!) &= \left\lfloor \frac{100}{3} \right\rfloor + \left\lfloor \frac{100}{9} \right\rfloor + \left\lfloor \frac{100}{27} \right\rfloor + \left\lfloor \frac{100}{81} \right\rfloor + \left\lfloor \frac{100}{243} \right\rfloor + \dots = 33 + 11 + 3 + 1 + 0 + \dots = 48
> \end{align*}
> $$
>

Dla każdej liczby pierwszej $p$ zachodzi:

$$\alpha_p (n!)< \frac{n}{p-1}$$

## Równania diofantyczne
Równaniem diofantycznym nazywamy dowolne równanie typu:

$$f(x_1,x_2,\cdots,x_n )=0$$

w którym szukane rozwiązanie składa się z liczb całkowitych.

Niech $a_1,\cdots,a_n\in\mathbb{Z}\setminus\{0\}$ i niech $b\in\mathbb{Z}$. Równanie diofantyczne w postaci:

$$a_1 x_1+a_2 x_2+\cdots+a_n x_n=b$$

o niewiadomych $x_1,\cdots,x_n$ nazywamy **liniowym równaniem diofantycznym**.

Dowolne równanie diofantyczne a postaci $ax+by=c$ o niewiadomych $x,y$ ma rozwiązanie wtedy i tylko wtedy, gdy $\mathrm{NWD}(a,b)\vert c$.

Jeżeli para $x_0,y_0$ jest rozwiązaniem równania diofantycznego $ax+by=c$, to wszystkie rozwiązania tego równania dane są wzorami:

$$x=x_{0}+\frac{b\cdot t}{\mathrm{NWD}(a,b)}, \qquad y=y_{0}-\frac{a\cdot t}{\mathrm{NWD}(a,b)}, \qquad t\in\mathbb{Z}$$

## Równanie Catalana
Równanie diofantyczne w postaci:

$$x^p−y^q=1$$

gdzie $p,q>1$ nazywamy **równaniem Catalana**.

W 1843 roku Eugène Catalan wysnuł hipotezę, że powyższe równanie ma tylko jedno rozwiązanie, hipotezę tą potwierdził dopiero w 2002 roku matematyk Prede Mihăilescu.

Rozwiązaniem zaproponowanym przez Catalana jest para $(3, 2)$, co pozwala na ułożenie równania:

$$3^2−2^3=1$$

## Cegiełka Eulera
Dane jest równanie diofantyczne:

$$a^2+b^2=c^2$$

Geometrycznie równanie to odpowiada prostokątowi o bokach $a,b$ i przekątnej $c$. Równanie to posiada nieskończenie wiele rozwiązań, które nazywamy trójkami pitagorejskimi. Przykładowe trójki pitagorejskie:

$$(3, 4, 5), (5, 12, 13), (7, 24, 25), (8, 15, 17), (9, 40, 41), (11, 60, 61), (12, 35, 37), (13, 84, 85)$$

Rozważmy układ równań diofantycznych:

$$\begin{cases}
a^2+b^2=d^2 \\
a^2+c^2=e^2 \\
b^2+c^2=f^2
\end{cases}$$

geometrycznie równanie to odpowiada prostopadłościanowi o bokach $a,b,c$ i przekątnych ścian bocznych $d,e,f$. Prostopadłościan ten nazywamy **cegiełką Eulera**. Przykładowe cegiełki Eulera:

$$(240, 170, 44), (275, 252, 240), (550, 504, 480), (693, 480, 140), (720, 132, 85)$$

Jeżeli do układu równań dorzucimy jeszcze czwarte równanie:

$$\begin{cases}
a^2+b^2=d^2 \\
a^2+c^2=e^2 \\
b^2+c^2=f^2 \\
a^2+b^2+c^2=g^2
\end{cases}$$

to geometrycznie szukamy takiej cegiełki Eulera, której przekątna $g$ również jest liczbą całkowitą. Cegiełkę taką nazywamy **doskonałą cegiełką Eulera**. Do dzisiaj nie udało się znaleźć żadnej trójki liczb $(a, b, c)$ tworzących doskonałą cegiełkę Eulera.

## Wielkie twierdzenie Fermata
Wielkie twierdzenie Fermata zostało poraz pierwsze wspomniane przez Pierre'a de Fermata na marginesie książki Arithmetica Diofantosa. Pierre zamieścił na marginesie następujący komentarz:

>[!danger] Wielkie twierdzenie Fermata
> Jest niemożliwe rozłożyć sześcian na dwa sześciany, czwartą potęgę na dwie czwarte potęgi i ogólnie potęgę wyższą niż druga na dwie takie potęgi; znalazłem naprawdę zadziwiający dowód tego, jednak margines jest za mały, by go pomieścić.

Komentarz ten został odkryty dopiero w 1670 roku, po śmierci Pierre'a de Fermata. Twierdzenie to było nieudowodnione przez ponad 300 lat, aż do momentu gdy w 1994 roku angielski matematyk Andrew Wiles opublikował liczącą ponad 100 stron pracę, która dzięki wykorzystaniu krzywych eliptycznych finalnie udowodniła wielkie twierdzenie Fermata.

Matematycznie rzecz ujmując, wielkie twierdzenie Fermata możemy zapisać jako:

$$∀_{n>2} \not\exists_{x,y,z\in\mathbb{N}_{+}} : x^n+y^n=z^n$$

Równanie w postaci $x^n+y^n=z^n$ jest przykładem równania diofantycznego, oczywiście dla $n=2$ istnieje nieskończenie wiele rozwiązań – trójki pitagorejskie, natomiast dla $n>2$ takie nietrywialne rozwiązania nie istnieją.

