## Reszta z dzielenia
Jeśli $m, n \in \mathbb{Z}$ oraz $n > 0$, to istnieje dokładnie jedna para liczb $q, r \in \mathbb{Z}$ taka, że:
$$ m = qn + r, \quad 0 \le r < n $$
Liczbę $r$ nazywamy **resztą z dzielenia** $m$ przez $n$. Wszystkie możliwe reszty z dzielenia przez $n$ zawarte są w zbiorze $\mathbb{Z}_n$.
* $a +_n b$ – reszta z dzielenia $a + b$ przez $n$.
* $a \cdot_n b$ – reszta z dzielenia $a \cdot b$ przez $n$.
## Podzielność
Jeżeli istnieje taka liczba $c \in \mathbb{Z}$, że $a : b = c$, to mówimy, że $a$ jest podzielne przez $b$, co zapisujemy jako $b \mid a$. W takim wypadku reszta z dzielenia tych liczb jest równa 0.

Jeżeli $a : b = c + r$ oraz $r \neq 0$, to liczba $b$ nie dzieli $a$, co zapisujemy jako $a \nmid b$. Ilość dzielników liczby całkowitej jest mniejsza bądź równa $|a|$ (dla $a \neq 0$) oraz jest skończona dla $a \neq 0$.
## Operacje modulo
Dla $n \in \mathbb{N}$ zapis:
$$ a \equiv b \pmod n \iff n \mid a - b $$
Można to rozumieć jako fakt, że jeżeli podzielimy $a$ lub $b$ przez $n$, to otrzymamy tę samą resztę z dzielenia.

**Podstawowe operacje modulo $n$:**
* **Dodawanie modulo $n$:** $a +_n b$ – reszta z dzielenia $a + b$ przez $n$.
* **Mnożenie modulo $n$:** $a \cdot_n b$ – reszta z dzielenia $a \cdot b$ przez $n$.
* **Potęgowanie modulo $n$:** $a^{k+1} = a^k \cdot_n a$ dla $k > 1$ oraz $a^1 = a$.
* **Liczba przeciwna:** $-_n a = n - a$ (liczba przeciwna do $a$).
## Elementy pierścienia $\mathbb{Z}_n$
Każdy element $r$ pierścienia $\mathbb{Z}_n$ możemy utożsamić ze zbiorem wszystkich liczb całkowitych, które przy dzieleniu przez $n$ dają resztę $r$. Czyli np. $0 = 2 = 4 = 6 = \dots$ w $\mathbb{Z}_2$, ponieważ $0 \equiv 2k \pmod 2$ dla $k \in \mathbb{Z}$. Pozwala to na łatwiejsze obliczanie działań w pierścieniach $\mathbb{Z}_n$ poprzez przejście na zbiór $\mathbb{Z}$.

Aby obliczyć, ile jest warta jakaś liczba $x$ w zbiorze $\mathbb{Z}_n$, możemy korzystać z operacji modulo:
$$ x \bmod n = x_n $$
Wynika z tego fakt, że w zbiorze $\mathbb{Z}_n$ liczba $x$ jest równa reszcie z dzielenia tej liczby przez $n$. Możemy stosować następujący algorytm:
1. Dzielimy liczbę $x$ przez $n$.
2. Wyznaczamy część całkowitą z tego ilorazu i mnożymy ją przez $n$.
3. Otrzymaną liczbę odejmujemy od liczby $x$, żeby otrzymać resztę z dzielenia.

> [!example] Przykład
> Oblicz ile jest równe $625$ w $\mathbb{Z}_{37}$:
> 1. $\frac{625}{37} = 16, \dots$
> 2. $16 \cdot 37 = 592$
> 3. $625 - 592 = 33$
> Więc $625 = 33$ w $\mathbb{Z}_{37}$.
## Skrótowe potęgowanie modulo $n$
Dla pierścieni $\mathbb{Z}_n$ istnieje sposób ułatwienia liczenia potęg konkretnych liczb. Aby obliczyć $x^y$:
1. Na początku musimy zapisać wykładnik $y$ jako sumę potęg dwójki (analogicznie do zapisu binarnego):   $$ y = 2^{k_1} + \dots + 2^{k_r} $$
2. Następnie liczymy potęgi liczby $x$ dla kolejnych potęg dwójek, szukając za każdym razem ich odpowiednika w zbiorze $\mathbb{Z}_n$ i podstawiając do kolejnej potęgi:
   $$ y^{2^{k_1}} = y_1 $$
   $$ y^{2^{k_2}} = y_1^{\frac{k_2}{k_1}} $$
	 I tak aż do obliczenia finalnej potęgi, po czym mnożymy je ze sobą.

> [!example] Przykład
> Oblicz $5^{30}$ w $\mathbb{Z}_{37}$:
> * $30 = 2^4 + 2^3 + 2^2 + 2^1 = 16 + 8 + 4 + 2$
> * $5^2 = 25$
> * $5^4 = (5^2)^2 = 25^2 = 625 = 33$, ponieważ $625 \equiv 33 \pmod{37}$
> * $5^8 = (5^4)^2 = 33^2 = 1089 = 11$, ponieważ $1089 \equiv 11 \pmod{37}$
> * $5^{16} = (5^8)^2 = 11^2 = 121 = 10$, ponieważ $121 \equiv 10 \pmod{37}$
> 
> Korzystając z powyższego:
> $$ 5^{30} = 5^{16+8+4+2} = 5^{16} \cdot 5^8 \cdot 5^4 \cdot 5^2 = 10 \cdot 11 \cdot 33 \cdot 25 = 90750 = 26 $$
> Ponieważ $90750 \equiv 26 \pmod{37}$.
## Małe twierdzenie Fermata
Małe twierdzenie Fermata to istotny element teorii liczb
> [!danger] Małe twierdzenie Fermata
> Jeśli $p$ jest liczbą pierwszą, a $a$ jest liczbą całkowitą niepodzielną przez $p$, to reszta z dzielenia $a^{p-1}$ przez $p$ wynosi $1$: $$ \forall_{a \in \mathbb{Z}} \forall_{p \in \mathbb{P}} : \gcd(a, p) = 1 \implies a^{p-1} \equiv 1 \pmod p $$

 Gdzie $\mathbb{P}$ to zbiór wszystkich liczb pierwszych. Z powyższego twierdzenia wynika również tożsamość:
$$ \forall_{a \in \mathbb{Z}} \forall_{p \in \mathbb{P}} : a^p \equiv a \pmod p $$
## Funkcja $\varphi$ Eulera
Liczba $a$ jest względnie pierwsza do liczby $b$, jeżeli $\gcd(a, b) = 1$, czyli jeżeli liczby te nie mają wspólnych dzielników różnych od 1. Przykładem par takich liczb są $5$ i $6$, ponieważ $\gcd(5, 6) = 1$.

Funkcja $\varphi(n)$ Eulera to funkcja zwracająca ilość liczb całkowitych dodatnich mniejszych od $n$, które są względnie pierwsze do $n$: $$ \varphi(n) = |\{1 \le k < n : \gcd(k, n) = 1\}| $$
**Przykłady:**
* $\varphi(1) = |\{1\}| = 1$
* $\varphi(2) = |\{1 \le k \le 2 : \gcd(k, 2) = 1\}| = |\{1\}| = 1$
* $\varphi(3) = |\{1, 2\}| = 2$
* $\varphi(4) = |\{1, 3\}| = 2$
* $\varphi(5) = |\{1, 2, 3, 4\}| = 4$
* $\varphi(6) = |\{1, 5\}| = 2$

Jeżeli znamy rozkład liczby na czynniki pierwsze $n = p_1^{k_1} \cdot p_2^{k_2} \cdot \dots \cdot p_r^{k_r}$, to $\varphi(n)$ możemy obliczyć ze wzoru:
$$ \varphi(n) = n \left(1 - \frac{1}{p_1}\right) \left(1 - \frac{1}{p_2}\right) \cdot \dots \cdot \left(1 - \frac{1}{p_r}\right) $$
Gdzie $p_x$ to kolejne czynniki pierwsze, a $k_x$ to ich potęgi.

> [!example] Przykład obliczenia $\varphi(12)$
> 1. Rozkład liczby na czynniki pierwsze: $12 = 2 \cdot 2 \cdot 3 = 2^2 \cdot 3$.
> 2. Obliczenie wartości:
>    $$ \varphi(12) = 12 \left(1 - \frac{1}{2}\right) \left(1 - \frac{1}{3}\right) = 12 \cdot \frac{1}{2} \cdot \frac{2}{3} = 4 $$
> 3. Zgodnie z definicją zbioru: $\varphi(12) = |\{1, 5, 7, 11\}| = 4$.

Stosując małe twierdzenie Fermata, możemy uprościć wzór dla liczb pierwszych:
$$ \forall_{p \in \mathbb{P}} \ \varphi(p) = p \left(1 - \frac{1}{p}\right) = p - 1 $$
## Pierścień reszt modulo $n$
Pierścień $(\mathbb{Z}_n, +_n, \cdot_n)$ nazywany jest pierścieniem reszt modulo $n$. System ten spełnia następujące własności:
* $+_n$ jest łączne i przemienne.
* $0$ jest elementem zerowym dodawania.
* Elementem przeciwnym do $a$ jest $-_n a$ dla $a \neq 0$ oraz $0$ dla $a = 0$.
* $\cdot_n$ jest łączne i przemienne.
* $1$ jest elementem neutralnym mnożenia.
* Mnożenie jest rozdzielne względem dodawania.
### Zbiór elementów odwracalnych
Prawdziwe jest następujące twierdzenie: równanie $a \cdot_n x = 1$ ma rozwiązanie w $\mathbb{Z}_n$ wtedy i tylko wtedy, gdy liczby $a$ i $n$ są względnie pierwsze:
$$ \exists_{a' \in \mathbb{Z}_n} : a \cdot_n a' = 1 \iff \gcd(a, n) = 1 $$
Oznacza to, że w pierścieniu $\mathbb{Z}_n$ istnieje element odwrotny do $a$ wtedy i tylko wtedy, gdy $a$ i $n$ nie mają wspólnych dzielników innych niż 1. Zbiór elementów odwracalnych w $\mathbb{Z}_n$ oznaczamy jako $\mathbb{Z}_n^*$:
$$ \mathbb{Z}_n^* = \{a \in \mathbb{Z}_n : \gcd(a, n) = 1\} $$
Funkcja Eulera pozwala nam obliczyć ilość elementów dla zbiorów $\mathbb{Z}_n^*$:
$$ |\mathbb{Z}_n^*| = \varphi(n) $$