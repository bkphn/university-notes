## Archiwizacja, Format i Kodek
* **Archiwizacja danych:** Proces katalogizowania i kompresji danych.

* **Format:** Ustalony standard zapisu danego pliku – sposób zakodowania informacji. Wyróżnia się m.in. formaty graficzne:
	  `.gif` (Graphics Interchange Format): Wykorzystuje algorytm LZW, jest przykładem grafiki rastrowej.
	  `.jpeg` (Joint Photographics Experts Group): Skompresowany plik graficzny, obsługuje $2^{24}$ kolorów.
	  `.bmp` (Bitmap): Popularny w systemie Windows, przechowuje obraz jako bitmapę pikseli.
	 `.png` (Portable Network Graphics).
	 `.raw` (Raw): Piksele opisywane jako ciągi szesnastkowe.

- **Kodek:** Program do kodowania i dekodowania danych ($\text{Kodek} = \text{Koder} + \text{Dekoder}$).

## Kod LZW
Zaproponowana przez Terry'ego Welcha metoda kodowania LZW opiera się na kodzie LZ78. Współcześnie LZW jest używane w formatach takich jak `.pdf` czy `.gif`. Kod LZW jest najoptymalniejszym z kodów słownikowych, w którym zakodowany ciąg odpowiada tylko jednemu znakowi:
 * **LZ77:** $c: s \mapsto \langle p, l, X \rangle$
 * **LZ78:** $c: s \mapsto \langle p, X \rangle$
 * **LZW:** $c: s \mapsto p$
W odróżnieniu do kodów LZ77 i LZ78, korzystanie z LZW wymagało uiszczenia opłaty za patent.

Chcąc zakodować komunikat $\vec{m} = m_1 \dots m_k \in \mathcal{A}^{\ast}$, wpisujemy do słownika $S$ wszystkie litery alfabetu $\mathcal{A} = \{a_1, \dots, a_n\}$ o indeksach $1, \dots, n$.

> [!abstract] Kroki kodowania LZW
> 1. Koder wczytuje pierwszą literę komunikatu $s_1 = m_1$ i koduje ją w postaci jej indeksu $i$. Hasło $s_1 m_2$ wpisujemy do słownika $S$ pod indeksem $n+1$.
> 2. Załóżmy, że $s_h$ znajduje się w słowniku na pozycji $j$, a $s_h m_{h+1} \notin S$. Wtedy kodujemy ciąg $s_h$ jako $j$, a hasło $s_h m_{h+1}$ wpisujemy do słownika pod odpowiednim indeksem.
> 3. **Kodowanie ostateczne:** 
>
>    $$c(\vec{m}) = \bigcup_{j} c(s_j)$$
>

> [!example] Przykład kodowania dla $\vec{m} = \text{AAABBCAAA}$
> * Alfabet początkowy $\mathcal{A} = \{\text{A, B, C}\}$ otrzymuje indeksy $1, 2, 3$.
> * Po przeanalizowaniu kolejnych par i dopisywaniu nowych fraz do słownika, wynikiem kodowania jest ciąg indeksów:
>
>   $$c(\vec{m}) = 1422341$$
>

## Algorytm dekodowania LZW
Proces dekodowania opiera się na dynamicznym odtwarzaniu i rozbudowie słownika po stronie odbiorcy.

> [!abstract] Kroki dekodowania LZW
> 1. Wpisujemy litery alfabetu $\mathcal{A} = \{a_1, \dots, a_n\}$ do słownika pod indeksami $1$ do $n$.
> 2. **i-ta iteracja:** Dekodujemy $i$-tą literę $\rho_i$ kodu $\vec{c}$:
>    * Jeżeli istnieje $s_h$ taki, że $\rho_i = p(s_h)$, to $s_i = s_h$.
>    * Jeżeli dany indeks nie występuje w słowniku, dodajemy do słownika konkatenację poprzedniego zdekodowanego ciągu z jego pierwszą literą pod kolejnym indeksem, a następnie dekodujemy brakujący element.
> 3. **Dekodowanie ostateczne:** 
>
>    $$c^{-1}(\vec{c}) = \bigcup_{j} s_j$$
>

> [!example] Przykład dekodowania dla $\vec{c} = 1422341$
> * Alfabet początkowy $\mathcal{A} = \{\text{A, B, C}\}$.
> * Po przetworzeniu kolejnych symboli kodu i dynamicznym uzupełnianiu słownika (w tym obsłudze brakującego indeksu 4 w drugiej iteracji), otrzymujemy odtworzony komunikat:
>
>   $$c^{-1}(\vec{c}) = \text{AAABBCAAA}$$
>
