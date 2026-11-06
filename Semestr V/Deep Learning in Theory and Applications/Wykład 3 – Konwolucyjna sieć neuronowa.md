## Konwolucyjna sieć neuronowa
**Konwolucyjna sieć neuronowa** (ang. *convolutional neural network*) CNN to rodzaj sieci neuronowej, która wykorzystuje operację konwolucji do automatycznego wykrywania i przetwarzania charakterystycznych cech danych.

Sieci CNN są szczególnie skuteczne w analizie danych mających strukturę czasową lub przestrzenną, takich jak obrazy, filmy, sygnały dźwiękowe czy tekst. Sieci CNN potrafią uczyć się lokalnych wzorców, z których następnie tworzą bardziej złożone struktury.

## Proces filtrowania
**Konwolucja** jest operacją, w której przepuszczamy ciąg danych wejściowych $\mathbf{x}$ przez pewien filtr $\mathbf{w}$. Przykładowo przyjmijmy dane wejściowe $\mathbf{x}=(0,0,1,1,1,0,1,0,0,0)$ oraz filtr $\color{magenta}\mathbf{w}=(-1,1,-1)$.

$$\begin{matrix}
(0,&0,&1,&1,&1, &0, &1, &0,&0,&0)\\
\cdot &\cdot&\cdot\\
\color{magenta}(-1,&\color{magenta}1,&\color{magenta}-1)\\
 ||&||&||\\
 \color{red}0&\color{red}0&\color{red}-1
\end{matrix}$$

Przepuszczamy pierwszą trójkę danych wejściowych przez filtr, mnożąc je przez odpowiadające im współczynniki. Pozyskane w ten sposób iloczyny sumujemy, a ich sumę wstawiamy na pierwszym miejscu w wektorze konwolucji $\mathbf{c}$.

$$\color{red}c_{1}=0+0-1=-1$$

Następnie przesuwamy filtr o jedną pozycję i powtarzamy całą operację:

$$\begin{matrix}
(0,&0,&1,&1,&1, &0, &1, &0,&0,&0)\\
&\cdot &\cdot&\cdot\\
\rightarrow&\color{magenta}(-1,&\color{magenta}1,&\color{magenta}-1)\\
 &||&||&||\\
& \color{blue}0&\color{blue}1&\color{blue}-1
\end{matrix}$$

$$\color{blue}c_{2}=0+1-1=0$$

Po zakończeniu wszystkich iteracji otrzymujemy pełny wektor konwolucji:

$$\mathbf{c}=(\color{red}c_{1}\color{black},\color{blue}c_{2}\color{black},c_{3},\dots,c_{8})=(\color{red}-1\color{black},\color{blue}0\color{black},-1,0,-2,1,-1,0)$$

Na koniec wektor konwolucji przepuszczamy przez funkcję aktywacji $\Psi$. Jeżeli $\Psi=\mathrm{ReLU}$, to:

$$\mathbf{y}=\mathrm{ReLU}(-1,0,-1,0,-2,1,-1,0)=(0,0,0,0,0,1,0,0)$$

## Konwolucja
W ujęciu matematycznym konwolucję dokonujemy na dowolnym wektorze $\mathbf{x}=(x_{1},\dots,x_{N})$ oraz filtrze $\mathbf{w}=(w_{1},w_{2},\dots,w_{K})$. Każdą współrzędną wektora $\mathbf{c}$ możemy zapisać jako:

$$c_{i}= \sum _{k=1}^K w_{k}x_{i+k-\left\lceil  \frac{K}{2} \right\rceil} $$

A po zastosowaniu funkcji aktywacji $\Psi$ otrzymujemy:

$$y_{i}=\Psi\left( \sum_{k=1}^K w_{k}x_{i+k-\left\lceil  \frac{K}{2} \right\rceil} \right)$$

Konwolucję wektora $\mathbf{x}$ przez filtr $\mathbf{w}$ oznaczamy jako:

$$\mathbf{c}=\mathbf{x}\ast\mathbf{w}$$

Konwolucję możemy traktować jak sieć złożoną z pojedynczego neuronu zamkniętego w pętli `for`.

Jak możemy zauważyć, w każdej konwolucji, otrzymany wektor wyjściowy jest mniejszy względem wektora wejściowego. Aby zapobiec temu problemowi możemy zastosować tzw. *padding*, który polega na dodaniu na początku i na końcu wektora wejściowego wartość $0$.

Przy konwolucji możemy także zaimplementować zmienną *stride* $S$. Odpowiada ona za to, co ile współrzędnych przesuwa się filtr przy każdym ruchu. W standardowej konwolucji $S=1$.

## Konwolucja dwuwymiarowa
Pojęcie konwolucji możemy uogólnić na macierze. Mamy wtedy do czynienia z macierzą danych wejściowych $\mathbf{X}=[x_{ij}]_{M\times N}$ oraz macierzą filtra $\mathbf{W}=[w_{ij}]_{K\times L}$. Macierz filtra przesuwamy po obu współrzędnych, pokrywając całą powierzchnię macierzy $\mathbf{X}$.

Przykładowo dla macierzy $\mathbf{X}$ $3\times{3}$ i filtra $\color{magenta}\mathbf{W}$ $2\times{2}$ otrzymujemy następujące ułożenia filtra: 
$$\begin{bmatrix}
x_{1,1}^{\color{magenta}\cdot w_{1,1}} &x_{1,2}^{\color{magenta}\cdot w_{1,2}}&x_{1,3}\\
x_{2,1}^{\color{magenta}{\cdot w_{2,1}}}&x_{2,2}^{\color{magenta}\cdot w_{2,2}}&x_{2,3}\\
x_{3,1}&x_{3,2}&x_{3,3}
\end{bmatrix}\quad

 \begin{bmatrix}
x_{1,1} &x_{1,2}^{\color{magenta}\cdot w_{1,1}}&x_{1,3}^{\color{magenta}\cdot w_{1,2}}\\
x_{2,1}&x_{2,2}^{\color{magenta}\cdot w_{2,1}}&x_{2,3}^{\color{magenta}\cdot{w_{2,2}}}\\
x_{3,1}&x_{3,2}&x_{3,3}
\end{bmatrix}\quad

\begin{bmatrix}
x_{1,1} &x_{1,2}&x_{1,3}\\
x_{2,1}^{\color{magenta}\cdot w_{1,1}}&x_{2,2}^{\color{magenta}\cdot w_{1,2}}&x_{2,3}\\
x_{3,1}^{\color{magenta}{⋅w_{2,1}}}&x_{3,2}^{\color{magenta} \cdot w_{2,2}}&x_{3,3}
\end{bmatrix}

\quad
\begin{bmatrix}
x_{1,1} &x_{1,2}&x_{1,3}\\
x_{2,1}&x_{2,2}^{\color{magenta}\cdot w_{1,1}}&x_{2,3}^{\color{magenta}\cdot w_{1,2}}\\
x_{3,1}&x_{3,2}^{\color{magenta} \cdot w_{2,1}}&x_{3,3}^{\color{magenta}\cdot w_{2,2}}
\end{bmatrix}$$

W ten sposób otrzymujemy macierz konwolucji:

$$\mathbf{C}=\begin{bmatrix}
x_{1,1}w_{1,1}+x_{1,2}w_{1,2}+x_{2,1}w_{2,1}+x_{2,2}w_{2,2} & x_{1,2}w_{1,1}+x_{1,3}w_{1,2}+x_{2,2}w_{2,1}+x_{2,3}w_{2,2} \\ x_{2,1}w_{1,1}+x_{2,2}w_{1,2}+x_{3,1}w_{2,1}+x_{3,2}w_{2,2} &
x_{2,2}w_{1,1}+x_{2,3}w_{1,2}+x_{3,2}w_{2,1}+x_{3,3}w_{2,2}
\end{bmatrix}$$

W konwolucji dwuwymiarowej stosujemy tzw. operację **poolingu**. Pooling polega na zmniejszaniu wymiarów macierzy konwolucji (*downsampling*). Przy poolingu musimy określić jego wymiary. Przykładowo dla poolingu $1\times{2}$ będziemy łączyć ze sobą po dwie współrzędne z jednego wiersza. Możemy wyróżnić wiele różnych operatorów, m.in.:
- **Max pooling**

$$\mathrm{MaxPooling}_{1\times{2}}\left( \begin{bmatrix}
\color{blue}c_{1,1}&\color{blue}c_{1,2}\\
\color{red}c_{2,1}&\color{red}c_{2,2}
\end{bmatrix}\right)=\begin{bmatrix}
\color{blue}\max\{c_{1,1},c_{1,2}\}\\
\color{red}\max\{c_{2,1},c_{2,2}\}
\end{bmatrix}$$

- **Average pooling**

$$\mathrm{AvgPooling}_{1\times{2}}\left( \begin{bmatrix}
\color{blue}c_{1,1}&\color{blue}c_{1,2}\\
\color{red}c_{2,1}&\color{red}c_{2,2}
\end{bmatrix}\right)=\begin{bmatrix}
\color{blue}\frac{{c_{1,1}+c_{1,2}}}{2}\\
\color{red}\frac{{c_{2,1}+c_{2,2}}}{2}
\end{bmatrix}$$

Innym popularnym rodzajem poolingu jest $\mathrm{MedPooling}_{m\times n}$, w którym wynikiem mediana wszystkich $m\times n$ wartości.

>[!example] Konwolucja dwuwymiarowa
>0. **Dane**
>Macierz wartości $\mathbf{X}=\begin{bmatrix}1&2&-1\\2&1&3\\-2 &0&0\end{bmatrix}$
>Macierz filtra $\mathbf{W}=\begin{bmatrix}1&-1\\-1&2\end{bmatrix}$
>Max pooling $2\times{1}$
>Funkcja aktywacji $\Psi=\mathrm{ReLU}$
>
>
>1. **Wyznaczamy konwolucję macierzy**
>   
>  $$\mathbf{X}\ast\color{magenta}\mathbf{W}\color{black}=\begin{bmatrix} 1&2&-1\\2&1&3\\-2 &0&0 \end{bmatrix}\ast\color{magenta}\begin{bmatrix} 1&-1\\-1&2 \end{bmatrix}\color{black}=$$
>  
>  $$=\begin{bmatrix} 1\cdot \color{magenta}{1}\color{black}+2\cdot \color{magenta}(-1)\color{black}+ 2 \cdot \color{magenta}-1 \color{black}+ 1 \cdot \color{magenta}2 \color{black} & 2\cdot \color{magenta}1\color{black}+(-1)\cdot \color{magenta}(-1)\color{black}+1\cdot \color{magenta}(-1)\color{black}+3\cdot \color{magenta}2\color{black} \\ 2\cdot \color{magenta}1\color{black}+1\cdot \color{magenta}(-1)\color{black}+(-2)\cdot \color{magenta}(-1)\color{black}+0\cdot \color{magenta}2\color{black} & 1\cdot \color{magenta}1\color{black}+3\cdot \color{magenta}(-1)\color{black}+0\cdot \color{magenta}(-1)\color{black}+0\cdot \color{magenta}2\color{black}\end{bmatrix}=$$
>  
>  $$=\begin{bmatrix}  1-2-2+2 & 2+1-1+6 \\ 2-1+2 & 1-3 \end{bmatrix}=\begin{bmatrix} -1 & 8 \\ 3 & -2 \end{bmatrix}$$
>  
>  2. **Dokonujemy max poolingu**
>    
>  $$\mathrm{MaxPooling}_{2\times{1}}\left( \begin{bmatrix} \color{blue}-1 & \color{red}8 \\ \color{blue}3 & \color{red}-2  \end{bmatrix} \right)=\begin{bmatrix} \max\{\color{blue}-1, 3 \color{ black}\} & \max\{\color{red} 8,-2 \color{black}\} \end{bmatrix}=\begin{bmatrix} \color{blue}3 & \color{red}8  \end{bmatrix}$$
>  
>  3. **Na złączonym wektorze aplikujemy funkcję aktywacji**
>    
>   $$\mathrm{ReLU}\left( \begin{bmatrix} 3 & 8  \end{bmatrix} \right)=\begin{bmatrix} \mathrm{ReLU(3)} & \mathrm{ReLU}(8)  \end{bmatrix}=\begin{bmatrix} 3 & 8 \end{bmatrix}$$ 

## Konwolucje wyższych wymiarów
Konwolucję możemy uogólnić na dowolną liczbę wymiarów. Zazwyczaj przy trzech wymiarach dane wejściowe traktujemy dwuwymiarowo – dzielimy wtedy tensor wejściowy $\boldsymbol{\mathcal{X}}\in\mathbb{R}^{M\times N\times O}$ na $O$ macierzy o wymiarach $M\times N$.

$$\boldsymbol{\mathcal{X}}=(\mathbf{X}_{1},\dots,\mathbf{X}_{O})$$

Każdą taką macierz $\mathbf{X}_{i}$ traktujemy indywidualnie i przepuszczamy przez filtry $\mathbf{W}_{i}$. Takie postępowanie występuje m.in. w przetwarzaniu kolorowych obrazów, gdzie mamy do czynienia z osobnymi macierzami dla każdego koloru: $\boldsymbol{\mathcal{X}}=(\mathbf{R},\mathbf{G},\mathbf{B})$. Macierze $\mathbf{R},\mathbf{G},\mathbf{B}$ mają takie same wymiary jak obraz wejściowy $\boldsymbol{\mathcal{X}}$.

$$\mathbf{C}=\mathbf{R}\ast\mathbf{W}_{R}+\mathbf{G}\ast\mathbf{W}_{G}+\mathbf{B}\ast\mathbf{W}_{B}$$

Innym, chociaż rzadszym podejściem, jest traktowanie całego tensora jako jednego obiektu, wtedy mamy do czynienia z tensorem danych wejściowych $\boldsymbol{\mathcal{X}}$ oraz tensorem filtra $\boldsymbol{\mathcal{W}}$ – to podejście działa dla tensorów dowolnego rzędu. Wykonujemy wtedy operację konwolucji:

$$\boldsymbol{\mathcal{C}}=\boldsymbol{\mathcal{X}}\ast\boldsymbol{\mathcal{W}}$$

Wraz ze wzrostem liczby wymiarów, wzdłuż których wykonywana jest konwolucja, brak paddingu może prowadzić do coraz większej względnej redukcji liczby elementów tensora wyjściowego.

## Sieć neuronowa z konwolucją
Mechanizm konwolucji możemy zaimplementować w sieci neuronowej, tak jak w poniższym przykładzie:
![[Pasted image 20261105213933.png|448]]
Aby wykonać feedforward na powyższej sieci zaczniemy od neuronu $l$:

$$l=\Psi(x_{1}v_{1})$$

Następnie obliczamy wartość neuronu $h$:

$$h=\Psi(x_{1}v_{2}+l)$$

Możemy teraz przejść do konwolucji:

$$\mathbf{z}=\begin{bmatrix}
x_{1}\\x_{2}\\x_{3}\\x_{4}\\x_{5}
\end{bmatrix}\ast \begin{bmatrix}
w_{1}\\w_{2}\\w_{3}
\end{bmatrix}= \begin{bmatrix}
x_{1}w_{1}+x_{2}w_{2}+x_{3}w_{3}\\
x_{2}w_{1}+x_{3}w_{2}+x_{4}w_{3} \\
x_{3}w_{1}+x_{4}w_{2}+x_{5}w_{3}
\end{bmatrix}$$

Na koniec obliczamy neuron wyjściowy:

$$\hat{y}_{1}=\Phi\left(\mathbf{z}^T\begin{bmatrix}
u_{1}\\u_{2}\\u_{_{3}}
\end{bmatrix} + hu_{4}\right)=\Phi(z_{1}u_{1}+z_{2}u_{2}+z_{3}u_{3}+hu_{4})$$
