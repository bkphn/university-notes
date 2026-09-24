## Wprowadzenie do kodu arytmetycznego
Średnia efektywność kodowania arytmetycznego jest uważana za najwyższą. Dany jest uporządkowany alfabet $\mathcal{X} = (x_1, x_2, \dots, x_n)$ o rozkładzie prawdopodobieństwa $P = (p_1, \dots, p_n)$. Każdemu ciągowi dwójkowemu $t_1t_2\dots t_m \in \{0, 1\}^*$ możemy przyporządkować liczbę wymierną $0.t_1t_2t_3\dots t_m = \frac{t_1}{2^1} + \frac{t_2}{2^2} + \dots + \frac{t_m}{2^m} \in [0, 1) \cap \mathbb{Q}$.
 
Kodowaniem arytmetycznym nazywamy odwzorowanie $c: \vec{x} \to c(\vec{x})$, gdzie $\vec{x} \in \mathcal{A}^*, c(\vec{x}) \in \{0, 1\}^{*}$. Słowo kodowe $c(\vec{x}) \in [P(\vec{x}), P(\vec{x}) + p(\vec{x})]$ jest reprezentacją dwójkową liczby naturalnej $t$, spełniającej nierówności $t-1 \le P(\vec{x}) \cdot 2^m < t$.
## Algorytm kodowania arytmetycznego
Dane jest słowo $\vec{m} = m_1m_2\dots m_t$, gdzie $m_i \in \mathcal{X}, t \in \mathbb{N} \setminus \{0\}$. Przyjmujemy, że dane są prawdopodobieństwa kumulatywne $P_t = p_1 + \dots + p_{t-1}$ oraz przedział początkowy $[L_0, R_0) = [0, 1)$.

> [!abstract] Algorytm kodowania arytmetycznego
> Dla każdego $i \in \{1, \dots, t\}$ wykonujemy: $m_i = x_k \in \mathcal{X}$. Obliczamy dolną i górną wartość granic przedziału:
> * $L_i = L_{i-1} + (R_{i-1} - L_{i-1}) \cdot P(x_{k-1})$
> * $R_i = L_{i-1} + (R_{i-1} - L_{i-1}) \cdot P(x_k)$
> 
> Komunikatowi elementarnemu $m_i$ odpowiada przedział $[L_i, R_i)$, co notujemy w postaci:
> $m_i \leftrightarrow [L_i, R_i)$
> 
> Słowo kodowe $c(\vec{m})$ wybieramy tak, aby należało do przedziału $[L_t, R_t)$. Można to zrobić na nieskończenie wiele sposobów, jednak w postaci dziesiętnej konstruujemy słowo kodowe stosując wzór:
> $$ c(\vec{m}) = \frac{L_t + R_t}{2} $$
> Następnie przepisujemy $c(\vec{m})$ w postaci dwójkowej:
> $c(\vec{m})_{(10)} = b_{(2)} = 0.b_1b_2\dots_{(2)}$
> gdzie $b_j \in \{0, 1\}$, a $\vec{b}$ jest słowem kodowym kodującym komunikat $\vec{m}$.

> [!example] Przykład kodowania: $\vec{m} = \text{GBRGA}$
> Zakoduj komunikat $\vec{m} = \text{GBRGA}$ nad alfabetem $\mathcal{A} = (\text{A, B, G, R})$ o rozkładzie prawdopodobieństw $P = (0.2, 0.4, 0.3, 0.1)$.
> 
> 0. **Inicjalizacja**
>    - $\vec{m} = m_1m_2m_3m_4m_5$
>    - $x_0 = \emptyset, x_1 = \text{A}, x_2 = \text{B}, x_3 = \text{G}, x_4 = \text{R}$
>    - $P(x_0) = 0$, $P(x_1) = 0.2$, $P(x_2) = 0.6$, $P(x_3) = 0.9$, $P(x_4) = 1$
>    - $[L_0, R_0) = [0, 1)$
> 1. **Pierwsza iteracja** ($m_1 = \text{G} = x_3$)
>    - $L_1 = L_0 + (R_0 - L_0) \cdot P(x_2) = 0.6$
>    - $R_1 = L_0 + (R_0 - L_0) \cdot P(x_3) = 0.9$
>    - $m_1 \leftrightarrow [0.6, 0.9)$
> 2. **Druga iteracja** ($m_2 = \text{B} = x_2$)
>    - $L_2 = L_1 + (R_1 - L_1) \cdot P(x_1) = 0.66$
>    - $R_2 = L_1 + (R_1 - L_1) \cdot P(x_2) = 0.78$
>    - $m_2 \leftrightarrow [0.66, 0.78)$
> 3. **Trzecia iteracja** ($m_3 = \text{R} = x_4$)
>    - $L_3 = L_2 + (R_2 - L_2) \cdot P(x_3) = 0.768$
>    - $R_3 = L_2 + (R_2 - L_2) \cdot P(x_4) = 0.78$
>    - $m_3 \leftrightarrow [0.768, 0.78)$
> 4. **Czwarta iteracja** ($m_4 = \text{G} = x_3$)
>    - $L_4 = L_3 + (R_3 - L_3) \cdot P(x_2) = 0.7752$
>    - $R_4 = L_3 + (R_3 - L_3) \cdot P(x_3) = 0.7788$
>    - $m_4 \leftrightarrow [0.7752, 0.7788)$
> 5. **Piąta iteracja** ($m_5 = \text{A} = x_1$)
>    - $L_5 = L_4 + (R_4 - L_4) \cdot P(x_0) = 0.7752$
>    - $R_5 = L_4 + (R_4 - L_4) \cdot P(x_1) = 0.77592$
>    - $m_5 \leftrightarrow [0.7752, 0.77592)$
> 6. **Kodowanie ostateczne**
>    - $c(\vec{m}) = \frac{L_5 + R_5}{2} = \frac{0.7752 + 0.77592}{2} = 0.77556$
>    - Konwersja na postać binarną (mnożenie przez 2 z wydzielaniem części całkowitych): $c(\vec{m}) = 110001101$

---

## Algorytm dekodowania arytmetycznego
Dane jest słowo kodowe $\vec{b} \in \{0, 1\}^*$ kodujące komunikat $\vec{m} = m_1m_2\dots \in \mathcal{X}^*$. W celu dekodowania słowa kodowego $\vec{b}$ konstruujemy tablicę kodową:

| $i$ | $x_i \in \mathcal{X}$ | $p_i$ | $[P(x_{i-1}), P(x_k))$ |
| :---: | :--- | :--- | :--- |
| 1 | $x_1$ | $p_1$ | $[0, p_1)$ |
| 2 | $x_2$ | $p_2$ | $[p_1, p_1 + p_2)$ |
| $\vdots$ | $\vdots$ | $\vdots$ | $\vdots$ |
| $n$ | $x_n$ | $p_n$ | $[p_1 + p_2 + \dots + p_{n-1}, 1)$ |

Następnie zapisujemy liczbę $\vec{b}_{(2)}$ w postaci dziesiętnej $T_1 = \vec{b}_{(10)}$. Szukamy takiego indeksu $s$, że $T_1 \in [p_1 + \dots + p_{s-1}, p_1 + \dots + p_{s-1} + p_s)$. Oznacza to, że pierwszym symbolem komunikatu $\vec{m}$ jest $m_1 = x_s \in \mathcal{X}$.

> [!abstract] Kroki iteracyjne dekodowania
> Dla każdego $i \in \{1, \dots, n\}$ szukamy litery $x_l = m_i$ i wyznaczamy $T_{i+1}$ korzystając ze wzoru:
> $$ T_{i+1} = \frac{T_i - P(x_{l-1})}{P(x_l) - P(x_{l-1})} $$
> Następnie wyznaczamy $m_{i+1}$ w taki sposób, że:
> $$ \exists_{r \in \{1, \dots, n\}} : T_{i+1} \in [p_1 + \dots + p_{r-1}, p_1 + \dots + p_r) \implies m_{i+1} = x_r $$

> [!example] Przykład dekodowania: $\vec{b} = 11011011$
> Zdekoduj komunikat $\vec{b} = 11011011$ który jest słowem kodowym dla komunikatu $\vec{m} = m_1m_2m_3m_4m_5$ nad alfabetem $\mathcal{X} = (A, M, R, U)$ o rozkładze prawdopodobieństw $P = (0.4, 0.1, 0.4, 0.1)$.
> 
> 0. **Inicjalizacja tablicy**
>    - $A \to [0, 0.4)$
>    - $M \to [0.4, 0.5)$
>    - $R \to [0.5, 0.9)$
>    - $U \to [0.9, 1)$
> 1. **Pierwsza iteracja**
>    - $T_1 = 0.110110111_{(2)} = 0.850586_{(10)}$
>    - $T_1 \in [0.5, 0.9) \implies m_1 = x_3 = R$
> 2. **Druga iteracja**
>    - $T_2 = \frac{T_1 - P(x_2)}{P(x_3) - P(x_2)} = \frac{0.85059 - 0.5}{0.9 - 0.5} \approx 0.876475$
>    - $T_2 \in [0.5, 0.9) \implies m_2 = x_3 = R$
> 3. **Trzecia iteracja**
>    - $T_3 = \frac{T_2 - P(x_2)}{P(x_3) - P(x_2)} = \frac{0.87647 - 0.5}{0.9 - 0.5} \approx 0.9411875$
>    - $T_3 \in [0.9, 1) \implies m_3 = x_4 = U$
> 4. **Czwarta iteracja**
>    - $T_4 = \frac{T_3 - P(x_3)}{P(x_4) - P(x_3)} = \frac{0.9411875 - 0.9}{1 - 0.9} \approx 0.411875$
>    - $T_4 \in [0.4, 0.5) \implies m_4 = x_2 = M$
> 5. **Piąta iteracja**
>    - $T_5 = \frac{T_4 - P(x_1)}{P(x_2) - P(x_1)} = \frac{0.411875 - 0.4}{0.5 - 0.4} \approx 0.11875$
>    - $T_5 \in [0, 0.4) \implies m_5 = x_1 = A$
> 6. **Wynik dekodowania**
>    - $c^{-1}(\vec{b}) = RRUMA$