## Szereg potęgowy
Szereg $\sum_{n=1}^{\infty} a_n \cdot (x - x_0)^n$ nazywamy **szeregiem potęgowym** o środku w punkcie $x_0$.

> [!example] Przykład badania zbieżności
> Zbadaj zbieżność szeregu $\sum_{n=1}^{\infty} r^n \cdot \frac{1}{n!} = \sum_{n=1}^{\infty} \frac{r^n}{n!}$.
> Stosując kryterium Cauchy'ego:
>
> $$\lim_{n \to \infty} \sqrt[n]{\frac{r^n}{n!}} = \lim_{n \to \infty} \frac{r}{\sqrt[n]{n!}} = \left[\frac{r}{\infty}\right] = 0 < 1$$
>
> Szereg jest zbieżny.

## Koło zbieżności
Dla dowolnego $a_n \in \mathbb{C}$, $n \in \mathbb{N}$ szereg $\sum_{n=1}^{\infty} a_n z^n$ jest zbieżny bezwzględnie w kole $\{z : |z| < R\}$, gdzie:

$$R = \left(\lim_{n \to \infty} \sqrt[n]{|a_n|}\right)^{-1}$$

Oznacza to, że dla wszystkich $x \in \{z : |z| < R\}$ szereg $\sum_{n=1}^{\infty} a_n \cdot x^n$ jest zbieżny bezwzględnie, rozbieżny dla $x \in \{z : |z| > R\}$, a dla $x \in \{z : |z| = R\}$ zbieżność może być różna. 

Wewnątrz koła zbieżności (czyli jeżeli szereg jest zbieżny) zachodzi równość:

$$\left(\sum_{n=0}^{\infty} a_n \cdot z^n\right)' = \sum_{n=0}^{\infty} (a_n \cdot z^n)'$$

### Wyznaczanie promienia za pomocą równości asymptotycznej
Dla dwóch dowolnych ciągów $a_n, b_n$ takich, że $a_n \sim b_n$, prawdziwa jest równość:

$$a_n \sim b_n \implies \lim_{n \to \infty} \sqrt[n]{|a_n|} = \lim_{n \to \infty} \sqrt[n]{|b_n|}$$

Fakt ten pozwala na łatwiejsze wyznaczanie promienia zbieżności, korzystając z kryterium Cauchy'ego.

## Uogólnione szeregi potęgowe (Szereg Laurenta)
Uogólnionym szeregiem potęgowym nazywamy sumę ciągu rozciągniętego do wyrazów ujemnych, czyli $n \in \mathbb{Z}$:

$$\sum_{n=-\infty}^{\infty} a_n z^n = \dots + a_{-1}z^{-1} + a_0 + a_1z^1 + \dots$$

Szereg $\sum_{n=0}^{\infty} (a_n \cdot z)^n$ jest zbieżny bezwzględnie wtedy i tylko wtedy, gdy $|a_n \cdot z| < 1$.

## Funkcje dyskretne
Funkcją dyskretną nazywamy funkcję, która nie jest określona dla wszystkich liczb, tylko dla określonego przeliczanego zbioru (np. liczby całkowite, naturalne):

$$f : T \cdot \mathbb{Z} \to \mathbb{R}$$

Funkcję dyskretną nazywamy inaczej funkcją impulsową. Wyróżniamy m.in.:
* **Delta Kroneckera:** Działa podobnie do macierzowego odpowiednika tej funkcji, z tym że zamiast dwóch wartości $i, j$ przyjmuje jedną i przyrównuje ją do zera:

  $$\delta(n) = \delta_{n,0} = \begin{cases} 1, & n = 0 \\ 0, & n \neq 0 \end{cases}$$

* **Funkcja skokowa Heaviside'a:** Odpowiednikiem dyskretnym funkcji wskaźnikowej jest funkcja skokowa Heaviside'a $u(n)$:

  $$u(n) = \begin{cases} 1, & n \ge 0 \\ 0, & n < 0 \end{cases}$$

