## Dystrybuanta wektora
Funkcję $F_{\xi\eta} (x,y)=F(x,y)=P(\xi<x, \eta<y)$ nazywamy **dystrybuantą wektora losowego** $(\xi, \eta)$ albo dystrybuatną łączną zmiennych losowych $\xi,\eta$.

Będziemy mówić, że dytrybuanta łączna zmiennych losowych $\xi ,\eta$ jest typu **absolutnie ciągłego**, jeżeli możemy ją przedstawić w postaci: $$F(x,y)=\int_{-\infty}^x\int_{-\infty}^y f(v,u) dvdu$$
Funkcję $f(v,u)$ nazywamy **gęstością łączną** zmiennych losowych $\xi ,\eta$.

Gęstość łączną możemy wyznaczyć jako pochodną dystrybuanty: $$\frac{\partial^2F(x,y)}{\partial x\partial y}=f(x,y)$$
## Dystrybuanty brzegowe
Funkcje $F_\xi  (x)=P(\xi <x),  F_\eta  (x)=P(\eta <x)$ nazywamy **dystrybuantami brzegowymi** dla wektora $(\xi ,\eta )$. Przy czym zachodzi $F_\xi  (x)=F(x,\infty)$ oraz $F_\eta  (x)=F(\infty,x)$.

Jeśli dystrybuanta wektora losowego $(\xi ,\eta )$ jest typu absolutnie ciągłego o gęstości $f(x,y)$, to dystrybuanty brzegowe $F_\xi  (x), F_\eta  (x)$ są typu absolutnie ciągłego o gęstościach: $$f_{\xi}(x)=\int_{-\infty}^\infty f(x,y) dy,\qquad f_{\eta}(y)=\int_{-\infty}^\infty f(x,y) dx$$
Zmienne losowe $\xi ,\eta$ są niezależne, jeżeli spełniona jest równość: $$f(x,y)=f_{\xi}(x)f_{\eta}(y)$$
Jeśli rozkład wektora losowego $(\xi ,\eta )$ jest absolutnie ciągły z gęstością $f(x,y)$ to dla dowolnego zbioru $B\subseteq \mathbb{R}^2$ zachodzi: $$P((\xi,\eta)\in B)=\iint_{B} f(u,v) dvdu$$
## Dystrybuanta warunkowa
Funkcję $F(x \mid y)=P(\xi <x \mid \eta =y)$ nazywamy **dystrybuatną warunkową** zmiennej losowej $\xi$ względem $\eta$ . Dystrybuanta warunkowa dana jest wzorem: $$F(x\mid y)=\begin{cases}
\frac{\int_{-\infty}^x f(u,v)du}{f_\eta(y)},
\quad f_\eta(y)>0 \\
0, \qquad f_\eta(y)=0
\end{cases}$$
gdzie funkcja $f(x \mid y)$ jest gęstością warunkową dla $\xi$ przy warunku $\eta =y$, którą definiujemy wzorem: $$f(x\mid y)=\begin{cases}
\frac{f(x,y)}{f_\eta(y)}, \quad f_\eta(y)>0 \\
0, \qquad f_\eta(y)=0
\end{cases}$$

Dla zmiennych losowych $\xi ,\eta$ zachodzi równość: $$P(\xi\in A)=\int_{-\infty}^\infty P(\xi\in A \mid \eta=y)\cdot f_{\eta}(y) dy$$którą można zapisać jako: $$P(\xi<x)=\int_{-\infty}^\infty P(\xi<x \mid \eta=y) f_{\eta}(y)dy$$
## Suma zmiennych losowych
Niech funkcje $F_\xi  (x), F_\eta  (x)$ będą dystrybuantami niezależnych zmiennych losowych $\xi ,\eta$ o gęstościach $f_\xi  (x), f_\eta  (x)$. 

Aby wyznaczyć dystrybuatnę sumy $\xi +\eta$ możemy skorzystać z wzoru na dystrybuantę sumy: $$F_{\xi+\eta}(x)=\int_{-\infty}^\infty F_{\xi}(x-y)\cdot f_{n}(y) dy$$
na podstawie powyższego wzoru możemy wyznaczyć gęstość sumy $\xi+\eta$: $$f_{\xi+\eta}(x)=\int_{-\infty}^\infty f_{\xi}(x-y)f_{\eta}(y) dy$$
Sumę zmiennych losowych $\xi +\eta$ często oznacza się często jako $\zeta$.

Jeżeli $\xi ,\eta \in\mathbb{Z}$ to mówimy możemy zauważyć, że $\xi +\eta\in\mathbb{Z}$.
