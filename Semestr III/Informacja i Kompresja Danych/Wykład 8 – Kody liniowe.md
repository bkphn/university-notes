## Kody nadmiarowe
**Kodem nadmiarowym** nazywamy kod, w wyniku którego ciąg $k$ liter po zakodowaniu jest ciągiem o długości $n$, gdzie $n > k$.
## Ciała Galois
Liniowym $(n, k)$-kodem nad ciałem $F_q$ jest nazywana podprzestrzeń $V$ wymiaru $k$ w przestrzeni liniowej $F_q^n$, gdzie $q = p^m$, $p \in \mathbb{P}$ a $F_q = \{0, 1, \dots, q-1\}$, przez $\mathbb{P}$ oznaczamy zbiór liczb pierwszych.

Aby struktura $(F_q, +_q, \cdot_q)$ była ciałem Galois, zbiór $F_q$ musi być zbiorem skończonym, a liczba $q$ musi być wielokrotnością liczby pierwszej. W przeciwnym przypadku otrzymana struktura jest pierścieniem reszt modulo $n$. W ciałach Galois stosuje się arytmetykę modularną modulo $q$.
Ciało Galois $(F_q, +_q, \cdot_q)$ możemy także oznaczać jako $\operatorname{GF}(q)$.

**Ciała proste i złożone:**
* **Ciałem prostym** nazywamy ciało $\operatorname{GF}(p)$, gdzie $p \in \mathbb{P}$. W ciałach prostych element odwrotny możemy wyznaczyć z następującego wzoru:$$ a^{-1} = a^{p-2} $$
* **Ciałem złożonym** nazywamy ciało $\operatorname{GF}(q)$, gdzie $q = p^m$, $p \in \mathbb{P}$. Tutaj do wyznaczenia elementu odwrotnego $a^{-1}$ musimy skorzystać z tabeli Cayleya działania $\cdot_q$.
## Kody liniowe
Każda podprzestrzeń $C$ przestrzeni $\operatorname{GF}(q)^n$ jest nazywana kodem liniowym. Przez $n$ będziemy oznaczać długość kodu $C$. Jeśli podprzestrzeń $C \subseteq \operatorname{GF}(q)^n$ ma wymiar $k$, to $C$ jest nazywany $q$-narnym $(n, k)$-kodem liniowym. Liczbę $(n-k)$ nazywamy redundancją kodu $C$.
 * Jeśli $C = \{0\}$ lub $C = \operatorname{GF}(q)^n$, to kod $C$ nazywamy trywialnym.
 * Jeśli kod $C = \operatorname{Lin}_{\operatorname{GF}(q)}\{c_1, \dots, c_k\}$ dla pewnych $c_1, \dots, c_k$, to elementy te nazywane są generatorami kodu $C$.
## Macierze generujące i równoważność kodów
Macierz $\mathbf{G} \in \mathbb{M}_{k,n}(\operatorname{GF}(q))$ złożoną z $k$ liniowo niezależnych wektorów $(n, k)$-liniowego kodu $C$ jest nazywana macierzą generującą kod $C$.

Niech $C$ będzie $(n, k)$-kodem liniowym oraz $\pi \in S_n$ będzie permutacją stopnia $n$ taką, że $\pi: C \rightarrow \operatorname{GF}(q)^n$. Wtedy odwzorowanie:
$$ \pi: c_1c_2\dots c_n \mapsto c_{\pi(1)}c_{\pi(2)}\dots c_{\pi(n)} $$
nazywamy permutacją pozycyjną.

Zbiór wszystkich możliwych permutacji zbioru $n$-elementowego oznaczamy jako $S_n$ i nazywamy grupą symetryczną $n$.

Dwa $(n, k)$-kody liniowe $C, C'$ nazywamy równoważnymi, jeśli jeden jest otrzymany z drugiego za pomocą skończonej liczby przekształceń:
* permutacji pozycyjnej,
* mnożenia symboli na pewnych ustalonych pozycjach we wszystkich słowach kodowych kodu $C$ przez element niezerowy.
## Macierze kontrolujące
Jeśli $\mathbf{G} \in \mathbb{M}_{k,n}(\operatorname{GF}(q))$ jest macierzą generującą kod $C$, to macierz $\mathbf{H} \in \mathbb{M}_{n-k,n}(\operatorname{GF}(q))$ spełniająca warunek:
$$ \mathbf{G H}^T = \mathbf{0}_{k,n-k} $$
jest nazywana macierzą kontrolną kodu $C$. Macierz kontrolna $\mathbf{H}$ jest także nazywana macierzą kontroli parzystości.

Dla macierzy kontrolnej $\mathbf{H}$ zachodzą własności:
* każdy układ z $d-1$ kolumn macierzy $\mathbf{H}$ jest liniowo niezależny wtedy i tylko wtedy, gdy minimalna odległość kodowa $d(C) \ge d$.
* $d(C) \le d$ wtedy i tylko wtedy, gdy istnieje układ z $d$ kolumn macierzy $\mathbf{H}$, który jest liniowo zależny.
## Przestrzenie informacyjne i pojemność
Liczby $n, k$ nazywamy kolejno długością i wymiarem kodu $C$, możemy je wyznaczyć na podstawie macierzy generującej $G$:
* $n$ jest liczbą kolumn macierzy generującej $G$,
* $k$ jest liczbą wierszy macierzy generującej $G$.

Zbiór $F_q^k$ nazywamy przestrzenią informacyjną, jest to ciąg wszystkich $k$-elementowych permutacji zbioru $F_q$.

Pojemność kodu $C$ oznaczamy przez $|C|$ i definiujemy wzorem:
$$ |C| = q^k $$

## Waga Hamminga i odległość kodowa
Liczbę niezerowych liter słowa kodowego $x$ nazywamy wagą Hamminga i oznaczamy przez $w_H(x)$.
>[!example] Przykłady
 >* $w_H(10100) = 2$
 >* $w_H(01110) = 3$
 >* $w_H(11010) = 3$
 
 **Minimalną odległością** kodową kodu $C$ nazywamy najmniejszą spośród wag Hamminga $w_H(c)$, gdzie $c \in C$. Minimalną odległość kodową kodu $C$ oznaczamy przez $d(C)$ i definiujemy wzorem:
 $$ d(C) = \min \{w_H(c) : c \ne 0, c \in C\} $$
## Zdolności kodu
**Zdolnością detekcyjną** kodu $C$ określamy, ile maksymalnie błędów może pojawić się w każdym słowie odebranym, zapewniając wciąż jednoznaczność komunikatu. Zdolność detekcyjną kodu oznaczamy literą $s$ i definiujemy wzorem:
 $$ s = d(C) - 1 $$

**Zdolnością korekcyjną** kodu $C$ określamy, ile błędów kod jest w stanie skorygować w każdym ze słów odebranych. Zdolność korekcyjną oznaczamy literą $t$ i definiujemy wzorem:
  $$ t = \left\lfloor \frac{d(C) - 1}{2} \right\rfloor $$
## Algorytm kodowania liniowego

> [!abstract] Algorytm kodowania liniowego
> 0. **Dane:** Macierz generująca $\mathbf{G} = \begin{bmatrix} c_1 \\ \vdots \\ c_\alpha \end{bmatrix} \in \mathbb{M}_{\alpha,\beta}(F_q)$.
> 1. **Wyznaczamy długość $n$ kodu $C$:** $n = \beta$, $\mathbf{G} \in \mathbb{M}_{\alpha,\beta}$.
> 2. **Wyznaczamy wymiar $k$ kodu $C$:** $k = \alpha$, $\mathbf{G} \in \mathbb{M}_{\alpha,\beta}$.
> 3. **Definiujemy przestrzeń informacyjną $(F_q)^k$:** $F_q = \{0, 1, \dots, q-1\} \implies (F_q)^k$.
> 4. **Obliczamy pojemność kodu $C$:** $|C| = q^k$.
> 5. **Szukamy słów kodowych kodu $C$:**
>    * Dla macierzy generującej $2 \times \beta$: $a = 2 \implies \begin{cases} \mathbf{c}_{1} \\  \mathbf{c}_{2}  \\  \mathbf{c}_{1}+_{q}\mathbf{c}_{2} \\  \vdots \end{cases}$
>    * Dla pozostałych kodów wyznaczamy wszystkie możliwe kombinacje wektorów $c_i$, ilość utworzonych wektorów zawsze wynosi $|C|$.
> 6. **Wyznaczamy wagi Hamminga** dla niezerowych słów kodowych $c_i \in C$: $w_H(c_1)$, $w_H(c_2)$, $w_H(c_1 + c_2)$.
> 7. **Wyznaczamy minimalną odległość kodową $d(C)$:** $d(C) = \min \{w_H(c_i) : c_i \in C \land c_i \ne 0\}$.
> 8. **Wyznaczamy zdolność detekcyjną $s$** kodu $C$: $s = d(C) - 1$.
> 9. **Wyznaczamy zdolność korekcyjną $t$** kodu $C$: $t = \left\lfloor \frac{d(C) - 1}{2} \right\rfloor$.
> 10. **Kodowanie:** Komunikat $m \in (F_q)^k$ kodujemy w słowo kodowe $c \in C$: $c = m \cdot_q G$.
> 11. **Wyznaczamy macierz kontrolną $\mathbf{H}$:** $\mathbf{G} = [\mathbf{I}_k \mid \mathbf{A}] \implies \mathbf{H} = [-_q \mathbf{A}^T \mid \mathbf{I}_{n-k}]$.
> 12. **Tworzymy tablicę Slepiana**
> 13. **Wyznaczamy syndromy liderów:** $S(x) = \mathbf{H} \cdot \mathbf{x}^T$.

