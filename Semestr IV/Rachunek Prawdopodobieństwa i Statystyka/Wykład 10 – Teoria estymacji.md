## Estymatory
Dla dowolnej $n$-argumentowej funkcji $g$, wartość $g(x_1,\dots,x_n )$ nazywamy **statystyką**.

Niech $\theta$ będzie pewnym nieznanym parametrem. **Estymatorem** parametru $\theta$ nazywamy każdą statystykę $g$, której wartość przyjmujemy jako wartość parametru $\theta$. Konkretną wartość liczbową tego estymatora nazywamy **oceną parametru** $\theta$.

Estymator parametru $\theta$ będziemy oznaczali jako $\hat{\theta}(x_1,…,x_n )$ bądź po prostu $\theta_{n}$. Obciążeniem estymatora nazywamy różnicę $\mathbb{E}[\theta_{n}]-\theta$.

Estymator $\theta_n$ możemy określić jako:
- **Estymator nieobciążony**

$$\mathbb{E}[\theta_{n}]=\theta, \quad \forall_{n}$$

- **Estymator asymptotycznie nieobciążony**

$$\lim_{ n \to \infty } \mathbb{E}[\theta_{n}]=\theta$$

- **Estymator zgodny**

$$\theta_{n} \xrightarrow[n \to \infty]{\text{p.n.}} \theta$$

## Efektywność estymatorów
Powiemy, że estymator $\theta_n^{(1)}$ jest efektywniejszy od estymatora $\theta_n^{(2)}$, jeżeli:

$$D^2\left[\theta_{n}^{(1)}\right]<D^2\left[\theta_{n}^{(2)}\right]$$

Estymatorem najlepszym nazywamy estymator $\theta_n^{\ast}$ taki, że:

$$D^2\left[\theta_{n}^{\ast} \right]\leq \inf{D^2\left[ \theta_{n} \right]}$$

gdzie $\theta_n\in\Theta, \Theta=\{\theta_{n} : \mathbb{E}[\theta_{n}]=\theta\}$.

## Nierówność Rao-Cramera
Niech populacja generalna $\xi$ ma gęstość $f(x,\theta)$, gdzie $\theta\in\Theta=[a,b]$ jest nieznanym parametrem, a $\theta_n$ jest nieobciążonym estymatorem $\theta$, wówczas zachodzi nierówność:

$$D^2[\theta_{n}] \geq \frac{1}{n\cdot \mathbb{E}\left[ \left( \frac{\partial}{\partial\theta} \ln{f(\xi,\theta)} \right)^2 \right]} = \frac{1}{n\cdot\int_{-\infty}^{\infty} \left( \frac{\partial}{\partial\theta} \ln{f(x,\theta)} \right)^2 f(x,\theta) dx}$$

Liczbę $I_n^2$ nazywamy **informację Fiszera** i definiujemy wzorem:

$$I_{n}^2 =n\cdot \mathbb{E}\left[\left( \frac{\partial}{\partial\theta} \ln{f(\xi,\theta)} \right)^2\right]$$

możemy wykazać, że:

$$I_{n}^2=-n\cdot \mathbb{E}\left[\frac{\partial^2}{\partial\theta^2} \ln{f(\xi,\theta)}\right]$$

Z powyższych równości wynika, że jeżeli próbka jest skończona $n<\infty$, to prawa część nierówności Rao-Cramera zawsze jest dodatnia, więc zawsze $D^2 [\theta_n ]>0$, z czego z kolei wynika, że dla skończonej ilości pomiarów nigdy nie będzie 100% oszachowania parametru $\theta$.

## Estymatory średniej i wariancji
Estymatorem wartości $m$ nazywamy $\overline{x}$ daną wzorem:

$$\overline{x}=\frac{1}{n}\sum_{i=1}^nx_{i}$$

Estymatorami wartości $\sigma^2$ nazywamy statystyki:
- $s^2=\frac{1}{n}\sum_{i=1}^n (x_{i}-\overline{x})^2$
- $\hat{s}^2 \frac{1}{n-1}\sum_{i=1}^n (x_{i}-\overline{x})^2$
- $\tilde{s}^2=\frac{1}{n} \sum_{i=1}^n (x_{i}-m)^2$

Jeżeli $\mathbb{E}[\xi^2]<\infty$, to:
- statystyka $\overline{x}$ jest nieobciążonym i mocno zgodnym estymatorem parametru $m$, a statystyka $\hat{s}^2$ jest nieobciążonym i mocno zgodnym estymatorem parametru $\sigma^2$.
- statystyka $s^2$ jest asymptotycznie nieobciążonym i mocno zgodnym estymatorem parametru $\sigma^2$.

Jeżeli $\xi\in \mathcal{N}(m,\sigma^2)$ to estymator $\overline{x}$ jest efektywnym estymatorem dla parametru $m$:

$$\mathbb{E}[\overline{x}]=m, \qquad \mathbb{E}\left[\tilde{s}^2\right]=\sigma^2, \qquad \mathbb{E}\left[s^2\right]=\frac{n-1}{n}\sigma^2$$

Estymator wartości $\sigma^2$ spełnia własność: $s^2=\tilde{s}^2-(\overline{x}-m)^2$.

## Dystrybuanta empiryczna
Niech $x_1, \dots, x_n$ będzie próbą losową, a $\nu_n$ oznacza liczbę obserwacji w tej próbie, które są mniejsze od wartości $x$. Dystrybuantą empiryczną nazywamy statystykę $Q_n$, która jest estymatorem dystrybuanty teoretycznej $F(x) = P(\xi < x)$, i definiujemy ją wzorem:

$$Q_{n}=\frac{\nu_{n}}{n}$$

Niech $\mathbb{1}_A (x)$ oznacza funkcję wskaźnikową (innym oznaczeniem jest $\chi_A (x)$), definiujemy ją wzorem:

$$\mathbb{1}_{A}(x)=\begin{cases}
1, \quad x\in A \\
0, \quad x \notin A \\
\end{cases}$$

Możemy wtedy zapisać dystrybuantę empiryczną, jako:

$$Q_{n}=\frac{1}{n}\sum_{i=1}^n \mathbb{1}_{(-\infty,x)}(x_{i})$$

**Dystrybuanta empiryczna spełnia własności:**
- $P(\eta_i(x)=1) = F(x)$
- $P(\eta_i(x)=0) = 1-F(x)$
- $\mathbb{E}[\eta_i(x)] = F(x)$

Dystrybuanta empiryczna jest estymatorem dystrybuanty: $\mathbb{E}[Q_n (x)]=F(x)$, jej rozkład możemy znaleźć za pomocą wzoru:

$$P\left(Q_n = \frac{k}{n}\right) = \binom{n}{k} (F(x))^k (1-F(x))^{n-k}$$

## Twierdzenia

>[!danger] Twierdzenie Gliwenki-Cantellego
>
> $$P\left( \lim_{n \to \infty} \sup_{x\in(-\infty,\infty)} |Q_{n}(x)-F(x)| = 0 \right) = 1$$
>

>[!danger] Twierdzenie Kołmogorowa
>
> $$\lim_{n\to\infty} P \left( \sqrt{n} \cdot \sup_{x \in (-\infty, \infty)} |Q_n(x) - F(x)| < z \right) = K(z) = \sum_{i=-\infty}^{\infty} (-1)^i \cdot e^{-2i^2z^2}$$
>

Z twierdzenia Kołmogorowa możemy wywnioskować zbieżność asymptotyczną:

$$Q_n(x) = F(x) + \omicron\left( \frac{1}{\sqrt{n}} \right)$$

gdzie $\omicron$ to notacja małego $\omicron$. Oznacza to, że występuje błąd rzędu $\frac{1}{\sqrt{ n }}$.

