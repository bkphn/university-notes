## Grafy
Grafem $G$ nazywamy parę $(V, E)$, gdzie $V$ jest zbiorem skończonych wierzchołków, a $E \subseteq \{\{u,v\} : u,v \in V, u \neq v\}$ jest zbiorem krawędzi.
>
>Grafem skierowanym nazywamy graf $G=(V,E)$, który oprócz krawędzi posiada także ich kierunek.

W przypadku grafu skierowanego dopuszczamy pętle, gdzie $V$ jest zbiorem skończonych wierzchołków, a $E \subseteq \{(u,v) : u,v \in V\}$ jest zbiorem krawędzi.

W opisie grafów stosujemy następujące nazewnictwo:
  * W krawędzi $e=(u,v) \in E$ wierzchołek $u$ nazywamy jej **początkiem**, a wierzchołek $v$ jej **końcem**, co dzieje się w przypadku grafu skierowanego.
  * Dwa wierzchołki $u, v \in V$ nazywamy **sąsiednimi**, jeżeli $\{u,v\} \in E$.
  * Dwie krawędzie $e_1, e_2$ nazywamy **sąsiednimi**, jeżeli $e_1 \cap e_2 \neq \emptyset$.
  * Wierzchołek $v$ nazywamy **incydentnym** z krawędzią $e \in E$, jeżeli $v \in e$.
  * **Stopniem wierzchołka** nazywamy liczbę krawędzi dochodzących do wybranego wierzchołka $v$.
  * Stopień wierzchołka $v$ grafu $G$ oznaczamy jako $\deg v$.

## Reprezentacja grafu
Graf możemy reprezentować na jeden z wybranych sposobów:
* **Postać graficzna:** Postać, w której wierzchołki grafu reprezentujemy jako węzły, a krawędzie to odcinki łączące je. Przykładem jest graf $G = (V,E)$, gdzie $V = \{a,b,c\}$ oraz $E = \{\{a,c\}, \{a,b\}\}$.
* **Macierz sąsiedztwa:** Graf $G$ możemy reprezentować za pomocą macierzy sąsiedztwa $\mathbf{A} = \mathbf{A}(G) \in \mathbb{M}_{n \times n}(\mathbb{Z})$. W przypadku grafu nieskierowanego macierz ta jedynie informuje, czy między wybranymi wierzchołkami występuje krawędź, i jest definiowana w następujący sposób:

  $$\mathbf{A}_{ij} = \begin{cases} 0, & i,j \notin E \\ 1, & i,j \in E \end{cases}$$

* **Macierz incydencji:** Graf $G$ możemy reprezentować za pomocą macierzy incydencji $\mathbf{B} = \mathbf{B}(G) \in \mathbb{M}_{n \times n}(\mathbb{Z})$, która informuje nas o wierzchołkach należących do kolejnych krawędzi. W grafie nieskierowanym definiuje się ją następująco:

  $$\mathbf{B}_{ij} = \begin{cases} 0, & i \notin e_j \\ 1, & i \in e_j \end{cases}$$

* **Ścieżką** nazywamy ciąg wierzchołków $\{v_0, v_1, ..., v_n\}$ prowadzący z wierzchołka $v_0$ do $v_n$, gdzie pomiędzy każdą parą sąsiednich wierzchołków jest łącząca krawędź.
* **Drogą** nazywamy ścieżkę, w której żaden wierzchołek się nie powtarza.
* **Podgrafem** nazywamy graf powstały po usunięciu pewnych wierzchołków.
* **Cyklem** nazywamy zamkniętą drogę, czyli drogę w postaci $\{v_0, v_1, ..., v_{n-1}, v_n\}$, gdzie $v_0 = v_n$.
* Graf nazywamy **acyklicznym**, jeżeli w grafie skierowanym nie istnieje żaden cykl.
* Graf nieskierowany nazywamy **spójnym**, jeżeli $\forall_{u,v \in V} \exists_e : e = \{u,v\}$.

## Problem komiwojażera
Problem komiwojażera definiuje się na grafie nieskierowanym $G=(V,E)$. Potraktujmy wierzchołki grafu jako miasta. Komiwojażer planuje odwiedzić każde miasto dokładnie raz, a po odwiedzeniu każdego planuje wrócić do punktu wyjścia. Problem polega na znalezieniu jak najkrótszej trasy pomiędzy wszystkimi miastami, spełniając wszystkie założenia.

## Algorytm Prima
Algorytm Prima stosowany jest do znajdowania drzewa o najmniejszym koszcie, nazywanego minimalnym drzewem rozpinającym. Wierzchołki grafu dzielimy na dwa zbiory: $T,W$. Punkt wyjścia $v_0$ umieszczamy w zbiorze $T$, a wszystkie pozostałe w zbiorze $W$.

W każdym kroku algorytmu, wybieramy wierzchołek ze zbioru $W$ taki, że łączy się krawędzią z wierzchołkiem w zbiorze $T$, o najmniejszym koszcie. Ten wierzchołek dodajemy do zbioru $T$ i usuwamy go ze zbioru $W$. Algorytm wykonujemy do momentu, aż zbiór $W$ nie będzie pusty.

## Algorytm Dijkstry
Zaproponowany w 1959 przez Edsgera Dijkstrę algorytm nazwany jego nazwiskiem służy do znajdowania najkrótszej ścieżki w grafie $G=(V,E)$. Algorytm zakłada, że koszt na krawędziach grafu jest liczbą dodatnią.

Na początek tworzymy zbiory $S=\emptyset$,  $Q=V$. Koszt $d$ wierzchołka startowego $v_0$ ustalamy na $0$:

$$d(v_0 )=0$$

Koszt wszystkich pozostałych wierzchołków ustalamy na $∞$. Poprzednik wierzchołków $v_i$  definiujemy jako $p(v_i$) i na początku ustawiamy im wartość `None`.

W każdym kroku wybieramy ze zbioru $Q$ wierzchołek $u$ o najmniejszej wartości $d(u)$. Następnie usuwamy ten wierzchołek ze zbioru $Q$ i dodajemy do zbioru $S$ i obliczamy koszt przejścia do każdego z wierzchołków sąsiadujących $w$.

## Algorytm A*
Opisany w 1968 roku przez Petera Harta, Nilsa Nilssona i Bertrama Raphaela algorytm został przez autorów, w ich pracy naukowej określony jako algorytm $A$. Ponieważ jego użycie daje optymalne zachowanie dla danej heurystyki, oficjalnie nazwano go A*.

Algorytm poszukuje ścieżki pomiędzy dwoma wierzchołkami w taki sposób, aby zminimalizować funkcję $f(v)=g(v)+h(v)$, gdzie:
- $g(v)$ to koszt drogi pomiędzy wierzchołkiem początkowym $v_0$, a obecnym $v$.
- $h(v)$ to przewidywany koszy drogi od obecnego wierzchołka $v$ do docelowego $v_n$.

## Algorytm Floyda-Warshalla
Algorytm Floyda-Warshalla służy do znajdowania najkrótszej drogi z jednego wierzchołka do drugiego. W wyniku działania algorytmu otrzymujemy dwie macierze: $\mathbf{D}$, której elementy $d_{ij}$ są najkrótszymi drogami pomiędzy wierzchołkami $i,j$ oraz macierz $\mathbf{P}$, przy pomocy której możemy odtworzyć najkrótszą drogę. Początkowe elementy tych macierzy zadane są następująco:

  $$(\mathbf{D}_0)_{ij} = \begin{cases} 0, & i=j \\ w(e_{ij}), & e_{ij} \in E \\ \infty, & e_{ij} \notin E \end{cases}$$

  $$(\mathbf{P}_0)_{ij} = \begin{cases} i, & e_{ij} \in E \\ 0, & e_{ij} \notin E \end{cases}$$

  gdzie $w(e_{ij})$ oznacza wagę krawędzi $e_{ij} = (i,j)$.
