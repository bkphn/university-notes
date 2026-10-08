## Funkcja znaku


## Dyskretne perceptrony
Zaprojektów jednowarstwową (ang. *single-layer*) sieć neuronową z dwoma wejściami i dwoma wyjściami z unipolarną dyskretną aktywacją (ang. *unipolar discrete activation*) *to realize the following* (*unit-step function*).

| $x_{1}$ | $x_{2}$ | $o_{1}$ | $o_{2}$ |
| ------- | ------- | ------- | ------- |
| $0$     | $0$     | $0$     | $0$     |
| $0$     | $1$     | $1$     | $0$     |
| $1$     | $0$     | $0$     | $1$     |
| $1$     | $1$     | $0$     | $0$     |
Liczba neuronów w warstwie wyjściowej musi być równa liczbe wyjść. Dla dwóch wyjść $o_{1},o_{2}$ potrzebujemy dwóch neuronów w warstwie wyjściowej.

$$\mathrm{sgn}'{(x)}=0$$

$H_{1}$ – *seperation line*

$$H_{1}=w_{1}^{(1)}x_{1}+w_{2}^{(1)}x_{2}+b^{(1)}=-x_{1}+x_{2}+b^{(1)}$$
$$H_{2}=w_{1}^{(2)}x_{1}+w_{2}^{(2)}x_{2}+b^{(2)}=x_{1}-x_{2}+b^{(2)}$$
Dopasowujemy tak, żeby zwracało wartości dodatnie dla $o=1$ i ujemne dla $o=0$ i jako funkcja aktywacji używamy funkcji aktywacji znaku.
$b^{(1)}\in(-1,0)$
$b^{(2)}\in(0,1)$

## Płytka sieć neuronowa
**Płytka sieć neuronowa** (ang. *shallow neural network*) 

Od trzech warstw sieci to deep learning, poniżej trzech warstw mamy płytką sieć. Udowodniono, że 3 warstwy są konieczne przybliżenia każdej funckji.

$x_{1},x_{2}\rightarrow\Phi\dots\Phi\rightarrow\Psi\rightarrow \hat{y}$
$w_{i,i}$, $v_{i}$



**Feed forward** do przodu sieć.

1. **Warstwa pierwsza**

$z_{i}=\Phi\left( \sum_{n=1}^N w_{in}x_{n}+b_{i} \right)$ – zapis skalarny

$\mathbf{z}=\Phi(\mathbf{W}\mathbf{x}+\mathbf{b})$ – zapis macierzowy
$$\mathbf{x}=\begin{bmatrix}x_{1} \\ \vdots \\ x_{N}\end{bmatrix} \qquad \mathbf{b}=\begin{bmatrix} b_{1}\\ \vdots \\ b_{M} \end{bmatrix} \qquad \mathbf{W}=\begin{bmatrix} w_{1,1} & \cdots & w_{1,n} \\  \vdots & \ddots & \vdots \\w_{M,1} & \cdots & w_{M,N}\end{bmatrix}$$
2. **Warstwa druga**
$\hat{y}=\Psi\left( \sum_{m=1}^M v_{m}z_{m}+c \right)$ – zapis skalarny
$\hat{y}=\Psi(\mathbf{v}\cdot \mathbf{z}+c)$ – zapis wektorowy
gdzie
$$\mathbf{v}=[v_{1}, v_{2},\dots,v_{M}] \qquad \mathbf{z}=\begin{bmatrix}
z_{1} \\ \vdots \\ z_{M}
\end{bmatrix}$$

## Backpropagation
**Backpropagation** to propagacja błędu do poprzednich warstw sieci.
$L(\mathbf{v})=\frac{1}{s}\sum_{s=1}^S (y^{(s)}-\hat{y}^{(s)})^2$



$$v_{1}\leftarrow v_{1}-\eta \frac{\partial L(v_{1})}{\partial v_{1}}=v_{1}-\eta\frac{\partial L(v_{1})}{\partial\hat{y}}\cdot\frac{\partial \hat{y}}{\partial v_{1}}=v_{1}-\eta\frac{2}{S}\sum_{s=1}^S (y^{(s)}-\hat{y}^{(s)})(-1)\cdot \Psi'\left( \sum_{m=1}^M v_{m}z_{m}+c \right)\cdot z_{1}$$

$$\mathbf{v}\leftarrow \mathbf{v}-\eta\nabla_{\mathbf{v}} L=\mathbf{v}-\mathbf{v}-\eta \begin{bmatrix}
 \frac{\partial L}{\partial v_{1}} & \frac{\partial L}{\partial v_{2}} & \dots &\frac{\partial L}{\partial v_{N}} & \frac{\partial L}{\partial c}
\end{bmatrix}=\mathbf{v}-\mathbf{v}-\eta \frac{\partial L}{\partial \hat{y}} \begin{bmatrix}
 \frac{\partial \hat{y}}{\partial v_{1}} & \frac{\partial \hat{y}}{\partial v_{2}} & \dots &\frac{\partial \hat{y}}{\partial v_{N}} & \frac{\partial \hat{y}}{\partial c}
\end{bmatrix}$$

$\frac{\partial v_{1}}{\partial \hat{y}}=\Psi'\left( \sum_{m=1}^M v_{m}z_{m} +c \right)\cdot z_{1}$
*mean-square error* or any loss function
