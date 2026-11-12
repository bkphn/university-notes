## Szereg czasowy
**Danymi czasowymi** nazywamy dane, których jedną z charakterystyk jest czas obserwacji. Dane czasowe możemy ułożyć w **szereg czasowy**, czyli ciąg obserwacji uporządkowanych chronologicznie, zgodnie z czasem ich wystąpienia:

$$x^{(0)},x^{(1)},\ldots,x^{(t-1)},x^{(t)}$$

Indeks czasu oznaczamy górnym indeksem $^{(t)}$, gdzie $t$ pochodzi od angielskiego *time*. Pojedyncza obserwacja $x^{(t)}$ może być skalarem lub wektorem cech. Indeks $(t)$ oznacza pozycję obserwacji w sekwencji.

## Neuron rekurencyjny
Do przetwarzania danych sekwencyjnych często wykorzystuje się **rekurencyjne sieci neuronowe** (ang. *Recurrent Neural Networks*) RNN.

**Neuronem rekurencyjnym** nazywamy neuron, którego wyjście z poprzedniego kroku czasowego stanowi jedno z wejść w bieżącym kroku. Takie połączenie nazywamy **połączeniem rekurencyjnym**, oznaczamy je symbolem $\Delta$, który reprezentuje opóźnienie o jeden krok czasowy. Wyjście neuronu, nazywane również jego stanem ukrytym, oznaczamy zwyczajowo literą $h$.

![[Pasted image 20261112201446.png|349]]
W każdym kolejnym kroku czasowym neuron przetwarza bieżące dane wejściowe oraz stan pochodzący z poprzedniego kroku. Równanie pojedynczego neuronu rekurencyjnego możemy przedstawić jako:

$$\boxed{h^{(t)}=\Psi(w_{1}x_{1}^{(t)}+\dots+w_{N}x_{N}^{(t)}+w_{r}h^{(t-1)}+b_{i})}$$

## Unfolding
W przypadku sieci rekurencyjnych stosujemy algorytm **Backpropagation Through Time** BPTT, będący zastosowaniem standardowej propagacji wstecznej BP do sieci rozwiniętej w czasie.

W przeciwieństwie do zwykłych sieci jednokierunkowych, stan neuronu rekurencyjnego zależy nie tylko od bieżących danych wejściowych, ale również od stanu z poprzedniego kroku. Oznacza to, że podczas obliczania gradientu musimy uwzględnić zależności między kolejnymi stanami ukrytymi.

W BPTT zaczynamy od operacji **rozwinięcia** (ang. *unfolding*), w której połączenie rekurencyjne zastępujemy sekwencją połączonych ze sobą kopii tego samego neuronu, odpowiadających kolejnym krokom czasowym. Każda kopia otrzymuje dane wejściowe z odpowiedniej chwili oraz stan poprzedniej kopii.

Wszystkie kopie współdzielą te same wagi i biasy. Oznacza to, że rozwinięcie nie zwiększa liczby trenowanych parametrów modelu.
![[Pasted image 20261112202102.png]]
Operację powtarzamy aż do wybranego przez nas kroku $k$, w faktycznych implementacjach zazwyczaj kilkaset razy. Po rozwinięciu otrzymujemy acykliczny graf obliczeniowy, na którym możemy zastosować standardowy algorytm BP.

Wyróżniamy dwa podejścia:
- **Full BPTT**: propagację gradientu przez całą rozpatrywaną sekwencję, aż do wartości $h^{(0)}$.
- **Truncated BPTT** — propagację gradientu jedynie przez ograniczoną liczbę kroków czasowych do wybranej przez nas wartości $h^{(k)}$.

## Backpropagation Through Time
BPTT działa analogicznie do zwykłego BP, z tą różnicą, że gradienty propagowane są również przez kolejne kroki czasowe rozwiniętej sieci. Rozpoczynamy od wybrania funkcji straty.

Dla danych sekwencyjnych funkcja straty może uwzględniać zarówno różne próbki, jak i różne kroki czasowe. Dla jednej próbki $S=1$, zawierającej $T$ obserwacji funkcję MSE zapiszemy następująco:

$$\mathcal{L}=\frac{1}{T}\sum_{t=1}^T (y^{(t)}-h^{(t)})^2$$

Aktualizacja pojedynczej wagi $w_{i}$ wygląda następująco:

$$w_{i}\leftarrow w_{i}-\eta \frac{\partial\mathcal{L}}{\partial w_{i}}$$

Ponieważ te same wagi wykorzystywane są w każdym kroku czasowym, ich gradient musi uwzględniać wkłady pochodzące ze wszystkich rozpatrywanych kroków. Przykładowo gradient $\frac{\partial{ \mathcal{L} }}{\partial{ w_{r}  }}$ dla trzech neuronów, dwóch wejść $x_{1}^{(t)}, x_{2}^{(t)}$ oraz braku biasu, po unfoldingu wygląda następująco:

$$\frac{\partial{ \mathcal{L} }}{\partial{ w_{r}  }}=\frac{\partial{ \mathcal{L} }}{\partial{ h^{(t)} }}\left( \frac{\partial{ h^{(t)} }}{\partial{  w_{r} }}  +\frac{\partial{ h^{(t)} }}{\partial{  h^{(t-1)} }} \left( {\frac{\partial{ h^{(t-1)} }}{\partial{ w_{r}  }}} + \frac{\partial{ h^{(t-1)} }}{\partial{ h^{(t-2)}  }} \left( {\frac{\partial{ h^{(t-2)} }}{\partial{ w_{r} }}} \right) \right)\right)$$

Kolejne gradienty obliczamy klasycznie:

$$\frac{\partial{ \mathcal{L} }}{\partial{ h^{(t)}  }}=\frac{2}{T} \sum_{t=1}^T (y^{(t)}-h^{(t)})(-1)$$

1. Neuron pierwszy $(t)$

$$\frac{\partial{ \mathcal{h^{(t)}} }}{\partial{ w_{r} }}=\Psi'(w_{1}x_{1}^{(t)}+w_{2}x_{2}^{(t)}+w_{r}h^{(t-1)})\cdot h^{(t-1)}$$

$$\frac{\partial{ h^{(t)} }}{\partial{  h^{(t-1)} }}=\Psi'(w_{1}x_{1}^{(t)}+w_{2}x_{2}^{(t)}+w_{r}h^{(t-1)})\cdot w_{r}$$

2. Neuron drugi $(t-1)$

$$\frac{\partial{ h^{(t-1)} }}{\partial{ w_{r}  }}=\Psi'(w_{1}x_{1}^{(t-1)}+w_{2}x_{2}^{(t-1)}+w_{r}h^{(t-2)})\cdot h^{(t-2)}$$

$$\frac{\partial{ h^{(t-1)} }}{\partial{ h^{(t-2)}  }}=\Psi'(w_{1}x_{1}^{(t-1)}+w_{2}x_{2}^{(t-1)}+w_{r}h^{(t-2)})\cdot w_{r}$$

3. Neuron trzeci $(t-2)$

$$\frac{\partial{ h^{(t-2)} }}{\partial{  w_{r} }}=\Psi'(w_{1}x_{1}^{(t-2)}+w_{2}x_{2}^{(t-2)}+w_{r}h^{(t-3)})\cdot h^{(t-3)}$$

Często pochodną funkcji aktywacji $\Psi'(w_{1}x_{1}^{(t)}+w_{2}x_{2}^{(t)}+\dots+w_{N}x_{N}^{(t)}+w_{r}h^{(t-1)})$ będziemy w skrócie zapisywać jako $\Psi'(\cdot)\Big|_{t}$. Podstawiając pod $t$ dowolną inną zmienną, zmieniamy górne indeksy przy argumentach. W uogólnieniu:

$$\boxed{\Psi'(\cdot)\Big|_{i}=\Psi'(w_{1}x_{1}^{(i)}+\dots+w_{N}x_{N}^{(i)}+w_{r}h^{(i-1)})}$$

## Zanikanie gradientu
Możemy zauważyć, że w gradientach dla każdego z neuronów po unfoldingu pojawia się waga $w_{r}$. Wiąże się to z problemem **zanikania gradientu** (ang. *gradient vanishing*). Jeżeli $-1<w_{r}<1$ i wykonujemy $K$ unfoldingów, to możemy zauważyć, że $\lim_{K\rightarrow\infty} w_{r}^K=0$. W praktyce wykonując setki unfoldingów dochodzi do sytuacji, gdy całą wartość mnożymy przez $w_{r}^K\approx{0}$.