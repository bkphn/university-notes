## Układy równań liniowych
Układem równań liniowych nazywamy układ równań w postaci:

$$\begin{cases} a_{11}x_1 + a_{12}x_2 + \dots + a_{1n}x_n = b_1 \\ a_{21}x_1 + a_{22}x_2 + \dots + a_{2n}x_n = b_2 \\ \vdots \\ a_{n1}x_1 + a_{n2}x_2 + \dots + a_{nn}x_n = b_n \end{cases}$$

Rozwiązaniem tego układu jest macierz $\mathbf{x} = \begin{bmatrix} x_1 \\ x_2 \\ \vdots \\ x_n \end{bmatrix}$. Macierz $\mathbf{b} = \begin{bmatrix} b_1 \\ b_2 \\ \vdots \\ b_n \end{bmatrix}$ nazywamy macierzą bądź kolumną wyrazów wolnych.

Układy możemy podzielić, ze względu na liczbę rozwiązań:
* **Układ oznaczony:** ma dokładnie jedno rozwiązanie.
* **Układ nieoznaczony:** ma więcej niż jedno rozwiązanie.
* **Układ sprzeczny:** nie ma rozwiązań.

## Równanie macierzowe
Zapis za pomocą układu równań jest tożsamy z zapisem za pomocą iloczynu macierzy:

$$\begin{bmatrix} a_{11} & \dots & a_{1m} \\ \vdots & \ddots & \vdots \\ a_{n1} & \dots & a_{nm} \end{bmatrix} \cdot \begin{bmatrix} x_1 \\ \vdots \\ x_n \end{bmatrix} = \begin{bmatrix} b_1 \\ \vdots \\ b_n \end{bmatrix}$$

Równanie macierzowe $\mathbf{A}\mathbf{x} = \mathbf{b}$ można rozwinąć do powyższej postaci.

### Wzory Cramera
Układ równań $\mathbf{A}x = \mathbf{b}$ nazywamy układem Cramera, jeśli $\det \mathbf{A} \neq 0$. Wzory Cramera pozwalają na obliczanie elementów macierzy $\mathbf{x}$:

$$x_1 = \frac{W_{x_1}}{W}, \quad x_2 = \frac{W_{x_2}}{W}, \quad \dots, \quad x_n = \frac{W_{x_n}}{W}$$

Gdzie:
* $W = \det \mathbf{A}$
* $W_{x_i} = \det \mathbf{A}_i$
* $\mathbf{A}_i$ to macierz powstała poprzez zastąpienie $i$-tej kolumny kolumną wyrazów wolnych.

## Macierz rozszerzona i Algorytm Eliminacji Gaussa
Macierzą rozszerzoną nazywamy macierz $[\mathbf{A} \mid \mathbf{b}]$, gdzie $\mathbf{b}$ jest macierzą wyrazów wolnych:

$$[\mathbf{A} \mid \mathbf{b}] = \begin{bmatrix} a_{11} & \dots & a_{1m} & b_1 \\ \vdots & \ddots & \vdots & \vdots \\ a_{n1} & \dots & a_{nm} & b_n \end{bmatrix}$$

Z wykorzystaniem macierzy rozszerzonej możemy wyznaczyć niewiadomą $\mathbf{x}$ za pomocą Algorytmu Eliminacji Gaussa:

$$[\mathbf{A} \mid \mathbf{b}] \xrightarrow{\text{Eliminacja Gaussa}} [\mathbf{A}' \mid \mathbf{b}']$$

Wystarczy sprowadzić macierz $\mathbf{A}$ do postaci schodkowej REF. Za pomocą macierzy, która zostanie utworzona wtedy z macierzy $\mathbf{b}$, jesteśmy w stanie obliczyć rozwiązanie układu równań, podstawiając otrzymane wartości do układu równań.

> [!example] Przykład obliczenia układu
> Rozważmy układ równań:
>
> $$\begin{cases} x + y + z + t = 2 \\ x + 2y + 2z + 2t = 3 \\ x - y + z - t = 2 \\ x + y + z + 2t = 1 \end{cases}$$
>
> Macierz rozszerzona $[\mathbf{A} \mid \mathbf{b}]$ po sprowadzeniu do postaci schodkowej daje układ:
>
> $$\begin{cases} x + y + z + t = 2 \\ y + z + t = 1 \\ 2z = 2 \\ t = -1 \end{cases}$$
>

## Układy nieoznaczone
Układem nieoznaczonym nazywamy równanie macierzowe posiadające więcej niż jedno rozwiązanie. Dzieje się tak, gdy zarówno któryś z wierszy w $\mathbf{A}$ doprowadzonej do postaci schodkowej REF, jak i ten sam wiersz w kolumnie wyrazów wolnych $\mathbf{b}'$ się wyzerowały:

$$\begin{bmatrix} a_{11} & \dots & a_{1m} & b_1 \\ \vdots & \ddots & \vdots & \vdots \\ 0 & \dots & 0 & 0 \end{bmatrix}$$

W tym przypadku należy **sparametryzować** zmienne, które nie posiadają rozwiązań jednoznacznych, i zależnie od nich wyznaczyć pozostałe współczynniki. Aby sparametryzować zmienną, przyrównujemy ją do parametru należącego do ciała $F$ (np. $x = \alpha, \alpha \in F$), a następnie rozwiązujemy układ równań. Rozwiązanie zapisujemy w postaci wektora lub układu równań.

## Układy sprzeczne
Układem sprzecznym nazywamy równanie macierzowe nieposiadające rozwiązań w ciele $F$. Układ jest sprzeczny, jeżeli po sprowadzeniu macierzy $\mathbf{A}$ do postaci schodkowej REF **jeden z wierszy w części macierzy $\mathbf{A}$ się wyzerował, jednak w odróżnieniu od układu nieoznaczonego nie wyzerował się współczynnik w kolumnie wyrazów wolnych $\mathbf{b}'$**:

$$\begin{bmatrix} a_{11} & \dots & a_{1m} & b_1 \\ \vdots & \ddots & \vdots & \vdots \\ 0 & \dots & 0 & b_n \end{bmatrix} \quad \text{(gdzie } b_n \neq 0 \text{)}$$

Taki wiersz daje równanie sprzeczne typu $0 = b_n$ (np. $0 = -7$), co oznacza brak rozwiązań.

## Twierdzenie Kroneckera - Capellego
Twierdzenie to pozwala określić istnienie i rodzaj rozwiązań układu równań $\mathbf{A}x = \mathbf{b}$ za pomocą rzędów macierzy.
>[!danger] Twierdzenie Kroneckera-Capellego
>* Układ równań $\mathbf{A}\mathbf{x} = \mathbf{b}$ ma rozwiązanie $\iff r(\mathbf{A}) = r([\mathbf{A} \mid \mathbf{b}])$.
> * Układ równań $\mathbf{A}\mathbf{x} = \mathbf{b}$ jest **oznaczony** $\iff r(\mathbf{A}) = r([\mathbf{A} \mid \mathbf{b}]) = n$.
>* Układ równań $\mathbf{A}\mathbf{x} = \mathbf{b}$ jest **nieoznaczony** $\iff r(\mathbf{A}) = r([\mathbf{A} \mid \mathbf{b}]) < n$, wtedy rozwiązanie jest zależne od dokładnie $(n - r(A))$ parametrów.

Gdzie $n$ to liczba niewiadomych, a $r([\mathbf{A} \mid \mathbf{b}])$ to rząd macierzy rozszerzonej, który obliczamy tak samo jak zwykły rząd macierzy, pomijając kreskę pionową i traktując macierz jako jedną całość.
