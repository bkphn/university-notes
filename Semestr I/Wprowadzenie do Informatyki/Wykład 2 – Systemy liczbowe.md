## Liczba
Liczba jest pojęciem abstrakcyjnym używanym do porównywania wielkości zbiorów i wielkości ciągłych. W systemach informatyki nabiera ona wartości informacyjnej i jest wygodnym oraz uniwersalnym nośnikiem informacji.
## System liczbowy
**System liczbowy** to zestaw zasad umożliwiających przedstawianie liczb za pomocą umownych symboli (cyfr) oraz zbiór reguł umożliwiających wykonywanie na nich działań.

Systemy liczbowe możemy podzielić na:
*   **Addytywne:** Liczby tworzy się przez dodawanie kolejnych symboli (np. rzymski system liczbowy).
*   **Pozycyjne:** Posiadają $p-1$ cyfr, gdzie $p$ to podstawa systemu. Wartość symbolu obliczamy w zależności od jego pozycji w liczbie.
## Systemy pozycyjne
W systemach o podstawie $p$ dowolną liczbę $X$ możemy przedstawić w postaci wielomianu:
$$ X = x_{n-1}p^{n-1} + \dots + x_1 p + x_0 + x_{-1}p^{-1} + \dots + x_{-m}p^{-m} = \sum_{i=-m}^{n-1} x_i p^i $$
gdzie:
*   $p$ – podstawa systemu liczbowego.
*   $n$ – liczba cyfr części całkowitej liczby $X$.
*   $m$ – liczba cyfr części ułamkowej liczby $X$.

Znając te wartości, możemy wyliczyć parametry skrajne (dla liczb nieujemnych):
*   **Wartość maksymalna:** $X_{\text{max}} = p^n - p^{-m}$.
*   **Wartość minimalna:** $X_{\text{min}} = p^{-m}$.
*   **Pojemność** (liczba różnych liczb $n+m$ cyfrowych): $\frac{X_{\text{max}}}{X_{\text{min}}} = p^{n+m} - 1$.
## Przegląd najpopularniejszych systemów pozycyjnych

| System                            | Podstawa | Zbiór cyfr                                                                    | Zastosowanie i właściwości                                                                                                                                                                                                                                                                 |
| :-------------------------------- | :------: | :---------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Dziesiętny**                    |   $10$   | $\{0, 1, \dots, 9\}$                                                          | Tradycyjny system zapisu, w którym $X = \sum_{i=-m}^{n-1} x_i \cdot 10^i$.                                                                                                                                                                                                                 |
| **Dwójkowy (binarny)**            |   $2$    | $\{0, 1\}$                                                                    | Powszechnie stosowany w maszynach cyfrowych ze względu na łatwą reprezentację sprzętową (1 = przepływ prądu, 0 = brak prądu). W logice dodatniej 1 to napięcie powyżej $2.4 \text{ V}$, a 0 to napięcie poniżej $0.8 \text{ V}$. Ciąg 8 bitów to jeden bajt ($1 \text{ B} = 8 \text{ b}$). |
| **Ósemkowy**                      |   $8$    | $\{0, 1, \dots, 7\}$                                                          | Stosowany kiedyś do skracania długich zapisów systemu binarnego, obecnie wypierany przez system szesnastkowy.                                                                                                                                                                              |
| **Szesnastkowy (heksadecymalny)** |   $16$   | $\{0, \dots, 9, \text{A}, \text{B}, \text{C}, \text{D}, \text{E}, \text{F}\}$ | Powszechny we współczesnej informatyce do skracania ciągów binarnych (pojedynczy bajt skraca się do dwóch cyfr szesnastkowych). Używany np. do opisu kolorów RGB w HTML (poprzedzony znakiem `#`).                                                                                         |
## Przekształcanie systemów liczbowych
Podstawę systemu liczbowego często zapisuje się w indeksie dolnym obok danej liczby (np. $2025_{(10)}$, $110_{(2)}$).

> [!abstract] Schemat zamiany systemów liczbowych $10\rightarrow p$
>1. Podzielenie z resztą liczby przez podstawę: $a : p = a_1 + b_1 \rightarrow b_1$.
>2. Bierzemy całkowitą część i powtarzamy algorytm: $a_1 : p = a_2 + b_2 \rightarrow b_2$.
>3. Powtarzamy do momentu, gdy $a_n = 0$: $a_{n-1} : p = 0 + b_n \rightarrow b_n$.
>4. Konkatenacja wartości $b_i$ stanowi liczbę w nowej podstawie: $b = b_n b_{n-1} \dots b_2 b_1$.

>[!abstract] Schemat zamiany systemów liczbowych $p \rightarrow 10$
>1. Rozpisanie potęg podstawy ($p^0, p^1, p^2, \dots, p^n$).
> 2. Dla dowolnej liczby $b = b_1 b_2 \dots b_n$ mnożymy każdą cyfrę przez odpowiadającą jej pozycję; suma wszystkich iloczynów stanowi liczbę w systemie dziesiętnym:
>   $$ b_p = b_1 \cdot p^n + b_2 \cdot p^{n-1} + \dots + b_n \cdot p^0 = a_{10} $$

>[!abstract] Schemat zamiany systemów liczbowych $p \rightarrow p^x$
>1. Grupujemy cyfry liczby w $x$-elementowe grupy: $a_1 \dots a_x \mid a_{x+1} \dots a_{2x} \mid \dots$.
>2. Każda z grup odpowiada jednej cyfrze w podstawie $p^x$, przekształcamy je w pamięci.
>3. Konkatenacja liczb $b_i$ stanowi liczbę w podstawie $p^x$: $b = b_1 b_2 \dots$.

> [!example] Przykład $2 \rightarrow 8$ (skoro $8 = 2^3$, to grupy są 3-elementowe)
> Zamiana liczby $1001011_{(2)}$ na system ósemkowy:
> 1. Grupowanie: $001 \ | \ 001 \ | \ 011$
> 2. Zamiana w locie: $1_{(8)} \ | \ 1_{(8)} \ | \ 3_{(8)}$
> 3. Wynik: $113_{(8)}$
## Uzupełnienia liczb
Dla systemu o podstawie $p$ oraz $(n+m)$-cyfrowej liczby nieujemnej $X$, definiuje się dwa rodzaje uzupełnień:
*   **Uzupełnienie $p$-te:** 
    $$ \overline{\overline{X}} = p^n - X $$
*   **Uzupełnienie $(p-1)$-sze:** 
    $$ \overline{X} = p^n - X - p^{-m} $$
*   **Główna zależność:** Wzór na wyliczenie uzupełnienia $p$-tego na podstawie $(p-1)$-szego:
    $$ \overline{\overline{X}} = \overline{X} + p^{-m} $$

Operację odejmowania dwóch nieujemnych liczb można w systemach liczbowych zdefiniować jako operację dodawania $p$-tego uzupełnienia liczby odejmowanej: $$ X - Y = X + \overline{\overline{Y}} $$
*   Jeśli podczas dodawania nastąpi przeniesienie z najbardziej znaczącej pozycji, **należy je uciąć** (zignorować).
*   Jeśli przeniesienie nie nastąpi, wynikiem jest **$p$-te uzupełnienie otrzymanego rezultatu, poprzedzone znakiem minus**.
