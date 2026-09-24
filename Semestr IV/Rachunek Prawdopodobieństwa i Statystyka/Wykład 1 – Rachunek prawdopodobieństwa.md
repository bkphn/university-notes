## Historia dziedziny
Rachunek prawdopodobieństwa powstał w XVII wieku, w odróżnieni do geometrii, która była bardzo potrzebna w życiu codziennym (np. liczenie objętości beczki), rachunek prawdopodobieństwa przez długi czas nie odnosił się do rzeczywistego świata. Wszystko zmieniło się wraz z wybuchem popularności gier hazardowych kiedy matematycy postanowili „ujażmić” szanse na zwycięstwo graczy w ścisłej, matematycznej strukturze.

Na początku prawdopodobieństwo było traktowane jako częstotliwość otrzymywania jakiegoś wyniku. Początkowo prawdopodobieństwo wyrzucenia reszki opisywało się wzorem: $$P(R)=\frac{n_R}{n_R+n_O}\rightarrow p\in[0, 1]$$gdzie:
- $n_R$ to liczba wyrzuconych rezsek,
- $n_O$ to liczba wyrzuconych orłów.  

Problem z tak zdefiniowanym prawdopodobienstwem był taki, że dokładość wyniku zależała tylko i wyłącznie od liczby i jakości przeprowadzonych testów. Dopiero w 1933 roku powstał aksjomatyczny zestaw reguł opisujący rachunek prawdopodobieństwa.

Na bazie rachunku prawdopodobieństwa powstała dziedzina matematyki nazywana statystyką, która zajmuje się analizą i reprezentacją danych opisujących zdarzenia.
## Zdarzenia
**Eksperymentem stochastycznym** nazywamy eksperyment, którego wyniki nie mogą być przyjmowane z góry. Eksperyment stochastyczny $S$ zwraca nam wyniki $\omega_i$ nazywane **zdarzeniami elementarnymi**. Zbiór wszystkich zdarzeń elementarnych nazywamy **przestrzenią zdarzeń** elementarnych i definiujemy ją jako: $$\Omega=\{\omega_1,\omega_2,\dots\}$$
Dowolny podzbiór $A$ zbioru przestrzeni zdarzeń elementarnych, nazywamy zdarzeniem $A\subseteq \Omega$.
Jeżeli $\omega\in A$ to mówimy, że $\omega$ sprzyja zdarzeniu $A$. Jeżeli $A=\Omega$ to zbiór $A$ nazywamy zdarzeniem pewnym. Jeżeli natomiast $A=\emptyset$ to mówimy, że $A$ jest zdarzeniem niemożliwym.
## Działania na zdarzeniach
Jako, że dowolne zdarzenie $A$ definiujemy jako zbiór $\{a_1,a_2,\dots,a_k\}\subseteq\Omega$. To działania na zdarzeniach wyglądają identycznie do działań na zbiorach.

**Sumę zdarzeń** $A, B$ oznaczamy jako $A\cup B$ i mówimy, że suma zdarzeń $A\cup B$ zachodzi wtedy i tylko wtedy gdy zachodzi $A$ lub zachodzi $B$.

**Iloczyn zdarzeń** $A,B$ oznaczamy jako $A\cap B$ lub w skrócie $AB$ i mówimy, że iloczyn zdarzeń $A\cap B$ zachodzi wtedy i tylko wtedy, gdy zachodzi $A$ i zachodzi $B$. Jeżeli $A\cap B=\emptyset$ to mówimy, że zdarzenia $A,B$ są **rozłączne**.

**Różnicę zdarzeń** $A, B$ oznaczamy jako $A\setminus B$ i mówimy, że różnica zdarzeń $A\setminus B$ zachodzi wtedy i tylko wtedy, gdy zachodzi $A$ i nie zachodzi $B$.

**Dopełnieniem zdarzenia** $A$ nazywamy zbiór $\Omega\setminus A$ i oznaczamy jako $\overline{A}$.
## Prawa na zdarzeniach
W oparciu własności operacji sumy i iloczynu oraz o prawa de Morgana możemy zdefiniować podstawowe prawa na zdarzeniach:
- **Rozdzielność względem sumy**: $$A\cup (B\cap C)=(A\cup B)\cap (A\cup C)$$
- **Rozdzielność względem iloczynu**: $$A\cap (B\cup C)=(A\cap B)\cup (A\cap C)$$
- **Pierwsze prawo de Morgana**: $$\overline{(A\cup B)}=\overline{A}\cap \overline{B}$$
- **Drugie prawo de Morgana**: $$\overline{(A\cap B)}=\overline{A}\cup \overline{B}$$
## Prawdopodobieństwo
Dana jest dyskretna (skończona) przestrzeń zdarzeń elementarnych $\Omega=\{\omega_1,\omega_2,…,\omega_n \}$. Niech każdemu wynikowi $\omega_i$ odpowiada liczba $p(\omega_i )$. Zbiór wszystkich liczb $p(\omega_i )$ nazywamy prawdopodobieństwem, jeżeli spełnione są warunki:
- $p(\omega_i )\geq 0$
- $\sum_{i=1}^\infty p(\omega_i ) =1$

Jeśli $A$ jest zdarzeniem w przestrzeni $\Omega$ to prawdopodobieństwem zdarzenia $A$ nazywamy sumę wszystkich wartości $p(\omega)$, gdzie $\omega\in A$. $$P(A)=\sum_{\omega\in A}p(\omega)$$
## Własności prawdopodobieństwa
Korzystając z przyjętych definicji możemy określic podstawowe własności prawdopodobieństwa dla dowolnych zdarzeń $A,B\subseteq \Omega$:
- $P(\Omega)=1$
- $P(\emptyset)=0$
- $A\subset B\implies P(B\setminus A)=P(B)-P(A),  P(A)\leq P(B)$
- $P(A\cup B)=P(A)+P(B)−P(AB)\implies P(A\cup B)\leq P(A)+P(B)$
- $AB=\emptyset \implies P(A\cup B)=P(A)+P(B)$
- $A_i, i\geq 1, A_i A_j=\emptyset, i\neq j\implies P\left( \bigcup_{i=1}^\infty A_i \right)=\sum_{i=1}^\infty P(A_i)$
## Schemat klasyczny
Schemat klasyczny prawdopodobieństwa stosujemy gdy dla przestrzeni $\Omega=\{\omega_1, \omega_2,\dots,\omega_n \}$ prawdopodobieństwo dwóch dowolnych zdarzeń jest jednakowe: $\forall_{i,j\leq n}  p(\omega_i )=p(\omega_j )$. W schemacie klasycznym $p(\omega_i )=\frac{1}{n}$. 

Schemat klasyczny jest wyjątkowo dobrze poznany z powodu faktu, że większość hazardowych gier karcianych podlega właśnie pod schemat klasyczny.

Niech dane będzie zdarzenie $A=\{\omega_1,\dots,\omega_k \}$ w schemacie klasycznym, wtedy: $$P(A)=\sum_{i=1}^k p(\omega_{i})=\frac{k}{n}$$
## Kombinatoryka
Kombinatoryka jest dziedziną matematyki zajmującą się badaniem skończonych bądź przeliczalnych struktur matematycznych. Kombinatorykę możemy stosować do analizowania przestrzeni zdarzeń.

Liczbę wszystkich możliwych ustawień n elementów, w przypadku gdy żaden z elementów nie może się powtórzyć nazywamy liczbą **permutacji bez powtórzeń** i definiujemy wzorem: $$P_n=n!$$
Liczbę wszystkich możliwych wyborów $k$ elementów z puli $n$-elementowej nazywamy liczbą **kombinacji bez powtórzeń** i określamy jako: $$C_{n}^k =\binom{n}{k}=\frac{n!}{k!⋅(n-k)!}$$
Liczbę wszystkich możliwych ustawień $k$ elementów z puli $n$-elementowej nazywamy liczbą **wariacji bez powtórzeń** i określamy jako: $$A_n^k=\frac{n!}{(n−k)!}$$
Liczbę wszystkich możliwych wyborów $k$ elementów z puli $n$-elementowej, z możliwością ponownego wybrania już wybranego elementu (tzw. ze zwracaniem) nazywamy liczbą **kombinacji z powtórzeniami** i określamy jako: $$\overline{C}^k_{n}=\binom{n+k-1}{k}$$
Liczbę wszystkich możliwych wyborów $k$ elementów z puli $n$-elementowej gdy $k\geq n$, w taki sposób, by każdy element wybrać co najmniej raz, nazywamy liczbą podziałów elementów na grupy i definiujemy jako: $$C_{k−1}^{n−1}=\binom{k-1}{n-1}$$
## Zdarzenia niezależne
Zdarzenia $A,B$ nazywamy niezależnymi, jeśli $P(A\cap B)=P(A)\cdot P(B)$. Zdarzenia $A_1,A_2,\dots,A_n$ nazywamy niezależnymi, gdy: $$P\left(\bigcap_{i=1}^n A_{i}\right)=\prod_{i=1}^n P(A_{i})$$
Zdarzenia niezależne i rozłączne nie są tym samym. Zdarzenia $A,\Omega$ zawsze są zdarzeniami niezależnymi, ponieważ:
$$P(A\cap \Omega)=P(A)=1\cdot P(A)=P(\Omega)\cdot P(A)$$
Jeśli zdarzenia $A,B$ są niezależne to zdarzenia $A,\overline{B}$ też są niezależne.
