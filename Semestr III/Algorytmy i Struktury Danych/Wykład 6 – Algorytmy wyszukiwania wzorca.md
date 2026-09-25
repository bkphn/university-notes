## Podstawowe pojęcia:
Wyszukiwanie wzorca jest klasycznym problemem przetwarzania tekstów. Problem ten występuje również w biologii (wyszukiwanie pewnych kombinacji genów) czy data mining (problemy klasyfikacji).
Załóżmy, że definiujemy go przy użyciu danych wejściowych:
* Alfabet $\Sigma = \{a, b, ..., z\}$
* Tekst $T$, $T_i \in \Sigma$, $i \in \{0, 1, ..., n-1\}$
* Wzorzec $P$, $P_i \in \Sigma$, $i \in \{0, 1, ..., m-1\}$

Problemem wyszukiwania wzorca będziemy nazywać wyszukiwanie wszystkich ciągów $P$ w tekście $T$.

Przyjmijmy następującą notację:
* $\Sigma^{\ast}$ - zbiór wszystkich słów skończonej długości nad alfabetem $\Sigma$
* $|w|$ - długość słowa $w$
* $\varepsilon \in \Sigma^{\ast}$ - słowo puste (spacja), czyli o długości 0
* $wu = w_1...w_n u_1...u_m$, $w = w_1...w_n$, $u = u_1...u_m$

## Odległość Levenshteina
Odległość Levenshteina jest miarą odmienności skończonych ciągów znaków, złożoność czasowa wynosi $O(mn)$, a pamięciowa $O(m)$.
Odległość definiujemy jako najmniejszą liczbę działań prostych przeprowadzających jeden ciąg znaków w drugi.
Jako działania proste rozumiemy:
* wstawienie nowego znaku
* usunięcie znaku
* zamiana na inny znak

Odległość Levenshteina słów $a, b$ definiujemy jako $\operatorname{lev}(a, b)$ i opisujemy wzorem:

$$\operatorname{lev}(a, b) = \begin{cases} |a|, & b = \varepsilon \\ |b|, & a = \varepsilon \\ \operatorname{lev}(\operatorname{tail}(a), \operatorname{tail}(b)), & \operatorname{head}(a) = \operatorname{head}(b) \\ 1 + \min\{\operatorname{lev}(\operatorname{tail}(a), b), \operatorname{lev}(a, \operatorname{tail}(b)), \operatorname{lev}(\operatorname{tail}(a), \operatorname{tail}(b))\}, & \text{w p. p.} \end{cases}$$

gdzie:
* $\operatorname{tail}(a_0a_1...a_n) = a_1...a_n$
* $\operatorname{head}(a_0a_1...a_n) = a_0$

## Algorytm N
Naive algorithm (Algorytm N) jest najprostszym algorytmem wyszukującym. Złożoność tego algorytmu jest równa $\Theta(nm - m^2 + m)$.
Idea polega na porównywaniu każdego elementu z tekstu ze wzorem i jego przesuwanie do przodu.

Przykładowy pseudokod:
```
Dane: tekst T, wzorzec P
n <- |T|
m <- |P|
i <- 0
Dopóki i <= n-m wykonuj:
    j <- 0
    Dopóki j < m i T[i+j] == P[j] wykonuj:
        j <- j + 1
    Jeżeli j == m wykonuj:
        Wypisz "Znaleziono wzorzec na pozycji: ", i
    i <- i + 1
```

## Algorytm Karpa-Rabina
Podobnie jak algorytm N, czas działania algorytmu Karpa-Rabina jest określany jako pesymistyczny i wynosi $\Theta(nm - m^2 + m)$.
Każdej literze $a_i \in \Sigma$, $i \in \{0, ..., n-1\}$ przyporządkowujemy wartość liczbową. W efekcie tekst $T$ będziemy reprezentować za pomocą jednej liczby, którą porównujemy z odpowiednikiem. Do wyszukiwania stosujemy funkcję haszującą $H$, poprzez którą wykonujemy porównanie. W wypadku gdy $H(P) = H(t)$, gdzie $t \in T$, przechodzimy do dokładnego porównywania.
Funkcją haszującą $H$ nazywamy w uogólnieniu funkcję przekształcającą dane, na których pracujemy, na ciąg znaków, który następnie poddajemy analizie. Funkcja haszująca może mieć inne postaci w zależności od tego, czy pracujemy na danych tekstowych, graficznych, dźwiękowych, etc.

Przykładowa implementacja w języku Python:
```python
t = "abcbbdedc"
w = "bd"
n = len(t)
m = len(w)
r = 26 # Liczba znaków w alfabecie
q = 97 # Przesunięcie ASCII

def a(c):
    return ord(c) - 97

def H(c, j, m):
    if m == 1:
        return a(c[j]) % q
    else:
        return (a(c[j+m-1]) + r * H(c, j, m-1)) % q
```

## Algorytm Morrisa-Pratta
Algorytm jest liniowym algorytmem wyszukiwania wzorca, jego złożoność obliczeniowa wynosi $\Theta(n + m)$, dzięki zastosowaniu funkcji pomocniczej obliczonej dla danego wzorca w czasie $O(m)$.
Funkcja prefiksowa dla wzorca $P$ zawiera informacje związane z porównywaniem wzorca z samym sobą.
Funkcja prefiksowa $f : \{1, 2, ..., m\} \to \{0, 1, ..., m-1\}$ jest dana równaniem:

$$f(q) = \max\{k : k < q \wedge P_k \in P_q\}$$

W przypadku wzorca $P = \text{FFFQQFFFQ}$ funkcja prefiksowa przyjmuje wartości:
$f(P) = 0120012330$

Algorytm ten jest algorytmem konkretniejszym od Algorytmu Naiwnego, ponieważ w przypadku braku dopasowania przesunięcie następuje tak, aby potencjalny sufiks został dopasowany.
Na początku tworzymy tabelkę, w której definiujemy wartości funkcji prefiksowej $f$; dla każdego znaku traktujemy cały dotychczasowy ciąg jako obecnie przetwarzany tekst i szukamy najdłuższego prefiksu, który będzie pokrywał się z sufiksem. Jego długość definiujemy jako wartość funkcji $f$ dla argumentu będącego tym znakiem.
Następnie porównujemy tekst od lewej strony i po braku dopasowania przesuwamy tak, aby ostatnia dopasowana litera $X$ pokryła się z indeksem $f(X)$ w ciągu $P$.

## Algorytm Boyera-Moore'a
Algorytm Boyera-Moore'a uważany jest za najefektywniejszy spośród algorytmów wyszukiwania wzorca w zadanym tekście. Wykorzystywany jest we wszystkich programach, w których możemy znaleźć polecenie "Szukaj".
Idea algorytmu polega na porównywaniu z prawej strony wzorca. Jeżeli wzorzec nie będzie pasował, to algorytm korzysta z dwóch funkcji nazywanych *good-suffix shift* oraz *bad-character shift*. W praktyce algorytm zakłada, że jeżeli sprawdzany znak nie pasuje do wzorca, to można przeskoczyć w tekście o jego długość. Przeważnie skoki są większe niż 1 element, stąd duża efektywność algorytmu.
Algorytm przeszukuje tekst od lewej do prawej strony, lecz szukany wzorzec jest porównywany od prawej do lewej. Jest to przydatne, ponieważ jeśli końcowy znak ze wzorca nie zgadza się ze znakiem tekstu i znak tekstu nie występuje dalej we wzorcu, to wzorzec można przesunąć o tyle pozycji w lewo, ile znaków ma wzorzec. Jeśli jednak dany znak występuje dalej we wzorcu, to wzorzec ustawiamy na takiej pozycji, aby zgrać znaki występujące jednocześnie w przeszukiwanym tekście i we wzorcu.

Zdefiniujmy funkcję $b$, która odpowiadać będzie za *bad-character*, dana jest ona wzorem:

$$b(x) = \begin{cases} n, & x \text{ to ostatni znak} \\ n - i(x) - 1, & \text{w p. p.} \end{cases}$$

gdzie:
* $n = |P|$
* $i(x)$ to indeks znaku $x$ w ciągu $P$

## Algorytm Aho-Corasick
Algorytm Aho-Corasick buduje automat skończony dla całego zestawu wzorców i wyszukuje wszystkie naraz w czasie $\mathcal{O}(n + k)$, gdzie $k$ jest liczbą dopasowań.
Aho-Corasick wyszukuje wiele wzorców naraz, budując trie z linkami niepowodzenia, które pozwalają przy niedopasowaniu szybko przejść do kolejnego możliwego dopasowania, dzięki czemu cały tekst można przeszukiwać w czasie liniowym.
Algorytm działa w dwóch etapach. Najpierw wszystkie wzorce są umieszczane w drzewie prefiksowym (trie), a następnie dla każdego węzła wyznaczane są tzw. linki niepowodzenia, które wskazują najdłuższy możliwy sufiks aktualnej ścieżki będący jednocześnie prefiksem innego wzorca. Dzięki temu podczas przeszukiwania tekstu, jeśli znak nie pasuje, można szybko przeskoczyć do właściwego miejsca w trie, zamiast wracać do początku. Podczas czytania tekstu znak po znaku algorytm przechodzi przez strukturę trie, a w każdym węźle, w którym kończy się jakiś wzorzec, zgłasza się dopasowanie.

## Algorytm Bitap
Wyszukiwanie wzorca przy użyciu operacji bitowych, bardzo szybkie na krótkich wzorcach.
Algorytm Bitap wyszukuje wzorzec w tekście przy użyciu operacji bitowych. Każdy znak wzorca ma przypisaną maskę bitową, a stan dopasowania reprezentowany jest przez zmienną bitową, w której kolejne bity odpowiadają kolejnym literom wzorca. Podczas czytania tekstu znak po znaku stan jest przesuwany i aktualizowany przy użyciu `AND` oraz `OR` z maskami, a jeśli odpowiedni bit stanu wskazuje 0, oznacza to pełne dopasowanie wzorca w tekście. Dzięki temu krótkie wzorce można przeszukiwać bardzo szybko.

Na początku decydujemy, czy będziemy korzystali z algorytmu `SHIFT-OR` czy `SHIFT-AND`, w zależności od tego przyjmujemy następujące założenia:
* `SHIFT-OR`: Pusta taśma to `1`, Dopasowanie to `0`, Operacja to `∨`
* `SHIFT-AND`: Pusta taśma to `0`, Dopasowanie to `1`, Operacja to `∧`

Zaczynami od zmapowania sobie liter wzorca $P$. W tym celu wprowadźmy funkcję $m$, która odpowiadać będzie za maskę. Wartość zwracana przez funkcję $m$ jest pustą taśmą z zaznaczonym dopasowaniem w miejscach, gdzie litera pokrywa się z wzorcem, zapisaną od końca (bo bity zapisujemy od prawej strony), np. $m$ dla $P = \text{YYXYX}$ wynosi $m(\text{X}) = 01011$ w przypadku algorytmu `SHIFT-OR` i $m(\text{X}) = 10100$ dla algorytmu `SHIFT-AND`.
Następnie przyjmujemy ciąg wejściowy $b_0$ pod indeksem 0 w tekście $T$ jako pustą taśmę o długości wzorca $|P|$. Dla każdej kolejnej litery w tekście $T$ wyznaczamy nowy ciąg bitów dany równaniem:

$$b_i = (b_{i-1} \ll 1) \vee m(T_i)$$

w przypadku `SHIFT-AND` zamieniamy oczywiście $\vee$ na $\wedge$. W momencie dopasowanego bitu na końcu ciągu bitowego przeskakujemy komórkę wyżej sprawdzając kolejny bit, gdy dojdziemy do początku wzorca $P$ otrzymaliśmy dopasowanie.

Operacja $\ll$ oznacza przesunięcie bitowe; przyjmując pustą taśmę jako same zera, operacja $b \ll p$ usunie $p$ pierwszych liter ciągu binarnego $b$ i dopisze na koniec $p$ zer (jako że przyjęliśmy pustą taśmę jako zera), zapewniając stałą długość ciągu $b$.
