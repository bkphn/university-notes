
## Konwolucje wyższych wymiarów
konwolucja na tensorach też działa. Zazwyczaj traktujemy je dwuwymiarowo i przechodzimy po kolei, ale można tworzyć filtry, które są tensorami. W takim wypadku z każdym kolejnym wymiarem tracimy coraz więcej informacji przez zmniejszanie się współrzędnych.

## Sieć neuronowa z konwolucją
v ukryta warstwa, u warstwa wyjściowa, w warstwa wejścowa, nie ma bias, konwolucja jest 3szeroka i ma 1opoznienia (stride) i linear activation

$\mathbf{x}=(x_{1},x_{2},x_{3},x_{4},x_{5})$
$\mathbf{f}=(f_{1},f_{2},f_{3})$
$\mathbf{c}=(w_{1}x_{1}+w_{2}x_{2}+w_{3}x_{3},\quad w_{1}x_{2}+w_{2}x_{3}+w_{3}x_{4},\quad w_{1}x_{3}+w_{2}x_{4}+w_{3}x_{5})$

$w=\Psi(x_{1})$
$v=\Psi\left( w_{1}l_{1}+x_{1} \right)$

$u_{1}=\Phi(v_{1}h_{1}+\mathbf{z}\mathbf{c})$



$\hat{y}=\Phi \Bigg(\Psi\bigg(\Psi\Big(  x^t\Big)l^t+x^t\bigg)h^t+\mathbf{z}^t(w_{1}x^{t}+w_{2}x^{t-1}+w_{3}x^{t-2},w_{1}x^{t-1}+w_{2}x^{t-2}+w_{3}x^{t-3}, w_{1}x^{t-2}+w_{2}x^{t-3}+w_{3}x^{t-4}\Bigg)$
