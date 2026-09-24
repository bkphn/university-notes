
> [!info] Definicja częściowego porządku
> Relację $\mathcal{R}$ w zbiorze $X$ nazywamy **częściowym porządkiem**, jeżeli spełnia ona jednocześnie trzy warunki: jest zwrotna, antysymetryczna oraz przechodnia. 
> Parę $(X, \mathcal{R})$ określamy wówczas mianem **zbioru częściowo uporządkowanego**.

## Własności i zapis
Aby relacja była częściowym porządkiem, musi posiadać następujące cechy:
* **Zwrotność:** $\forall_{a \in X} \ a\mathcal{R}a$.
* **Antysymetryczność:** $\forall_{a,b \in X} \ (a\mathcal{R}b \wedge b\mathcal{R}a \implies a = b)$.
* **Przechodniość:** $\forall_{a,b,c \in X} \ (a\mathcal{R}b \wedge b\mathcal{R}c \implies a\mathcal{R}c)$.

> [!tip] Porządek liniowy
> Jeśli relacja częściowego porządku jest dodatkowo **spójna** (tzn. dla każdych $a, b \in X$ zachodzi $a < b \vee b < a \vee a = b$), to nazywamy ją **porządkiem liniowym**.

W notatkach częściowy porządek jest zwyczajowo oznaczany symbolem $<$, co odczytujemy jako „$a$ *poprzedza* $b$” lub „$b$ *następuje po* $a$”. W sytuacji, gdy dla różnych elementów $a, b \in X$ relacja nie zachodzi w żadną stronę (i $a \ne b$), mówimy, że elementy te są **nieporównywalne**.

**Przykład:**
Dla zbioru dzielników $D_{n} = \{d \in \mathbb{N} : d|n\}$, relacja podzielności ($|$) stanowi częściowy porządek.

---

## Diagram Hassego

> [!info] Definicja
> Diagram Hassego to graficzne uproszczenie służące do oznaczania relacji częściowego porządku ($<$) za pomocą grafów.

Przy jego tworzeniu obowiązują następujące zasady:
* Nie rysuje się kresek poziomych.
* Konstrukcja wyklucza strzałki skierowane w obie strony.
* Pomija się krawędzie (połączenia), które wynikają bezpośrednio z przechodniości relacji.
* Nie rysuje się pętli.
* Bezpośrednia kreska (krawędź) prowadzi od elementu $a$ do $b$ tylko wtedy, gdy nie istnieje żaden element pośredni $c$ (taki, że $a < c < b$ oraz $a \ne c$ i $c \ne b$).

---

## Elementy ekstremalne
Rozważmy zbiór częściowo uporządkowany $(X, <)$. Możemy w nim wyróżnić specjalne typy elementów:

| Typ elementu    | Zapis logiczny                                  | Interpretacja                                                    |
| :-------------- | :---------------------------------------------- | :--------------------------------------------------------------- |
| **Najmniejszy** | $\forall_{x \in X} \ a < x$                     | Element $a$ jest mniejszy od wszystkich elementów w zbiorze $X$. |
| **Minimalny**   | $\forall_{x \in X} \ (x < a \Rightarrow x = a)$ | Nie ma w zbiorze elementu mniejszego od $a$.                     |
| **Największy**  | $\forall_{x \in X} \ x < a$                     | Element $a$ jest większy od wszystkich elementów w zbiorze $X$.  |
| **Maksymalny**  | $\forall_{x \in X} \ (a < x \Rightarrow x = a)$ | Nie ma w zbiorze elementu większego od $a$.                      |

---

## Ograniczenia i kresy zbiorów

Niech $(X, <)$ będzie zbiorem częściowo uporządkowanym, a $A$ jego podzbiorem.

* **Ograniczenie dolne:** Element $x \in X$ nazywamy ograniczeniem dolnym zbioru $A$, jeżeli dla każdego $a \in A$ zachodzi $x < a$.
* **Ograniczenie górne:** Element $x \in X$ nazywamy ograniczeniem górnym zbioru $A$, jeżeli dla każdego $a \in A$ zachodzi $a < x$.

> [!abstract] Kresy zbioru (Infimum i Supremum)
> * **Infimum** ($\inf_{<}(A)$): Nazywamy tak największe ograniczenie dolne zbioru $A$.
> * **Supremum** ($\sup_{<}(A)$): Nazywamy tak najmniejsze ograniczenie górne zbioru $A$.

**Przykład własności:**
Dla zbioru liczb naturalnych z relacją podzielności $(\mathbb{N}, |)$ oraz elementów $a, b \in \mathbb{N}$ zachodzi:
$$\sup_{|} \{a,b\} = NWW(a,b)$$
$$\inf_{|} \{a,b\} = NWD(a,b)$$