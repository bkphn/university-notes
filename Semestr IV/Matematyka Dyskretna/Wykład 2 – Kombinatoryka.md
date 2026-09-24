## Kombinatoryka
Kombinatoryka to dział matematyki dyskretnej zajmujący się zliczaniem elementów zbioru. W. T. Tutte opisał kombinatorykę w sposób następujący:

*It is difficult to find a definition of combinatorics that is both concise and complete, uness we are satisfied with the statement "Combinatorics is what combinatorialists do."*

Zbieraniem różnych definicji kombinatoryki zajął się Igor Pak, o czym można poczytać w jego książce *What is Combinatorics?*.
## PIN-y matematyków
Prowadzący przytoczył historię z życia, gdzie miał do wybrania sześciocyfrowy kod PIN do drzwi. Zaproponował on kod 111111, ten jednak został odrzucony jako zbyt trywialny. Zamiast tego został wybrany PIN 117763.

Dr Pawlik dał za zadanie odgadnięcie dlaczego ten PIN został wybrany. Okazało się, że jest to 11111-sta liczba pierwsza. Podał on przy tej okazji trzy inne kody PIN używane przez matematyków:$$p_1111=8933$$ $$p_11111=117763$$ $$p_111111=1456667$$gdzie prze $p_n$ rozumie się $n$-tą liczbę pierwszą.
## Prawo iloczynu
Liczbę wybrań po jednym elemencie ze skończonych zbiorów $S_1,S_2,\dots,S_n$  opisuje prawo iloczynu:
$$|S_1\times S_2\times \dots\times S_n |=\prod_{i=1}^n|S_i|$$

Każdy element zbioru $S_1\times S_2\times \dots\times S_n$ ma postać $(s_1,s_2,\dots,s_n )$, czyli z każdego ze zbiorów $S_i$ wybieramy po jednym elemencie. Możemy określić liczbę elementów tego iloczynu w następujący sposób:
1. $s_1$ możemy wybrać na $|S_1|$ sposobów
2. Dla każdego $s_1$ możemy wybrać $s_2$ na $|S_2|$ sposobów, co daje $|S_1 |\cdot |S_2 |$ sposobów na wybór pary $(s_1,s_2)$
3. Dla każdej pary $(s_1,s_2)$  możemy wybrać $s_3$  na $|S_3|$  sposobów, co daje $|S_1 |\cdot |S_2 |\cdot |S_3 |$  sposobów na wybór trójki $(s_1,s_2,s_3 )$
	⋮
  $n$. $s_n$ można wybrać na $|S_n|$  sposobów co daje $|S_1 |\cdot |S_2 |\cdot  ... \cdot |S_n |$  sposobów na wybór elementu $(s_1,s_2,\dots,s_n )$

Szybki wzrost złożoności problemu wraz z niewielkimi zmianami w liczbie danych wejściowych powodują, że metoda brute force jest nieskuteczna przy długich ciągach danych.
## Silnia
Silnia jest funkcją, którą definiujemy dla nieujemnych liczb całkowitych. Oznaczamy ją jako $n!$ i definiujemy następująco: $$0!=1$$$$ n!=1\cdot 2\cdot ... \cdot (n−1)\cdot n, \quad n≥1$$
W skrócie dla $n\geq1$ możemy silnię określic wzorem jawnym:
$$n!=\prod_{i=1}^n i$$
bądź wzorem rekurencyjnym:
$$n!=(n−1)!\cdot n$$
Początkowe wartości silni dla $n≤12$ wyglądają następująco:
$$1, 1, 2, 6, 24, 120, 720, 5040, 40320, 362880, 3628800, 39916800, 479001600$$
## $k$-permutacje
Mówimy, że słowo $A$ jest anagramem słowa $B$, jeżeli można otrzymać $A$ poprzez zamianę kolejności liter w $B$. Przykładowo anagramami są słowa *elevenplustwo* oraz *twelveplusone*.

Anagramy są przykładami permutacji. **Permutacją** nazywamy dowolne ułożenie elementów jakiegoś ciągu. Liczba różnych permutacji zbioru $n$-elementowego wynosi $n!$.

Losując $k$ elementów z $n$-elementowego zbioru mamy do czynienia z tzw. $k$-permutacją, nazywaną również **permutacją częściową**, przy czym każda permutacja $n$-elementowego zbioru jest jego $n$-permutacją.

Liczba różnych $k$-permutacji zbioru $n$-elementowego wynosi $\frac{n!}{(n−k)!}$.

Zauważmy, że $k$-permutacja zbioru $n$-elementowego to uporządkowany ciąg $(a_1,a_2,\dots,a_n )$. Zauważmy, że:
1. $a_1$ możemy wybrać na n sposobów
2. $a_2$ możemy wybrać na $(n−1)$ sposobów.
3. $a_3$ możemy wybrać na $(n−2)$ sposobów.
	 ⋮
  $n$. $a_k$ możemy wybrać na $n−(k−1)$ sposobów.

Korzystając z prawa iloczynu otrzymujemy, że liczba różnych $k$-permutacji wynosi:
$$n\cdot (n−1)\cdot (n−2)\cdot \dots\cdot (n−(k−1))=\frac{n!}{(n−k)!}$$
## Wzór dwumianowy Newtona:
Symbolem dwumianowym Newtona nazywamy wyrażenie $$\binom{n}{k}=\frac{n!}{k!\cdot (n−k)!}$$co czytamy jako $n$ *po* $k$. Często przyjmuje się, że jeżeli $k>n$, to $\binom{n}{k}=0$. Liczba różnych $k$-elementowych podzbiorów zbioru $n$-elementowego wynosi $\binom{n}{k}$.

> [!example] Wyznacz liczbę anagramów słowa *rearrange*.
> 
> Słowo *rearrange* składa się z $9$ liter, wśród których występują powtórzenia:
> - litera *r* występuje $3$ razy,
> - litera *e* występuje $2$ razy,
> - litera *a* występuje $2$ razy,
> - litery *n* oraz *g* występują po $1$ razie.
> 
> Ponieważ przestawianie miejscami identycznych liter nie tworzy nowego słowa, korzystamy ze wzoru na permutacje z powtórzeniami. Dzielimy silnię z całkowitej liczby liter przez iloczyn silni z liczby wystąpień poszczególnych liter:
> $$P = \frac{9!}{3! \cdot 2! \cdot 2! \cdot 1! \cdot 1!} = \frac{362880}{6 \cdot 2 \cdot 2 \cdot 1 \cdot 1} = \frac{362880}{24} = 15120$$
> 
> **Odpowiedź:** Liczba anagramów słowa *rearrange* wynosi $15120$.

**Symbol dwumianowy Newtona spełnia następujące własności:** $$\binom{n}{0}=\binom{n}{n}=1$$ $$\binom{n}{1}=\binom{n}{n-1}=n$$ $$\binom{n}{2}=\binom{n}{n-2}=\frac{n^2-n}{2}$$
$$\binom{n}{k}=\binom{n}{n-k}$$

Dla dowolnych $x,y\in\mathbb{R}$ i dla dowolnego $n\in\mathbb{N}$ zachodzi tzw. wzór dwumianowy Newtona:
$$(x+y)^n=\sum_{k=0}^n \binom{n}{k}x^{n-k}y^k$$
## Wzór Pascala
Oprócz wzoru dwumianowego Newtona do rozwijania wyrażeń w postaci $(x+y)^n$ można wykorzystać także tzw. trójkąt Pascala.

Równanie Pascala mówi, że dla każdej pary $n,k\in\mathbb{Z}$ takich, że $1≤k<n$ zachodzi:
$$\binom{n}{k}=\binom{n-1}{k}+\binom{n-1}{k-1}$$
Korzystając z tego faktu, możemy utworzyć tzw. trójkąt Pascala:
![[Pasted image 20260904150057.png|462]]

Każdy $n$-ty wiersz trójkąta Pascala (numerując od $0$) odpowiada za współczynniki stojące przy niewiadomych w rozwinięciu sumy: $(x+y)^n$.
## -iliony i -iliardy
Do zapisu dużych liczb powszechnie stosuje się dwie notacje:
- **Skala długa**: Oryginalna skala, używana m.in. w Polsce. W długiej skali przyrostek -ilion odnosi się do miliona, a łaciński przedrostek mówi, do której potęgi musimy podnieść milion$$.
n\text{-ilion}=(10^6 )^n$$ Uzupełnieniem skali długiej są -iliardy. Są one uzupełnieniem luk między kolejnymi ilionami. Wprowadza się mnożnik tysiąc:
$$n\text{-iliard} =1000\cdot 10^6n=10^{6n+3}$$

- **Skala krótka**: Skala krótka, używana głównie w państwach anglojęzycznych (USA, UK) wywodzi się z skali długiej. Celem skali długiej było usprawnienie zapisu poprzez pozbycie się -iliardów, kolejne -illiony zastępują bezpośrednio po sobie. Główną wadą tej skali jest jednak rozjechanie się łacińskich nazw, które już nie odnoszą się do wartości liczby.

Największą liczbą jaką jesteśmy w stanie nazwać w obu skalach jest Centylion (oraz Centyliard), który w notacji długiej wynosi $(10^6 )^{100}=10^{600}$, a w notacji krótkiej $10^{303}$. Oczywiście nazwy można tworzyć dalej korzystając z łacińskiego nazewnictwa, nie jest ono jednak oficjalnie stosowane.
## Liczby Catalana
Liczby Catalana są szczególnym ciągiem liczbowym mającym związek z kombinatoryką. Liczby te zostały nazwane na cześć belgijskiego matematyka Eugène'a Charlesa Catalana.

Każdy wyraz ciągu ma wzór jawny:
$$C_{n}=\frac{1}{n+1}\binom{2n}{n}=\frac{(2n)!}{(n+1)!\cdot n!}$$
Rekurencyjnie ciąg ten jest określony następująco: $$C_0=1$$$$C_{n}=c_{0}c_{n-1}+c_{1}c_{n-2}+\dots+c_{n-2}c_{1}+c_{n-1}c_{0}=\sum_{i=0}^{n-1}c_{i}c_{n-1-i}$$Początkowe wyrazy tego ciągu, to:
$$1, 1, 2, 5, 14, 42, 132, 429, 1430, 4862, 16796, 58786, 208012, 742900, 2674440, 9694845$$
## Operator dodjąć
Znak plus-minus $\pm$ jest wykorzystywany jako matematyczny zamiennik symboli $+$ oraz $−$. W miejsce znaku $\pm$ można wstawić dowolny z tych dwóch znaków, a równanie zawsze będzie spełnione. Dr Pawlik zaproponował polskie tłumaczenie operatora *plus-minus* jako *dodjąć*. Symbol dodjąć można wykorzystywać np. przy reprezentowaniu dwóch równań jednocześnie:
$$x=3\lor x=-3\iff x=\pm3$$
Uzupełnieniem symbolu $\pm$ jest operator $\mp$, który mówi, że jeżeli za symbol $\pm$ wykorzystujemy +, to za $\mp$, należy wykorzystać $-$. Symbole te są wykorzystywane w wielu wzorach i definicjach matematycznych, m.in. we wzorze na cosinus sumy:
$$\cos(\alpha\pm\beta)=\cos\alpha \cos\beta\mp \sin\alpha \sin\beta$$
## Liczba elementów zbioru
Chcąc wyznaczyć liczbę wszystkich podzbiorów zbioru $n$-elementowego, możemy skorzystać z przypisań im wartości $0, 1$, gdzie $1$ oznacza należenie do podzbioru, a $0$ oznacza brak należenia.

Korzystając z prawa iloczynu wiemy, że takich różnych przypisań jest dokładnie $2\cdot2\cdot 2\cdot ... \cdot2=2^n$.

Zbiór wszystkich podzbiorów zbioru $A$ nazywamy zbiorem potęgowym zbioru $A$ i oznaczamy jako:
$$\mathcal{P}(A)=2^{|A|}$$z czego wynika:
$$|2^A |=2^{|A|}$$Dla każdego $n\in\mathbb{N}$ zachodzi:
$$\binom{n}{0}+\binom{n}{1}+\dots+\binom{n}{n}=2^n$$
Niech $S_1,\dots,S_n$ będą zbiorami, które są parami rozłączne, wtedy:
$$\left\vert \bigcup_{i=1}^nS_{i} \right\vert=\sum_{i=1}^n|S_{i}|$$
Dla dwóch dowolnych zbiorów skończonych $S_1,S_2$ zachodzi:
$$|S_1\cup S_2 |=|S_1 |+|S_2 |−|S_1\cap S_2 |$$
Dla dwóch dowolnych zbiorów $X,Y$ zachodzi:
$$|X\setminus Y|=|X|-|X\cap Y|$$
Korzystając z **zasady włączeń i wyłączeń** możemy zdefiniować moc sumy zbiorów za sobą kolejnych operatorów sumy.
>[!danger] Zasada włączeń i wyłączeń
> Niech $n\geq 2$ i niech $S_1,S_2,\dots,S_n$ będą zbiorami skończonymi. Liczba elementów sumy zbiorów $S_1,\dots,S_n$ jest równa liczbie elementów wszystkich możliwych przecięć nieparzystej liczby zbiorów spośród $S_1,\dots,S_n$  pomniejszonej o liczbę elementów wszystkich możliwych różnych przecięć parzystej liczby zbiorów $S_1,\dots,S_n$: $$\left\vert \bigcup_{i=1}^n S_{i} \right\vert = \sum_{i=1}^n|S_{i}|-\sum_{i,j : i<j} |S_{i}\cap S_{j}|+\sum_{i,j,k : i<j<k} |S_{i}\cap S_{j}\cap S_{k}|-\dots \pm |S_{1}\cap S_{2}\cap S_{3}\cap \dots\cap S_{n}|$$

## Podzielność liczb
Chcąc dowiedzieć się ile jest liczb dodatnich mniejszych od pewnej liczby $x$, które są jednocześnie podzielne przez $n,m$ możemy podejść do tego zadania wyznaczając kolejne przekroje zbiorów. 

Przez $A_k$ oznaczmy zbiór wszystkich liczb podzielnych przez $k$, mniejszych od $x$: $A_k=\{d :d\vert k, d<x\}$. Wtedy przekrój zbiorów $A_n, A_m$  możemy zdefiniować następująco:
$$|A_n\cap A_m |=|A_{\operatorname{NWW}(n,m)} |=\left\lfloor  \frac{x}{\operatorname{NWW}(n,m)}  \right\rfloor$$
gdzie dla dowolnego $A_n$:
$$|A_n|=\left\lfloor \frac{x}{n}\right\rfloor$$
> [!example] Wyznaczanie liczb podzielnych przez 2 lub 3
> Wyznacz liczbę wszystkich całkowitych dodatnich liczb mniejszych od 1000, które są podzielne przez 2 lub przez 3.
> 
> $$
> \begin{align*}
> |A_2| &= |\{2, 4, 6, 8, \dots, 998\}| = 499 \\
> |A_3| &= |\{3, 6, 9, \dots, 999\}| = 333 \\
> |A_2 \cap A_3| &= |A_{\text{NWW}(2,3)}| = |A_6| = |\{6, 12, 18, \dots, 996\}| = 166 \\
> |A_2 \cup A_3| &= |A_2| + |A_3| - |A_2 \cap A_3| = 499 + 333 - 166 = 666
> \end{align*}
> $$

**Zbiorem standardowym $n$-elementowym** nazywamy zbiór wszystkich liczb całkowitych $k$ takich, że: $1\leq k\leq n$. Zbiór standardowy oznaczamy za pomocą nawiasów kwadratowych i definiujemy jako:
$$[n]=\{1, 2, 3,\dots,n−1,n\}$$
## Gra kombinatoryczna
Jedna z warszawskich studentek zaproponowała własną grę kombinatoryczną bazowaną na kultowym Kółko i Krzyżyk. Grę rozgrywa się na planszy $n\times 1$.

Zasada gry jest taka, że gracze na zmianę umieszczają na niej symbole $\text{X}$, $\text{O}$, w taki sposób, by zachowywać między sobą, ustaloną odległość $k$. Zwyczajowo $k=1 \lor k=2$.