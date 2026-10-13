## Wykres ramka-wąsy
**Wykres ramka-wąsy** (ang. *boxplot*) przedstawia podstawowe charakterystyki rozkładu:
- Dolna krawędź ramki odpowiada $Q_1$.
- Górna krawędź ramki odpowiada $Q_3$.
- Linia wewnątrz ramki oznacza medianę $Q_{2}$.
- Wąsy sięgają do najbardziej ekstremalnych obserwacji znajdujących się wewnątrz granic Tukeya.
- Punkty poza wąsami oznaczają potencjalne obserwacje odstające.

```python
plt.boxplot(x)
plt.title("Ramka-wąsy")
plt.show()
```

## Histogram
**Histogram** przedstawia rozkład liczności obserwacji w określonych przedziałach wartości. Liczność $n_j$ przedziału $I_j$ można zapisać jako:

$$
n_j=\sum_{i=1}^{n}\mathbb{1}_{I_j}(x_i)
$$  

gdzie $\mathbb{1}_{I_j}$ jest funkcją wskaźnikową.

```python
plt.hist(x, bins=20)
plt.title("Histogram")
plt.show()
```

## Estymator gęstości KDE
**Estymacja jądrowa gęstości** (ang. *Kernel Density Estimation*) KDE pozwala otrzymać wygładzone przybliżenie funkcji gęstości prawdopodobieństwa.

Estymator definiujemy jako:

$$
\hat{f}_{h}(t)=
\frac{1}{nh}\sum_{i=1}^{n}
K\left(\frac{t-x_i}{h}\right)
$$  
gdzie:
- $K$ – funkcja jądra,
- $h>0$ – szerokość pasma (ang. *bandwidth*),
- $n$ – liczność próby.

Szerokość pasma kontroluje stopień wygładzenia:

- małe $h$ – więcej lokalnych szczegółów, ale większa wrażliwość na szum,
- duże $h$ – silniejsze wygładzenie, ale ryzyko ukrycia istotnych cech rozkładu.

```python
sns.kdeplot(x=x)
plt.title("Gęstość KDE")
plt.show()
```

## Porównanie z rozkładem teoretycznym
Dla rozkładu normalnego:

$$
f(t)=\frac{1}{\sigma\sqrt{2\pi}}\cdot e^{-\frac{(t-m)^2}{2\sigma^2}}
$$  
Możemy porównać histogram próby, estymator KDE oraz teoretyczną funkcję gęstości.

```python
t = np.linspace(x.min()-3, x.max()+3, 400)

plt.hist(x, bins=20, density=True)

sns.kdeplot(x=x, label="KDE")

plt.plot(
    t,
    stats.norm.pdf(t, mu, sigma),
    "r--",
    label="Rozkład normalny"
)

plt.legend()
plt.show()
```

## Wykres kwantylowy Q-Q
**Wykres Q-Q** (ang. *Quantile-Quantile Plot*) służy do porównywania kwantyli empirycznych z kwantylami rozkładu teoretycznego.

Pozwala ocenić, czy próba może pochodzić z określonego rozkładu.

Zaczynamy od porządkowania próby:

$$
x_{(1)}\leq x_{(2)}\leq\dots\leq x_{(n)}
$$  
Następnie każdej obserwacji przypisujemy poziom prawdopodobieństwa:

$$
p_i=\frac{i-\frac12}{n}
$$  
  
Dla rozkładu normalnego standardowego:

$$
q_i=\Phi^{-1}(p_i)
$$  
  
gdzie $\Phi$ jest dystrybuantą rozkładu $\mathcal{N}(0,1)$.

Rysujemy punkty:

$$
(q_i,x_{(i)})
$$  
  
Jeżeli próba pochodzi z rozkładu $\mathcal{N}(m,\sigma^2)$, to teoretyczne kwantyle spełniają:

$$
x_{(i)}\approx m+\sigma q_i
$$  
  
Punkty powinny więc układać się w przybliżeniu wzdłuż prostej.

```python
xs = np.sort(x)
p = (np.arange(1, n+1) - 0.5) / n
q = stats.norm.ppf(p)

plt.scatter(q, xs)
plt.plot(q, x.mean() + x.std(ddof=1) * q, "r")
plt.show()
```
Zamiast estymować prostą poprzez średnią i odchylenie standardowe, możemy wykorzystać kwartyle.

Dla rozkładu normalnego:

$$
b=\frac{Q_3-Q_1}
{\Phi^{-1}(0.75)-\Phi^{-1}(0.25)}
$$  
  
  

$$
a=Q_1-b\Phi^{-1}(0.25)
$$  
  

Otrzymujemy prostą:

$$
y=a+bq
$$  
  

```python
q1, q3 = np.percentile(x, [25, 75])

z1, z3 = stats.norm.ppf([0.25, 0.75])

slope = (q3 - q1) / (z3 - z1)

plt.scatter(q, xs)

plt.plot(q, q1 + slope*(q-z1), "b--")

plt.show()
```

## Dystrybuanta empiryczna
**Dystrybuantę empiryczną** (ang. *Empirical Cumulative Distribution Function*) ECDF definiujemy jako:

$$
F_n(t)=\frac{1}{n}\sum_{i=1}^{n}
\mathbb{1}_{{x_i\leq t}}
$$  
Funkcja określa odsetek obserwacji, których wartości nie przekraczają $t$.

```python
xs = np.sort(x)

plt.step(xs, np.arange(1, n+1)/n, where="post", label="ECDF")
plt.plot(t, stats.norm.cdf(t, mu, sigma), "r", label="Rozkład teoretyczny")
plt.legend()
plt.show()
```

## Wykres skrzypcowy
**Wykres skrzypcowy** (ang. *violin plot*) przedstawia oszacowanie gęstości rozkładu, często w połączeniu z podstawowymi statystykami opisowymi.

Pozwala zaobserwować cechy, które mogą być niewidoczne na wykresie ramka-wąsy, np. wielomodalność.

```python
sns.violinplot(y=x, inner="box")
sns.stripplot(y=x, color="k", alpha=0.25, size=3)
plt.show()
```

## Wykres rozrzutu
**Wykres rozrzutu** (ang. *scatter plot*) przedstawia pary obserwacji:

$$
(x_i,y_i),\quad i=1,\dots,n
$$
  
Służy do wizualnej oceny zależności między zmiennymi.
