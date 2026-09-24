## Przeszukiwanie grafu
Przeszukiawniem grafu nazywamy algorytm, który w konkretny sposób przechodzi po wszystkich wierzchołkach grafu. Wyróżniamy dwa główne metody przeszukiwań:
- **Breath-first search (BFS)**: Odwiedzamy wszystkich sąsiadów aktualnego wierzchołka, zanim przejdziemy do następnego.
- **Depth-first search (DFS)**: Po odwiedzeniu $v_{k+1}$ wierzchołka $v_k$, przechodzimy do nieodwiedzonego sąsiada $v_{k+2}$ wierzchołka $v_{k+1}$ albo – w przypadku braku nieowiedzonych sąsiadów – cofamy się do wierzchołka $v_k$ i powtarzamy.
## Grafy ważone
Niech $G=(V,E)$ będzie grafem i $w:E\rightarrow \mathbb{R}$ będzie funkcją. Parę $(G,w)$ nazywamy **grafem ważonym**, a funkcję $w$ wagą.

Innymi słowy grafem ważonym nazywamy graf, w którym każdej krawędzi przypisana jest liczba rzeczywista (może ona reprezentować odległość między wierzchołkami, przepustowość sieci, ilość interakcji, itd.) Graf ważony $(G,w)$ możemy reprezentować za pomocą macierzy sąsiedztwa.
## Algorytm Dijkstry
Algorytm zaproponowany przez informatyka Edsgera Dijkstrę służy do wyszukiwania najkrótszej drogi od danego wierzchołka do pozostałych w grafie ważonym bez pętli, w którym wagi są liczbami nieujemnymi.

>[!abstract] Algorytm Dijkstry
> 0. **Dane**
> Graf $G=(V,E)$
> Wierzchołki $V=\{v_0,v_1, v_2,\dots,v_{n−1} \}$
> Funkcja $w$
> Wierzchołek startowy $v_0=0$
> 1. **Podstaw**
> $Q\leftarrow \{v_0, v_1, v_2, \dots, v_n \}$
> $S\leftarrow \emptyset$
> $d(v_0 )\leftarrow 0, \quad d(v)\leftarrow \infty$
> $p(v_0 )\leftarrow,0, \quad p(v)\leftarrow \mathtt{NULL}$
> 
> 2. **Dopóki $Q\neq\emptyset$ powtarzaj:**
> $\nu\leftarrow \operatorname{argmin}_{v} d(v)$
> $Q\leftarrow Q\setminus\{\nu\}$
> $S\leftarrow S\cup\{\nu\}$
>
> 	Jeżeli $d(u)>d(v)+w(\nu,u)$:
> >$d(u)\leftarrow d(u)+w(\nu,u)$
>> $p(u)\leftarrow \nu$
> 3. **Wynik**
> Minimalna długość drogi od $v_{0}$ do $v$ to $d(v)$ 


Algorytm Dijkstry najczęściej reprezentujemy za pomocą tabeli. W pierwszej kolumnie umieszczane są najkrótsze drogi a w indeksie dolnym jest waga tej drogi. Elementy tabeli to wagi dróg z wierzchołka startowego $v_0$ do danego wierzchołka $v$, tutaj w wolnych indeksach umieszczamy przedostatni element ścieżki z $v_0$ do $v$. W sytuacji gdy w wierszu mamy więcej niż jedną drogę o najmniejszej wadze, wybieramy dowolną z nich.

>[!example] Przykład działania algorytmu Dijkstry dla $v_{0}=A$
>![[Pasted image 20260922214439.png|281]]
>
>|          | $B$                | $C$                | $D$                | $E$                | $F$                | $G$                |
| -------- | ------------------ | ------------------ | ------------------ | ------------------ | ------------------ | ------------------ |
| $A_0$    | $6_A$              | $\color{red}{1_A}$ | $\infty$           | $3_A$              | $\infty$           | $\infty$           |
| $AC_1$   | $6_A$              | –                  | $4_C$              | $\color{red}{3_A}$ | $3_C$              | $\infty$           |
| $AE_3$   | $6_A$              | –                  | $4_C$              | –                  | $\color{red}{3_C}$ | $\infty$           |
| $ACF_3$  | $6_A$              | –                  | $\color{red}{4_C}$ | –                  | –                  | $4_F$              |
| $ACD_4$  | $5_D$              | –                  | –                  | –                  | –                  | $\color{red}{4_F}$ |
| $ACFG_4$ | $\color{red}{5_D}$ | –                  | –                  | –                  | –                  | –                  |
| $ACDB_5$ | –                  | –                  | –                  | –                  | –                  | –                  |

Problem znalezienia najkrótszej ścieżki można rozwiązać również algorytmem brute force, wystarczy określić wagę wszystkich ścieżek między rozważanymi wierzchołkami i wybrać najmniejszą. Ta metoda jest jednak niezwykle nieoptymalna dla bardziej złożonych grafów.
## Grafy eulerowskie
Jeżeli w grafie $G$ istnieje cykl niewłaściwy $c$ przechodzący przez każdą krawędź grafu $G$ dokładnie raz, to $c$ nazywamy **cyklem Eulera**, a graf $G$ **grafem eulerowskim**.

Jeżeli graf $G$ nie jest grafem eulerowskim i istnieje ścieżka $c$ przechodząca przez każdą krawędź grafu $G$ dokładnie jeden raz, to $G$ nazywamy **grafem półeulerowskim** (jednobieżnym).

Innymi słowy, graf $G$ jest Eulerowski, jeżeli możemy narysować jego krawędzie bez odrywania ręki od kartki i na koniec wrócimy do wierzchołka początkowego oraz jest półeulerowski, jeżeli możemy narysować jego krawędzie bez odrywania ręki od kartki, ale na koniec **nie** wracamy do początkowego wierzchołka.
## Problem mostów królewieckich:
Grafy eulerowskie zostały nazwane po Leonhardzie Eulerze, który zainteresował się pewną lokalną zagadką Königsberga (współcześnie Królewiec/Kaliningrad):

*Czy istnieje możliwość zwiedzenia Königsberga przechodząc przez każdy most dokładnie raz, wracając na koniec do punktu wyjścia?*

Leonhard Euler zauważył, że zadanie to można uprościć do badania grafu, w którym każdy reprezentuje konkretną krawędź grafu:
![[Pasted image 20260919135557.png|406]]
Euler doszedł do wniosku, że zadanie to jest niemożliwe, badanie tego grafu jednak pozwoliło mu na odkrycie wielu fascyjnujących własności charakteryzujących grafy nazywane dzisiaj eulerowskimi.

## Twierdzenia grafów eulerowskich

>[!danger] Lemat o istnieniu cyklu
>Jeżeli $\delta(G)\geq 2$ to graf $G$ zawiera cykl.

Jeżeli graf $G$ zawiera cykl bądź pętle to stają się one cyklem, więc powyższe twierdzenie spełnione jest trywialnie. Jeżeli graf $G$ jest grafem prostym to jednym z podgrafów tego grafu jest ścieżka $P_n$. W ścieżce każdy wierzchołek poza końcami spełnia warunek $\deg ⁡v=2$ jako, że wymuszamy $\delta(G)\geq 2$ to wierzchołki skrajne też muszą mieć drugą krawędź. Dowolne połączenie wierzchołków skrajnych z innymi krawędziami tworzy cykl.

Jednym z twierdzeń zauważonych przez Eulera w 1741 roku, w trakcie badania grafu opartego na Königsbergu, było:

>[!danger] Twierdzenie Eulera-Hierholzera
> Niech $G$ będzie grafem spójnym. Graf $G$ jest eulerowski wtedy i tylko wtedy, gdy każdy wierzchołek ma stopień parzysty.

Analizując mapę Königsberga można zauważyć, że każdy wierzchołek ma tam stopień nieparzysty, co rozwiązuje zagadkę. Euler zauważył również, że:

>[!danger] Twierdzenie o drodze Eulera
> Niech $G$ będzie grafem spójnym. Graf $G$ nazywamy pół-eulerowskim wtedy i tylko wtedy, gdy ma dokładnie dwa wierzchołki stopnia nieparzystego.

Na podstawie powyższych informacji można wyprowadzić ostatnie twierdzenie:

>[!danger] Twierdzenie Veblena
>Niech $G$ będzie grafem spójnym. Graf $G$ nazywamy eulerowskim wtedy i tylko wtedy, gdy jego zbiór krawędzi można podzielić na rozłączne cykle.
## Algorytm Fleury'ego
**Mostem** nazywamy tę krawędź w skończonym grafie $G$, której usunięcie powoduje zwiększenie liczby spójnych składowych grafu $G$.

Przy szukaniu cyklu Eulera możemy posłużyć się tzw. Algorytmem Fleury'ego. Zaczynamy od dowolnego wierzchołka, cykl tworzymy dodając do niego kolejne krawędzie w taki sposób, że dodajemy do cyklu most tylko wtedy, gdy nie ma innej możliwości.
## Problem chińskiego listonosza
Problem chińskiego listonosza polega na znalezieniu niewłaściwego cyklu zawierającego każdą krawędź danego grafu co najmniej raz i mającego jak najmniejszy koszt.

Rozwiązaniem problemu chińskiego listonosza jest następujący algorytm:
- jeżeli graf $G$ jest eulerowski to rozwiązaniem jest dowolny cykl Eulera,
- jeżeli graf $G$ nie jest eulerowski to dublujemy niektóre krawędzie, aby otrzymać graf eulerowski i wtedy szukamy cyklu Eulera. Aby otrzymać najoptymalniejsze ścieżki:
	- dla grafów nieważonych przeszukujemy go wstecz,
	- dla grafów z nieujemnymi wagami można skorzystać z algorytmu Dijkstry,
	- dla grafów z dowolnymi wagami można skorzystać z algorytmu Bellmana-Forda.
## Grafy hamiltonowskie
Jeżeli w grafie $G$ istnieje cykl $c$ przechodzący przez każdy wierzchołek grafu $G$ dokładnie jeden raz, to $c$ nazywamy **cyklem Hamiltona**, a graf $G$ **grafem hamiltonowskim**.

Jeżeli $G$ nie jest grafem hamiltonowskim oraz istnieje ścieżka $c$ przechodzący przez każdy wierzchołek grafu $G$ dokładnie jeden raz, to $G$ nazywamy **grafem półhamiltonowskim** (trasowalnym).

Jednym ze sposobów szukania grafów hamiltonowskich jest twierdzenie zaproponowane przez Oysteina Ore w 1960 roku:

>[!danger] Twierdzenie Orego
> Jeżeli graf prosty $G$ ma $n$ wierzchołków, gdzie $n\geq 3$ oraz $\deg ⁡u+\deg ⁡v\geq n$ dla każdej pary niesąsiednich wierzchołków $u,v$, to graf $G$ jest hamiltonowski.

Kolejne ze stwierdzeń sformułował Paul Dirac w 1952 roku:

>[!danger] Twierdzenie Diraca
>Jeżeli minimalny stopień grafu $G$ jest nie mniejszy niż połowa liczby wierzchołków tego grafu $\delta(G)\geq \frac{|G|}{2}$ to $G$ jest grafem hamiltonowskim.

## Problem komiwojażera
Problemem komiwojażera nazywamy następujący problem: *Mając daną listę miast i odległości między tymi miastami, znaleźć najkrótszą drogę przechodzącą przez wszystkie miasta (przez każde tylko raz) i powracającą do punktu wyjścia.*

Co w języku teorii grafów możemy ubrać w następujące słowa: Znaleźć najoptymalniejszy cykl Hamiltona w ważonym grafie pełnym.

Problem komiwojażera jest jednym z nierozwiązanych zadań optymalizacyjnych. Przykładową metodą może być brute force, który jest jednak niezwykle niefektywny. Jedną z najpopularniejszych metod rozwiązywania problemu komiwojażera jest tzw. algorytm najbliższego sąsiada. Zaczynamy w nim od dowolnego wierzchołka i poruszamy się zawsze wzdłuż krawędzi o najmniejszych wagach. Jest to rozwiązanie przybliżone, średnio o 25% gorsze od optymalnego.
## Grafy hipohamiltonowskie
Graf $G$ nazywamy hipohamiltonowskim, jeżeli istnieje taki wierzchołek $v\in V(G)$, że podgraf indukowany $G−v$ jest grafem hamiltonowskim.

Przykładem grafu hipohamiltonowskiego jest graf Petersena.