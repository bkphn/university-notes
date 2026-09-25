## Metoda empiryczna
Rozważmy próbę losową składającą się z pomiarów $\xi_n = \{x_1, \dots, x_n\}$, dla których prawdopodobieństwo wylosowania pojedynczej obserwacji przy zwrocie to $P(\xi_n = x_i) = \frac{1}{n}$. Niech $\Theta$ będzie klasą poszukiwanych parametrów postaci $\Theta = \{\theta: \theta = h(\mathbb{E}[g(\xi)])\}$, gdzie $h$ oraz $g$ to pewne z góry znane funkcje.

W metodzie tej, szacowany parametr $\theta$ wyznaczamy zastępując teoretyczną wartość oczekiwaną $\mathbb{E}[g(\xi)]$ jej empirycznym odpowiednikiem, czyli średnią arytmetyczną z próby. Estymator przyjmuje zatem postać:

$$\theta_n = h\left( \frac{1}{n} \sum_{i=1}^n g(x_i) \right)$$

Jeśli założymy, że pochodna $h'(\mathbb{E}[\xi]) \neq 0$, to jesteśmy w stanie opisać asymptotyczny rozkład tego estymatora. Na mocy Centralnego Twierdzenia Granicznego, ustandaryzowany błąd estymacji zbiega według rozkładu do standardowego rozkładu normalnego $\mathcal{N}(0,1)$, co zapisujemy za pomocą granicy dystrybuanty $\Phi(z)$:

$$\lim_{n \to \infty} P\left( \frac{\sqrt{n} \cdot (\theta_n - \theta)}{h'(\mathbb{E}[\xi]) \cdot \sqrt{D^2[g(\xi)]}} < z \right) = \Phi(z)$$

Wnioskiem z tego twierdzenia jest to, że rozrzut estymatora zachowuje się jak przeskalowana, losowa zmienna normalna $\eta$. Dystans między prawdziwym parametrem a naszą oceną dąży do zera wraz ze wzrostem wielkości próby w tempie odwrotnie proporcjonalnym do $\sqrt{n}$. Używając notacji asymptotycznej $\mathcal{O}$ możemy to zapisać jako:

$$\theta_n = \theta + \mathcal{O}\left(\frac{1}{\sqrt{n}}\right)$$

## Metoda Największej Wiarygodności (MNW)
Niech populacja generalna $\xi$ posiada gęstość prawdopodobieństwa określoną jako $f(x, \theta)$, gdzie nieznany szacowany parametr należy do przedziału $\theta \in \Theta = [a,b]$. Metoda ta opiera się na wyznaczeniu takiego $\theta$, przy którym szansa uzyskania zaobserwowanych wyników z próby jest matematycznie najwyższa.

Zakładając, że funkcja gęstości jest odpowiednio gładka (np. jest trzykrotnie różniczkowalna, $f \in C^3$), operujemy wielkością całkową zwaną Informacją Fishera (oznaczoną jako $I(\theta)$):

$$I(\theta) = \int_{-\infty}^\infty \left( \frac{\partial \ln f(x, \theta)}{\partial \theta} \right)^2 f(x, \theta) dx$$

Zgodnie z twierdzeniem o własnościach ocen wiarygodności, prawidłowo wyznaczony estymator MNW charakteryzuje się świetnymi własnościami dla dużych prób:
- Jest mocno zgodny, tzn. zbiega z prawdopodobieństwem 1 do prawdziwej wartości parametru $\theta^{\ast}$: $\theta_n \xrightarrow{\text{p.n.}}\theta^{\ast}$.
- Ma rozkład asymptotycznie normalny $\mathcal{N}(0,1)$, uwarunkowany przez Informację Fishera: $\lim_{n \to \infty} P\left(\sqrt{n \cdot I(\theta)} \cdot (\theta_n - \theta) < x\right) = \Phi(x)$.

## Metoda Momentów (MM)
Jest to historycznie jedna z pierwszych procedur punktowego szacowania parametrów. Z racji niskiej efektywności dla wielu rozkładów, nie jest ona już obecnie powszechnie stosowana w analityce.

Bazuje ona na teoretycznym momencie rzędu $k$ ($k \in \mathbb{N}$), zdefiniowanym przez wartość oczekiwaną odpowiedniej potęgi zmiennej losowej:

$$m_k(\theta) = \mathbb{E}[\xi^k] = \int_{-\infty}^\infty x^k f(x, \theta) dx$$

Pod warunkiem, że relacja ta zachowuje ciągłość i posiada jawną funkcję odwrotną $m_k^{-1}$, tworzymy estymator przyrównując moment teoretyczny do momentu wyliczonego bezpośrednio z próby empirycznej:

$$\theta_n(\vec{x}) = m_k^{-1}\left( \frac{1}{n} \sum_{i=1}^n x_i^k \right)$$

## Funkcja Gamma
Funkcja Gamma (często nazywana Gammą Eulera) powstała w celu uogólnienia dyskretnej operacji silni ($!$) na zbiór liczb rzeczywistych $\mathbb{R}$ oraz zespolonych $\mathbb{C}$. Warto podkreślić, że matematycznie nie jest to jedyne możliwe rozszerzenie. Przez zbiór izolowanych punktów opisujących klasyczną silnię można teoretycznie przeprowadzić nieskończenie wiele różnych krzywych ciągłych, jednak to właśnie funkcja Gamma ze względu na swoje właściwości analityczne stała się fundamentalnym standardem.

Dla liczb zespolonych o dodatniej części rzeczywistej ($\mathfrak{R}(z) > 0$), funkcję definiujemy wzorem całkowym: 

$$\Gamma(z) = \int_0^\infty t^{z-1} e^{-t} dt$$

W szerszym ujęciu (dla dowolnych liczb zespolonych poza biegunami) istnieje definicja w tzw. postaci iloczynowej:

$$\Gamma(z) = \frac{1}{z} \prod_{n=1}^\infty \frac{\left(1 + \frac{1}{n}\right)^z}{1 + \frac{z}{n}}$$

Własności bazowe funkcji Gamma:
- Wartość dla jedności: $\Gamma(1) = 1$.
- Równanie rekurencyjne pozwalające podnosić argument: $\Gamma(z+1) = z \cdot \Gamma(z)$.
- Relacja z silnią dla liczb naturalnych ($n \in \mathbb{N}$): $\Gamma(n+1) = n!$.
- Wartości dla liczb połówkowych: $\Gamma\left(n + \frac{1}{2}\right) = \frac{(2n-1)!!}{2^n} \sqrt{\pi}$.

## Rozkłady
Procedury dowodowe w statystyce (wykraczające poza samą dystrybuantę $P(\xi < x) = F(x)$) silnie bazują na trzech fundamentalnych rozkładach ciągłych:
- **Rozkład normalny** $\mathcal{N}(m, \sigma^2)$: Klasyczny rozkład przyjmujący formę dzwonu, o wariancji $\sigma^2$ i wartości oczekiwanej $m$. Jest punktem zbieżności asymptotycznej dla większości klasycznych estymatorów.![[Pasted image 20260922030413.png|307]]
- **Rozkład Chi-kwadrat** ($\chi_k^2$): Rozkład ten opisuje zmienną losową zdefiniowaną jako suma kwadratów $k$ sztuk niezależnych standardowych zmiennych normalnych $\xi$ (gdzie parametr $k$ to tzw. stopnie swobody):

$$\chi_k^2 \equiv \sum_{i=1}^k \xi_i^2$$

Jego skomplikowana gęstość prawdopodobieństwa powiązana jest wprost ze wspomnianą wyżej funkcją Gamma. Dla wartości dodatnich $x > 0$ przybiera ona postać:

$$k_n(x) = \frac{x^{\frac{k}{2}-1} \cdot e^{-\frac{x}{2}}}{2^{\frac{k}{2}} \cdot \Gamma\left(\frac{k}{2}\right)}$$

![[Pasted image 20260922030429.png|288]]
- **Rozkład t-Studenta (Gosseta)**: Narzędzie niezbędne przy opracowywaniu wyników z małych próbek o nieznanej wariancji dokładnej. Zmienną tego rozkładu konstruuje się dzieląc zmienną o rozkładzie normalnym przez spierwiastkowaną, empiryczną wariancję innych zmiennych:

$$t_n = \frac{\xi}{\sqrt{\frac{1}{n} \sum_{i=1}^n \xi_i^2}}$$

Jego gęstość probabilistyczna dana jest ułamkiem:

$$s_n(x) = \frac{1}{\sqrt{n\pi}} \cdot \frac{\Gamma\left(\frac{n+1}{2}\right)}{\Gamma\left(\frac{n}{2}\right)} \cdot \left(1 + \frac{x^2}{n}\right)^{-\frac{n+1}{2}}$$

![[Pasted image 20260922030440.png|299]]
