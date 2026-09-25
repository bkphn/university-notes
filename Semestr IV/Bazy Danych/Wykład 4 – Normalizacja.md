## Zależności funkcyjne
Atrybut $B$ jest zależny funkcyjnie od relacji $R$ od atrybutów $A_1,A_2,\dots,A_n$ jeśli dla dowolnych dwóch krotek tej relacji zgodność atrybutów $A_1,A_2,\dots,A_n$ pociąga za sobą zgodność atrybutu $B$, co zapisujemy jako: $A_1,A_2,\dots,A_n\rightarrow B$.

Przez zgodność atrybutu $A$ rozumiemy, że krotki mają taką samą wartość składowej odpowiadającej atrybutowi $A$.

Jeśli zbiór $A_1,A_2,\dots  ,A_n$ określa jednoznacznie więcej atrybutów $B_1,B_2,\dots  ,B_m$ to zależność tą oznaczamy jako $A_1,A_2,\dots  ,A_n\rightarrow B_1,B_2,\dots  ,B_m$.

Zależność $A_1,A_2,\dots  ,A_n\rightarrow B$ jest zależnością trywialną jeśli $B=A_i$,  $i\in\{1,\dots  ,n\}$. 

## Klucz
Zbiór atrybutów $\{A_1,A_2,\dots  ,A_m \}$ tworzy klucz relacji, jeśli:
- wszystkie pozostałe atrybuty relacji są funkcyjnie od nich niezależne;
- nie istnieje właściwy podzbiór zbioru $\{A_1,\dots  ,A_m\}$ od którego pozostałe atrybuty relacji $R$ są zależne funkcyjnie.

Każdy zbiór atrybutów relacji $R$, który zawiera klucz tej relacji nazywany jest nadkluczem.

Niech $R= \mathtt{PRACOWNICY(imie, nazwisko, pesel, miasto, kod\_pocztowy, data\_ur, wiek, nr\_dom)}$
Z definicji klucza wynika zależność funkcyjna:

$$\mathtt{pesel} \rightarrow  \mathtt{imie, nazwisko, miasto, kod\_pocztowy, data\_ur, wiek, dom}$$

Ponadto można wyróżnić zależności:
- $\mathtt{kod\_pocztowy} \rightarrow \mathtt{miasto}$
- $\mathtt{data\_ur} \rightarrow \mathtt{wiek}$

## Anomalie
Problemy, które powstają, gdy sami próbujemy wstawić do relacji zbyt wiele danych nazywamy **anomaliami**. Możemy wyróżnić następujące typy anomalii:
- **Redundancja**: Redundancja oznacza, że te same dane powtarzają się niepotrzebnie w krotkach.
- **Anomalia modyfikacji**: Anomalia modyfikacji oznacza, że w trakcie modyfikacji dane zostają poprawione tylko w jednej krotce, a w innych nie.
- **Anomalia usunięć**: Anomalia usunięć oznacza, że gdy jako pewien atrybut ustawimy wartość pustą, część danych zostaje niepowrotnie utracona.

## Dekompozycja relacji
Sposobem na uniknięcie anomalii jest dekompozycja relacji. Sprowadza się ona do podziału atrybutów relacji $R$ na dwa schematy nowych relacji. Relację $R$ o schemacie $R(A_1,\dots  ,A_n )$ dekomponujemy na dwie relacje $S,T$ o schematach $S(B_1,\dots  ,B_m )$ oraz $T(C_1,\dots  ,C_k )$, tak aby:

$$\{A_1,\dots  ,A_n \}=\{B_1,\dots  ,B_m \}\cup \{C_1,\dots  ,C_k\}$$

Krotki relacji $S$ powstają przez rzutowanie wszystkich krotek z relacji $R$ na zbiór atrybutów $\{B_1,\dots  ,B_m\}$. Oznacza to, że z każdej krotki $t$ z bieżącej instancji relacji $R$ pobieramy wartości atrybutów i tworzymy w ten sposób krotkę relacji $S$. Analogicznie postępujemy w przypadku relacji $T$.

## Normalizacja
Normalizacja polega na wykryciu anomalii w relacjach i wykonaniu dekompozycji prowadzącej do wyeliminowania wad stworzonych relacji. Jest wiele postaci normalnych relacji, wśród nich możemy wyróżnić:
- **Pierwsza postać normalna 1NF**: Relacja spełnia pierwszą postać normalną, jeśli posiada tylko wartości niepodzielne (atomowe).
- **Druga postać normalna 2NF**: Relacja spełnia drugą postać normalną, jeśli spełnia 1NF oraz kolumny nie wchodzące w skład klucza głównego są zależne od całego klucza głównego.
- **Trzecia postać normalna 3NF**: Relacja jest w trzeciej postaci normalnej, jeśli jest 2NF oraz każdy niekluczowy atrybut nie zależy funkcyjnie od pozostałych atrybutów nie należących do klucza.
- **Postać normalna Boyce'a-Codda BCNF**: Relacja $R$ jest w postanci BCNF, gdy dla każdej nietrywialnej zależności $A_1,\dots  ,A_n\rightarrow B$ zbiór $\{A_1,\dots  ,A_n \}$ jest nadkluczem relacji $R$. BCNF zapewnia, że w relacji nie ma anomalii.

>[!abstract] Dekompozycja do BCNF
> 1. Znajdujemy funkcyjną zależność $A_1,\dots  ,A_n\rightarrow B_1,\dots  ,B_m$  naruszającą BCNF.
> 2. Na podstawie zależności naruszającej BCNF tworzymy pierwszą relację zawierającą atrybuty $\{A_1,\dots  ,A_n,B_1,\dots  ,B_m \}$.
> 3. Drugą relację tworzą atrybuty po lewej stronie zależności $\{A_1,\dots  ,A_n \}$ i pozostałe atrybuty należące do rozważanej relacji, które nie należą ani do zbioru $A$ ani $B$.
>4. Dla każdej z otrzymanych relacji powtarzamy proces dopóki nie otrzymamy BCNF.

