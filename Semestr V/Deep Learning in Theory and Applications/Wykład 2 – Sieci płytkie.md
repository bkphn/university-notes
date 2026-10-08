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

$x_{1},x_{2}\rightarrow\Phi\dots\Phi\rightarrow\Psi\rightarrow \hat{y}$
$w_{i,i}$, $v_{i}$

## Sprzężenie w przód
**Sprzężenie w przód** (ang. *feedforward*) to architektura, w której sygnał przepływa jednokierunkowo: od warstwy wejściowej, przez warstwy ukryte, aż do wyjściowej, bez tworzenia pętli sprzężenia zwrotnego



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
$$\mathbf{v}=[v_{1}, v_{2},\dots,v_{M}] \qquad \mathbf{z}=\begin{bmatrix} z_{1} \\ \vdots \\ z_{M} \end{bmatrix}$$

## Backpropagation
**Backpropagation** (propagacja wsteczna) BP to algorytm służący do efektywnego obliczania gradientu funkcji straty względem wag sieci, oparty na regule łańcuchowej różniczkowania. Umożliwia on aktualizację wag w procesie uczenia.


Niech $L(\mathbf{v})=\mathrm{MSE}(\mathbf{v})$. Pojedynczą wagę $v_{i}$ będziemy aktualizować za pomocą wzoru:

$$v_{i}\leftarrow v_{i}-\eta \frac{\partial L(v_{i})}{\partial v_{i}}$$

Co możemy rozpisać jako: 

$$v_{i}-\eta \frac{\partial L(v_{i})}{\partial v_{i}}=v_{i}-\eta\cdot\color{red}{\frac{\partial L(v_{i})}{\partial\hat{y}}}\color{black}{\cdot}\color{blue}{\frac{\partial \hat{y}}{\partial v_{i}}}\color{black}=v_{i}-\eta\cdot\color{red}\frac{2}{S}\sum_{s=1}^S (y^{(s)}-\hat{y}^{(s)})(-1)\color{black}\cdot  \color{blue}\Psi'\left( \sum_{m=1}^M v_{m}z_{m}+c \right)\cdot z_{i}$$

W zapisie macierzowym wyrazimy to jako:

$$\mathbf{v}\leftarrow \mathbf{v}-\eta\nabla_{\mathbf{v}} L=\mathbf{v}-\eta \begin{bmatrix}
 \frac{\partial L}{\partial v_{1}} & \frac{\partial L}{\partial v_{2}} & \dots &\frac{\partial L}{\partial v_{M}} & \frac{\partial L}{\partial c}
\end{bmatrix}=\mathbf{v}-\eta \frac{\partial L}{\partial \hat{y}} \begin{bmatrix}
 \frac{\partial \hat{y}}{\partial v_{1}} & \frac{\partial \hat{y}}{\partial v_{2}} & \dots &\frac{\partial \hat{y}}{\partial v_{M}} & \frac{\partial \hat{y}}{\partial c}
\end{bmatrix}$$

