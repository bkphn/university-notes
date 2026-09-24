## Grupowanie danych
Klasteryzacja danych, nazywana również grupowaniem bądź analizą skupień, wywodzi się z eksploracji danych, w której wykorzystujemy tzw. klasyfikację bezwzorcową. Dokonujemy tutaj podziału danych wejściowych na względnie jednorodne klasy. Dane są grupowe na podstawie podobieństwa między elementami, które najczęściej określamy przy pomocy metryki podobieństwa.

**Klastrem** nazywamy grupę podobnych do siebie obiektów.

Grupując dane możemy dokonać prostej klasyfikacji, wyodrębnić struktury i powiązania, utworzyć tzw. klasy abstrakcji, w których elementy będą opisane jakąś wspólną grupą cech.
## Metody hierarchiczne
Metody hierarchiczne to algorytmy, które klastrują dane korzystając z hierarchii klasyfikacji. Na początku algorytm dzieli zbiór obiektów na pojedyncze klasy abstrakcji i stopniowo łączy je w pary do momentu uzyskania klastrów.

Możemy wyróżnić dwa rodzaje metod hierarchicznych:
- **Procedury aglomeracyjne**: Procedury aglomeracyjne tworzą macierz podobieństw klasyfikowanych obiektów, a następnie w kolejnych iteracjach, łączą w klastry obiekty najbardziej do siebie podobne.
- **Procedury deglomeracyjne**: Procedury deglomeracyjne zaczynają od klastra ogólnego obejmującego wszystkie obiekty, a następnie w kolejnych krokach dzielą je na mniejsze i bardziej jednorodne skupienia aż do momentu, gdy każdy obiekt stanowi oddzielny klaster.
## Metody $k$-średnich
Metody $k$-średnich to algorytmy niehierarchiczne, w których dane grupujemy na określoną liczbę $k$ różnych klas.

W kolejnych iteracjach podział jest poprawiany względem zadanej funkcji poprzez przenoszenie elementów między klasami, aby uzyskać minimalną wariancję wewnątrz każdej klasy. Przestawiając elementy między klasami abstrakcji układamy je według podobieństwa w poszczególnych klasach.

Przykładami metod $k$-średnich mogą być:
- algorytm centroidów,
- algorytym rozmytej analizy skupień.
## Algorytm centroidów
Algorytm centroidów został opracowany w 1967 roku przez J. MacQueena. Algorytm jest prostym podziałem wejściowego zbioru danych na ustaloną liczbę klas według wyodrębnionych środków nazywanych **centroidami**.

Centroid jest reprezentantem danego skupienia, przydatnym w interpretacji wyników. Określamy go jako typowego reprezentanta każdej klasy abstrakcji. Przy zbyt zróżnicowanych elementach tworzenie klas jest ciężkie, praktycznie niemożliwym staje się wybranie reprezentatywnego centroidu.

Każdy element $\mathbf{x}_{p}$ przypisujemy do takiej klasy, aby miara podobieństwa $\mathbf{x}_{i}$ do centroidu tej klasy $\mathbf{c}_{p}$ wyrażana wzorem $\parallel \mathbf{x}_{p}-\mathbf{c}_{p}\parallel$ była jak najmniejsza. Najczęściej używamy odległości euklidesowej, jej kwadratu, bądź odległości Czebyszewa.

Po przypisaniu elementów do centroidu wyznaczamy nowy centroid. Najczęściej centroidy wyznacza się jako średnią arytmetyczną pozostałych elementów należących do danej klasy.

Powtarzamy algorytm aż do osiągnięcia kryterium zbieżności, z reguły jako takową przyjmuje się fakt, iż elementy nie zmieniają już przynależności do klasy.
## Algorytm rozmytej analizy skupień
Algorytm rozmytej analizy skupień opiera się na metodzie $c$-średnich. Metody rozmytej analizy skupień mogą przydzielać element do więcej niż jednej kategorii, z tego powodu są stosowane w zadaniu kategoryzacji (przydziału jednostek do dowolnej liczby grup). 

Metody te różnią się od metod klasycznej analizy skupień, w wyniku których uzyskana klasyfikacja ma charakter grupowania rozłącznego, którego wynikiem jest to, że każdy element należy tylko do jednej klasy.

Algorytm rozmytej analizy skupień zaczyna się od rozlosowania początkowych centrów $\mathbf{c}_p$. Przy czym jeżeli dane uczące reprezentują funkcję ciągłą to początkowe centra umieszczamy w punktach minimalnych i maksymalnych funkcji. 

Następnie dla $p$-tego wzorca $\mathbf{x}_p$ ze zbioru uczącego wybieramy centrum $\mathbf{c}_p$ i je aktualizujemy:
$$c_p\leftarrow c_p+\eta(x_p−c_p )$$
gdzie współczynnik $\eta$ jest współczynnikiem uczenia, który maleje w kolejnych iteracjach:
$$\eta =\frac{\eta_0}{1+\frac{t}{T}}$$gdzie $t$ to obecna iteracja, a $T$ to liczba wszystkich iteracji.

Cały algorytm powtarzamy kilkukrotnie.
## Algorytm KNN
Algorytm KNN z angielskiego *K Nearest Neighbours*. Algorytm KNN jest prostym klasyfikatorem, który polega na znalezieniu K elementów w danych zbiorze danych, które są najbardziej zbliżone do testowanego elementu. Elementy o podobnych cechach nazywamy **sąsiadami**.

Zakładamy, że sąsiedzi sami wybiorą, do której grupy będą należeć kolejne rekordy. Wynikiem klasyfikacji jest grupa, która zawiera największą liczbę sąsiadów. Podobieństwo rekordów określamy mierząc odległości między elementami, które mają cechy opisane jako wektory. Do tego pomiaru zastosujemy metrykę euklidesową, Manhattan lub inną wybraną.

Załóżmy, że $\mathbf{a},\mathbf{b}$ są rekordami o charakterystyce $n$, pomiędzy którymi mierzymy odległość. Elementy zbioru danych są interpretowane jako wektory cech. Wtedy funkcję odległości można zdefiniować na podstawie wybranej metryki, przykładowo:
- **Odległość Euklidesa**
$$d_{E}(\mathbf{a},\mathbf{b})=\sqrt{\sum_{i=1}^n(a_{i}-b_{i})^2}$$
- **Odległość Manhattan**
$$d_{M}(\mathbf{a},\mathbf{b})=\sum_{i=1}^n |a_{i}-b_{i}|$$
Funkcje te spełniają warunek identyczności elementów nieodróżnialnych, symetrii i nierówności trójkątów, a zatem reprezentują metryki. Algorytm KNN nie zbiera informacji o danym problemie, jest to tzw. leniwa klasteryzacja.

W algorytmie, po zadeklarowaniu liczby sąsiadów $K$ i zdefiniowaniu funkcji odległości $d$ możemy przejść do klastrowania obiektów. Dla każdego obiektu testowego $\mathbf{y}$ wyznaczamy odległość między nim a każdym obiektem $\mathbf{x}_{i}$ w zbiorze treningowym. W tym zbiorze wykonywane jest głosowanie. Wartości, które występują najczęściej zostają przypisane obiektowi $\mathbf{y}$.

W przypadku gdy nie jesteśmy w stanie jednoznacznie na podstawie sąsiadów sklastrować obiektu $\mathbf{y}$ to porównujemy odległości $d(\mathbf{x}_i,\mathbf{y})$ i wybieramy ten obiekt, który leży najbliżej.
## Wymiarowość danych
**Wymiarowością danych** nazywamy liczbę wymiarów, cech lub zmiennych wejściowych skojarzonych z opisem obiektu w zbiorze danych. Poszczególne cechy możemy traktować jako kolejne elementy wektora. 

Zmniejszenie wymiarowości oznacza zmniejszenie liczby cechy w zbiorze danych. Algorytmy redukcji wymiarowości rzutują dane wielowymiarowe do przestrzeni o niewielkich wymiarach zachowując jednocześnie jak najwięcej istotnych informacji.

Możemy wyróżnić dwa podejścia do redukcji wymiarowości:
- **Redukcja liniowa**: Projekcja liniowa polega na liniowym rzutowaniu danych z przestrzeni wielowymiarowej do przestrzeni niskowymiarowej na podstawie analizy składowych głównych, dekompozycji wartości osobliwych czy rzutowaniu losowemu.
- **Redukcja nieliniowa**: Redukcja nieliniowa polega na wieloktronym uczeniu się algorytmu tego jak skutecznie zrzutować wielowymiarowy obiekt do przestrzeni niskowymiarowej.
## Algorytm analizy głównych komponentów
Algorytm analizy głównych komponentów nazywany również **algorytmem PCA** jest jednym z algorytmów liniowej redukcji wymiarowości danych.

Algorytm PCA znajduje niskowymiarową reprezentację danych, zachowując jak najwięcej zmienności. Główną koncepcją PCA jest rozważenie korelacji między cechami. Jeśli korelacja jest bardzo wysoka wśród podzbioru cech PCA spróbuje połączyć wysoce skorelowane cechy i przedstawić te dane z mniejszą liczbą liniowo nieskorelowanych cech (liniowow niezależnych wektorów).

Algorytm wykonuje redukcję kolreacji, znajdując kierunki maksymalnej wairancji w oryginalnych danych wielowymiarowych i rzutując je na mniejszą przestrzeń wymiarową. Te nowo uzystkanie składniki nazywany **składnikami głównymi**.

Dzięki tym komponentom możliwe jest odwtorzenie oryginalnych cech. Algorytm PC aktywnie stara się minimalizować błąd rekonstrukcji podczas poszukiwania optymalnych komponentów.

PCA to nienadzorowany algorytm uczenia maszynowego analizujący główne komponenety danych decyzyjnych. Wymiarowość zbioru danych znacząco wpływa na wyniki, dlatego często ją redukujemy do najważniejszych wymiarów. Konieczne jest wykonanie skalowania cech przed uruchomieniem PCA, jeśli istnieje znacząca różnica w skali między cechami zbioru danych.
## Typy klasyfikacji danych
Przy klasyfikafikacji danych często zmagamy się z problemem oceny skuteczności danego algorytmu. Możemy wtedy posłużyć się różnymi typami klasyfikacji danych, które reprezentują oceny systemu decyzyjnego.

Standardowo wyróżniamy cztery podstawowe oceny klasyfikacji:
- **Prawdziwe dodatni**: Prawdziwie dodatni (ang. *true positive*) oznacza, że model poprawnie zaakceptował pewną prawdziwą wartość, ocenę tę oznaczamy jako $\text{TP}$.
- **Prawdziwie ujemny**: Prawdziwie ujemny (ang. *true negative*) oznacza, że model poprawnie odrzucił pewną fałszywą wartość, ocenę tę oznaczamy jako $\text{TN}$.
- **Fałszywie ujemny**: Fałszywie ujemny (ang. *false negative*) oznacza, że model błędnie zaakceptował pewną fałszywą wartość, mamy tutaj do czynienia z przeoczeniem. Błąd ten nazywamy błędem I rodzaju i oznaczamy jako $\text{FP}$.
- **Fałszywie dodatni**: Fałszywie dodatni (ang. *false positive*) oznacza, że model błędne odrzucił prawdziwą wartość, mamy tutaj do czynienia z "fałszywym alarmem".  Błąd ten nazywany błędem II rodzaju i oznaczamy jako $\text{FN}$.
## Miary oceny klasyfikatora
Często oceny klasyfikacji nie mówią nam wystarczająco dużo o konkretnym działaniu klasyfikatora, możemy wtedy posłużyć się wybraną przez nas miarą oceny klasyfikatora, opierającą się na metrykach:
- **Dokładność**: Dokładność (ang. *accuracy*) mówi nam o tym jak często dobrej odpowiedzi udzielił klasyfiaktor. Dokładność oznaczamy symbolem $\text{ACC}$ i definiujemy wzorem: $$\text{ACC}=\frac{\text{TP}+\text{TN}}{\text{TP}+\text{TN}+\text{FP}+\text{FN}}$$
- **Wrażliwość**: Wrażliwość (ang. *sensitivity-recall*) mówi nam o tym jak skutecznie program poprawnie sklasyfikował faktycznie dodatnie wartości. Wrażliwość oznaczamy symbolem $\text{TPR}$ i definiujemy wzorem: $$\text{TPR}=\frac{\text{TP}}{\text{TP}+\text{FN}}$$
- **Precyzja**: Precyzja (ang. *precision*) mówi nam o tym jak wiarygodny jest klasyfikator, gdy klasyfikuje wartości jako dodatnie. Precyzję oznaczamy symbolem $\text{PPV}$ i definiujemy wzorem: $$\text{PPV}=\frac{\text{TP}}{\text{TP}+\text{FP}}$$
- **F1**: Miara F1 (ang. *F1 score*) jest średnią harmoniczną precyzji i wrażliwości, stosuje się ją wtedy gdy zależy nam na zbalansowaniu obu miar. Miarę F1 oznaczamy symbolem $F_{1}$ i definiujemy wzorem: $$F_{1}=2\cdot \frac{\text{PPV}\cdot \text{TPR}}{\text{PPV}+\text{TPR}}$$
-  **Swoistość**: Swoistość (ang. *specificity*) mówi nam o tym jak skutecznie klasyfikator wykrywa przypadki ujemne. Swoistość oznaczamy symbolem $\text{TNR}$ i definiujemy wzorem: $$\text{TNR}=\frac{\text{TN}}{\text{TN}+\text{FP}}$$
## Macierz błędu
Macierz błędu, nazywana również macierzą (bądź tablicą) pomyłek, lub macierzą dezorientacji, jest rodzajem tabeli pokazującej skuteczność algorytmu klasyfikacyjnego. Każda kolumna przedstawia możliwe oceny klasyfikacji.

Wiersze i kolumny macierzy błędu odpowiadają kolejno za: stan rzeczywisty i stan przewidywany. Jako elementy tej macierzy umieszczamy liczbę kolejnych ocen klasyfikatora.
<table style="text-align: center; border-collapse: collapse;">
  <tr>
    <th colspan="2" rowspan="2" style="border: 1px solid #aaa;"></th>
    <th colspan="2" style="border: 1px solid #aaa; background-color: #f2f2f2;">Stan przewidywany</th>
  </tr>
  <tr>
    <th style="border: 1px solid #aaa; background-color: #f2f2f2;">Pozytywny</th>
    <th style="border: 1px solid #aaa; background-color: #f2f2f2;">Negatywny</th>
  </tr>
  <tr>
    <th style="border: 1px solid #aaa; background-color: #f2f2f2;" rowspan="2">Stan<br>rzeczywisty</th>
    <th style="border: 1px solid #aaa; background-color: #f2f2f2;">Pozytywny</th>
    <td style="border: 1px solid #aaa; background-color: #d4edda;">TP</td>
    <td style="border: 1px solid #aaa; background-color: #f8d7da;">FN</td>
  </tr>
  <tr>
    <th style="border: 1px solid #aaa; background-color: #f2f2f2;">Negatywny</th>
    <td style="border: 1px solid #aaa; background-color: #f8d7da;">FP</td>
    <td style="border: 1px solid #aaa; background-color: #d4edda;">TN</td>
  </tr>
</table>
tabela ta w praktyce sprowadza się do macierzy:
$$\mathbf{M}_{C}=\begin{bmatrix}\text{TP} & \text{FN}\\ \text{FP} & \text{TN} \end{bmatrix}$$

Macierz błędu możemy rozszerzyć o dodatkowe metryki informujące nas o miarach oceny klasyfikatora, przykładowym rozszerzeniem macierzy błędu może być:
<table style="text-align: center; border-collapse: collapse;">
  <tr>
    <th colspan="2" rowspan="2" style="border: 1px solid #aaa;"></th>
    <th colspan="2" style="border: 1px solid #aaa; background-color: #f2f2f2;">Stan przewidywany</th>
    <th colspan="2" style="border: 1px solid #aaa;"></th>
  </tr>
  <tr>
    <th style="border: 1px solid #aaa; background-color: #f2f2f2;">Pozytywny</th>
    <th style="border: 1px solid #aaa; background-color: #f2f2f2;">Negatywny</th>
    <td style="border: 1px solid #aaa; background-color: #f8d7da;">P</td>
    <td style="border: 1px solid #aaa;"></td>
  </tr>
  <tr>
    <th style="border: 1px solid #aaa; background-color: #f2f2f2;" rowspan="2">Stan<br>rzeczywisty</th>
    <th style="border: 1px solid #aaa; background-color: #f2f2f2;">Pozytywny</th>
    <td style="border: 1px solid #aaa; background-color: #d4edda;">TP</td>
    <td style="border: 1px solid #aaa; background-color: #f8d7da;">FN</td>
    <td style="border: 1px solid #aaa; background-color: #d4edda;">TPR</td>
    <td style="border: 1px solid #aaa; background-color: #f8d7da;">FNR</td>
  </tr>
  <tr>
    <th style="border: 1px solid #aaa; background-color: #f2f2f2;">Negatywny</th>
    <td style="border: 1px solid #aaa; background-color: #f8d7da;">FP</td>
    <td style="border: 1px solid #aaa; background-color: #d4edda;">TN</td>
    <td style="border: 1px solid #aaa; background-color: #f8d7da;">FPR</td>
    <td style="border: 1px solid #aaa; background-color: #d4edda;">TNR</td>
  </tr>
  <tr>
    <td style="border: 1px solid #aaa;"></td>
    <td style="border: 1px solid #aaa; background-color: #d4edda;" rowspan="2">ACC</td>
    <td style="border: 1px solid #aaa; background-color: #d4edda;">PPV</td>
    <td style="border: 1px solid #aaa; background-color: #f8d7da;">FOR</td>
    <td style="border: 1px solid #aaa; background-color: #d4edda;">LR+</td>
    <td style="border: 1px solid #aaa; background-color: #d4edda;" rowspan="2">DOR</td>
  </tr>
  <tr>
    <td style="border: 1px solid #aaa;"></td>
    <td style="border: 1px solid #aaa; background-color: #f8d7da;">FDR</td>
    <td style="border: 1px solid #aaa; background-color: #d4edda;">NPV</td>
    <td style="border: 1px solid #aaa; background-color: #d4edda;">LR-</td>
  </tr>
</table>

Oprócz standardowych miar $\text{ACC}$, $\text{TPR}$, $\text{PPV}$ czy $\text{TNR}$ w tej tabeli możemy zauważyć także nowe miary, między innymi:
- **Chorobowość** (ang. *prevalence*) $$\text{P}=\frac{\text{TP}+\text{FN}}{\text{TP}+\text{TN}+\text{FP}+\text{FN}}$$
- **Odsetek fałszywie negatywnych** (ang. *false negative rate*) $$\text{FNR}=\frac{\text{FN}}{\text{TP}+\text{FN}}$$
- **Odsetek fałszywie pozytywnych** (ang. *false positive rate*) $$\text{FPR}=\frac{\text{FP}}{\text{TN}+\text{FP}}$$
- **Odsetek fałszywych pominięć** (ang. *false omission rate*) $$\text{FOR}=\frac{\text{FN}}{\text{TN}+\text{FN}}$$
- **Odsetek fałszywych odkryć** (ang. *false discovery rate*) $$\text{FDR}=\frac{\text{FP}}{\text{TP}+\text{FP}}$$
- **Ujemna wartość predykcyjna** (ang. *negative predictive value*) $$\text{NPV}=\frac{\text{TN}}{\text{TN}+\text{FN}}$$

- **Wskaźnik wiarygodności wyniku dodatniego** (ang. *positive likelihood ratio*) $$\text{LR}+=\frac{\text{TPR}}{\text{FPR}}$$

- **Wskaźnik wiarygodności wyniku ujemnego** (ang. *negative likelihood ratio*) $$\text{LR}-=\frac{\text{FNR}}{\text{TNR}}$$
- **Diagnostyczny iloraz szans** (ang. *diagnostic odds ratio*) $$\text{DOR}=\frac{\text{LR}+}{\text{LR}-}$$
