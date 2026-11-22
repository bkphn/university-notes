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

i obliczamy błąd na zbiorze walidacyjnym:

$$E_{k}=\frac{1}{\mathcal{D}_{\text{val}}^{(k)}} \sum_{(x,y)\in{\mathcal{D}_{\text{val}}^{(k)}}} \mathcal{L}(f_{\theta_{k}}(x),y)$$

Ostatecznie estymator błędu cross-validation przyjmuje postać:

$$E_{\mathrm{CV}}=\frac{1}{K}\sum_{k=1}^K E_{k}$$

Jeżeli foldy mają różną liczebność, to zamiast tego stosujemy średnią ważoną.

Jednym z najczęstszych błędów przy implementacji walidacji krzyżowej jest zapominanie o resetowaniu parametrów modelu przy każdej kolejnej iteracji, dochodzi wtedy do wycieku danych.

**Leave-One-Scenario-Out** (LOSO) to metoda walidacji krzyżowej, w której model jest trenowany na danych pochodzących z kilku scenariuszy, a następnie oceniany na danych z jednego, całkowicie wykluczonego z treningu scenariusza. Głównym celem jest sprawdzenie, czy model potrafi generalizować na scenariusze, których nigdy wcześniej nie widział.

## Wartwa dropout
**Warstwa dropout** (ang. *dropout layer*) to technika regularyzacji stosowana w sieciach neuronowych, której głównej celem jest ograniczenie przeuczenia modelu. 

Polega na losowym wyłączaniu części neuronów podczas treningu, dzięki czemu model nie może nadmiernie polegać na pojedynczych neuronach i musi uczyć się bardziej odpornych reprezentacji danych.

Technika została szczegółowo opisana przez Nitishę Srivastavę i współautorów w pracy *Dropout: A Simple Way to Prevent Neural Networks from Overfitting*.

Dropout opiera się na parametrze $p$, który odpowiada za prawdopodobieństwo wyzerowania każdego z neuronów. Na końcu sieci podpinamy warstwę dropout, w której każdy neuron, z prawdopodobieństwem $p$ zostanie nadpisany liczbą $0$, następnie przy aktualizowaniu wag, niektóre wagi nie są po prostu aktualizowane, ponieważ ich gradient też wynosi zero.

W praktycznej implementacji przyjmujemy zazwyczaj $p\leq 25\%$.

## Wczesne zatrzymywanie
**Wczesne zatrzymywanie** (ang. *early stopping*) to technika regularyzacji stosowana podczas trenowania modeli. Polega na automatycznym zatrzymaniu treningu, gdy wyniki modelu na zbiorze walidacyjnym przestają się poprawiać.

![[Pasted image 20261122191713.png|365]]
Na powyższym przykładzie możemy zauważyć dwie krzywe. **Krzywą uczenia** i **krzywą walidacji**. Jak widać, *training loss* stale maleje, ale *validation loss* zaczyna rosnąć od epoki 17 – w związku z tym model zaczyna wykazywać oznaki przeuczenia (jest coraz lepszy na widzianych danych, lecz coraz gorzej mu idzie z tymi niewidzianymi).

Oczywiście pojedynczy wzrost *validation loss* nie oznacza od razu przeuczenia, stosujemy tutaj parametr cierpliwości `patience`. Wartość tego parametru mówi, ile epok bez poprawy *validation loss* wymagamy, aby zakończyć trening.

## Axolotl
**Axolotl** to framework służący do trenowania i dostrajania dużych modeli językowych (LLM). Jedną z jego funkcjonalności jest _Streaming Datasets_, czyli strumieniowe wczytywanie danych treningowych. Zamiast ładować cały zbiór danych do pamięci RAM, system pobiera kolejne fragmenty danych w miarę potrzeb.

## LASSO
**Regularyzacja L1** (ang. *L1 regularization*) to technika ograniczania złożoności modelu poprzez dodanie do funkcji straty kary zależnej od sumy wartości bezwzględnych jego parametrów. Funkcja straty kary L1 prezentuje się następująco:

$$L_{1}=\frac{\lambda}{m} \sum_{j=1}^n |\theta_{j}|$$

gdzie $\lambda$ jest współczynnikiem reguralyzacji, który określa siłę kary nakładanej na duże parametry.

Niech $\mathcal{L}_{0}$ będzie dowolną funkcją straty (np. MSE). Funkcję kosztu, będącą sumą funkcji straty i L1 nazywamy **LASSO** i definiujemy jako:

$$\mathcal{\mathcal{L}}=\mathcal{L}_{0}+L_{1}$$

## Ridge
**Reguralyzacja L2** (ang. *L2 regularization*) to technika ograniczania złożoności modelu poprzez dodanie do funkcji straty kary zależnej od sumy kwadratów jego parametrów. Funkcja straty kary L2 prezentuje się następująco:

$$L_{2}=\frac{\lambda}{2m}\sum_{j=1}^n \theta_{j}^2$$

gdzie $\lambda$ jest współczynnikiem reguralyzacji, który określa siłę kary nakładanej na duże parametry.

Niech $\mathcal{L}_{0}$ będzie dowolną funkcją straty (np. MSE). Funkcję kosztu, będącą sumą funkcji straty i L2 nazywamy **ridge regression** i definiujemy jako:

$$\mathcal{L}=\mathcal{L}_{0}+L_{2}$$

Funkcja $\mathcal{L}_{0}$ zajmuje się optymalizacją testów, a współczynnik $L_{2}$ pilnuje, by parametry nie były zbyt duże.

## Elastic net
**Elastic net** to funkcja kosztu łącząca zarówno L1, jak i L2. W ogólnym przypadku, dla funkcji straty $\mathcal{L}_{0}$ elastic net możemy wyrazić jako:

$$\boxed{\mathcal{L}=\mathcal{L}_{0}+L_{1}+L_{2}=\mathcal{L}_{0}+\frac{\lambda}{m}\sum_{j=1}^n |\theta_{j}|+\frac{\lambda}{2m}\sum_{j=1}^n\theta_{j}^2}$$

## Clipping
Nieco prostszą metodą ograniczania wielkości parametrów $\theta$ jest **clipping**. Polega on na tym, że jeżeli parametr $\theta$ osiągnie wartość wyższą niż ustalony próg (ang. *threshold*) to sztucznie zmniejszamy jego wartość nieco poniżej progu.

## Iteracja a epoka
W uczeniu maszynowym, szczególnie podczas trenowania sieci neuronowych, **epoka** (ang. *epoch*) i **iteracja** (ang. *iteration*) opisują dwa różne poziomy procesu treningowego:
- **Epoch**: jedno pełne przejście przez cały zbiór danych treningowych.
- **Iteration**: jeden krok optymalizacji, podczas którego model przetwarza porcję danych (_batch_) i aktualizuje swoje parametry.

W wielu modelach epoka i iteracja jest tożsama, ponieważ model w trakcie każdego kroku optymalizacji przetwarza cały zbiór treningowy.

## Stochastic Gradient Descent  
Załóżmy, że dysponujemy zbiorem treningowym $\mathcal{D}_{\text{train}}=\{(x_{1},y_{1}),\dots,(x_{N},y_{N})\}$. W podejściu *single-sample* podczas jednego kroku optymalizacji wykorzystujemy jedną obserwację. Oznacza to więc, że rozmiar batcha wynosi $B=1$.

Gradient obliczamy po funkcji straty pojedynczej obserwacji $\ell$, a następnie aktualizujemy parametry.

$$\theta ^{(t+1)}=\theta^{(t)}-\eta \nabla_{\theta}\ell(\hat{y},y)$$

## Batch Learning (Gradient Descent)
**Batch Gradient Descent** to metoda optymalizacji, w której gradient funkcji straty obliczamy na podstawie wszystkich obserwacji ze zbioru treningowego, a następnie wykonujemy jedną aktualizację parametrów modelu.

Funkcję straty definiujemy jako:

$$\mathcal{L}(\theta)=\frac{1}{S} \sum_{s=1}^S \ell(\hat{y}_{i}^{(s)}-y_{i}^{(s)})$$

gdzie $\ell$ jest funkcją straty pojedynczej obserwacji. Następnie aktualizujemy parametry:

$$\theta ^{(t+1)}=\theta ^{(t)}-\eta \nabla_{\theta}\mathcal{L}$$

Gradient jest dokładnym gradientem empirycznej funkcji straty, a nie jej przybliżeniem uzyskanym z podzbioru obserwacji.

## Mini-Batch
**Mini-Batch Gradient Descent** to metoda optymalizacji, w której zbiór treningowy dzielimy na mniejsze partie danych (*mini-batches*). Rozmiar batcha (ang. *batch size*) określać będziemy przez $B$, a liczbę próbek przez $N$:
- **Stochastic Gradient Descent** (**SGD**): 

$$B=1$$

- **Batch Gradient Descent**

$$B=N$$

- **Mini-Batch Gradient Descent**

$$B<N$$

Niech:

$$
\mathcal B_t\subseteq\{1,\ldots,N\}
$$

oznacza zbiór indeksów obserwacji należących do mini-batcha w iteracji $t$

Gradient obliczamy jako:

$$\nabla_{\theta ^{(t)}}\mathcal{L}=
\frac{1}{|\mathcal B_t|}
\sum_{i\in\mathcal B_t}
\nabla_\theta\ell(f_{\theta ^{(t)}}(x_i),y_i)$$

Parametry aktualizujemy według reguły:

$$
\theta ^{(t+1)}=\theta ^{(t)}-\eta \nabla_{\theta ^{(t)}}\mathcal{L}
$$

W praktycznych implementacjach wartość $B$ często wybieramy jako potęgę liczby $2$ z czysto praktycznego względu – GPU (ang. *Graphics Processing Unit*) najoptymalniej radzi sobie z przetwarzaniem danych pogrupowanych w $2^n$ elementów.

## Long-short term memory
**Long-short term memory** (LSTM) to rodzaj rekurencyjnej sieci neuronowej, zaprojektowany do przetwarzania danych sekwencyjnych oraz uczenia się zależności występujących pomiędzy odległymi elementami sekwencji. LSTM są poniekąd poprzednikami LLM-ów, pierwsze czaty (między innymi popularne okienka *Can i help you?* opierały się właśnei na LSTM-ach).

LSTM jest siecią rekurencyjną, rekurencji poddajemy jednak całe **komórki LSTM** (ang. *LSTM cell*), a nie pojedyncze neurony. Budowa takiej sieci wygląda następująco:

[]

$C_{t-1}\rightarrow \times →_{\alpha_{t-1}} →C_{t}$
zapomianym część wspomnień, a rezta przechodzi dalej. Tworzymy nowe wspomnienie w neuronach 1,2. Odpowiadaja one za short time memory. Main output tworzy neuron 3. (0, 1, 2, 3 to biasy)

