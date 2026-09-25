
## Wolfram Mathematica
Mathematica jest jednym z najpopularniejszych programów do obliczeń symbolicznych i numerycznych, opracowanym w 1988 roku przez Stephena Wolframa. Program ten charakteryzuje się wysoką wydajnością, szerokimi możliwościami wizualizacji i prezentacji danych oraz przenośnością na platformy 32- i 64-bitowe. Mathematica posiada własny język programowania funkcyjnego (podobny do języka Lisp), który operuje na listach i oferuje bogate możliwości ich przetwarzania.

## Podstawowe operatory
W programie Wolfram Mathematica możemy wykonywać wszystkie podstawowe operacje matematyczne. Wykorzystywane do tego są następujące symbole:

| Zapis matematyczny         | Zapis w Mathematice |
| :------------------------- | :------------------ |
| $2+2$                      | `2 + 2`             |
| $5-2$                      | `5 - 2`             |
| $2\cdot3$ lub $2\times3$   | `2 * 3` lub `2 3`   |
| $4\div2$ lub $\frac{4}{2}$ | `4 / 2`             |
| $2^4$                      | `2 ^ 4`             |
| $\sqrt{4}$                 | `4 ^ (1/2)`         |

## Output (Wyniki obliczeń)
Mathematica automatycznie wyświetla rozwiązanie każdego wprowadzonego równania:
	`In[1]:= 2 + 2`
	`Out[1]= 4`

**Ukrywanie wyników:** W bardziej skomplikowanych programach automatyczne wyświetlanie wyników może wprowadzić duże zamieszanie. Jeżeli nie chcemy, by wynik (output) został wyświetlony na ekranie, na końcu równania należy umieścić średnik `;`:
	`In[1]:= 2 + 2;`

**Odwoływanie się do poprzednich wyników:** Mathematica automatycznie zapisuje wszystkie wyniki w zmiennej `Out[n]`, gdzie `n` to numer równania opisanego jako `In[n]`. Można wywołać wcześniejszy wynik wprost (np. `Out[1] + 2`).

**Operator `%`:** Skrótowo można korzystać z operatora `%`, który odwołuje się do ostatnich wyników:
  * `%` odpowiada `Out[x-1]` (poprzedni wynik)
  * `%%` odpowiada `Out[x-2]`
  * `%%%` odpowiada `Out[x-3]`

## Przybliżanie
Mathematica operuje na stałych matematycznych i fizycznych, zachowując ich dokładną postać (np. $\sqrt{2}$ to po prostu $\sqrt{2}$). Aby przybliżać wartości, korzystamy z funkcji $\mathtt{N}$ (przybliżenie numeryczne):

 **Metody przybliżania**
* **Podstawowe użycie:** $\mathtt{N}[\sqrt{2}]$ lub zapis ze znakiem specjalnym $\sqrt{2}$ // N` zwróci wynik `1.41421`.
* **Ustalenie dokładności:** Wywołanie $\mathtt{N}[a, n]$, gdzie `n` jest dokładnością. Przykład: $\mathtt{N}[\sqrt{2}, 10]$ zwróci `1.4142135624`.
* **Liczby zmiennoprzecinkowe:** Umieszczenie kropki po wartości całkowitej (np. $\sqrt{2.}$) sprawia, że operujemy na liczbach zmiennoprzecinkowych, które z definicji są numeryczne i zwracają wynik `1.41421`.

## Stałe
Mathematica posiada całą gamę stałych, mają one jednak unikalne symbole (rozpoczynające się zawsze z wielkiej litery), których nie należy mylić z niewiadomymi.

| Stała             | Zapis matematyczny | Symbol w Mathematice                 | Skrót klawiszowy |
| :---------------- | :----------------- | :----------------------------------- | :--------------- |
| Liczba pi         | $\pi$              | $\mathtt{Pi}$ lub symbol *`π`*       | `ESC p ESC`      |
| Liczba Eulera     | $e$                | $\mathtt{E}$ lub symbol $\mathbb{e}$ | `ESC ee ESC`     |
| Złoty podział     | $\varphi$          | $\mathtt{GoldenRatio}$               |                  |
| Stała Eulera      | $\gamma$           | $\mathtt{EulerGamma}$                |                  |
| Jednostka urojona | $i$                | $\mathtt{I}$ lub symbol $\mathbb{i}$ | `ESC ii ESC`     |

## Funkcje matematyczne
Funkcje matematyczne są zawsze zapisywane z wielkiej litery, a argumenty przyjmują w nawiasach kwadratowych. Funkcje trygonometryczne standardowo operują na radianach; aby działać na kątach, należy po wartości liczbowej umieścić znak stopni `°`.

| Zapis matematyczny         | Zapis w Mathematice         |
| :------------------------- | :-------------------------- |
| $\sin x$                   | `Sin[x]`                    |
| $\cos x$                   | `Cos[x]`                    |
| $\tan x$ / $\text{tg } x$  | `Tan[x]`                    |
| $\cot x$ / $\text{ctg } x$ | `Cot[x]`                    |
| $\ln x$                    | `Log[x]`                    |
| $\log_{10} x$              | `Log10[x]` lub `Log[10, x]` |
| $\log_b x$                 | `Log[b, x]`                 |

## Pomoc w Mathematice
Mathematica ma wbudowaną funkcję pomocy. Aby z niej skorzystać, należy użyć symbolu `?` przed funkcją:
* `?Log` – Pojedynczy znak zapytania zwraca opis działania i poprawny zapis funkcji.
* `??Log` – Podwójny znak zapytania zwraca wyjaśnienie oraz szczegóły systemowe funkcji (np. atrybuty jak `Listable`, `Protected`).
* `?Log*` – Znak zapytania przed funkcją i gwiazdka na końcu zwróci listę wszystkich dostępnych funkcji zaczynających się od podanego ciągu znaków (np. `Log`, `Log10`, `Log2`, `LogGamma`, itd.).

## Pochodne i całki
W Mathematice można wykonywać obliczenia symboliczne z zakresu analizy matematycznej:

| Zapis matematyczny                                  | Zapis w Mathematice          |
| :-------------------------------------------------- | :--------------------------- |
| $\frac{df}{dx}$ lub $\frac{\partial f}{\partial x}$ | `D[f, x]`                    |
| $\int f(x) dx$                                      | `Integrate[f[x], x]`         |
| $\int_{a}^{b} f(x) dx$                              | `Integrate[f[x], {x, a, b}]` |

## Zmienne
Zmienne pozwalają na przechowywanie wartości.
* **Przypisanie:** `a = 2`.
* **Operacje:** Zmiennych można używać w równaniach, np. `a + 3` zwróci `5`, a `a + b` zwróci `2 + b` (jeśli `b` nie ma przypisanej wartości).
* **Czyszczenie przypisania:** Aby wyczyścić zmienną, należy przypisać jej wartość do kropki (np. `a = .`) lub skorzystać z funkcji $\mathtt{Clear}$, która pozwala usunąć wiele przypisań (np. `Clear[a]`, `Clear[a, b, c]`).

## Wektory
Aby utworzyć wektor, należy do zmiennej przypisać zbiór (w nawiasach klamrowych): `v = {1, 2, 3}`.

**Operacje na wektorach:**

| Zapis matematyczny                           | Zapis w Mathematice     |
| :------------------------------------------- | :---------------------- |
| $\vec{v} + \vec{u}$                          | `v + u`                 |
| $2 \cdot \vec{v}$                            | `2v`                    |
| $\Vert\vec{v}\Vert$                          | `Norm[v]`               |
| $\Vert\vec{v}\Vert_{\infty}$                 | `Norm[v, \infty]`       |
| Wersor wektora                               | `Normalize[v]`          |
| $\vec{v} \cdot \vec{u}$ (iloczyn skalarny)   | `v . u` lub `Dot[v, u]` |
| $\vec{v} \times \vec{u}$ (iloczyn wektorowy) | `Cross[v, u]`           |

**Odwoływanie i modyfikowanie elementów wektora:**
* Długość wektora uzyskuje się używając funkcji `Length[v]`.
* Umieszczenie podwójnego nawiasu klamrowego `[[i]]` oznacza odwołanie się do $i$-tego elementu wektora (np. `v[[3]]` zwróci `6` dla `v = {2, 4, 6}`).
* Zmiana konkretnego elementu wektora działa przez operator równości: `v[[2]] = 8` zmienia stary wektor z `{2, 4, 6}` na `{2, 8, 6}`.

## Macierze
Macierze w programie tworzymy poprzez zagnieżdżanie zbiorów wewnątrz zbiorów.
`M = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}}`

Aby wyświetlić macierz w postaci klasycznej tablicy, należy wywołać funkcję `MatrixForm[M]`.

**Operacje na macierzach:**

| Zapis matematyczny      | Zapis w Mathematice |
| :---------------------- | :------------------ |
| $\mathbf{M + N}$        | `M + N`             |
| $\mathbf{M \cdot N}$    | `M . N`             |
| $\mathbf{M}^T$          | `Transpose[M]`      |
| $\det \mathbf{M}$       | `Det[M]`            |
| $\text{tr } \mathbf{M}$ | `Tr[M]`             |
| $\mathbf{M}^{-1}$       | `Inverse[M]`        |
| $\dim \mathbf{M}$       | `Dimensions[M]`     |
**Macierze specjalne:**
* $\mathbf{I}_n$ (jednostkowa): `IdentityMatrix[n]`
* $\mathbf{0}_{m\times n}$ (zerowa): `ConstantArray[0, {m, n}]`
* $\text{diag}(d_1, d_2, d_3)$ (diagonalna): `DiagonalMatrix[{d1, d2, d3}]`

Podobnie jak przy wektorach, odwołujemy się do konkretnych elementów: `M[[1, 2]]` (pierwszy wiersz, druga kolumna), `M[[2]]` (cały drugi wiersz), `M[[All, 2]]` (cała druga kolumna).

## Tabele
Funkcja `Table` służy do generowania list (zbiorów, wektorów, macierzy) utworzonych według określonych zasad.

* **Składnia podstawowa:** `Table[f[i], {i, a, b, n}]`, gdzie:
  * `f[i]` – wartość (najczęściej funkcja zmiennej), która będzie dodawana do zbioru.
  * `i` – zmienna iteracyjna.
  * `a` – wartość początkowa `i`.
  * `b` – wartość końcowa `i`.
  * `n` – krok zmiany zmiennej iteracyjnej.
* **Przykład wywołania wektora:** `Table[i^3, {i, 0, 12, 2}]` zwróci `{0, 8, 64, 216, 512, 1000, 1728}`.
* **Rozszerzenie dla macierzy:** `Table[f[i, j], {i, a, b}, {j, c, d}]`, gdzie stosuje się podwójną iterację dla wierszy (`i`) oraz kolumn (`j`). Np. `Table[i * j, {i, 1, 3}, {j, 1, 3}]` zwraca zagnieżdżoną listę odzwierciedlającą macierz $3\times3$.

## Rozwiązania równań
Do rozwiązywania równań (lub układów równań) wykorzystuje się funkcję `Solve[e, x]`, gdzie $e$ to równanie lub lista równań, a $x$ to szukana niewiadoma (lub zbiór niewiadomych).

* **Przykład:** `Solve[x^2 + 2x - 3 == 0, x]` zwróci wynik w formie listy reguł `{{x -> -3}, {x -> 1}}`.
* **Ekstrakcja wyników:** Przypisując rezultat do zmiennej `s`, możemy odwołać się do poszczególnych rozwiązań:
  * `s[[1]]` zwraca zbiór z pierwszą odpowiedzią: `{x -> -3}`.
  * `s[[1, 1]]` zwraca całą regułę: `x -> -3`.
  * `s[[1, 1, 2]]` wyciąga wyłącznie konkretną wartość numeryczną: `-3`.

