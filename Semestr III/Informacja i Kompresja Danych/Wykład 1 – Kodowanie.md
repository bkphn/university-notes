## Rodzaje kodowania
> * **Kodowanie nadmiarowe (korygujące błędy):** Polega na dodawaniu do informacji nadmiarowych bitów, służących kontroli błędów (np. kod parzystości).
> * **Kodowanie ekonomiczne (kompresja):** Polega na przekształceniu ciągu symboli / liter w krótszy ciąg, przy zachowaniu możliwości odtworzenia oryginału. Wyróżnia się kompresję bezstratną oraz stratną (np. MP3).
> * **Kodowanie w celu ukrycia treści (kryptografia):** Polega na przekształceniu (szyfrowaniu) informacji w taki sposób, że staje się ona nieczytelna bez odpowiedniego klucza.

**Tekstem jawnym** (otwarty) nazywamy tekst dostępny dla wszystkich. **Komunikat** (wiadomość, meldunek, jednostka informacji) jest podstawową jednostką informacji jawnej.

## Źródła
Dana jest para $S = (\mathcal{A}, P)$, gdzie $\mathcal{A} = \{a_1, a_2, \dots, a_q\}$ to alfabet, a $P = (p_1, p_2, \dots, p_q)$ to rozkład prawdopodobieństw zdarzeń $a_i \in \mathcal{A}$ taki, że $\forall_i p_i = p(a_i)$ oraz $\sum_{i=1}^q p_i = 1$. Parę tę nazywamy **źródłem nad alfabetem** $\mathcal{A}$.

Jeżeli alfabet $\mathcal{A}$ jest zbiorem zawierającym wartości $0, 1$, to źródło nad alfabetem $\mathcal{A}={0, 1}$  nazywamy źródłem dwójkowym.

Źródło $S=(\mathcal{A}),P)$ nazywane jest źródłem dyskretnym bezpamięciowym jeżeli dla dowolnych $a_m\in \mathcal{A}$ zachodzi:

$$p(a_{m_{1}},a_{m_{2}},\dots,a_{m_{k}})=\prod_{i=1}^k a_{m_{i}}$$

## Kodowanie i Dekodowanie
**Kodowaniem** nazywamy funkcję $c: \mathcal{A} \rightarrow \mathcal{B}^{\ast}$ przyporządkowującą litery alfabetu $\mathcal{A}$ słowom z alfabetu $\mathcal{B}$. Słowo $c(a)$ nazywamy słowem (wektorem) kodowym.

**Funkcję rozszerzenia** $\overline{c}: \mathcal{A}^{\ast} \rightarrow \mathcal{B}^{\ast}$ definiujemy jako:

$$\overline{c}(a_{i_1}a_{i_2}\dots a_{i_k}) = c(a_{i_1})c(a_{i_2})\dots c(a_{i_k})$$

* $\mathcal{A}$ – alfabet wejściowy.
* $\mathcal{B}$ – alfabet wyjściowy (kodowania).
* **Dekodowanie:** Funkcja odwrotna $\overline{c}^{-1}: \mathcal{B}^{\ast} \rightarrow \mathcal{A}^{\ast}$.
* Kodowanie jest jednoznacznie dekodowalne, jeżeli funkcja $c$ jest iniekcją.

## Kody
Zbiór $C = \operatorname{Im}_c = \{c(a_1), c(a_2), \dots, c(a_n)\} \subseteq \mathcal{B}^{\ast}$ nazywamy kodem, a wartość $l_{i}=l(c_{i})$ nazywamy długością słowa kodowego. Średnią długość słowa kodowego oznaczamy przez $l(C)$ i definiujemy następująco:

$$l(C) = \sum_{i=1}^n p_i \cdot l_i$$

### Kody powtórzeniowe
Zbiór $C = \{a_1a_1\dots a_1, a_2a_2\dots a_2, \dots, a_nan\dots a_n\}$ nazywamy kodem powtórzeniowym, o długości $n$ określającej liczbę powtórzeń każdego elementu (np. dla $\mathcal{A} = \{0, 1\}$ i $n=3$: $C = \{000, 111\}$).

### Szyfr Cezara
Szyfrem Cezara nazywamy szyfr przesuwający, który dla każdej litery $a_i$  z alfabetu $\mathcal{A}$ przyporządkowuje literę $a_{i+k}$. Wartość $k$ nazywana jest kluczem szyfru i określa o ile pozycji ma zmienić się alfabet wyjściowy.

Nazwa szyfr Cezara pochodzi od rzymskiego wodza i polityka Juliusza Cezara, który wykorzystywał szyfr Cezara do szyfrowania korespondencji do przyjaciół. Juliusz Cezar używał klucza $k=3$.

### Kody przedrostkowe
* **Przedrostek (prefiks):** Dla słowa $\vec{a} = a_1a_2\dots a_n$, przedrostkiem jest słowo $a_1a_2\dots a_i$ ($i \in \{1, \dots, n\}$). Słowo $\vec{a}$ jest przedrostkiem niewłaściwym.
* **Kod bezprzedrostkowy:** Kod, w którym żadne słowo $\vec{x} \in C$ nie jest przedrostkiem innego słowa $\vec{y} \in C$.

### Kody zwięzłe i optymalne
* Kodowanie $c$ jest nazywane **zwięzłym**, jeśli kod $C$ jest jednoznacznie dekodowalny oraz dla każdego innego kodowania $c_1$ zachodzi $l(C) \le l(C_1)$.
* W zwięzłym kodzie wiadomość o najmniejszym prawdopodobieństwie jest kodowana w najdłuższe słowo ($p(\vec{a}_i) > p(\vec{a}_j) \Rightarrow l(c(\vec{a}_i)) < l(c(\vec{a}_j))$).
* Kod zwięzły nazywamy **optymalnym**, jeśli zachodzi równość:

  $$l(C) = \frac{H(\mathcal{A})}{\log_2 |\mathcal{A}|}$$

