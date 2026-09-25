## Wektory
Wektor to uporządkowana lista liczb reprezentująca punkt, kierunek bądź element przestrzeni wektorowej. W fizyce wektory oznaczamy strzałką nad zmienną, w matematyce ta strzałka jest często pomijana na rzecz pogrubionej czcionki bez kursywy $\vec{v} = \mathbf{v}$, jednak dla przejrzystości można ją stosować. Wektor $\mathbf{v} = (a_1, \dots, a_n)$ reprezentuje kierunek w $n$-wymiarowej przestrzeni.

### Podstawowe operacje na wektorach:
* **Dodawanie i odejmowanie wektorów:**

$$\mathbf{a} \pm \mathbf{b} = (a_1 \pm b_1, a_2 \pm b_2, \dots, a_n \pm b_n)$$

* **Mnożenie wektora przez skalar:**

$$\alpha \cdot \mathbf{a} = (\alpha a_1, \alpha a_2, \dots, \alpha a_n)$$

* **Norma wektora:**

$$\|\mathbf{a}\| = \sqrt{a_1^2 + a_2^2 + \dots + a_n^2}$$

* **Iloczyn skalarny:**

$$\mathbf{a} \cdot \mathbf{b} = (a_1 b_1, a_2 b_2, \dots, a_n b_n)$$

* **Iloczyn wektorowy (tylko w $\mathbb{R}^3$):**

$$\mathbf{a} \times \mathbf{b} = (a_2 b_3 - a_3 b_2, a_3 b_1 - a_1 b_3, a_1 b_2 - a_2 b_1)$$

## Wektor zerowy
Wektor zerowy jest odpowiednikiem macierzy zerowej dla wektorów. Oznaczamy go jako $\mathbf{0}$ lub $\mathbf{\vec{0}}$. Dla każdej przestrzeni $\mathbb{R}^n$ zachodzi $\mathbf{\vec{0}} = (0, \dots, 0)$. Wektor ten jest elementem neutralnym dodawania wektorów.

## Przestrzeń wektorowa
Przestrzeń wektorowa, nazywana również przestrzenią liniową, oznaczana jest symbolem $V$. Przestrzenie tworzone są nad ciałem $F$ (zazwyczaj $F = \mathbb{R}$ lub $F=\mathbb{C}$). Elementy ciała $F$ nazywamy skalarami.

Przestrzeń $V$ jest zbiorem wektorów, dla których zdefiniowane są dwie operacje:
* Dodawanie wektorów: $\mathbf{a} + \mathbf{b} = (a_1 + b_1, \dots, a_n + b_n)$.
* Mnożenie wektora przez skalar: $\alpha \cdot \mathbf{a} = (\alpha a_1, \dots, \alpha a_n)$.

Zapis $F^n$ oznacza przestrzeń $n$-wymiarową nad ciałem $F$.

## Podprzestrzenie
Jeżeli niepusta przestrzeń $U$ jest częścią przestrzeni wektorowej $V$, to mówimy, że $U$ jest podprzestrzenią $V$ i zapisujemy jako $U < V$. Aby $U < V$, spełnione muszą być trzy warunki:

$$\forall_{\mathbf{u}, \mathbf{v} \in U} : \mathbf{u} + \mathbf{v} \in U$$

$$\forall_{\mathbf{u} \in U, \alpha \in F} : \alpha \mathbf{u} \in U$$

$$0 \in U$$

Najmniejszą możliwą podprzestrzenią jest $U = \{0\}$. Jeżeli $U, W < V$, to zarówno $U \cap W < V$, jak i $U + W < V$.

### Suma prosta
Przestrzeń $V$ nazywamy sumą prostą podprzestrzeni $U$ i $W$, jeżeli spełnione są następujące warunki:

$$V = U + W$$

$$U \cap W = \{0\}$$

Jeżeli $V$ jest sumą prostą $U$ i $W$, zapisujemy to jako $V = U \oplus W$.

## Wektor własny i przestrzeń własna
Wektor własny macierzy $\mathbf{A}$ to taki niezerowy wektor $\mathbf{v}$, że:

$$\mathbf{A}\mathbf{v} = \lambda \mathbf{v}$$

Gdzie $\lambda$ jest wartością własną macierzy, obliczaną ze wzoru:

$$\det(\mathbf{A} - \lambda \mathbf{I}) = 0$$

Na logikę można wyobrazić sobie to tak, że wektor własny macierzy $\mathbf{A}$ to taki wektor, którego przekształcenie $\mathbf{A} \cdot \mathbf{v}$ zmieni tylko długość (i zwrot), nie zmieni się natomiast jego kierunek. Wektor własny obliczamy ze wzoru:

$$(\mathbf{A} - \lambda_i \mathbf{I})\mathbf{v} = 0$$

Jeżeli $\lambda$ jest wartością własną macierzy $\mathbf{A}$, to zbiór wszystkich wektorów własnych odpowiadających tej wartości własnej wraz z wektorem zerowym $\mathbf{x} = (0, \dots, 0)$ nazywamy **przestrzenią własną** $V_\lambda$ macierzy $\mathbf{A}$:

$$V_\lambda = \{\mathbf{x} \in F^n : (\mathbf{A} - \lambda \mathbf{I})\mathbf{x} = 0\}$$

Przestrzeń własna $V_\lambda$ jest podprzestrzenią przestrzeni $F^n$. Jej wymiar jest większy od 0 i nie przekracza krotności pierwiastka charakterystycznego $\lambda$.

## Kombinacja liniowa wektorów
Dane są wektory $\mathbf{v}_1, \dots, \mathbf{v}_n$. Wektor $\mathbf{v} = \alpha_1 \mathbf{v}_1 + \dots + \alpha_n \mathbf{v}_n$ nazywamy liniową kombinacją wektorów $\mathbf{v}_1, \dots, \mathbf{v}_n$. Zbiór wszystkich liniowych kombinacji wektorów $\mathbf{v}_1, \dots, \mathbf{v}_n$ będziemy oznaczać jako $\operatorname{Lin}(\mathbf{v}_1, \dots, \mathbf{v}_n)$ (stosuje się również zapis $\operatorname{span}$ zamiast $\operatorname{Lin}$):

$$\operatorname{Lin}(\mathbf{v}_1, \dots, \mathbf{v}_n) = \{\alpha_1 \mathbf{v}_1 + \dots + \alpha_n \mathbf{v}_n : \forall_n \alpha_n \in F \land \mathbf{v}_n \in F\}$$

Zbiór $\operatorname{Lin}(X)$ jest najmniejszą podprzestrzenią przestrzeni $V$ zawierającą zbiór $X$. Podprzestrzeń tę nazywamy **powłoką liniową** zbioru $X$ bądź podprzestrzenią rozpiętą na zbiorze $X$, a sam zbiór $X$ nazywamy **zbiorem generatorów** przestrzeni $\operatorname{Lin}(X)$.

## Zależność liniowa
Powiemy, że wektory $\mathbf{v}_1, \dots, \mathbf{v}_n$ są **liniowo zależne**, jeżeli istnieją skalary $\alpha_1, \dots, \alpha_n$, z których przynajmniej jeden jest niezerowy, oraz:

$$\alpha_1 \mathbf{v}_1 + \dots + \alpha_n \mathbf{v}_n = \mathbf{\vec{0}}$$

Jeżeli jedynym rozwiązaniem tego równania jest $\alpha_1 = \alpha_2 = \dots = \alpha_n = 0$, to powiemy, że wektory te są **liniowo niezależne**.

W przestrzeni $V = F^n$ może istnieć maksymalnie $n$ wektorów liniowo niezależnych. Wszystkie inne są nadmiarowe, ponieważ każdy kierunek w $n$-wymiarowej przestrzeni możemy opisać za pomocą $n$ niezależnych kierunków.

## Baza przestrzeni
Zbiór liniowo niezależnych wektorów, który generuje całą przestrzeń $V$, nazywamy **bazą** przestrzeni $V$ i oznaczamy jako $\mathcal{B}$. Zbiór $\mathcal{B} = \{\mathbf{b}_1, \dots, \mathbf{b}_n\} \subset V$ jest bazą, jeżeli:
* $\operatorname{Lin}(\mathcal{B}) = V$
* $\mathbf{b}_1, \dots, \mathbf{b}_n$ są liniowo niezależne

Gdzie $n = \dim V$. Jeżeli $\mathcal{B}$ jest bazą $V$, to każdy wektor $\mathbf{v} \in V$ można zapisać jako kombinację liniową wektorów bazowych:

$$\mathbf{v} = \alpha_1 \mathbf{b}_1 + \dots + \alpha_n \mathbf{b}_n$$

Wtedy skalary $\alpha_i$ nazywamy współrzędnymi $\mathbf{v}$ względem bazy $\mathcal{B}$ i oznaczamy jako $\mathbf{v} = (\alpha_1, \dots, \alpha_n)_\mathcal{B}$. Jeśli $\mathcal{B}$ i $\mathcal{C}$ są bazami przestrzeni $V$, to $|\mathcal{B}| = |\mathcal{C}| = \dim V$.

Dla każdej przestrzeni $F^n$ możemy zdefiniować bazę kanoniczną (standardową) $\mathcal{E} = (\mathbf{e}_1, \dots, \mathbf{e}_n)$, gdzie:
* $\mathbf{e}_1 = (1, 0, \dots, 0)$
* $\mathbf{e}_2 = (0, 1, \dots, 0)$
* $\mathbf{e}_n = (0, 0, \dots, 1)$

## Twierdzenie Steinitza o wymianie
W przestrzeni $F^n$ istnieje prosty sposób sprawdzenia, czy zbiór wektorów jest liniowo niezależny. Dane są wektory $\mathbf{a}_1, \dots, \mathbf{a}_m$. Tworzymy z nich macierz $\mathbf{A} = [\mathbf{a}_1 \mid \dots \mid \mathbf{a}_m]$. Zbiór $\{\mathbf{a}_1, \dots, \mathbf{a}_m\}$ jest liniowo niezależny wtedy i tylko wtedy, gdy $\operatorname{rank}(\mathbf{A}) = m$. Jeżeli ponadto $n = m$, to zbiór ten stanowi bazę przestrzeni $F^n$.

>[!danger] Twierdzenie Steinitza
>Jeśli $\mathcal{B} = \{\mathbf{b}_1, \dots, \mathbf{b}_n\}$ jest bazą przestrzeni $V$, a wektory $\mathbf{v}_1, \dots, \mathbf{v}_m$ są liniowo niezależne, to:
> * $m \le n$
> * $m = n \implies \{\mathbf{v}_1, \dots, \mathbf{v}_m\}$ jest bazą przestrzeni $V$
> * $m < n \implies \exists_{\mathbf{v}_{m+1}, \dots, \mathbf{v}_n} : \{\mathbf{v}_1, \dots, \mathbf{v}_m\} \cup \{\mathbf{v}_{m+1}, \dots, \mathbf{v}_n\}$ jest bazą przestrzeni $V$

## Wymiar przestrzeni
Wymiarem przestrzeni $V$ nad ciałem $F$ nazywamy liczbę elementów dowolnej bazy tej przestrzeni i zapisujemy jako $\dim V$. Prawdziwa jest równość:

$$\dim V = n - r(\mathbf{A} - \lambda \mathbf{I})$$

Jeśli $U, W < V$, to:

$$\dim(U + W) = \dim U + \dim W - \dim(U \cap W)$$

Dla wielomianu charakterystycznego $w_{\mathbf{A}}(x) = (x - \lambda_1)^{d_1} + \dots + (x - \lambda_n)^{d_n}$, macierz $\mathbf{A}$ jest diagonalizowalna wtedy i tylko wtedy, gdy:

$$\dim V_{\lambda_i} = n - r(\mathbf{A} - \lambda_i \mathbf{I}) = d_i \quad \text{dla } i \in \{1, \dots, n\}$$

Z tego wynika, że jeśli $w_{\mathbf{A}}(x)$ ma dokładnie $n$ różnych pierwiastków, to macierz $\mathbf{A}$ jest diagonalizowalna.

## Macierz zmiany bazy
Jeżeli $\mathcal{B} = \{\mathbf{b}_1, \dots, \mathbf{b}_n\}$ i $\mathcal{C} = \{\mathbf{c}_1, \dots, \mathbf{c}_n\}$ są bazami przestrzeni $V$, to dowolny wektor $\mathbf{b}_i$ możemy wyrazić jako kombinację liniową wektorów $\mathbf{c}_i$:

$$\mathbf{b}_1 = p_{11}\mathbf{c}_1 + \dots + p_{n1}\mathbf{c}_n$$

$$\mathbf{b}_2 = p_{12}\mathbf{c}_1 + \dots + p_{n2}\mathbf{c}_n$$

$$\mathbf{b}_n = p_{1n}\mathbf{c}_1 + \dots + p_{nn}\mathbf{c}_n$$

Macierz utworzoną ze skalarów $p_{ij}$ nazywamy **macierzą przejścia** od bazy $\mathcal{C}$ do bazy $\mathcal{B}$ (lub macierzą zmiany bazy) i oznaczamy jako $\mathbf{P}_{\mathcal{C} \leftarrow \mathcal{B}}$ lub po prostu $\mathbf{P}$:

$$\mathbf{P} = \begin{bmatrix} p_{11} & \dots & p_{1n} \\ \vdots & \ddots & \vdots \\ p_{n1} & \dots & p_{nn} \end{bmatrix}$$

W podobny sposób możemy wyrazić wektory $\mathbf{c}_i$ za pomocą kombinacji liniowej wektorów $\mathbf{b}_i$. Wtedy macierz $\mathbf{Q} = [q_{ij}]_{n \times n}$ jest macierzą odwrotną do $\mathbf{P}$, więc $\mathbf{Q}\mathbf{P} = \mathbf{P}\mathbf{Q} = \mathbf{I}$. Macierzy przejścia $\mathbf{P}$ możemy używać do zamiany współrzędnych wektorów zapisanych w bazie $\mathcal{C}$ na współrzędne względem bazy $\mathcal{B}$:
Jeśli $\mathbf{v} = \alpha_1 \mathbf{c}_1 + \dots + \alpha_n \mathbf{c}_n = \beta_1 \mathbf{b}_1 + \dots + \beta_n \mathbf{b}_n$, to:

$$\begin{bmatrix} \alpha_1 \\ \vdots \\ \alpha_n \end{bmatrix} = \mathbf{P} \begin{bmatrix} \beta_1 \\ \vdots \\ \beta_n \end{bmatrix} \implies \begin{bmatrix} \beta_1 \\ \vdots \\ \beta_n \end{bmatrix} = \mathbf{Q} \begin{bmatrix} \alpha_1 \\ \vdots \\ \alpha_n \end{bmatrix}$$

