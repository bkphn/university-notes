## Relacyjny model danych
Relacyjny model danych jest aktualnie najbardziej użytecznym modelem danych, bazuje on na pojęciu **relacji**, rozumianej jako dwuwymiarowa tabela do której wypisywane są dane.

Ze względu na brak elastyczności modelu relacyjnego na etapie projektowania łatwiej jest zaprojektować bazę w oparciu o model związków encji, a następnie przejść do modelu relacyjnego.
## Budowa relacji
Dane w modelu relacyjnym reprezentuje się za pomocą dwumiarowych tablic, zwanych **relacjami**:

| $\mathtt{FILM}$   | $\mathtt{ROK}$ |
| ----------------- | -------------- |
| `Terminator`      | `1984`         |
| `Łowca Androidów` | `1982`         |

W relacjach możemy wyróżnić następujące elementy:
- **Atrybuty**: Atrybuty umieszczamy w nagłówkach tabeli (relacji). Służą one do reprezentowania cech obiektów. Atrybuty oddają znaczenie danych umieszczanych poniżej.
- **Schematy**: Nazwę relacji oraz zbiór atrybutów nazywa się schematem relacji. Schemat relacji oznaczamy literą $R$ i zapisujemy jako $R(A_{1},\dots,A_{n})$ gdzie $A_{i}$ to kolejne atrybuty.
- **Krotki**: Wiersze tabeli (relacji), nie wliczając wiersza atrybutów nazywamy krotkami. W każdej krotce reprezentowany jest pojedynczy obiekt. Pojedyncza krotka bez schematu relacji nie jest czytelna, bo nie wiemy jakie atrybuty reprezentują kolejne wartości.
- **Relacja**: Relacją nazywamy zbiór krotek. Nie może być sytuacji, że w jednej tabeli znajdą się dwie takie same krotki.
- **Dziedziny**: W modelu relacyjnym każda składowa relacji musi mieć określony typ atomowy, tzn. musi być typem niepodzielnym. Wartość atrybutu nie może być rekordem, listą, ani tablicą. Zakłada się, że każdy atrybut jest powiązany z dziedziną, czyli z pewnym typem elementarnym.
- **Stan relacji**: Stan relacji $R$ oznaczamy jako $r(R)$, oznacza on zbiór krotek relacji $R$ należących do bazy danych.
- **Baza danych**: Relacyjną bazę danych oznaczamy literą $S$ i definiujemy jako zbiór schematów relacji, $S=\{R_{1},\dots,R_{m}\}$
- **Klucz obcy**: Zbiór atrybutów $F_{K}$ w schemacie relacji $R_{1}$ odwołujący się do $R_{2}$ jest kluczem obcym tego schematu, gdy spełnione są warunki:
	- Wartości atrybutów $F_{K}$ należą do tej samej dziedziny co argumenty pełniące rolę klucza głównego w $R_{2}$
	- Wartość klucza obcego w krotce $t_{1}$ w stanie $r(R_{1})$ musi być równa wartości klucza głównego pewnej innej krotki $t_{2}$ w stanie $r(R_{2})$.
- **Klucz główny**: Atrybut klucza oznaczamy przez $P_{K}$, musi on być unikalny dla każdej krotki.
## Ograniczenia
W relacyjnym modelu bazy danych musimy nakładać pewne ograniczenia na dane, jakie możemy przechowywać, jako atrybuty krotek:
- **Ograniczenia dziedziny**: Wartość dowolnego atrybutu musi być atomowa
- **Ograniczenie wartości pustych**: Na atrybuty można nałożyć dodatkowe ograniczenie, które określa czy w można stosować atrybut `NULL`.
- **Ograniczenia klucza**: Często może zdarzyć się, że dwa różne obiekty będą miały identyczne atrybuty, zbiór atrybutów nazywamy wtedy nadkluczem relacji. Aby zapobiec sytuacji nierozróżnialności dwóch krotek musimy do każdej krotki dodać atrybut klucza. Atrybut klucza musi być niezmienny i niepusty by zapewnić poprawne działanie bazy danych
## Więzy integralności
Więzy integralności informują o ograniczeniach wynikających z modelu relacyjnego:
- **Więzy integralności encji**: Żadna wartość atrybutu klucza głównego nie może mieć wartości pustej.
- **Więzy integralności odwołań**: Krotka należąca do jednej relacji i odwołująca się do innej, zawsze musi odwoływać się do istniejącego obiektu.

Jeżeli warunki te są spełnione w modelu związków encji to na jej podstawie możemy utworzyć model relacyjny.
## Tworzenie modelu relacyjnego
Opiszemy teraz kolejne kroki algorytmu odwzorowującego model E/R w relacyjny schemat bazy danych.

>[!abstract] Algorytm odwzorowujący model E/R w relacyjny schemat bazy danych
> 1. **Odwzorowanie zwykłych zbiorów encji**
>Dla każdego zbioru encji $E$ w modelu E/R należy stworzyć odpowiadającą mu relację  w modelu relacyjnym, która będzie zawierała wszystkie atrybuty proste typu zbioru encji .
> 2. **Odwzorowanie słabych zbiorów encji**
> Dla każdego słabego zbioru encji należy stworzyć relację zawierającą wszystkie proste atrybuty zbioru encji, ponadto każda taka relacja powinna dodatkowo zawierać atrybut klucza głównego.
> 3. **Odwzorowywanie związków binarnych** 
> Podejście oparte na wykorzystaniu klucza obcego. Wybieramy jedną z relacji odpowiadających jednemu ze zbiorów encji tego związku i wstawiamy w niej klucz główny drugiej relacji tego związku.
> 4. **Odwzorowanie związków binarnych** 
> W relacji reprezentującej zbiór encji będący w związku po stronie  wstawiamy dodatkowy atrybut klucza obcego reprezentującego klucz główny relacji reprezentującej zbiór encji w związku po stronie .
>5. **Odwzorowanie związków binarnych** 
> Należy stworzyć nową relację dla tego związku. Relacja powinna posiadać klucze obce wskazujące na klucze główne zbiorów encji będących w tym związku. Relacja ta powinna zawierać również wszystkie atrybuty proste tego związku.
> 6. **Odwzorowanie atrybutów wielowartościowych**
> Dla każdego atrybutu wielowartościowego należy stworzyć nową relację, która zawiera atrybuty odpowiadające wielowartościowemu atrybutowi zbiorów encji i atrybutom klucza głównego relacji reprezentującej zbiór encji posiadający atrybut wielowartościowy.
>7. **Odwzorowanie związków wieloargumentowych**
> Dla każdego wieloargumentowego związku należy stworzyć nową relację zawierającą klucze główne wszystkich relacji reprezentujących zbiory encji należących do tego związku oraz atrybuty proste związku.
