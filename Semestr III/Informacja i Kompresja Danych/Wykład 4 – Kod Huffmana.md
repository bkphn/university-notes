## Źródło zredukowane
Dane jest źródło $S = (\mathcal{A}, P)$ z alfabetem $\mathcal{A} = (a_1, \dots, a_q)$ oraz rozkładem $P = (p_1, \dots, p_q)$. 

Źródłem zredukowanym $S'$ nazywamy parę $(\mathcal{A}', P')$ taką, że alfabet $\mathcal{A}' = (a_1, \dots, a_{q-2}, a_{q-1}')$, a rozkład prawdopodobieństw to $P' = (p_1, \dots, p_{q-2}, p_{q-1}')$, gdzie:
$$a_{q-1}' = a_{q-1}a_q,$$
$$p_{q-1}' = p_{q-1} + p_q$$
Z źródłami zredukowanymi mamy do czynienia m.in. w kodowaniu Huffmana, gdzie w kolejnych iteracjach konkatenacja dwóch liter o najmniejszym prawdopodobieństwie daje nowy element o prawdopodobieństwie równym sumie ich prawdopodobieństw.
## Kod a
Kodowanie a opracowane przez David Huffmana w 1952 roku jest jedną z najprostszych do implementacji metod kompresji, dzięki temu jest powszechnie stosowana w systemach komputerowych. Kompresja MP3 czy JPEG korzystają z kodowania Huffmana.

> [!abstract] Algorytm kodu Huffmana
> 1. **Porządkujemy alfabet $\mathcal{A}$** w kolejności nierośnięcia ich prawdopodobieństw: $\mathcal{A} = \{a_1, \dots, a_n\} \iff p(a_1) \ge \dots \ge p(a_n)$.
> 2. **Łączymy litery o najmniejszym prawdopodobieństwie**, przy czym literze o mniejszym prawdopodobieństwie przypisujemy bit $1$, a tej o większym bit $0$.
> 3. **Z nowo powstałego zbioru ponownie łączymy litery** o najmniejszym prawdopodobieństwie i powtarzamy przypisywanie bitów.
> 4. **Powtarzamy czynność** do momentu uzyskania jednoelementowego zbioru.
> 5. **Konkatenacja bitów** przypisanych do każdej z liter na ścieżce od korzenia do liścia stanowi jej kod końcowy.
