## Przeuczenie
**Przeuczeniem** (ang. *overfitting*) to zjawisko w uczeniu maszynowym, w którym model zbyt mocno dopasowuje się do danych treningowych, przez co osiąga bardzo dobre wyniki na zbiorze treningowym, ale znacznie gorsze na nowych, wcześniej niewidzianych danych.

Innymi słowy, model zamiast nauczyć się ogólnych zależności występujących w danych, zaczyna uczyć się danych na pamięć.

## Walidacja krzyżowa
**Walidacja krzyżowa** (ang. *cross-validation*) CV to metoda oceny modeli uczenia maszynowego, która polega na wielokrotnym trenowaniu i ocenianiu modelu na różnych podzbiorach dostępnych danych. Jej głównym celem jest oszacowanie, jak dobrze model będzie generalizował na nowych, wcześniej niewidzianych danych.

W klasycznym podejściu dzielimy zbiór danych $\mathcal{D}$ na $\mathcal{D}_{\text{train}}$ oraz $\mathcal{D}_{\text{test}}$. W walidacji dodajemy jeszcze jeden zbiór walidacyjny $\mathcal{D}_{\text{val}}$, który służy do testowania parametrów. W walidacyji krzyżowej $K$*-Fold Cross-Validation* dzielimy zbiór $\mathcal{D}$ na $K$ elementów:

$$\mathcal{D}=D_{1}\cup D_{2} \cup \dots \cup D_{K}$$

Następnie przeprowadzamy $K$ iteracji, w których trenujemy model na pozostałych $K-1$ podzbiorach, w iteracji $k\in\{1,\dots,K\}$ definiujemy:

$$\mathcal{D}_{\text{train}}^{(k)}=\mathcal{D}\setminus D_{k}, \qquad \mathcal{D}_{\text{val}}^{(k)}=D_{k}$$

Następnie trenujemy model $f$ optymalizując parametr $\theta$ dla każdej iteracji:

$$\theta_{k}= \arg\min_{\theta} \frac{1}{\mathcal{D}^{(k)}_{\text{train}}}\sum_{(x,y)\in \mathcal{D}_{\text{train}}^{(k)}} \mathcal{L}(f_{\theta}(x),y)$$


Należy pamiętać o resetowanie parametrów modelu przy cross-validation, bo sie o tym zapomina.

*leave one scenario out*

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

