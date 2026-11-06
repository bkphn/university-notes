## Bramki kwantowe
Bramką kwantową ${U}$ nazywamy operator działający na stan:

$$\ket{\psi'}={U}\ket{\psi}$$

Dla jednego kubitu $U$ ma rozmiar $2\times{2}$. Obwód kwantowy jest uporządkowaną sekwencją takich operacji.

Dowolna bramka kwantowa musi spełniać warunek:

$${U}^{\dagger}U=UU^{\dagger}={I}$$

Zatem $U^{\dagger}=U^{-1}$. Unitarność zachowuje normę stanu:

$$\|U|\psi\rangle\|^2=\bra{\psi}U^{\dagger}U \ket{\psi}=\braket{\psi|\psi}=1$$

## Obwody kwantowe
**Obwód kwantowy** (ang. *quantum circuit*) to model obliczeń kwantowych, w którym operacje na kubitach przedstawiamy jako sekwencję bramek kwantowych i pomiarów.

Można go traktować jako kwantowy odpowiednik obwodu logicznego znanego z klasycznej informatyki. Zamiast operować na bitach przyjmujących wartości $0$ lub $1$, obwód kwantowy przekształca stany kwantowe kubitów.

Obwód kwantowy możemy przedstawiać matematycznie:

$$\ket{\psi_{\text{out}}}=ZH\ket{0}$$

lub graficznie:
![[Pasted image 20261104202051.png|309]]
Symbol umieszczony na końcu obwodu oznacza **pomiar**. W obu przypadkach podany obwód interpretujemy następująco:
1. Na wejściu przyjmujemy stan $\ket{0}$.
2. Przepuszczamy go przez bramkę $H$ otrzymując $H\ket{0}$.
3. Stan $H\ket{0}$ przepuszczamy przez bramkę $Z$ otrzymując $ZH\ket{0}$.
4. Dokonujemy pomiaru odczytując stan $\ket{\psi_{\text{out}}}$.

## Najważniejsze bramki kwantowe
Wśród najważniejszych bramek kwantowych możemy wyróżnić:
- **Bramka identyczności** $I$: Nie zmienia stanu. Jest neutralnym elementem mnożenia operatorów.

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

- **Bramka Hadamarda** $H$: Łączy bazę obliczeniową $Z$ z bazą $X$. Dla bramki Hadamarda zachodzi $H\ket{0}=\ket{+},H\ket{1}=\ket{-}$ oraz $H\ket{+}=\ket{0},H\ket{-}=\ket{1}$.

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

- **Bramka obrotu** $R_{z}(\theta)$: Na sferze Blocha odpowiada obrotowi o kąt $\theta$ wokół osi $z$. Bramka obrotu $R_{z}(\theta)$ spełnia $R_{z}(\pi)=-iZ$.

$$R_z(\theta)= \begin{bmatrix} e^{-i\frac{\theta}{2}} & 0\\ 0 & e^{i\frac{\theta}{2}} \end{bmatrix}$$

$$R_z(\theta) \begin{bmatrix} \alpha\\ \beta \end{bmatrix} = \begin{bmatrix} \alpha e^{-i\frac{\theta}{2}}\\ \beta e^{i\frac{\theta}{2}} \end{bmatrix}$$

>[!example] Przykład obliczeniowy dla $HTH\ket{0}$
>$$HTH\ket{0}=HTH\begin{bmatrix}
>1\\0
>\end{bmatrix}=HT\begin{bmatrix}
\frac{1}{\sqrt{ 2 }} \\ \frac{1}{\sqrt{ 2 }}
>\end{bmatrix}=H\begin{bmatrix}
\frac{1}{\sqrt{ 2 }} \\ \frac{1+i}{\sqrt{ 2 }}
>\end{bmatrix}=\begin{bmatrix}
\frac{\frac{1}{\sqrt{ 2 }}+\frac{1+i}{2}}{\sqrt{ 2 }} \\
\frac{{\frac{1}{\sqrt{ 2 }}-\frac{1+i}{2}}}{\sqrt{ 2 }}
>\end{bmatrix}=\begin{bmatrix}
\frac{{\sqrt{ 2 }+1+i}}{2\sqrt{ 2 }} \\ 
\frac{\sqrt{ 2 }-1-i}{2\sqrt{ 2 }}
>\end{bmatrix}$$

## Operatory dla wielu kubitów
Dla dwóch kubitów mamy do czynienia z przestrzenią czterowymiarową. Jeżeli bramka $A$ działa na pierwszy kubit, a bramka $B$ na drugi kubit, to ich wspólny operator ma postać $A\otimes B$.

$$(A\otimes B)\ket{\psi\phi}=A\ket{\psi}\otimes B\ket{\phi}$$

Macierz działająca na $n$ kubitów ma rozmiar $2^n\times {2}^n$.

## Bramki wielokubitowe
Wśród najpopularniejszych bramek wielokubitowych możemy wyróżnić:
- **Bramka CNOT** (*controlled not*): Pierwszy kubit jest sterujący, a drugi docelowy. Bramka CNOT zmienia wartość kubitu docelowego, jeżeli sterujący ma wartość $1$. Dla $b_{1},b_{2}\in\{0,1\}$ zachodzi $\mathrm{CNOT}\ket{b_{1},b_{2}}=\ket{b_{1},b_{1}+_{2}b_{2}}$.

$$\mathrm{CNOT}=\begin{bmatrix}
1&0&0&0\\
0&1&0&0\\
0&0&0&1\\
0&0&1&0
\end{bmatrix}$$

$$\mathrm{CNOT}\begin{bmatrix}
\alpha_\psi\alpha_{\phi}\\\alpha_{\psi}\beta_{\phi}\\
\beta_{\psi}\alpha_{\phi}\\\beta_{\psi}\beta_{\phi}
\end{bmatrix}=\begin{bmatrix}
\alpha_{\psi}\alpha_{\phi}\\\alpha_{\psi}\beta_{\phi}\\
\beta_{\psi}\beta_{\phi} \\
\beta_{\psi}\alpha_{\phi}
\end{bmatrix}$$

- **Bramka SWAP**: Bramka SWAP polega na zamianie miejscami stanów obu kubitów $\mathrm{SWAP}\ket{\psi\phi}=\ket{\phi\psi}$.

$$\mathrm{SWAP}=\begin{bmatrix}
1&0&0&0\\
0&0&1&0\\
0&1&0&0\\
0&0&0&1
\end{bmatrix}$$

$$\mathrm{SWAP}\begin{bmatrix}
\alpha_\psi\alpha_{\phi}\\\alpha_{\psi}\beta_{\phi}\\
\beta_{\psi}\alpha_{\phi}\\\beta_{\psi}\beta_{\phi}
\end{bmatrix}=\begin{bmatrix}
\alpha_{\psi}\alpha_{\phi}\\
\beta_{\psi}\alpha_{\phi}\\\alpha_{\psi}\beta_{\phi}\\
\beta_\psi\beta_{\phi}\\\end{bmatrix}$$

- **Bramka Toffoliego** $\mathrm{CCNOT}$: W bramce Toffoliego mamy dwa kubity sterujące oraz jeden docelowy. Tylko jeżeli dwa pierwsze mają stan $\ket{1}$, to zamieniamy ostatni.

$$\mathrm{CCNOT}=\begin{bmatrix}1&0&0&0&0&0&0&0\\0&1&0&0&0&0&0&0\\0&0&1&0&0&0&0&0\\0&0&0&1&0&0&0&0\\0&0&0&0&1&0&0&0\\0&0&0&0&0&1&0&0\\0&0&0&0&0&0&0&1\\0&0&0&0&0&0&1&0\\\end{bmatrix}$$

$$\mathrm{CCNOT}\begin{bmatrix} \alpha_\psi\alpha_\phi\alpha_\gamma\\ \alpha_\psi\alpha_\phi\beta_\gamma\\ \alpha_\psi\beta_\phi\alpha_\gamma\\ \alpha_\psi\beta_\phi\beta_\gamma\\ \beta_\psi\alpha_\phi\alpha_\gamma\\ \beta_\psi\alpha_\phi\beta_\gamma\\ \beta_\psi\beta_\phi\alpha_\gamma\\ \beta_\psi\beta_\phi\beta_\gamma \end{bmatrix}=
\begin{bmatrix}
\alpha_\psi\alpha_\phi\alpha_\gamma\\
\alpha_\psi\alpha_\phi\beta_\gamma\\
\alpha_\psi\beta_\phi\alpha_\gamma\\
\alpha_\psi\beta_\phi\beta_\gamma\\
\beta_\psi\alpha_\phi\alpha_\gamma\\
\beta_\psi\alpha_\phi\beta_\gamma\\
\beta_\psi\beta_\phi\beta_\gamma\\
\beta_\psi\beta_\phi\alpha_\gamma
\end{bmatrix}$$

## Tworzenie stanów Bella
Niech wejście wynosi 

$$\ket{+}\otimes \ket{0}=\frac{1}{\sqrt{ 2 }}\ket{00}+\frac{1}{\sqrt{ 2 }}\ket{10}$$

Spróbujmy uruchomić bramkę CNOT:

$$\mathrm{CNOT}(\ket{+,0} )=\frac{1}{\sqrt{ 2 }}\ket{00}+\frac{1}{\sqrt{ 2 }}\ket{11}=\ket{\Phi^+}$$

Przepuśliśmy więc niesplątany stan przez bramkę CNOT, a na wyjściu otrzymujemy stan splątany – właśnie takie mechanizmy pozwalają nam na splątywanie kubitów.

Dlaczego wynik jest splątany? Załóżmy, że 

$$\frac{1}{\sqrt{ 2 }}\ket{00}+\frac{1}{\sqrt{ 2 }}\ket{11}=\big(\alpha_{\psi} \ket{0}+\beta_{\psi} \ket{1}  \big)\otimes \big(\alpha_{\phi} \ket{0} +\beta_{\phi} \ket{1} \big)$$

Prawa strona daje:

$$α_{\psi}\alpha_{\phi}\ket{00}+\alpha_{\psi}\beta_{\phi}\ket{01}+\beta_{\psi}\alpha_{\phi}\ket{10}+\beta_{\psi}\beta_{\phi}\ket{11}$$

Musiałoby zachodzić:

$$\alpha_{\psi}\alpha_{\phi}=\beta_{\psi}\beta_{\phi}=\frac{1}{\sqrt{ 2 }} \land \alpha_{\psi}\beta_{\phi}=\beta_{\psi}\alpha_{\phi}=0$$

Nie istnieją liczby $\alpha_{\psi},\beta_{\psi},\alpha_{\phi},\beta_{\phi}$ spełniające te warunki, więc stanu nie można rozdzielić na dwa niezależne kubity.

## Bramki odwrotne
W poniższej tabeli wypisano bramki odwrotne dla podstawowych bramek kwantowych.

| $A$             | $A^{-1}$        |
| --------------- | --------------- |
| $I$             | $I$             |
| $X$             | $X$             |
| $Y$             | $Y$             |
| $Z$             | $Z$             |
| $H$             | $H$             |
| $S$             | $S^{\dagger}$   |
| $T$             | $T^{\dagger}$   |
| $\mathrm{CNOT}$ | $\mathrm{CNOT}$ |
