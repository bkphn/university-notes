	## Sprzężenie zespolone
Dla dowolnej liczby zespolonej $z=a+bi$ sprzężeniem nazywamy liczbę $a-bi$, którą oznaczamy jako $\overline{z}$ bądź $z^\ast$. Możemy zauważyć, że:

$$z\cdot z^\ast=|z|^2=a^2+b^2$$

## Wektory kolumnowe
Dowolny wektor w dwuwymiarowej przestrzeni zespolonej zapisujemy jako:

$$\mathbf{v}=\begin{bmatrix}
v_{0}\\v_{1}
\end{bmatrix}, \qquad v_{0},v_{1}\in\mathbb{C}$$

W dwuwymiarowej przestrzeni możemy wyróżnić dwa wektory bazowe:

$$\mathbf{e}_{0}=\begin{bmatrix}
1 \\ 0
\end{bmatrix}, \qquad \mathbf{e}_{1}=\begin{bmatrix}
0 \\ 1
\end{bmatrix}$$

Dowolny wektor $\mathbf{v}=\begin{bmatrix}\alpha \\ \beta\end{bmatrix}$ w tej przestrzeni z bazą $\mathcal{B}=\{\mathbf{e}_{0},\mathbf{e}_{1}\}$ możemy rozłożyć do postaci:

$$\mathbf{v}=\alpha \mathbf{e}_{0}+\beta\mathbf{e}_{1}$$

## Notacja Diraca – Ket
W mechanice kwantowej wektor kolumnowy $\begin{bmatrix}\alpha \\ \beta\end{bmatrix}$ reprezentujemy jako $\ket{\psi}$.

$$\ket{\psi}\equiv \begin{bmatrix}
\alpha \\ \beta
\end{bmatrix} $$

**Ket** $\ket{\text{ }}$ oznacza wektor przestrzeni Hilberta. W wybranej bazie możemy reprezentować go jako wektor kolumnowy.

$$\ket{0}\equiv \begin{bmatrix}
1 \\ 0
\end{bmatrix}, \qquad \ket{1} = \begin{bmatrix}
0 \\ 1
\end{bmatrix}  $$

Dzięki temu stan ogólny, możemy przedstawić w postaci macierzowej:

$$\ket{\psi}=\alpha \ket{0}+\beta \ket{1}=\alpha \begin{bmatrix}
1 \\ 0
\end{bmatrix} + \beta \begin{bmatrix}
0 \\ 1
\end{bmatrix} =\begin{bmatrix}
 \alpha \\ \beta
\end{bmatrix}    $$

## Notacja Diraca – Bra
**Bra**, oznaczane symbolem $\bra{\text{ }}$ jest **sprzężeniem hermitowskim** ${\dagger}$ keta. Sprzężenie hermitowskie oznacza transpozycję oraz sprzężenie zespolone po współrzędnych wektora:

$$\ket{\psi}^{\dagger}=\begin{bmatrix}
\alpha \\ \beta
\end{bmatrix}^{\dagger}=\begin{bmatrix}
\alpha^\ast \\ \beta^\ast
\end{bmatrix}^T =\begin{bmatrix}
\alpha^\ast & \beta^\ast
\end{bmatrix}=\bra{\psi}  $$

>[!example] Przykład
>Dla ketu $\ket{\psi}=\begin{bmatrix} \frac{\sqrt{3}}{2} \\ \frac{i}{2} \end{bmatrix}$ bra liczymy następująco:
>
> $$\ket{\psi}^{\dagger}=\begin{bmatrix} \frac{\sqrt{3}}{2} \\ \frac{i}{2} \end{bmatrix}^{\dagger}=\begin{bmatrix} \left(\frac{\sqrt{3}}{2}\right)^\ast & \left(\frac{i}{2}\right)^\ast \end{bmatrix}=\begin{bmatrix}\frac{\sqrt{ 3 }}{2} & -\frac{i}{2}\end{bmatrix}=\bra{\psi}$$
>

Sprzężenie hermitowskie działa również na macierzach, dla dowolnej macierzy zespolonej $\mathbf{A}$:

$$\mathbf{A}^{\dagger}=\left(\mathbf{A^\ast}\right)^T$$

## Notacja Diraca – Braket
**Braketem** nazywamy iloczyn skalarny bra i keta. Dla $\ket{\psi}=\begin{bmatrix}\psi_{0} \\ \psi_{1}\end{bmatrix}$ oraz $\ket{\phi}=\begin{bmatrix}\phi_{0} \\ \phi_{1} \end{bmatrix}$ braket $\bra{\phi}\cdot\ket{\psi}$ oznaczamy skrótowo jako $\braket{\phi\vert\psi}$ i definiujemy następująco:

$$\braket{\phi\vert\psi}=\begin{bmatrix}
\phi^\ast_{0}&\phi^\ast_{1}\end{bmatrix} \cdot \begin{bmatrix}
 \psi_{0} \\ \psi_{1}
\end{bmatrix}=\phi_{0}^\ast\psi_{0}+\phi_{1}^\ast\psi_{1} $$

Wykorzystując braket możemy obliczyć normę ketu ze wzoru:

$$\|\psi\|=\sqrt{ \braket{\psi\vert\psi} }$$

## Ortogonalność i normalizacja
Wektor $\ket{\psi}$ jest znormalizowany, gdy:

$$\braket{\psi\vert\psi}=1$$

dowolny **stan fizyczny** musi być znormalizowany.

Dwa wektory $\ket{\phi},\ket{\psi}$ są ortogonalne, gdy:

$$\braket{\phi\vert\psi}=0$$

Jeżeli dwa wektory $\ket{\psi}, \ket{\phi}$ są **ortogonalne** i **znormalizowane** to tworzą **bazę ortonormalną** $\mathcal{B}$ dwuwymiarowej przestrzeni wektorowej.

>[!example] Sprawdź czy wektory $\ket{0},\ket{1}$ tworzą bazę ortonormalną.
>
>$$\braket{0\vert{1}}=\begin{bmatrix}
>1 \\ 0
>\end{bmatrix}^{\dagger}\begin{bmatrix}
>0 \\ 1
>\end{bmatrix}=\begin{bmatrix}
>1 & 0
>\end{bmatrix}\begin{bmatrix}
>0 \\ 1
>\end{bmatrix}=1\cdot{0}+0\cdot 1=0 $$
>
>$$\braket{1\vert{0}}=\begin{bmatrix}
> 0 \\ 1
>\end{bmatrix}^{\dagger} \begin{bmatrix}
>1 \\ 0
>\end{bmatrix}=\begin{bmatrix}
> 0 & 1
>\end{bmatrix} \begin{bmatrix}
> 1 \\ 0
>\end{bmatrix}=0\cdot{1}+1\cdot 0$$
>
> $$\braket{0\vert{0}}=1, \qquad \braket{1\vert 1}=1 $$

## Obliczanie prawdopodobieństwa
Niech $\ket{x}$ będzie znormalizowanym wektorem należącym do ortonormalnej bazy pomiarowej. Dla znormalizowanego stanu $\ket\phi$ prawdopodobieństwo otrzymania wyniku odpowiadającego $\ket{x}$ wynosi:

$$P(x)=|\braket{x\vert\phi}|^2$$

Dla kubitu $\ket{\psi}=\alpha \ket{0}+\beta \ket{1}$ otrzymujemy:

$$P(0)=|\braket{0\vert\psi}|^2=|\alpha|^2$$

$$P(1)=|\braket{1\vert\psi} |^2=|\beta|^2$$

## Operatory kwantowe
**Operatorem kwantowym** nazywamy pewny liniowy operator $K$, który w fizyce kwantowej często oznaczamy daszkiem $\hat{K}$:

$$\hat{K}:\mathcal{H}\rightarrow \mathcal{H}$$

Liniowość oznacza, że dla dowolnych wektorów $\ket{\psi},\ket{\phi}\in \mathcal{H}$ oraz skalarów $\alpha,\beta\in\mathbb{C}$ zachodzi:

$$\hat{K}(\alpha \ket{\psi}+\beta \ket{\phi} )=\alpha \hat{K}\ket{\psi}+\beta \hat{K}\ket{\phi}   $$

Każdy operator liniowy $\hat{K}$ w skończenie wymiarowej przestrzeni Hilberta można reprezentować za pomocą odpowiadającej mu macierzy $\mathbf{K}$. Jego działanie na wektor obliczamy przez mnożenie macierzy przez wektor współrzędnych.

Jeżeli na stan $\ket\psi$ najpierw działa operator $\hat{K}$, a następnie operator $\hat{L}$, otrzymujemy:

$$\hat{L}(\hat{K}\ket\psi)=(\hat{L}\hat{K})\ket\psi$$

Operator zapisany najbliżej ketu działa jako pierwszy. Na ogół mnożenie macierzy nie jest przemienne:
 
 $$\mathbf{LK}\neq \mathbf{KL}$$

Wśród najważniejszych operatorów kwantowych możemy wyróżnić:
- **Operator projekcji na stan $\ket{0}$**:

$$\hat{P}_{0}\ket{\psi} =\ket{0} \bra{0}\ket{\psi} =\begin{bmatrix}
1 & 0 \\ 0 & 0
\end{bmatrix}\ket{\psi}  $$

- **Operator projekcji na stan $\ket{1}$**:

$$\hat{P}_{1}\ket{\psi} =\ket{1} \bra{1}\ket{\psi} =\begin{bmatrix}
0 & 0 \\ 0 & 1
\end{bmatrix}\ket{\psi}  $$

- **Operator hermitowski**: Operator hermitowski $\hat{A}$ polega na mnożeniu przez macierz $\mathbf{A}$, która musi spełniać warunek:

$$\mathbf{A}^{\dagger}=\mathbf{A}$$

- **Operator unitarny**: Operator unitarny $\hat{U}$ polega na mnożeniu przez macierz $\mathbf{U}$, która musi spełniać:

$$\mathbf{U}^{\dagger}\mathbf{U}=\mathbf{U}\mathbf{U}^{\dagger}=\mathbf{I}$$


## Iloczyn tensorowy
**Iloczyn tensorowy** (ang. *tensor product*) to konstrukcja, która pozwala połączyć dwie przestrzenie wektorowe w nową przestrzeń wektorową, uwzględniając wszystkie kombinacje ich kierunków bazowych. Iloczyn tensorowy możemy wykonywać na:
- **Przestrzeniach wektorowych**: Dla dwóch przestrzeni $V,W$ ich iloczyn tensorowy oznaczamy jako $V\otimes W$, wymiar przestrzeni $V\otimes W$ wynosi:
  $$\dim(V\otimes W)=\dim V\cdot\dim W$$
  
  Dla baz $\mathcal{B}_{V}=\{\mathbf{v}_{1},\dots,\mathbf{v}_{n}\}$, $\mathcal{B}_{W}=\{\mathbf{w}_{1},\dots,\mathbf{w}_{m}\}$ baza przestrzeni $V\otimes W$ wynosi:

$$\mathcal{B}_{V\otimes W}=\{\mathbf{v}_{1}\otimes \mathbf{w}_{1},\dots,\mathbf{v}_{1}\otimes \mathbf{w}_{m},\dots,\mathbf{v}_{n}\otimes \mathbf{w}_{1},\dots,\mathbf{v}_{n}\otimes \mathbf{w}_{m} \}$$

- **Wektorach**: Dla dwóch wektorów $\mathbf{a}=(a_{0},\dots,a_{n}),\mathbf{b}=(b_{0},\dots,b_{m})$ ich iloczyn tensorowy definiujemy jako wektor wszystkich możliwych iloczynów ich współrzędnych.

$$\mathbf{a}\otimes\mathbf{b}=(a_{0}b_{0},\dots,a_{0}b_{m},\dots,a_{n}b_{0},\dots,a_{n}b_{m})$$

- **Macierzach**: Dla dwóch macierzy $\mathbf{A}=[a_{ij}], \mathbf{B}=[b_{ij}]$ iloczyn tensorowy definiujemy jako macierz wszystkich możliwych iloczynów ich wartości.

$$\mathbf{A}\otimes \mathbf{B}=[a_{ij}\cdot \mathbf{B}]$$

W przypadku wektorów i macierzy iloczyn tensorowy nazywamy **iloczynem Kroneckera**.

## Przestrzeń Hilberta
**Przestrzeń Hilberta** to zespolona przestrzeń wektorowa wyposażona w iloczyn skalarny i zupełna względem normy. W przypadku pojedynczego kubitu przestrzeń Hilberta $\mathcal{H}$ jest izomorficzna z $\mathbb{C}^2$:

$$\mathcal{H}\cong\mathbb{C}^2$$

Wśród najważniejszych własności przestrzeni Hilberta wyróżniamy:
- stany są znormalizowanymi wektorami,
- baza ortonormalna pozwala zapisać współrzędne stanu,
- iloczyn skalarny daje amplitudy projekcji,
- operatory liniowe działają na stany.

Dla dwóch przestrzeni $\mathcal{H}_{0},\mathcal{H}_{1}$, przestrzeń wspólna tych układów ma postać:

$$\mathcal{H}_{0,1}=\mathcal{H}_{0}\otimes \mathcal{H}_{1}$$
