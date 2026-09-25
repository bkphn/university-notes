## Metody numeryczne
Metody numeryczne zajmują się sposobami rozwiązywania problemów matematycznych za pomocą operacji na liczbach. Otrzymywane tą drogą wyniki są zazwyczaj jedynie przybliżeniem, jednak dokładność obliczeń może być z góry określona i dobrana w zależności od potrzeb.
 
Wykorzystuje się je, gdy badany problem nie ma rozwiązania analitycznego lub korzystanie z takich rozwiązań jest uciążliwe ze względu na ich złożoność.
Najczęściej używa się ich do:
 * znajdowania miejsc zerowych funkcji nieliniowych,
 * rozwiązywania złożonych układów równań liniowych,
 * aproksymacji,
 * całkowania,
 * rozwiązywania równań różniczkowych,
 * znajdowania wartości wektorów własnych.

## Zadania numeryczne
Zadaniem numerycznym nazywamy proces przekształcenia pewnego elementu zbioru danych $D$ w taki element zbioru wyników $W$, który spełnia wymagania $R_1, R_2, \dots$ Układ $\{D, W, R_1, R_2, \dots\}$ nazywamy klasą zadań numerycznych.

> [!example] Zadanie wyznaczenia wartości wielomianu
> Wielomian: $W_n(x) = \sum_{i=0}^n a_i x^i$.
> * **Zbiór danych ($D$):** Zdefiniowany wektorem danych $\vec{d} = (x, a_0, a_1, \dots, a_n)^T$. 
>   $D = \{(x, a_0, a_1, \dots, a_n)^T : x \in \mathbb{R} \land a_i \in \mathbb{R} \land i = 0, 1, \dots, n\} = \mathbb{R}^{n+2}$.
> * **Zbiór wyników ($W$):** Jednoelementowy wektor wyników $\vec{w} = (y)$, stąd $W = \mathbb{R}$.
> * **Wymagania:** $R_1: y = W_n(x)$.

## Algorytmy numeryczne
Algorytm numeryczny to opis jednoznacznie uporządkowanego ciągu operacji, które przekształcają zbiór danych $D$ w zbiór wyników $W$ dla pewnej klasy zadań numerycznych. Operacje oznaczają działania arytmetyczne i logiczne.

Możemy wyróżnić następujące formy opisu algorytmu:
* zapis matematyczny
* zapis słowno-matematyczny
* zapis słowny
* schemat blokowy

## Algorytm Hornera
Algorytm Hornera jest przykładem algorytmu służącego do wyznaczania wartości wielomianu dla danego argumentu.

Wielomian $W_n(x)$ możemy zapisać jako:

$$W_n(x) = \sum_{i=0}^n a_i x^i = (\dots((a_n x + a_{n-1})x + a_{n-2})x + \dots + a_1)x + a_0$$

Obliczając kolejno:
* $y_n = a_n$
* $y_{n-1} = a_{n-1} + y_n x$
* $y_{n-2} = a_{n-2} + y_{n-1} x$
	$\vdots$
* $y_0 = a_0 + y_1 x$
Otrzymamy poszukiwaną wartość $W_n(x) = y_0$.

### Sposoby reprezentacji algorytmu Hornera

**1. Zapis matematyczny**

$$\begin{cases} y_n = a_n \\ y_i = a_i + y_{i+1} x, \quad i \in \{n-1, n-2, \dots, 1, 0\} \end{cases}$$

**2. Zapis słowno-matematyczny**
1. Dane: $x, a_0, a_1, \dots, a_n$
2. Podstawiamy $y_n = a_n$
3. Dla każdego $i \in \{n-1, n-2, \dots, 1, 0\}$ liczymy $y_i = a_i + y_{i+1} x$
4. Wynikiem jest $y_0$
**3. Schemat blokowy**
