## Teoria dystrybucji
Teoria dystrybucji to dział analizy funkcjonalnej, który rozwinął się w połowie XX wieku za sprawą Laurenta Schwarta. Jej głównym celem było rozszerzenie pojęcia funkcji w taki sposób, aby można było sensownie operować na obiektach, które nie są klasycznymi funkcjami, np. na delcie Diraca.
## Klasy funkcji
Klasą nazywamy obiekt matematyczny zbyt duży, by być zbiorem (np. „zbiór wszystkich zbiorów”, który zgodnie z paradoksem Russella nie może istnieć jako typowy zbiór). Przykłady klas:
* **$\text{Card}$**: klasa wszystkich liczb kardynalnych
* **$\text{Ord}$**: klasa wszystkich liczb porządkowych
* **$C$**: klasa wszystkich funkcji

Dowolną klasę $C^n$ będziemy nazywać klasą wszystkich funkcji ciągłych, posiadających w każdym punkcie pochodną $n$-tego rzędu:
* **Klasa $C^0$**: klasa zawierająca wszystkie funkcje ciągłe.
* **Klasa $C^1$**: klasa zawierająca wszystkie funkcje ciągłe, które posiadają pochodną pierwszego rzędu.
* **Klasa $C^2$**: klasa zawierająca wszystkie funkcje ciągłe, które posiadają pochodną drugiego rzędu.
	$\vdots$
* **Klasa $C^\infty$**: klasa wszystkich funkcji, które posiadają pochodne dowolnego rzędu i są ciągłe.
## Domknięcie zbioru
Domknięciem zbioru $A$ nazywamy zbiór zawierający wszystkie elementy tego zbioru wraz z jego punktami granicznymi; domknięcie to oznaczamy jako $\bar{A}$.

> [!example] Przykład wyznaczenia domknięcia
> Niech $X = \{x \in \mathbb{R} : x > 0 \land x \le 10\} = (0, 10]$.
> Domknięcie wynosi:
> $$ \bar{X} = \{x \in \mathbb{R} : x > 0 \land x \le 10\} \cup \{0, 10\} = (0, 10] \cup \{0, 10\} = [0, 10] $$
## Funkcje testowe
Funkcje testowe, nazywane również funkcjami próbnymi, to funkcje, na których działają dystrybucje. Funkcja należy do klasy $C^\infty$, jeżeli ma pochodne dowolnego rzędu w każdym punkcie dziedziny ($f \in C^\infty$).

Nośnikiem funkcji będziemy nazywać podzbiór jej dziedziny, który zwraca tylko niezerowe argumenty funkcji (miejsca, w których funkcja „nie znika”). Nośnik funkcji wyznaczamy za pomocą funkcji $\operatorname{supp}$, definiowanej wzorem:
$$ \operatorname{supp}(f) = \{x \in \mathbb{R}^n : f(x) \neq 0\} $$
> [!example] Przykłady wyznaczania nośników
> * Dla $f(x) = e^x$: $e^x = 0 \iff x \in \emptyset$, więc $\operatorname{supp}(e^x) = \mathbb{R}$.
> * Dla funkcji skokowej $g(x) = u(x)$: $u(x) = 0 \iff x < 0$, więc $\operatorname{supp}(u) = [0, \infty)$.
> * Dla funkcji $h(x) = \operatorname{sgn}(x)$: $\operatorname{sgn}(x) = 0 \iff x = 0$, więc $\operatorname{supp}(\operatorname{sgn}) = \mathbb{R} \setminus \{0\}$.
### Przestrzeń funkcji testowych
Przestrzeń funkcji testowych to podzbiór klasy $C^\infty$, zawierający funkcje ze zwartym nośnikiem (takie, których nośnik jest zbiorem skończonym). Przestrzeń funkcji testowych o nośniku zawartym w $U \subseteq \mathbb{R}^n$ oznaczamy jako $\mathcal{D}(U)$. Każda funkcja $f : \mathbb{R} \to \mathbb{R}$ należy do klasy $\mathcal{D}(\mathbb{R})$, gdy $f \in C^\infty$ oraz $\operatorname{supp} f \subset [c, d]$.

**Zbieżność funkcji testowych:** Dany jest ciąg funkcji $f_n \in \mathcal{D}(\mathbb{R})$ oraz funkcja $f \in \mathcal{D}(\mathbb{R})$. Mówimy, że $f_n$ zbiega w przestrzeni funkcji testowych do $f$ ($f_n \to f$), gdy:
1. **Wspólny ograniczony nośnik:** Funkcje $f_n$ i $f$ mają wspólny ograniczony nośnik ($\exists_{[c,d]} \forall_n : \operatorname{supp} f_n \subset [c, d] \land \operatorname{supp} f \subset [c, d]$).
2. **Zbieżność jednostajna:** Funkcje zbiegają jednostajnie ($f_n \Rightarrow f = \max_{x \in [c,d]} |f_n(x) - f(x)| \to 0$).
Powyższe warunki muszą być spełnione również dla pochodnej dowolnego rzędu.
## Funkcjonały i dystrybucje
**Funkcjonałem** nazywamy odwzorowanie, które jako argument przyjmuje funkcję, a jako wartość zwraca liczbę ($T : X \to \mathbb{R}$, gdzie $X$ jest przestrzenią funkcji). Przykłady:
  * $T(f) = \int_{a}^{b} f(x) \, dx$ (zwraca pole pod wykresem)
  * $T(f) = f(0)$ (zwraca wartość w punkcie zerowym)

**Funkcjonałem liniowym** nazywamy odwzorowanie $T : \mathcal{D}(\mathbb{R}) \to \mathbb{R}$, dla którego zachodzi $T(\alpha f + \beta g) = \alpha T(f) + \beta T(g)$ dla dowolnych skalarów $\alpha, \beta$ i funkcji $f, g$.

**Dystrybucja** to funkcjonał liniowy $T$ określony na $\mathbb{R}$, któr spełnia warunek: $$\int_{\mathbb{R}} T \cdot f_n = \int_{\mathbb{R}} T \cdot f \iff f_n \to f$$Każda całkowalna i określona funkcja na $\mathbb{R}$ jest dystrybucją. Zachodzi też relacja: $$T_n \to T \iff \int_{\mathbb{R}} T_n \cdot f \to \int_{\mathbb{R}} T \cdot f$$
## Pochodne dystrybucji i delta Diraca
$T'$ jest pochodną dystrybucji $T$, gdy spełniony jest warunek:
$$ \int_{\mathbb{R}} T' \cdot f = -\int_{\mathbb{R}} T \cdot f' $$

> [!example] Pochodna funkcji Heaviside'a
> Licząc pochodną funkcji Heaviside'a $u(x)$ za pomocą definicji dystrybucyjnej:
> $$ -\int_{\mathbb{R}} u(x) \cdot f'(x) \, dx = -\int_{0}^{\infty} f'(x) \, dx = -[f(x)]_0^\infty = f(0) = \delta(x) $$
> W kontekście dystrybucji delta Diraca jest pochodną funkcji skokowej Heaviside'a ($u'(x) = \delta(x)$).

### Własności delty Diraca
Dystrybucja $\delta(x)$ to delta Diraca – reprezentacja nieskończenie krótkiego impulsu o całkowitej powierzchni równej 1. Opisuje ją wzór:
$$ \int_{-\infty}^{\infty} \delta(x) \, dx = 1 \land \delta(x) = \begin{cases} 0, & x \neq 0 \\ \infty, & x = 0 \end{cases} $$

Na delcie Diraca można przesuwać argument:
$$ \delta(x - a) = \begin{cases} 0, & x \neq a \\ \infty, & x = a \end{cases}, \quad \int_{-\infty}^{\infty} \delta(x - a) \, dx = 1 $$

**Transformacja Laplace'a dla delty Diraca:**
Definiując deltę jako granicę $\delta(x) = \lim_{\varepsilon \to 0^{+}} \delta_\varepsilon(x)$, gdzie:
$$ \delta_\varepsilon(x) = \begin{cases} \frac{1}{\varepsilon}, & x \in [0, \varepsilon] \\ 0, & x \notin [0, \varepsilon] \end{cases} $$
Obliczamy transformatę Laplace'a:
$$ \mathcal{L}[\delta_\varepsilon(x)](s) = \int_{0}^{\varepsilon} \frac{e^{-sx}}{\varepsilon} \, dx = \frac{e^{-s\varepsilon} - e^0}{-s\varepsilon} $$
Przechodząc do granicy, otrzymujemy poszukiwaną transformatę:
$$ \mathcal{L}[\delta(x)](s) = \lim_{\varepsilon \to 0} \left[\frac{e^{-s\varepsilon} - 1}{-s\varepsilon}\right] = 1 $$