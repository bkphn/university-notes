## Porządek leksykograficzny
Dane są dwa słowa $\vec{a} = a_1a_2\dots a_h$, $\vec{b} = b_1b_2\dots b_h \in \mathcal{A}^h$. Mówimy, że $\vec{a} < \vec{b}$ (w porządku leksykograficznym), jeżeli istnieje taki indeks $k \in \{1, \dots, h\}$, że:>

$$\begin{cases} a_j = b_j, & j < k \\ a_j < b_j, & j = k \end{cases}$$

## Słownik i kody słownikowe
Słownik możemy zdefiniować jako niepusty, skończony zbiór słów (wektorów): $S = (\vec{m}_1, \vec{m}_2, \dots, \vec{m}_n)$, gdzie dla każdego $i$ zachodzi $\vec{m}_i \in \mathcal{A}^{\ast}$. Słowa te posiadają swoje indeksy $i$. Słowniki mogą być statyczne lub dynamiczne (zmieniające się w procesie kodowania).

Koder rozpoczyna pracę ze słownikiem początkowym $S_0 = (d_1, d_2, \dots, d_n)$, gdzie $\forall_i d_i = a_i$, przy ustalonym porządku liter $a_1 < a_2 < \dots < a_n$. Komunikat $\vec{m} = m_1m_2\dots m_l \in \mathcal{A}^{\ast}$ jest kodowany w słowo kodowe $c(\vec{m})$.

## Kod LZ77
W 1977 roku Awraham Lempel i Jacob Ziv wynaleźli metodę kodowania, która współcześnie nazywana jest metodą LZ77. Główną ideą metody LZ77 jest to, że drugie i kolejne wchodzenia pewnego podciągu $\vec{s}$ symboli w procesie kodowania są zamieniane odwołaniami na pierwsze wchodzenie tego podciągu w $\vec{m}$.

Metoda ta używa okna ślizgającego się po komunikacie $\vec{m}$, składającego się z dwóch części:
* **Bufor słownikowy** o pojemności $l_1$.
* **Bufor kodowania** o pojemności $l_2$.

> [!abstract] Algorytm kodowania LZ77
> 1. **Inicjalizacja:** Numerujemy wszystkie pozycje okna liczbami od $0$ do $l_1 + l_2 - 1$. W buforze słownikowym umieszczamy pierwszą literę $m_1$ słowa $\vec{m}$, a bufor kodowania uzupełniamy kolejnymi literami słowa $\vec{m}$.
> 2. **$i$-ta iteracja:** Koder przeszukuje bufor słownikowy $S$ w celu znalezienia najdłuższego przedrostka $s_1$ ciągu $s$, który znajduje się w buforze kodowym.
>    * Jeżeli koder znajduje taki podciąg $s_1 \in S$, to koduje go w postaci trójki uporządkowanej $\langle p, l, X \rangle$, gdzie $p$ to numer pozycji początkowej ciągu $s_1$ w buforze $S$, $l$ to długość podciągu ($l = |s_1|$), a $X$ to pierwsza litera w buforze kodowania $s$ następująca po $s_1$.
>    * Jeżeli koder nie odnajdzie podciągu $s_1$, to koduje pierwszą literę $a$ ciągu $s$ w postaci trójki $\langle p, 0, a \rangle$, gdzie $p$ jest losowo wybraną liczbą z zakresu $[0, l_1 - 1]$.
>    * Na koniec zawartość okna przesuwamy o $l+1$ pozycji w lewo, przez co $l+1$ symboli lewostronnych zostaje usuniętych z bufora słownikowego $S$.
> 3. **Kodowanie:** Słowo $\vec{m}$ kodujemy za pomocą konkatenacji kolejnych trójek $\langle p, l, X \rangle$. Do odbiorcy przekazany musi być kod poprzedzony pierwszą literą $m_1$ słowa $\vec{m}$ ($\vec{x} = m_1 c(\vec{m})$), co jest konieczne, aby dekoder mógł rozpocząć pracę.

## Dekodowanie kodu LZ77
W dekodowaniu LZ77 okno składa się z dwóch buforów: słownikowego $S$ o pojemności $l_1$ oraz dekodowego o pojemności $l_2$. Dekodujemy komunikat $\vec{x} = m_1 c(\vec{m})$. 
W inicjalizacji bufor słownikowy $S$ wypełniamy pierwszą literą kodu $m_1$, a w buforze dekodowym umieszczamy pierwszą trójkę w postaci $\langle p, l, X \rangle$.

Następnie w każdej iteracji dekodujemy trójkę $\langle p, l, X \rangle$. Zdekodowany ciąg stanowi sekwencję następujących po sobie liter bufora słownikowego, zaczynając od $p$-tego indeksu, po którym należy umieścić literę $X$. Potem przesuwamy bufor o $l+1$ pozycji w lewo i do bufora kodowania wpisujemy kolejną trójkę.
