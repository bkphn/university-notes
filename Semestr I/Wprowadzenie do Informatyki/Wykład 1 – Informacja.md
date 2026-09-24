
## Informatyka
**Informatyka** jest nauką o przechowywaniu, przetwarzaniu i przesyłaniu informacji. Do organizacji tych procesów służą systemy informatyki. Komputery są systemami informatyki o określonym sposobie zapisu informacji i algorytmów opierając się na odpowiedniej strukturze urządzeniowej.

**Informacją**, zgodnie ze ścisłym podejściem, nazywamy pewną wartość fizyczną lub strukturalną obiektów. Własność ta stanowi wyróżnienie tego obiektu ze zbioru innych obiektów.
## Alfabet i prawdopodobieństwo
Przyjmijmy, że istnieje zbiór wydarzeń $S = \{x_1, x_2, \dots, x_n\}$. Zbiór $S$ nazywamy **alfabetem**, jeżeli każdy element $x_i$ jest symbolem (np. literą) używanym do konstruowania komunikatów.

Przyjmijmy również, że prawdopodobieństwo $p$ każdego wydarzenia jest znane, więc $p(x_i) = p_i$. Zbiór $P = \{p_1, p_2, \dots, p_n\}$ nazywamy zbiorem prawdopodobieństwa wydarzeń $S$. Suma wszystkich prawdopodobieństw jest równa 100%:
$$ \sum_{i=1}^{n} p_i = 1 $$
## Autoinformacja i rodzaje logarytmów
Jeżeli każde z wydarzeń $x_i$ jest niezależne od reszty, to możemy wprowadzić pojęcie **informacji własnej $I$**, zwanej również **entropią indywidualną**. Entropia odzwierciedla stopień nieuporządkowania informacji i zmienia się odwrotnie proporcjonalnie do prawdopodobieństwa. 
Oblicza się ją ze wzoru (dla $k > 0, k \ne 1$):
$$ I(x_i) = -\log_k p_i $$

W zależności od wybranej podstawy logarytmu ($k$) otrzymujemy inną jednostkę informacji:

| Podstawa |    Zapis    | Nazwa logarytmu     | Jednostka informacji |
| :------: | :---------: | :------------------ | :------------------- |
|   $2$    | $\text{lb}$ | logarytm binarny    | bit (binary digit)   |
|   $3$    |      -      | -                   | trit                 |
|   $10$   | $\text{lg}$ | logarytm dziesiętny | hartley              |
|   $e$    | $\text{ln}$ | logarytm naturalny  | nat                  |
## Obliczanie Entropii

> [!example] Oblicz ile bitów informacji wyniesie wybranie każdej z opcji
> Dla alfabetu $S = \{x_1, x_2, x_3, x_4\}$ oraz zbioru prawdopodobieństw $P = \left\{\frac{1}{2}, \frac{1}{4}, \frac{1}{8}, \frac{1}{8}\right\}$.
> $$I(x_1) = -\text{lb}\left(\frac{1}{2}\right) = \text{lb} \, 2 = 1 \text{ bit}$$
> $$I(x_2) = -\text{lb}\left(\frac{1}{4}\right) = 2 \text{ bity}$$
> $$I(x_3) = I(x_4) = -\text{lb}\left(\frac{1}{8}\right) = 3 \text{ bity}$$
## Entropia stowarzyszona
Często istnieje potrzeba obliczenia entropii całego zbioru lub alfabetu. **Entropią stowarzyszoną** $H(S)$ nazywamy miarę nieuporządkowania danego zbioru, co definiujemy wzorem:
$$ H(S) = \sum_{i=1}^{n} p_i \cdot I(x_i) $$
## Kodowanie Huffmana
Jednym ze sposobów konstruowania kodu spełniającego warunki jednoznacznej dekodowalności jest metoda Huffmana. Rozważać będziemy źródło $S$ emitujące sygnały $a_i$ z prawdopodobieństwem wystąpienia symbolu równego $p_i$.

> [!abstract] Algorytm kodu Huffmana
> 1. **Porządkujemy alfabet $S$** w kolejności nierośnięcia ich prawdopodobieństw: $S = \{a_1, \dots, a_n\} \iff p(a_1) \ge \dots \ge p(a_n)$.
> 2. **Łączymy litery o najmniejszym prawdopodobieństwie**, przy czym literze o mniejszym prawdopodobieństwie przypisujemy bit $1$, a tej o większym bit $0$.
> 3. **Z nowo powstałego zbioru ponownie łączymy litery** o najmniejszym prawdopodobieństwie i powtarzamy przypisywanie bitów.
> 4. **Powtarzamy czynność** do momentu uzyskania jednoelementowego zbioru.
> 5. **Konkatenacja bitów** przypisanych do każdej z liter na ścieżce od korzenia do liścia stanowi jej kod końcowy.