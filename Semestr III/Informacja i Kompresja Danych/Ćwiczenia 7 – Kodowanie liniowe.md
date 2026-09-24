## Algorytm kodowania liniowego
W poniższych przykładach będziemy korzystali z okrojonej wersji algorytmu kodowania liniowego, ograniczając się tylko do pierwszych 11 podpunktów, spowodowane jest to tym, że na kolokwium obowiązuje nas tylko ten zakres algorytmu.

>[!abstract] Algorytm kodowania liniowego (1–11)
> 0. **Dane:**
> - Komunikat $\mathbf{m}$
  > - Macierz generująca $\mathbf{G} = \begin{bmatrix} \mathbf{c}_1 \\ \vdots \\ \mathbf{c}_\alpha \end{bmatrix} \in \mathbb{M}_{\alpha,\beta}(F_q)$
>1. **Wyznaczamy długość $n$ kodu $C$:**
  > $$ n = \beta, \quad \mathbf{G} \in \mathbb{M}_{\alpha,\beta} $$
>2. **Wyznaczamy wymiar $k$ kodu $C$:**
>   $$ k = \alpha, \quad \mathbf{G} \in \mathbb{M}_{\alpha,\beta} $$
>3. **Definiujemy przestrzeń informacyjną $(F_q)^k$:**
  > $$ F_q = \{0, 1, \dots, q-1\} \implies (F_q)^k $$
>4. **Obliczamy pojemność kodu $C$:**
  > $$ |C| = q^k $$
>5. **Szukamy słów kodowych kodu $C$:**
  > - Dla macierzy generującej $2 \times \beta$ $$\alpha = 2 \implies \begin{cases} c_1 \\ \mathbf{c}_2 \\ \mathbf{c}_1 +_q \mathbf{c}_2 \\ \mathbf{0} \end{cases}$$
   >- Dla pozostałych kodów wyznaczamy wszystkie możliwe kombinacje wektorów $\mathbf{c}_i$, ilość utworzonych wektorów zawsze wynosi $|C|$.
>6. **Wyznaczamy wagi Hamminga dla niezerowych słów kodowych $\mathbf{c}_i \in C$:**
  > - $w_H(\mathbf{c}_1)$
   >- $w_H(\mathbf{c}_2)$
   >- $w_H(\mathbf{c}_1 +_q \mathbf{c}_2)$
>7. **Wyznaczamy minimalną odległość kodową $d(C)$:**
  > $$ d(C) = \min \{w_H(\mathbf{c}_i) : \mathbf{c}_i \in C \land \mathbf{c}_i \ne 0\} $$
>8. **Wyznaczamy zdolność detekcyjną $s$ kodu $C$:**
  > $$ s = d(C) - 1 $$
>9. **Wyznaczamy zdolność korekcyjną $t$ kodu $C$:**
  > $$ t = \left\lfloor \frac{d(C) - 1}{2} \right\rfloor $$
>10. **Kodowanie:** Komunikat $\mathbf{m} \in (F_q)^k$ kodujemy w słowo kodowe $\mathbf{c} \in C$:
  > $$ \mathbf{c} = \mathbf{m} \cdot_q \mathbf{G} $$
>11. **Wyznaczamy macierz kontrolną $\mathbf{H}$:**
  >  $$ \mathbf{G} = [\mathbf{I}_k \mid \mathbf{A}] \implies \mathbf{H} = [-_q \mathbf{A}^T \mid \mathbf{I}_{n-k}] $$

>[!example] Przykład 1
>12. **Dane:**
   >- $\mathbf{m} = 01$
  > - Macierz generująca $\mathbf{G} = \begin{bmatrix} 1 & 0 & 1 & 0 & 0 \\ 0 & 1 & 1 & 1 & 0 \end{bmatrix} \in \mathbb{M}_{2,5}(F_2)$
>1. **Wyznaczamy długość $n$ kodu $C$:**
  > $$ n = 5 $$
>2. **Wyznaczamy wymiar $k$ kodu $C$:**
  > $$ k = 2 $$
>3. **Definiujemy przestrzeń informacyjną $(F_q)^k$:**
  > $$ (F_2)^2 = \{00, 01, 10, 11\} $$
>4. **Obliczamy pojemność kodu $C$:**
  > $$ |C| = 2^2 = 4 $$
>5. **Szukamy słów kodowych kodu $C$:**
  > $$ \begin{cases} \mathbf{c}_1 = (1, 0, 1, 0, 0) \\ \mathbf{c}_2 = (0, 1, 1, 1, 0) \\ \mathbf{c}_1 +_2 \mathbf{c}_2 = (1, 1, 0, 1, 0) \\ \mathbf{0} = (0, 0, 0, 0, 0) \end{cases} $$
>6. **Wyznaczamy wagi Hamminga dla niezerowych słów kodowych:**
  > - $w_H(10100) = 2$
   >- $w_H(01110) = 3$
   >- $w_H(11010) = 3$
>7. **Wyznaczamy minimalną odległość kodową $d(C)$:**
  > $$ d(C) = \min\{2, 3, 3\} = 2 $$
>8. **Wyznaczamy zdolność detekcyjną $s$ kodu $C$:**
  > $$ s = d(C) - 1 = 2 - 1 = 1 $$
>9. **Wyznaczamy zdolność korekcyjną $t$ kodu $C$:**
   $$ t = \left\lfloor \frac{d(C) - 1}{2} \right\rfloor = \left\lfloor \frac{2 - 1}{2} \right\rfloor = \left\lfloor \frac{1}{2} \right\rfloor = 0 $$
>10. **Kodowanie:**
  > $$ \mathbf{c} = \begin{bmatrix} 0 & 1 \end{bmatrix} \cdot_2 \begin{bmatrix} 1 & 0 & 1 & 0 & 0 \\ 0 & 1 & 1 & 1 & 0 \end{bmatrix} = \begin{bmatrix} 0 & 1 & 1 & 1 & 0 \end{bmatrix} $$
>11. **Wyznaczamy macierz kontrolną $\mathbf{H}$:**
  > $$ \mathbf{G} = \begin{bmatrix} 1 & 0 & 1 & 0 & 0 \\ 0 & 1 & 1 & 1 & 0 \end{bmatrix} \implies \mathbf{A} = \begin{bmatrix} 1 & 0 & 0 \\ 1 & 1 & 0 \end{bmatrix} $$
> $$ -_2 \mathbf{A}^T = -_2 \begin{bmatrix} 1 & 0 & 0 \\ 1 & 1 & 0 \end{bmatrix}^T = \begin{bmatrix} 1 & 1 \\ 0 & 1 \\ 0 & 0 \end{bmatrix} $$
   > $$ \mathbf{H} = [-_2 \mathbf{A}^T \mid \mathbf{I}_{n-k}] = \begin{bmatrix} 1 & 1 & 1 & 0 & 0 \\ 0 & 1 & 0 & 1 & 0 \\ 0 & 0 & 0 & 0 & 1 \end{bmatrix} $$

>[!example] Przykład 2
> 12. **Dane:**
   >- $\mathbf{m} = 11$
   >- Macierz generująca $\mathbf{G} = \begin{bmatrix} 1 & 0 & 1 & 0 & 1 \\ 0 & 1 & 0 & 1 & 1 \end{bmatrix} \in \mathbb{M}_{2,5}(F_2)$
>1. **Wyznaczamy długość $n$ kodu $C$:**
 > $$ n = 5 $$
> 2. **Wyznaczamy wymiar $k$ kodu $C$:**
   $$ k = 2 $$
>3. **Definiujemy przestrzeń informacyjną $(F_q)^k$:**
>   $$ (F_2)^2 = \{00, 01, 10, 11\} $$
>4. **Obliczamy pojemność kodu $C$:**
  > $$ |C| = 2^2 = 4 $$
>5. **Szukamy słów kodowych kodu $C$:**
  > $$ \begin{cases} \mathbf{c}_1 = (1, 0, 1, 0, 1) \\ \mathbf{c}_2 = (0, 1, 0, 1, 1) \\ \mathbf{c}_1 +_2 \mathbf{c}_2 = (1, 1, 1, 1, 0) \\ \mathbf{0} = (0, 0, 0, 0, 0) \end{cases} $$
>6. **Wyznaczamy wagi Hamminga dla niezerowych słów kodowych:**
  > - $w_H(10101) = 3$
   >- $w_H(01011) = 3$
   >- $w_H(11110) = 4$
>7. **Wyznaczamy minimalną odległość kodową $d(C)$:**
  > $$ d(C) = \min\{3, 3, 4\} = 3 $$
> 8. **Wyznaczamy zdolność detekcyjną $s$ kodu $C$:**
  > $$ s = d(C) - 1 = 3 - 1 = 2 $$
>9. **Wyznaczamy zdolność korekcyjną $t$ kodu $C$:**
  > $$ t = \left\lfloor \frac{d(C) - 1}{2} \right\rfloor = \left\lfloor \frac{3 - 1}{2} \right\rfloor = \left\lfloor \frac{2}{2} \right\rfloor = 1 $$
>10. **Kodowanie:**
  > $$ \mathbf{c} = \begin{bmatrix} 1 & 1 \end{bmatrix} \cdot_2 \begin{bmatrix} 1 & 0 & 1 & 0 & 1 \\ 0 & 1 & 0 & 1 & 1 \end{bmatrix} = \begin{bmatrix} 1 & 1 & 1 & 1 & 0 \end{bmatrix} $$
>11. **Wyznaczamy macierz kontrolną $\mathbf{H}$:**
  > $$ \mathbf{G} = \begin{bmatrix} 1 & 0 & 1 & 0 & 1 \\ 0 & 1 & 0 & 1 & 1 \end{bmatrix} \implies \mathbf{A} = \begin{bmatrix} 1 & 0 & 1 \\ 0 & 1 & 1 \end{bmatrix} $$
>$$ -_2 \mathbf{A}^T = -_2 \begin{bmatrix} 1 & 0 & 1 \\ 0 & 1 & 1 \end{bmatrix}^T = \begin{bmatrix} 1 & 0 \\ 0 & 1 \\ 1 & 1 \end{bmatrix} $$
  > $$ \mathbf{H} = [-_2 \mathbf{A}^T \mid \mathbf{I}_{n-k}] = \begin{bmatrix} 1 & 0 & 1 & 0 & 0 \\ 0 & 1 & 0 & 1 & 0 \\ 1 & 1 & 0 & 0 & 1 \end{bmatrix} $$

>[!example] Przykład 3
>12. **Dane:**
>   - $\mathbf{m} = 00$
  > - Macierz generująca $\mathbf{G} = \begin{bmatrix} 1 & 0 & 1 & 1 & 1 \\ 0 & 1 & 0 & 0 & 0 \end{bmatrix} \in \mathbb{M}_{2,5}(F_2)$
>1. **Wyznaczamy długość $n$ kodu $C$:**
  > $$ n = 5 $$
>2. **Wyznaczamy wymiar $k$ kodu $C$:**
  > $$ k = 2 $$
>3. **Definiujemy przestrzeń informacyjną $(F_q)^k$:**
  > $$ (F_2)^2 = \{00, 01, 10, 11\} $$
>4. **Obliczamy pojemność kodu $C$:**
  > $$ |C| = 2^2 = 4 $$
>5. **Szukamy słów kodowych kodu $C$:**
  > $$ \begin{cases} \mathbf{c}_1 = (1, 0, 1, 1, 1) \\ \mathbf{c}_2 = (0, 1, 0, 0, 0) \\ \mathbf{c}_1 +_2 \mathbf{c}_2 = (1, 1, 1, 1, 1) \\ \mathbf{0} = (0, 0, 0, 0, 0) \end{cases} $$
>6. **Wyznaczamy wagi Hamminga dla niezerowych słów kodowych:**
  > - $w_H(10111) = 4$
   >- $w_H(01000) = 1$
   >- $w_H(11111) = 5$
>7. **Wyznaczamy minimalną odległość kodową $d(C)$:**
  > $$ d(C) = \min\{4, 1, 5\} = 1 $$
>8. **Wyznaczamy zdolność detekcyjną $s$ kodu $C$:**
  > $$ s = d(C) - 1 = 1 - 1 = 0 $$
>9. **Wyznaczamy zdolność korekcyjną $t$ kodu $C$:**
  > $$ t = \left\lfloor \frac{d(C) - 1}{2} \right\rfloor = \left\lfloor \frac{1 - 1}{2} \right\rfloor = \left\lfloor \frac{0}{2} \right\rfloor = 0 $$
>10. **Kodowanie:**
  > $$ \mathbf{c} = \begin{bmatrix} 0 & 0 \end{bmatrix} \cdot_2 \begin{bmatrix} 1 & 0 & 1 & 1 & 1 \\ 0 & 1 & 0 & 0 & 0 \end{bmatrix} = \begin{bmatrix} 0 & 0 & 0 & 0 & 0 \end{bmatrix} $$
>11. **Wyznaczamy macierz kontrolną $\mathbf{H}$:**
  > $$ \mathbf{G} = \begin{bmatrix} 1 & 0 & 1 & 1 & 1 \\ 0 & 1 & 0 & 0 & 0 \end{bmatrix} \implies \mathbf{A} = \begin{bmatrix} 1 & 1 & 1 \\ 0 & 0 & 0 \end{bmatrix} $$
> $$ -_2 \mathbf{A}^T = -_2 \begin{bmatrix} 1 & 1 & 1 \\ 0 & 0 & 0 \end{bmatrix}^T = \begin{bmatrix} 1 & 0 \\ 1 & 0 \\ 1 & 0 \end{bmatrix} $$
  > $$ \mathbf{H} = [-_2 \mathbf{A}^T \mid \mathbf{I}_{n-k}] = \begin{bmatrix} 1 & 0 & 1 & 0 & 0 \\ 1 & 0 & 0 & 1 & 0 \\ 1 & 0 & 0 & 0 & 1 \end{bmatrix} $$

>[!example] Przykład 4
>0. **Dane:**
  > - $\mathbf{m} = 11$
   >- Macierz generująca $\mathbf{G} = \begin{bmatrix} 1 & 0 & 1 & 2 & 0 \\ 0 & 1 & 1 & 0 & 2 \end{bmatrix} \in \mathbb{M}_{2,5}(F_3)$
>1. **Wyznaczamy długość $n$ kodu $C$:**
  > $$ n = 5 $$
>2. **Wyznaczamy wymiar $k$ kodu $C$:**
  > $$ k = 2 $$
>3. **Definiujemy przestrzeń informacyjną $(F_q)^k$:**
  > $$ (F_3)^2 = \{00, 01, 02, 10, 11, 12, 20, 21, 22\} $$
>4. **Obliczamy pojemność kodu $C$:**
  > $$ |C| = 3^2 = 9 $$
>5. **Szukamy słów kodowych kodu $C$:**
  > - $\mathbf{c}_1 = (1, 0, 1, 2, 0)$
   >- $\mathbf{c}_2 = (0, 1, 1, 0, 2)$
   >- $\mathbf{c}_1 +_3 \mathbf{c}_2 = (1, 1, 2, 2, 2)$
   >- $\mathbf{c}_1 +_3 \mathbf{c}_1 = (2, 0, 2, 1, 0)$
   >- $\mathbf{c}_2 +_3 \mathbf{c}_2 = (0, 2, 2, 0, 1)$
   >- $\mathbf{c}_1 +_3 \mathbf{c}_1 +_3 \mathbf{c}_2 = (2, 1, 0, 1, 2)$
   >- $\mathbf{c}_1 +_3 \mathbf{c}_2 +_3 \mathbf{c}_2 = (1, 2, 0, 2, 1)$
   >- $\mathbf{c}_1 +_3 \mathbf{c}_1 +_3 \mathbf{c}_2 +_3 \mathbf{c}_2 = (2, 2, 1, 1, 1)$
   >- $\mathbf{0} = (0, 0, 0, 0, 0)$
>6. **Wyznaczamy wagi Hamminga dla niezerowych słów kodowych:**
  > - $w_H(10120) = 3$
   >- $w_H(01102) = 3$
   >- $w_H(11222) = 5$
   >- $w_H(20210) = 3$
   >- $w_H(02201) = 3$
   >- $w_H(21012) = 4$
   >- $w_H(12021) = 4$
   >- $w_H(22111) = 5$
>7. **Wyznaczamy minimalną odległość kodową $d(C)$:**
  > $$ d(C) = \min\{3, 3, 5, 3, 3, 4, 4, 5\} = 3 $$
>8. **Wyznaczamy zdolność detekcyjną $s$ kodu $C$:**
  > $$ s = d(C) - 1 = 3 - 1 = 2 $$
>9. **Wyznaczamy zdolność korekcyjną $t$ kodu $C$:**
  > $$ t = \left\lfloor \frac{d(C) - 1}{2} \right\rfloor = \left\lfloor \frac{3 - 1}{2} \right\rfloor = \left\lfloor \frac{2}{2} \right\rfloor = 1 $$
>10. **Kodowanie:**
  > $$ \mathbf{c} = \begin{bmatrix} 1 & 1 \end{bmatrix} \cdot_3 \begin{bmatrix} 1 & 0 & 1 & 2 & 0 \\ 0 & 1 & 1 & 0 & 2 \end{bmatrix} $$
>11. **Wyznaczamy macierz kontrolną $\mathbf{H}$:**
  > $$ \mathbf{G} = \begin{bmatrix} 1 & 0 & 1 & 2 & 0 \\ 0 & 1 & 1 & 0 & 2 \end{bmatrix} \implies \mathbf{A} = \begin{bmatrix} 1 & 2 & 0 \\ 1 & 0 & 2 \end{bmatrix} $$
>$$ -_3 \mathbf{A}^T = -_3 \begin{bmatrix} 1 & 2 & 0 \\ 1 & 0 & 2 \end{bmatrix}^T = \begin{bmatrix} 2 & 1 & 0 \\ 2 & 0 & 1 \end{bmatrix} $$
  > $$ \mathbf{H} = [-_3 \mathbf{A}^T \mid \mathbf{I}_{n-k}] = \begin{bmatrix} 2 & 2 & 1 & 0 & 0 \\ 1 & 0 & 0 & 1 & 0 \\ 0 & 1 & 0 & 0 & 1 \end{bmatrix} $$
  