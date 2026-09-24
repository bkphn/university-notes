## Operacje relacji
W modelu relacyjnym danych istnieje zestaw operacji na danych, które przedstawiają działanie modelu relacyjnego z perspektywy użytkownika. Operacje na danych zdefiniowane są w sposób algebraiczny i tworzą algebrę relacji. Algebrę relacji opieramy na zbiorze wszystkich krotek, definiowanym następująco: $$\mathcal{S}=\{(s_{j1}, s_{j2},\cdots,s_{jn}): j\in\{1,…,m\} \}$$
Operacje relacji są oparte na operacjach teoriomnogościowych, jednak oparcie ich w modelu relacyjnym pozwala na definicje nowych działań:
- **Suma**: Suma zbiorów $R,S$ jest zbiorem, do którego należą wszystkie elementy z $R$ i $S$. $$R\cup S$$
- **Przekrój**: Przekrój zbiorów $R,S$ jest zbiorem, do którego należą tylko elementy, należące jednocześnie do $R$ i $S$. $$R\cap S$$
- **Różnica**: Różnica zbiorów $R,S$ jest zbiorem, do którego należą wszystkie elementy z $R$ nie występujące w zbiorze $S$. $$R\setminus S$$
- **Iloczyn kartezjański**: Iloczyn kartezjański relacji $R,S$ jest zbiorem wszystkich par, z których pierwsza należy do zbioru $R$, a druga do zbioru $S$. $$R\times S$$
- **Złączenie naturalne**: Złączenie naturalne relacji $R,S$ jest nową relacją, która łączy relacje $R,S$ łącząc ze sobą powtrzające się atrybuty. $$R\bowtie S$$
- **Złączenie theta**: Złączenie theta (ang. *$\theta$-join*) tworzy nową relację, który łączy ze sobą relacje $R,S$ zgodnie z warunkiem $\theta$. $$R\bowtie_{\theta} S$$
- **Rzutowanie**: Rzutowanie relacji $R$ dla atrybutów $A_1,…,A_n$ zwraca nową relację składającą się z tych atrybutów. $$\pi_{A_{1}, \dots,A_{n}}(R)$$
- **Selekcja**: Selekcja relacji $R$ dla warunku $\theta$ zwraca nową relację składającą się z krotek spełniających warunek $\theta$. $$\sigma_{\theta}(R)$$
- **Przemianowanie**: Przemianowanie schematu relacji $R(A_1,\dots,A_n )$ zwraca kopię tej relacji określoną jako $S$, gdzie każdy atrybut zostaje kolejno przemianowany na $B_1,\dots,B_n$. $$\rho_{S(B_{1},\dots,B_{n})}(R)$$
## Rzutowanie
Z operacji rzutowania korzysta się przy tworzeniu nowej relacji, która powstaje z relacji $R$ poprzez usunięcie pewnych kolumn. Nową relację, która powstaje przez zachowanie atrybutów $A_1,\dots,A_n$ oznaczamy jako: $$\pi_{A_1,\dots,A_n} (R)$$
odpowiada ona poleceniu `SELECT` $A_1,\dots,A_n$ `FROM` $R$.

Przykładowo dana jest relacja $R$:

| $\mathtt{FILM}$   | $\mathtt{AKTOR}$        | $\mathtt{ROK\_WYDANIA}$ |
| ----------------- | ----------------------- | ----------------------- |
| `Terminator`      | `Arnold Schwarzenegger` | `1984`                  |
| `Łowca Androidów` | `Harrison Ford`         | `1982`                  |

Wyrażenie $π_{\mathtt{FILM, AKTOR}}(R)$ ma postać:

| $\mathtt{FILM}$   | $\mathtt{AKTOR}$        |
| ----------------- | ----------------------- |
| `Terminator`      | `Arnold Schwarzenegger` |
| `Łowca Androidów` | `Harrison Ford`         |
## Selekcja
W wyniku zastosowania selekcji dla relacji $R$ powstaje nowa relacja, która zawiera tylko część krotek relacji $R$. Krotki relacji wynikowej są wybierane według kryterium, które określa warunek $\theta$ narzucony na krotki relacji $R$. Nową relację będącą wynikiem selekcji oznaczamy: $$\sigma_{\theta}(R)$$odpowiada ona poleceniu `WHERE` $\theta$.

$\theta$ jest wyrażeniem warunkowym, w którym operandami mogą być stałe lub atrybuty relacji. Wartość wyrażenia $\theta$ jest obliczana dla każdej krotki $t$ relacji $R$ w ten sposób, że w miejsce atrybutów wstawiane są odpowiednie składowe krotki $t$. Jeśli warunek $\theta$ jest spełniony dla krotki $t$ to jest ona dołączana do relacji $\sigma_\theta (R)$.

Przykładowo dana jest relacja $R$:

| $\mathtt{FILM}$   | $\mathtt{AKTOR}$        | $\mathtt{ROK\_WYDANIA}$ |
| ----------------- | ----------------------- | ----------------------- |
| `Terminator`      | `Arnold Schwarzenegger` | `1984`                  |
| `Łowca Androidów` | `Harrison Ford`         | `1982`                  |

Wyrażenie $\sigma_{1983 > \mathtt{ROK\_WYDANIA}}(R)$ ma postać:

| $\mathtt{FILM}$ | $\mathtt{AKTOR}$        | $\mathtt{ROK\_WYDANIA}$ |
| --------------- | ----------------------- | ----------------------- |
| `Terminator`    | `Arnold Schwarzenegger` | `1984`                  |
## Złączenie naturalne
Operacja złączenia naturalnego relacji $R,S$ polega na połączeniu w pary krotek, które mają identyczne wartości dla określonych atrybutów. Złączenie naturalne relacji $R,S$ oznaczamy jako: $$R\bowtie S$$
odpowiada ono poleceniu `JOIN` $S$. 

Załóżmy, że atrybuty $A_1,\dots, A_n$ występują w obu schematach relacji $R,S$. Wówczas krotka $r\in R$ zostaje połączona w parę z krotką $s\in S$ jeśli wartości składowych $A_1,\dots,A_n$ są takie same.

Przykładowo dana jest relacja $R$:

| $\mathtt{FILM}$   | $\mathtt{AKTOR}$        |
| ----------------- | ----------------------- |
| `Terminator`      | `Arnold Schwarzenegger` |
| `Łowca Androidów` | `Harrison Ford`         |
| `Gwiezdne Wojny`  | `Mark Hamill`           |
oraz relacja $S$:

| $\mathtt{FILM}$   | $\mathtt{ROK\_WYDANIA}$ |
| ----------------- | ----------------------- |
| `Terminator`      | `1984`                  |
| `Łowca Androidów` | `1982`                  |
| `Szczęki`         | `1975`                  |
Złączenie $R\bowtie S$ ma postać:

| $\mathtt{FILM}$   | $\mathtt{AKTOR}$        | $\mathtt{ROK\_WYDANIA}$ |
| ----------------- | ----------------------- | ----------------------- |
| `Terminator`      | `Arnold Schwarzenegger` | `1984`                  |
| `Łowca Androidów` | `Harrison Ford`         | `1982`                  |

Czasem konieczne jest złączenie krotek relacji według innego kryterium niż w złączeniu naturalnym. **Złączenie theta** relacji $R,S$ oznaczamy symbolem $R\bowtie_\theta S$ i definiujemy następująco: $$R \bowtie_{\theta} S=\sigma_{\theta}(R\times S)$$
Czasem konieczne jest zachowanie wszystkich rekordów przy złączaniu tabel, przydaje się wtedy złączenie zewnętrzne, które ustawia każdy atrybut niesparowanego rekrodu na wartość `NULL`.
Złączenie zewnętrzne oznaczamy jako: $$R \operatorname{⟗} S$$
co odpowiada poleceniu `OUTER JOIN` $S$.

Złączenie zewnętrzne $R \operatorname{⟗} S$ ma postać:

| $\mathtt{FILM}$   | $\mathtt{AKTOR}$        | $\mathtt{ROK\_WYDANIA}$ |
| ----------------- | ----------------------- | ----------------------- |
| `Terminator`      | `Arnold Schwarzenegger` | `1984`                  |
| `Łowca Androidów` | `Harrison Ford`         | `1982`                  |
| `Gwiezdne Wojny`  | `Mark Hamill`           | `NULL`                  |
| `Szczęki`         | `NULL`                  | `1975`                  |
## Złączenia jednostronne
Często zamiast łączyć tabele zależy nam na filtrowaniu danych na podstawie innej tabeli, w grę wchodzą wtedy złączenia jednostronne, możemy wyróżnić:
- **Pół-złączenia**: Półzłączenia zwracają tylko rekordy, które należałyby do złączenia naturalnego dwóch tabel: $$R \ltimes S=\pi_{r_{i}\in R}(R\bowtie S)$$
- **Złączenia zewnętrzne**: Jednostronne złączenia zewnętrzne zwracają, złączenie dwóch tabel, a w miejscach w których druga tabela nie mogła znaleźć pasujących rekordów, ustawiane są wartości `NULL` dla każdego z atrybutów. Odpowiadają one poleceniom `LEFT JOIN` oraz `RIGHT JOIN`: $$(R\operatorname{⟕}S)\cup (R\operatorname{⟖}S)=R\operatorname{⟗}S$$
- **Anty-złączenia**: Anty-złączenia zwracają tylko rekordy, które nie znalazły pasujących rekordów do sparowania: $$R\triangleright S=R\setminus R \ltimes S$$
## Więzy relacji
W algebrze relacji istnieją dwa sposoby określania więzów. Wyrażenie $R=\emptyset$ stanowi więzy, które można interpretować jako fakt, że relacja $R$ nie zawiera żadnych krotek. Wyrażenie $R\subseteq S$ oznacza natomiast, że każda krotka relacji $S$ należy również do relacji $R$.

Jeśli encja $E$ jest połączona więzami integralności z encją $F$ to encja $F$ musi istnieć. Możemy to zapisać jako: $$\pi_{A_1} (E)\subseteq \pi_{B_1} (F)$$
## Zależność funkcyjna
W algebrze relacyjnej parę krotek określamy jako iloczyn kartezjański. Stąd, aby wyrazić zależność funkcyjną musimy wykonać selekcję krotek iloczynu kartezjańskiego elementów tej samej relacji, które spełniają warunek równości atrybutów po lewej i różności po prawej stronie zależności.

Żeby zależność funkcyjna była spełniona, relacja będąca wynikiem wspomnianej selekcji musi być pusta: $$\sigma_{R_A=S_A  \land R_B\neq S_B} (R\times S)=∅$$
## Multizbiory
Multizbiorem (bądź wielozbiorem) nazywamy zbiór, w którym dwa identyczne elementy są rozróżnialne. W klasycznych zbiorach: $\{1\}\cup\{1\}=\{1\}$, dodanie drugiego takiego samego elementu nie modyfikuje zawartości zbioru, natomiast jeżeli operujemy na mutlizbiorach, to suma multizbiorów $\{1\} \uplus \{1\}=\{1, 1\}$. W multizbiorach, tak jak w zwykłych zbiorach, kolejność elementów nie wpływa na zawartość multizbioru $\{1, 2, 1\}=\{1, 1, 2\}$, to odróżnia multizbiór od krotki.

Multizbiory często mogą występować jako składowe relacji, przykładowo przechowując w tabeli dane o imieniu i nazwisku, jest możliwe, że pojawią się dwie osoby, o identycznych danych. Operowanie na wielozbiorach pozwala na przyspieszenie operacji na relacjach, przykładowo obliczając sumę dwóch relacji $A\cup B$, nie musimy już dłużej sprawdzać czy obecnie dodawana krotka $t$ już należy do sumy $A\cup B$.
