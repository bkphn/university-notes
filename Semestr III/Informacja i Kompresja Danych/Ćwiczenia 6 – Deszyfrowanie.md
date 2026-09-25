## Deszyfrowanie kodów afinicznych
Do deszyfrowania kodów afinicznych wykorzystuje się relację odwrotności współczynnika $a$ w zbiorze ${Z}_q$. Wzór deszyfrowania przyjmuje postać:

$$D_l(\vec{c}) = a^{-1}(\vec{c} - b) \pmod q$$

 gdzie $a^{-1} = \alpha$ spełnia warunek $a \cdot \alpha \equiv 1 \pmod q$.

## Algorytm dekodowania kodu afinicznego

> [!abstract] Algorytm dekodowania kodu afinicznego
>1. **Dane:** Kryptogram $\vec{c} = c_1c_2\dots c_n$, klucz $k = (a, b)$, zbiór kryptogramów $\mathcal{C} = \mathbb{Z}_q$.
>2. **Zamiana na liczby:** Zapisujemy kryptogram za pomocą wartości numerycznych odpowiadających literom alfabetu $\mathcal{C}$.
>3. **Wyznaczenie odwrotności:** Znajdujemy element odwrotny $a^{-1}$ taki, że $a \cdot a^{-1} \equiv 1 \pmod q$.
>4. **Deszyfrowanie:** Dla każdego elementu kryptogramu $z_i$ obliczamy wartość deszyfrowaną:
>
>$$m_i = a^{-1}(z_i - b) \pmod q$$
>
>5. **Zapis ostateczny:** Mapujemy otrzymany ciąg liczbowy z powrotem na litery alfabetu pierwotnego $\mathcal{A}$.

> [!example] Przykład: Rozszyfrowanie $\vec{c} = \text{ZIUZIA}$
> 1. **Dane:** $\vec{c} = \text{ZIUZIA}$, klucz $k = (15, 6)$ w przestrzeni $\mathcal{C} = \mathcal{M} = {Z}_{32}$.
> 2. **Wartości numeryczne kryptogramu:** $29, 11, 26, 29, 11, 00$.
> 3. **Odwrotność:** Dla $a = 15$ w ${Z}_{32}$ otrzymujemy $15^{-1} = 15$, ponieważ $15 \cdot 15 = 225 \equiv 1 \pmod{32}$.
> 4. **Obliczenia deszyfrujące dla poszczególnych znaków:**
> $c_1 = 29 \implies m_1 = 15(29 - 6) = 345 \equiv 25$
> $c_2 = 11 \implies m_2 = 15(11 - 6) = 75 \equiv 11$
> $c_3 = 26 \implies m_3 = 15(26 - 6) = 300 \equiv 12$
> $c_4 = 29 \implies m_4 = 15(29 - 6) = 345 \equiv 25$
> $c_5 = 11 \implies m_5 = 15(11 - 6) = 75 \equiv 11$
> $c_6 = 00 \implies m_6 = 15(0 - 6) = 15 \cdot 26 = 384 \equiv 6$
> 5. **Wynik:** Odtworzony komunikat $\vec{m} = 251112251106$ po zmapowaniu daje wynik tekstowy.

## Deszyfrowanie szyfru Playfair
Deszyfrowanie kodów Playfair odbywa się w sposób analogiczny do szyfrowania, z tą różnicą, że **zmieniamy kierunek wykonywania przesunięć** w tabeli liter.

> [!example] Przykład: Zdeszyfrowanie $\vec{c} = \text{CPQSPENZMVPI}$
> * **Analiza par:** Poszczególne pary liter kryptogramu analizowane są względem tabeli szyfrów.
> * **Kierunki przesunięć:** Dla liter leżących w poziomach, pionach lub na skos stosuje się odwrotne reguły przesunięć, uwzględniając wstawione znaki pomocnicze.
> * **Wynik:** Ostateczny odszyfrowany ciąg po usunięciu znaków uzupełniających.

