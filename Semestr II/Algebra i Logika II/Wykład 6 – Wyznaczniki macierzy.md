## Wyznacznik macierzy
Wyznacznik macierzy istnieje tylko w przypadku macierzy kwadratowych i informuje o tym, czy dana macierz jest odwracalna. Wyznacznik macierzy $\mathbf{A}$ zapisujemy jako $\det(\mathbf{A})$ lub $|\mathbf{A}|$. Używanie pionowych kresek zamiast $\det$ pozwala na usunięcie nawiasu:

$$\det\left(\begin{bmatrix} a_{11} & \dots & a_{1n} \\ \vdots & \ddots & \vdots \\ a_{m1} & \dots & a_{mn} \end{bmatrix}\right) = \begin{vmatrix} a_{11} & \dots & a_{1n} \\ \vdots & \ddots & \vdots \\ a_{m1} & \dots & a_{mn} \end{vmatrix}$$

Ogólny wzór na wyznacznik macierzy $n \times n$ (wzór Laplace'a) wygląda następująco:

$$\det(\mathbf{A}) = \sum_{k=1}^{n} (-1)^{k+j} \det(\mathbf{A}_{kj}) = \sum_{k=1}^{n} (-1)^{i+k} \det(\mathbf{A}_{ik})$$

Gdzie $\mathbf{A}_{ij}$ to macierz, która powstaje z macierzy $\mathbf{A}$ poprzez usunięcie $i$-tego wiersza oraz $j$-tej kolumny. Jest to wzór konieczny do obliczania wyznaczników macierzy o wymiarach większych niż $3 \times 3$ (przy wymiarach $4 \times 4$ liczenie jest w miarę proste).

### Metody obliczania dla wybranych wymiarów:
* **Metoda Sarrusa (dla macierzy $3 \times 3$):** Należy dodawać do siebie wartości po pierwszej przekątnej, a następnie odejmować wartości po drugiej przekątnej. Wzór przyjmuje postać:

  $$\det\left(\begin{bmatrix} a & b & c \\ d & e & f \\ g & h & i \end{bmatrix}\right) = aei + bfg + cdh - ceg - fha - ibd$$

* **Dla macierzy $2 \times 2$:** $\det\left(\begin{bmatrix} a & b \\ c & d \end{bmatrix}\right) = ad - bc$.
* **Dla macierzy $1 \times 1$:** $\det([a]) = a$.

Jeżeli $\det(\mathbf{A}) \neq 0$, to macierz jest **nieosobliwa**. Jeżeli $\det(\mathbf{A}) = 0$, to macierz jest **osobliwa**.

## Macierz blokowa
Macierzą blokową nazywamy taką macierz $\mathbf{A}$, która składa się z dwóch niezerowych macierzy $\mathbf{A}_1, \mathbf{A}_2$ ustawionych po przekątnych:

$$\mathbf{A} = \begin{bmatrix} \mathbf{A}_1 & 0 \\ 0 & \mathbf{A}_2 \end{bmatrix}$$

Wyznacznik takiej macierzy jest wtedy równy iloczynowi wyznaczników macierzy $\mathbf{A}_1$ i $\mathbf{A}_2$:

$$\det \mathbf{A} = \det \mathbf{A}_1 \cdot \det \mathbf{A}_2$$

## Rząd macierzy
Rząd macierzy to jedna z jej własności, która mówi o tym, ile niezerowych wierszy zostaje po sprowadzeniu macierzy do postaci REF. Rząd macierzy $\mathbf{A}$ zapisujemy jako $r(\mathbf{A})$ bądź $\operatorname{rank} \mathbf{A}$.

**Własności rzędu macierzy:**
* $r(\mathbf{A}_{m \times n}) \le \min\{m, n\}$
* $r(\mathbf{A}) = r(\mathbf{A}^T)$
* $r(\mathbf{AB}) \le \min\{r(\mathbf{A}), r(\mathbf{B})\}$
* $r(\mathbf{A}_{n \times n}) = n \iff \det(\mathbf{A}) \neq 0$

> [!example] Przykłady macierzy w postaci REF i ich rzędy
> * $\mathbf{A} = \begin{bmatrix} 1 & 1 & 1 & 1 \\ 0 & -1 & -1 & -1 \\ 0 & 0 & -1 & -1 \\ 0 & 0 & 0 & 0 \end{bmatrix} \implies r(\mathbf{A}) = 3$
> * $\mathbf{A} = \begin{bmatrix} 1 & 2 & 3 & 4 \\ 0 & 1 & 2 & 3 \\ 0 & 0 & 1 & 2 \\ 0 & 0 & 0 & 1 \end{bmatrix} \implies r(\mathbf{A}) = 4$
> * $\mathbf{A} = \begin{bmatrix} 1 & 1 & 2 & 1 & 1 & 6 \\ 0 & 1 & 0 & 2 & 0 & 3 \\ 0 & 0 & 1 & 4 & 3 & 8 \\ 0 & 0 & 0 & 0 & 0 & 0 \end{bmatrix} \implies r(A) = 3$
> * $\mathbf{A} = \begin{bmatrix} 1 & 0 & -2 \\ 0 & 1 & 3 \\ 0 & 0 & 0 \end{bmatrix} \implies r(\mathbf{A}) = 2$
> * Dla macierzy zerowej $\mathbf{A = 0} \implies r(\mathbf{0}) = 0$

## Minory
Minorem stopnia $k$ macierzy $\mathbf{A}$ nazywamy wyznacznik macierzy powstającej z $\mathbf{A}$ poprzez wykreślenie $k$ wierszy oraz $k$ kolumn. Każdy współczynnik macierzy $\mathbf{A}$ jest minorem stopnia 1. 
**Twierdzenie:** Rząd macierzy $\mathbf{A}$ jest równy stopniowi największego niezerowego minora tej macierzy.

## Dopełnienia algebraiczne
Niech $\mathbf{A} = [a_{ij}]_{n \times m}$. Dopełnieniem algebraicznym elementu $a_{ij}$ nazywamy element $b_{ij}$ taki, że:

$$b_{ij} = (-1)^{i+j} \cdot \det(\mathbf{A}_{ij})$$

Gdzie $\mathbf{A}_{ij}$ to macierz powstała z $\mathbf{A}$ poprzez usunięcie $i$-tego wiersza oraz $j$-tej kolumny. Macierz $\mathbf{A}^D = [b_{ij}]_{n \times m}$ nazywamy **macierzą dopełnień algebraicznych**.

Dla każdej macierzy kwadratowej $\mathbf{A}$ zachodzi równość:

$$\mathbf{A} \cdot (\mathbf{A}^D)^T = \det \mathbf{A} \cdot \mathbf{I} = \begin{vmatrix} \det \mathbf{A} & 0 & \dots & 0 \\ 0 & \det \mathbf{A} & \dots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \dots & \det \mathbf{A} \end{vmatrix}$$

## Wyznaczanie macierzy odwrotnej za pomocą dopełnień
Jeśli $\mathbf{A} = [a_{ij}]_{n \times n}$ jest macierzą kwadratową stopnia $n$ oraz $\det \mathbf{A} \neq 0$, to prawdziwy jest wzór na macierz odwrotną:

$$\mathbf{A}^{-1} = \frac{1}{\det \mathbf{A}} \cdot (\mathbf{A}^D)^T$$

## Podsumowanie zbiorów macierzy
* $\mathbb{M}_{n,m}(F)$ – zbiór macierzy o wymiarach $m \times n$ nad ciałem $F$:

  $$\mathbb{M}_{n,m}(F) = \{\mathbf{A} = [a_{ij}]_{n \times m} : a_{ij} \in F\}$$

* $\mathbb{M}_n(F)$ – zbiór macierzy kwadratowych stopnia $n \times n$ nad ciałem $F$:

  $$\mathbb{M}_n(F) = \{\mathbf{A} \in \mathbb{M}_{n,m}(F) : n = m\}$$

* $\operatorname{Gl}_n(F)$ – zbiór macierzy odwracalnych nad ciałem $F$:

  $$\operatorname{Gl}_n(F) = \{\mathbf{A} \in \mathbb{M}_n(F) : \det \mathbf{A} \neq 0\}$$

* $\operatorname{Sl}_n(F)$ – zbiór macierzy odwracalnych nad ciałem $F$ o wyznaczniku równym 1:

  $$\operatorname{Sl}_n(F) = \{\mathbf{A} \in \operatorname{Gl}_n(F) : \det \mathbf{A} = 1\}$$

