## Macierze
**Macierzą** nazywamy uporządkowaną tabelę liczbową. Dla ciała $F$ oraz $m, n \in \mathbb{N}$ możemy stworzyć macierz o wymiarach $m \times n$ o współczynnikach nad ciałem $F$, która będzie prostokątną tablicą złożoną z $m \cdot n$ elementów ciała $F$ ułożonych w $m$ wierszy i $n$ kolumn. To, że macierz jest nad ciałem, oznacza, że każdy z jej współczynników (elementów) jest częścią tego ciała.

Konkretny współczynnik macierzi oznaczamy w indeksie jego współrzędnymi $a_{ij}$, gdzie pierwsza współrzędna to numer wiersza, a druga to numer kolumny:

$$\mathbf{A} = \begin{bmatrix} a_{11} & \dots & a_{1n} \\ \vdots & \ddots & \vdots \\ a_{m1} & \dots & a_{mn} \end{bmatrix} = [a_{ij}]_{m \times n}$$

Gdzie $a_{ij} \in F$ jest położony w $i$-tym wierszu i $j$-tej kolumnie dla $i \in \{1, \dots, m\} \land j \in \{1, \dots, n\}$.

> [!example] Przykład
> Wskazać współczynnik $a_{23}$ z macierzy $\mathbf{A}$:
>
> $$\mathbf{A} = \begin{bmatrix} 1 & 2 & 3 \\ 2 & 1 & 5 \\ \frac{1}{2} & \frac{2}{3} & -0.3 \end{bmatrix}$$
>
> Wynik: $a_{23} = 5$.

## Zbiór macierzy
Zapis $[a_{ij}]_{m \times n}$ oznacza macierz o wymiarach $m \times n$. Zbiór $\mathbb{M}_{m,n}(F)$ nazywamy zbiorem wszystkich macierzy o wymiarach $m \times n$ nad ciałem $F$. Oprócz notacji $\mathbb{M}_{m,n}(F)$ można spotkać zapisy: $\mathbb{M}(m,n,F)$, $\mathbb{M}(m,n)$, $\mathbb{M}_{m \times n}(F)$ lub $\mathbb{M}_{m,n}$ (w miejsce $\mathbb{M}$ można również używać $\mathcal{M}$ lub $\text{Mat}$).

## Operacje na macierzach

### Dodawanie i odejmowanie macierzy
Dodawanie i odejmowanie macierzy polega na dodawaniu lub odejmowaniu od siebie elementów o tych samych współrzędnych. Dla $\mathbf{A}, \mathbf{B} \in \mathbb{M}_{m,n}(F)$:

$$\mathbf{A} \pm \mathbf{B}=\begin{bmatrix} a_{11} & \dots & a_{1n} \\ \vdots & \ddots & \vdots \\ a_{m1} & \dots & a_{mn} \end{bmatrix} \pm \begin{bmatrix} b_{11} & \dots & b_{1n} \\ \vdots & \ddots & \vdots \\ b_{m1} & \dots & b_{mn} \end{bmatrix} = \begin{bmatrix} a_{11} \pm b_{11} & \dots & a_{1n} \pm b_{1n} \\ \vdots & \ddots & \vdots \\ a_{m1} \pm b_{m1} & \dots & a_{mn} \pm b_{mn} \end{bmatrix}$$

> [!example] Przykład dodawania
> Niech $\mathbf{A} = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}$ oraz $\mathbf{B} = \begin{bmatrix} 4 & 3 \\ 2 & 1 \end{bmatrix}$.
>
> $$\mathbf{A} + \mathbf{B} = \begin{bmatrix} 1+4 & 2+3 \\ 3+2 & 4+1 \end{bmatrix} = \begin{bmatrix} 5 & 5 \\ 5 & 5 \end{bmatrix}$$
>

### Mnożenie skalarów przez macierze
Skalar w matematyce to pojedyncza liczba nieposiadająca kierunku (np. dowolna liczba rzeczywista, zespolona). Chcąc pomnożyć macierz przez taki skalar, mnożymy przez niego każdy jej współczynnik:

$$\alpha \cdot [a_{ij}]_{mn} = [\alpha a_{ij}]_{mn}$$

Dla $\mathbf{A} \in \mathbb{M}_{m,n}(F)$ oraz $\alpha \in F$:

$$\alpha \cdot \begin{bmatrix} a_{11} & \dots & a_{1n} \\ \vdots & \ddots & \vdots \\ a_{m1} & \dots & a_{mn} \end{bmatrix} = \begin{bmatrix} \alpha \cdot a_{11} & \dots & \alpha \cdot a_{1n} \\ \vdots & \ddots & \vdots \\ \alpha \cdot a_{m1} & \dots & \alpha \cdot a_{mn} \end{bmatrix}$$

**Własności mnożenia przez skalar** (dla $\mathbf{A}, \mathbf{B} \in \mathbb{M}_{m,n}(F)$ oraz $\alpha, \beta \in F$):
* $\alpha(\mathbf{A} + \mathbf{B}) = \alpha \mathbf{A} + \alpha \mathbf{B}$
* $(\alpha + \beta)\mathbf{A} = \alpha \mathbf{A} + \beta \mathbf{A}$
* $(\alpha\beta)\mathbf{A} = \alpha(\beta \mathbf{A})$
* $1 \cdot \mathbf{A} = \mathbf{A}$

### Mnożenie macierzy przez macierz
Aby móc wymnożyć dwie macierze, liczba wierszy drugiej macierzy musi być równa liczbie kolumn pierwszej macierzy. Wynika z tego, że mnożenie macierzy nie jest przemienne, ale jest łączne. Wynikowa macierz ma tyle wierszy, ile miała pierwsza macierz, i tyle kolumn, ile miała druga macierz:

$$[a_{ij}]_{m \times n} \cdot [b_{ij}]_{n \times k} = [c_{ij}]_{m \times k}$$

Gdzie poszczególne elementy obliczamy ze wzoru:

$$c_{ij} = \sum_{l=1}^{n} a_{il} \cdot b_{lj}$$

> [!example] Przykład mnożenia
> Niech $\mathbf{A} = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}$ oraz $\mathbf{B} = \begin{bmatrix} 4 & 3 \\ 2 & 1 \end{bmatrix}$.
>
> $$\mathbf{A} \cdot \mathbf{B} = \begin{bmatrix} 1 \cdot 4 + 2 \cdot 2 & 1 \cdot 3 + 2 \cdot 1 \\ 3 \cdot 4 + 4 \cdot 2 & 3 \cdot 3 + 4 \cdot 1 \end{bmatrix} = \begin{bmatrix} 8 & 5 \\ 20 & 13 \end{bmatrix}$$
>

### Potęgowanie macierzy
Potęgowanie polega na mnożeniu macierzy przez samą siebie określoną liczbę razy, dlatego operację tę można wykonać wyłącznie dla macierzy kwadratowych (których liczba wierszy jest równa liczbie kolumn). Macierz $\mathbf{A}_{m \times m}$ nazywamy macierzą kwadratową stopnia $m$, a zbiór takich macierzy oznaczamy jako $\mathbb{M}_m(F)$.
* $\mathbf{A}^2 = \mathbf{A} \cdot \mathbf{A}$
* $\mathbf{A}^3 = \mathbf{A}^2 \cdot \mathbf{A} = \mathbf{A} \cdot \mathbf{A}^2 = \mathbf{A} \cdot \mathbf{A} \cdot \mathbf{A}$

## Wybrane rodzaje macierzy
* **Macierz zerowa:** Każda struktura $(\mathbb{M}_{m,n}(F), +)$ jest grupą abelową, co oznacza istnienie elementu neutralnego dodawania – macierzy zerowej, której każdy współczynnik jest równy zero. Oznaczamy ją symbolem $\mathbf{0}$.
* **Macierz przeciwna:** Istnienie grupy abelowej gwarantuje też obecność macierzy przeciwnych. Macierzą przeciwną do $A = [a_{ij}]_{m \times n}$ jest macierz $-\mathbf{A} = [-a_{ij}]_{m \times n}$, przy czym $\mathbf{A} + (-\mathbf{A}) = \mathbf{0}$.
* **Macierz jednostkowa:** Jest rodzajem macierzy diagonalnej i elementem neutralnym mnożenia macierzy. Definiujemy ją jako $\mathbf{I}_n = [\delta_{ij}]_{n \times n}$, gdzie $\delta_{ij}$ to delta Kroneckera posiadająca jedynki na przekątnej:

$$\delta_{ij} = \begin{cases} 0, & i \neq j \\ 1, & i = j \end{cases}$$

  Spełnia warunek: $\mathbf{A} \cdot \mathbf{I}_n = \mathbf{I}_n \cdot \mathbf{A} = \mathbf{A}$.

## Transponowanie macierzy
Transponowanie macierzy polega na zamianie jej wierszy z kolumnami. Dla $\mathbf{A} = [a_{ij}]_{m \times n}$, macierz transponowaną oznaczamy jako $\mathbf{A}^T = [a_{ji}]_{n \times m}$.

> [!example] Przykład
> Dla macierzy $\mathbf{A} = \begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \\ 7 & 8 & 9 \end{bmatrix}$, macierz transponowana wynosi $\mathbf{A}^T = \begin{bmatrix} 1 & 4 & 7 \\ 2 & 5 & 8 \\ 3 & 6 & 9 \end{bmatrix}$.

**Własności macierzy transponowanych** (dla $\mathbf{A}, \mathbf{B}$ odpowiednich wymiarów i $\alpha \in F$):
* $(\mathbf{A} + \mathbf{B})^T = \mathbf{A}^T + \mathbf{B}^T$
* $(\alpha \mathbf{A})^T = \alpha \cdot \mathbf{A}^T$
* $(\mathbf{AB})^T = \mathbf{B}^T \cdot \mathbf{A}^T$
* $(\mathbf{A}^T)^T = \mathbf{A}$
* Macierz $\mathbf{A}$ nazywamy **antysymetryczną**, gdy $\mathbf{A}^T = -\mathbf{A}$.

## Macierze trójkątne i diagonalne
Niech $\mathbf{A} = [a_{ij}]_{m \times n}$. Wyróżniamy następujące rodzaje macierzy:
* **Macierz trójkątna górna:** Jeżeli $a_{ij} = 0$ dla każdego $i > j$.
* **Macierz trójkątna dolna:** Jeżeli $a_{ij} = 0$ dla każdego $i < j$.
* **Macierz diagonalna:** Jeżeli $a_{ij} = 0$ dla każdego $i \neq j$ (oznaczana jako $\mathrm{diag}(a_{11}, a_{22}, a_{33})$).

## Odwrotność macierzy
Macierz $\mathbf{A} \in \mathbb{M}_n(F)$ nazywamy **macierzą odwracalną**, jeżeli istnieje macierz $\mathbf{B} \in \mathbb{M}_n(F)$ taka, że:

$$\mathbf{A \cdot B = B \cdot A = I}$$

Jeżeli macierz $\mathbf{A}$ jest odwracalna, to istnieje dokładnie jedna macierz odwrotna, oznaczana jako $\mathbf{A}^{-1}$. Macierz jest odwracalna wtedy i tylko wtedy, gdy $\det(\mathbf{A}) \neq 0$.

Dla macierzy stopnia $2 \times 2$ postaci $\mathbf{A} = \begin{bmatrix} a & b \\ c & d \end{bmatrix}$, wzór na macierz odwrotną ma postać:

$$\mathbf{A}^{-1} = \frac{1}{\det(\mathbf{A})} \begin{bmatrix} d & -b \\ -c & a \end{bmatrix}$$

Zbiór wszystkich macierzy odwracalnych stopnia $n$ nad ciałem $F$ zapisujemy jako $\mathrm{Gl}_n(F)$. 
Dla $\mathbf{A, B} \in \mathrm{Gl}_n(F)$ zachodzi:
* $\mathbf{A \cdot B} \in \mathrm{Gl}_n(F)$
* $(\mathbf{AB})^{-1} = \mathbf{B}^{-1} \cdot \mathbf{A}^{-1}$
* $\mathbf{A}^{-1} \in \mathrm{Gl}_n(F)$
* $(\mathbf{A}^{-1})^{-1} = \mathbf{A}$
