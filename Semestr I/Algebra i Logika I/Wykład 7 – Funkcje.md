
> [!info] Definicja funkcji
> **Definicja zwyczajowa:**
> Funkcją przekształcającą zbiór $X$ w zbiór $Y$ nazywamy przyporządkowanie każdemu elementowi zbioru $X$ **dokładnie jednego** elementu zbioru $Y$.
> 
> **Definicja formalna:**
> Funkcję przekształcającą zbiór $X$ w zbiór $Y$ nazywamy podzbiór $f \subseteq X \times Y$ taki, że:
> 1. $\forall_{x \in X} \exists_{y \in Y} : (x,y) \in f$
> 2. $\forall_{x \in X} \forall_{y_1, y_2 \in Y} \left((x,y_1) \in f \wedge (x,y_2) \in f \Rightarrow y_1 = y_2\right)$

**Oznaczenia i terminologia:**
* Zapis funkcji: $f: X \rightarrow Y$
* Zapis mapowania: $x \mapsto y$
* Argumenty funkcji: $x \in X$
* Wartość funkcji w punkcie $x$: $f(x)$
* Dziedzina funkcji $f$: Zbiór $X$
* Przeciwdziedzina funkcji $f$: Zbiór $Y$

**Równość funkcji:**
Funkcje $f: X \rightarrow Y$ oraz $g: A \rightarrow B$ są równe (co zapisujemy jako $f=g$), jeżeli spełniają trzy warunki:
1. $X=A$ (równe dziedziny)
2. $Y=B$ (równe przeciwdziedziny)
3. $\forall_{x \in X} \ f(x) = g(x)$ (równe wartości dla każdego argumentu)

---

## Operacje modulo i zbiory funkcji
Rozważmy operacje dodawania ($+_{2}$) i mnożenia ($\cdot_{2}$) modulo 2 w zbiorze $\mathbb{Z}_2 = \{0, 1\}$.

| $+_{2}$ | 0 | 1 |
| :---: | :---: | :---: |
| **0** | 0 | 1 |
| **1** | 1 | 0 |

| $\cdot_{2}$ |  0  |  1  |
| :---------: | :-: | :-: |
|    **0**    |  0  |  0  |
|    **1**    |  0  |  1  |

> [!tip] Zbiór wszystkich funkcji $Y^X$
> Jeśli $X, Y$ są zbiorami, to przez $Y^X$ oznaczamy zbiór wszystkich funkcji $f: X \rightarrow Y$.
> Jeśli $|X| = m$ oraz $|Y| = n$, to liczba wszystkich możliwych funkcji wynosi:
> $$ |Y^X| = n^m $$

**Wariacje (Ciągi):**
Niech $X$ będzie zbiorem $n$-elementowym. Funkcję $f: \{1, \dots, k\} \rightarrow X$ nazywamy $k$-wyrazową wariacją zbioru $n$-elementowego. Takich wariacji (ciągów długości $k$) jest $n^k$.

---

## Operacje na funkcjach

### Złożenie (Superpozycja)
Dane są funkcje $f: X \rightarrow Y$ oraz $g: Y \rightarrow Z$.
Złożeniem funkcji $f$ i $g$ nazywamy funkcję $(g \circ f): X \rightarrow Z$, określoną wzorem:
$$ (g \circ f)(x) = g(f(x)) $$
Złożenie funkcji jest działaniem łącznym: $h \circ (g \circ f) = (h \circ g) \circ f$.

### Funkcja identycznościowa
W zbiorze $X$ funkcję $id_{X}: X \rightarrow X$ nazywamy identycznością, jeżeli dla każdego elementu zwraca ona ten sam argument:
$$ id_{X}(x) = x $$
Dla dowolnej funkcji $f: X \rightarrow Y$ zachodzą równości:
$$ id_{Y} \circ f = f $$
$$ f \circ id_{X} = f $$

### Funkcja odwrotna
Dana jest funkcja $f: X \rightarrow Y$. Funkcję $g: Y \rightarrow X$ nazywamy funkcją odwrotną do $f$, jeśli:
$$ f \circ g = id_{Y} \wedge g \circ f = id_{X} $$

* Funkcje, które posiadają funkcje odwrotne, nazywamy **funkcjami odwracalnymi**.
* Jeśli $f$ jest odwracalna, to posiada *dokładnie jedną* funkcję odwrotną, oznaczaną jako $f^{-1}$.
* Zachodzi relacja: $f^{-1}(y) = x \Leftrightarrow f(x) = y$.
* Wykres funkcji odwrotnej jest odbiciem wykresu funkcji odwracalnej względem prostej $y=x$ (np. $f(x)=e^x$ oraz $f^{-1}(x)=\ln x$).

**Przykład wyliczania funkcji odwrotnej:**
$$ y = 2x+3 $$
$$ y-3 = 2x $$
$$ x = \frac{y-3}{2} \Rightarrow f^{-1}(x) = \frac{x-3}{2} $$

### Potęgi funkcji złożonych
Wielokrotne złożenie tej samej funkcji ze sobą oznaczamy jako potęgowanie:
* $f \circ f = f^2$
* $f^{n-1} \circ f = f^n$
* $f^{-1} \circ f = f^0 = id_{X}$
* $f^n(f(x)) = f(f^n(x))$

---

## Przyporządkowania funkcji

Zbiorem wartości funkcji $f: X \rightarrow Y$ nazywamy zbiór $\text{Im}(f) = \{ f(x) : x \in X \}$.

| Typ funkcji | Alternatywna nazwa | Warunek logiczny | Interpretacja |
| :--- | :--- | :--- | :--- |
| **Surjekcja** | Funkcja „na” | $\text{Im}(f) = Y$ | Zbiór wartości funkcji całkowicie pokrywa się z jej przeciwdziedziną. |
| **Iniekcja** | Różnowartościowa | $\forall_{x_1, x_2 \in X} (x_1 \ne x_2 \Rightarrow f(x_1) \ne f(x_2))$ | Funkcja nie osiąga tej samej wartości dla dwóch różnych argumentów. |
| **Bijekcja** | Wzajemnie jednoznaczna | Surjekcja $\wedge$ Iniekcja | Każdy element przeciwdziedziny ma dokładnie jeden przypisany argument z dziedziny. |

> [!abstract] Twierdzenia o przyporządkowaniu
> 1. **Zasada szufladkowa Dirichleta:** Jeśli $X, Y$ są zbiorami skończonymi i $|X| > |Y|$, to *żadna* funkcja $f: X \rightarrow Y$ nie jest różnowartościowa (iniekcją) i *żadna* funkcja $g: Y \rightarrow X$ nie jest „na” (surjekcją).
> 2. **Odwracalność:** Funkcja jest odwracalna wtedy i tylko wtedy, gdy jest bijekcją. Jeśli $f$ jest bijekcją, to $f^{-1}$ również jest bijekcją.
> 3. **Złożenia:** Złożenie dwóch surjekcji to surjekcja. Złożenie dwóch iniekcji to iniekcja. Złożenie dwóch bijekcji to bijekcja.
> 4. **Zbiory skończone:** Jeśli zbiór $X$ jest skończony ($|X|=|Y|$), to funkcja $f: X \rightarrow Y$ jest surjekcją wtedy i tylko wtedy, gdy jest iniekcją.

---

## Równoliczność i przeliczalność zbiorów

Powiemy, że zbiory $A$ i $B$ są **równoliczne** (zapisujemy to jako $|A| = |B|$), jeśli istnieje bijekcja $f: A \rightarrow B$.

**Własności równoliczności:**
* Symetria: Jeśli $|A| = |B|$, to $|B| = |A|$.
* Przechodniość: Jeśli $|A| = |B|$ i $|B| = |C|$, to $|A| = |C|$.

**Przykłady zbiorów równolicznych:**
* Każde dwa dowolne przedziały otwarte są równoliczne: $|(a,b)| = |(c,d)|$
* Przedział otwarty jest równoliczny z całym zbiorem liczb rzeczywistych $\mathbb{R}$: 
  * $|(-\frac{\pi}{2}, \frac{\pi}{2})| = |\mathbb{R}|$ (bijekcją jest funkcja $f(x) = \tan(x)$)
  * $|(0, +\infty)| = |\mathbb{R}|$ (bijekcją jest funkcja $f(x) = \ln(x)$)

> [!info] Przeliczalność
> Zbiór $X$ jest **przeliczalny**, jeżeli jest skończony lub jest równoliczny ze zbiorem liczb naturalnych ($|X| = |\mathbb{N}|$). 
> Oznacza to, że istnieje bijekcja $f: X \rightarrow \mathbb{N}$, dzięki której wszystkie elementy zbioru $X$ można bez pominięć ustawić w ciąg $x_1, x_2, x_3, \dots$.