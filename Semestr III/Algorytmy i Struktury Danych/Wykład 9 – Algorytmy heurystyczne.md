## Heurystyka
Słowo **heurystyka** wywodzi się od greckiego *ευρεσις* oznaczającego *odnaleźć*. Heurystyka to metoda znajdowania rozwiązań problemu, dla którego nie ma gwarancji znalezienia rozwiązania optymalnego, a często nawet prawidłowego.

Heurystyki to algorytmy służące do rozwiązania problemów optymalizacyjnych lub innych, gdzie algorytm rozwiązujący jest zbyt kosztowny lub gdy jest nieznany. Często używamy modelu heurystycznego operatego o wzroce ze świata zwierząt lub roślin.

## Funkcje kryterialne
**Funkcją kryterialną** nazywamy funkcję wykorzystywaną w optymalizacji i modelowaniu, która definiuje cechy modelowanego zjawiska w postaci modelu matematycznego opisującego zależności optymalnego działania badanego zjawiska.

Jako funkcję kryterialną możemy przyjąć np. pierwszą funkcję testową de Jonga, definiowaną następująco:

$$f_{\text{deJong1}}(\mathbf{x}) = \sum_{i=1}^{N} x_i^2$$

  gdzie $N$ to wymiar punktu $\mathbf{x}$ o współrzędnych $x_i$. Funkcja ta przyjmuje minimum w punkcie $f_{dejong1}(0) = 0$ .

Innym przykładem funkcji kryterialnej może być funkcja testowa Rastragina, definiowana następująco:

$$f_{\text{Rastr}}(\mathbf{x}) = 10 \cdot N + \sum_{i=1}^{N} (x_i^2 - 10 \cos(2\pi \cdot x_i))$$

## Optymalizacja gradientowa
Optymalizacja gradientowa jest jedną z metod optymalizacji. Algorytm numeryczny wykorzystuje kierunek gradientu w przestrzeni poszukiwań rozwiązań modelu matematycznego. Algorytm rozpoczyna się od losowego wyboru punktu $\mathbf{x}_{0}$, który jest pierwszą losową optymalną pozycją. 

W dalszych krokach kierujemy się gradientem. Gradient $\nabla f(\mathbf{x}_{i})$ jest kierunkiem najszybszego wzrostu funkcji mierzonym w punkcie . Następnie nowy punkt znajdujemy za pomocą formuły:

$$\mathbf{x}_{i}^{t+1}=\mathbf{x}_{i}^t-\lambda\cdot\nabla f(\mathbf{x}_{i})$$

gdzie dla punktów $\mathbf{x}_{i}$ parametr $\lambda$ reprezentuje wartość kroku, a $t$ to horyzont czasu reprezentowany przez iteracje. Jeśli wartość funkcji kryterialnej $f$ dla nowego punktu $\mathbf{x}_{i}^{t+1}$ jest mniejsza niż $f(\mathbf{x}_{i})$, to nowy punkt zamienia stary. Algorytm jest wykonywany do spełnienia warunku zatrzymania, np. liczba iteracji lub dokładność.

## Algorytm genetyczny
Algorytm genetyczny został stworzony przez Johna Hollanda w 1973 roku. Główną ideą było stworzenie programu komputerowego rozwiązaującego problemy w sposób podobny do naturalnego procesu ewolucji. Zastosowano ewolucję populacji składającej się z pewnej liczby osobników, w której każda osoba miała ustawiona binarny kod genetyczny odpowiadający chromosomom w organizmach oraz operacje, które zachodzą podczas biologicznego procesu ewolucji.

Pierwszym krokiem algorytmu genetycznego jest inicjalizacja, która polega na ustaleniu wielkości populacji, kodowaniu chromosomów i funkcji kryterialnej z zestawem ograniczeń. Elementy początkowej populacji znajdujemy w sposób losowy. Kolejnym krokiem jest reprodukcja. Osobnik $\mathbf{x}_{i}$ jest przenoszony do następnego pokolenia z prawdopodobieństwem, które rośnie wraz z wyższym poziomem funkcji kryterialnej $f(x)$. 

Dla wybranej grupy w populacji $\mathcal{P}^t$ określamy zmienną losową $p_{r}$ za pomocą równań:

$$p_r(\mathbf{x}_{i}^t) =\frac{f(\mathbf{x}_{i}^t)}{\mathbf{x}_{i}^t},\qquad \mathbf{x}_{i}^t\in\mathcal{P}^t$$

Losowa zmienna jest próbkowana kilka razy i wprowadzana jest funkcja rozkładu prawdopodobieństwa rozmnażania:

$$P_{r}(\mathbf{x}_{i}^t)=\sum_{j=1}^i p_{r}(\mathbf{x}_{i}^t)$$

następnie pobierana jest losowa liczba $\alpha\in(0,1)$. Jeśli osobnik $\mathbf{x}_{i}$ spełnia założenie:

$$P_{r}(\mathbf{x}_{i-1}^t)<\alpha<P_{r}(\mathbf{x}_{i}^t)$$

to jest reprodukowany. Reprodukcja jest kontrolowana przez operator genetyczny, który pozwala tworzyć zróżnicowaną populację. Operatory klasyczne to mutacje i krzyżowanie.

Mutacja to proces zmiany chromosomów, na przykład dodanie losowego $\mathbf{\xi}\in(0,1)^N$, zmutowanego osobnika $\mathbf{x}_{i}^{t+1}$ definiujemy następująco:

$$x_{i}^{t+1}\leftarrow \mathbf{x}_{i}^t+\xi$$

Krzyżowanie to operacja, w której wymieniany jest materiał genetyczny między dwoma osobnikami, nazywanymi rodzicami. Krzyżowanie dwóch rodziców tworzy dwie osoby, które są dodawane do populacji. Następnie chromosomy rodzicielskie są uśredniane za pomocą następującej formuły:

$$\mathbf{x}_{i}^{t+1}=\mathbf{x}_{i}^{t+1}+\eta(\mathbf{x}_{i+1}^t-\mathbf{x}_{i}^t)$$

gdzie $\mathbf{x}_{i},\mathbf{x}_{i+1}$ to rodzice, a $\eta$ to losowa liczba z przedziału $(0,1)$.

W następnym kroku wszystkie osoby muszą zostać ocenione, w jaki sposób pasują do środowiska. Nowa populacja zastępuje starszą. Proces ten nazywamy sukcesją.

## Ewolucja różnicowa
Ewolucja różnicowa została zaproponowana w 1997 roku. Algorytm ten jest heurystycznym podejściem do minimalizowania nieliniowych i nierozróżnialnych funkcji przestrzeni ciągłej. Algorytm ewolucji różnicowej opiera się na trzech argumentach:
  * $N_P$ – wielkość populacji,
  * $F$ – parametr kontroli mutacji,
  * $P_C$ – prawdopodobieństwo krzyżowania.

Ewolucja różnicowa działa na populacji $\mathcal{X}$ osobników $\mathbf{x}_{i}$, gdzie $i\in\set{1,\dots,N_{P}}$ oraz $\mathbf{x}_{i}=\left[\begin{matrix}x_{1i}\\\vdots\\x_{Di}\end{matrix}\right]$.
Na początek tworzymy losowo populację osobników $x_i^G$, gdzie $G=1$ jest liczbą osób w populacji. 

- **Mutacja** to losowe permutacje wektorów $x_i$ poprzez różnicowanie dwóch wektorów z populacji $\mathcal{X}$, skalując je przez stałą wartość. Dla każdego wektora $x_i^G$ generujemy zmutowany wektor $\mu(x_i^G)$:

  $$\mu(x_i^{G+1}) = x_{r_1}^G + F \cdot (x_{r_2}^G - x_{r_3}^G)$$

  o losowych indeksach $r_1, r_2, r_3$, a $F \in [0, 2]$.

* **Krzyżowanie** to mieszanie losowych elementów wektora macierzystego $x_i^G$ oraz wektora $\mu(x_i^{G+1})$ po mutacji. Nowy wektor oznaczmy przez $\beta(x_i^G, \mu(x_i^{G+1}))$, a elementy tego wektora definiujemy następująco:

$$(b_i^{G+1})_j = \begin{cases} (\mu_i^{G+1})_j, & R < P_C \wedge j = d_i \\ (x_i^G)_j, & R > P_C \wedge j \neq d_i \end{cases}$$

  gdzie $R$ jest jednolitym generatorem liczb pseudolosowych z przedziału $[0, 1]$, a $d_i \in \{1, 2, ..., D\}$ jest losowym indeksem.

## Algorytm Kukułki
Algorytm Kukułki został wprowadzony przez Yanga i Deba w 2009 roku. Algorytm ten jest bardzo skutecznyną techniką optymalizacji bezgradientowej, w której stosujemy rozkład Gaussa. Algorytm symuluje zachowanie kukułek, które mają szczególny model rozmnażania. Kukułka leci i szuka gniazda, by złożyć jajo. Wybiera gniazdo, gdzie są już jaja. Kukułki składają jajo i odlatują. Kiedy gospodarze wracają do domu to albo pozbywają się jaja, albo akceptują sytuację.

Proces poszukiwania gniazda jest częścią algorytmu kukułki, gdzie przez $\mathbf{x}_{i}$ będziemy oznaczać kukułkę. Każda kukułka będzie miała do złożenia tylko jedno jajo. Najlepsze gniazda zawierające jajka są przenoszone do następnej generacji. Reszta populacji kukułki jest rozmieszczana losowo. Hosty mogą rozpoznać jajo intruza z prawdopodobieństwem $1-p_{\alpha}\in[0,1]$ i pozbyć się go. W tym przypadku nowa kukułka rozmieszczana jest losowo.

Wirtualny ruch kukułki definiujemy jako:

$$x_i^{t+1} = x_i^t + \mu \cdot L(\beta, \gamma, \delta)$$

gdzie:
  * $x_i^{t+1}$ to nasza kukułka w czasie $t+1$,
  * $\mu$ to długość kroku w błądzeniu losowym,
  * $L(\beta, \gamma, \delta)$ to lot Lévy'ego o kroku $\beta$,
  * $\delta$ to minimalna długość kroku w błądzeniu losowym,
  * $\gamma$ to parametr skalujący lot Lévy'ego.
 
**Lot Lévy'ego** definiujemy następująco:

  $$L(\beta, \gamma, \delta) = \begin{cases} \sqrt{\frac{\gamma}{2\pi}} \cdot \frac{\exp\left(-\frac{\gamma}{2(\beta-\delta)}\right)}{(\beta-\delta)^{\frac{3}{2}}}, & 0 < \delta < \beta < \infty \\ 0, & \text{w p. p.} \end{cases}$$

Na koniec określamy, czy jajo kukułki zostało odkryte.
