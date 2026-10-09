## Dyskretne perceptrony
**Perceptron dyskretny** to najprostszy model sztucznego neuronu, pełniący funkcję binarnego klasyfikatora liniowego. Określenie dyskretny odnosi się do zastosowanej w nim funkcji aktywacji, która przyjmuje skończoną liczbę wartości.

Liczba neuronów w warstwie wyjściowej musi być równa liczbie wyjść. Dla dwóch wyjść $o_{1},o_{2}$ potrzebujemy dwóch neuronów w warstwie wyjściowej.

**Linią separującą** (ang. *separation line*) nazywamy prostą $H$, która dzieli przestrzeń wejściową (tworzoną przez wektory $x$) na dwie części. Pozwala to na oddzielenie od siebie próbek należących do różnych klas, którym następnie przypisywana jest ostateczna wartość za pomocą funkcji aktywacji $\psi$.

>[!example] Zaprojektuj jednowarstwową sieć neuronową z dwoma wejściami i dwoma wyjściami z dyskretną aktywacją $\psi$, gdzie $\psi$ jest funkcją skokową Heaviside'a.
> 0. Dane
> 
> | $x_{1}$ | $x_{2}$ | $o_{1}$ | $o_{2}$ |
> | ------- | ------- | ------- | ------- |
> | $0$     | $0$     | $0$     | $0$     |
> | $0$     | $1$     | $1$     | $0$     |
> | $1$     | $0$     | $0$     | $1$     |
> | $1$     | $1$     | $0$     | $0$     |
>
> $$\psi(z)=\begin{cases} 1, \qquad z\geq 0 \\ 0, \qquad z<0\\ \end{cases}$$
>
>
>
> 1. Wyznaczamy równania linii sepracujących
>
> $$H_{1}=w_{1}^{(1)}x_{1}+w_{2}^{(1)}x_{2}+b^{(1)}=-x_{1}+x_{2}+b^{(1)}$$
> 
> $$H_{2}=w_{1}^{(2)}x_{1}+w_{2}^{(2)}x_{2}+b^{(2)}=x_{1}-x_{2}+b^{(2)}$$
>
> Możemy zauważyć, że: 
> $$b^{(1)}\in(-1,0)$$
> 
> $$b^{(2)}\in(-1,0)$$
>
>2. Wynik
>
> $$o_{1}=\psi(H_{1})=\psi(-x_{1}+x_{2}+b^{(1)})$$
>
>$$o_{2}=\psi(H_{2})=\psi(+x_{1}-x_{2}+b^{(2)})$$

## Płytka sieć neuronowa
**Płytka sieć neuronowa** (ang. *shallow neural network*) to sztuczna sieć neuronowa o najprostszej możliwej do zastosowania w uczeniu maszynowym architekturze. Jej kluczową cechą jest to, że pomiędzy danymi wejściowymi a wynikiem znajdują się zazwyczaj maksymalnie dwie warstwy.

Jeżeli dana sieć neuronowa posiada od trzech warstw wzwyż (w uczeniu maszynowym nie liczymy warstwy wejściowej – nie wykonuje ona żadnych obliczeń) to sieć taką nazywamy **głęboką siecią neuronową** (ang. *deep neural network*).

>[!danger] Twierdzenie o uniwersalnej aproksymacji
>Jednokierunkowa sieć neuronowa z jedną skończoną warstwą ukrytą może z dowolną dokładnością przybliżyć każdą ciągłą funkcję na zbiorach domkniętych i ograniczonych przestrzeni euklidesowych.

![[Pasted image 20261008182839.png|400]]
## Operator nabla
Pole wektorowe wskazujące kierunki najszybszych wzrostów wartości danego pola skalarnego w poszczególnych punktach nazywamy **gradientem**.

Gradient pewnej funkcji $f(x_{1},\dots,x_{n})$ oznaczamy jako $\nabla f$, gdzie $\nabla$ to wektorowy operator różniczkowy nazywany **nabla**. W układzie współrzędnych kartezjańskich gradient jest wektorem, którego składowe są pochodnymi cząstkowymi funkcji $f$. W układzie współrzędnych kartezjańskich składowe gradientu funkcji $f$ są pochodnymi cząstkowymi.

$$\nabla f=\begin{bmatrix}
\frac{\partial f}{\partial x_{1}} & \dots & \frac{\partial f}{\partial x_{n}}
\end{bmatrix}$$

Zapis $\nabla_{\mathbf{v}} f$ definiuje układ pochodnych cząstkowych funkcji obliczanych po kolejnych zmiennych zgrupowanych w wektorze $\mathbf{v}$. W zależności od tego, czy badana funkcja zwraca wartość liczbową, czy wektor, definicja tej macierzy przyjmuje jedną z dwóch podstawowych form:
- **Dla funkcji skalarnej**: Jeżeli funkcja $f(\mathbf{v})$ ma charakter skalarny (tzn. $f: \mathbb{R}^n \to \mathbb{R}$), a wektor zmiennych składa się z $n$ współczynników $\mathbf{v} = [v_1, v_2, \dots, v_n]^T$, to operator $\nabla_{\mathbf{v}} f$ jest klasycznym gradientem. W ujęciu algebry liniowej wektor ten reprezentowany jest jako macierz pionowa o wymiarach $n \times 1$:

$$\nabla_{\mathbf{v}} f = \begin{bmatrix} \frac{\partial f}{\partial v_1} \\ \frac{\partial f}{\partial v_2} \\ \vdots \\ \frac{\partial f}{\partial v_n} \end{bmatrix}$$

- **Dla funkcji wektorowej** Jeżeli operujemy na funkcji wektorowej (tzn. $\mathbf{f}: \mathbb{R}^n \to \mathbb{R}^m$), która składa się z $m$ niezależnych funkcji skalarnych $\mathbf{f}(\mathbf{v}) = [f_1(\mathbf{v}), f_2(\mathbf{v}), \dots, f_m(\mathbf{v})]^T$, to $\nabla_{\mathbf{v}} \mathbf{f}$ oznacza pełną macierz pochodnych cząstkowych, powszechnie określaną mianem macierzy Jacobiego.
  
  $$\nabla_{\mathbf{v}} \mathbf{f} = \begin{bmatrix} \frac{\partial f_1}{\partial v_1} & \frac{\partial f_1}{\partial v_2} & \dots & \frac{\partial f_1}{\partial v_n} \\ \frac{\partial f_2}{\partial v_1} & \frac{\partial f_2}{\partial v_2} & \dots & \frac{\partial f_2}{\partial v_n} \\ \vdots & \vdots & \ddots & \vdots \\ \frac{\partial f_m}{\partial v_1} & \frac{\partial f_m}{\partial v_2} & \dots & \frac{\partial f_m}{\partial v_n} \end{bmatrix}$$

Zastosowanie takiej konwencji macierzowej upraszcza obliczenia wymagające reguły łańcuchowej (chain rule) w rachunku wielowymiarowym, co jest fundamentalne m.in. w mechanice analitycznej przy równaniach Eulera-Lagrange'a oraz w systemach uczących algorytmów sztucznej inteligencji (wsteczna propagacja błędu).

## Sprzężenie w przód
**Sprzężenie w przód** (ang. *feedforward*) FF to architektura, w której sygnał przepływa jednokierunkowo: od warstwy wejściowej, przez warstwy ukryte, aż do wyjściowej, bez tworzenia pętli sprzężenia zwrotnego

![[Pasted image 20261008182922.png|406]]

gdzie $\Phi, \Psi$ to funkcje aktywacji. 

W powyższej sieci możemy wyróżnić dwie warstwy, każdą z nich możemy wyrazić w zapisie skalarnym, bądź macierzowym:
1. **Warstwa pierwsza**
   - Zapis skalarny: $z_{i}=\Phi\left( \sum_{n=1}^N w_{i,n}x_{n}+b_{i} \right)$
   - Zapis macierzowy: $\mathbf{z}=\Phi(\mathbf{W}\mathbf{x}+\mathbf{b})$

$$\mathbf{x}=\begin{bmatrix}x_{1} \\ \vdots \\ x_{N}\end{bmatrix} \qquad 
\mathbf{b}=\begin{bmatrix} b_{1}\\ \vdots \\ b_{M} \end{bmatrix} \qquad \mathbf{W}=\begin{bmatrix} w_{1,1} & \cdots & w_{1,n} \\  \vdots & \ddots & \vdots \\w_{M,1} & \cdots & w_{M,N}\end{bmatrix}$$

2. **Warstwa druga**
   - Zapis skalarny: $\hat{y}=\Psi\left( \sum_{m=1}^M v_{m}z_{m}+c \right)$
   - Zapis macierzowy: $\hat{y}=\Psi(\mathbf{v}\cdot \mathbf{z}+c)$
$$\mathbf{v}=\begin{bmatrix} v_{1}  & v_{2}  & \dots & v_{M} \end{bmatrix} \qquad \mathbf{z}=\begin{bmatrix} z_{1} \\ \vdots \\ z_{M} \end{bmatrix}$$

## Backpropagation
**Backpropagation** (propagacja wsteczna) BP to algorytm służący do efektywnego obliczania gradientu funkcji straty względem wag sieci, oparty na regule łańcuchowej różniczkowania. Umożliwia on aktualizację wag w procesie uczenia.
![[Pasted image 20261008182959.png|443]]

Niech $L(\mathbf{v})=\mathrm{MSE}(\mathbf{v})$. Pojedynczą wagę $v_{i}$ będziemy aktualizować za pomocą wzoru:

$$v_{i}\leftarrow v_{i}-\eta \frac{\partial L(v_{i})}{\partial v_{i}}$$

Co możemy rozpisać jako: 

$$v_{i}-\eta \frac{\partial L(v_{i})}{\partial v_{i}}=v_{i}-\eta\cdot\color{red}{\frac{\partial L(v_{i})}{\partial\hat{y}}}\color{black}{\cdot}\color{blue}{\frac{\partial \hat{y}}{\partial v_{i}}}\color{black}=v_{i}-\eta\cdot\color{red}\frac{2}{S}\sum_{s=1}^S (y^{(s)}-\hat{y}^{(s)})(-1)\color{black}\cdot  \color{blue}\Psi'\left( \sum_{m=1}^M v_{m}z_{m}+c \right)\cdot z_{i}$$

W zapisie macierzowym wyrazimy to jako:

$$\mathbf{v}\leftarrow \mathbf{v}-\eta\nabla_{\mathbf{v}} L=\mathbf{v}-\eta \begin{bmatrix}
 \frac{\partial L}{\partial v_{1}} \\ \frac{\partial L}{\partial v_{2}} \\ \vdots \\\frac{\partial L}{\partial v_{M}} \\ \frac{\partial L}{\partial c}
\end{bmatrix}=\mathbf{v}-\eta \frac{\partial L}{\partial \hat{y}} \begin{bmatrix}
 \frac{\partial \hat{y}}{\partial v_{1}} \\ \frac{\partial \hat{y}}{\partial v_{2}} \\ \vdots \\ \frac{\partial \hat{y}}{\partial v_{M}} \\ \frac{\partial \hat{y}}{\partial c}
\end{bmatrix}$$

