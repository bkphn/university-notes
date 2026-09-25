## Grafy
**Grafem** $G$ nazywamy parę $(V(G),E(G))$, gdzie $V(G)\neq\emptyset$ jest zbiorem wierzchołków, a $E(G)$ jest zbiorem krawędzi. Dowolna krawędź $e\in E(G)$ jest definiowana jako zbiór dwóch wierzchołków $v_1,v_2\in V$.

**Rysunkiem grafu** nazywamy jego graficzną reprezentację. Zwyczajowo wierzchołki oznacza się punktami, a krawędzie odcinkami między nimi.

Parę zbiorów $(V,E)$ zgodnych z powyższą definicją nazywa się często **grafem nieskierowanym**. Pojęcie grafu wprowadził w 1878 roku James Sylvester, który porównywał grafy do graficznych reprezentacji cząstek chemicznych.

## Cechy grafu
**Rząd grafu** $G$ oznaczamy jako $|G|=n$ i definiujemy wzorem:

$$|G|=|V(G)|$$

**Rozmiar grafu** $G$ oznaczamy jako $\| G\| =m$ i definiujemy wzorem:

$$\|G\|=|E(G)|$$

Wierzchołki $u,v$ nazywamy **końcami krawędzi** $\{u,v\}$. Krawędź $\{v,v\}$ nazywamy **pętlą**. Dowolną krawędź $\{u,v\}$ oznaczać będziemy jako $uv$, przy czym $uv=vu$. 

Dany jest graf $G=(V,E)$. Jeżeli $\{u,v\}\in E$, to wierzchołek $u$ nazywamy **wierzchołkiem sąsiednim** do $v$. Krawędź $uv$ nazywamy **krawędzią sąsiednią** do wierzchołków $u,v$.

Jeżeli $\{u,v\}, \{v, w\}\in E$ to krawędź $uv$ nazywamy **krawędzią sąsiednią** do krawędzi $vw$.

Jeżeli $E$ jest multizbiorem (krawędzie mogą się powtarzać), to graf $G=(V,E)$ nazywamy **multigrafem**.

## Grafy proste
**Grafem prostym** nazywamy graf $G=(V,E)$, przy czym zbiór $E$ nie jest multizbiorem i nie zawiera pętli.

Jeżeli $G$ jest grafem prostym, to:

$$0\leq\|G \|\leq\ \binom{|G|}{2}$$

Jeżeli $\|  G\|  =0$ to $G$ nazywamy **grafem pustym**. Jeżeli $\|  G\|  =\binom{|G|}{2}$ to $G$ nazywamy **grafem pełnym** bądź kliką.

Mówimy, że graf $G$ jest nasycony, jeżeli $\|  G\|$ jest bliskie $\binom{|G|}{2}$ oraz, że graf jest słabo nasycony, jeżeli $\|  G\|$ jest bliskie $0$.

## Stopnie
**Stopniem wierzchołka** $v$ nazywamy liczbę wszystkich krawędzi sąsiednich z $v$, przy czym pętle liczymy dwukrotnie. Stopień wierzchołka $v$ oznaczamy jako $\deg ⁡v$ i w przypadku grafu prostego (bez pętli) definujemy wzorem:

$$\deg v=|\{e : v\in e \land e\in E(G)\}|$$

**Minimalnym stopniem grafu** $G=(V,E)$ nazywamy najmniejszy ze stopni wierzchołków, co oznaczamy jako $\delta(G)$ i definiujemy wzorem:

$$\delta(G)=\min_{v\in V}\{\deg v\}$$

**Maksymalnym stopniem grafu** $G=(V,E)$ nazywamy największy ze stopni wierzchołków, co oznaczamy jako $\Delta(G)$ i definiujemy wzorem:

$$\Delta(G)=\max_{v\in V}\{\deg v\}$$

Dla dowolnego $v\in V$ gdzie $G=(V,E)$ zachodzi:

$$0\leq\delta(G)\leq \deg v\leq\Delta(G) \leq |G|-1$$

## Twierdzenia:
Podstawowe twierdzenie grafów zaproponowane przez Leonharda Eulera w 1736 roku mówi:

>[!danger] Podstawowe twierdzenie teorii grafów
> Suma stopni wszystkich wierzchołków skończonego grafu prostego $G=(V,E)$ jest dwa razy większa od liczby jego krawędzi:
>
> $$\sum_{v\in V} \deg v = 2\cdot \| G\|$$
>
 
Podstawowe twierdzenie teorii grafów jest często nazywane **lematem o uściskach dłoni**. Pierwsza nazwa służy podkreśleniu fundamentalnego charakteru wyniku, a druga była stosowana przez Eulera i wskazuje na naturalną interpretację równania.

Lemat o uściskach dłoni mówi, że dla dowolnej grupy osób witających się uściskiem dłoni, sumaryczna liczba wymienionych uścisków jest parzysta. Innym twierdzeniem, które można zinterpretować za pomocą uścisków dłoni jest fakt, że wśród $n$ osób, które ściskały między sobą dłonie, zawsze istnieje para osób, które wykonały tyle samo uścisków. Matematycznie to drugie twierdzenie możemy zapisać jako:

$$|G|\geq 2 \implies \exists_{v,u\in V} : \deg v= \deg u, \qquad u\neq v$$

## Macierze grafów
**Macierz sąsiedztwa** grafu $G$ to kwadratowa macierz $\mathbf{A}_G=[a_{ij}]$, w której $a_{ij}$ określa liczbę krawędzi od $i$-tego do $j$-tego wierzchołka. W przypadku grafu prostego:

$$a_{ij}= \begin{cases}
1, \qquad v_iv_j\in E(G) \\
0, \qquad v_iv_j\notin E(G)
\end{cases}$$

Dla dowolnego $n\in \mathbb{N}$, $\mathbf{A}_{G}^n=[t_{ij}]$, gdzie $t_ij$ oznacza liczbę różnych dróg długości $n$ od $i$-tego do $j$-tego wierzchołka.

**Macierz incydencji** grafu $G$ to macierz $\mathbf{B}_G=[b_{ij}]$, w której:

$$b_{ij}=\begin{cases}
1, \qquad v_i\in e_j \\
0, \qquad v_i \notin e_j
\end{cases}$$

Suma elementów w $i$-tym wierszu macierzy incydencji wynosi $\deg⁡ v_i$, natomiast suma elementów w $j$-tej kolumnie wynosi $2$.

## Podgrafy
Jeżeli $H,G$ są grafami takimi, że $V(H)\subset V(G)$ oraz $E(H)\subset E(G)$ to mówimy, że graf $H$ jest podgrafem grafu $G$, natomiast graf $G$ jest nadgrafem grafu $H$.

Niech $G=(V,E)$ będzie grafem oraz $v\in V$ i $e\in E$. Podgraf grafu $G$ powstały przez usunięcie krawędzi $e$ oznaczać będziemy jako $G−e$, natomiast podgraf powstały przez usunięcie wierzchołka $v$ i wszystkich krawędzi z nim sąsiadujących oznaczać będziemy jako $G−v$.

Podgraf $H$ grafu $G$ nazywamy podgrafem indukowanym przez zbiór $W\subset V(G)$, jeżeli $H$ zawiera wszystkie krawędzie grafu $G$ łączące wierzchołki ze zbioru $W$ oraz $W=V(H)$.

## Drogi
Niech $G=(V,E)$ będzie grafem. **Drogą** nazywamy ciąg wierzchołków $(v_1,\dots ,v_n )$ w grafie $G$ taki, że $\{v_i,v_{i+1} \}\in E$ dla każdego $1\leq i\leq n−1$. **Ścieżką** nazywamy drogę, w której każdy wierzchołek występuje co najwyżej jeden raz.

**Cyklem** nazywamy drogę, w której $v_1=v_n$ oraz wszystkie pozostałe wierzchołki występują co najwyżej raz. **Cyklem niewłaściwym** nazywamy drogę, w której $v_1=v_n$ (wierzchołki mogą się powtarzać).

Graf $G$ jest spójny, gdy dla każdej pary wierzchołków istnieje ścieżka zawierająca te wierzchołki. Maksymalny podgraf spójny danego grafu nazywamy składową spójności.

## Graf Petersena
Graf Petersena oznaczany literą $P$ to pewien szczególny graf prosty o 10 wierzchołkach i 15 krawędziach. Graf Petersena, ze względu na swoją specyfikę, często jest wykorzystywany przy testowaniu algorytmów grafowych.

Graf Petersena:
![[Pasted image 20260919124357.png|250]]

## Izomorfizm grafów
Funkcję $f:V(G)\rightarrow V(H)$ nazywamy izomorfizmem grafów $G,H$, jeżeli $f$ jest bijekcją zachowującą sąsiedztwo wierzchołków. Grafy $G$ i $H$ nazywamy izomorficznym, gdy istnieje między nimi izomorfizm $f$. Izomorficzność grafów $G,H$ oznaczamy jako:

$$G\cong H$$

Jeżeli $G$ i $H$ są grafami ważonymi, to $f$ zachowuje wagi krawędzi, a jeżeli $G,H$ są multigrafami, to $f$ zachowuje liczbę krawędzi.

Niezmienniki będące warunkami koniecznymi, ale nie dostatecznymi dla istnienia izomofrizmu:
- rząd,
- rozmiar,
- liczba wierzchołków danego stopnia,
- liczba składowych spójności,
- liczba krawędzi wielokrotnych,
- liczba pętli,
- liczba cykli danej długości,
- liczba ścieżek.

Przez $\overline{G}$ oznaczamy dopełnienie grafu $G$, przez które rozumiemy graf, powstały poprzez dorysowanie brakujących krawędzi i usunięcie tych wcześniej istniejących.

## Podstawowe grafy proste
Grafem prostym nazywamy skończony graf bez pętli i krawędzi wielokrotnych. Wśród najpopularniejszych rodzajów grafów prostych możemy wyróżnić:
- **Graf pusty** $E_n$  $(\overline{K}_n)$

$$V(E_n )=\{1, 2,\dots ,n\},\qquad E(E_n )=\emptyset$$

![[Pasted image 20260919124700.png|302]]

- **Graf pełny** $K_n$

$$V(K_n )=\{1, 2, \dots ,n\},  \qquad E(K_n )=\{\{i,j\}  :i,j\in V(K_n )\land i\neq j\}$$

![[Pasted image 20260919125247.png|339]]

- **Ścieżka** $P_n$

$$V(P_n )={1, 2,\dots ,n}, \qquad  E(P_n)=\{\{i, i+1\}  :i\in \{1, 2,\dots ,n−1\}\}$$

![[Pasted image 20260919125323.png|348]]

- **Cykl** $C_n$

$$V(C_n )={1, 2, \dots ,n},   \qquad E(C_n )=\{\{i,j\}  :i,j\in V(C_n )\land |i−j| \equiv_n 1\}$$

![[Pasted image 20260919125538.png|377]]

- **Drzewo**: Graf spójny niezawierający cykli.
![[Pasted image 20260919125602.png|203]]

- **Las** $F$: Graf niezawierający cykli.
![[Pasted image 20260919125618.png|379]]
- **Graf $r$-regularny**: Graf, w którym stopień każdego wierzchołka wynosi $r$.
![[Pasted image 20260919125638.png|382]]

Jeżeli $\deg ⁡v=1$ to wierzchołek $v$ nazywamy **liściem**.

## Grafy dwudzielne
Grafem dwudzielnym nazywamy graf $G=(V,E)$, w którym zbiór wierzchołków $V$ można podzielić na dwa rozłączne podzbiory $V_1,V_2$ takie, że:

$$E(G)\subset \{\{i,j\}  :i\in V_1, j\in V_2 \}$$

Graf $G$ jest dwudzielny wtedy i tylko wtedy, gdy $G$ nie zawiera cyklu nieparzystej długości.

Szczególnym przypadkiem grafu dwudzielnego jest:
- **Graf pełny dwudzielny** $K_{n,m}$

$$V(K_{n,m})=V_1\cup V_2, \qquad  E(K_{n,m} )=\{\{i,j\}  :i\in V_1, j\in V_2 \}$$

![[Pasted image 20260919125926.png|366]]

## Gwiazdy
Gwiazdą nazywamy graf pełny dwudzielny, w którym wartość $n=1$. Nazwa gwiazda, bierze się z zwyczajowej reprezentacji takiego grafu, gdzie pojedynczy wierzchołek $v_0$ umieszczamy w środku, a pozostałe wierzchołki stają się „ramionami” takiej gwiazdy.
- **Gwiazda** $K_{1,m}$

$$V(K_{1,m} )=\{v_0\}\cup V_2,   E(K_{1,m} )=\{\{v_0,j\}  :j\in V_2 \}$$

![[Pasted image 20260919130038.png|358]]

