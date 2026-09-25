
## Kompresja danych
**Kompresja** to funkcja polegająca na przekształceniu ciągu symboli lub liter w krótszy ciąg przy zachowaniu możliwości odtworzenia oryginału.
* **Kompresja bezstratna:** Istnieje funkcja odwrotna $c^{-1}(c(a)) = a$, co pozwala na dekompresję i odtworzenie 100% oryginału.
* **Kompresja stratna:** Brak możliwości pełnego odtworzenia informacji (często stosowana w plikach muzycznych lub filmowych, gdzie spadek jakości nie jest zbytnio zauważalny).
* **Kompresja statyczna:** Rodzaj kompresji, w którym alfabet wyjściowy pozostaje niezmieniony, a najczęściej spotykanym alfabetem wyjściowym jest $\mathcal{B} = \{0, 1\}$.

## Efektywność kodu
Efektywność kodu $C \subseteq \{0,1\}^{\ast}$ kodującego litery alfabetu $\mathcal{A} = \{a_1, \dots, a_n\}$ oznaczamy jako $\mathrm{ef}(C)$ i definiujemy wzorem:

$$\mathrm{ef}(C) = \frac{H(\mathcal{A})}{l(C)} \cdot 100\%$$

gdzie średnia długość słów kodowych $l(C)$ dana jest wzorem:

$$l(C) = \sum_{i=1}^n l_i \cdot p_i$$

## Prawdopodobieństwo kumulatywne
Prawdopodobieństwo $P_i$ nazywane jest prawdopodobieństwem kumulatywnym i definiuje się je wzorem:

$$P_i = \sum_{j=1}^{i-1} p_j$$

## Kod Shannona
Kod Shannona jest metodą kompresji bezstratnej zaprezentowaną przez Claude'a Shannona, która nie jest kodem optymalnym.

> [!abstract] Algorytm kodu Shannona
> 1. **Porządkujemy alfabet $\mathcal{A}$** w kolejności nierośnięcia prawdopodobieństw: $\mathcal{A} = \{a_1, \dots, a_n\} \iff p(a_1) \ge \dots \ge p(a_n)$.
> 2. **Konstruujemy prawdopodobieństwa kumulatywne**: $P_1 = 0$, $P_2 = p_1$, ..., $P_n = p_1 + \dots + p_{n-1}$.
> 3. **Obliczamy długości słów kodowych $l_i$**: $l_1 = \lceil -\log_2 p_1 \rceil, \dots, l_n = \lceil -\log_2 p_n \rceil$.
> 4. **Przekształcamy prawdopodobieństwa $P_i$ na postać binarną**, z dokładnością do $l_i$ liczb po przecinku.
> 5. **Kodowanie za pomocą otrzymanych wartości**: wyznaczanie słów kodowych $c(a_i)$.

## Dekodowanie kodu Shannona
Po wypełnieniu tabeli można przejść do dekodowania. Polega ono na analizowaniu kolejnych liter zakodowanego słowa $c(\vec{a})$ i sprawdzaniu, czy dany prefiks znajduje się w kodzie $C$ ($c(a_1 \dots a_q) \in C \implies a_1 \dots a_q = m_1$).
