## Równoliczność zbiorów
Powiemy, że zbiory $A$ i $B$ są **równoliczne**, jeśli istnieje bijekcja $f: A \rightarrow B$.	Równoliczność zapisujemy jako $|A| = |B|$ bądź $A\sim B$.

**Własności równoliczności:**
* **Symetria:** Jeśli $|A| = |B|$, to $|B| = |A|$.
* **Przechodniość:** Jeśli $|A| = |B|$ i $|B| = |C|$, to $|A| = |C|$.

## Liczby kardynalne
Liczby kardynalne to rodzaj liczb pozaskończonych, służących do opisywania mocy zbiorów nieskończonych.

Najmniejszą liczbą kardynalną jest $\aleph_0$ (alef zero) i jest ona zdefiniowana jako moc zbioru liczb naturalnych.

## Zbiory przeliczalne
Zbiory $\mathbb{N}$ oraz $\mathbb{Z}$ są równoliczne. Aby to udowodnić, musimy uporządkować te zbiory, przypisując każdy element każdemu (tworząc bijekcję):

$$\mathbb{N}: \quad 0 \qquad 1 \qquad 2 \qquad 3 \qquad 4 \quad \dots$$

$$\mathbb{Z}: \quad 0 \quad -1 \qquad 1 \quad -2 \qquad 2 \quad \dots$$

Każdy element jest sparowany z każdym, co dowodzi ich równoliczności.

Zbiór $X$ nazywamy **przeliczalny**, jeżeli jest skończony lub gdy $|X| = |\mathbb{N}|$. Jeśli zbiór $X$ jest przeliczalny, to wszystkie jego elementy można ustawić w ciąg $x_1, x_2, x_3, \dots$.

## Zbiory nieprzeliczalne i Continuum
Zbiory nieprzeliczalne to takie, których nie da się ponumerować kolejnymi liczbami naturalnymi. Przykładem takiego zbioru są liczby rzeczywiste $\mathbb{R}$. Dowodzi tego **metoda przekątniowa** (zawsze jesteśmy w stanie znaleźć kolejną niesparowaną liczbę rzeczywistą).

Moc zbioru liczb rzeczywistych określamy jako **continuum** i oznaczamy symbolem $\mathfrak{c}$. Możemy również udowodnić, że continuum jest równe mocy zbioru potęgowego liczb naturalnych:

$$|\mathbb{R}| = |\mathcal{P}(\mathbb{N})| \qquad \mathfrak{c} = 2^{\aleph_0}$$

### Hipoteza continuum
Wprowadźmy oznaczenie $\aleph_n$ (gdzie $n \in \mathbb{N}$), które symbolizuje $n$-tą liczbę kardynalną w kolejności rosnącej.
* **Hipoteza continuum:** Jest to teoria mówiąca o tym, że continuum jest drugą najmniejszą liczbą kardynalną, równą $\aleph_1$. Zapisujemy to jako $|\mathbb{R}| = \mathfrak{c} = 2^{\aleph_0} = \aleph_1$.
* Teoria ta jest niedowiedlna – nie istnieje sposób, aby ją obalić bądź potwierdzić w ramach aksjomatyki ZFC.
* **Uogólniona hipoteza continuum:** Głosi, że zachodzi równość $\aleph_{n+1} = 2^{\aleph_n}$.

## Operacje na liczbach kardynalnych
Dla $\alpha \in \mathbb{R}$ zachodzą następujące własności arytmetyczne:
* $\aleph_n + \aleph_n = \aleph_n$.
* $\aleph_n \cdot \aleph_n = \aleph_n$.
* $\aleph_n + \alpha = \aleph_n$.
* $\aleph_n \cdot \alpha = \aleph_n$ (gdzie $\alpha \in \mathbb{R} \setminus \{0\}$).
* $\aleph_n \cdot 0 = 0$.

## Działania na zbiorach rozłącznych
Dane są rozłączne zbiory $A$ i $B$, czyli takie, że $A \cap B = \emptyset$. 
Załóżmy, że $|A| = \mathfrak{m}$ oraz $|B| = \mathfrak{n}$. Wówczas zachodzi:
* Moc sumy rozłącznej: $|A \sqcup B| = \mathfrak{m} + \mathfrak{n}$.
* Moc iloczynu kartezjańskiego: $|A \times B| = \mathfrak{m} \cdot \mathfrak{n}$.
* Moc przestrzeni funkcji: $|A^B| = |\{f: B \rightarrow A\}| = \mathfrak{m}^\mathfrak{n}$.
