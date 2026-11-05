## Konwolucyjna sieć neuronowa
**Konwolucyjna sieć neuronowa** (ang. *convolutional neural network*) CCN to rodzaj sieci neuronowej, która wykorzystuje operację konwolucji do automatycznego wykrywania i przetwarzania charakterystycznych cech danych.

Sieci CNN są szczególnie skuteczne w analizie danych mających strukturę czasową lub przestrzenną, takich jak obrazy, filmy, sygnały dźwiękowe czy tekst. Sieci CNN potrafią uczyć się lokalnych wzorców, z których następnie tworzą bardziej złożone struktury.

## Proces filtrowania
**Konwolucja** jest operacją, w której przepuszczamy ciąg danych wejściowych $\mathbf{x}$ przez pewien filtr $\mathbf{w}$. Przykładowo przyjmijmy dane wejściowe $\mathbf{x}=(0,0,1,1,1,0,1,0,0,0)$ oraz filtr $\color{magenta}\mathbf{w}=(-1,1,-1)$.

$$\begin{matrix}
(0,&0,&1,&1,&1, &0, &1, &0,&0,&0)\\
\cdot &\cdot&\cdot\\
\color{magenta}(-1,&\color{magenta}1,&\color{magenta}-1)\\
 ||&||&||\\
 0&0&-1
\end{matrix}$$

Przepuszczamy pierwszą trójkę danych wejściowych przez filtr, mnożąc je przez odpowiadające im współczynniki. Pozyskane w ten sposób iloczyny sumujemy, a ich sumę wstawiamy na pierwszym miejscu w wektorze konwolucji $\mathbf{c}$.

$$c_{1}=0+0-1=-1$$

Następnie przesuwamy filtr o jedną pozycję i powtarzamy całą operację:

$$\begin{matrix}
(0,&0,&1,&1,&1, &0, &1, &0,&0,&0)\\
&\cdot &\cdot&\cdot\\
\rightarrow&\color{magenta}(-1,&\color{magenta}1,&\color{magenta}-1)\\
 &||&||&||\\
& 0&1&-1
\end{matrix}$$

$$c_{2}=0+1-1=0$$

Po zakończeniu wszystkich iteracji otrzymujemy pełny wektor konwolucji:

$$\mathbf{c}=(c_{1},c_{2},\dots,c_{8})=(-1,0,-1,0,-2,1,-1,0)$$

Na koniec wektor konwolucji przepuszczamy przez funkcję aktywującą $\psi$. Jeżeli $\psi=\mathrm{ReLU}$, to:

$$\mathbf{y}=\mathrm{ReLU}(-1,0,-1,0,-2,1,-1,0)=(0,0,0,0,0,1,0,0)$$

## Konwolucja
W ujęciu matematycznym konwolucję dokonujemy na dowolnym wektorze $\mathbf{x}=(x_{1},\dots,x_{N})$ oraz filtrze $\mathbf{w}=(w_{1},w_{2},\dots,w_{K})$. Każdą współrzędną wektora $\mathbf{c}$ możemy zapisać jako:

$$c_{i}= \sum _{k=1}^K w_{k}x_{i+k-\left\lceil  \frac{k}{2} \right\rceil} $$

A po zastosowaniu funkcji aktywacji $\Psi$ otrzymujemy:

$$y_{i}=\Psi\left( \sum_{k=1}^K w_{k}x_{i+k-\left\lceil  \frac{k}{2} \right\rceil} \right)$$

Konwolucję wektora $\mathbf{x}$ przez filtr $\mathbf{w}$ oznaczamy jako:

$$\mathbf{y}=\mathbf{x}\ast\mathbf{w}$$

Konwolucję możemy traktować jak sieć złożoną z pojedynczego neuronu zamkniętego w pętli `for`.


---

$y_{i}=\Psi\left( \sum_{k=1}^K w_{k}x_{i+k-\lceil\frac{k}{2}\rceil} \right)$
---
padding dodajemy zera na krańcach, jeżeli nie chcemy my nam malały wektory konwolucji

---
uogólnienie konwolucji na macierze, wtedy filtr też jest kwadratem

pooling operation (np, maxpooling, avgpooling, med.pooling) wyciągamy macierz Conv po przefiltrowaniu obrazu. Funkcja pooling jest nieuczalna, wybieramy pooling size (1,2)np. i wybieramy wektory 1×2 po kolei, i np. dla maxpooling bierzemy max z wspolrzednych wybranych wektorów i tworzymy nowy wektor/macierz pomiajajac te niepasujace dane, są po prostu stracone.

jezeli pooling nei pasuje do macierzy conv to 

---

konwolucja na tensorach też działa. Zazwyczaj traktujemy je dwuwymiarowo i przechodzimy po kolei, ale można tworzyć filtry, które są tensorami. W takim wypadku z każdym kolejnym wymiarem tracimy coraz więcej informacji przez zmniejszanie się współrzędnych.

---

v ukryta warstwa, u warstwa wyjściowa, w warstwa wejścowa, nie ma bias, konwolucja jest 3szeroka i ma 1opoznienia (stride) i linear activation

---
*residual connection*
*jeżeli mamy dwa wyjścia lub więcej, to przy BP musimy sumować błędy dla każdego z wyjść (sumować, jeżeli w funkcji straty jest suma, w p.p. wykonujemy poprawną operację)*

---

$\mathbf{x}=(x_{1},x_{2},x_{3},x_{4},x_{5})$
$\mathbf{f}=(f_{1},f_{2},f_{3})$
$\mathbf{c}=(w_{1}x_{1}+w_{2}x_{2}+w_{3}x_{3},\quad w_{1}x_{2}+w_{2}x_{3}+w_{3}x_{4},\quad w_{1}x_{3}+w_{2}x_{4}+w_{3}x_{5})$

$w=\Psi(x_{1})$
$v=\Psi\left( w_{1}l_{1}+x_{1} \right)$

$u_{1}=\Phi(v_{1}h_{1}+\mathbf{z}\mathbf{c})$



$\hat{y}=\Phi \Bigg(\Psi\bigg(\Psi\Big(  x^t\Big)l^t+x^t\bigg)h^t+\mathbf{z}^t(w_{1}x^{t}+w_{2}x^{t-1}+w_{3}x^{t-2},w_{1}x^{t-1}+w_{2}x^{t-2}+w_{3}x^{t-3}, w_{1}x^{t-2}+w_{2}x^{t-3}+w_{3}x^{t-4}\Bigg)$
	