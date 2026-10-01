## Modele przetwarzania danych
OLAP i OLTP

## Eksploracja danych
Dyscyplina **eksploracji danych** skupia się na analizie danych, zawyczaj w dużych ilościach. Jej zadaniem jest odkrywanie nietrywialnych zależności, związków, podobieństw, trendów i wzorców zachowań (ang. *pattern*).

Wzroce mają najczęściej postać reguł logicznych, klasyfikatorówm zbiorów skupień (tzw. klastrów) czy też różnego rodzaju wykresów. Same wzorce czasem mogą być przewidywalne, ale w większości przypadków są nie do wykrycia gołym okiem. Do analityka należy ich selekcja, często przy wykorzystaniu dodatkowych założeń.

## Odkrywanie wiedzy
Szerszą dyscypliną od eksploracji danych jest tzw. **odkrywanie wiedzy**. Wyróżniamy w nim następujące etapy:
- **czyszczenie danych** (ang. *data cleaning*): usuwanie i/lub weryfikacja danych niepełnych, niepoprawnych, nieistotnych;
- **integracja danych** (ang. *data integration*): łączenie danych pochodzących z różnych, często rozproszonych źródeł;
- **selekcja danych** (ang. *data selection*);
- **konsolidacja danych** (ang. *data consolidation*) oraz **transformacja danych** (ang. *data transformation*): przekształcenie danych po ich selekcji do postaci wymaganej przez konkretną metodą ekploracji danych;
- **ekploracja danych** (ang. *data mining*);
- **ocena uzyskanych wzorców** (ang. *pattern evaluation*);
- **wizualizacja uzyskanych wzorców** (ang. *knowledge visualization*).

## Metody opisu danych
Ze względu na charakterystykę metod eksploracji danych wyróżniamy następujący ich podział:
- **metody opisu danych** (ang. *description methods*): w szczególności np. odkrywanie reguł asocjacyjnych, opisujących zbiory produktów najczęściej nabywanych łącznie;
- **metody predykcji danych** (ang. *prediction methods*): przewidywanie trendów, ogólnych tendencji, zachowań klientów, itp.

Możemy jeszcze podzielić metody ze względu na cel eksploracji:
- **klasyfikacja**: obejmująca metody konstrukcji modeli lub funkcji (klasyfikatorów), opisujących zależności pomiędzy charakterystykami obiektów, a ich przyporządkowaniem do konkretnej grupy obiektów;
- **grupowanie** (analiza skupień, klasteryzacja): jej celem jest wyszukiwanie zbiorów obiektów (klastrów) podobnych do siebie;
- **odkrywanie asocjacji**: asocjacja to inaczej zależność/korelacja, jej odkrywanie skutkuje budową odpowiednich reguł asocjacyjnych;
- **odkrywanie wzorców sekwencji**: analiza sekwencji i przebiegów czasowych.

Dodatkowo wyróżnia się eksplorację tekstu, danych semistrukturalnych (`.xml`), sieci społecznościowych, danych multimedialnych, przestrzennych itd., jak również np. analizę sekwencji DNA. Przed właściwą eksploracją danych, są one poddawane procesom czyszczenia, integracji, selekcji i konsolidacji, w których wykorzystuje się techniki takie jak analiza składowych głównych, analiza czynnikowa, analiza korespondencji.
## Koncepcja składowych głównych
Załóżmy, że pewnie zjawisko (obiekt) opisane jest za pomocą zmiennych (cech) $x_1,x_{2},\dots,x_{p}$. Ponieważ $p$ w praktyce może być duże, a przez to może mieć niekorzystyny wpływ na statystyczną analizę zjawiska, chcielibyśmy zredukować liczbę zmiennych, tak jednak, aby zachować tak dużo informacji o badanym zjawisku jak to tylko możliwe. Jedną z technik statystycznych stosowanych do rozwiązania tego zagadnienia jest analiza składowych głównych.

Zasadnicze cele **analizy składowych głównych** (ang. *principal components analysis*) PCA można określić w następujący sposób:
- redukcja liczby zmiennych opisujących dane zjawisko poprzez wprowadzenie pewnych zmiennych sztucznych (nieobserwowalnych), wzajemnie ortogonalnych, będących pewnymi kombinacjami liniowymi zmiennych wyjściowych (obserwowalnych);
- wykrycie struktury i ogólnych prawidłowości w związkach pomiędzy zmiennymi;
- ocena (weryfikacja) wykrytych powiązań i prawidłowości;
- opis zjawiska za pomocą nowych współrzędnych (składowych głównych).

## Wyznaczenie składowych głównych
Weżmy pod uwagę zmienne $x_{1},x_{2},\dots,x_{p}$. Chcielibyśmy zredukowa¢ ich liczbę, zachowując jednocześnie tak dużo zmienności (informacji) jaką niosą ze sobą jak to tylko możliwe.

Tworzymy zatem nowe nieobserwowalne zmienne, które będą kombinacjami liniowymi zmiennych oryginalnych (obserwowalnych). Będą to tzw. **składowe główne**. Niech $z_{1}$ będzie pierwszą
składową główną. 

$$z_{1}=a_{1,1}x_{1}+a_{1,2}x_{2}+\dots+a_{1,p}x_{p}$$

Powyższe, mimo, że jest podobne do równania regresji wielorakiej, różni się od niego dość istotnie. Nie wprowadzamy w nim rozróżnienia zmiennych niezależnych i zmiennej zależnej, brak jest w nim wyrazu wolnego oraz składnika losowego (reszty). By zachować tak dużo zmienności wyjściowego układu zmiennych obserwowalnych $x_{1},\dots,x_{p}$ jak to tylko możliwe, wyznaczamy współczynniki $a_{1,j} , j = 1, ..., p$, równania tak, aby wariancja $S^2(z_{1})$ zmiennej $z_{1}$ była maksymalna.

Stosujemy jednak ograniczenie $\sum_{j=1}^p a_{i,j}^2 =1$, czyli normalizujemy wektor współczynników przyjunąc $|\mathbf{a}_{1}|=1$.

$$\mathbf{a}_{1}=\begin{bmatrix}
a_{1,1}\\
\vdots\\
a_{1,p}\\
\end{bmatrix}$$

Przyjmując oznaczenie $\mathbf{x}=\begin{bmatrix} x_{1} \\ \vdots \\ x_{p}\end{bmatrix}$ otrzymujemy następującą równość:

$$S^2(z_{1})=S^2(\mathbf{a}_{1}^T \mathbf{x})=\mathbf{a}_{1}^T \mathbf{S}\mathbf{a}_{1}=\sum_{i=1}^p\sum_{j=1}^p a_{1,i}a_{1,j}s_{i,j}$$

gdzie $\mathbf{S}$ jest macierzą kowariancji układu zmiennych wejściowych $x_{1},\dots,x_{p}$:

$$\mathbf{S}=\begin{bmatrix} D(x_{1}) & \mathrm{cov}(x_{1},x_{2}) & \cdots & \mathrm{cov}(x_{1},x_{p})  \\   \mathrm{cov}(x_{2},x_{1}) & D(x_{2}) & \cdots & \mathrm{cov}(x_{2},x_{p})  \\  \vdots & \vdots & \ddots & \vdots  \\  \mathrm{cov}(x_{p},x_{1}) & \mathrm{cov}(x_{p},x_{2}) & \cdots & D(x_{p})\end{bmatrix}$$

gdzie $D(x_{i})$ to wariancja zmiennej $x_{i}$, a $\mathrm{cov}(x_{i},x_{j})$ kowariancja zmiennych $x_{i},x_{j}$.

Dowolny element $s_{i,j}$ macierzy $\mathbf{S}$ możemy obliczyć ze wzoru:

$$s_{i,j}=\mathrm{cov}(x_{i},x_{j})=\frac{1}{n}\sum_{k=1}^n (x_{i,k}-\overline{x}_{i})(x_{j,k}-\overline{x}_{j})$$

gdzie $x_{i,k}$ to wartość zmiennej $x_{i}$ uzyskaną dla $k$-tego elementu $p$-wymiarowej $n$-elementowej próby losowej zmiennych $x_{1},\dots,x_{p}$, a $\overline{x}_{i}$ to średnia wartość cechy $x_{i}$ w tej próbie.

Poszukujemy zatem takiego wektora $a_1$, dla którego $S^2(z_{1})$ będzie maksymalne, przy czym $\mathbf{a}_{1}^T \mathbf{a1} = 1$ (jest to warunek normalizacyjny równoważny temu, że wektor $\mathbf{a}_{1}$ jest wektorem jednostkowym). W rozwiązaniu powyższego zagadnienia wykorzystamy rachunek różniczkowy, uwzględniając warunek normalizacyjny w postaci **mnożnika Lagrange'a** $l_{1}$. Obliczając pochodną względem wektora $\mathbf{a}_{1}$, otrzymujemy:

$$\frac{\partial\left(S^2(z_{1})+l_{1}(1-\mathbf{a}_{1}^T\mathbf{a}_{1}) \right)}{\partial \mathbf{a}_{1}}=2(\mathbf{S}-l_{1}\mathbf{I})\mathbf{a}_{1}$$

gdzie przez $\mathbf{I}$ oznaczamy macierz jednostkową.

Poszukiwane współrzędne wektora $\mathbf{a}_{1}$ muszę zatem spełniać układ prównać liniowych postaci (warunek konieczny istnienia ekstremum) $(\mathbf{S}-l_{1}\mathbf{I})\mathbf{a}_{1}=\mathbf{0}$.

Ponieważ rozwiązanie tego układu musi być niezerowe, zatem $l_{1}$ musi być liczbą taką, by $\det{(\mathbf{S}-l_{1}\mathbf{I})}=0$. Wnioskujemy stąd, że $l_{1}$ musi być własnością własną macierzy kowariancji $\mathbf{S}$, natomiast $\mathbf{a}_{1}$ – odpowiadającym tej wartości wektorem własnym. Wykorzystując fakt, że $\mathbf{a}_{1}^T\mathbf{a}_{1}=1$ otrzymujemy:

$$\mathbf{a}_{1}^T (\mathbf{S}-l_{1}\mathbf{I})\mathbf{a}_{1}=0$$

z czego wynika

$$l_{1}=\mathbf{a}_{1}^T \mathbf{S}\mathbf{a}_{1}=S^2(z_{1})$$

Ponieważ wariancja $S^2(z_{1})$ zmiennej $z_{1}$ miała być maksymalna, zatem $l_{1}$ musi być największą wartością własną macierzy kowariancji $\mathbf{S}$, zaś $\mathbf{a}_{1}$ wektorem własnym odpowiadającym tej wartości.