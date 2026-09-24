
## Działania $n$-arne
Dany jest niepusty zbiór $A$ oraz $n \in \mathbb{N}$. Funkcję $f: A^n \rightarrow A$ nazywamy $n$-arnym działaniem w zbiorze $A$. Liczba $n$ oznacza ilość elementów, które biorą udział w działaniu.

Jeżeli $n=2$, działanie nazywamy **binarnym** (np. dodawanie, mnożenie).

Dane działanie musi być ściśle określone (zamknięte) dla wszystkich elementów zbioru, w którym je definiujemy.

**Przykłady:**
* Działanie $+$ jest działaniem binarnym w zbiorach $\mathbb{N}, \mathbb{Z}, \mathbb{Q}, \mathbb{R},\dots$
* Dzielenie $:$ nie jest działaniem binarnym w zbiorze $\mathbb{R}$, ponieważ wyrażenie $\frac{r}{0} \notin \mathbb{R}$ (nie jest określone).
* Dzielenie $:$ nie jest działaniem binarnym w zbiorze $\mathbb{Z} \setminus \{0\}$, ponieważ np. $\frac{1}{2} \notin \mathbb{Z}$ (wynik "wyskakuje" poza dziedzinę).
## Tabela Cayley'a
Jeśli $A$ jest zbiorem skończonym $A = \{a_1, a_2, \dots, a_n\}$, a $\circ$ jest działaniem binarnym w tym zbiorze, możemy opisać to działanie przy pomocy tabeli:

| $\circ$  |      $a_1$      |      $a_2$      | $\dots$  |      $a_n$      |
| :------: | :-------------: | :-------------: | :------: | :-------------: |
|  $a_1$   | $a_1 \circ a_1$ | $a_1 \circ a_2$ | $\dots$  | $a_1 \circ a_n$ |
|  $a_2$   | $a_2 \circ a_1$ | $a_2 \circ a_2$ | $\dots$  | $a_2 \circ a_n$ |
| $\vdots$ |    $\vdots$     |    $\vdots$     | $\ddots$ |    $\vdots$     |
|  $a_n$   | $a_n \circ a_1$ | $a_n \circ a_2$ | $\dots$  | $a_n \circ a_n$ |
Działanie binarne $\circ$ w zbiorze $A$ nazywamy:
* **Łącznym:** $\forall_{a,b,c \in A} \ a \circ (b \circ c) = (a \circ b) \circ c$.
* **Przemiennym:** $\forall_{a,b \in A} \ a \circ b = b \circ a$.
## Elementy zbiorów:
**Element neutralny $e \in A$:**
* Lewostronny: $\forall_{a \in A} \ e \circ a = a$.
* Prawostronny: $\forall_{a \in A} \ a \circ e = a$.
* Obustronny: $\forall_{a \in A} \ a \circ e = e \circ a = a$.

**Element odwrotny $a' \in A$:**
Jeżeli w zbiorze istnieje element neutralny $e$, to $a'$ nazywamy elementem odwrotnym do $a$, jeśli:
$$ \forall_{a \in A} \ a \circ a' = e $$
* W działaniach addytywnych (np. $+$) element ten nazywamy **przeciwnym** (zapisywanym jako $-a$).
* Jeśli $a$ posiada dokładnie jeden element odwrotny w zapisie multiplikatywnym (np. $\cdot$), to oznaczamy go jako $a^{-1}$.

**Rozdzielność działań:**
Działanie $\circ$ jest rozdzielne względem działania $\oplus$, jeżeli:
* (Lewostronnie) $\forall_{a,b,c \in A} \ a \circ (b \oplus c) = (a \circ b) \oplus (a \circ c)$.
* (Prawostronnie) $\forall_{a,b,c \in A} \ (a \oplus b) \circ c = (a \circ c) \oplus (b \circ c)$.
## Struktury algebraiczne

> [!abstract] Definicja
> Strukturą algebraiczną nazywamy zbiór wraz ze zdefiniowanymi na nim pewnymi działaniami. (Działań w strukturze może być nieskończenie wiele).

### Podstawowe rodzaje struktur algebraicznych:
| Nazwa struktury | Wymogi logiczne (Warunki) |
| :--- | :--- |
| **Magma** (Grupoid) | Struktura $(M, *)$, w której działanie jest wewnętrzne (zamknięte): $\forall_{a,b \in M} \ a * b \in M$. |
| **Półgrupa** | Struktura $(S, *)$, która jest magmą, a działanie $*$ jest **łączne**. |
| **Monoid** | Struktura $(S, *)$, która jest półgrupą posiadającą **element neutralny** $e$. |
| **Grupa** | Struktura $(G, *)$, która jest monoidem, a każdy jej element posiada **element odwrotny** $a'$. |
| **Grupa abelowa** | Grupa, w której działanie $*$ jest dodatkowo **przemienne**: $\forall_{a,b} \ a * b = b * a$. |

### Struktury z dwoma działaniami:
* **Pierścień:** Struktura $(R, \oplus, \otimes)$, w której:
  * $(R, \oplus)$ jest grupą abelową,
  * $(R, \otimes)$ jest półgrupą,
  * Działanie $\otimes$ jest rozdzielne względem $\oplus$.
* **Pierścień przemienny:** Pierścień, w którym działanie $\otimes$ jest przemienne.
* **Pierścień z jedynką:** Pierścień, w którym struktura $(R, \otimes)$ jest monoidem (posiada element neutralny mnożenia, zwany jedynką).
* **Ciało:** Struktura $(F, \oplus, \otimes)$, która jest pierścieniem przemiennym z jedynką, a każdy jej niezerowy element posiada element odwrotny względem drugiego działania (czyli $(F \setminus \{0\}, \otimes)$ jest grupą abelową).

---

## Inne wybrane struktury algebraiczne

* **Kwazigrupa:** Magma $(Q, *)$, w której dla każdego $a, b \in Q$ istnieje takie $x \in Q$, że $a * x = b$ (istnieje operacja odwrotna).
* **Pętla:** Kwazigrupa, w której istnieje element neutralny $e$.
* **Półkrata:** Struktura $(S, \wedge)$, w której działanie jest łączne, przemienne i idempotentne ($\forall_{a \in S} \ a \wedge a = a$).
* **Krata:** Struktura $(L, \vee, \wedge)$, w której obie operacje tworzą oddzielnie półkraty.
* **Algebra Boole'a:** Krata $(B, \vee, \wedge, \neg)$ spełniająca prawa absorpcji, rozdzielności oraz posiadająca elementy neutralne i odwrotne (dopełnienia) dla obu działań.
* **Półpierścień:** Struktura $(R, \oplus, \otimes)$, w której oba działania tworzą monoidy, a $(R, \oplus)$ jest dodatkowo monoidem przemiennym z zerem.

> [!note]- Algebra Liego
> Strukturę $(\mathfrak{g}, [,])$ nazywamy algebrą Liego, jeżeli $\mathfrak{g}$ jest przestrzenią wektorową nad ciałem $F$, a *nawias Liego* $[,]$ jest biliniowy, alternujący ($[x,x] = 0$) oraz spełnia Tożsamość Jacobiego:
> $$ [x, [y,z]] + [z, [x,y]] + [y, [z,x]] = 0 $$

---

## Permutacje

> [!info] Definicja permutacji
> Permutacją zbioru nazywamy dane uporządkowanie jego elementów. Można ją wyrazić za pomocą bijekcji $f: X \rightarrow X$. 
> Liczbę wszystkich możliwych permutacji zbioru $n$-elementowego oblicza się ze wzoru silni: **$n!$**.

* Zbiór wszystkich permutacji zbioru $X$ zapisujemy jako $\operatorname{Sym}(X)$ i nazywamy **grupą symetryczną** zbioru $X$.

> [!example] Przykład dla zbioru 3-elementowego
> Niech $X = \{1, 2, 3\}$. Moc zbioru $|X| = 3$.
> Liczba permutacji: $|\operatorname{Sym}(X)| = 3! = 6$.
> Wypisane zbiory permutacji to:
> $$ \operatorname{Sym}(X) = \{(1,2,3), (1,3,2), (2,1,3), (2,3,1), (3,2,1), (3,1,2)\} $$