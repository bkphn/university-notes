## Generowanie zmiennych skorelowanych
Rozważamy dwie zmienne losowe $\xi$ i $\eta$. **Korelacja** jest miarą siły i kierunku określonego rodzaju zależności statystycznej.

W celu uzyskania zmiennych o zadanej korelacji $\rho$ możemy wykorzystać konstrukcję:

$$
\eta=\mu_y+\sigma_y
\left(
\rho\xi^*+\sqrt{1-\rho^2}\varepsilon
\right)
$$  
gdzie:
- $\xi^*$ – zmienna $\xi$ po standaryzacji,
- $\varepsilon\sim \mathcal{N}(0,1)$ – niezależna zmienna losowa,
- $\rho\in[-1,1]$ – zadany współczynnik korelacji. 

Standaryzacja zmiennej losowej ma postać:

$$
\xi^*=\frac{\xi-\mathbb{E}[\xi]}{\sigma_\xi}
$$  
W laboratorium wykorzystujemy standaryzację na podstawie próby:

$$
x_i^*=\frac{x_i-\overline{x}}{s}
$$  
```python
rho = 0.7

xs_std = (df.x - df.x.mean()) / df.x.std(ddof=1)

df["y"] = 10 + 2 * (
    rho * xs_std +
    np.sqrt(1-rho**2) * rng.normal(size=n)
)

df["z"] = rng.normal(20, 4, n)

print(df.describe().round(3))
```

## Kowariancja
**Kowariancja** opisuje kierunek liniowej współzmienności dwóch zmiennych losowych.

$$
\mathrm{Cov}(\xi,\eta)=
\mathbb{E}\left[
(\xi-\mathbb{E}[\xi])
(\eta-\mathbb{E}[\eta])
\right]
$$

Dla próby:

$$
S_{xy}=
\frac{1}{n}
\sum_{i=1}^{n}
(x_i-\overline{x})(y_i-\overline{y})
$$ 
Wersja skorygowana:

$$
s_{xy}=
\frac{1}{n-1}
\sum_{i=1}^{n}
(x_i-\overline{x})(y_i-\overline{y})
$$ 
```python
cov = np.cov(df.x, df.y, ddof=1)
print(cov)
```

## Korelacja Pearsona
**Współczynnik korelacji Pearsona** jest miarą liniowej zależności dwóch zmiennych. Dla zmiennych losowych:

$$
\rho_{\xi\eta}=
\frac{\operatorname{Cov}(\xi,\eta)}
{\sigma_\xi\sigma_\eta}
$$  
Dla próby:

$$
r_{xy}=
\frac{
\sum_{i=1}^{n}
(x_i-\overline{x})(y_i-\overline{y})
}{
\sqrt{
\sum_{i=1}^{n}(x_i-\overline{x})^2
\sum_{i=1}^{n}(y_i-\overline{y})^2
}
}
$$

Zachodzi:

$$
-1\leq r_{xy}\leq 1
$$  
Interpretacja:
- $r_{xy}=1$ – doskonała dodatnia zależność liniowa,
- $r_{xy}=-1$ – doskonała ujemna zależność liniowa,
- $r_{xy}=0$ – brak korelacji liniowej.

```python
r = stats.pearsonr(df.x, df.y)

print(r.statistic)
print(r.pvalue)
print(r.confidence_interval())
```
Domyślnie testowana jest hipoteza:

$$
H_0:\rho_{\xi\eta}=0
$$ 
wobec:

$$
H_1:\rho_{\xi\eta}\neq 0
$$

Wartość $p$ określa prawdopodobieństwo uzyskania wyniku co najmniej tak ekstremalnego jak zaobserwowany, przy założeniu prawdziwości hipotezy zerowej i spełnienia założeń testu.

## Korelacja Spearmana
**Współczynnik korelacji Spearmana** jest miarą zależności monotonicznej. W odróżnieniu od korelacji Pearsona nie wymaga liniowej zależności pomiędzy zmiennymi.

Współczynnik Spearmana jest korelacją Pearsona obliczoną dla **rang obserwacji**. Jeżeli nie występują rangi wiązane, można wykorzystać wzór:

$$
r_s=
1-\frac{6\sum_{i=1}^{n}d_i^2}
{n(n^2-1)}
$$    

gdzie $d_i$ oznacza różnicę rang odpowiadających sobie obserwacji.

```python
r_s = stats.spearmanr(df.x, df.y)

print(r_s.statistic)
print(r_s.pvalue)
```
Współczynnik Spearmana jest odporniejszy na wpływ wartości ekstremalnych niż korelacja Pearsona, ale nie jest całkowicie niewrażliwy na obserwacje odstające.

## Korelacja Kendalla
**Współczynnik korelacji Kendalla** bazuje na zgodności uporządkowania par obserwacji.

Rozważmy dwie pary obserwacji:

$$
(x_i,y_i),\quad (x_j,y_j)
$$

Para jest:
- zgodna, jeśli $(x_i-x_j)(y_i-y_j)>0$,
- niezgodna, jeśli $(x_i-x_j)(y_i-y_j)<0$.

Przy braku remisów:
$$
\tau=
\frac{C-D}{\binom{n}{2}}
$$  
gdzie:
- $C$ – liczba par zgodnych,
- $D$ – liczba par niezgodnych.

W przypadku remisów stosuje się odpowiednie poprawki, np. współczynnik $\tau_b$.

```python
r_k = stats.kendalltau(df.x, df.y)

print(r_k.statistic)
print(r_k.pvalue)
```

## Macierz korelacji
Dla kilku zmiennych współczynniki korelacji zapisujemy w postaci macierzy:

$$
\mathbf{R} =
\begin{bmatrix}
1&r_{xy}&r_{xz}\\
r_{xy}&1&r_{yz}\\
r_{xz}&r_{yz}&1\\
\end{bmatrix}
$$  
  
  Macierz korelacji jest symetryczna, a na jej przekątnej znajdują się jedynki, o ile korelacje są zdefiniowane.

```python
print(df.corr())
print(df.corr(method="spearman"))
print(df.corr(method="kendall"))
```

Wizualizacja macierzy korelacji:
```python
sns.heatmap(
    df.corr(),
    annot=True,
    fmt=".2f",
    vmin=-1,
    vmax=1,
    cmap="RdBu_r"
)

plt.show()
```
## Zależność nieliniowa a korelacja
Brak korelacji liniowej nie oznacza braku zależności statystycznej. Rozważmy:

$$
\eta=(\xi-15)^2
$$  
Dla symetrycznego rozkładu zmiennej $\xi$ względem wartości $15$ zachodzi:

$$
\mathrm{Cov}(\xi,\eta)=0
$$ 
mimo że $\eta$ jest jednoznacznie wyznaczona przez $\xi$.
