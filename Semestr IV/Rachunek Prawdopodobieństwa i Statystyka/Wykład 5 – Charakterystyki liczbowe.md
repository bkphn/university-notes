## Wartość oczekiwana
**Wartość oczekiwaną** zmiennej losowej $\xi$ (czasem nazywaną wartością przeciętną, bądź nadzieją matematyczną) oznaczamy symbolem $\mathbb{E}[x]$, innymi stosowanymi notacjami są $E(\xi )$ bądź $\operatorname{E}\xi $, i definiujemy następująco:
- Jeśli zmienna losowa $\xi$ jest typu dyskretnego o rozkładzie $P(x_i )=p_i$, to: $$\mathbb{E}[\xi]=\sum_{k=1}^\infty x_{k}p_{k}$$
- Jeśli zmienna losowa $\xi$ jest typu absolutnie ciągłego z gęstością $f(x)$, to: $$\mathbb{E}[\xi]=\int_{-\infty}^\infty x\cdot f(x) dx$$
Wartość oczekiwana jest „środkiem ciężkości” różnych prób w rozkładzie prawdpodobieństwa. Proces jej obliczania można rozumieć tak: znajdujemy iloczyn wartości zmiennej losowej przez prawdpodobieństwo tego, że zmienna losowa przybiera daną wartość $x_i p_i=x_i, P(\xi=x_i )$, następnie obliczamy sumę wszystkich możliwych iloczynów.

Podobnie traktujemy wzór: $$\mathbb{E}[g(x)]=\int_{-\infty}^\infty g(x) \cdot f(x) dx$$
## Własności wartości oczekiwanej
Niech $a,b\in\mathbb{R}$ będą stałymi, a $\xi,\eta$ niezależnymi zmiennymi losowymi. Wtedy dla wartości oczekiwanej $\mathbb{E}$ zachodzą własności:
- $\mathbb{E}[a]=a$
- $\mathbb{E}[a\xi+b\eta]=a\cdot \mathbb{E}[\xi]+b\cdot \mathbb{E}[\eta]$
- $\mathbb{E}[\xi\eta]=\mathbb{E}[\xi]\cdot \mathbb{E}[\eta]$
- $\left|\mathbb{E}[\xi]\right|\leq \mathbb{E}[|\xi|]$

> [!example] Dla $\xi$ o rozkładzie zero-jedynkowym, wykładniczym i Gaussa, wyznacz $E(\xi)$
> 
> **1. Rozkład zero-jedynkowy**
> $$P(\xi = 1) = p, \quad P(\xi = 0) = 1 - p = q$$
> $$\mathbb{E}[\xi] = 1 \cdot p + 0 \cdot q = p$$
> 
> **2. Rozkład wykładniczy**
> $$f(x) = \lambda e^{-\lambda x}$$
> $$\mathbb{E}[\xi] = \lambda \int_{0}^{\infty} x e^{-\lambda x} \, dx = \frac{1}{\lambda}$$
> 
> **3. Rozkład Gaussa**
> $$f(x) \in N(m, \sigma^2) \Rightarrow f(x) = \frac{\exp\left( - \frac{(x-m)^2}{2\sigma^2} \right)}{\sigma\sqrt{2\pi}}$$
> $$\mathbb{E}[\xi] = \frac{1}{\sigma\sqrt{2\pi}} \int_{-\infty}^{\infty} x \exp\left( - \frac{(x-m)^2}{2\sigma^2} \right) dx = \left| \frac{x-m}{\sigma} = v \right| =$$
> $$= \frac{1}{\sqrt{2\pi}} \int_{-\infty}^{\infty} (\sigma v + m) \exp\left( - \frac{v^2}{2} \right) dv =$$
> $$= \frac{\sigma}{\sqrt{2\pi}} \int_{-\infty}^{\infty} v \exp\left( - \frac{v^2}{2} \right) dv + \frac{m}{\sqrt{2\pi}} \int_{-\infty}^{\infty} \exp\left( - \frac{v^2}{2} \right) dv = m$$
> $$\mathbb{E}[\xi] = m$$
## Wariancja
Wariancję zmiennej losowej $\xi$ oznaczamy jako $D[\xi]$ (w europejskiej notacji stosuje się zapis $V[\xi ]$) i definiujemy wzorem: $$D^2 [\xi ]=\mathbb{E}[\xi −\mathbb{E}[\xi ]]^2$$przy czym zachodzi związek: $$D^2 [\xi ]=\mathbb{E}[\xi ^2 ]−\mathbb{E}^2 [\xi ]$$gdzie $\mathbb{E}^2[\xi]=(\mathbb{E}[\xi])^2$.

Dla niezależnych zmiennych losowych $\xi ,\eta$ oraz stałych $a,b$ wariancja spełnia własności:
- $D[a]=0$
- $D^2 [\xi ]=0\implies\xi =\mathbb{E}[\xi ]$
- $D[a\xi +b\eta ]=a^2 D[\xi ]+b^2 D[\eta ]$
- $D^2 [\xi ±\eta ]=D^2 [\xi ]+D^2 [\eta ]$

Pamiętając, że zmienną losową $\xi$ możemy przedstawić w postaci $\xi=\sum_{i=1}^n\xi_{i}$ gdzie zmienne $\xi_{i}$ są parami niezależne, to dla dowolnych $a_i\in\mathbb{R}$ zachodzą własności:
- $D^2[\xi]=D^2\left[\sum_{i=1}^n \xi_{i}\right]=\sum_{i=1}^n D^2[\xi_{i}]$
- $D\left[ \sum_{i=1}^n a_{i}\xi_{i} \right]=\sum_{i=1}^n a_{i}^2D[\xi_{i}]$

Jeżeli $\xi \in\mathcal{N}(m, \sigma^2)$, to:
- $\mathbb{E}[\xi ]=m$
- $D^2 [\xi ]=\sigma^2$
## Nierówność Czebyszewa
Nierówność zaproponowana oryginalnie przez Bienaymé'a została udowodniona w 1967 roku przez rosyjskiego matematyka Pafnutija Czebyszewa. 

Twierdzenie to mówi nam w praktyce, że większość wartości przyjmowanych przez zmienną losową skupia się blisko jej wartości oczekiwanej. Prawdopodobieństwo tego, że wynik eksperymentu odchyli się od średniej o bardzo dużą wartość, jest ściśle ograniczone z góry przez wariancję. 

>[!danger] Nierówność Czebyszewa
> Jeśli zmienna losowa $\xi$ jest taka, że $D[\xi ]<\infty$, to dla dowolnego $\varepsilon>0$ zachodzi nierówność: $$P(|\xi −\mathbb{E}[\xi ]|\geq \varepsilon)\leq\frac{D^2 [\xi ]}{\varepsilon^2}$$

## Momenty
**Momentem rzędu** $k$ zmiennej losowej $\xi$ o dystrybuancie $F(x)$ nazywamy wielkość: $$m_{k}=\mathbb{E}\left[\xi^k\right]$$
**Momentem centralnym rzędu** $k$ zmiennej losowej $\xi$ o dystrybuancie $F(x)$ nazywamy wielkość: $$\mu_{k}=\mathbb{E}[\xi-\mathbb{E}[\xi]]^k$$
**Momentem absolutnym rzędu** $k$ zmiennej losowej $\xi$ o dytrybuancie $F(x)$ nazywamy wielkość: $$\nu_{k}=\mathbb{E}[|\xi-\mathbb{E}[\xi]|]^k$$
## Wskaźniki
Niech dystrybuanta $F(x)$ będzie ciągła. **Kwantylem rzędu** $p$ dystrybuanty $F$ nazywamy najmniejszy pierwiastek równania $F(x)=p$, czyli liczbę $k(p)$, dla której: $$F(k(p))=p, \quad 0<p<1$$
Kwantyl rzędu $p=\frac{1}{2}$ zmiennej losowej $\xi$ nazywamy **medianą** i oznaczamy jako $m_e$.

Wskaźnikami nazywamy miary kształtu rozkładu. Są to wielkości statystyczne, które pozwalają nam ocenić, jak wygląda rozkład prawdopodobieństwa zmiennej losowej. Możemy wyróżnić następujące wskaźniki:
- **Wskaźnik zmienności** $$\gamma_{1}=\frac{D[\xi]}{\mathbb{E}[\xi]}$$
- **Wskaźnik asymetrii** $$\gamma_{2}=\frac{\mu_{3}}{D^3[\xi]}$$
- **Kurtoza** $$\gamma_{3}=\frac{\mu_{4}}{D^4[\xi]}-3$$
## Współczynniki korelacji
Współczynnikiem korelacji zmiennych losowych $\xi ,\eta$ nazywamy liczbę: $$\rho_{\xi\eta}=\frac{\mathbb{E}\left[(\xi-\mathbb{E}[\xi])(\eta-\mathbb{E}[\xi])\right]}{D[\xi]D[\eta]}$$
Współczynnik korelacji spełnia własności:
- $|\rho_{\xi \eta}  |\leq 1$
- Jeżeli $\xi ,\eta$ są niezależne, to $\rho_{\xi \eta} =0$
- Dla dowolnych $a,b>0, c,d\in\mathbb{R}$ zachodzi $ρ_{a\xi+c, b\eta+d}=\rho_{\xi\eta}$ 
- $\rho_{\xi\eta}=\pm 1\implies\exists_{a,b}:\xi=a\eta+b$

Jeżeli $0.8\leq|\rho_{\xi \eta}|\leq1$ to mówimy, że współczynnik korelacji jest bardzo mocny, jeżeli $0.5\leq|\rho_{\xi \eta} |<0.8$ to mówimy, że współczynnik korelacji jest umiarkowany.

>[!danger] Twierdzenie Cauchy'ego-Buniakowskiego 
> Jeśli zmienne losowe $\xi ,\eta$ są takie, że wartości oczekiwane obu zmiennych losowych są skończone, to zachodzi: $$|\mathbb{E}[\xi\eta]|\leq \sqrt{ \mathbb{E}[\xi^2] \mathbb{E}[\eta^2] }$$
