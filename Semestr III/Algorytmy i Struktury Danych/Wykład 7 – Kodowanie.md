## Kodowanie i dekodowanie
Kodowaniem nazywamy proces przyporządkowania danym elementom tekstu odpowiedników z innego alfabetu np. binarnego. Dekodowaniem nazywamy proces odwrotny do kodowania. Kodowanie jest powszechnie stosowane w kompresji i kryptografii.
Wyróżniamy dwa rodzaje kodów:
* Stałej długości
* Różnej długości

Dobry algorytm kodowania powinien być jednoznaczny, efektywny i powinien mieć małą złożoność obliczeniową.

## Wybrane metody kodowania
* **Kodowanie Shannona-Fano:** Metoda kompresji bezstratnej, powszechnie stosowana w kompresatorze ZIP. Zalety i wady algorytmu to prostota, nadmiarowość kodu, wagi podzbiorów nie są równe, a także jedno kodowanie, lecz kilka różnych kodów.
* **Kodowanie Huffmana:** Jeden z najprostszych i najłatwiejszych do implementacji algorytmów kompresji. Nie jest on najefektywniejszy obliczeniowo, dlatego w praktyce raczej nie jest popularny, choć zdarza się jego wykorzystanie do kompresji bezstratnej w plikach MP3.

### Kodowanie Graya
Kod Graya to binarna numeracja, w której kolejne liczby różnią się dokładnie jednym bitem. Jest on powszechnie stosowany w enkoderach optycznych, elektronice cyfrowej oraz w redukcji błędów transmisji.

Będziemy kodować ciąg bitów $B = b_0 b_1 b_2 \dots$, jako wynik otrzymując szyfrogram $G = g_0 g_1 g_2 \dots$. Jako pierwszą literę szyfrogramu $G$ przyjmujemy pierwszą literę ciągu $B$:

$$g_0 = b_0$$

Każdą następną literę szyfrogramu $G$ kodujemy jako operację XOR obecnej i poprzedniej bitowej wartości ciągu $B$:

$$g_i = b_i \oplus b_{i-1}$$

Żeby zdekodować ciąg $G = g_0 g_1 g_2 \dots$, skorzystamy z poniższego algorytmu:
Jako pierwszą literę ciągu $B$ przyjmujemy pierwszą literę szyfrogramu $G$ ($g_0 = b_0$). Każdą następną literę komunikatu $B$ kodujemy jako XOR ostatniej zdekodowanej litery ciągu $B$ i aktualnej litery tekstu $G$:

$$b_i = b_{i-1} \oplus g_i$$

> [!example] Przykład: Zakoduj komunikat 0101 stosując algorytm Graya
> 0. $B = 0101 \implies b_0 = 0, b_1 = 1, b_2 = 0, b_3 = 1$
> 1. $g_0 = b_0 = 0$
> 2. $g_1 = b_0 \oplus b_1 = 0 \oplus 1 = 1$
> 3. $g_2 = b_1 \oplus b_2 = 1 \oplus 0 = 1$
> 4. $g_3 = b_2 \oplus b_3 = 0 \oplus 1 = 1$
> 5. Wynik: $B = 0111$

## Szyfrowanie i Kryptologia
Kryptologia jest nauką o bezpiecznych sposobach przechowywania i przesyłania danych. Dzielimy ją na dwie dziedziny:
* **Kryptografię:** Nauka o tworzeniu szyfrów i zabezpieczaniu z wykorzystaniem kluczy szyfrujących.
* **Kryptoanalizę:** Nauka o łamaniu szyfrów, czyli odczytywaniu zaszyfrowanych danych bez wiedzy o kluczu.

Szyfry możemy podzielić na dwa rodzaje:
* **Symetryczny:** Do szyfrowania i deszyfrowania wykorzystywany jest ten sam klucz.
* **Asymetryczny:** Do szyfrowania i deszyfrowania wykorzystywana jest para kluczy.

Aby szyfr był niemożliwy do złamania, musiałby spełniać poniższe założenia:
* klucz szyfrujący jest takiej samej długości jak wiadomość,
* klucz będzie wykorzystany tylko raz,
* istnieje dowolne podstawienie znaków.
Taki szyfr jest jednak niepraktyczny i niemożliwy do stosowania.

Możemy wyróżnić następujące rodzaje łamania szyfrów:
* **Brute Force:** Atak polegający na sprawdzaniu wszystkich możliwych kluczy do momentu złamania zabezpieczenia.
* **Frequency Analysis:** Opiera się na analizowaniu częstości występowania znaków i na jej podstawie przewidywaniu liter alfabetu jawnego.
* **Meet in the Middle:** Polega na łamaniu szyfrów używając jednocześnie wielu kluczy dla jednego algorytmu.

W szyfrowaniu symetrycznym jeden klucz jest znany nadawcy i odbiorcy – nadawca szyfruje dane, wysyła zaszyfrowaną wiadomość, a odbiorca dzięki kluczowi je odszyfrowuje. 
W szyfrowaniu asymetrycznym wykorzystuje się dwa klucze:
* **Klucz publiczny:** Używany do szyfrowania danych.
* **Klucz prywatny:** Używany do odszyfrowania danych, jest znany tylko osobie deszyfrującej.

## Szyfr Cezara
Jest to jedna z najstarszych i najprostszych technik szyfrowania symetrycznego. Szyfr polega na zastępowaniu znaków innymi, oddalonymi o stałą liczbę $k$.

Szyfrowanie definiujemy następująco:

$$E_k(x) = x + k \pmod m$$

gdzie $m = |\mathcal{A}|$ jest długością alfabetu (26 dla łacińskiego, 32 dla polskiego), a $k$ jest ustalonym przesunięciem.
Deszyfrowanie definiujemy korzystając ze wzoru:

$$D_k(x) = x - k \pmod m$$

> [!example] Przykład: Zakoduj hasło "CEZAR" za pomocą szyfru Cezara dla $k=3$
> **0. Zamiana alfabetów:**
>    Alfabet wejściowy: $\set{\text{A,B,C,D,E,F,G,H,I,J,K,L,M,N,O,P,Q,R,S,T,U,V,W,X,Y,Z}}$
>    Alfabet wyjściowy: $\set{\text{D,E,F,G,H,I,J,K,L,M,N,O,P,Q,R,S,T,U,V,W,X,Y,Z,A,B,C}}$
> **1. Kodowanie:**
>    * $E_k(\text{C}) = \text{F}$
>    * $E_k(\text{E}) = \text{H}$
>    * $E_k(\text{Z}) = \text{C}$
>    * $E_k(\text{A}) = \text{D}$
>    * $E_k(\text{R}) = \text{U}$
> **2. Wynik:** $E_k(\text{CEZAR}) = \text{FHCDU}$

## Algorytm RSA
Algorytm Rivesta-Shamira-Adlemana (RSA) jest jednym z pierwszych asymetrycznych algorytmów kryptograficznych. Jako główną zaletę RSA podaje się trudność problemu faktoryzacji dużych liczb złożonych.

### Generowanie kluczy
1. Wybieramy dwie losowe liczby pierwsze $p, q \in \mathbb{P}$.
2. Obliczamy wartość $n = p \cdot q$, a następnie wartość funkcji Eulera:

$$\varphi(n) = (p-1)(q-1)$$

3. Wybieramy liczbę $e$ względnie pierwszą z $\varphi(n)$, taką że $1 < e < \varphi(n)$.
4. Znajdujemy taką liczbę $d$, że $d \cdot e \equiv 1 \pmod{\varphi(n)}$.

W ten sposób generujemy parę:
* Klucz publiczny: $(n, e)$
* Klucz prywatny: $(n, d)$

### Szyfrowanie i deszyfrowanie
Mając oba klucze, dane dzielimy na bloki $m$ (nie większe niż $n$), a następnie każdy z bloków szyfrujemy stosując:

$$c \equiv m^e \pmod n$$

Zaszyfrowane dane będą złożone z bloków długości $c$, więc deszyfrowanie zachodzi poprzez formułę:

$$m \equiv c^d \pmod n$$

> [!example] Przykład: Zaszyfruj komunikat $m=9$ algorytmem RSA
> 1. Generowanie Kluczy:
>    * Przyjmijmy $p = 11$, $q = 13 \implies n = 11 \cdot 13 = 143$
>    * $\varphi(143) = (11-1)(13-1) = 10 \cdot 12 = 120$
>    * Wybieramy $e = 7$
>    * Wyznaczamy $d = 103$, ponieważ $103 \cdot 7 \equiv 1 \pmod{143}$
>    * Otrzymujemy klucz publiczny $(143, 7)$ oraz klucz prywatny $(143, 103)$
> 2. Szyfrowanie:
>    * $c = 9^7 \pmod{143} = 4782969 \pmod{143} = 48$
> 3. Deszyfrowanie:
>    * $m = 48^{103} \pmod{143} = 9$

## Algorytm ElGamal
Algorytm ElGamal został zaproponowany w 1985 roku przez egipskiego kryptologa Tahera Elgamala. Jest to szyfr asymetryczny oparty na trudności obliczania logarytmu dyskretnego, wykorzystujący operacje w grupach modularnych (może być używany do szyfrowania oraz podpisów cyfrowych).

1. **Generowanie kluczy:** Wybieramy dowolną liczbę pierwszą $p \in \mathbb{P}$, liczbę $g$ będącą pierwiastkiem pierwotnym modulo $p$ oraz dowolne $k \in \mathbb{Z}$ takie, że $1 < k < p$. Następnie obliczamy liczbę $y = g^k \pmod p$. Trójka $(p, g, y)$ jest kluczem publicznym, a $(p, g, y, k)$ kluczem prywatnym.
2. **Szyfrowanie wiadomości:** Chcąc zaszyfrować komunikat $\vec{m}$, wybieramy losowe $x \in (1, p-1)$ i wyznaczamy dwie liczby $c_1, c_2$:

$$c_1 = g^x \pmod p, \quad c_2 = \vec{m} \cdot y^x \pmod p$$

Para $(c_1, c_2)$ jest naszym szyfrogramem.
3. **Deszyfrowanie:** Mając kryptogram $\vec{c} = (c_1, c_2)$, wyznaczamy wartość $s = c_1^x \pmod p$, a następnie odszyfrowujemy komunikat:

   $$\vec{m} = c_2 \cdot s^{-1} \pmod p$$

## Szyfr Vigenère'a
Szyfr Vigenère'a to metoda wieloalfabetowa, w której każda litera szyfrogramu zależy od odpowiedniej litery klucza. Klucz powtarza się cyklicznie nad tekstem jawnym.

Aby zaszyfrować komunikat $m = m_1 m_2 \dots m_n$ szyfrem Vigenère'a, wybieramy klucz $k = k_1 k_2 \dots k_l$ Oba komunikaty mapujemy na alfabet ${Z}_{26}$ (lub ${Z}_{32}$ dla j. polskiego). Następnie każdą literę $m_i$ komunikatu szyfrujemy jako $m_i + k_i \pmod{26}$, a w przypadku kończenia się klucza – zapętlamy go.

> [!example] Przykład: Zaszyfruj komunikat $m = \text{ALGORYTM}$ szyfrem Vigenère'a dla klucza $k = \text{AISD}$
> 1. **Mapowanie alfabetu**
> 2. **Mapowanie komunikatu i zapętlonego klucza:**
>    * $m = \text{ALGORYTM} \implies 00, 11, 06, 14, 17, 24, 19, 12$
>    * $k = \text{AISD} \implies \text{AISDAISD} \implies 00, 08, 18, 03, 00, 08, 18, 03$
> 3. **Szyfrowanie (dodawanie modulo 26):**
>    * $c_1 = 0 + 0 \pmod{26} = 0$
>    * $c_2 = 11 + 8 \pmod{26} = 19$
>    * $c_3 = 6 + 18 \pmod{26} = 24$
>    * $c_4 = 14 + 3 \pmod{26} = 17$
>    * $c_5 = 17 + 0 \pmod{26} = 17$
>    * $c_6 = 24 + 8 \pmod{26} = 6$
>    * $c_7 = 19 + 18 \pmod{26} = 11$
>    * $c_8 = 12 + 3 \pmod{26} = 15$
> 4. **Mapowanie kryptogramu:**
>    $c = 00, 19, 24, 17, 17, 06, 11, 15 \implies \text{ATYRRGLP}$

## Kod Woźniaka
Na egzaminie z Algorytmów i Struktur Danych prowadzący prof. dr hab. inż. Marcin Woźniak zaprezentował swój autorski kod służący do zakodowania swoich danych na arkuszu egzaminacyjnym, potocznie nazywany kodem Woźniaka.

Zaczynami od umieszczenia danych wejściowych w macierzy $n \times m$, a następnie zaczynając od elementu o indeksach $(1, 1)$, przypisujemy każdemu elementowi kolejną dodatnią liczbę naturalną. Po dotarciu na koniec pierwszego wiersza przechodzimy do drugiego i przypisywanie indeksów rozpoczynamy od ostatniego elementu. Po dotarciu do początku drugiego wiersza przeskakujemy do trzeciego i powtarzamy cykl. Kodem elementu $a_{ij}$ jest jej indeks. Moim indeksem na egzaminie był numer $11$.
