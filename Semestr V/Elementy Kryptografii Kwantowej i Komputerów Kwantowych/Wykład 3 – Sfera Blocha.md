## Faza globalna
Dany jest stan kubitu $\ket{\psi}=\alpha \ket{0}+\beta \ket{1}$, możemy pomnożyć cały stan przez skalar $e^{i\gamma}$, który nazywamy **fazą globalną**. Amplitudy $\alpha', \beta'$ stanu się zmieniają, ale ich moduły pozostają niezmienne.

$$e^{i\gamma}\ket{\psi} =e^{i\gamma}\alpha\ket{0}+e^{i\gamma}\beta \ket{1}=\alpha'\ket{0}+\beta'\ket{1}  $$

Dla dowolnego stanu pomiarowego $\ket{m}$:

$$\braket{m|\psi'}=\bra{m}e^{i\gamma}\ket{\psi}=e^{i\gamma}\braket{m|\psi}$$

stany $\ket{\psi}$ oraz $\ket{\psi'}$ opisują ten sam stan fizyczny, z tego powodu faza globalna może być pomijana przy obliczeniach.

**Faza względna** to różnica faz amplitud dwóch składowych superpozycji. W przeciwieństwie do fazy globalnej może wpływać na interferencję oraz prawdopodobieństwa pomiarów wykonywanych w innych bazach.

## Parametryzacja kubitu
Po usunięciu nieobserwowalnej fazy globalnej każdy czysty stan kubitu $\ket{\psi}$ możemy zapisać w postaci:

$$\ket{\psi}=\cos \frac{\theta}{2}\ket{0}+e^{i\varphi}\sin \frac{\theta}{2}\ket{1}$$

gdzie: $0\leq\theta\leq\pi$ jest kątem polarnym, a $0\leq\varphi< 2\pi$ kątem fazowym, nazywany też azymuytalnym.

Możemy zauważyć, że dostajemy trygonometryczny wzór na amplitudy:

$$\alpha=\cos \frac{\theta}{2}$$

$$\beta=e^{i\varphi}\sin\frac{\theta}{2}$$

Możemy także wykorzystać operacje odwrotne, aby wyznaczyć kąty na podstawie amplitud:

$$\theta=2\arccos|\alpha|$$

$$\varphi=\arg(\beta)-\arg(\alpha) \bmod 2\pi$$

Na biegunach sfery Blocha, gdy $\alpha=0$ lub $\beta=0$, kąt $\varphi$ nie jest jednoznacznie określony i nie ma znaczenia fizycznego.

## Sfera Blocha
Każdemu czystemu kubitowi $\ket{\psi}$ odpowiada punkt na sferze jednostkowej $x^2+y^2+z^2=1$, zwanej **sferą Blocha**. Każdemu czystemu stanowi kubitu $\ket{\psi}\in \mathcal{H}$, z dokładnością do fazy globalnej, odpowiada wektor jednostkowy $\mathbf r\in\mathbb R^3$, zwany wektorem Blocha.
![[Pasted image 20261102230435.png|338]]

Wektor Blocha odpowiadający stanowi kwantowemu $\ket\psi$ oznaczamy jako $\mathbf r=(x,y,z)$, gdzie:
- $x=\sin\theta \cos\varphi=2\mathfrak{R}(\alpha^\ast\beta)$,
- $y=\sin\theta \sin\varphi=2\mathfrak{I}(\alpha^\ast\beta)$,
- $z=\cos\theta=|\alpha|^2-|\beta|^2$.

Dzięki sferze Blocha prawdopodobieństwo możemy interpretować geometrycznie – na przykład dla $\theta=90\degree$ odległość $\mathbf{r}$ od $\ket{0}$ i $\ket{1}$ jest identyczna, oznacza to, że pomiar w bazie obliczeniowej ma identyczne prawdopodobieństwo pokazania obu stanów. Wraz ze zmianą kąta $\theta$ zmienia się odległość od biegunów, a tym samym ich prawdopodobieństwo. 

Wtedy dla pomiaru w bazie $Z$ zachodzi:

$$P(0)=\frac{1+z}{2},\qquad P(1)=\frac{1-z}{2}$$
w bazie $Y$:

$$P(i)=\frac{1+y}{2},\qquad P(-i)=\frac{1-y}{2}$$

i w bazie $X$:

$$P(+)=\frac{1+x}{2},\qquad P(-)=\frac{1-x}{2}$$

## Stopnie swobody
**Stopnie swobody** (ang. *degrees of freedom*) DOF to liczba niezależnych parametrów potrzebnych do jednoznacznego opisania danego układu. Liczba stopni swobody zależy od tego, jaki układ rozpatrujemy oraz jakie ograniczenia na niego nakładamy.

Dla stanu $\ket{\psi}$ może nam się wydawać, że potrzebne są aż trzy stopnie swobody $x,y,z$. Wiedząc jednak o tym, że punkt na sferze jednostkowej możemy zapisać jako parę kątów, możemy wykazać, że czysty stan fizyczny pojedynczego kubitu ma dwa niezależne parametry rzeczywiste $\theta,\varphi$, po uwzględnieniu normalizacji i pominięciu fazy globalnej.

## Stany charakterystyczne
Na sferze Blocha leży sześć stanów charakterystycznych. Pamiętając, że $\ket{\psi}=\cos \frac{\theta}{2}\ket{0}+e^{i\varphi}\sin \frac{\theta}{2}\ket{1}$, możemy przedstawić jako wektor Blocha $\mathbf{r}\in\mathbb{R}^3$ możemy wyrazić stany charakterystyczne następująco:

| Stan       | $\theta$        | $\varphi$        | $(x,y,z)$  |
| ---------- | --------------- | ---------------- | ---------- |
| $\ket{0}$  | $0$             | dowolny          | $(0,0,1)$  |
| $\ket{1}$  | $\pi$           | dowolny          | $(0,0,-1)$ |
| $\ket{+}$  | $\frac{\pi}{2}$ | $0$              | $(1,0,0)$  |
| $\ket{-}$  | $\frac{\pi}{2}$ | $\pi$            | $(-1,0,0)$ |
| $\ket{i}$  | $\frac{\pi}{2}$ | $\frac{\pi}{2}$  | $(0,1,0)$  |
| $\ket{-i}$ | $\frac{\pi}{2}$ | $\frac{3\pi}{2}$ | $(0,-1,0)$ |

## Stany antypodyczne
Punkt przeciwny do stanu $\mathbf{r}$ ma współrzędne $-\mathbf{r}$. Dla stanu $\ket{\psi}=\cos \frac{\theta}{2} \ket{0}+e^{i\varphi} \sin \frac{\theta}{2} \ket{1}$ stan antypodyczny można zapisać jako:

$$\ket{\psi_{\bot}}=\sin \frac{\theta}{2} \ket{0}-e^{i\varphi} \cos \frac{\theta}{2}\ket{1}  $$

Dwa wektory, które na sferze Blocha mają ten sam kierunek, a przeciwny zwrot, są wektorami ortogonalnymi:

$$\braket{\psi\vert\psi_{\bot}}=0 $$

## Stany czyste
Stan czysty opisuje pojedynczy znormalizowany ket. Na sferze Blocha leży on na powierzchni $|\mathbf{r}|=1$. Stan mieszany opisuje klasyczną niepewność dotyczącą przygotowania stanu. Odpowiada punktowi wewnątrz kuli:

$$0\leq|\mathbf{r}|<1$$

Stan maksymalnie mieszany znajduje się w środku: $\mathbf{r} = (0, 0, 0)$.

## Polaryzacja fotonu
Niech $\ket H\equiv\ket0, \ket V\equiv\ket1$. Stan polaryzacji liniowej pod kątem $\chi$ zapisujemy:

$$
\ket\chi=
\cos\chi\ket H+\sin\chi\ket V
$$

Odpowiada mu wektor Blocha:

$$
\boxed{
\mathbf r=(\sin2\chi,0,\cos2\chi)
}
$$

Zatem polaryzacje liniowe można przedstawić jako punkty na okręgu wielkim sfery Blocha, leżącym w płaszczyźnie $xz$.