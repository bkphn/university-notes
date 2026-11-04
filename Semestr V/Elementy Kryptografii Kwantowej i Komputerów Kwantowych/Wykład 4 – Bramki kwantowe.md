## Bramki kwantowe
Bramką kwantową ${U}$ nazywamy operator działający na stan:

$$\ket{\psi'}={U}\ket{\psi}  $$

Dla jednego kubitu $U$ ma rozmiar $2\times{2}$. Obwód kwantowy jest uporządkowaną sekwencją takich operacji.

Dowolna bramka kwantowa musi spełniać warunek:

$${U}^{\dagger}U=UU^{\dagger}={I}$$

Zatem $U^{\dagger}=U^{-1}$. Unitarność zachowuje normę stanu:

$$\|U|\psi\rangle\|^2=\bra{\psi}U^{\dagger}U \ket{\psi}=\braket{\psi|\psi}=1  $$

## Obwody kwantowe

## Najważniejsze bramki kwantowe
Wśród najważniejszych bramek kwantowych możemy wyróżnić:
- **Bramka identyczności** $I$: 

$$I=\begin{bmatrix}
1&0\\0&1
\end{bmatrix}$$

$$I\begin{bmatrix}
\alpha\\\beta
\end{bmatrix}=\begin{bmatrix}
\alpha\\\beta
\end{bmatrix}$$

- **Bramka Pauliego** $X$: Odpowiednik negacji bitu. Na sferze Blocha odpowiada obrotowi o $\pi$ wokół osi $x$. Bramka Pauliego $X$ spełnia $X^2=I$.

$$X=\begin{bmatrix}
0&1\\1&0
\end{bmatrix}$$

$$X\begin{bmatrix}
\alpha\\\beta
\end{bmatrix}=\begin{bmatrix}
\beta\\\alpha
\end{bmatrix}$$

- **Bramka Pauliego** $Y$: Na sferze Blocha odpowiada obrotowi o $\pi$ wokół osi $y$.  Bramka Pauliego $Y$ spełnia $Y^2=I$.

$$Y=\begin{bmatrix}
0&-i\\ i&0
\end{bmatrix}$$

$$Y\begin{bmatrix}
\alpha\\\beta
\end{bmatrix}=\begin{bmatrix}
-i\beta\\ i\alpha
\end{bmatrix}$$

- **Bramka Pauliego** $Z$: Na sferze Blocha odpowiada obrotowi o $\pi$ wokół osi $z$.  Bramka Pauliego $Z$ spełnia $Z^2=I$.

$$Z=\begin{bmatrix}
1&0\\0&-1
\end{bmatrix}$$

$$Z\begin{bmatrix}
\alpha\\\beta
\end{bmatrix}=\begin{bmatrix}
\alpha\\-\beta
\end{bmatrix}$$

- **Bramka Hadamarda** $H$:

$$H=\begin{bmatrix}
\frac{1}{\sqrt{2}} & \frac{1}{\sqrt{ 2 }} \\
\frac{1}{\sqrt{ 2 }} & -\frac{1}{\sqrt{ 2 }}
\end{bmatrix}$$

$$H\begin{bmatrix}
\alpha\\\beta
\end{bmatrix}=\begin{bmatrix}
\frac{\alpha+\beta}{\sqrt{ 2 }} \\
\frac{\alpha-\beta}{\sqrt{ 2 }}
\end{bmatrix}$$

- **Bramka fazowa** $S$: Na sferze Blocha odpowiada obrotowi o $\frac{\pi}{2}$ wokół osi $z$ z dokładnością do fazy globalnej. Bramka fazowa $S$ spełnia $S^2=Z$.

$$S=\begin{bmatrix}
1&0\\0&i
\end{bmatrix}$$

$$S\begin{bmatrix}
\alpha\\\beta
\end{bmatrix}=\begin{bmatrix}
\alpha\\i\beta
\end{bmatrix}$$

- **Bramka fazowa** $T$: Na sferze Blocha odpowiada obrotowi o $\frac{\pi}{4}$ wokół osi $z$ z dokładnością do fazy globalnej. Bramka fazowa $T$ spełnia $T^2=S$.

$$T=\begin{bmatrix}
1&0\\0&e^{i\frac{\pi}{4}}
\end{bmatrix}$$

$$T\begin{bmatrix}
\alpha\\\beta
\end{bmatrix}=\begin{bmatrix}
\alpha \\
\frac{1+i}{\sqrt{ 2 }}\beta
\end{bmatrix}$$

- **Bramka obrotu** $R_{x}(\theta)$: Na sferze Blocha odpowiada obrotowi o kąt $\theta$ wokół osi $x$. Bramka obrotu $R_{x}(\theta)$ spełnia $R_{x}(\pi)=-iX$.

$$R_{x}(\theta)=\begin{bmatrix}
\cos \frac{\theta}{2}& -i \sin{\frac{\theta}{2}} \\
-i \sin \frac{\theta}{2} & \cos \frac{\theta}{2}
\end{bmatrix}$$

$${R_x(\theta) \begin{bmatrix} \alpha\\ \beta \end{bmatrix} = \begin{bmatrix} \alpha\cos\frac{\theta}{2}-i\beta\sin\frac{\theta}{2}\\ -i\alpha\sin\frac{\theta}{2}+\beta\cos\frac{\theta}{2} \end{bmatrix} }$$

- **Bramka obrotu** $R_{y}(\theta)$: Na sferze Blocha odpowiada obrotowi o kąt $\theta$ wokół osi $y$. Bramka obrotu $R_{y}(\theta)$ spełnia $R_{y}(\pi)=-iY$.

$$R_{y}(\theta)=\begin{bmatrix}
\cos{\frac{\theta}{2}}&-\sin{\frac{\theta}{2}} \\
\sin{\frac{\theta}{2}}&\cos{\frac{\theta}{2}}
\end{bmatrix}$$

$$R_y(\theta) \begin{bmatrix} \alpha\\ \beta \end{bmatrix} = \begin{bmatrix} \alpha\cos\frac{\theta}{2}-\beta\sin\frac{\theta}{2}\\ \alpha\sin\frac{\theta}{2}+\beta\cos\frac{\theta}{2} \end{bmatrix}$$

- **Bramka obrotu** $R_{x}(\theta)$: Na sferze Blocha odpowiada obrotowi o kąt $\theta$ wokół osi $x$. Bramka obrotu $R_{z}(\theta)$ spełnia $R_{z}(\pi)=-iZ$.

$$R_z(\theta)= \begin{bmatrix} e^{-i\frac{\theta}{2}} & 0\\ 0 & e^{i\frac{\theta}{2}} \end{bmatrix}$$

$$R_z(\theta) \begin{bmatrix} \alpha\\ \beta \end{bmatrix} = \begin{bmatrix} \alpha e^{-i\frac{\theta}{2}}\\ \beta e^{i\frac{\theta}{2}} \end{bmatrix}$$

## Operatory dla wielu kubitów
Dla dwóch kubitów mamy do czynienia z przestrzenią czterowymiarową. Jeżeli bramka $A$ działa na pierwszy kubit, a bramka $B$ na drugi kubit, to ich wspólny operator ma postać $A\otimes B$.

Macierz działająca na $n$ kubitów ma rozmiar $2^n\times {2}^n$.

## Bramki wielokubitowe
Wśród najpopularniejszych bramek wielokubitowych możemy wyróżnić:
- **Bramka CNOT** (*controlled not*):

$$\mathrm{CNOT}=\begin{bmatrix}
1&0&0&0\\
0&1&0&0\\
0&0&0&1\\
0&0&1&0
\end{bmatrix}$$

- **Bramka SWAP**:

$$\mathrm{SWAP}=\begin{bmatrix}
1&0&0&0\\
0&0&1&0\\
0&1&0&0\\
0&0&0&1
\end{bmatrix}$$

- **Bramka Toffolego**

