## Regresja liniowa
**Regresja liniowa** (ang. *linear regression*) to metoda statystyczna służąca do badania i modelowania liniowej zależności między zmienną zależną $y$, a zmienną niezależną $x$. 

Zmienna zależna $y$ reprezentuje obserwowaną wartość objaśnianą za pomocą zmiennej niezależnej $x$. Model regresji wyznacza jej przewidywaną wartość oznaczaną jako $\hat y$.

Równanie wartości przewidywanej $\hat{y}$ wygląda następująco:

$$\hat{y}=wx+b$$

współczynniki $w,b$ nazywamy **parametrami wyuczalnymi** (ang. *learnable parameters*). Współczynniki $w,b$ przechowujemy w wektorze $\mathbf{w}=(w,b)$.

Wyznaczenie współczynników $w,b$ sprowadza się do zminimalizowania wartości **funkcji błędu** $\mathcal{L}$ w tym przypadku opartej na metodzie najmniejszych kwadratów, danej wzorem:

$$\mathcal{L}(\mathbf{w})=\frac{1}{S}\sum_{s=1}^S (y^{(s)}-\hat{y}^{(s)})^2$$

Aby nauczyć model regresji liniowej należy od obecnych wartości $\mathbf{w}$ odejmować ich gradient $\frac{\partial \mathcal{L}(\mathbf{w})}{\partial\mathbf{w}}$. Gradient wskazuje kierunek największego wzrostu błędu, więc odejmując go zbliżamy się w stronę minimum funkcji minimalizując błąd:

$$\mathbf{w} \leftarrow\mathbf{w}^{}-\frac{\partial \mathcal{L}(\mathbf{w})}{\partial \mathbf{w}}$$

**Reguła łańcuchowa** (ang. *chain rule*) pozwala na rozbicie gradientu $\frac{\partial \mathcal{L}(\mathbf{w})}{\partial\mathbf{w}}$ na iloczyn pochodnej straty po przewidywaniach $\frac{\partial L(\mathbf{w})}{\partial \hat{y}}$ oraz pochodnej przewidywań po wagach $\frac{\partial \hat{y}}{\partial \mathbf{w}}$:

$$\frac{\partial \mathcal{L}(\mathbf{w})}{\partial \mathbf{w}}=\frac{\partial \mathcal{L}(\mathbf{w})}{\partial\hat{y}}\cdot\frac{\partial \hat{y}}{\partial \mathbf{w}}$$

## Funkcje błędu
**Funkcją błędu** nazywamy pewną funkcję $\mathcal{L}$, która jako argumenty przyjmuje parametry wyuczalne danego modelu, a jako wartość zwraca ich błąd. Funkcję $\mathcal{L}$ można zdefiniować na wiele sposobów, w zależności od potrzeb, wśród najpopularniejszych możemy wyróżnić:
- **Metoda najmniejszych kwadratów** (ang. *least square loss*) SSE
  $$\mathcal{L}(\mathbf{w})=\frac{1}{2}\sum_{s=1}^S \left(y^{(s)}-\hat{y}^{(s)}\right)^2=\mathrm{SSE}(\mathbf{w})$$
  $$\mathcal{L}'(\mathbf{w})=\hat y^{(s)}-y^{(s)}=\mathrm{SSE}'(\mathbf{w})$$

- **Błąd średniokwadratowy** (ang. *mean square error*) MSE
  $$\mathcal{L}(\mathbf{w})=\frac{1}{S}\sum_{s=1}^S\left( y^{(s)} -\hat{y}^{(s)}\right)^2=\mathrm{MSE}(\mathbf{w})$$
  $$\mathcal{L}'(\mathbf{w})=\frac{2}{S}\sum_{s=1}^S(\hat y^{(s)}-y^{(s)})(-1)=\mathrm{MSE}'(\mathbf{w})$$

## Adaptacyjne neurony liniowe
Adaptacyjnym liniowym neuronem (ang. *adaptive linear neuron*), nazywanym w skrócie **ADALINE**, nazywamy funkcję $f$, która na wejściu przyjmuje wartości $x,b$ wraz z wagami $\mathbf{w}$, a zwraca wartość $\hat{y}$.

ADALINE działa w fazie uczenia w sposób identyczny do regresji liniowej, jednak jako klasyfikator rozszerza ten proces o przepuszczenie ostatecznego wyniku przez funkcję progową decydującą o przynależności do klasy.

![[Pasted image 20261008182206.png|343]]

## Wielowymiarowa regresja liniowa
W praktyce wartość $x$ rzadko jest jednowymiarowa, co oznacza potrzebę rozszerzenia równania $\hat{y}=wx+b$ o kolejne wejścia. Dla $M$ wymiarów funkcja przybiera postać:

$$\hat{y}=w_{1}x_{1}+w_{2}x_{2}+\dots+w_{M}x_{M}+b=\sum_{m=1}^M w_{m}x_{m}+b$$

## Funkcja aktywacji
**Funkcją aktywacji** (ang. *activation function*) $\psi$ nazywamy funkcję, która przekształca sumę sygnałów wejściowych neuronu. Funkcję $\psi$ można zdefiniować na wiele sposobów, w zależności od potrzeb, wśród najpopularniejszych możemy wyróżnić:
- **Unipolarna funkcja sigmoidalna** (ang. *unipolar sigmoid*)
  $$\psi(z)=\frac{1}{1+e^{-z}}=\sigma(z)$$
  $$\psi'(z)=\frac{e^{-z}}{(1+e^{-z})^2}=\sigma'(z)
$$

- **Tangens hiperboliczny** (ang. *tangent hyperbolic*)
  $$\psi(z)=\frac{e^z-e^{-z}}{e^z+e^{-z}}=\tanh(z)$$
  $$
\psi'(z)=\frac{4}{(e^z+e^{-z})^2}=\tanh'(z)
$$

- **ReLU** (ang. *rectified linear unit*)
  $$\psi(z)=\max(\{0,z\})=\mathrm{ReLU}(z)$$
  $$
\psi'(z)=
\begin{cases}
0 & z<0\\
1 & z>0
\end{cases}=\mathrm{ReLU}'(z)
$$

- **Leaky ReLU** (ang. *leaky rectified linear unit*)
  $$\psi(z)=\max{(\{\alpha z,z\})}=\mathrm{LReLU}(z)$$
  
  $$
\psi'(z)=
\begin{cases}
\alpha & z<0\\
1 & z>0
\end{cases}=\mathrm{LReLU}'(z)$$
  
  domyślnie parametr $\alpha=0.1$

- **Funkcja skokowa Heaviside'a** (ang. *step function*)
  $$\psi(z)=\begin{cases}
  1, \qquad z\geq 0 \\
  0, \qquad z < 0
  \end{cases}=\mathbb{1}(z)$$
  $$ \psi'(z)=0= \mathbb{1}'(z)  $$
  
  Pochodna $\mathbb{1}'(z)$ nie istnieje dla $z=0$.
## Neurony nieliniowe
Zbudowanie nieliniowego neuronu polega na przepuszczeniu zsumowanego, wielowymiarowego wyniku  $w_1x_1 + w_2x_2 +\dots+ b$ przez funkcję aktywacji $\psi$. Zmodyfikowane równanie przyjmuje dla $M$ wymiarów postać:

$$\hat{y} = \psi\left(\sum_{m=1}^M w_{m}x_{m}+b\right)$$

![[Pasted image 20261008182325.png|372]]

## Współczynnik uczenia
Łatwo może dojść do sytuacji, w której trenowany model aktualizuje swoje wagi $\mathbf{w}$ w sposób powodujący oddalanie się od minimum globalnego funkcji $\mathcal{L}$ (np. wartość pochodnej jest zbyt wielka i model oddala się od rozwiązania, albo utyka w minimum lokalnym).

Aby temu zapobiec wprowadzamy **współczynnik uczenia** (ang. *learning rate*), oznaczany symbolem $\eta$, który jest mnożnikiem określającym wielkość kroku podczas aktualizacji wag za pomocą spadku gradientu.

$$\mathbf{w}\leftarrow\mathbf{w}-\eta \frac{\partial \mathcal{L}(\mathbf{w})}{\partial\mathbf{w}}$$

Współczynnik uczenia zazwyczaj przyjmuje wartość $\eta\in(0,1)$. W zaawansowanych optymalizatorach sieci neuronowych stosuje się adaptacyjny współczynnik uczenia (ang. *adaptive learning rate*), który dostosowuje się dynamicznie w trakcie uczenia.

>[!example] Wyznacz wagi $w,b$
>
>0. Dane
>
>Liczba epok $\varepsilon=3$
>
>Współczynnik uczenia $\eta=0.5$
>
>Wartości $x,y$
>
>
> | $x$ | $y$ |
> | ----- | ----- |
> | $17$  | $12$  |
> | $12$  | $17$  |
>
>1. Inicjalizacja parametrów
  >
>
>$$w=1, \qquad b=0$$
>
>$$\mathcal{L}(\mathbf{w})=\frac{1}{2}\sum^S_{s=1} (y^{(s)}-\hat{y}^{(s)})^2$$
>
$$\hat{y}=wx+b$$
>
$$w\leftarrow w-\eta\frac{\partial \mathcal{L}}{\partial w}, \qquad b\leftarrow b-\eta\frac{\partial \mathcal{L}}{\partial b}$$
>
$$\frac{\partial \mathcal{L}}{\partial w}=\sum_{s=1}^S -(y^{(s)}-\hat{y}^{(s)})x^{(s)}, \qquad \frac{\partial \mathcal{L}}{\partial b}=\sum_{s=1}^S -(y^{(s)}-\hat{y}^{(s)})$$
>
>2. Pierwsza epoka
  >  
>$$\hat{y}_{1}^{(1)}=1\cdot 17 + 0 =17, \qquad \hat{y}_{2}^{(1)}=1\cdot 12+0=12$$
  > 
>
>$$w^{(1)}=1-0.5\cdot\left( -(12-17)(17) - (17-12)(12) \right) = -11.5$$
>
>$$b^{(1)} = 0 - 0.5 \cdot \left( -(12-17) - (17-12) \right) = 0$$
>
>3. Druga epoka
  > 
>$$\hat{y}_{1}^{(2)}=-11.5\cdot 17 +0=-195.5, \qquad \hat{y}_{2}^{(2)}=-11.5\cdot 12 + 0 = -138$$
  > 
>
>$$w^{(2)} = -11.5 - 0.5 \cdot \left( -(12 - (-195.5))(17) - (17 - (-138))(12) \right) = 2682.25$$
>
>$$b^{(2)} = 0 - 0.5 \cdot \left( -(12 - (-195.5)) - (17 - (-138)) \right) = 181.25$$
>
>4. Trzecia epoka
  > 
>$$\hat{y}_{1}^{(3)} = 2682.25 \cdot 17 + 181.25 = 45779.5, \qquad \hat{y}_{2}^{(3)} = 2682.25 \cdot 12 + 181.25 = 32368.25$$
  >
  > 
>$$w^{(3)} = 2682.25 - 0.5 \cdot \left( -(12 - 45779.5)(17) - (17 - 32368.25)(12) \right) = -580449$$
>
$$b^{(3)} = 181.25 - 0.5 \cdot \left( -(12 - 45779.5) - (17 - 32368.25) \right) = -38878.125$$
>
>5. Wynik
  > 
>$$\hat{y}=-580449x -38878.125$$
  > 
>Możemy zauważyć, że nasz model przestrzelił minimum (ang. _overshooting_) i ucieka do nieskończoności, błędnie aproksymuje on punkty $(17,12), (12,17)$.

