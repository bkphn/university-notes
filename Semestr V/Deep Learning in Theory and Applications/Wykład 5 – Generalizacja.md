## Przeuczenie
**Przeuczeniem** (ang. *overfitting*) to zjawisko w uczeniu maszynowym, w którym model zbyt mocno dopasowuje się do danych treningowych, przez co osiąga bardzo dobre wyniki na zbiorze treningowym, ale znacznie gorsze na nowych, wcześniej niewidzianych danych.

Innymi słowy, model zamiast nauczyć się ogólnych zależności występujących w danych, zaczyna uczyć się danych na pamięć.

## Walidacja krzyżowa
**Cross-validation**
Należy pamiętać o resetowanie parametrów modelu przy cross-validation, bo sie o tym zapomina.

*leave one scenario out*

Jeżeli c

## Dropout layer

raczej ponizej $p<=25\%$ w praktyce
.

## Early stopping

patience parameter

ancelot, rom albo ram. przekazywana z rom do ram w podobny sposob jak dzila streaming. 

nie używać w gradient vanishing i gradient exploding, a w generelizacji


L1 + linear = lasso

$$\mathcal{L}=\text{loss function}+ \frac{\lambda}{m}\sum_{j=1}^n |\theta_{j}|$$
*penalize*
L2 + linear = ridge:
$$\mathcal{L}(\mathbf{W})=\text{zwykły loss function np. MSE}+\frac{\lambda}{2m}\sum_{j=1}^n \theta_{j}^2$$

zwykle loss optymalizuje testy, a θj2 optymalizuje parametry i pilnuje, by nie byly zbyt duze. 

jeżeli θj^n jest wektorem to uzywamy normy ‖‖


Elastic net = L1 + L2

$$\mathcal{L}= \frac{1}{2m} \sum_{i=1}^m (h_{\theta}(x^{(i)})-y^{(i)})^2+  \lambda_{1}\sum_{j=1}^n |\theta_{j}| + \lambda_{2} \sum_{j=1}^n \theta_{j}^2 $$

## Clipping
jak ursona wagi za bardzo to zamiast l1 czy l2 mozna po prostu uzyc clippingu, czyli jezeli sa zbyt duze to je sztucznie zmniejszamy pod pewien thresholdx.

## Iteracja a epoka
epoka jak wszystko zrobie, a iteracja jak przeleci model do konca

## A single sample / iterative
bardzo noisy i bardzo czasochlonne, ale nei obciaza tak pamieciowo

## Batch Learning (Gradient Descent)


## Mini-Batch
Jedna epoka to wszystkie itracje czyli jeden batch to jedna iteracja, a a wszystkie batche to to epoch (epik?).s

$B$ wybieramy jako potęgę liczby dwa, bo GPU sobie radzi najlepiej z takimi,

## Long-short term memory
LSTM, przed LLMami can i help you dzialalo na bazie LSTM kiedys. LSTM minimalizuje problemy z gradient descent.

LSTM units w każdej warstwie jest ich dużo, to jest taki neuron zbiór neuronów.

$C_{t-1}\rightarrow \times →_{\alpha_{t-1}} →C_{t}$
zapomianym część wspomnień, a rezta przechodzi dalej. Tworzymy nowe wspomnienie w neuronach 1,2. Odpowiadaja one za short time memory. Main output tworzy neuron 3. (0, 1, 2, 3 to biasy)

