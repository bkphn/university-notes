## Regresja liniowa
**Regresja liniowa** (ang. *linear regression*) to metoda statystyczna służąca do badania i modelowania liniowej zależności między zmienną zależną $y$, a zmienną niezależną $x$. 

Przez $y$ rozumiemy wartość empiryczną, którą zwracają nam zmienne niezależne $x$. Wartość przewidywaną przez model oznaczamy jako $\hat{y}$. Wartość jest jedynie szacowaniem faktcznych wartości $y$.

Równanie wartości przewidywanej $\hat{y}$ wygląda następująco:

$$\hat{y}=wx+b$$

współczynniki $w,b$ nazywamy **parametrami wyuczalnymi** (ang. *learnable parameters*). Współczynniki $w,b$ przechowujemy w wektorze $\mathbf{w}=\begin{bmatrix}w \\ b\end{bmatrix}$.

Wyznaczenie współczynników $w,b$ sprowadza się do zminimalizowania wartości funkcji błędu $L$ opartej na metodzie najmniejszych kwadratów (ang. *least squares loss*), danej wzorem:

$$L(\mathbf{w})=\sum_{s=1}^S (y^{(s)}-\hat{y}^{(s)})^2$$

Aby nauczyć model regresji liniowej należy od obecnych wartości $\mathbf{w}$ odejmować ich gradient $\frac{\partial L(\mathbf{w})}{\partial\mathbf{w}}$. Gradient wskazuje kierunek największego wzrostu błędu, więc odejmując go zbliżamy się w stronę minimum funkcji minimalizując błąd:

$$\mathbf{w}^{(k+1)}= \mathbf{w}^{(k)}-\frac{\partial L(\mathbf{w}^{(k)})}{\partial \mathbf{w}^{(k)}}$$

gdzie $^{(k)}$ to obecna iteracja.

**Reguła łańcuchowa** (ang. *chain rule*) pozwala na rozbicie gradientu $\frac{\partial L(\mathbf{w})}{\partial\mathbf{w}}$ na ilocznyn pochodnej straty po przewidywaniach $\frac{\partial L(\mathbf{w})}{\partial \hat{y}(\mathbf{w})}$ oraz pochodnej przewidywań po wagach $\frac{\partial \hat{y}}{\partial \mathbf{w}}$:

$$\frac{\partial L(\mathbf{w})}{\partial \mathbf{w}}=\frac{\partial L(\mathbf{w})}{\partial\hat{y}(\mathbf{w})}\cdot\frac{\partial \hat{y}}{\partial \mathbf{w}}$$

które to z kolei możemy wyznaczyć ze wzorów:

$$\frac{\partial L(\mathbf{w})}{\partial \hat{y}(\mathbf{w})}=2\sum_{s=1}^S (y^{(s)}-\hat{y}^{(s)})(-1)$$

$$\frac{\partial\hat{y}}{\partial\mathbf{w}}=\begin{bmatrix}
x \\ 1
\end{bmatrix}$$
## Adaptacyjne neurony liniowe
Adaptacyjnym liniowym neuronem (ang. *adaptive linear neuron*) nazywamy funkcję $f$, która na wejściu przyjmuje wartości $x,b$, a zwraca wartość $\hat{y}$. Działa on w sposób identyczny do regresji linowej.

## Wielowymiarowa regresja liniowa
W praktyce wartość $x$ rzadko jest jednowymiarowa, co oznacza potrzebę rozszerzenia równania $\hat{y}=wx+b$ o kolejne wejścia. Dla $M$ wymiarów funkcja przybiera postać:

$$\hat{y}=w_{1}x_{1}+w_{2}x_{2}+\dots+w_{M}x_{M}+b=\sum_{m=1}^M w_{m}x_{m}+b$$

## Funkcja aktywacji
**Funkcją aktywacji** (ang. *activation function*) $\psi$ nazywamy funkcję, która przekształca sumę sygnałów wejściowych neuronu. Funkcję $\psi$ można zdefiniować na wiele sposobów, w zależności od potrzeb, wśród najpopularniejszych możemy wyróżnić:
- **Unipolarna funkcja sigmoidalna** (ang. *unipolar sigmoid*)
  $$\psi(z)=\frac{1}{1+e^{-z}}$$

- **Tangens hiperboliczny** (ang. *tangent hyperbolic*)
  $$\psi(z)=\frac{e^z-e^{-z}}{e^z+e^{-z}}$$

- **ReLU** (ang. *rectified linear unit*)
  $$\psi(z)=\max(\{0,z\})$$

- **Leaky ReLU** (ang. *leaky rectified linear unit*)
  $$\psi(z)=\max{(\{\alpha z,z\})}$$
  domyślnie parametr $\alpha=0.1$

## Neurony nieliniowe
Zbudowanie nieliniowego neuronu polega na przepuszczeniu zsumowanego, wielowymiarowego wyniku  $w_1x_1 + w_2x_2 +\dots+ b$ przez funkcję aktywacji $\psi$. Zmodyfikowane równanie przyjmuje dla $M$ wymiarów postać: 

$$\hat{y} = \psi\left(\sum_{m=1}^M w_{m}x_{m}+b\right)$$

## Współczynnik uczenia
Łatwo może dojść do sytuacji, w której trenowany model aktualizuje swoje wagi $\mathbf{w}$ w sposób powodujący oddalanie się od minimum globalnego funkcji $L$.

Aby temu zapobiec wprowadzamy **współczynnik uczenia** (ang. *learning rate*), oznaczany symbolem $\eta$, który jest mnożnikiem określającym wielkość kroku podczas aktualizacji wag za pomocą spadku gradientu.

$$\mathbf{w}^{(k+1)}=\mathbf{w}^{(k)}-\eta \frac{\partial L(\mathbf{w}^{(k)})}{\partial\mathbf{w}^{(k)}}$$

Współczynnik uczenia zazwyczaj przyjmuje wartość $\eta\in(0,1)$. W zaawansowanych optymalizatorach sieci neuronowych stosuje się adaptacyjny współczynnik uczenia (ang. *adaptive learning rate*), który dostosowuje się dynamicznie w trakcie uczenia

>[!example] Wyznacz wagi $\mathbf{w}$ 
>0. Dane
>Liczba epok $\varepsilon=3$
>Współczynnik uczenia $\eta=\frac{1}{2}$
>Wartości $x=(17,12), y=(12,12)$
>
>1. Inicjalizacja parametrów
>
>$$w_{1}=1, \qquad b=1$$
>
> $$L=\frac{1}{2}\sum^S_{s=1} (y^{(s)}-\hat{y}^{(s)})^2$$
>
>




