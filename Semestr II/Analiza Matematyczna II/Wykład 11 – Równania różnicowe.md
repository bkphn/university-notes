## Równania różnicowe
Równaniem różnicowym nazywamy równanie wiążące ze sobą ogólny wyraz ciągu $a_n$ z jego wcześniejszymi elementami $a_{n-k}$. W równaniach różnicowych często stosuje się zapis $a(n)$ zamiast $a_n$. Równanie często ma również podane warunki początkowe $a(0) = \alpha, \dots$, które pozwalają nam na obliczenie ogólnego wyrazu ciągu.
## Funkcja sterująca i impulsowa
* **Funkcję $s(n)$** nazywamy impulsową, jeżeli wysyła dwa różne sygnały (wartości) w zależności od argumentu.
* **Funkcję $p(n)$** nazywamy sterującą, jeżeli jej działanie wynika z wymuszenia (lewej strony równania różnicowego). Znając wzór funkcji impulsowej, jesteśmy w stanie wyznaczyć funkcję sterującą.

> [!example] Przykład wyznaczenia funkcji sterującej
> Niech $p(n) = s(n+2) - 2s(n+1) + s(n)$, gdzie $s(n) = \frac{1}{2}(1 + (-1)^n)$.
> Po rozpisaniu wartości dla parzystych i nieparzystych $n$:
> $$ s(n) = \begin{cases} \frac{1}{2}(1+1), & 2 \mid n \\ \frac{1}{2}(1-1), & 2 \nmid n \end{cases} \implies s(n) = \begin{cases} 1, & 2 \mid n \\ 0, & 2 \nmid n \end{cases} $$
> Podstawiając do wzoru na $p(n)$:
> $$ p(n) = s(n+2) - 2s(n+1) + s(n) = \begin{cases} 1 - 2 \cdot 0 + 1, & 2 \mid n \\ 0 - 2 \cdot 1 + 0, & 2 \nmid n \end{cases} \implies p(n) = \begin{cases} 2, & 2 \mid n \\ -2, & 2 \nmid n \end{cases} $$
> Ostatecznie funkcja sterująca przyjmuje postać: $p(n) = 2(-1)^n$.

## Schemat rozwiązywania równań różnicowych

> [!example] Przykład z rozwiązaniem krok po kroku
> Rozwiąż równanie różnicowe $s(n+1) - 4s(n) = 12u(n)$ z warunkiem początkowym $s(0) = 0$.
> 1. **Zapisanie równania wyjściowego:** $s(n+1) - 4s(n) = 12u(n)$.
> 2. **Nałożenie transformaty Z na obie strony:** $\mathcal{Z}[s(n+1) - 4s(n)] = \mathcal{Z}[12u(n)] \implies \mathcal{Z}[s(n+1)] - 4\mathcal{Z}[s(n)] = 12\mathcal{Z}[u(n)]$.
> 3. **Wykorzystanie własności przesunięcia:** $z(F(s) - s(0)) - 4F(s) = 12 \frac{z}{z-1} \implies F(s)z - 0 - 4F(s) = 12 \frac{z}{z-1}$.
> 4. **Przekształcenie algebraiczne w celu wyznaczenia $F(s)$:** $F(s)(z - 4) = 12 \frac{z}{z-1} \implies F(s) = \frac{12z}{(z-1)(z-4)}$.
> 5. **Rozkład na ułamki proste:** $F(s) = \frac{12z}{(z-1)(z-4)} = \frac{A}{z-1} + \frac{B}{z-4}$.
> 6. **Wyznaczenie współczynników $A$ i $B$:** $A(z-4) + B(z-1) = 12z$, co prowadzi do układu równań $\begin{cases} A + B = 12 \\ -4A - B = 0 \end{cases} \implies \begin{cases} A = -4 \\ B = 16 \end{cases}$.
> 7. **Zapisanie funkcji w postaci rozbitej:** $F(s) = \frac{-4}{z-1} + \frac{16}{z-4}$.
> 8. **Zastosowanie odwrotnej transformaty Z:** $\mathcal{Z}^{-1}[F(s)] = \mathcal{Z}^{-1}\left[\frac{-4}{z-1} + \frac{16}{z-4}\right] \implies s(n) = -\mathcal{Z}^{-1}\left[\frac{4}{z-1}\right] + \mathcal{Z}^{-1}\left[\frac{16}{z-4}\right]$.
> 9. **Przekształcenie składników do postaci tabelarycznej:** 
>    * $\frac{4}{z-1} = 4 \cdot \frac{1}{z-1} = \sum_{n=1}^{\infty} 4 \cdot \left(\frac{1}{z}\right)^n \implies \bar{s}(n) = 4 \cdot 1^n = 4$
>    * $\frac{16}{z-4} = 4 \cdot \frac{4}{z-4} = \sum_{n=1}^{\infty} 4 \cdot \left(\frac{4}{z}\right)^n \implies \bar{\bar{s}}(n) = 4 \cdot 4^n$
> 10. **Otrzymanie ostatecznego rozwiązania ciągu:** $s(n) = -\bar{s}(n) + \bar{\bar{s}}(n) \implies s(n) = -4 + 4 \cdot 4^n$.