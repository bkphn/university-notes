## Błąd pomiaru
Zakładając, że istnieje rzeczywista wartość zjawiska, które mierzymy, błędem pomiaru tegoż zjawiska nazywamy różnicę między wielkością zmierzoną w eksperymencie a tą faktyczną:$$ \Delta x = x - x_0 $$Gdzie $\Delta x$ to błąd pomiaru, $x$ to wartość zmierzona, a $x_0$ to wartość rzeczywista.

**Podział błędów:**
* **Błędy przypadkowe** – związane ze zdarzeniami przypadkowymi.
* **Błędy grube** – związane z pomyłką osoby przeprowadzającej eksperyment.
* **Błędy systematyczne** – związane z cechami metody pomiarowej.

Za pomocą błędu pomiaru możemy obliczyć przedział $(x_0 - \Delta x, x_0 + \Delta x)$, w którym znajduje się wartość rzeczywista. Parametr $\Delta x$ nazywamy niepewnością graniczną.
## Niepewność standardowa
Niepewność standardowa to niepewność wyniku pomiaru przedstawiona w formie odchylenia standardowego. Obliczana jest ze wzoru:
$$ u(x) = \sqrt{u_a^2(x) + u_b^2(x)} $$
Gdzie $u(x)$ to niepewność standardowa, $u_a(x)$ to niepewność statystyczna, a $u_b(x)$ to niepewność pomiarowa.

### 1. Niepewność pomiarowa
Niepewność pomiarowa zależna jest od niedokładności używanego sprzętu i wyznaczamy ją wzorem:
$$ u_b(x) = \frac{a}{\sqrt{3}} $$
Gdzie $a$ oznacza:
* **Dla przyrządów mechanicznych:** najmniejsza podziałka sprzętu.
* **Dla przyrządów analogicznych:** $\frac{\text{klasa dokładności} \cdot \text{zakres pomiarowy}}{100}$.
* **Dla przyrządów cyfrowych:** $\text{klasa przyrządu} \cdot \text{wynik} + \text{liczba naturalna} \cdot \text{rozdzielczość}$.

### 2. Niepewność statystyczna
Niepewność statystyczna otrzymywana jest w zależności od uzyskanych wyników za pomocą wzoru:
$$ u_a(x) = \sqrt{\frac{1}{N(N-1)} \cdot \sum_{i=1}^{N} (x_i - \bar{x})^2} \cdot t_{\alpha, N} $$
Gdzie $N$ to ilość wykonanych pomiarów, $x_i$ to $i$-ty pomiar, $t_{\alpha, N}$ to współczynnik Studenta-Fishera, a $\bar{x}$ to średnia arytmetyczna wszystkich wyników:
$$ \bar{x} = \frac{1}{N} \cdot \sum_{i=1}^{N} x_i $$
Dla zwykłych pomiarów wybiera się poziom ufności $\alpha = 0.6828$ (w tabelach oznaczany również jako $0.6826^*$).
## Prawo propagacji niepewności
Pomiar pośredni to doświadczenie, w którym poszukiwaną wartość wyznacza się za pomocą innych – mierzonych bezpośrednio. Wartość taką wyznacza się funkcją $y = f(x_1, \dots, x_k)$. Jeżeli każdy z pomiarów bezpośrednich posiada swoją niepewność, to niepewność pomiaru pośredniego wyraża się wzorem:
$$ u(y) = \sqrt{\sum_{i=1}^{k} \left[\frac{\partial y}{\partial x_i} \cdot u(x_i)\right]^2} $$
Gdzie $u(y)$ to niepewność pomiaru pośredniego, $x_i$ to $i$-ty pomiar bezpośredni, a $u(x_i)$ to niepewność $i$-tego pomiaru bezpośredniego.
## Zapis wyników końcowych
Niepewność podaje się z dokładnością do dwóch cyfr znaczących. Wyniki końcowe należy zapisywać w jednym z trzech formatów:
* **Format słowny:** Okres wahadła wynosi $1.2867\text{ s}$ z niepewnością $0.0035\text{ s}$.
* **Format symboliczny:** $T = 1.2867\text{ s}, \, u(T) = 0.0035\text{ s}$.
* **Format skrócony:** $T = 1.2867(35)\text{ s}$ (w formacie skróconym podajemy niepewność dla dwóch ostatnich cyfr, bez użycia przecinka).
## Zgodność wyniku końcowego
Jeżeli poniższa nierówność jest prawdziwa, to wartość uznaje się za zgodną z wartością dokładną:
$$ |y - y_0| < U(y) $$
Gdzie $y$ to wartość zmierzona, $y_0$ to wartość rzeczywista, a $U(y)$ to niepewność rozszerzona. Według przyjętych standardów niepewność rozszerzona jest dwukrotnością niepewności wyniku pomiaru:
$$ U(y) = 2 \cdot u(y) $$
Zapis końcowy niepewności rozszerzonej wygląda następująco: $T = 1.2867 \pm 0.0070\text{ s}$.
## Regresja liniowa
Jeżeli zależność między wielkościami jest uważana za liniową, linię trendu wyznacza się metodą regresji liniowej w postaci $y = ax + b$, gdzie $a$ to współczynnik kierunkowy prostej, a $b$ to przecięcie prostej z osią $OY$.

Wzory dla linii trendu pomiarów:
$$ a = \frac{n \cdot S_{xy} - S_x \cdot S_y}{n \cdot S_{xx} - S_x^2}, \quad b = \frac{S_{xx} \cdot S_y - S_x \cdot S_{xy}}{n \cdot S_{xx} - S_x^2} $$

Wzory dla niepewności pomiarowych współczynników regresji:
$$ u(a) = \sqrt{\frac{n}{n-2} \cdot \frac{S_{\varepsilon\varepsilon}}{n \cdot S_{xx} - S_x^2}}, \quad u(b) = \sqrt{\frac{1}{n-2} \cdot \frac{S_{xx} \cdot S_{\varepsilon\varepsilon}}{n \cdot S_{xx} - S_x^2}} $$

Gdzie poszczególne sumy wyznacza się następująco:
* $\varepsilon_i = y_i - ax_i - b$
* $S_x = \sum_{i=1}^{n} x_i$
* $S_y = \sum_{i=1}^{n} y_i$
* $S_{xy} = \sum_{i=1}^{n} x_i \cdot y_i$
* $S_{xx} = \sum_{i=1}^{n} x_i^2$
* $S_{\varepsilon\varepsilon} = \sum_{i=1}^{n} \varepsilon_i^2$
## Wytyczne dotyczące wykresów
* Na osi $Y$ przedstawia się wielkości będące skutkiem tych na osi $X$.
* Osie wykresu muszą mieć ustaloną skalę liczbową i należy je podpisać nazwą osi oraz jednostką.
* Osie nie muszą zaczynać się od 0.
* Na wykresie należy przedstawić punkty pomiarowe oraz zaznaczyć słupki niepewności dla wielkości mierzonych bezpośrednio.
* Punktów pomiarowych nie należy łączyć odcinkami.
* Należy przedstawić linię trendu (w przypadku zależności liniowej wyznaczoną za pomocą regresji liniowej).
* Wartości odczytywane z wykresu należy podpisać.