## Kod LZ78
W 1977 roku Jacob Ziv i Awraham Lempel przedstawili metodę LZ77, której główną wadą była stała wielkość słownika. Powodowało to, że zawartość okna słownikowego zmieniała się cały czas wraz z napływaniem nowych danych, przez co powtarzające się ciągi spoza okna musiały być zapamiętywane na nowo. Odpowiedzią na te ograniczenia był przedstawiony rok później **kod LZ78,** w którym słownik jest zewnętrzny i rozszerzany dynamicznie w miarę potrzeb.

Chcąc zakodować komunikat $\vec{m} \in \mathcal{A}^*$ metodą LZ78, pierwszą literę komunikatu kodujemy jako parę uporządkowaną $\langle 0, m_1 \rangle$. W kolejnych iteracjach koder poszukuje najdłuższego podciągu $s$ maksymalnej długości, który znajduje się już w słowniku $S$, i koduje go w postaci dwójki uporządkowanej $\langle p, X \rangle$, gdzie $p$ to indeks podciągu $s$ w $S$, a $X$ to litera bezpośrednio następująca po ciągu $s$.

Przez literę $S$ oznaczamy słownik. Do pracy wykorzystuje się zestawienie koder–słownik:

| Koder       | Koder                      | Słownik  | Słownik  |
| :---------- | :------------------------- | :------- | :------- |
| $s_1 = m_1$ | $\langle 0, m_1 \rangle$   | $1$      | $m_1$    |
| $s_2$       | $\langle p_2, X_2 \rangle$ | $2$      | $s_2$    |
| $\vdots$    | $\vdots$                   | $\vdots$ | $\vdots$ |
| $s_n$       | $\langle p_n, X_n \rangle$ | $n$      | $s_n$    |

> [!abstract] Algorytm kodowania LZ78
> 1. **Pierwsza iteracja:** Kodujemy pierwszą literę komunikatu $\vec{m} = m_1m_2m_3\dots$ za pomocą pary:
>    $$ c(m_1) = \langle 0, m_1 \rangle $$
> 2. **$i$-ta iteracja:** Kodujemy $i$-ty podciąg $s_i = sX$ za pomocą pary uporządkowanej $(p, X)$, gdzie:
>    - $s$ jest najdłuższym podciągiem komunikatu $\vec{m}$ takim, że $s \in S$,
>    - $p$ jest indeksem podciągu $s$ w słowniku $S$,
>    - $X$ jest literą następującą w komunikacie $\vec{m}$ po ciągu $s$.
>    
>    W przypadku gdy nie istnieje taki podciąg $s \in S$, kodujemy pierwszą literę pozostałego komunikatu za pomocą pary $(0, X)$.
> 3. **Kodowanie:** Komunikat $\vec{m}$ kodujemy za pomocą konkatenacji kodów $c(s_i)$:
>    $$ c(\vec{m}) = 0m_1 p_2 X_2 \dots p_n X_n $$

> [!example] Przykład kodowania dla $\vec{m} = \text{AAAABABBB}$
> 1. **Pierwsza iteracja:** $s = \text{A} \implies c(\text{A}) = \langle 0, \text{A} \rangle$. Słownik: indeks $1 \to \text{A}$.
> 2. **Druga iteracja:** $s = \text{A} \in S$, ale $s = \text{AA} \notin S \implies c(\text{AA}) = \langle 1, \text{A} \rangle$. Słownik: indeks $2 \to \text{AA}$.
> 3. **Trzecia iteracja:** $s = \text{A} \in S$, ale $s = \text{AB} \notin S \implies c(\text{AB}) = \langle 1, \text{B} \rangle$. Słownik: indeks $3 \to \text{AB}$.
> 4. **Czwarta iteracja:** $s = \text{AB} \in S$, ale $s = \text{ABB} \notin S \implies c(\text{ABB}) = \langle 3, \text{B} \rangle$. Słownik: indeks $4 \to \text{ABB}$.
> 5. **Piąta iteracja:** $s = \text{B} \notin S \implies c(\text{B}) = \langle 0, \text{B} \rangle$. Słownik: indeks $5 \to \text{B}$.
> 6. **Wynik ostateczny:** 
>    $$ c(\vec{m}) = \text{0A1A1B3B0B} $$
## Algorytm dekodowania LZ78
Po otrzymaniu kodu $c(\vec{m})$ proces dekodowania przebiega iteracyjnie:

> [!abstract] Algorytm dekodowania LZ78
> 1. **Pierwsza iteracja:** Dekodujemy pierwszą literę kodu $c(\vec{m}) = 0X_1 p_2 X_2 \dots p_n X_n$ jako literę $X_1$, a uzyskaną informację umieszczamy w słowniku pod indeksem 1.
> 2. **$i$-ta iteracja:** Dekodujemy każdą kolejną parę $c(s_i) = p_i X_i$ jako ciąg $S_{p_i} X_i$. Jeżeli $p_i = 0$, to parę $0 X_i$ dekodujemy jako $X_i$. Po każdym dekodowaniu dopisujemy pozycję do słownika.
> 3. **Dekodowanie:** Komunikat $\vec{m}$ odtwarzamy przez konkatenację ciągów $s_i$:
>    $$ \vec{m} = X_1 S_{p_2} X_2 \dots S_{p_n} X_n $$

> [!example] Przykład dekodowania: $c(\vec{m}) = \text{0A1A1B3B0B}$
> 1. $c(s_1) = 0\text{A} \implies s_1 = \text{A}$. Słownik: $S_1 = \text{A}$.
> 2. $c(s_2) = 1\text{A} \implies s_2 = S_1 \text{A} = \text{AA}$. Słownik: $S_2 = \text{AA}$.
> 3. $c(s_3) = 1\text{B} \implies s_3 = S_1 \text{B} = \text{AB}$. Słownik: $S_3 = \text{AB}$.
> 4. $c(s_4) = 3\text{B} \implies s_4 = S_3 \text{B} = \text{ABB}$. Słownik: $S_4 = \text{ABB}$.
> 5. $c(s_5) = 0\text{B} \implies s_5 = \text{B}$. Słownik: $S_5 = \text{B}$.
> 6. **Wynik ostateczny:**
>    $$ c^{-1}(c(\vec{m})) = \vec{m} = \text{AAAABABBB} $$
