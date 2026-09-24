## Szeregi liczbowe
Ciąg liczbowy $a_n$ jest tak naprawdę funkcją $a(n)$, która przyjmuje tylko argumenty należące do zbioru liczb naturalnych. Sumą częściową ciągu, oznaczaną jako $S_n$, nazywamy sumę pierwszych $n$ elementów tego ciągu: $$ s_n = \sum_{i=0}^{n} a_i $$Sumę nieskończonej ilości elementów tego ciągu nazywamy szeregiem liczbowym i oznaczamy: $$ \sum_{i=0}^{\infty} a_i $$
Wśród szeregów liczbowych warto zwrócić szczególną uwagę, na:
* **Szereg harmoniczny**: $$\sum_{n=1}^{\infty} \frac{1}{n}$$
* **Szereg aharmoniczny**: $$\sum_{n=1}^{\infty} \frac{(-1)^{n+1}}{n}$$
## Zbieżność szeregu
Mówimy, że szereg jest zbieżny, gdy suma jego elementów dąży do jakiejś stałej liczby rzeczywistej $s$:
$$ \sum_{i=0}^{\infty} a_i \text{ jest zbieżny} \iff \lim_{n \to \infty} s_n = s \in \mathbb{R} $$
Liczba $s$ jest nazywana sumą szeregu. Z powyższej definicji wynika, że jeżeli $a_n \not\to 0$, to $\sum_{i=0}^{\infty} a_i$ jest rozbieżny.
## Szacowanie sumy szeregu
Górne i dolne szacowanie sumy szeregu pozwala nam na badanie jego zbieżności. Prawdziwe są następujące twierdzenia:
* Jeżeli $\sum_{i=0}^{\infty} b_i$ jest zbieżny oraz $\sum_{i=0}^{\infty} a_i \le \sum_{i=0}^{\infty} b_i$, to $\sum_{i=0}^{\infty} a_i$ jest zbieżny.
* Jeżeli $\sum_{i=0}^{\infty} c_i$ jest rozbieżny oraz $\sum_{i=0}^{\infty} a_i \ge \sum_{i=0}^{\infty} c_i$, to $\sum_{i=0}^{\infty} a_i$ jest rozbieżny.

> [!example] Sprawdzenie zbieżności szeregu harmonicznego
> Rozważmy szereg harmoniczny:
> $$ \sum_{n=1}^{\infty} \frac{1}{n} = \frac{1}{1} + \frac{1}{2} + \frac{1}{3} + \frac{1}{4} + \frac{1}{5} + \frac{1}{6} + \frac{1}{7} + \frac{1}{8} + \dots $$
> Stosując szacowanie dolne przez wyrazy mniejsze lub równe:
> $$ \frac{1}{1} + \frac{1}{2} + \frac{1}{4} + \frac{1}{4} + \frac{1}{8} + \frac{1}{8} + \frac{1}{8} + \frac{1}{8} + \dots $$
> Otrzymujemy ograniczenie dolne w postaci szeregu:
> $$ \frac{1}{1} + \sum_{k=1}^{\infty} k \cdot \frac{1}{2^k} = 1 + \frac{1}{2} + \frac{1}{2} + \dots = \infty $$
> Skoro dolne szacowanie sumy szeregu jest rozbieżne, to sam szereg harmoniczny również musi być rozbieżny.
## Potęgi szeregu harmonicznego
W badaniu zbieżności często porównuje się szeregi do szeregu postaci $\sum_{n=1}^{\infty} \frac{1}{n^p}$. Zasada zbieżności takiego szeregu jest prosta:
* $\sum_{n=1}^{\infty} \frac{1}{n^p}$ jest **zbieżny**, dla $p > 1$.
* $\sum_{n=1}^{\infty} \frac{1}{n^p}$ jest **rozbieżny**, dla $p \le 1$.
## Kryteria zbieżności szeregów
### 1. Badanie zbieżności szeregu całką oznaczoną
Jeżeli $a(n)$ jest ciągła, nieujemna i malejąca oraz $a_n = a(n)$, to:
$$ \sum_{n=0}^{\infty} a_n \text{ jest zbieżny} \implies \int_{0}^{\infty} a(x) \, dx \neq \pm\infty $$
### 2. Badanie zbieżności asymptotycznej
Jeżeli funkcje $f(n)$ i $g(n)$ zachowują się w identyczny sposób dla dużych $n$, to mówimy, że są **asymptotycznie równe** i zapisujemy jako $f(n) \sim g(n)$. Aby dwie funkcje były asymptotycznie równe, granica ich ilorazu musi być równa 1:
$$ f(n) \sim g(n) \iff \lim_{n \to \infty} \frac{f(n)}{g(n)} = 1 $$
Równość asymptotyczna pozwala nam na badanie zbieżności szeregu, ignorując mniejsze potęgi czy skalary.

> [!example] Przykład
> Badamy zbieżność szeregu $\sum_{n=1}^{\infty} \frac{\sqrt[4]{n^3 + 17}}{n^4 - 5n^2 + 3n}$:
> $$ \frac{\sqrt[4]{n^3 + 17}}{n^4 - 5n^2 + 3n} \sim \frac{\sqrt[4]{n^3}}{n^4} = \frac{n^{\frac{3}{4}}}{n^4} = \frac{1}{n^{\frac{13}{4}}} $$
> Ponieważ szereg $\sum_{n=1}^{\infty} \frac{1}{n^{13/4}}$ jest zbieżny ($p = \frac{13}{4} > 1$), badany szereg również jest zbieżny.

### 3. Kryterium Cauchy'ego
Kryterium Cauchy'ego pozwala na badanie zbieżności szeregu poprzez badanie granicy pierwiastka z ciągu:
* $\lim_{n \to \infty} \sqrt[n]{a_n} < 1 \implies \sum_{n=1}^{\infty} a_n$ jest **zbieżny**.
* $\lim_{n \to \infty} \sqrt[n]{a_n} = 1 \implies$ **nie rozstrzygnięto**.
* $\lim_{n \to \infty} \sqrt[n]{a_n} > 1 \implies \sum_{n=1}^{\infty} a_n$ jest **rozbieżny**.

Kryterium to jest bardzo przydatne w wypadkach, gdy ogólny wyraz ciągu jest podniesiony do $n$-tej potęgi, która skraca się z pierwiastkiem: $a_n = (b_n)^n \implies \lim_{n \to \infty} \sqrt[n]{(b_n)^n} = \lim_{n \to \infty} b_n$.

### 4. Kryterium d'Alemberta
Kryterium d'Alemberta opiera się na wyznaczeniu ilorazu dwóch kolejnych wyrazów ciągu:
* $\lim_{n \to \infty} \frac{a_{n+1}}{a_n} < 1 \implies \sum_{n=1}^{\infty} a_n$ jest **zbieżny**.
* $\lim_{n \to \infty} \frac{a_{n+1}}{a_n} = 1 \implies$ **nie rozstrzygnięto**.
* $\lim_{n \to \infty} \frac{a_{n+1}}{a_n} > 1 \implies \sum_{n=1}^{\infty} a_n$ jest **rozbieżny**.

Kryterium d'Alemberta jest przydatne, gdy ogólny wyraz ciągu jest ilorazem $a_n = \frac{b_n}{c_n}$.
## Szeregi o wyrazach różnych znaków (naprzemienne)
Jeżeli istnieje nieskończenie wiele wyrazów ciągu o znakach dodatnich oraz ujemnych, mamy do czynienia z szeregami o wyrazach różnych znaków, zwanymi również szeregami naprzemiennymi.
* Mówimy, że szereg $\sum_{n=1}^{\infty} a_n$ jest **zbieżny bezwzględnie**, jeżeli szereg $\sum_{n=1}^{\infty} |a_n|$ jest zbieżny.
* Mówimy, że szereg $\sum_{n=1}^{\infty} a_n$ jest **zbieżny warunkowo**, jeżeli sam w sobie jest zbieżny, ale szereg $\sum_{n=1}^{\infty} |a_n|$ jest rozbieżny (oznacza to, że szereg jest zbieżny tylko dlatego, że jego wyrazy się znoszą).
### Kryterium Leibniza
Kryterium Leibniza pozwala badać zbieżność warunkową ciągów naprzemiennych. Mówi ono, że jeżeli:
* $a_n \to 0$
* $a_n$ jest malejący
* $a_n > 0$
to szereg $\sum_{n=1}^{\infty} (-1)^n \cdot a_n$ oraz szereg $\sum_{n=1}^{\infty} (-1)^{n+1} \cdot a_n$ są **zbieżne warunkowo**.
## Twierdzenia dotyczące szeregów naprzemiennych
>[!danger] Twierdzenie Dirichleta
> Jeżeli szereg $\sum_{n=1}^{\infty} a_n$ jest zbieżny bezwzględnie, to dla dowolnej permutacji $\sigma: \mathbb{N} \to \mathbb{N}$ zachodzi:   $$ \sum_{n=1}^{\infty} a_{\sigma(n)} = \sum_{n=1}^{\infty} a_n $$

>[!danger] Wniosek z kryterium porównawczego
>Jeżeli $\sum_{n=1}^{\infty} a_n$ jest zbieżny bezwzględnie, a ciąg $b_n$ jest ograniczony, to szereg $\sum_{n=1}^{\infty} a_n \cdot b_n$ jest zbieżny bezwzględnie.

>[!danger] Twierdzenie Riemanna o szeregach warunkowo zbieżnych
>Jeżeli szereg $\sum_{n=1}^{\infty} a_n$ jest zbieżny warunkowo i nie jest zbieżny bezwzględnie, to w zależności od funkcji $\sigma(n)$ suma może przyjmować dowolną wartości lub rozbiegać się:
   $$ \sum_{n=1}^{\infty} a_{\sigma(n)} = +\infty \lor \sum_{n=1}^{\infty} a_{\sigma(n)} = -\infty \lor \sum_{n=1}^{\infty} a_{\sigma(n)} = r \in \mathbb{R} $$
   