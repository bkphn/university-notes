## Funkcja Ackermanna
Funkcja Ackermanna odkryta przez Wilhelma Ackermanna w 1928 roku jest przykładem funkcji o bardzo szybkim wzroście. Jest to funkcja dwuargumentowa $A :\mathbb{N}^2\rightarrow\mathbb{Z}$, którą definiujemy następująco:

$$A(m,n)=\begin{cases}
n+1, \qquad m=0 \\
A(m-1, 1), \quad n=0 \\
A(m-1,A(m,n-1)), \quad m,n>0
\end{cases}$$

Dla małych $m$ funkcja ta przybiera wartości:
- $A(1, n)=n+2$
- $A(2,n)=3+2n$
- $A(3,n)=2^{n+3}−3$

Początkowe wartości funkcji Ackermanna $A$ umieszczono w poniższej tabeli:

| **$m, n$** | **0**    | **1**          | **2**           | **3**                 | $\dots$ | **$n$**                                          |
| :--------- | :------- | :------------- | :-------------- | :-------------------- | :------ | :----------------------------------------------- |
| **0**      | $1$      | $2$            | $3$             | $4$                   | $\dots$ | $n + 1$                                          |
| **1**      | $2$      | $3$            | $4$             | $5$                   | $\dots$ | $2 + (n + 3) - 3$                                |
| **2**      | $3$      | $5$            | $7$             | $9$                   | $\dots$ | $2 \cdot (n + 3) - 3$                            |
| **3**      | $5$      | $13$           | $29$            | $61$                  | $\dots$ | $2 \uparrow (n + 3) - 3$                         |
| **4**      | $13$     | $65533$        | $2^{65533} - 3$ | $A(3, 2^{65533} - 3)$ | $\dots$ | $2 \uparrow\uparrow (n + 3) - 3$                 |
| **5**      | $65533$  | $A(4, 65533)$  | $A(4, A(5,1))$  | $A(4, A(5,2))$        | $\dots$ | $2 \uparrow\uparrow\uparrow (n + 3) - 3$         |
| **6**      | $A(5,1)$ | $A(5, A(5,1))$ | $A(5, A(6,1))$  | $A(5, A(6,2))$        | $\dots$ | $2 \uparrow\uparrow\uparrow\uparrow (n + 3) - 3$ |

## Złota proporcja
Złotym podziałem nazywamy podział odcinka na dwie części tak, by stosunek długości dłuższej z nich do krótszej, był taki sam jak całego odcinka do dłuższej:

$$\frac{a+b}{a}=\frac{a}{b}$$

Stosunek ten jest równy $\frac{1+\sqrt{5}}{2}=1.6180339887…$ . Liczbę tę nazywamy złotą proporcją i oznaczamy jako $\varphi$.

## Złote ciągi
Złotymi ciągami nazywamy dowolny ciąg rekurencyjny, dany wzorem:

$$φ_{n}=\begin{cases}
\varphi_{0}, \qquad n=0\\
\varphi_{1}, \qquad n=1\\
\varphi_{n-1}+\varphi_{n-2}, \quad n>1
\end{cases}$$

niezależnie od jego wyrazów początkowych $\varphi_{0}, \varphi_{1}$. Najpopularniejszym złotym ciągiem jest tzw. ciąg Fibonacciego.

Granica ilorazu kolejnych wyrazów dowolnego złotego ciągu zawsze zbiega do złotej proporcji $\varphi$.

$$\lim_{ n \to \infty } \frac{\varphi_{n+1}}{\varphi_{n}}=\varphi$$

