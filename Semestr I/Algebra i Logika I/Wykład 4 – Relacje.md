
> [!info] Definicja relacji
> Niech $X$ oraz $Y$ będą zbiorami. 
> **Relacją ze zbioru $X$ w zbiorze $Y$** nazywamy dowolny podzbiór iloczynu kartezjańskiego $X \times Y$.
> **Relacją w zbiorze $X$** nazywamy dowolny podzbiór zbioru $\{(x,y) : x,y \in X\}$.

**Symbol relacji:**
Niech $\mathcal{R}$ będzie relacją w zbiorze $X$. Możemy to zapisać jako:
$$
\mathcal{R} \subseteq X^{2} = X \times X
$$
Jeśli $(x,y) \in \mathcal{R}$, to będziemy pisać $x\mathcal{R}y$.
Jeśli $(x,y) \notin \mathcal{R}$, to będziemy pisać $x\mathcal{\cancel{ R }}y$.

---
## Rodzaje relacji
Niech $\mathcal{R} \subseteq A \times A$.

| Nazwa relacji       | Zapis (Definicja)                                                                                                                                                | Przykład                                          |
| :------------------ | :--------------------------------------------------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------ |
| **Zwrotna**         | $\forall_{x \in A} \ x\mathcal{R}x$                                                                                                                              | $x\mathcal{R}y \iff x \le y$ (ponieważ $x \le x$) |
| **Symetryczna**     | $\forall_{x,y \in A} \ (x\mathcal{R}y \implies y\mathcal{R}x)$                                                                                                   | $x\mathcal{R}y \iff x = y$                        |
| **Przechodnia**     | $\forall_{x,y,z \in A} \ (x\mathcal{R}y \wedge y\mathcal{R}z \implies x\mathcal{R}z)$                                                                            | $x\mathcal{R}y \iff x \le y$                      |
| **Antysymetryczna** | $\forall_{x,y \in A} \ (x\mathcal{R}y \wedge y\mathcal{R}x \implies x = y)$                                                                                      | $x\mathcal{R}y \iff x \le y$                      |
| **Asymetryczna**    | $\forall_{x,y \in A} \ (x\mathcal{R}y \implies \neg y\mathcal{R}x)$                                                                                              | $x\mathcal{R}y \iff x < y$                        |
| **Spójna**          | $\forall_{x,y \in A} \ (x\mathcal{R}y \vee y\mathcal{R}x \vee x = y)$                                                                                            | Relacja porządku na osi liczbowej.                |
| **Równoważności**   | $\forall_{x,y,z \in A} \ (x\mathcal{R}x) \wedge (x\mathcal{R}y \Rightarrow y\mathcal{R}x) \wedge (x\mathcal{R}y \wedge y\mathcal{R}z \Rightarrow x\mathcal{R}z)$ | $x\mathcal{R}y \iff x = y$                        |

> [!abstract] Relacja równoważności
> Relacja jest relacją równoważności, jeśli jest jednocześnie **zwrotna**, **symetryczna** i **przechodnia**.

---

## Relacja przystawania modulo $n$
Niech $n \in \mathbb{N}$. Definiujemy przystawanie modulo $n$ jako:
$$
a \equiv b \pmod{n} \iff  n | (a-b)
$$
*Interpretacja:* Jeżeli podzielimy $a$ lub $b$ przez $n$, to otrzymamy tę samą resztę z dzielenia.

**Własności relacji przystawania:**
1.  **Zwrotność:** $a \equiv a \pmod{n} \Rightarrow n | (a-a)$
2.  **Symetria:** $a \equiv b \pmod{n} \Rightarrow b \equiv a \pmod{n}$, ponieważ:
    $$
    n | (a-b) \implies a-b = n \cdot k \quad (\text{dla } k \in \mathbb{Z})
    $$
    $$
    b-a = n \cdot (-k) \implies n | (b-a) \Rightarrow b \equiv a \pmod{n}
    $$
3.  **Przechodniość:** $(a \equiv b \pmod{n} \wedge b \equiv c \pmod{n}) \implies a \equiv c \pmod{n}$
4.  **Dodawanie/Mnożenie:** $(a \equiv b \pmod{n} \wedge c \equiv d \pmod{n}) \implies a+c \equiv b+d \pmod{n} \wedge a \cdot c \equiv b \cdot d \pmod{n}$

> [!tip] Twierdzenie o dzieleniu z resztą
> Niech $a, b \in \mathbb{Z}$ oraz $b > 0$. Wtedy istnieje dokładnie jedna para liczb całkowitych $q, r$ taka, że:
> $$ a = q \cdot b + r \quad \text{oraz} \quad 0 \le r < b $$
> Liczbę $r$ nazywamy **resztą z dzielenia** $a$ przez $b$.

---

## Operacje na relacjach
Dane są relacje $\mathcal{R}_{1}$ oraz $\mathcal{R}_{2}$ w zbiorze $X$.
*   **Suma relacji:** $\quad x(\mathcal{R}_{1} \cup \mathcal{R}_{2})y \Leftrightarrow x\mathcal{R}_{1}y \vee x\mathcal{R}_{2}y$
*   **Przekrój relacji:** $\quad x(\mathcal{R}_{1} \cap \mathcal{R}_{2})y \Leftrightarrow x\mathcal{R}_{1}y \wedge x\mathcal{R}_{2}y$
*   **Złożenie relacji:** $\quad x(\mathcal{R}_{1} \circ \mathcal{R}_{2})y \Leftrightarrow \exists_{z \in X} \ (x\mathcal{R}_{1}z \wedge z\mathcal{R}_{2}y)$

---

## Klasy abstrakcji
> [!info] Definicja Klasy Abstrakcji
> Niech $\mathcal{R}$ będzie **relacją równoważności** w zbiorze $X$ i niech $x \in X$. Klasą abstrakcji elementu $x$ nazywamy zbiór:
> $$[x]_{\mathcal{R}} = \{ y \in X : x\mathcal{R}y \}$$

Istnieje podzbiór $S \subseteq X$ (tzw. zbiór reprezentantów) taki, że zbiór $X$ jest sumą rozłącznych klas abstrakcji:
$$
X = \bigcup_{x \in S} [x]_{\mathcal{R}}
$$

**Przykłady klas abstrakcji:**
1.  **Równość** ($a\mathcal{R}b \Leftrightarrow a=b$):
    $[a]_{\mathcal{R}} = \{ x \in X : x\mathcal{R}a \} = \{a\}$
2.  **Relacja pełna w $X$**:
    $[a]_{\mathcal{R}} = X$
3.  **Wartość bezwzględna** ($X = \mathbb{R}, a\mathcal{R}b \Leftrightarrow |a|=|b|$):
    $[a]_{\mathcal{R}} = \{ x \in \mathbb{R} : |x| = |a| \} = \{a, -a\}$
4.  **Przystawanie modulo 5 w $\mathbb{Z}$** ($5 | (a-b)$):
    $[0]_{\equiv 5} = \{ x \in \mathbb{Z} : x \equiv 0 \pmod{5} \} = \{ x \in \mathbb{Z} : \exists_{k \in \mathbb{Z}} \ x=5k \}$
    $[0]_{\equiv 5} = \{ 5k : k \in \mathbb{Z} \} = 5\mathbb{Z}$

**Własności klas abstrakcji:**
*   Klasy abstrakcji nigdy nie są puste: $\forall_{x \in X} \ [x]_{\mathcal{R}} \ne \emptyset$
*   Są albo identyczne, albo rozłączne: $\forall_{x,y \in X} \ ([x]_{\mathcal{R}} = [y]_{\mathcal{R}} \vee [x]_{\mathcal{R}} \cap [y]_{\mathcal{R}} = \emptyset)$
*   Elementy są w relacji wtedy i tylko wtedy, gdy ich klasy abstrakcji są równe: $\forall_{x,y \in X} \ ([x]_{\mathcal{R}} = [y]_{\mathcal{R}} \Leftrightarrow x\mathcal{R}y)$

---

## Liczby Bella
> [!info] Definicja Liczby Bella
> Liczbę wszystkich możliwych relacji równoważności (czyli podziałów zbioru na rozłączne klasy abstrakcji) na zbiorze $n$-elementowym nazywamy **$n$-tą liczbą Bella** i oznaczamy ją przez $B_{n}$.

**Początkowe liczby Bella:**
$$ B_{0} = 1 $$
$$ B_{1} = 1 $$
$$ B_{2} = 2 $$
$$ B_{3} = 5 $$

**Wzór rekurencyjny:**
$$
B_{n+1} = \sum_{k=0}^{n} \binom{n}{k} \cdot B_{k}
$$
Gdzie symbol Newtona to: $\binom{n}{k} = \frac{n!}{k! \cdot (n-k)!}$

**Przykład dla $B_4$:**
Obliczamy $B_{4}$ na podstawie wzoru (dla $n=3$):
$$ B_{4} = \sum_{k=0}^{3} \binom{3}{k} \cdot B_{k} $$
$$ B_{4} = \binom{3}{0}B_{0} + \binom{3}{1}B_{1} + \binom{3}{2}B_{2} + \binom{3}{3}B_{3} $$
Wiedząc, że $\binom{n}{0}=1$, $\binom{n}{n}=1$ oraz $\binom{n}{1}=n$:
$$ B_{4} = 1 \cdot 1 + 3 \cdot 1 + 3 \cdot 2 + 1 \cdot 5 = 1 + 3 + 6 + 5 = 15 $$