## Transformacja $\mathcal{Z}$-Laurenta
Transformacja $\mathcal{Z}$-Laurenta, zwana również transformacją $\mathcal{Z}$, pozwala na zamianę równań różnicowych na wyrażenia algebraiczne. Jest ona odpowiednikiem transformacji Laplace'a dla szeregów liczbowych.

Transformacja Laurenta zamienia dyskretny ciąg $a(n)$ na funkcję zespoloną $F(a)$. Ogólny wzór na transformację Z ciągu $a(n)$ wygląda następująco:
$$ \mathcal{Z}[a(n)] = \sum_{n=-\infty}^{\infty} a(n) \cdot z^{-n} $$
Najczęściej $a(n) = 0$ dla $n < 0$.

> [!example] Wyprowadzenie transformaty dla $\delta(n)$
> $$ \mathcal{Z}[\delta(n)] = \sum_{n=-\infty}^{\infty} \delta(n) \cdot z^{-n} = \dots + \frac{\delta(-1)}{z^{-1}} + \frac{\delta(0)}{z^0} + \frac{\delta(1)}{z^1} + \dots = \dots + 0 + 1 + 0 + \dots = 1 $$
## Tabela transformat $\mathcal{Z}$-Laurenta

| Ciąg                                          | Transformata $\mathcal{Z}$                                                         |
| :-------------------------------------------- | :--------------------------------------------------------------------------------- |
| $\sum_{n=-\infty}^{\infty} a(n) \cdot z^{-n}$ | $a(n)$                                                                             |
| $\delta(n)$                                   | $1$                                                                                |
| $\delta(n+k)$                                 | $\frac{1}{z^k}$                                                                    |
| $u(n)$                                        | $\frac{z}{z-1}$                                                                    |
| $\alpha$                                      | $\frac{\alpha}{z-1}$                                                               |
| $\alpha \cdot \beta^n$                        | $\frac{\alpha\beta}{z-\beta}$                                                      |
| $a(n+k)$                                      | $z^k \left(F(a) - a(0) - \frac{a(1)}{z^1} - \dots - \frac{a(k-1)}{z^{k-1}}\right)$ |
Transformata $\mathcal{Z}$ jest $\mathcal{Z}$: $$ \mathcal{Z}[\alpha \cdot a(n) + \beta \cdot b(n)] = \alpha \cdot \mathcal{Z}[a(n)] + \beta \cdot \mathcal{Z}[b(n)] $$
## Odwrotna transformacja $\mathcal{Z}$-Laurenta
Transformacja $\mathcal{Z}^{-1}$ jest transformacją odwrotną do transformacji Z-Laurenta: $\mathcal{Z}^{-1}[\mathcal{Z}[a(n)]] = a(n)$.

| Funkcja                                  | Ciąg $\mathcal{Z}^{-1}$                                            |
| :--------------------------------------- | :----------------------------------------------------------------- |
| $1$                                      | $\delta(n)$                                                        |
| $\frac{1}{z^k}$                          | $\delta(n+k)$                                                      |
| $\frac{z}{z-1}$                          | $u(n)$                                                             |
| $\alpha \cdot \frac{\beta}{z-\beta}$     | $\alpha \cdot \beta^n, \quad n \ge 1$                              |
| $\alpha \cdot \frac{\beta}{z+\beta}$     | $-\alpha \cdot (-\beta)^n, \quad n \ge 1$                          |
| $\alpha \cdot \frac{\beta}{(z-\beta)^2}$ | $\alpha \cdot \beta^n \cdot n, \quad n \ge 1$                      |
| $\alpha \cdot \frac{\beta}{(z-\beta)^p}$ | $\alpha \cdot \beta^n \cdot \frac{n^{p-1}}{(p-1)!}, \quad n \ge 1$ |

> [!example] Przykład obliczenia $a(n)$
> Oblicz $a(n)$ dla $\mathcal{Z}[a(n)] = \frac{3z}{z^2 + z - 2}$:
> $$ \mathcal{Z}[a(n)] = \frac{3z}{(z+2)(z-1)} = \frac{A}{z+2} + \frac{B}{z-1} = \frac{1}{z-1} + \frac{2}{z+2} = $$
> $$ = \frac{\frac{1}{z}}{1 - \frac{1}{z}} + (-1) \cdot \frac{\frac{-2}{z}}{1 - \left(\frac{-2}{z}\right)} = \sum_{n=1}^{\infty} \left(\frac{1}{z}\right)^n - 1 \cdot \sum_{n=1}^{\infty} \left(\frac{-2}{z}\right)^n \implies a(n) = 1 - 1 \cdot (-2)^n = 1 - (-2)^n $$