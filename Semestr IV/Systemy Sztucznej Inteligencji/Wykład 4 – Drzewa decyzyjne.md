## Drzewa decyzyjne
**Drzewa decyzyjne**, zwane również drzewami klasyfikacyjnymi to modele systemów ekspertowych. Klasyfikacji drzewa zaczyna się w jego **korzeniu**, natomiast kończy po dotarciu do liścia. Każdy **węzeł** drzewa jest odpowiedzialny za test na danym atrybucie.

Każda **gałąź** reprezentuje połączenie cech. Opis klasy jest reprezentowany przez liść danego drzewa. Proces klasyfikacji to przejście od korzenia do liścia danego drzewa. Takie drzewa są wykorzystywane do uczenia ponieważ pozwalają na określenie danego obiektu na podstawie jego cech.

## Zstępowanie
Drzewa decyzyjne buduje się poprzez działanie nazywane **zstępowaniem**. Zstępowaniem nazywamy wyjście z jednego korzenia do kolejnego poziomu. W efekcie, podejmując jedną decyzję, możemy spotkać się z konsekwencją podjęcia kolejnej.

## Kryterium stopu
Załóżmy, że drzewo konstruowane w sposób rekurencyjny. Zaczynamy od korzenia i przemieszczamy się w dół podejmując decyzje czy stworzyć kolejny liść czy nie.  Jeśli nasze kryterium będzie spełnione, stworzymy liść i na podstawie podzbioru ustalamy etykietę. W drugim przypadku, tworzymy węzeł i wybieramy test.

Liść tworzymy wtedy i tylko wtedy, gdy spełniony jest jeden z warunków:
- Podzbiór zawiera przykłady należące tylko do jednej klasy.
- Podzbiór jest pusty.
- Znacząca większość pochodzi z jednej klasy.
- Zbiór testów jest pusty.

## Testy
Określając warunek podziału korzystamy z tak zwanych testów binarnych. Służą one do dzielenia zbioru danych na mniejsze, bardziej jednorodne podzbiory. W drzewach decyzyjnych każdy węzeł zawiera test, który decyduje którą gałęzią powinien podążyć badany obiekt $\mathbf{x}\in P$. Możemy wyróżnić trzy rodzaje testów:
- **Testy równościowe**

$$t(\mathbf{x})=\begin{cases}
1, \quad \operatorname{atr}(\mathbf{x})=u \\
0, \quad \operatorname{atr}(\mathbf{x})\neq u
\end{cases}$$

- **Testy przynależnościowe**

$$t(\mathbf{x})=\begin{cases}
1, \quad \operatorname{atr}(\mathbf{x})\in U \\
0, \quad \operatorname{atr}(\mathbf{x})\not \in U
\end{cases}$$

- **Testy progowe**

$$t(\mathbf{x})=\begin{cases}
1, \quad \operatorname{atr}(\mathbf{x})\leq \theta \\
0, \quad \operatorname{atr}(\mathbf{x})\ge \theta
\end{cases}$$

Przez $\operatorname{atr}(\mathbf{x})=\mathbf{x}_i$ rozumiemy sprawdzany aktualnie atrybut obiektu $\mathbf{x}$. $U$ oznacza zbiór pewnych atrybutó, a $u$ pewien atrybut. Natomiast przez $\theta$ rozumiemy środek posortowanego zbioru atrybutów obiektów $\mathbf{x}_j\in P$. Przez $0, 1$ rozumiemy tutaj podążenie prawą lub lewą ścieżką drzewa.

## Przyrost informacji
Niech $P$ oznacza zbiór wszystkich obiektów w obecnym węźle. Przez $D$ oznaczamy wszystkich możliwych klas decyzyjnych np. $D=\{\mathtt{chory}, \mathtt{zdrowy}\}$. Niech $P^d$ oznacza zbiór wszystkich obiektów w klasie $d\in D$. Niech $R$ oznacza zbiór wszystkich możliwych wyników pewnego testu $t$ (zbiór wszystkich gałęzi wychodzących z węzła), a przez $P_r$ rozumiemy zbiór wszystkich elementów, które wpadają do gałęzi $r\in R$ po teście $t$.

Kryterium wyboru stopu to jeden z najważniejszych elementów procesu zstępującego. Całość polega na wyborze najlepszego atrubutu, który poddajemy testowi $t$. W praktyce testy powinny podzielić zbiór $P$ na takie podzbiory, które są silnie zróżnicowane.

Przyrostem informacji nazywamy różnicę entropii pewnego zbioru $P$ oraz entropii zbioru $P$ po teście $R$. Przyrost informacji zazwyczaj oznacza się jako $\text{Gain}$. Matematycznie przyrost informacji określa dokładnie to samo co informacja wzajemna $I(P;R)$, dla przejrzystości, to tego zapisu będziemy używać. Możemy powiedzieć, że przyrost informacji dany jest wzorem:

$$I(P;R)=H(P)-H(P\mid R)$$

Chcąc wyznaczyć najlepszy test zależy nam na zmaksymalizowaniu ilości informacji po teście $R$, zależy nam więc na wartości $\operatorname{argmax}_{R}I(P;R)$. 

Entropię $H(P)$ obliczamy ze wzoru:

$$H(P)=-\sum_{d\in D} \frac{|P^d|}{|P|}\cdot \log_{2}\left( \frac{|P^d|}{|P|} \right)$$

Entropię warunkową $H(P \mid R)$ obliczamy ze wzoru:

$$H(P\mid R)=\sum_{r\in R} \frac{|P^d|}{P}\cdot H(P_{r})=\sum_{r\in R} \frac{|P_{r}|}{|P|}\cdot \left( \sum \frac{|P_{r}^d|}{|P_{r}|} \cdot \log_{2}\left( \frac{|P_{r}^d|}{|P_{r}|} \right) \right)$$

Oczywiście możemy przyjąć dowolne inne kryterium wyboru testu, zamiast maksymalizować wartość $I(P ;R)$ możemy przykładowo minimalizować wartość $H(P)$.

## Miary Giniego
Innym kryterium wyboru testu jest tzw. wybór na podstawie indeksu Giniego. Współczynnikiem bądź indeksem Giniego nazywamy miarę nierównomierności rozkładu pewnej zmiennej losowej. 

Niech $Y=\{y_1,y_2,\dots, y_n \}$ będzie zbiorem obserwacji ułożonych rosnąco. **Współczynnik Giniego** zbioru $Y$ oznaczamy jako $G(Y)$ i definiujemy wzorem:

$$G(Y)= \frac{\sum_{i=1}^n (2i-n-1)y_{i}}{n^2 \sum_{i=1}^n\left( \frac{y_{i}}{n} \right)}$$

Współczynnik Giniego zawsze przyjmuje wartości w przedziale $[1, 0]$. Jeśli $G(Y)=0$ to próbki rozłożone są równomiernie, a więc wzrost wartości indeksu oznacza wzrost nierównomierności rozkładu.

**Nieczystość Giniego** (ang. *Gini Impurity*) oznaczamy jako $I_G$ bądź $\text{Gini}$. Określa ona jak bardzo wymieszane są klasy w danym węźle (przykładowo jak dużo chorych i zdrowym pacjentów mamy w naszej grupie). Nieczystość Giniego wykorzystuje się przy wyznaczaniu prawdopodobieństwa błędnej klasyfikacji. Nieczystość Giniego dana jest wzorem:

$$I_{G}(P)=1-\sum _{d\in D} \left( \frac{|P^d|}{|P|} \right)^2$$

## Algorytm C4.5
Algorytm C4.5 został opracowany przez Rossa Quinlana. Algorytm zaczyna od zbudowania drzewa decyzyjnego na podstawie danych, a następnie odcina mało ważne gałęzie zapobiegając przeuczeniu. Algorytm następnie wybiera atrybut dla której największa jest znormalizowana informacja wzajemna $I(P ;R)$. Podział kończy się w momencie, gdy każda z gałęzi posiada obiekty z jednej klasy.

Algorytm działa następująco:
1. Jeśli w liściu znajdują się elementy jednej klasy algorytm kończy działanie oznaczając ten liść daną klasą.
2. Dla każdego atrybutu w danej klasie określamy dane oraz wyznaczamy przysrost informacji na atrybucie.
3. Najlepszy atrybut zostaje przypisany do testu na danym podziale.
4. Dla każdej gałęzi poniżej powtarzamy proces.

Jedną z najpopularniejszych implementacji algorytmu C4.5 jest algorytm J48, który jest implementacją C4.5 w języku Java.

Jak każdy algorytm, C4.5 również ma swoje słabe strony:
- **Puste gałęzie**: Puste gałęzie powodują, że drzewo staje się szerokie i skomplikowane. Wiele węzłów może posiadać wartości zerowe, bądź bliskie zeru.
- **Niesistotne gałęzie**: Jeżeli nieistotne gałęzie będą brane pod uwagę przy podziale budującym drzewo, to mogą zmniejszyć skuteczność tego drzewa lub spowodować przeuczenie się.
- **Przeuczenie**: Przeuczenie może wydarzyć się gdy algorytm otrzyma dane z nietypowymi cechami. Wywołują one dużą fragmentację w procesie podziału. Zazwyczaj gałęzie rosną na tyle, aby dobrze sklasyfikować przykłady treningowe. Jeśli dane posiadają szum, może dojść do przeuczenia. Aby temu zapobiec stosuje się jedną z dwóch strategii: zaprzestanie rozwoju zanim dojdzie do maksimum oszacowań, bądź oczyszczając drzewo po przeuczeniu.

## Uczenie drzew decyzyjnych
Podstawowy algorytm uczenia drzew decyzyjnych jest oparty na algorytmie **dziel i zwyciężaj** (ang. *divide and conquer*), algorytm taki powinien spełniać własności:
- atrybuty są jednoznaczne,
- drzewo jest konstruowane w sposób rekurencyjny od góry,
- na początku wszystkie dane treningowe są u podstaw,
- przykłady są partycjonowane rekurencyjnie na podstawie wybranych atrybutów,
- atrybuty są wybierane na podstawie funkcji (np. $I(P ;R)$).

Drzewo powinno przestać się dzielić na kolejne rozgałęzienia w przypadku: gdy wszystkie przykłady dla danego węzła należą do tej samej klasy, jeśli nie ma pozostałych atrybutów do dalszego partycjonowania to większość klasy to liść, brakuje dalszych przykładów.

## Pień decyzyjny
Pień decyzyjny (ang. *decision stump*) wykorzystuje drzewa decyzyjne na jednym poziomie. Jest to prosty test jednej cechy. 

Problemem tej metody jest to, że może nie być w stanie prawidłowo dopasować danych jeśli źle wybierzemy podstawę. Istnieje możliwość połączenia wielu pni decyzyjnych w kombinację liniową co daje nam **wzmocniony pień decyzyjny**. Taka kombinacja jest podobna do drzewa decyzyjnego, jednak często działa lepiej.

Wzmocniony pień decyzyjny może zostać uogólniony do regionów nie pokrytych przez zestaw testowy. Głosowanie w drzewie decyzyjnym jest zależne od danych na małym obszarze, a w pniu decyzyjnym głosowanie jest między słabmi klasyfikatorami.

## Lasy decyzyjne
Lasy losowe (ang. *Random Forest*) są zaliczane do procedur agregrujących, ich działanie polega na klasyfikacji za pomocą grupy drzew decyzyjnych. Decyzja ostateczna jest wynikiem głosowania większościowego. 

Każde drzewa z lasu jest tworzone z wykorzystaniem próby bootstrapowej, która powstaje przez losowanie ze zwracaniem $n$ elementów z zestawu uczącego.

Klasyfikator drzew losowych jest kolekcją drzew, gdzie każde drzewo jest zależne od losowego wektora z niezależną próbką. Lasy losowe radzą sobie gdy brakuje danych, wśród metod klasyfikacyjnych mają bardzo wysoką trafność. Metoda ta potrafi sobie poradzić bardzo dobrze z dużą ilością danych. Aby poprawić osiągane wyniki można sprawdzić jak duże znaczenie mają konkretne cechy i wykluczyć te, które okażą się niepotrzebne.
