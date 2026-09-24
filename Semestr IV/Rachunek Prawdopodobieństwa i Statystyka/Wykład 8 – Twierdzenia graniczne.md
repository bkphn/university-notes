## Prawa wielkich liczb
Przy dowolnym eksperymencie stochatycznym $S$ wyniki przy małej liczbie pomiarów mogą być niemiarodajne, dopiero przy bardzo dużej liczbie pomiarów dostajemy bliskie rzeczywistości wyniki. Podobna sytuacja zachodzi dla zmiennych losowych.

>[!danger] Słabe prawo wielkich liczb
>Dany jest ciąg niezależnych zmiennych losowych $\xi_n$ o jednakowym rozkładzie, dla których wartość oczekiwana wynosi $\mathbb{E}[\xi_i]=a$, wtedy dla średniej arytmetycznej ciągu $\bar{\xi}_n = \frac{1}{n} \sum_{i=1}^n \xi_i$ zachodzi:
> $$\overline{\xi}_n \xrightarrow[n \to \infty]{P} a$$

>[!danger] Silne prawo wielkich liczb
>Dany jest ciąg niezależnych zmiennych losowych $\xi_n$ o jednakowym rozkładzie, dla których wartość oczekiwana wynosi $\mathbb{E}[\xi_i]=a$, wtedy dla średniej arytmetycznej ciągu $\bar{\xi}_n = \frac{1}{n} \sum_{i=1}^n \xi_i$ zachodzi:
>$$\overline{\xi}_n \xrightarrow[n \to \infty]{\text{p.n.}} a$$
## Twierdzenia wielkich liczb
Przy stosowaniu praw wielkich liczb do wyznaczania wartości $a$ przydają się pewne twierdzenia, najczęściej stosowanymi są:

>[!danger] Twierdzenie Czebyszewa
> Niech $\xi_n$ będzie ciągiem niezależnych zmiennych losowych o wspólnej wartości oczekiwanej $\mathbb{E}[\xi_i]=a$, których wariancje są wspólnie ograniczone stałą, taką że $D^2[\xi_i] \le C$. Wtedy zachodzi: $$\frac{1}{n}\sum_{i=1}^n \xi_{i} \xrightarrow[n \to \infty]{P} a$$

>[!danger] Twierdzenie Bernoullego
> Niech w schemacie Bernoullego z prawdopodobieństwem sukcesu $p$ symbol $\nu_{n}$ oznacza liczbę sukcesów w $n$ doświadczeniach. Wtedy zachodzi: $$\frac{\nu_{n}}{n}\xrightarrow[n \to \infty]{P} p$$

>[!danger] Twierdzenie Kołmogorowa 
>Dane są niezależne zmienne losowe $\xi_n$ o jednakowym rozkładzie, posiadające skończoną wartość oczekiwaną $\mathbb{E}[\vert{}\xi_i\vert{}] < \infty$. Przyjmując $\mathbb{E}[\xi_i]=a$, zachodzi: $$\frac{1}{n} \sum_{i=1}^n \xi_{i} \xrightarrow[n \to \infty]{\text{p.n.}} a$$

## Centralne twierdzenie graniczne
Jeżeli $\xi_n$ jest ciągiem niezależnych zmiennych losowych o jednakowym rozkładzie $\mathbb{E}[\xi_n ]=a$ i $D^2 [\xi_{n}]=\sigma^2$, to: $$\lim_{ n \to \infty } P\left( \frac{\sum_{i=1}^n \xi_{i}-an}{\sqrt{n}\sigma} <x\right)=\Phi(x)=\frac{1}{\sqrt{ 2\pi }} \int_{-\infty}^x e^{-\frac{v^2}{2}} dv$$
>[!danger] Integralne twierdzenie Laplace'a-Moivre'a
> Jeżeli $\nu_{n}$ jest liczbą zajść zdarzenia $A$ przy $n$ doświadczeniach niezależnych, a $p$ oznacza prawdopodobieństwo jego zajścia w każdym doświadczeniu z osobna, $q=1−p$, to dla dowolnych $a<b$: $$\lim_{ n \to \infty } P\left( a < \frac{\nu_{n}-np}{\sqrt{ npq }} < b \right)=\frac{1}{\sqrt{ 2\pi }} \int_{a}^b e^{-\frac{v^2}{2}} dv$$

Z powyższego twierdzenia możemy wynzaczyć przybliżenie: $$P(a<\nu_{n}<b)\approx \Phi\left( \frac{b-np}{\sqrt{ npq }} \right) - \Phi\left( \frac{a-np}{\sqrt{ npq }} \right)$$
> [!danger] Lokalne twierdzenie Laplace'a-Moivre'a
> Dla $\lim_{\substack{n \to \infty \\ k \to \infty}} \frac{k-np}{\sqrt{npq}}=y$ zachodzi: $$\lim_{\substack{n \to \infty \\ k \to \infty}} \sqrt{npq}\cdot P(\nu_{n} = k) = \frac{1}{\sqrt{ 2\pi }} \cdot e ^{-\frac{y^2}{2}}$$

Tak samo jak w przypadku integralnego twierdzenia, z lokalnego także możemy wyznaczyć przybliżenie: $$P(\nu_{n}=k) \approx \frac{1}{\sqrt{ 2\pi npq }}\cdot e^{-\frac{(k-np)^2}{2npq}}$$
