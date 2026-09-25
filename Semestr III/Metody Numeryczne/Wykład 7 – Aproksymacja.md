## Sformułowanie zagadnienia
Zadanie aproksymacji polega na zastąpieniu funkcji $f$, którą znamy lub której wartość znamy w pewnych punktach, inną funkcją $F$, która będzie ją przybliżać. W odróżnieniu od interpolacji, w aproksymacji funkcja $F$ nie musi przechodzić dokładnie przez węzły.
* **Aproksymacja dyskretna:** gdy zbiór, na którym mierzymy błędy, jest zbiorem dyskretnym.
* **Aproksymacja integralna:** gdy zbiór, na którym mierzymy błędy, jest przedziałem.

Będziemy szukać funkcji $F \in E$, aproksymującej $f$, gdzie $E$ to $m+1$ wymiarowa podprzestrzeń liniowa z bazą $\mathcal{B}_E = \{\varphi_0(x), \varphi_1(x), \dots, \varphi_m(x)\}$. Funkcję $F$ (wielomian uogólniony) wyrażamy jako:

$$F(x) = a_0\varphi_0(x) + a_1\varphi_1(x) + \dots + a_m\varphi_m(x)$$

Współczynniki wyznaczamy tak, aby minimalizować normę różnicy $||F(x) - f(x)||$.

## Iloczyn skalarny funkcji
Iloczyn skalarny dla funkcji (z uwzględnieniem funkcji wagowej $w(x)$) definiujemy w następujący sposób:
* **Dla funkcji dyskretnych:**

  $$(g, h) = \sum_{j=0}^n w(x_j) \cdot g(x_j)h(x_j)$$

* **Dla funkcji integralnych:**

  $$(g, h) = \int_a^b w(x) \cdot g(x)h(x) dx$$

## Aproksymacja średniokwadratowa dyskretna
Dla funkcji określonej na dyskretnym zbiorze poszukujemy minimum sumy:

$$||F(x) - f(x)||^2 = \sum_{i=0}^n w(x_i)(F(x_i) - f(x_i))^2$$

Współczynniki wyznaczamy za pomocą układu równań:

$$\sum_{i=0}^m a_i \cdot (\varphi_i, \varphi_k) = (f, \varphi_k), \quad k \in \{0, 1, \dots, m\}$$

co w zapisie macierzowym daje układ $\mathbf{D}\mathbf{\overline{a}} = \mathbf{\overline{f}}$.

> [!abstract] Algorytm aproksymacji średniokwadratowej dyskretnej
> 0. **Dane**
>    - Stopień wielomianu $m$
>    - Funkcja wagowa $w(x)$
>    - Węzły $x_i$ i wartości $y_i$
> 1. **Inicjalizacja**
>    - $F(x) = a_0 + a_1x^1 + \dots + a_mx^m$
>    - $\varphi_0(x) = x^0, \dots, \varphi_m(x) = x^m$
> 2. **Wyznaczamy elementy wektora $\mathbf{\overline{f}}$**
>    - $\overline{f}_k = \sum_{j=0}^n w(x_j) \cdot f(x_j)\varphi_k(x_j)$
>    - $\mathbf{\overline{f}} = (\overline{f}_0, \dots, \overline{f}_m)^T$
> 3. **Wyznaczamy elementy macierzy $\mathbf{D}$**
>    - $d_{ki} = d_{ik} = \sum_{j=0}^n w(x_j) \cdot \varphi_i(x_j)\varphi_k(x_j)$
>    - Budujemy symetryczną macierz kwadratową $\mathbf{D}$
> 4. **Rozwiązujemy układ równań** $\mathbf{D}\mathbf{\overline{a}} = \mathbf{\overline{f}}$
>    - Wyznaczamy wektor współczynników $\mathbf{\overline{a}}$
> 5. **Wynik**
>    - $F(x) = a_0 + a_1x^1 + \dots + a_mx^m$

> [!example] Przykład dyskretny
> Aproksymować punkty wielomianem drugiego stopnia dla węzłów $x_i \in \{0, 1, 2, 3\}$, wartości $y_i \in \{1, -1, 2, 4\}$ oraz wagi $w(x)=1$.
> 6. $F(x) = a_0 + a_1x + a_2x^2$.
> 7. Po obliczeniach sum dla poszczególnych elementów: $\mathbf{\overline{f}} = \begin{bmatrix} 6 \\ 15 \\ 43 \end{bmatrix}$.
> 8. Po zsumowaniu iloczynów węzłów: $\mathbf{D} = \begin{bmatrix} 4 & 6 & 14 \\ 6 & 14 & 36 \\ 14 & 36 & 98 \end{bmatrix}$.
> 9. Z układu wyliczono współczynniki: $a_0 = \frac{7}{9}$, $a_1 = -\frac{9}{5}$, $a_2 = 1$.
> 10. **Wynik:** $F(x) = \frac{7}{9} - \frac{9}{5}x + x^2$.

## Aproksymacja średniokwadratowa integralna
Dla funkcji $f$, określonej na przedziale $[a, b]$, poszukujemy minimum całki:

$$||F(x) - f(x)||^2 = \int_a^b w(x)(F(x) - f(x))^2 dx$$

Układ macierzowy ma taką samą postać $\mathbf{D}\mathbf{\overline{a}} = \mathbf{\overline{f}}$, ale elementy wyznaczane są za pomocą całek.

> [!abstract] Algorytm aproksymacji średniokwadratowej integralnej
> 0. **Dane**
>    - Stopień wielomianu $m$
>    - Funkcja $y$, przedział $[a, b]$, waga $w(x)$
> 1. **Inicjalizacja**
>    - $F(x) = a_0 + a_1x^1 + \dots + a_mx^m$
>    - $\varphi_0(x) = x^0, \dots, \varphi_m(x) = x^m$
> 2. **Wyznaczamy elementy wektora $\mathbf{\overline{f}}$**
>    - $\overline{f}_k = \int_a^b w(x) \cdot f(x)\varphi_k(x) dx$
>    - $\mathbf{\overline{f}} = (\overline{f}_0, \dots, \overline{f}_m)^T$
> 3. **Wyznaczamy elementy macierzy $\mathbf{D}$**
>    - $d_{ki} = d_{ik} = \int_a^b w(x) \cdot \varphi_i(x)\varphi_k(x) dx$
>    - Budujemy macierz $\mathbf{D}$
> 4. **Rozwiązujemy układ równań** $\mathbf{D}\mathbf{\overline{a}} = \mathbf{\overline{f}}$
>    - Wyznaczamy wektor $\mathbf{\overline{a}}$
> 5. **Wynik**
>    - $F(x) = a_0 + a_1x^1 + \dots + a_mx^m$

> [!example] Przykład integralny
> Aproksymować na przedziale $[0, 1]$ funkcję $y = e^x$ funkcją liniową dla $w(x) = 1$.
> 1. Inicjalizacja: $m=1$, $F(x) = a_0 + a_1x$.
> 2. Obliczenie wektora: $\overline{f}_0 = \int_0^1 e^x dx = e - 1$, oraz (przez części) $\overline{f}_1 = \int_0^1 xe^x dx = 1$. Zatem $\mathbf{\overline{f}} = \begin{bmatrix} e - 1 \\ 1 \end{bmatrix}$.
> 3. Obliczenie macierzy: $d_{00} = \int_0^1 1 dx = 1$, $d_{01} = d_{10} = \int_0^1 x dx = \frac{1}{2}$, $d_{11} = \int_0^1 x^2 dx = \frac{1}{3}$. Zatem $\mathbf{D} = \begin{bmatrix} 1 & \frac{1}{2} \\ \frac{1}{2} & \frac{1}{3} \end{bmatrix}$.
> 4. Po rozwiązaniu układu równań wyliczono: $a_0 = 2(2e - 5)$ oraz $a_1 = 6(3 - e)$.
> 5. **Wynik:** $F(x) = 2(2e - 5) + 6(3 - e)x$.
