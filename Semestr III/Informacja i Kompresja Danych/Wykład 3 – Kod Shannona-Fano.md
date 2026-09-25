## Kodowanie Shannona-Fano
> Kodowanie Shannona-Fano to metoda kompresji bezstratnej wynaleziona równolegle przez Claude'a Shannona i Roberta Fano. Kodowanie to jest zbliżone do optymalnego. Podobnie jak kodowanie Huffmana, można je przedstawić za pomocą drzewa binarnego.

> [!abstract] Algorytm kodu Shannona-Fano
> 1. **Porządkujemy alfabet $\mathcal{A}$** w kolejności nierośnięcia ich prawdopodobieństw: $\mathcal{A} = \{a_1, \dots, a_n\} \iff p(a_1) \ge \dots \ge p(a_n)$.
> 2. **Dzielimy zbiór** (jeśli posiada przynajmniej dwa elementy) na dwa podzbiory według wszystkich możliwych konfiguracji, zachowując kolejność prawdopodobieństw.
> 3. **Szukamy takiej pary zbiorów $s_1, s_2$**, że różnica sum prawdopodobieństw jest najmniejsza: $\min(\{m_1, \dots, m_{n-1}\}) = q$, co daje podział $s_1 = \{a_1, \dots, a_q\}$ oraz $s_2 = \{a_{q+1}, \dots, a_n\}$.
> 4. **Przyporządkowujemy bity**: dla każdego elementu ze zbioru $s_1$ przypisujemy bit $1$, a dla elementów ze zbioru $s_2$ przypisujemy bit $0$.
> 5. **Powtarzamy kroki** dla każdego ze zbiorów $s_1, s_2$ aż do momentu dotarcia do pojedynczego elementu.

## Dekodowanie kodu Shannona-Fano
Dekodowanie przebiega analogicznie do kodu Shannona i polega na analizowaniu kolejnych liter zakodowanego słowa $c(\vec{a})$ w celu sprawdzenia, czy dany fragment należy do kodu $C = \operatorname{Im}(c)$:
* Jeśli $c(a_1) \notin C$, sprawdzamy kolejne znaki.
* Jeżeli $c(a_1 \dots a_q) \in C$, oznacza to, że odnaleziono prefiks kodujący komunikat $m_1$.
