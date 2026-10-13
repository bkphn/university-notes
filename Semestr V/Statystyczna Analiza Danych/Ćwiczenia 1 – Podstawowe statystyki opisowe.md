## Generowanie próby losowej
Dana jest zmienna losowa $\xi$ o rozkładzie normalnym:

$$
\xi\sim \mathcal{N}(m,\sigma^2)
$$

gdzie:
- $m\sim\mathbb{E}[\xi]$ – wartość oczekiwana,
- $\sigma\sim D[\xi]$ – odchylenie standardowe,
- $\sigma^2\sim D^2[\xi]$ – wariancja.

**Próbą losową** nazywamy ciąg niezależnych zmiennych losowych $\xi_1,\dots,\xi_n$ o jednakowym rozkładzie. Ich realizacjami są wartości $x_1,\dots,x_n$.

W przykładzie generujemy próbę o liczności $n=100$ pochodzącą z rozkładu:

$$
\xi\sim \mathcal{N}(15,9)
$$

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from scipy import stats

rng = np.random.default_rng(2026)

n, m, sigma = 100, 15, 3
x = rng.normal(m, sigma, n)

df = pd.DataFrame({"x": x})
print(df.head())
```

Funkcja `rng.normal(m, sigma, n)` – generuje `n` liczb z rozkładu normalnego o średniej `m` i odchyleniu standardowym `sigma`. Polecenie `pd.DataFrame()` tworzy tabelaryczną strukturę danych, natomiast `df.head()` zwraca pierwszych pięć wierszy.

## Podstawowe statystyki opisowe
Wśród podstawowych statystyk opisowych możemy wyróżnić:
- **Średnia arytmetyczna**: Średnią arytmetyczną próby $x_1,\dots,x_n$ nazywamy liczbę:
  $$ \overline{x}=\frac{1}{n}\sum_{i=1}^{n}x_i $$ 
  Średnia arytmetyczna jest estymatorem wartości oczekiwanej $\mathbb{E}[\xi]$. W Pythonie wywołujemy ją poleceniem `x.mean()`.

- **Wariancja**: W statystyce rozróżniamy dwa sposoby obliczania wariancji. Wariancja opisowa próby:

$$
S^2=\frac{1}{n}\sum_{i=1}^{n}(x_i-\overline{x})^2
$$  
  Wariancja nieobciążona:
  
  $$ s^2=\frac{1}{n-1}\sum_{i=1}^{n}(x_i-\overline{x})^2 $$ 
   W drugim przypadku wykorzystujemy poprawkę Bessela, polegającą na zastąpieniu mianownika $n$ przez $n-1$. Dzięki temu $s^2$ jest nieobciążonym estymatorem wariancji populacji, przy założeniu niezależnej próby o jednakowym rozkładzie i skończonej wariancji.
   
   W Pythonie wariancję wywołujemy poleceniem `x.var(ddof=0)` gdzie `ddof=0` oznacza wariancję próby, a `ddof=1` wariancję nieobciążoną.

- **Odchylenie standardowe**: Odchylenie standardowe to miara rozproszenia danych wokół ich średniej arytmetycznej. Podobnie jak wariancję rozróżniamy dwa rodzaje: odchylenie standardowe próby $S$ oraz nieobciążone $s$:
  $$ S=\sqrt{ S^2 } \qquad s=\sqrt{ s^2 }$$
  
  W języku Python implementujemy ją poleceniem `x.std(ddof=0)`, bądź `ddof=1` dla wariantu nieobciążonego.

- **Kwartyle**: Kwartyle dzielą uporządkowaną próbę na cztery części:
1. $Q_1$ – pierwszy kwartyl, odpowiadający poziomowi $25\%$,
2. $Q_2$ – drugi kwartyl, czyli mediana, odpowiadający poziomowi $50\%$,
3. $Q_3$ – trzeci kwartyl, odpowiadający poziomowi $75\%$.
   
- **Rozstęp międzykwartylowy** (ang. *interquartile range*) Rozstępem międzykwartylowym IQR nazywamy wartość $\mathrm{IQR}$ daną wzorem:
   $$ \mathrm{IQR}=Q_{3}-Q_{1}$$
   
   IQR jest miarą rozproszenia środkowych $50\%$ obserwacji. Kwartyle i rozstęp międzykwartylowy w Pythonie możemy wyznaczyć w następujący sposób:

``` python
median = np.median(x)

q1, q3 = np.percentile(x, [25, 75])

iqr = q3 - q1

print(median, q1, q3, iqr)
```

- **Rozstęp**: Rozstępem nazywamy różnicę pomiędzy największą i najmniejszą wartością próby:
  
  $$ R=x_{(n)}-x_{(1)} $$
  
- **Współczynnik zmienności** (ang. *Coefficient of Variation*): Współczynnik zmienności CV jest względną miarą rozproszenia. Współczynnik zmienności możemy obliczyć albo na podstawie wariancji opisowej próby, albo na podstawie nieobciążonej:
  
  $$ \gamma_{0}=\frac{S}{|\overline{x}|} \qquad \mathrm{CV}=\frac{s}{|\overline{x}|}$$

- **Momenty centralne**: Momentem centralnym rzędu $k$ nazywamy liczbę:
  
  $$ \mu_k=\frac{1}{n}\sum_{i=1}^{n}(x_i-\overline{x})^k $$

- **Współczynnik asymetrii**: Współczynnik asymetrii, inaczej skośność definiujemy jako:
  
  $$ \gamma_1=\frac{\mu_3}{S^3}=\frac{\mu_3}{\mu_2^{1.5}} $$
  
  Skośność możemy interpretować następująco:
  - $\gamma_1=0$ – brak asymetrii mierzonej trzecim momentem centralnym,
  - $\gamma_1>0$ – asymetria prawostronna,
  - $\gamma_1<0$ – asymetria lewostronna.
  
- **Kurtoza**: Współczynnik skupienia, inaczej kurtoza określamy jako:
  
  $$\gamma_2=\frac{\mu_4}{S^4}=\frac{\mu_4}{\mu_2^2}$$
  
- **Eksces**: Eksces, czyli kurtoza nadmiarowa dana jest wzorem:
  
  $$\mathrm{Excess}=\gamma_{2}-3$$

- **Mediana odchyleń bezwzględnych** (ang. *Median Absolute Deviation*): Mediana odchyleń bezwzględnych MAD jest określona wzorem: 
  
  $$ \mathrm{MAD}=\mathrm{Me}(\{|x_{i}-Q_{2}|:1\leq i\leq n\}) $$

- **Średnia ucięta**: Średnia ucięta polega na odrzuceniu określonej części najmniejszych i największych obserwacji przed obliczeniem średniej. W Pythonie do obliczenia średniej uciętej możemy wykorzystać polecenie `trim_mean(x, 0.1)`, gdzie `0.1` oznacza, że odrzucamy po $10\%$ z obu końców uporządkowanej próby.

- **Błąd standardowy średniej** (ang. *Standard Error*): Błąd standardowy średniej SE określa odchylenie standardowe rozkładu średniej z próby. 
  
  $$\mathrm{SE}(\overline{\xi})=\frac{\sigma}{\sqrt{n}}$$

- **Granice Tukeya**: Do identyfikacji potencjalnych obserwacji odstających wykorzystujemy granice Tukeya:
  
  $$ L=Q_{1}-1.5\cdot \mathrm{IQR} \qquad U=Q_{3}+1.5\cdot \mathrm{IQR}$$
  
  Obserwację uznajemy za potencjalnie odstającą, jeżeli:
  $$ x_i<L\quad\lor\quad x_i>U$$
