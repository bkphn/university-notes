## Postać schodkowa REF
Postać schodkowa to szczególna postać macierzy, określana jako REF (Row Echelon Form). Aby macierz była w formie schodkowej, musi spełniać następujące wymogi:
* Wiersze zerowe są na dole – wszystkie wiersze zawierające same zera muszą być pod wierszami niezerowymi.
* W każdym niezerowym wierszu element wiodący występuje dalej na prawo niż w poprzednim wierszu.
* Element wiodący to pierwszy niezerowy element w danym wierszu (zaczynając od lewej).
* Wszystkie elementy poniżej każdego elementu wiodącego są zerami (dopuszczalne jest, by zera znajdowały się również nad nimi).

**Przykłady macierzy w postaci schodkowej REF:**
$$ \mathbf{A} = \begin{bmatrix} 0 & 1 & 3 \\ 0 & 2 & 0 \\ 0 & 0 & 3 \end{bmatrix} $$
$$ \mathbf{B} = \begin{bmatrix} 1 & 6 & 3 \\ 0 & 0 & 6 \\ 0 & 0 & 0 \end{bmatrix} $$
## Postać zredukowana RREF
Postać schodkowa zredukowana (RREF – Reduced Row Echelon Form) to inna forma postaci schodkowej, do której możemy doprowadzić macierz. Aby macierz była w postaci RREF, musi spełniać wymogi postaci REF oraz dodatkowe warunki:
* Każdy element wiodący musi być równy 1 (pierwszy niezerowy element w każdym niezerowym wierszu wynosi 1).
* Każdy element wiodący musi być jedynym niezerowym elementem w swojej kolumnie – wszystkie elementy nad i pod elementem wiodącym są zerami.

**Przykłady macierzy w postaci schodkowej zredukowanej RREF:**
$$ \mathbf{A} = \begin{bmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix} $$
$$ \mathbf{B} = \begin{bmatrix} 1 & 0 & -2 \\ 0 & 1 & 3 \\ 0 & 0 & 0 \end{bmatrix} $$
## Przekształcenia elementarne macierzy
Na macierzach możemy wykonywać tzw. przekształcenia elementarne, czyli operacje pozwalające na ich modyfikację. Wyróżniamy następujące przekształcenia:

1. **Dodawanie i odejmowanie wierszy:** Od każdego wiersza macierzy możemy odjąć bądź dodać inny. Operacja ta polega na operowaniu na odpowiadających sobie współczynnikach:
   $$ \begin{bmatrix} a_1 & a_2 & a_3 \end{bmatrix} \pm \begin{bmatrix} b_1 & b_2 & b_3 \end{bmatrix} = \begin{bmatrix} a_1 \pm b_1 & a_2 \pm b_2 & a_3 \pm b_3 \end{bmatrix} $$
   Otrzymany wiersz zastępuje wiersz, od którego odejmowaliśmy. Zapisujemy to jako $\mathbf{A} \xrightarrow{w_n \pm w_k} \mathbf{A}'$, gdzie $n, k$ to numery wierszy.

2. **Mnożenie wiersza przez skalar:** Dowolny wiersz macierzy możemy pomnożyć przez dowolny niezerowy skalar, aby otrzymać nowy wiersz zastępujący poprzedni. Polega to na mnożeniu każdego współczynnika wiersza przez ten skalar:
   $$ \begin{bmatrix} a_1 & a_2 & a_3 \end{bmatrix} \cdot \alpha = \begin{bmatrix} \alpha \cdot a_1 & \alpha \cdot a_2 & \alpha \cdot a_3 \end{bmatrix} $$
   Zapisujemy to jako $\mathbf{A} \xrightarrow{w_n \cdot \alpha} \mathbf{A}'$, gdzie $\alpha \neq 0$.

3. **Dodawanie i odejmowanie krotności wiersza:** Połączenie dwóch powyższych przekształceń:
   $$ \begin{bmatrix} a_1 & a_2 & a_3 \end{bmatrix} \pm \alpha \begin{bmatrix} b_1 & b_2 & b_3 \end{bmatrix} = \begin{bmatrix} a_1 \pm \alpha b_1 & a_2 \pm \alpha b_2 & a_3 \pm \alpha b_3 \end{bmatrix} $$
   Zapisujemy to jako $\mathbf{A} \xrightarrow{w_n \pm \alpha w_k} \mathbf{A}'$ dla $\alpha \neq 0$.

4. **Zamiana wierszy miejscami:** Jeżeli zamienimy $n$-ty wiersz z $k$-tym, to $n$-ty wiersz stanie się $k$-tym i *vice versa*. Zapisujemy to jako $\mathbf{A} \xrightarrow{w_n \leftrightarrow w_k} \mathbf{A}'$.
## Algorytmy przekształceń
* **Algorytm Eliminacji Gaussa:** Służy do doprowadzenia macierzy do postaci REF. Wykonujemy kolejne przekształcenia elementarne, zerując po kolei każdą z kolumn (zaczynając od lewej strony) oprócz elementu wiodącego, wykorzystując go do zerowania elementów pod nim ($w_n \pm w_w$, gdzie $w_w$ to wiersz z elementem wiodącym).
* **Algorytm Eliminacji Gaussa-Jordana:** Rozszerzenie Algorytmu Eliminacji Gaussa pozwalające na doprowadzenie macierzy do postaci RREF. Po uzyskaniu postaci REF kontynuujemy przekształcenia, zerując współczynniki nad elementami wiodącymi (zaczynając od prawej strony). *Uwaga: jeżeli na głównej przekątnej znajduje się element zerowy, macierz w tej formie może wymagać przestawienia wierszy, by dokończyć RREF*.
## Wyznaczanie macierzy odwrotnych
Parą macierzy nazywamy dwie macierze o takich samych wymiarach, zapisywane jako $[\mathbf{A} \mid \mathbf{B}]$. Wykonując dowolne przekształcenie elementarne na jednej z nich, identyczne operacje wykonujemy na drugiej.

Wykorzystując **Algorytm Eliminacji Gaussa-Jordana**, możemy wyznaczyć macierz odwrotną:
1. Tworzymy parę macierzy $[\mathbf{A} \mid \mathbf{I}]$, gdzie $\mathbf{I}$ to macierz jednostkowa o wymiarach identycznych jak $\mathbf{A}$.
2. Stosujemy algorytm, przekształcając lewą stronę $\mathbf{A}$ do macierzy jednostkowej $\mathbf{I}$.
3. W wyniku po prawej stronie otrzymujemy macierz odwrotną $\mathbf{A}^{-1}$:
   $$ [\mathbf{A} \mid \mathbf{I}] \xrightarrow{\text{Gauss-Jordan}} [\mathbf{I} \mid \mathbf{A}^{-1}] $$

> [!example] Wykorzystując Algorytm Eliminacji Gaussa - Jordana wyznacz macierz $\mathbf{A}^{-1}$
> $$ \mathbf{A} = \begin{bmatrix} 1 & 2 & 3 & 4 \\ 1 & 3 & 5 & 7 \\ 2 & 5 & 9 & 13 \\ 3 & 7 & 11 & 16 \end{bmatrix} $$
> 
> $$ [\mathbf{A} \mid \mathbf{I}] = \left[\begin{array}{cccc|cccc} 1 & 2 & 3 & 4 & 1 & 0 & 0 & 0 \\ 1 & 3 & 5 & 7 & 0 & 1 & 0 & 0 \\ 2 & 5 & 9 & 13 & 0 & 0 & 1 & 0 \\ 3 & 7 & 11 & 16 & 0 & 0 & 0 & 1 \end{array}\right] \xrightarrow{\substack{w_2-w_1 \\ w_3-2w_1 \\ w_4-3w_1}} \left[\begin{array}{cccc|cccc} 1 & 2 & 3 & 4 & 1 & 0 & 0 & 0 \\ 0 & 1 & 2 & 3 & -1 & 1 & 0 & 0 \\ 0 & 1 & 3 & 5 & -2 & 0 & 1 & 0 \\ 0 & 1 & 2 & 4 & -3 & 0 & 0 & 1 \end{array}\right] \rightarrow $$
> 
> $$ \xrightarrow{\substack{w_3-w_2 \\ w_4-w_2}} \left[\begin{array}{cccc|cccc} 1 & 2 & 3 & 4 & 1 & 0 & 0 & 0 \\ 0 & 1 & 2 & 3 & -1 & 1 & 0 & 0 \\ 0 & 0 & 1 & 2 & -1 & -1 & 1 & 0 \\ 0 & 0 & 0 & 1 & -2 & -1 & 0 & 1 \end{array}\right] \xrightarrow{\substack{w_3-2w_4 \\ w_2-3w_4 \\ w_1-4w_4}} \left[\begin{array}{cccc|cccc} 1 & 2 & 3 & 0 & 9 & 4 & 0 & -4 \\ 0 & 1 & 2 & 0 & 5 & 4 & 0 & -3 \\ 0 & 0 & 1 & 0 & 3 & 1 & 1 & -2 \\ 0 & 0 & 0 & 1 & -2 & -1 & 0 & 1 \end{array}\right] \rightarrow $$
> 
> $$ \xrightarrow{\substack{w_2-2w_3 \\ w_1-3w_3}} \left[\begin{array}{cccc|cccc} 1 & 2 & 0 & 0 & 0 & 1 & -3 & 2 \\ 0 & 1 & 0 & 0 & -1 & 2 & -2 & 1 \\ 0 & 0 & 1 & 0 & 3 & 1 & 1 & -2 \\ 0 & 0 & 0 & 1 & -2 & -1 & 0 & 1 \end{array}\right] \xrightarrow{w_1-2w_2} \left[\begin{array}{cccc|cccc} 1 & 0 & 0 & 0 & 2 & -3 & 1 & 0 \\ 0 & 1 & 0 & 0 & -1 & 2 & -2 & 1 \\ 0 & 0 & 1 & 0 & 3 & 1 & 1 & -2 \\ 0 & 0 & 0 & 1 & -2 & -1 & 0 & 1 \end{array}\right] $$
> 
> $$ \mathbf{A}^{-1} = \begin{bmatrix} 2 & -3 & 1 & 0 \\ -1 & 2 & -2 & 1 \\ 3 & 1 & 1 & -2 \\ -2 & -1 & 0 & 1 \end{bmatrix} $$

## Wyznacznik macierzy
Wyznacznik macierzy istnieje tylko w przypadku macierzy kwadratowych i informuje o tym, czy dana macierz jest odwracalna. Oznaczamy go jako $\det(\mathbf{A})$ lub $|\mathbf{A}|$.

Ogólny wzór na wyznacznik macierzy $n \times n$ (tzw. **wzór Laplace'a**):
$$ \det(\mathbf{A}) = \sum_{k=1}^{n} (-1)^{k+j} \det(\mathbf{A}_{kj}) = \sum_{k=1}^{n} (-1)^{i+k} \det(\mathbf{A}_{ik}) $$
Gdzie $\mathbf{A}_{ij}$ to macierz powstała z macierzy $\mathbf{A}$ poprzez usunięcie $i$-tego wiersza oraz $j$-tej kolumny. Wzór ten jest konieczny dla wymiarów większych niż $3 \times 3$.
### Metody obliczania dla mniejszych wymiarów:
* **Metoda Sarrusa (dla macierzy $3 \times 3$):** Dodajemy do siebie wartości po przekątnych głównych, a następnie odejmujemy wartości po przekątnych pobocznych.
  $$ \det\left(\begin{bmatrix} a & b & c \\ d & e & f \\ g & h & i \end{bmatrix}\right) = aei + bfg + cdh - ceg - fhi - abd $$

* **Dla macierzy $2 \times 2$:** $\det\left(\begin{bmatrix} a & b \\ c & d \end{bmatrix}\right) = ad - bc$.
* **Dla macierzy $1 \times 1$:** $\det([a]) = a$.

**Własności wyznaczników:**
$$\det(\mathbf{A}^T) = \det(\mathbf{A})$$
$$\det(\alpha \mathbf{A}_{n \times n}) = \alpha^n \det(\mathbf{A})$$
$$\det(\mathbf{AB}) = \det(\mathbf{A}) \cdot \det(\mathbf{B})$$
$$\det(\mathbf{A}^{-1}) = \frac{1}{\det(\mathbf{A})}$$
