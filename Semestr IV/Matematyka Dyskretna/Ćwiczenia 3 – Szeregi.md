## Liczby trójkątne
Liczby trójkątne są specjalnym szeregiem danym wzorem:
$$T_{n}=\sum_{i=1}^n i$$

Pierwsze wyrazy ciągu $T_n$ prezentują się następująco:
$$1, 3, 6, 10, 15, 21, 28, 36, 45, 55, 66, 78, 91, 105,\dots$$

Określenie liczby trójkątne (ang. *triangular number*) pochodzi z faktu, iż z dowolnego wyrazu ciągu $T_n$ jesteśmy w stanie skontruować trójkąt równoboczny.

Ciąg ten w OEIS (*Online Encyclopedia of Integer Sequences*) jest opisany jako ciąg [ciąg A000217](https://oeis.org/A000217).

## Problem bazylejski
Problem bazylejski jest przykładem zagadnienia analizy matematycznej. Polega ona na obliczeniu  sumy szeregu danego wzorem:
$$\sum_{i=1}^\infty \frac{1}{i^2}$$
Problem ten udało rozwiązać się dopiero w XVII wieku, jego rozwiązaniem jest liczba:
$$\sum_{i=1}^\infty \frac{1}{i^2}=\frac{\pi^2}{6}\approx 1.6449$$
Możemy także zdefiniować ciąg $B_n=\sum_{i=1}^\infty \frac{1}{i^2}$, jego granicą jest wartość $\pi^2/6$, natomiast pierwsze wyrazy tego ciągu prezentują się następująco:
$$\frac{1}{1}, \frac{5}{4}, \frac{49}{36}, \frac{205}{144}, \frac{5296}{3600}, \frac{5369}{3600}, \frac{266681}{176400},\dots$$
## Indukcja matematyczna
Niech $n_0\in\mathbb{N}$. Jeżeli $\phi$ jest własnością określoną w $\mathbb{N}$ taką, że:
- zachodzi warunek $\phi(n_0)$
- zachodzi następny warunek, jeżeli liczba naturalna $n$ spełnia $\phi(n)$, to $n+1$ też spełnia własność $\phi(n+1)$. Zachodzi $\phi(n)\implies\phi(n+1)$
to dla każdej liczby naturalnej $n≥n_0$ zachodzi własność $\phi$.

Rozumowanie indukcyjne przeprowadza się w czterech krokach:
1. **Baza indukcyjna**: Pokazujemy, że warunek $\phi$ zachodzi dla pewnej stałej liczby $n_0$
2. **Założenie indukcyjne**:	Zakładamy, że warunek $\phi$ zachodzi dla pewnej liczby $n$. Założenie indukcyjne oznaczamy jako $Z_i$.
3. **Teza indukcyjna**: Fomułujemy warunek $\phi$ dla liczby naturalnej $n+1$. Tezę indukcyjną oznaczamy jako $T_i$.
4. **Dowód indukcyjny**: Udowadaniamy, implikację $\phi(n)\implies\phi(n+1)$. Czyli z założenia $Z_{i}$  udowadniamy tezę $T_i$.

Jeżeli rozumowanie jest poprawne to na mocy indukcji matematycznej uzasadniamy, że warunek $\phi$ zachodzi dla każdej liczby naturalnej $n\ge n_0$.
## Wieża potęgowa
Wieżą potęg nazywamy $n$-krotne powtórzenie działania potęgowania. Nazwa wieża potęgowa bierze się z graficznej reprezentacji takiego potęgowania, które przedstawiamy następująco:
$$x^{x^{x^{x^{\dots^x}}}}$$
gdzie $x$ występuje dokładnie $n$ razy.

Leonhard Euler udowodnił, że przy $n\rightarrow\infty$, taka wieża potęg jest zbieżna, jeżeli
$$x\in\left[e^{-e}, e^{\frac{1}{e}}\right]$$
Bazując na wieży potęg, będącej w praktyce iterowanym potęgowaniem możemy zdefiniować kolejną operację nazywaną **tetracją**. Tetrację zapisujemy standardowo jako:
$$^nx$$
gdzie $x$ jest podstawą wieży, a $n$ jej wysokością.

Inną powszechnie stosowanym zapisem jest tzw. **notacja strzałkowa Knutha**, w której potęgowanie oznacza się jako $x\uparrow n$, a tetrację jako $x\upuparrows n$.

Tetracja rośnie zdecydowanie szybciej niż dowolna funkcja wykładnicza, przykładowo:
$$^33=7 625 597 484 987$$
## Tangramy
Tangramem nazywamy dowolne słowo, którego każda litera występuje parzystą liczbę razy. Przykładem tangramów mogą być słowa *mama*, *tata*.

Słowo tangram pochodzi od nazwy pewnej chińskiej łamigłówki polegającej na ułożeniu fragmentów kwadratu w konkretne symbole. Kwadrat zwyczajowo rozcina się na następujące elementy, nazywane tanami:
![[Pasted image 20260905161506.png|194]]

A następnie układa się z nich proste figury geometryczne, które znaleźć można w licznych książkach z łamigłówkami. Figury są przedstawione jedynie za pomocą ich obwodu, co skłania rozwiązującego do samodzielnego testowania różnych ułożeń.

