## Definicja Całki
Niech $F'(x) = f(x)$ dla $x \in (a, b)$. Wówczas funkcję $F$ nazywamy **funkcją pierwotną** funkcji $f$.

Funkcji pierwotnych jest nieskończenie wiele (różnią się o stałą $C$). Zbiór wszystkich funkcji pierwotnych nazywamy **całką nieoznaczoną** i zapisujemy jako $$\int f(x) dx$$
Tabela najważniejszych całek:

| Funkcja                  | Całka                     |
| :----------------------- | :------------------------ |
| $x^n$ ($n \ne -1$)       | $\frac{x^{n+1}}{n+1} + c$ |
| $x^{-1}$                 | $\ln                      |
| $a^x$                    | $\frac{a^x}{\ln a} + c$   |
| $e^x$                    | $e^x + c$                 |
| $\sin x$                 | $-\cos x + c$             |
| $\cos x$                 | $\sin x + c$              |
| $\frac{1}{\sin^2 x}$     | $-\cot x + c$             |
| $\frac{1}{\cos^2 x}$     | $\tan x + c$              |
| $\frac{1}{1+x^2}$        | $\arctan x + c$           |
| $\frac{1}{\sqrt{1-x^2}}$ | $\arcsin x + c$           |
## Metody całkowania
**Całkowanie przez części:**
Jeżeli funkcje $u, v$ mają ciągłe pochodne $u', v'$, to stosujemy wzór:
$$ \int (u \cdot v') dx = u \cdot v - \int (u' \cdot v) dx $$

**Całkowanie przez podstawienie:**
Jeżeli $\phi, \phi'$ są ciągłe, to: $$ \int \phi(x) \cdot \phi'(x) dx =\left| \begin{matrix}
t=\phi(x) \\dt=\phi'(x) dx
\end{matrix}\right|= \int t \, dt $$