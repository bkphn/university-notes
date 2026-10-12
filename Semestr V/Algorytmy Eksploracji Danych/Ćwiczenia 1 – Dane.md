## Rodzaje danych
**Dane strukturalne** to dane uporządkowanie w określony sposób, czyli uporządkowane według zdefiniowanego modelu danych.

**Dane nieustrukturyzowane** to dane nie zorganizowane zgodnie z wybranym modelem / strukturą danych.

## Big Data
**Big Data** to bardzo duży zbiór różnorodnych danych, przysrastających w szybkim tempie, gdzie tradycyjne metody przetwarzania danych są już niewystaraczające.

Big Data często opisuje się za pomocą pięciu charakterystycznych właściwości:
1. **Volume**: ogromne ilości danych;
2. **Velocity**: duże tempo generowania i przetwarzania danych;
3. **Variety**: dane występują w różnych formatach;
4. **Veracity**: dane mogą zawierać błędy, szum i nieścisłości;
5. **Value**: możliwość uzyskania użytecznych informacji z danych.

## Cykl życia danych
Cykl życia danych może składać się z różnej ilości etapów w zależności od przyjętej metodologii.

Można wyróżnić cztery podstawowe etapy cyklu życoa danych:
1. **Generowanie danych**: Etap ten odnosi się do różnorodnych i złożonych zestawów danych z różnych rozproszonych źródeł.
2. **Zbieranie danych**: Polega na zbieraniu danych z różnych źródeł oraz ich przygotowaniu do dalszej analizy. Dane mogą być poddane filtrowaniu, wykluczaniu danych nieaktualnych lub niepełnych usuwanie duplikatów, ustalane są zależności pomiędzy danymi i uzyskiwane są nowe informacje.
3. **Analizowanie danych**: Jest to zasadniczy etap przetwarzania danych, polega na przetwarzaniu i wyszukiwania wzorców wewnątrz danych.
4. **Wizualizacja i wnioskowanie**: Ostatni etap polegający na zwizualizowaniu wniosków uzyskanych z przeanalizowanych i przetworzonych danych. Wyniki powinny zostać tak przedstawione, aby użytkownicy nie będący analitykami danych byli w stanie je odczytać.

## Odkrywanie wiedzy z baz danych
**Knowledge Discovery in Databases** KDD to proces prowadzący do pozyskania użytecznych informacji i wzorców z dużych zbiorów danych.

KDD składa się z etapów:
- selekcja danych,
- przygtowanie danych,
- eksploracja danych,
- wydobywanie danych (ang. *data mining*),
- ocena, interpretacja, analiza, wizualizacja.

## Redukcja wymiarów
**Redukcja wymiarów** to proces przekształcający pierwotny zbiór danych w zbiór o mniejszej liczbie wymiarów, zachowując przy tym informacje, które te dane ze sobą niosą.

Redukcja wymiarów pozwala na:
- wizualizację i zrozumienie danych,
- kompresję danych i przyśpieszenie obliczeń,
- wykrywanie anomalii,
- uniknięcie nadmiernego dopasowania do danych.

Najczęściej stosowane metody redukcji wymiarów możemy podzielić w oparoicu o szukanie czynników pomiędzy wymiarami (np. PCA, ICA, Factor Analysis) bądź w oparciu o rzutowanie jednego wymiaru na inny (np. $t$-SNE, ISOMAP, UMAP, Autoenkodery). 

## Analiza głównych składowych
**Analiza głównych składowych** (ang. *Principal Component Analysis*) PCA opiera się o wyznaczenie osi zachowującej największą wartość wairancji zbioru uczącego. Składowae wyznaczamy jako kombinację liniową badanych zmiennych. Idea tworzenia kolejnych składowych poelga na tym, że:
- kolejne składowe nie są skorelowane ze sobą (nie są ze sobą związane);
- mają na celu zmaksymalizować zmiennność, która nie została wyjaśniona przez poprzednią składową.

W celu wyszukiwania głównych składowych korzysta się z techniki faktoryzacji macierzy, zwanej rozkładem według wartości osobliwych (ang. *singular value decomposition*) SVD. Technika ta rozkłada macierz danych na iloczyn skalarny.

## Rozkład macierzy SVD
Rozkład macierzy SVD polega na przedstawieniu macierzy $\mathbf{A}$ w postaci $\mathbf{U}\mathbf{\Sigma}\mathbf{V}^T$ gdzie $\mathbf{U}, \mathbf{V}$ to macierze ortogonalne, czyli macierze kwadratowe, mające m.in. właściwość, że macierz odwrotna macierzy $\mathbf{X}$ jest macierzą transponowaną do tej macierzy $\mathbf{X}^{-1}=\mathbf{X}^T$, a $\mathbf{\Sigma}=\mathrm{diag}(\sigma_{1},\sigma_{2},\dots,\sigma_{n})$ jest macierzą diagonalną zawierającą wartości osobliwe (ang. *singular values*) macierzy $\mathbf{A}$.

Wartości osobliwe $\sigma_{i}$ macierzy $\mathbf{A}$ dane są wzorem:

$$σ_{i}=\sqrt{ \lambda_{i} }$$

gdzie $\lambda_{i}$ to wartość własna macierzy $\mathbf{A}^T\mathbf{A}$


Implementacja SVD w języku Python:
``` python
import numpy as np
from scipy.linalg import svd

A = np.array([[3,3,2,1],[2,3,-2,5],[2,3,8,0],[0,0,2,3]])

U,Σ,VT = svd(A)
```
