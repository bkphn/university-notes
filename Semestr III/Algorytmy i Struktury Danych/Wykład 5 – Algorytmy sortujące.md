## Sortowanie
Sortowaniem nazywamy proces porządkowania pewnego zbioru $\langle a_{0},...,a_{n}\rangle$ danych względem pewnych cech charakterystycznych dla tego zbioru.
Sortując zbiór $A=\langle a_{0},...,a_{n}\rangle$ zgodnie z relacją $x\mathcal{R}y=x\le y$ otrzymamy w wyniku zbiór $A^{\prime}$ $=\langle a_{0}^{\prime},...,{a_{n}}^{\prime}\rangle$ będący permutacją zbioru A, taką że: $a_{0}^{\prime}\le\cdot\cdot\cdot\le a_{n}^{\prime}$

## Sortowanie przez wstawianie
Algorytm sortowania przez wstawianie (Insert Sort) jest jednym z podstawowych algorytmów sortowania. Porównuje on poszczególne znaki sortowanego ciągu, spośród nich wybieramy największy element i wstawiamy go na koniec badanego ciągu, następnie sortujemy pozostały ciąg. Ponieważ największy element znajduje się już na końcu ciągu procedura porównania odbywa się dla $n-1$ elementów pierwotnego ciągu. Ta procedura powtarzana jest aż do uzyskania jednoelementowego ciągu.
Do wyznaczenia złożoności czasowej tego algorytmu należy zauważyć, że na ciągu n elementowym wykonujemy $n-1$ równań. Po przestawieniu elementu największego na koniec opuszczamy go w następnej iteracji i ilość potrzebnych porównań zmniejsza się o jeden.
$(n-1)+(n-2)+\cdot\cdot\cdot+2+1=\frac{n-1}{2}n=\frac{1}{2}n^{2}-\frac{1}{2}n\approx n^{2}$
Złożoność obliczeniowa sortowania przez wstawianie wynosi: $\mathcal{O}(n^{2})$

## Sortowanie bąbelkowe
Sortowanie bąbelkowe (Bubble Sort) to jeden z ważniejszych algorytmów ze względu na jego sposób działania. Różnica polega na tym, że zamiana elementów dokonana zostaje w poszczególnej iteracji poprzez sąsiednie elementy.
Porównujemy ze sobą kolejne elementy w każdej rozpatrywanej parze. Znalezioną wartość ekstremalną przesuwamy w ustalonym kierunku. Następnie porównujemy elementy w kolejnej utworzonej parze szukając największego i przesuwając go na koniec. Takie porównania wykonujemy do końca ciągu, aż element największy znajdzie się na ostatnim miejscu.
Złożoność czasowa sortowania bąbelkowego wynosi: $\Theta(n^{2})$.

## Sortowanie szybkie
Metoda sortowania szybkiego (Quick Sort) polega na wyborze elementu środkowego, nazywanego pivotem, w badanym ciągu. Następnie układamy elementy mniejsze od środkowego z lewej strony i elementy większe lub równe z jego prawej strony. Najczęściej przyjmuje się indeks elementu środkowego jako wartość losową.
W kolejnych iteracjach zajmujemy się sortowaniem elementów należących do utworzonych ciągów. W ciągu elementów po lewej i prawej stronie wyznaczamy właściwe im elementy środkowe. Względem tych elementów dokonujemy takiego samego przestawienia jak w poprzednim kroku. Po lewej stronie elementów środkowych umieszczamy elementy od nich mniejsze, a po prawej większe.
Złożoność obliczeniowa sortowania szybkiego wynosi: $\Theta(n\cdot log_{2}n)$
W niekorzystnym przypadku złożoność obliczeniowa może wynieść: $\mathcal{O}(n^{2})$

## Sortowanie przez kopcowanie
W celu zmniejszenia złożoności obliczeniowej sortowania zauważmy, że niektóre porównania w trakcie realizacji algorytmu są zbędne. Drzewo binarne pełne pomoże nam je wyeliminować.
Drzewo binarne to drzewo, w którym każdy z węzłów ma dwa węzły potomne, poza ostatnim rzędem tzw. liści. Drzewo pełne oznacza, że nie może brakować węzła wewnątrz drzewa i jednocześnie wszystkie liście są dosunięte do lewej strony. Numeracja w drzewie rozpoczyna się od 1 do n i przechodzi od znajdującego się na samym szczycie węzła poprzez wszystkie kolejne poziomy.
W czasie sortowania układamy elementy, aby spełniały zależności:
$\begin{cases}a_{i}\ge a_{2i+1}\\ a_{i}\ge a_{2i+2}\end{cases}$
układające wartość większą w wierzchołku rodzica 2 wierzchołków. Zaczynając układać elementy w kopiec od $\lfloor\frac{n-2}{2}\rfloor$ wykonamy tylko niezbędne operacje. Elementy od $n-1$ do $\lfloor\frac{n-2}{2}\rfloor$ będą w ostatnich poziomach kopca. Elementy od $\lfloor\frac{n-2}{2}\rfloor-1$ do 0 będą ocenione według powyższej zależności.
Procedura ta będzie polegała na budowaniu kopca i jego sortowaniu w każdej iteracji.
Kopiec n elementowy dwudzielny ma szacowaną wysokość k (liczba poziomów kopca) $\log_{2}n \le \log_{2}2\le k$, możemy napisać, że $k\approx\lfloor log_{2}n\rfloor+1$
Złożoność obliczeniowa sortowania przez kopcowanie wynosi: $\Theta(n\cdot log_{2}n)$

## Sortowanie przez scalanie
Sortowanie przez scalanie (Merge sort) opiera się o metodę dziel i zwyciężaj. Algorytm możemy przedstawić w wersji rekurencyjnej lub efektywniejszej, iteracyjnej.
W pierwszej iteracji algorytmu iteracyjnego scalamy pojedyncze elementy ciągu w posortowane pary, w drugiej w posortowane czwórki, następnie w ósemki itd. Przy kolejnych konkatenacjach zawsze porównujemy ze sobą tylko pierwsze elementy podciągów, bo są one posortowane.
Złożoność obliczeniowa sortowania przez scalanie wynosi: $\Theta(n\cdot log_{2}n)$

## Sortowanie Shella
Sortowaniem Shella (Shell sort) nazywamy sortowanie za pomocą malejących przyrostów. Bazuje na algorytmie sortowania przez wstawianie. Polega na tym, że sortowany zbiór dzielimy na mniejsze podzbiory.
W poszczególnych podzbiorach znajdują się elementy, które były odległe od siebie o zadany przyrost h w oryginalnym zbiorze. Każdy z podzbiorów zostaje uporządkowany sortowaniem insert sort. Następnie zmniejszamy przyrost h, co implikuje powstanie nowych podzbiorów, które znowu sortujemy metodą insert sort do momentu, aż h osiągnie wartość równą 1. Wtedy sortuje cały zbiór sortowaniem insert sort. Sortowanie insert sort jest wtedy bardziej efektywne, ponieważ dany zbiór jest bardziej uporządkowany.
Odległość h możemy definiować sobie w wybrany przez siebie sposób, oryginalna definicja Shella zakładała, że dla i-tego podziału $h_{i}=\lfloor\frac{n}{2^{i}}\rfloor$, gdzie n jest ilością sortowanych liczb.
Sortowanie liczb oddalonych od siebie o przyrost h nazywamy h-sortowaniem.

## Zbiory trudnosortowalne
Zbiorami trudnosortowalnymi, zwanymi też posiewami danych, nazywamy zbiory, w których złożoność obliczeniowa znacząco rośnie; są to najbardziej niekorzystne przypadki do rozważenia.
Paradoksalnie najczęściej mamy do czynienia ze zbiorami trudnosortowalnymi, co wynika z tego, że zbiór z którym przyjdzie nam pracować często składa się z wielu posortowanych podzbiorów.
Przykładem zbioru trudnosortowalnego może być zbiór: $(1, 3, 5, ..., n, 2, 4, 6, ..., n + 1)$

## Drzewo binarne
Drzewem binarnym $T=(V,E)$ nazywamy szczególny przypadek grafu, w którym z każdego węzła wychodzi dokładnie jedna ścieżka; do jednego węzła mogą wchodzić maksymalnie dwie ścieżki (w przypadku dowolnych drzew n-arnych może wchodzić n ścieżek); każdy węzeł, który nie jest korzeniem posiada dokładnie jednego rodzica; węzeł może mieć n dzieci; dowolny węzeł wraz ze swoimi potomkami tworzy poddrzewo wyjściowego drzewa.

W przypadku drzew stosujemy następujące słownictwo:
* **Rodzic:** Węzeł, który jest w relacji z co najmniej jednym węzłem znajdującym się niżej od niego w strukturze.
* **Dziecko:** Węzeł, który posiada rodzica.
* **Rodzeństwo:** Dzieci jednego rodzica.
* **Korzeń:** Węzeł znajdujący się na górze drzewa i nieposiadający rodzica.
* **Węzeł wewnętrzny:** Węzeł, który posiada zarówno rodzica, jak i ma co najmniej jedno dziecko.
* **Liść:** Węzeł, który nie posiada dzieci.
* **Poziom węzła:** Liczba krawędzi prowadzącej od korzenia drzewa.
* **Wysokość drzewa:** Największy spośród poziomów węzła.
* **Stopień węzła:** Ilość dzieci danego rodzica.
* **Stopień drzewa:** Największy spośród stopni węzłów.

## Kopiec
Kopcem nazywamy specjalny rodzaj drzewa binarnego, w którym w korzeniu znajduje się element najmniejszy, a na ścieżkach od korzenia do liścia, elementy są posortowane nierosnąco.
Kopcem zupełnym nazywamy kopiec, którego wszystkie poziomy są całkowicie wypełnione, wyjątkiem może być ostatni węzeł, który jest spójnie wypełniony od lewej strony.
