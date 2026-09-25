## Ślad macierzy
Ślad macierzy występuje tylko w przypadku macierzy kwadratowych. Śladem macierzy nazywamy sumę wszystkich elementów na jej głównej przekątnej i zapisujemy jako $\mathrm{tr} \mathbf{A}$:

$$\mathrm{tr} \mathbf{A}_{n \times n} = \sum_{i=1}^{n} a_{ii} = a_{11} + a_{22} + \dots + a_{nn}$$

**Własności śladu macierzy:**

$$\mathrm{tr} \mathbf{A} + \mathrm{tr} \mathbf{B} = \mathrm{tr}(\mathbf{A} + \mathbf{B})$$

$$\mathrm{tr}(c\mathbf{A}) = c \mathrm{tr} \mathbf{A}$$

$$\mathrm{tr} \mathbf{A} = \lambda_1 + \dots + \lambda_n$$

## Wektor
Wektor to uporządkowana lista liczb reprezentująca punkt, kierunek bądź element przestrzeni wektorowej. W fizyce wektory oznaczamy strzałką nad zmienną, w matematyce ta strzałka jest często pomijana, jednak dla przejrzystości można ją stosować.

Wektor $\mathbf{v} = (a_1, \dots, a_n)$ reprezentuje kierunek w $n$-wymiarowej przestrzeni. Wektor możemy zapisać w postaci macierzy kolumnowej:

$$\mathbf{v} = \begin{bmatrix} a_1 \\ \vdots \\ a_n \end{bmatrix}$$

Pozwala to na wykonywanie operacji na macierzach poprzez mnożenie jej prawostronnie przez wektor: $\mathbf{A}\mathbf{v}$.

## Wartości i wektory własne
Dla macierzy kwadratowej $\mathbf{A}$, niezerowy wektor $\mathbf{v} = (x_1, x_2, \dots, x_n) \in F$ nazywamy **wektorem własnym** macierzy, jeżeli istnieje taki skalar $\lambda$, że:

$$\mathbf{A} \begin{bmatrix} x_1 \\ \vdots \\ x_n \end{bmatrix} = \lambda \begin{bmatrix} x_1 \\ \vdots \\ x_n \end{bmatrix}$$

Każdy skalar $\lambda$, dla którego prawdziwe jest powyższe równanie, nazywamy **wartością własną** macierzy $\mathbf{A}$. Macierz stopnia $n$ ma nie więcej niż $n$ różnych wartości własnych.

## Wielomiany charakterystyczne
Chcąc uporządkować powyższe równanie, musimy pomnożyć $\lambda$ przez macierz jednostkową $\mathbf{I}$, ponieważ nie możemy odjąć skalara od macierzy $\mathbf{A}$. Po wymnożeniu macierz $\lambda \mathbf{I}$ będzie macierzą diagonalną o współczynnikach $\lambda$. Teraz możemy uporządkować równanie i przerzucić wszystkie elementy na jedną stronę:

$$\mathbf{A} \begin{bmatrix} x_1 \\ \vdots \\ x_n \end{bmatrix} - \lambda \mathbf{I} \begin{bmatrix} x_1 \\ \vdots \\ x_n \end{bmatrix} = 0 \implies (\mathbf{A} - \lambda \mathbf{I}) \begin{bmatrix} x_1 \\ \vdots \\ x_n \end{bmatrix} = 0 \implies (\mathbf{A} - \lambda \mathbf{I})\mathbf{v} = 0$$

Żeby równanie $(\mathbf{A} - \lambda \mathbf{I})\mathbf{v} = 0$ miało niezerowe rozwiązanie (ponieważ z definicji wektory własne są niezerowe), macierz $(\mathbf{A} - \lambda \mathbf{I})$ musi być osobliwa, czyli:

$$\det(\mathbf{A} - \lambda \mathbf{I}) = 0$$

Równanie to nazywamy **równaniem charakterystycznym**. Po zdefiniowaniu funkcji:

$$w_{\mathbf{A}}(x) = \det(\mathbf{A} - x\mathbf{I})$$

otrzymujemy wielomian charakterystyczny macierzy $\mathbf{A}$.

Skalar $\lambda$ jest wartością własną macierzy $\mathbf{A}$ wtedy i tylko wtedy, gdy $\lambda$ jest pierwiastkiem wielomianu charakterystycznego macierzy $\mathbf{A}$, czyli gdy $\det(\mathbf{A} - x\mathbf{I}) = 0 \implies x = \lambda$.

> [!example] Przykład dla macierzy $2 \times 2$
> Niech $\mathbf{A} = \begin{bmatrix} a & b \\ c & d \end{bmatrix}$.
>
> $$w_{\mathbf{A}}(x) = \det(\mathbf{A} - x\mathbf{I}) = \det\begin{bmatrix} a - x & b \\ c & d - x \end{bmatrix} = (a - x)(d - x) - bc = x^2 - (a + d)x + ad - bc$$
>
> Z przykładu tego wynika, że dla macierzy stopnia $2 \times 2$ prawdziwe jest równanie:
>
> $$w_{\mathbf{A}}(x) = x^2 - \mathrm{tr}(\mathbf{A}) \cdot x + \det \mathbf{A}$$
>

>[!danger] Twierdzenie Hamiltona - Cayleya
> Jeśli $w_{\mathbf{A}}(x)$ jest wielomianem charakterystycznym macierzy $\mathbf{A}$, to:
>
> $$w_{\mathbf{A}}(\mathbf{A}) = 0$$
>

## Macierze podobne
Macierze $\mathbf{A}$ i $\mathbf{B}$ nazywamy **podobnymi**, gdy istnieje macierz odwracalna $\mathbf{P}$ taka, że:

$$\mathbf{B} = \mathbf{P}^{-1}\mathbf{A}\mathbf{P}$$

Macierze podobne mają identyczne wielomiany charakterystyczne: $w_{\mathbf{A}}(x) = w_{\mathbf{B}}(x)$. Jeżeli macierze $\mathbf{A}$ i $\mathbf{B}$ są podobne, zapisujemy to jako $\mathbf{A} \sim \mathbf{B}$.

## Macierze diagonalizowalne
Macierzą diagonalizowalną nazywamy taką macierz $\mathbf{A}$, która posiada macierz podobną $\mathbf{B}$ będącą macierzą diagonalną. Macierz $\mathbf{B}$ nazywamy **postacią diagonalną** macierzy $\mathbf{A}$:

$$\exists_{\mathbf{P}} \quad \mathbf{B} = \mathbf{P}^{-1}\mathbf{A}\mathbf{P}$$

$$\mathbf{B} = \mathrm{diag}(b_{11}, \dots, b_{nn})$$

Jeżeli $\mathbf{B} = \mathrm{diag}(b_1, \dots, b_n)$ jest postacią diagonalną macierzy $\mathbf{A}$, to:

$$w_{\mathbf{A}}(x) = w_{\mathbf{B}}(x) = (x - b_1)(x - b_2) \cdot \dots \cdot (x - b_n) = (x - b_1)^{d_1} \cdot \dots \cdot (x - b_n)^{d_n}$$

Zbiór $\{b_1, \dots, b_n\}$ to zbiór wszystkich wartości własnych macierzy $\mathbf{A}$. Z tego wynika, że wszystkie elementy występujące na przekątnej macierzy $\mathbf{B}$ są wartościami własnymi macierzy $\mathbf{A}$.

Macierz $\mathbf{A}$ jest diagonalizowalna wtedy i tylko wtedy, gdy $n - r(\mathbf{A} - a_i\mathbf{I}) = d_i$ dla $i \in \{1, \dots, n\}$. Jeżeli wektory $\mathbf{v}_i$ są rozwiązaniami układu równań $(\mathbf{A} - x_i\mathbf{I})\mathbf{v} = 0$, to macierz $\mathbf{P} = \begin{bmatrix} \mathbf{v}_1 & \dots & \mathbf{v}_n \end{bmatrix}$ jest macierzą taką, że $\mathbf{P}^{-1}\mathbf{A}\mathbf{P} \sim \mathbf{A}$.

> [!example] Przykład sprawdzenia diagonalizowalności
> Sprawdź czy macierz $\mathbf{A}$ jest diagonalizowalna i wyznacz $\mathbf{P}$ dla:
>
> $$\mathbf{A} = \begin{bmatrix} -1 & -4 & -4 \\ 1 & 4 & 2 \\ 1 & 1 & 3 \end{bmatrix}$$
>
> $$w_{\mathbf{A}}(x) = \det\begin{bmatrix} -1-x & -4 & -4 \\ 1 & 4-x & 2 \\ 1 & 1 & 3-x \end{bmatrix} = -x^3 + 6x^2 - 11x + 6 = (x - 1)(x - 2)(x - 3)$$
>
> **I. Dla $x = 1$:**
>
> $$(\mathbf{A} - 1 \cdot \mathbf{I})\begin{bmatrix} x \\ y \\ z \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \\ 0 \end{bmatrix} \implies \begin{bmatrix} -2 & -4 & -4 \\ 1 & 3 & 2 \\ 1 & 1 & 2 \end{bmatrix} \begin{bmatrix} x \\ y \\ z \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \\ 0 \end{bmatrix}$$
>
> Po przekształceniach Gaussa otrzymujemy:
>
> $$\begin{cases} x + 3y + 2z = 0 \\ 2y = 0 \end{cases} \implies \begin{cases} x = -2\alpha \\ y = 0 \\ z = \alpha \end{cases}$$
>
> Stąd wektor własny: $\mathbf{v}_1 = \begin{bmatrix} -2 \\ 0 \\ 1 \end{bmatrix}$.
> 
> **II. Dla $x = 2$:**
>
> $$(\mathbf{A} - 2 \cdot \mathbf{I})\begin{bmatrix} x \\ y \\ z \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \\ 0 \end{bmatrix} \implies \begin{bmatrix} -3 & -4 & -4 \\ 1 & 2 & 2 \\ 1 & 1 & 1 \end{bmatrix} \begin{bmatrix} x \\ y \\ z \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \\ 0 \end{bmatrix}$$
>
> Po przekształceniach otrzymujemy:
>
> $$\begin{cases} x = 0 \\ y + z = 0 \end{cases} \implies \begin{cases} x = 0 \\ y = -\alpha \\ z = \alpha \end{cases}$$
>
> Stąd wektor własny: $\mathbf{v}_2 = \begin{bmatrix} 0 \\ -1 \\ 1 \end{bmatrix}$.
> 
> **III. Dla $x = 3$:**
>
> $$(\mathbf{A} - 3 \cdot \mathbf{I})\begin{bmatrix} x \\ y \\ z \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \\ 0 \end{bmatrix} \implies \begin{bmatrix} -4 & -4 & -4 \\ 1 & 1 & 2 \\ 1 & 1 & 0 \end{bmatrix} \begin{bmatrix} x \\ y \\ z \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \\ 0 \end{bmatrix}$$
>
> Po przekształceniach otrzymujemy:
>
> $$\begin{cases} x + y = 0 \\ z = 0 \end{cases} \implies \begin{cases} x = -\alpha \\ y = \alpha \\ z = 0 \end{cases}$$
>
> Stąd wektor własny: $\mathbf{v}_3 = \begin{bmatrix} -1 \\ 1 \\ 0 \end{bmatrix}$.
> 
> **Wyznaczenie $\mathbf{P}$ oraz iloczynu:**
>
> $$\mathbf{P}^{-1}\mathbf{A}\mathbf{P} = \mathrm{x_1, x_2, x_3) = \mathrm{diag}(1, 2, 3) = \begin{bmatrix} 1 & 0 & 0 \\ 0 & 2 & 0 \\ 0 & 0 & 3 \end{bmatrix}$$
>
> $$\mathbf{P} = \begin{bmatrix} \mathbf{v}_1 \mid \mathbf{v}_2 \mid \mathbf{v}_3 \end{bmatrix} = \begin{bmatrix} -2 & 0 & -1 \\ 0 & -1 & 1 \\ 1 & 1 & 0 \end{bmatrix}$$
>
> Sprawdzenie macierzowe:
>
> $$\mathbf{A}\mathbf{P} = \mathbf{P} \cdot \mathrm{bmatrix} -2 & 0 & -1 \\ 0 & -1 & 1 \\ 2 & 1 & 0 \end{bmatrix} \cdot \begin{bmatrix} 1 & 0 & 0 \\ 0 & 2 & 0 \\ 0 & 0 & 3 \end{bmatrix} = \begin{bmatrix} -2 & 0 & -3 \\ 0 & -2 & 3 \\ 1 & 2 & 0 \end{bmatrix}$$
>

## Macierz ortogonalna
Macierz ortogonalna jest rodzajem macierzy kwadratowej – jest to taka macierz $\mathbf{A}$, która jest odwrotna do jej transpozycji:

$$\mathbf{A}^T \cdot \mathbf{A} = \mathbf{I} \implies \mathbf{A}^T = \mathbf{A}^{-1}$$

> [!example] Przykład macierzy ortogonalnej
> $$\mathbf{A} = \begin{bmatrix} \cos \alpha & \sin \alpha \\ -\sin \alpha & \cos \alpha \end{bmatrix}$$
>
