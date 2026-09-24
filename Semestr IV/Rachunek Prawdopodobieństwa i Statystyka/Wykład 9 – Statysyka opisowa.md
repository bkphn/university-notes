## Pomiary
Dana jest zmienna losowa $\xi$ taka, że $P(\xi<x)=F(x)$. Liczbę $\xi$ będziemy nazywać **populacją generalną**.

Przy wykonywaniu pomiarów należy pamiętać, że każdy z nich musi być niezależny od pozostałych, a także, że wszystkie należy wykonywać w tych samych warunkach. Dane, które uzyskamy z takich pomiarów możemy ułożyć w ciąg: $x_1,x_2,\dots,x_n$, który nazywamy **wartościami próby losowej**.

Zadaniem statystyki matematycznej jest wyznaczenie pewnych cech liczby $\xi$ na podstawie **próbek** $x_1,x_2,\dots,x_n$. Przykładem populacji generalnej $\xi$ może być wzrost wszystkich ludzi na ziemi, a próbą $x_1,\dots,x_n$ są wzrosty $n$ zmierzonych przez nas osób.

Statystyka opisowa zajmuje się wyciąganiem danych bez wykorzystywania zaawansowanych aparatów matematycznych.
## Elementy statystyki opisowej
Jeżeli próbę $x_1,\dots,x_n$ ułożymy w sposób taki, że: $$x_{(1)}\leq x_{(2)}\leq\dots\leq x_{(n)}$$to szereg ten nazywamy **szeregiem wariacyjnym**.

W statystyce opisowej najczęściej posługujemy się następującymi charakterystykami:
- **Średnia arytmetyczna**: Średnia arytmetyczna $\overline{x}$ odpowiada wartości oczekiwanej zmiennej losowej $\overline{x}\sim \mathbb{E}[\xi]$, definiujemy ja wzorem: $$\overline{x}=\frac{1}{n}\sum_{i=1}^n x_{i}$$
- **Wariancja**: Wariancją próby $x_1,\dots,x_n$ nazywamy liczbę $s^2$, która odpowiada wariancji zmiennej losowej $s^2  \sim D^2 [\xi]$, definiujemy ją wzorem: $$s^2=\frac{1}{n}\sum_{i=1}^n (x_{i}-\overline{x})^2$$
- **Odchylenie standardowe**: Odchyleniem standardowym próby $x_1,\dots,x_n$ nazywamy liczbę $s$, którą określamy wzorem: $$s=\sqrt{ s^2 }=\sqrt{ \frac{1}{n}  \sum_{i=1}^n (x_{i}-\overline{x})^2}$$ 
- **Kwantyle**: Kwantyl rzędu $p$ oznaczamy jako $k(p)$, gdzie $0\leq p\leq 1$ i definiujemy wzorem: $$k(p)=\min\left\{ x_{(k)} : \frac{k}{n} >p \right\}$$
- **Kwartyle**: Pierwszym kwartylem $Q_1$ nazywamy liczbę, która dzieli szereg wariacyjny (uporządkowany zbiór danych), w proporcjach $25\% :75\%$.
  
  Drugim kwartylem $Q_2$ nazywamy liczbę, która dzieli szereg wariacyjny w proporcjach $50\% :50\%$. 
  
  Trzecim kwartylem $Q_3$ nazywamy liczbę, która dzieli szereg wariacyjny w proporcjach $75\% :25\%$.

- **Odchylenie ćwiartkowe**: Odchyleniem ćwiartkowym nazywamy liczbę: $$Q=\frac{Q_{3}-Q_{1}}{2}$$
- **Mediana**: Medianą nazywamy drugi kwartyl i oznaczamy ją jako $\tilde{x}$ bądź $\text{Me}$: $$\tilde{x}=Q_{2}$$
- **Momenty**: Momentem rzędu $k$ nazywamy liczbę $m_k$, odpowiada ona wartości oczekiwanej $m_k  \sim \mathbb{E}[\xi^k ]$, definiujemy je wzorem: $$m_{k}=\frac{1}{n}\sum_{i=1}^n x_{i}^k$$
- **Momenty centralne**: Momentem centralnym rzędu $k$ nazywamy liczbę $\mu_k$, która jest odpowiednikiem $\mu_{k}\sim \mathbb{E}[(\xi-\mathbb{E}[\xi])^k]$, definiujemy je wzorem: $$\mu_{k}=\frac{1}{n}\sum_{i=1}^n (x_{i}-\overline{x})^k$$
- **Momenty centralne absolutne**: Momentem centralnym absolutnym rzędu $k$ nazywamy liczbę $\nu_{k}$: $$\nu_{k}=\frac{1}{n} \sum_{i=1}^n |x_{i}-\overline{x}|^k$$
- **Wskaźnik zmienności**: Wskaźnikiem zmienności zmiennej $\xi$ nazywamy liczbę $\gamma_{0}$: $$\gamma_{0}=\frac{\sigma}{|\overline{x}|}$$

- **Wskaźnik asymetrii**: Wskaźnikiem asymetrii zmiennej $\xi$ nazywamy liczbę $\gamma_1$: $$\gamma_{1}=\frac{\mu_{3}}{\sigma^3}$$
- **Wskaźnik skupienia**: Wskaźnikiem skupienia (kurtozą) z próby $x_1,\dots,x_n$ nazywamy liczbę $\gamma_2$: $$\gamma_{2}=\frac{\mu_{4}}{\sigma^4}$$
## Obszary zmienności
**Rozstępem** badanej cechy $\xi$ w próbie $x_{(1)}, x_{(2)}, \dots, x_{(n)}$ nazywamy liczbę $R$, daną wzorem: $$R=x_{(n)}-x_{(1)}$$
Przedziały $(\overline{x}-s, \overline{x}+s), (Q_{2}-Q, Q_{2}+Q)$ nazywamy **typowymi obszarami zmienności** cechy $\xi$.

Obszarem $K\sigma$ nazywamy przedział $(\overline{x}−Ks, \overline{x}+Ks)$. **Prawo trzech sigm** mówi, że:
- **Jeden sigma**: W przedziale $1\sigma=(\overline{x}−s, \overline{x}+s)$ mieści się $\sim68.3\%$ populacji.
- **Dwa sigma**: W przedziale $2\sigma=(\overline{x}−2s, \overline{x}+2s)$ mieści się $\sim95.5\%$ populacji.
- **Trzy sigma**: W przedziale $3\sigma=(\overline{x}−3s, \overline{x}+3s)$ mieści się $\sim99.7\%$ populacji.

W fizyce przy ogłaszaniu nowych zjawisk posługuje się właśnie obszarami zmienności. Jeżeli obserwacja mieści się tylko w przedziałach $1\sigma$, $2\sigma$ to prawdopodobieństwo, że sygnał jest tylko szumem informacyjnym jest zbyt wielkie.

Jeżeli obserwacja wpada w przedział $3\sigma$ to szansa, że sygnał jest przypadkowy wynosi $1 :1000$, obserwację taką uznaje się za silną poszlakę i pretekst do dalszych badań, jednak to wciąż za mało, by ogłosić odkrycie.

**Złotym standardem** odkrycia jest próg **$5\sigma$**. Oznacza to, że prawdopodobieństwo uzyskania tak ekstremalnego wyniku wyłącznie wskutek losowej fluktuacji tła wynosi około $1 : 3\,500\,000$. Dopiero osiągnięcie tego progu uprawnia do oficjalnego ogłoszenia odkrycia.
