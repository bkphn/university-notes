## Schemat ogólny metod iteracyjnych
Układ równań liniowych możemy zapisać w postaci macierzowej $\mathbf{Ax} = \mathbf{b}$, gdzie $\mathbf{A} = [a_{ij}]_{n \times n}$ jest macierzą współczynników, $\mathbf{x}$ kolumną niewiadomych, a $\mathbf{b}$ kolumną wyrazów wolnych.

Zakładamy, że macierz $\mathbf{A}$ jest nieosobliwa ($\det \mathbf{A} \ne 0$), co oznacza, że układ ma dokładnie jedno rozwiązanie $\mathbf{x}_d$.

W metodach iteracyjnych poszukujemy przybliżeń $\mathbf{x}_m$ (gdzie $\mathbf{x}_0$ to przybliżenie początkowe), korzystając z jednokrokowego, stacjonarnego wzoru iteracyjnego:

$$\mathbf{x}_{i+1} = \mathbf{M}\mathbf{x}_i + \mathbf{w}$$

Stacjonarność oznacza, że macierz $\mathbf{M}$ i wektor $\mathbf{w}$ nie zmieniają się w kolejnych krokach iteracji.
Wprowadzając macierz $\mathbf{N} = (\mathbf{I} - \mathbf{M})\mathbf{A}^{-1}$, otrzymujemy $\mathbf{w} = \mathbf{Nb}$. Podstawiając to do wzoru iteracyjnego:

$$\mathbf{x}_{i+1} = \mathbf{M}\mathbf{x}_i + \mathbf{Nb}$$

Rozwiązanie dokładne $\mathbf{x}_d$ musi być punktem stałym przekształcenia ($\mathbf{x}_d = \mathbf{M}\mathbf{x}_d + \mathbf{Nb}$).
Aby wzór był poprawny, macierze $\mathbf{M}, \mathbf{N}$ muszą spełniać **test zgodności**:

$$\mathbf{M} + \mathbf{NA} = \mathbf{I}$$

## Zbieżność
**Promień spektralny macierzy**
Liczbę $\rho(\mathbf{A}) = \max_{i \in \{1, \dots, n\}} |\lambda_i|$, gdzie $\lambda_i$ to wartości własne macierzy $\mathbf{A}$, nazywamy promieniem spektralnym. 

> [!danger] Warunek zbieżności przybliżeń
> Jeśli promień spektralny macierzy iteracji jest mniejszy od jedynki ($\rho(\mathbf{M}) < 1$), to ciąg $\{\mathbf{x}_i\}$ uzyskany z metody jest zbieżny do rozwiązania dokładnego przy dowolnym przybliżeniu początkowym.

**Norma wektora**
Normą wektora $\mathbf{v} = (v_1, v_2, \dots, v_n)$ w przestrzeni euklidesowskiej nazywamy pierwiastek z sumy kwadratów jego współrzędnych (długość wektora):

$$||\mathbf{v}|| = \sqrt{v_1^2 + v_2^2 + \dots + v_n^2}$$

## Metoda Jacobiego
Macierz $\mathbf{A}$ rozkładamy na sumę trzech macierzy: $\mathbf{A} = \mathbf{L} + \mathbf{D} + \mathbf{U}$.
* $\mathbf{L}$ – macierz poddiagonalna
* $\mathbf{D}$ – macierz diagonalna (jeżeli elementy na przekątnej są zerowe, należy odpowiednio przestawić wiersze, by $\det \mathbf{D} \ne 0$)
* $\mathbf{U}$ – macierz naddiagonalna

Po przekształceniu równania $(\mathbf{L} + \mathbf{D} + \mathbf{U})\mathbf{x} = \mathbf{b}$ otrzymujemy wzór iteracyjny:

$$\mathbf{x}_{i+1} = -\mathbf{D}^{-1}(\mathbf{L} + \mathbf{U})\mathbf{x}_i + \mathbf{D}^{-1}\mathbf{b}$$

Co daje nam postać macierzy ogólnych:
* $\mathbf{M} = -\mathbf{D}^{-1}(\mathbf{L} + \mathbf{U})$
* $\mathbf{N} = \mathbf{D}^{-1}$

Test zgodności potwierdza poprawność metody: $\mathbf{M} + \mathbf{NA} = -\mathbf{D}^{-1}(\mathbf{L} + \mathbf{U}) + \mathbf{D}^{-1}\mathbf{A} = \mathbf{D}^{-1}(\mathbf{A} - \mathbf{L} - \mathbf{U}) = \mathbf{D}^{-1}\mathbf{D} = \mathbf{I}$. Błędem przybliżenia jest wartość normy $||\mathbf{Ax}_n - \mathbf{b}||$.

> [!abstract] Algorytm Metody Jacobiego
> 1. **Dane**
>    - Macierz $\mathbf{A}$
>    - Kolumna wyrazów wolnych $\mathbf{b}$
>    - Przybliżenie początkowe $\mathbf{x}_0$
>    - Dokładność $\varepsilon$
> 2. **Wyznaczamy potrzebne macierze**
>    - $\mathbf{D}^{-1}$
>    - $(\mathbf{L} + \mathbf{U})$
> 3. **Obliczamy $\mathbf{M}, \mathbf{w}$**
>    - $\mathbf{M} = -\mathbf{D}^{-1}(\mathbf{L} + \mathbf{U})$
>    - $\mathbf{w} = \mathbf{D}^{-1}\mathbf{b}$
> 4. **Podstawiamy $\mathbf{x}_n$**
>    - $\mathbf{x}_n = \mathbf{x}_0$
> 5. **Tak długo jak $||\mathbf{A}\mathbf{x}_n - \mathbf{b}|| > \varepsilon$:**
>    - $\mathbf{x}_s = \mathbf{x}_n$
>    - $\mathbf{x}_n = \mathbf{M}\mathbf{x}_s + \mathbf{w}$
> 6. **Wynik**
>    - Wynikiem jest wektor $\mathbf{x} = \mathbf{x}_n$

## Metoda Gaussa-Seidla
W metodzie Jacobiego nie używa się nowo obliczonych, „ulepszonych” wartości składowych wektora przed obliczeniem całego nowego wektora $\mathbf{x}_{i+1}$. Metoda Gaussa-Seidla różni się tym, że poprawione wartości poszczególnych składowych są wykorzystywane zaraz po ich wyliczeniu, podczas tej samej iteracji.

Po rozkładzie $\mathbf{A} = \mathbf{L} + \mathbf{D} + \mathbf{U}$, iteracja wygląda następująco:

$$\mathbf{x}_{i+1} = -\mathbf{D}^{-1}\mathbf{L}\mathbf{x}_{i+1} - \mathbf{D}^{-1}\mathbf{U}\mathbf{x}_i + \mathbf{D}^{-1}\mathbf{b}$$

W zapisie składowych:

$$x_{k(i+1)} = -\frac{1}{a_{kk}} \sum_{j=1}^{k-1} a_{kj} x_{j(i+1)} - \frac{1}{a_{kk}} \sum_{j=k+1}^n a_{kj} x_{j(i)} + \frac{1}{a_{kk}} b_k$$

W postaci schematu ogólnego:
* $\mathbf{M} = -(\mathbf{D} + \mathbf{L})^{-1}\mathbf{U}$
* $\mathbf{N} = (\mathbf{D} + \mathbf{L})^{-1}$
Metoda jest zbieżna dla $\rho(\mathbf{M}) < 1$.

> [!abstract] Algorytm Metody Gaussa-Seidla
> 1. **Dane**
>    - Macierz $\mathbf{A}$
>    - Kolumna wyrazów wolnych $\mathbf{b}$
>    - Przybliżenie początkowe $\mathbf{x}_0$
>    - Dokładność $\varepsilon$
> 2. **Wyznaczamy potrzebne macierze**
>    - $(\mathbf{D} + \mathbf{L})^{-1}$
> 3. **Obliczamy $\mathbf{M}, \mathbf{w}$**
>    - $\mathbf{M} = -(\mathbf{D} + \mathbf{L})^{-1}\mathbf{U}$
>    - $\mathbf{w} = (\mathbf{D} + \mathbf{L})^{-1}\mathbf{b}$
> 4. **Podstawiamy $\mathbf{x}_n$**
>    - $\mathbf{x}_n = \mathbf{x}_0$
> 5. **Tak długo jak $||\mathbf{A}\mathbf{x}_n - \mathbf{b}|| > \varepsilon$:**
>    - $\mathbf{x}_s = \mathbf{x}_n$
>    - $\mathbf{x}_n = \mathbf{M}\mathbf{x}_s + \mathbf{w}$
> 6. **Wynik**
>    - Wynikiem jest wektor $\mathbf{x} = \mathbf{x}_n$

