## Logika
Istnieje dokładnie $2^{(2^n )}$  $n$-arnych operatorów logicznych, podstawiając $n=2$ możemy obliczyć, że istnieje 16 binarnych operatorów logicznych, takich jak: $\land,  \lor,  \implies,  \iff, \oplus,\dots$ .

Każde zdanie logiczne może być zapisane w równoważnej postaci za pomocą spójników logicznych $\lor, \land, \neg$.  Spójniki te nazywamy **podstawowymi operatorami logicznymi**.
## Funkcje boolowskie
Wielomianem boolowskim $W$ zmiennych $x_1,x_2,\dots,x_n$ nazywamy formułę zdaniową zbudowaną wyłącznie z $x_1,\dots,x_n$ oraz spójników $\lor,  \land,  \neg$.

Wartościowanie logiczne wielomianu boolowskiego $W$ nazywamy $n$-argumentową funkcją boolowską $f=W(x_1,\dots,x_n )$ i mówimy wtedy, że $W$ generuje $f$. Zbiór wszystkich $n$-argumentowych funkcji boolowskich oznaczamy jako $\mathtt{Bool}(n)$.

Funkcja boolowska przyjmuje argumenty o wartościach $0$ lub $1$ i zwraca wartość $0$ lub $1$. Można ją traktować jako regułę decyzyjną: dla każdej kombinacji wejść mówi, czy wynik jest fałszywy czy prawdziwy.

> [!example] Wyznaczanie zbioru Bool(1)
> **Wyznacz zbiór $\mathtt{Bool}(1)$**
> 
> Rozpisujemy wszystkie możliwe funkcje unarne:
> 
> | $x$ | $f_1(x\text{ })$ | $f_2(x\text{ })$ | $f_3(x\text{ })$ | $f_4(x\text{ })$ |
> | :---: | :---: | :---: | :---: | :---: |
> | $0$ | $0$ | $0$ | $1$ | $1$ |
> | $1$ | $0$ | $1$ | $0$ | $1$ |
> 
> Możemy zauważyć, że:
> *   $f_1(x) = 0$
> *   $f_2(x) = x$
> *   $f_3(x) = \neg x$
> *   $f_4(x) = 1$
> 
> Zatem:
> $$ \mathtt{Bool}(1) = \{0, x, \neg x, 1\} $$

Dla każdej liczby naturalnej $n$ zachodzi: $$|\mathtt{Bool}(n)|=2^{(2^n)}$$
## Algebry Boole'a
Niech $B$ będzie zbiorem z działaniami binarnymi $\lor, \land$ i działaniem unarnym $\neg$ oraz $0, 1\in B$, gdzie $0\neq1$. Taką szóstkę $(B,  \land ,  \lor ,  \neg , 0, 1)$ nazywamy algebrą Boole'a wtedy i tylko wtedy, gdy dla dowolnych $x,y,z\in B$ zachodzi:
- $x\land y=y\land x,\qquad   x\lor y=y\lor x$
- $(x\land y)\land z=x\land (y\land z),\qquad   (x\lor y)\lor z=x\lor (y\lor z)$
- $x\lor (y\land z)=(x\lor y)\land (x\lor z),\qquad  x\land (y\lor z)=(x\land y)\lor (x\land z)$
- $1\land x=x,\qquad  0\lor x=x$
- $\neg x\land x=0,\qquad  \neg x\lor x=1$

Czasem stosuje się alternatywną notację, gdzie operator $\lor$ zastępujemy symbolem $+$, symbol $\land$ zastępujemy symbolem $\cdot$, a symbol $\neg$ zastępujemy $\bar{}$ . Szóstkę $(B,  \land ,  \lor ,  \neg , 0, 1)$ oznaczamy skrótowo jako $B$.

Podstawową algebrą Boole'a nazywamy szóstkę, w której $B={0, 1}$. Zbiór taki nazywamy zbiorem **wartości boolowskich** (ang. *boolean domain*) i oznaczamy symbolem $\mathbb{B}$. Pozostałymi algebrami Boole'a są szóstki, w których $B=\mathbb{B}^n$, gdzie $\mathbb{B}^n=\{0, 1\}^n$ jest produktem kartezjańskim $n$ kopii zbioru $\mathbb{B}$. Operacje logiczne są tutaj wykonywane kolejno po każdej współrzędnej. W każdej algebrze Boole'a elementy $0, 1$ oraz $\neg x$ są określone jednoznacznie. 

Niech $(B,  \land ,  \lor ,  \neg , 0, 1)$ będzie algebrą Boole'a. Wówczas dla każdego $x,y∈B$ zachodzi:
- $x\lor 1=1,\qquad   x\land 0=0$
- $(x\land y)\lor x=x,\qquad   (x\lor y)\land x=x$
- $\neg 0=1,   \neg 1=0,\qquad   \neg (\neg x)=x$
- $x\lor x=x,\qquad   x\land x=x$
- $\neg (x\lor y)=\neg x\land \neg y,\qquad   \neg (x\land y)=\neg x\lor \neg y$

W algebrze Boole'a $(B,  \land ,  \lor ,  \neg , 0, 1)$ relację $\leq$ definiujemy następująco: $$\forall_(x,y\in B)   x\leq y\iff x\lor y=y$$
## Atomy
Niech $(B,  \land ,  \lor ,  \neg , 0, 1)$ będzie nietrywialną algebrą Boole'a. Niezerowy element $a\in B$ nazywamy atomem $B$ wtedy i tylko wtedy, gdy dla każdych $b,c\in B$ zachodzi: $$a=b\lor c\implies a=b\lor a=c$$
Niejedynkowy element $\alpha \in B$ nazywamy co-atomem $B$ wtedy i tylko wtedy, gdy dla każdych $\beta,\gamma\in B$ zachodzi: $$\alpha=\beta\land \gamma\implies \alpha=\beta\lor \alpha=\gamma$$
Niezerowy element $a\in B$ jest atomem algebry $B$ wtedy i tylko wtedy, gdy nie istnieje $x\in B$ taki, że $0<x<a$, analogicznie niejedynkowy element $\alpha\in B$ jest co-atomem algebry $B$ wtedy i tylko wtedy, gdy nie istnieje $\xi \in B$ taki, że $\alpha<\xi<1$.

Liczba różnych atomów i co-atomów algebrze $\mathbb{B}^n$ wynosi dokładnie $n$. Przykładowo atomami $\mathbb{B}^3$  są: $(0, 0, 1), (0, 1, 0), (0, 0, 1)$, natomiast co-atomami $\mathbb{B}^3$ są: $(0, 1, 1), (1, 0, 1), (1, 1, 0)$.

Każdy niezerowy element skończonej algebry Boole'a jest alternatywą różnych atomów tej algebry, natomiast każdy niejedynkowy element skończonej algebry Boole'a jest koniunkcją różnych co-atomów tej algebry.
## Izomorfizm algebr
Niech $B_1,B_2$ będą algebrami Boole'a. Funkcję $f:B_1\rightarrow B_2$ nazywamy **izomorfizmem** $B_1$ i $B_2$ wtedy i tylko wtedy, gdy dla każdych $x,y\in B_1$ zachodzi:
- $f$ jest bijekcją,
- $f(x\land y)=f(x)\land f(y)$,
- $f(x\lor y)=f(x)\lor f(y)$,
- $f(\neg x)=\neg f(x)$,
- $f(0)=0$,
- $f(1)=1$.

Zatem izomorfizmem jest bijekcja zachowująca wszystkie działania. Jeżeli istnieje $f$ będąca izomofizmem to mówimy, że **$B_1$ i $B_2$ są izomorficzne**, co oznaczamy jako: $B_1\cong B_2$.

Dwie skończone algebry Boole'a są izomorficzne, gdy mają taką samą liczbę atomów. Każda skończona algebra Boole'a jest izomorficzna z $\mathbb{B}^n$ dla pewnej liczby naturalnej $n$.
## Indeksy atomu
Dowolną funkcję boolowską $f$ możemy reprezentować za pomocą:
- wielomianów boolowskich,
- tabeli wartości,
- indeksów atomu,
- indeksów co-atomu.

Indeksem atomu $a$ nazywamy ten argument, dla którego funkcja $f$ przyjmuje wartość $1$. Indeks atomu zwykle zapisywany jest jako liczba w systemie dziesiętnym, która odpowiada ciągowi binarnemu, będącemu argumentem. Takie przedstawienie zaczynamy od symbolu $\sum$, po którym wypisuje się liczby dziesiętne odpowiednich atomów.

Indeksem co-atomu $\alpha$ nazywamy ten argument, dla którego funkcja przyjmuje wartość $0$. Takie przedstawienie $f$ zaczynamy od symbolu $\prod$.

> [!example] Przedstaw funkcję $f$ za pomocą indeksów atomów i co-atomów
> $$ f(x, y, z) = (x \land \neg y) \lor z $$
> 
> **1. Obliczamy wartości dla wszystkich argumentów z $\mathbb{B}^3$**
> 
> | $x$ | $y$ | $z$ | $f(x, y, z\text{ })$ | $(x\text{ }y\text{ }z\text{ })_{(10)}$ |
> | :---: | :---: | :---: | :---: | :---: |
> | $0$ | $0$ | $0$ | $0$ | $0$ |
> | $0$ | $0$ | $1$ | $1$ | $1$ |
> | $0$ | $1$ | $0$ | $0$ | $2$ |
> | $0$ | $1$ | $1$ | $1$ | $3$ |
> | $1$ | $0$ | $0$ | $1$ | $4$ |
> | $1$ | $0$ | $1$ | $1$ | $5$ |
> | $1$ | $1$ | $0$ | $0$ | $6$ |
> | $1$ | $1$ | $1$ | $1$ | $7$ |
> 
> **2. Funkcję $f$ reprezentujemy jako indeksy atomów, tam gdzie $f(x, y, z) = 1$:**
> $$ f = \sum(1, 3, 4, 5, 7) $$
> 
> **3. Funkcję $f$ reprezentujemy jako indeksy co-atomów, tam gdzie $f(x, y, z) = 0$:**
> $$ f = \prod(0, 2, 6) $$
## Termy
Literałem zmiennej $x$ nazywamy wartości $x$ lub $\neg x$. **Termem** nazywamy koniunkcję literałów różnych zmiennych $x_i$. **Co-termem** nazywamy alternatywę literałów różnych zmiennych.

**Mintermem** nazywamy term zawierający wszystkie zmienne, a **maxtermem** nazywamy co-term zawierający wszystkie zmienne.

Każdy atom $\mathtt{Bool}(n)$ jest generowany przez dokładnie jeden minterm, analogicznie każdy 
co-atom $\mathtt{Bool}(n)$ jest generowany przez dokładnie jeden maxterm.
## Dysjunkcyjna postać normalna
Każda funkcja boolowska jest generowana przez alternatywę mintermów. Reprezentacja wielomianu boolowskiego w postaci alternatywy mintermów jest nazywana dysjunkcyjną postacią normalną (DNF).

> [!example] Wygeneruj funkcję $f \in \text{Bool}(3)$ daną wzorem
> $$ f(x,y,z) = \neg(x \land (\neg y \Leftrightarrow z)) \Rightarrow y $$ za pomocą DNF.
> 
> **1. Obliczamy wartości dla wszystkich argumentów z $\mathbb{B}^3$**
> 
> | $x$ | $y$ | $z$ | $f(x, y, z\text{ })$ | Mintermy |
> | :---: | :---: | :---: | :---: | :--- |
> | $0$ | $0$ | $0$ | $0$ | |
> | $0$ | $0$ | $1$ | $0$ | |
> | $0$ | $1$ | $0$ | $1$ | $\neg x \land y \land \neg z$ |
> | $0$ | $1$ | $1$ | $1$ | $\neg x \land y \land z$ |
> | $1$ | $0$ | $0$ | $0$ | |
> | $1$ | $0$ | $1$ | $1$ | $x \land \neg y \land z$ |
> | $1$ | $1$ | $0$ | $1$ | $x \land y \land \neg z$ |
> | $1$ | $1$ | $1$ | $1$ | $x \land y \land z$ |
> 
> **2. Rozpisujemy DNF jako alternatywę mintermów**
> $$ \text{DNF}(f) = (\neg x \land y \land \neg z) \lor (\neg x \land y \land z) \lor (x \land \neg y \land z) \lor (x \land y \land \neg z) \lor (x \land y \land z) $$
## Koniunkcyjna postać normalna
Każda funkcja boolowska jest generowana przez koniunkcję maxtermów. Reprezentacja wielomianu boolowskiego w postaci koniunkcji maxtermów jest nazywana koniunkcyjną postacią normalną (CNF).

> [!example] Wygeneruj funkcję $f \in \text{Bool}(3)$ daną wzorem
> $$ f(x,y,z) = \neg(x \land (\neg y \Leftrightarrow z)) \Rightarrow y $$ za pomocą CNF.
> 
> **1. Obliczamy wartości dla wszystkich argumentów z $\mathbb{B}^3$**
> 
> | $x$ | $y$ | $z$ | $f(x, y, z\text{ })$ | Maxtermy |
> | :---: | :---: | :---: | :---: | :--- |
> | $0$ | $0$ | $0$ | $0$ | $x \lor y \lor z$ |
> | $0$ | $0$ | $1$ | $0$ | $x \lor y \lor \neg z$ |
> | $0$ | $1$ | $0$ | $1$ | |
> | $0$ | $1$ | $1$ | $1$ | |
> | $1$ | $0$ | $0$ | $0$ | $\neg x \lor y \lor z$ |
> | $1$ | $0$ | $1$ | $1$ | |
> | $1$ | $1$ | $0$ | $1$ | |
> | $1$ | $1$ | $1$ | $1$ | |
> 
> **2. Rozpisujemy CNF jako koniunkcję maxtermów**
> $$ \text{CNF}(f) = (x \lor y \lor z) \land (x \lor y \lor \neg z) \land (\neg x \lor y \lor z) $$
## Sieci logiczne
Algebra Boole'a stanowi podstawę układów elektrycznych:
- **Switch**: Switch to urządzenie dwustanowe. Może być ustawiony albo w pozycji otwartej albo zamkniętej.
- **System przełączający**: Obwód elektryczny składa się ze źródła energii, wyjścia oraz switchów.
- **Łączenie switchów**: Dwa podstawowe sposoby łączenia switchów to równoległy ($\lor$) i szeregowy ($\land$). Czasami konieczne jest użycie switcha, który jest w pozycji odwrotnej do ustalonego ($\neg$).
- **Sieć logiczna**: Sieć logiczna to matematyczny model systemu przełączającego.
- **Bramki logiczne**: Switche są reprezentowane przez bramki logiczne, źródło energii się pomija. Podstawowe bramki logiczne, to: `NOT`, `AND`, `OR` odpowiadające kolejno: $\neg, \land, \lor$.

