## Test sferyczności Bartletta
Przeprowadzenie analizy składowych głównych powinno być poprzedzone weryfikacj poniższych warunków. Należy ocenić zasadność zastosowania tej metody. Wszystkie współczynniki korelacji pomiędzy wyjściowymi zmiennymi $x_{1},\dots,x_{p}$ powinny być istotnie różne od zera (zaleca się, by były one większe od $0.3$ co do wartości bezwzględnej). Do oceny zasadności zastosowania metody składowych głównych służy **test sferyczności Bartletta**.

W teście sferyczności weryfikacji podlega hipoteza zerowa postaci:

$$H_{0}:\mathbf{R}=\mathbf{I}$$

gdzie $\mathbf{R}$ jest symetryczną macierzą kwadratową wymiaru $p$ współczynników korelacji pomiędzy zmiennymi $x_{1},\dots,x_{p}$, natomiast $\mathbf{I}$ oznacza macierz jednostkową wymiaru $p$.

Statystyką testową testu Bartletta jest następująca funkcja próby
losowej cech $x_{1},\dots,x_{p}$:

$$\chi^2=-\left( n-1-\frac{2p+5}{6} \right)\cdot\ln|R|=-\left( n-1-\frac{2p+5}{6} \right)\sum_{i=1}^p \ln \lambda_{i}$$
gdzie $\lambda_{i}, i\in\{1,\dots,p\}$, są wartościami własnymi macierzy korelacji $\mathbf{R}$,
natomiast n oznacza liczebność próby, czyli liczbę przypadków, na
podstawie których wyznaczana jest postać macierzy R. Przy
zaªożeniu prawdziwości hipotezy H0 powyższa statystyka testowa
ma rozkªad chi kwadrat o p(p−1)
2 stopniach swobody. Zbiór
krytyczny testu sferyczności ma postać K = [χ2
p(p−1)/2,1−α, ∞),
gdzie χ2
p(p−1)/2,1−α jest kwantylem rzędu 1 − α rozkªadu chi
kwadrat o p(p−1)
2 stopniach swobody, a α oznacza poziom
istotności testu.

Zwerykować należy adekwatność macierzy wspóªczynników
korelacji pomiędzy zmiennymi X1, ..., Xp.
Do tego celu sªuży wspóªczynnik Kaisera-Mayera-Olkina
,
gdzie ri,j jest wartością wspóªczynnika korelacji liniowej Pearsona
pomiędzy zmiennymi Xi oraz Xj obliczoną na podstawie realizacji
n-elementowej próby losowej, natomiast̂ ri,j oznacza wspóªczynnik
korelacji cząstkowej pomiędzy zmiennymi Xi oraz Xj.

Wspóªczynnik ten jest zdeniowany w następujący sposób:̂

gdzie Ri,j oznacza dopeªnienie algebraiczne elementu ri,j macierzy
wspóªczynników korelacji R pomiędzy zmiennymi.
Wspóªczynnik korelacji cząstkoweĵ ri,j opisuje siªę i kierunek
zależności korelacyjnej pomiędzy zmiennymi Xi oraz Xj przy
wyeliminowaniu wpªywu na tę zależność pozostaªych
zmiennych wyjściowego ukªadu.
Porównując zatem wartoścî ri,j oraz zwykªego wspóªczynnika
korelacji liniowej Pearsona ri,j możemy stwierdzić, jak bardzo
zależność pomiędzy Xi a Xj jest wzmacniana bąd¹ osªabiana
poprzez obecność innych zmiennych.


## Paradoks Bertranda