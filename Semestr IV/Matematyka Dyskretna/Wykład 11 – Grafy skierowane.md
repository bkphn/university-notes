## Digrafy
**Digrafem** $D$ nazywamy parę $(V(D), E(D))$ gdzie $V(D)$ to zbiór wierzchołków, a $E(D)\in V(D)^2$  to zbiór **łuków**. Digrafy nazywamy również często grafami skierowanymi. Większość pojęć stosowanych przy grafach nieskierowanych przenosi się na digrafy. 

Dowolną parę $(x,y)\in E(D)$ nazywamy łukiem bądź krawędzią skierowaną. Wierzchołek $y$ nazywamy sąsiednim do $x$. Wierzchołek $x$ nazywamy **początkiem łuku**, a $y$ **końcem łuku**. Luk $(x,x)$ nazywamy pętlą.

Dowolna krawędź $\{x,y\}$ odpowiada parze łuków $(x,y),(y,x)$. 

## Stopnie w digrafach
**Stopniem wyjściowym** wierzchołka $v$ w digrafie $D$ nazywamy liczbę krawędzi, których początkiem jest $v$. Stopień wyjściowy oznaczamy jako $\mathrm{odeg}  v$.

**Stopniem wejściowym** wierzchołka $v$ w digrafie $D$ nazywamy liczbę krawędzi, których końcem jest $v$. Stopień wejściowy wierzchołka $v$ oznaczamy jako $\mathrm{ideg}  v$.

Podstawowe twierdzenie teorii digrafów mówi:
>[!danger] Podstawowe twierdzenie teorii digrafów
> Dla każdego digrafu $D=(V,E)$ zachodzi:
>
> $$\sum_{v\in V} \mathrm{odeg} v= \sum_{v\in V} \mathrm{ideg} v = \|D \|$$
>

Podczas dodawania stopni wyjściowych oraz wejściowych każdy łuk jest liczony tylko raz. Twierdzenie do jest odpowiednikiem lematu o uściskach dłoni dla digrafów.

## Macierze digrafowe
Macierzą sąsiedztwa digrafu $D$ jest macierz $\mathbf{A}_D=[a_{ij}]$, w której $a_{ij}$ określa liczbę łuków od $i$-tego do $j$-tego wierzchołka.

Macierzą incydencji digrafu $D$ nazywamy macierz $\mathbf{B}_D=[b_{ij}]$, w której $\forall_{}$:

$$b_{ij}=\begin{cases}
1, \qquad e_j=(v_i,x) \\
-1, \quad e_j=(x,v_i) \\
0, \qquad e_j=(x,y)
\end{cases}$$

Suma elementów w $i$-tym wierszu macierzy incydencji digrafu $D$ wynosi $\mathrm{odeg}  v_i−\mathrm{ideg}  v_i$, a suma elementów w $j$-tej kolumnie macierzy incydencji digrafu $D$ wynosi $0$.

## Grafy pierwotne
Niech $D=(V,E)$ będzie digrafem.
- Digraf $D$ nazywamy **symetrycznym**, gdy:

$$(u,v)\in E\implies(v,u)\in E,  \forall_{u,v\in V}$$

- Digraf $D$ nazywamy grafem **zorientowanym**, gdy:

$$(u,v)\in E\implies(v,u)\in E,  \forall_{u,v\in V}$$

- Graf $G$ nazywamy **grafem pierwotnym** bądź szkieletem digrafu $D$ gdy graf $G$ możemy otrzymać poprzez zastąpienie dowolnego łuku $(v,u)\in E$ bądź pary łuków $(v,u),(u,v)\in E$ poprzez krawędź $\{v,u\}$.

- Jeżeli $G$ jest grafem pierwotnym digrafu $D$, to $D$ nazywamy **orientacją** grafu $G$.

## Drogi
Niech $D=(V,E)$ będzie digrafem:
- **Drogą** nazywamy ciąg wierzchołków $v_1,v_2,\dots,v_n$ taki, że $(v_i,v_{i+1})\in E$ dla każdego $i$.
- **Drogą nieskierowaną** nazywamy ciąg wierzchołków $v_1,v_2,\dots,v_n$ taki, że $(v_i,v_{i+1})\in E$ lub $(v_{i+1},v_i )\in E$ dla każdego $i$.
- **Ścieżką** nazywamy drogę, w której każdy wierzchołek występuje co najwyżej raz.
- **Cyklem** nazywamy drogę, w której $v_1=v_n$, a pozostałe wierzchołki występują co najwyżej raz.
- **Cyklem niewłaściwym** nazywamy drogę, w której $v_1=v_n$.
- **Digraf** $D$ nazywamy acyklicznym, jeżeli nie posiada cykli.

Digraf $D$ nazywamy **spójnym**, jeżeli dla każdej pary wierzchołków istnieje ścieżka nieskierowana łącząca te wierzchołki. 

Digraf $D$ nazywamy **silnie spójnym**, jeżeli dla każdej pary wierzchołków $u,v$ istnieje ścieżka o początku $u$ i końcu $v$ oraz o początku $v$ i końcu $u$.

>[!danger] Twierdzenie Robbinsona
> Spójny graf $G$ jest orientowalny wtedy i tylko wtedy, gdy każda krawędź grafu $G$ jest zawarta w co najmniej jednym cyklu.

## Turnieje
Digraf $D$ jest $r$-regularny, jeżeli równania: $\mathrm{odeg}  v=\mathrm{ideg}  v=r$ zachodzą dla każdego $v\in V(D)$.

Dowolną orientację grafu pełnego nazywamy **turniejem** i oznaczamy zwyczajowo literą $T$. Turniej $T$ jest przechodni, jeżeli $(u,v),(v,w)\in E(T)\implies(u,w)\in E(T)$

Nazwa turniej odnosi się do tego, że możemy interpretować turnieje jako „starcia”, w której każdy każdy wierzchołek reprezentuje drużynę, a kierunek łuku odpowiada „wygrywaniu” z inną drużyną.

Turniej przechodni oznacza z kolei, że istnieje pewien liniowy porządek pomiędzy drużynami – wygrywanie jest przechodnie, więc jeżeli drużyna $A$ wygrywa z drużyną $B$, a $B$ z $C$, to drużyna $A$ wygrywa z drużyną $C$. Przykładem turnieju nieprzechodniego może być graf reprezentujący grę w kamień, papier, nożyce.

Przy badaniu turniejów często korzysta się z następujących twierdzeń:

>[!danger] Równoważność turnieju przechodniego i acyklicznego
> Turniej $T$ jest przechodni wtedy i tylko wtedy, gdy jest acykliczny.
 
 >[!danger] Twierdzenie o unikalności turnieju przechodniego
> Dla każdej liczby całkowitej $n\geq 3$ istnieje dokładnie jeden przechodni turniej rzędu $n$.

## Digrafy eulerowskie
Jeżeli w digrafie $D$ istnieje cykl niewłaściwy $d$ przechodzący przez każdą krawędź digrafu $D$ dokładnie jeden raz, to $d$ nazywamy **cyklem Eulera**, a digraf $D$ **digrafem eulerowskim**.

Jeżeli digraf $D$ nie jest eulerowski i istnieje ścieżka $d$ przechodząca przez każdą krawędź digrafu $D$ dokładnie jeden raz, to $d$ nazywamy **ścieżką Eulera**, a $D$ **digrafem półeulerowskim**.

Digraf $D$ jest eulerowski wtedy i tylko wtedy, gdy jest spójny oraz dla każdego wierzchołka $w\in V(D)$ zachodzi:

$$\mathrm{odeg}  w=\mathrm{ideg}  w$$

Digraf $D$ jest półeulerowski wtedy i tylko wtedy, gdy jest spójny i zawiera dwa wierzchołki $u,v\in V(D)$ takie, że:

$$\mathrm{odeg}  u=\mathrm{ideg}  u+1, \quad  \mathrm{ideg}  v=\mathrm{odeg}  v+1, \quad  \mathrm{odeg}  w=\mathrm{ideg}  w,   \qquad \forall_{w\in V(D)}  :w\neq u,v$$

## Digrafy hamiltonowskie
Jeżeli w digrafie $D$ istnieje cykl $h$ przechodzący przez przez każdy wierzchołek digrafu $D$ dokładnie jeden raz, to $h$ nazywamy **cyklem Hamiltona**, a $D$ **digrafem hamiltonowskim**.

Jeżeli digraf $D$ nie jest digrafem hamiltonowskim i istnieje ścieżka $h$ przechodząca przez każdy wierzchołek tego digrafu dokładnie jeden raz, to $h$ nazywamy **ścieżką Hamiltona**, a $D$ **digrafem półhamiltonowskim**.

>[!danger] Twierdzenie Rédeia
> Każdy turniej $T$ jest półhamiltonowski lub hamiltonowski. 

Przy czym w większości przypadków turnieje są półhamiltonowskie. Z powyższego twierdzenia możemy zauważyć, że każdy turniej przechodni zawiera dokładnie jedną ścieżkę Hamiltona. 

Niech $D=(V,E)$ będzie digrafem, jeżeli dla każdej pary wierzchołków $u,v\in V$ takich, że $(u,v)\in E$ zachodzi $\mathrm{odeg}  u+\mathrm{ideg}  v\geq n$, to $D$ jest digrafem hamiltonowskim.

Jeżeli dla każdego wierzchołka $v\in V(D)$ zachodzi $\mathrm{odeg}  v\geq \frac{n}{2}$ oraz $\mathrm{ideg}  v\geq \frac{n}{2}$ to $D$ również jest digrafem hamiltonowskim.

