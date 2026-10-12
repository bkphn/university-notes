## Test sferyczności Bartletta
Przeprowadzenie analizy składowych głównych powinno być poprzedzone weryfikacj poniższych warunków. Należy ocenić zasadność zastosowania tej metody. Wszystkie współczynniki korelacji pomiędzy wyjściowymi zmiennymi $x_{1},\dots,x_{p}$ powinny być istotnie różne od zera (zaleca się, by były one większe od $0.3$ co do wartości bezwzględnej). Do oceny zasadności zastosowania metody składowych głównych służy **test sferyczności Bartletta**.

W teście sferyczności weryfikacji podlega hipoteza zerowa postaci:

$$H_{0}:\mathbf{R}=\mathbf{I}$$

gdzie $\mathbf{R}$ jest symetryczną macierzą kwadratową wymiaru $p$ współczynników korelacji pomiędzy zmiennymi $x_{1},\dots,x_{p}$, natomiast $\mathbf{I}$ oznacza macierz jednostkową wymiaru $p$.

Statystyką testową testu Bartletta jest następująca funkcja próby
losowej cech $x_{1},\dots,x_{p}$:

$$\chi^2=-\left( n-1-\frac{2p+5}{6} \right)\cdot\ln|R|=-\left( n-1-\frac{2p+5}{6} \right)\sum_{i=1}^p \ln \lambda_{i}$$
gdzie $\lambda_{i}, i\in\{1,\dots,p\}$, są wartościami własnymi macierzy korelacji $\mathbf{R}$, natomiast $n$ oznacza liczebność próby, czyli liczbę przypadków, na podstawie których wyznaczana jest postać macierzy $\mathbf{R}$. Przy założeniu prawdziwości hipotezy $H_{0}$ powyższa statystyka testowa ma rozkład chi kwadrat o $\frac{p(p−1)}{2}$ stopniach swobody. Zbiór krytyczny testu sferyczności ma postać $K = [\chi^2_{ \frac{p(p−1)}{2},1−\alpha}, \infty)$,
gdzie $χ^2_{\frac{p(p-1)}{2},1-\alpha}$ jest kwantylem rzędu $1 -\alpha$ rozkładu chi kwadrat o $\frac{p(p−1)}{2}$ stopniach swobody, a $\alpha$ oznacza poziom istotności testu.

Zweryfikować należy adekwatność macierzy współczynników korelacji pomiędzy zmiennymi $x_{1},\dots,x_{p}$. Do tego celu służy współczynnik Kaisera-Meyera-Olkina $\mathrm{KMO}$, obliczany ze wzoru:

$$\mathrm{KMO}=\frac{\sum_{i\neq j} r^2_{i,j}}{\sum_{i\neq j} r^2_{i,j}+\sum_{i\neq j}\hat{r}^2_{i,j}}$$

gdzie $r_{i,j}$ jest wartością współczynnika korelacji liniowej Pearsona pomiędzy zmiennymi $x_{i}$ oraz $x_{j}$ obliczoną na podstawie realizacji $n$-elementowej próby losowej, natomiast $\hat{r}_{i,j}$ oznacza współczynnik
korelacji cząstkowej pomiędzy zmiennymi $x_{i}$ oraz $x_{i}$.

Współczynnik ten jest zdefiniowany w następujący sposób:

$$\hat{r}_{i,j}=- \frac{R_{i,j}}{\sqrt{ R_{i,i} R_{j,j} }}$$

gdzie $R_{i,j}$ oznacza dopełnienie algebraiczne elementu $r_{i,j}$ macierzy współczynników korelacji $\mathbf{R}$ pomiędzy zmiennymi. Współczynnik korelacji cząstkowej $\hat{r}_{i,j}$ opisuje siłę i kierunek zależności korelacyjnej pomiędzy zmiennymi $x_{i}$ oraz $x_{j}$ przy wyeliminowaniu wpływu na tę zależność pozostałych zmiennych wyjściowego układu. Porównując zatem wartości $\hat{r}_{i,j}$ oraz współczynnika
korelacji liniowej Pearsona $r_{i,j}$ możemy stwierdzić, jak bardzo zależność pomiędzy $x_i$ a $x_{j}$ jest wzmacniana bądź osłabiana poprzez obecność innych zmiennych.

Współczynnik $\mathrm{KMO}$ przyjmuje wartości z przedziału $[0, 1]$. Im większa jego wartość, tym bardziej zasadne jest zastosowanie metody analizy składowych głównych do układu cech $x_{1},\dots,x_{p}$ (tym większy będzie potencjalny zysk z zastosowania PCA mierzony redukcją wymiaru zadania). Współczynnik ten powinien być większy od $0.5$, a najlepiej, by przekraczał $0.7$.

## Paradoks Bertranda
Paradoks Bertranda został przedstawiony przez francuskiego matematyka Josepha Bertranda w 1889 roku w książce *Calcul des probabilités*.

Dany jest okrąg o promieniu $r=1$, wewnątrz tego okręgu wpisujemy trójkąt równoboczny, następnie losujemy cięciwę okręgu. Jakie jest prawdopodobieństwo, że długość wylosowanej cięciwy będzie większa od długości boku wpisanego trójkąta?

Długość boku trójkąta równobocznego wpisanego w okrąg o promieniu $r=1$ wynosi:

$$
a=\sqrt{3}r=\sqrt{ 3 }
$$

Szukamy więc prawdopodobieństwa zdarzenia:

$$
P(l>\sqrt3)
$$

gdzie $l$ oznacza długość losowej cięciwy.

Bertrand zaproponował trzy naturalne sposoby losowania i otrzymał trzy różne wyniki:
1. **Losujemy dwa punkty na okręgu**: Losujemy punkt $A$ na obwodzie okręgu, następnie niezależnie losujemy drugi punkt $B$ na obwodzie. Łączymy oba punkty odcinkiem. Dla tego podejścia otrzymujemy:
   
   $$ P(l>\sqrt{ 3 })=\frac{\frac{2\pi}{3}}{2\pi} =\frac{1}{3}$$

2. **Losujemy odległość cięciwy od środka**: Losujemy kierunek promienia okręgu. Na tym promieniu losujemy punkt $M$, jednostajnie względem odległości od środka. Przez punkt $M$ prowadzimy cięciwę prostopadłą do promienia. Dla tego podejścia otrzymujemy:
   
   $$ P(l>\sqrt{ 3 })=\frac{1}{2} $$

3. **Losujemy środek cięciwy**: Losujemy punkt $M$ jednostajnie z powierzchni koła. Konstruujemy cięciwę, której środkiem jest punkt $M$. Dla tego podejścia otrzymujemy:
   
   $$ P(l>\sqrt{ 3 })=\frac{\frac{\pi}{4}}{\pi}=\frac{1}{4}  $$

Paradoks polega na tym, że intuicyjne pojęcie „losowej cięciwy” nie wyznacza jednoznacznie rozkładu prawdopodobieństwa. Nie istnieje zatem jedna poprawna odpowiedź bez sprecyzowania mechanizmu losowania.