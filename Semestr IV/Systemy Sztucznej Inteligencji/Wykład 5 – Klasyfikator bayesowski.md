## Losowe klasy abstrakcji
Wyelimiowanie determinizmu klasyfikacji daje podstawy do wprowadzenia pojęcia losowej klasy abstrakcji. Losowa klasa abstrakcja jest wyznaczana poprzez prawdopodobieństwo $P(X \mid C_p )$  określająca gęstość przynależności $X$ do klasy $C_p$. Ponieważ dla wielu $p$ jednocześnie może zachodzić $P(X \mid C_p )>0$, zatem wiele wektorów cech nie może być zakwalifikowanych jednoznacznie do tylko jednej klasy.

Celem klasyfikacji statystycznej jest klasyfikacja, której odpowiada najmniejsze prawdopodobieństwo nieprawidłowej decyzji.

## Klasyfikator Bayesa
Naiwny klasyfikator Bayesa jest przykładem prostego klasyfikatora probabilistycznego, który korzystając z rzekomej niezależności cech maksymalizuje prawdopodobieństwo a posteriori. Prawdopodobieństwem *a priori* nazywamy $P(h)$, a prawdopodobieństwa *a posteriori* $P(h \mid D)$, gdzie $D$ oznacza dane, a $h$ hipotezę.

Prawdopodobieństwo warunkowe mówi nam jaką decyzję podejmiemy znając określone informacje:

$$P(h_{n} \mid D)=\frac{P(h_{n})\cdot P(D \mid h_{n})}{\sum_{i} P(h_{i})\cdot P(D\mid h_{i})}$$

Prawdopodobieństwo warunkowe jest stosowane w regułach i drzewach decyzyjnych, zachodzi tutaj tzw. reguła łańcuchowa

>[!danger] Reguła łańcuchowa
>
> $$P(X_{1}, \dots, X_{n})=$$
>
> $$=P(X_{1}, \dots, X_{n-1})\cdot P(X_{n} \mid X_{1}, \dots, X_{n-1})=$$
>
> $$=P(X_{1}, \dots, X_{n-2})\cdot P(X_{n-1} \mid X_{1}, \dots, X_{n-2}) \cdot P(X_{n} \mid X_{1}, \dots, X_{n-1})=$$
>
> $$=\prod_{i=1}^n P(X_i \mid X_{1}, \dots, X_{i-1})$$
>

Największymi wadami klasyfikatora Bayesa jest fakt, że ta metoda wymaga dokładnych wartości lub rozkładów prawdopodobieństw pojawienia się zjawiska; często trzeba dokonać nierealistycznych założeń i  cechy systemu muszą być niezależne.

## Sieć bayesowska
Sieć bayesowska to acykliczny graf skierowany, drzewo którego wierzchołki reprezentują zmienne losowe o rozkładzie $P(X_i  \mid  R(X_i))$, gdzie $R(X_i)$ to stan $X_i$ w wierzchołku rodzica. Krawędzie reprezentują bezpośrednią zależność przyczyna → skutek. Każda zmienna jest niezależna od nie-potomków pod warunkiem rodziców. Dla każdego wierzchołka zdefiniowana jest tablica prawdopodobieństw warunkowych dla każdej kombinacji wartości jego rodziców w grafie.

Przykładowa sieć bayesowska:
![[Pasted image 20260918181127.png\mid 319]]

## Klasyfikator bayesowski
Schemat klasyfikacji bayesowskiej prezentuje się następująco:
> [!abstract] Schemat klasyfikacji bayesowskiej
> 1. W klasyfikacji Bayesa maksymalizujemy
>
>    $$P(C_i \mid  X) = \frac{P(X \mid  C_i) P(C_i)}{P(X)}$$
>
> 2. Ponieważ $P(X)$ jest stałe, zatem maksymalizujemy iloczyn:
>
>    $$P(X \mid  C_i) \cdot P(C_i)$$
>
> 3. Przyjmujemy, że $P(C_i) = \frac{s_i}{s}$, gdzie $s$ oznacza liczbę obiektów w zbiorze treningowym, a $s_i$ liczbę obiektów w klasie $C_i$.
> 4. Dla $X = (x_1, \dots, x_n)$ wartość $P(X \mid  C_i)$ obliczamy jako iloczyn $P(X \mid  C_i) = P(x_1 \mid  C_i) \cdot P(x_2 \mid  C_i) \cdot \dots \cdot P(x_n \mid  C_i)$, gdzie $P(x_k \mid  C_i) = \frac{s_{ik}}{s_i}$, gdzie $s_{ik}$ oznacza liczbę obiektów klasy $C_i$, dla których wartość atrybutu $A_k = x_k$

