## Dobry porządek
Porządek $<$ w zbiorze $X$ nazywamy **dobrym porządkiem**, jeżeli spełnia dwa warunki: jest liniowy oraz każdy niepusty podzbiór zbioru $X$ posiada element najmniejszy. 

Wtedy parę $(X,<)$ nazywamy zbiorem dobrze uporządkowanym.

**Przykłady:**
* $(\mathbb{N},\le)$ jest dobrze uporządkowany.
* $(\mathbb{Q},\le)$ nie jest dobrze uporządkowany.

**Aksjomat dobrego uporządkowania**: Każdy zbiór można dobrze uporządkować.

## Aksjomatyka Peano
W 1908 roku Giuseppe Peano przedstawił zestaw pięciu aksjomatów, za pomocą którego definiuje się liczby naturalne:

| Aksjomat | Zapis logiczny | Interpretacja |
| :--- | :--- | :--- |
| **1.** | $\varphi \in \mathbb{N}$ | Zbiór $\mathbb{N}$ zawiera element $\varphi$. |
| **2.** | $\forall_{n \in \mathbb{N}} \exists!_{S(n) \in \mathbb{N}}$ | Dla każdej liczby naturalnej $n$ istnieje dokładnie jedna liczba naturalna $S(n)$ zwana jej następnikiem. |
| **3.** | $\forall_{n \in \mathbb{N}} S(n) \ne \varphi$ | Element $\varphi$ nie jest następnikiem żadnej liczby naturalnej. |
| **4.** | $\forall_{n,m \in \mathbb{N}} n \ne m \Rightarrow S(n) \ne S(m)$ | Różne liczby naturalne mają różne następniki. |
| **5. Aksjomat indukcji** | $\forall_{A \subset \mathbb{N}} (\varphi \in A \wedge \forall_{n \in \mathbb{N}} n \in A \Rightarrow S(n) \in A) \Rightarrow A = \mathbb{N}$ | Niech $A$ będzie podzbiorem $\mathbb{N}$ zawierającym element $\varphi$. Jeżeli $A$ zawiera jakąś liczbę, to zawiera też jej następnik. Wówczas $A$ jest całym zbiorem $\mathbb{N}$. |

## Indukcja matematyczna
Indukcja matematyczna jest metodą dowodzenia twierdzeń, powstałą na podstawie aksjomatu indukcji.

> [!danger] Twierdzenie o indukcji matematycznej
> Dana jest własność $\phi(n)$ elementów zbioru $\mathbb{N}$. Jeżeli:
> - zdanie $\phi(1)$ jest prawdziwe,
> - zdanie $\forall_{n \in \mathbb{N}} \phi(n) \Rightarrow \phi(n+1)$ jest prawdziwe,
> 
> to własność $\phi(n)$ jest prawdziwa dla wszystkich liczb naturalnych $n$.

Dowody przeprowadzane tą metodą nazywamy dowodami indukcyjnymi.

> [!abstract] Schemat dowodu indukcyjnego
> 1. **Krok bazowy:** Sprawdzamy, że $\phi(1)$ jest prawdziwe.
> 2. **Krok indukcji:** 
> - **Założenie indukcji:** Zakładamy, że $\phi(n)$ jest prawdziwe dla $n \in \mathbb{N}$.
> - **Teza indukcji:** Stawiamy tezę, że $\phi(n+1)$ jest prawdziwe dla $n \in \mathbb{N}$.
> - **Dowód kroku indukcji:** Należy wykazać implikację $\phi(n) \Rightarrow \phi(n+1)$.

> [!example] Rozważmy własność: $\phi(n) \Leftrightarrow \left( \sum_{i=1}^{n} i = \frac{n(n+1)}{2} \right)$
> 
> **1. Krok bazowy:** Sprawdzamy prawdziwość dla $n=1$.
>
> $$\sum_{i=1}^{1} i = 1 \quad \text{oraz} \quad \frac{1(1+1)}{2} = \frac{2}{2} = 1$$
>
> **2. Krok indukcji:**
> **Założenie indukcyjne:** $\sum_{i=1}^{n} i = \frac{n(n+1)}{2}$
> **Teza indukcyjna:** $\sum_{i=1}^{n+1} i = \frac{(n+1)((n+1)+1)}{2} = \frac{(n+1)(n+2)}{2}$
> 
> **Dowód:** Należy wykazać, że $\phi(n) \Rightarrow \phi(n+1)$.
> Rozpisujemy lewą stronę ($L$) tezy, wyciągając ostatni wyraz i korzystając z założenia indukcyjnego:
>
> $$\begin{align*}
> L &= 1 + 2 + \dots + n + (n+1) \\
> &= \frac{n(n+1)}{2} + (n+1) \\
> &= \frac{n(n+1)}{2} + \frac{2(n+1)}{2} \\
> &= \frac{n(n+1) + 2(n+1)}{2} \\
> &= \frac{(n+1)(n+2)}{2} = P
> \end{align*} $$
>

