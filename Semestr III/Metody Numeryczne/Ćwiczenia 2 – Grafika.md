## Rysowanie wykresu funkcji
Jedną z kluczowych funkcji w Mathematice jest możliwość wyświetlenia wykresu wybranej funkcji, do czego służy polecenie `Plot`.

Minimalna liczba argumentów tej funkcji to dwa: `Plot[f(x), A]`, gdzie `f(x)` jest funkcją do wyświetlenia, a zbiór `A = {x, a, b}` zawiera zmienną oraz początek (`a`) i koniec (`b`) zakresu.
`Plot[Sin[x], {x, 0, 2*Pi}]`
![[Pasted image 20260902215056.png|244]]
## Formatowanie wykresu
W Mathematice możemy swobodnie edytować wykres, dodając kolejne argumenty do funkcji `Plot`.

**Zmiana stylu linii (kolor, przerywana linia, grubość):**
`Plot[Sin[x], {x, 0, 2*Pi}, PlotStyle -> {Red, Dashing[{0.02, 0.05}], Thickness[0.015]}]`
![[Pasted image 20260902215115.png|233]]

**Ograniczenie zakresu osi (PlotRange):**
`Plot[Sin[x], {x, 0, 2*Pi}, PlotStyle -> {Red, Thickness[0.02]}, PlotRange -> {0, 5/6}]`
![[Pasted image 20260902215126.png|265]]

**Wypełnienie obszaru pod wykresem (Filling):**
`Plot[Sin[x], {x, 0, 2*Pi}, Filling -> Axis]`
![[Pasted image 20260902215137.png|272]]

## Wiele funkcji na jednym wykresie
Mathematica pozwala na umieszczanie więcej niż jednej funkcji na jednym wykresie. Można to zrobić na dwa sposoby:

**Sposób 1: Zastąpienie funkcji zbiorem funkcji**
W miejsce pojedynczej funkcji wstawiamy listę funkcji w nawiasach klamrowych.
`Plot[{Sin[x], Cos[x]}, {x, 0, 2*Pi}, PlotStyle -> {{Red, Thickness[0.01]}, {Green, Dashing[0.03, 0.04]}}]`
![[Pasted image 20260902215154.png|271]]

**Sposób 2: Korzystanie z funkcji Show**
Funkcje zapisuje się najpierw do zmiennych, a następnie wyświetla je na jednym wspólnym wykresie za pomocą funkcji `Show`.
* `p1 = Plot[Exp[-x^2], {x, -2, 2}, PlotStyle -> Red];`
* `p2 = DiscretePlot[Exp[-x^2], {x, -2, 2, 0.25}, PlotStyle -> {PointSize[0.02]}];`
* `Show[p1, p2]`

![[Pasted image 20260902215220.png|320]]
## Przechowywanie danych w tabeli
Za pomocą polecenia `Table` możemy tworzyć pary liczb i przechowywać je w formie tabeli (zbioru punktów). 
Funkcja ta operuje na dwóch argumentach: `Table[F, A]`, gdzie `F = {x, f(x)}`, a `A = {x, a, b, n}` (gdzie `n` to krok).

**Przykład:**
`Table[{x, x^2}, {x, -2, 2, 1}]`
## Wykresy trójwymiarowe
Mathematica pozwala na pracę przy wykresach dwóch zmiennych, do czego wykorzystuje się polecenie `Plot3D`, działające analogicznie do zwykłego `Plot`.

**Przykład podstawowy 3D:**
`Plot3D[Exp[-x^2 - y^2], {x, -2, 2}, {y, -2.2, 2}]`
![[Pasted image 20260902215235.png|282]]

**Wykres 3D bez siatki (Mesh):**
`Plot3D[Exp[-x^2 - y^2], {x, -2, 2}, {y, -2.2, 2}, Mesh -> False]`
![[Pasted image 20260902215246.png|278]]

**Wykres 3D z funkcją koloru (ColorFunction):**
`Plot3D[Exp[-x^2 - y^2], {x, -2, 2}, {y, -2.2, 2}, ColorFunction -> Hue]`
![[Pasted image 20260902215259.png|285]]
## Wykresy parametryczne
Funkcje parametryczne nie są funkcjami w ścisłym kontekście matematycznym (gdzie dla każdego $x$ istnieje dokładnie jeden $y$). Operują na parametrach, gdzie współrzędne są wyliczane niezależnie: $x = f(t)$, $y = g(t)$ (np. okrąg). W programie używa się do tego funkcji `ParametricPlot`.

**Wykres parametryczny 2D:**
`ParametricPlot[{Sin[t], Cos[t]}, {t, 0, 2*Pi}]`
![[Pasted image 20260902215309.png|228]]

**Wykres parametryczny 3D:**
Trójwymiarowe funkcje parametryczne tworzy się analogicznie za pomocą `ParametricPlot3D`.
`ParametricPlot3D[{Sin[t], Cos[t], t/4}, {t, 0, 20}, PlotStyle -> Green]`
![[Pasted image 20260902215317.png|164]]
## Animacje
W Mathematice możemy również animować wykresy funkcji, korzystając z polecenia `Animate[p, Z]`, gdzie `p` jest funkcją rysującą (np. `Plot`), a `Z = {t, a, b}` to zakres, w jakim zmienia się parametr czasu $t \in (a, b)$.

**Przykład animacji:**
`Animate[Plot[Exp[Sin[x*t]], {x, -Pi, Pi}, PlotRange -> {0, 3}], {t, 0, 10}]`
![[Pasted image 20260902215325.png|394]]