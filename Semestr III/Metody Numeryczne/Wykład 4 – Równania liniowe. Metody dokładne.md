## Układy trójkątne
Układy równań liniowych, których macierze są macierzami trójkątnymi, rozwiązuje się szczególnie łatwo.

**Układ z macierzą trójkątną górną**
* Ma postać układu równań, w którym współczynniki pod główną przekątną są zerowe. 
* Jeżeli $a_{ii} \ne 0$, to niewiadome można wyznaczyć w kolejności od ostatniej do pierwszej.
* Można to zwinąć do jednego wzoru: $x_i = \frac{b_i - \sum_{j=i+1}^n a_{ij}x_j}{a_{ii}}$.
* Algorytm ten, ze względu na swoją specyfikę, nazywa się **postępowaniem odwrotnym**.

**Układ z macierzą trójkątną dolną**
* Korzystamy wtedy z algorytmu nazywanego **postępowaniem wprzód**.
* Kolejne elementy wektora $\mathbf{x}$ obliczamy za pomocą wzoru: $x_i = \frac{b_i - \sum_{j=1}^{i-1} a_{ij}x_j}{a_{ii}}$.

> [!example] Rozwiązywanie układu równań (postępowanie odwrotne)
> 1. **Dane układu:**
>    $2x_1 + 3x_2 - 4x_3 = 1$
>    $7x_2 + 10x_3 = 17$
>    $4x_3 = 4$
> 2. **Podstawiamy pod wzór postępowania odwrotnego:**
>    $x_3 = \frac{4}{4} = 1$
>    $x_2 = \frac{17 - 10x_3}{7} = 1$
>    $x_1 = \frac{1 + 4x_3 - 3x_2}{2} = 1$
> 3. **Wynik:**
>    Wektor $\mathbf{x} = (1, 1, 1)$
## Eliminacja Gaussa
Najważniejszą z metod bezpośredniego rozwiązywania układ równań liniowych jest 
eliminacja Gaussa.

Zaczynamy od doprowadzenia macierzy do postaci REF. W tym celu wykonujemy kolejne przekształcenia elementarne zerując po kolei każdą z kolumn (zaczynając od lewej strony $\rightarrow$), oprócz jej elementu wiodącego. W tym celu wykorzystujemy element wiodący danego wiersza, czyli wykonujemy takie przekształcenia elementarne, że $w_n±w_w$, gdzie $w_w$ to wiersz, w którym leży element wiodący. Po wyzerowaniu pierwszej kolumny, powtarzamy czynność dla kolejnych.

Gdy doprowadzimy parę $[\mathbf{A} \mid \mathbf{b}]$  do postaci REF otrzymujemy macierz trójkątną górną, możemy teraz skorzystać z postępowania odwrotnego, żeby wyznaczyć macierz $\mathbf{x}$.

Standardowa eliminacja Gaussa zawodzi, gdy któryś z elementów wiodących $a_{ii}=0$, możemy wtedy skorzystać z tzw. częściowego wyboru elementów wiodących.
## Algorytm Thomasa
Macierzą trójdiagonalną (trójprzekątniową) nazywamy macierz kwadratową $\mathbf{A}$, w której wszystkie elementy poza główną przekątną i dwoma sąsiednimi przekątnymi są zerowe.

Rozważać będziemy trójprzekątniowy układ równań liniowych $\mathbf{A}\mathbf{x} = \mathbf{d}$, zapisany w postaci:
$$ d_i = a_i x_{i-1} + b_i x_i + c_i x_{i+1}, \quad i \in \{1, 2, \dots, n\} $$
Rozwiązania układu szukamy w postaci zależnej od współczynników: $x_i = \beta_i x_{i+1} + \gamma_i$.

> [!abstract] Algorytm Thomasa
> 1. **Dane**
>    - Macierz trójprzekątniowa $\mathbf{A}$
>    - Kolumna wyrazów wolnych $\mathbf{d}$
> 2. **Liczymy** $\beta_1$, $\gamma_1$
>    - $\beta_1 = \frac{-c_1}{b_1}$
>    - $\gamma_1 = \frac{d_1}{b_1}$
> 3. **Dla $i \in \{1, 2, \dots, n\}$ liczymy współczynniki** $\beta_i$, $\gamma_i$
>    - $\beta_i = \frac{-c_i}{a_i \beta_{i-1} + b_i}$
>    - $\gamma_i = \frac{d_i - a_i \gamma_{i-1}}{a_i \beta_{i-1} + b_i}$
> 4. **Podstawiamy** $\gamma_n$
>    - $x_n = \gamma_n$
> 5. **Dla $i \in \{1, 2, \dots, n-1\}$ liczymy** $x_i$
>    - $x_i = \beta_i x_{i+1} + \gamma_i$
> 6. **Wynik**
>    - $\mathbf{x} = \begin{bmatrix} x_1 \\ x_2 \\ \vdots \\ x_n \end{bmatrix}$
## Algorytm Banachiewicza rozkładu LU
W tej metodzie macierz $\mathbf{A}$ układu równań liniowych przedstawiamy w postaci iloczynu dwóch macierzy trójkątnych $\mathbf{L}$ oraz $\mathbf{U}$, gdzie $\mathbf{L}$ jest macierzą trójkątną dolną, a $\mathbf{U}$ macierzą trójkątną górną (z jedynkami na przekątnej).
* Równanie $\mathbf{A}\mathbf{x} = \mathbf{b}$ przyjmuje postać $\mathbf{L}\mathbf{U}\mathbf{x} = \mathbf{b}$.
* Przyjmując $\mathbf{y} = \mathbf{U}\mathbf{x}$, aby rozwiązać układ równań $\mathbf{A}\mathbf{x} = \mathbf{b}$, musimy rozwiązać dwa układy trójkątne: $\mathbf{L}\mathbf{y} = \mathbf{b}$ oraz $\mathbf{U}\mathbf{x} = \mathbf{y}$.
* Problem sprowadza się do rozłożenia macierzy $\mathbf{A}$ na macierze $\mathbf{L}$ i $\mathbf{U}$ za pomocą algorytmu Banachiewicza.

> [!abstract] Algorytm Banachiewicza rozkładu LU
> 1. **Dane**
>    - Macierz $\mathbf{A} = \mathbf{L}\mathbf{U}$
> 2. **Dla $i \in \{1, 2, \dots, n\}$ liczymy** $l_{i1}$
>    - $l_{i1} = a_{i1}$
> 3. **Dla $j \in \{2, 3, \dots, n\}$ liczymy** $u_{1j}$
>    - $u_{1j} = \frac{a_{1j}}{l_{11}}$
> 4. **Dla $j \in \{2, 3, \dots, n\}$ liczymy:**
>    - a) Dla $i \in \{2, 3, \dots, j-1\}$ liczymy:
>      $u_{ij} = \frac{1}{l_{ii}} \cdot \left(a_{ij} - \sum_{k=1}^{i-1} l_{ik} u_{kj}\right)$
>    - b) Dla $i \in \{j, j+1, \dots, n\}$ liczymy:
>      $l_{ij} = a_{ij} - \sum_{k=1}^{i-1} l_{ik} u_{kj}$
> 5. **Wynik**
>    - $\mathbf{L} = [l_{ij}]_{n \times n}$
>    - $\mathbf{U} = [u_{ij}]_{n \times n}$