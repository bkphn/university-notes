## Faza globalna
Dany jest stan kubitu $\ket{\psi}=\alpha \ket{0}+\beta \ket{1}$, możemy pomnożyć cały stan przez skalar $e^{i\gamma}$, który nazywamy **fazą globalną**. Amplitudy $\alpha', \beta'$ stanu się zmieniają, ale ich moduły pozostają niezmienne.

$$e^{i\gamma}\ket{\psi} =e^{i\gamma}\alpha\ket{0}+e^{i\gamma}\beta \ket{1}=\alpha'\ket{0}+\beta'\ket{1}  $$

Dla dowolnego stanu pomiarowego $\ket{m}$:

$$\braket{m|\psi'}=\bra{m}e^{i\gamma}\ket{\psi}=e^{i\gamma}\braket{m|\psi}$$

stany $\ket{\psi}$ oraz $\ket{\psi'}$ opisują ten sam stan fizyczny, z tego powodu faza globalna może być pomijana przy obliczeniach.

## Parametryzacja kubitu
Po usunięciu nieobserwowalnej fazy globalnej każdy czysty stan kubitu $\ket{\psi}$ możemy zapisać w postaci:

$$\ket{\psi}=\cos \frac{\theta}{2}\ket{0}+e^{i\varphi}\sin \frac{\theta}{2}\ket{1}$$

gdzie: $0\leq\theta\leq\pi$ jest kątem polarnym, a $0\leq\varphi\leq 2\pi$ kątem fazowym, nazywany też azymuytalnym.

## Sfera Blocha
Każdemu czystemu kubitowi $\ket{\psi}$ odpowiada punkt na sferze jednostkowej $x^2+y^2+z^2=1$, zwanej **sferą Blocha**. Kubit jest tutaj wektorem jednostkowym, który przedstawiamy za pomocą kątów $\theta,\varphi$.



Wektor stanu kwantowego $\ket{\psi}$ na sferze bloka będziemy oznaczać jako $\mathbf{r}=(x,y,z)$, gdzie:
- $x=\sin\theta \cos\varphi$,
- $y=\sin\theta \sin\phi$,
- $z=\cos\theta$.

## Stopnie swobody


## Bieguny sfery Blocha
Na sferze Blocha, na biegunach leży sześć stanów charakterystycznych. Pamiętając, że $\ket{\psi}=\cos \frac{\theta}{2}\ket{0}+e^{i\varphi}\sin \frac{\theta}{2}\ket{1}=(x,y,z)$, możemy wyrazić stany charakterystyczne następująco:

| Stan       | $\theta$        | $\varphi$        | $(x,y,z)$  |
| ---------- | --------------- | ---------------- | ---------- |
| $\ket{0}$  | $0$             | dowolny          | $(0,0,1)$  |
| $\ket{1}$  | $\pi$           | dowolny          | $(0,0,-1)$ |
| $\ket{+}$  | $\frac{\pi}{2}$ | $0$              | $(1,0,0)$  |
| $\ket{-}$  | $\frac{\pi}{2}$ | $\pi$            | $(-1,0,0)$ |
| $\ket{i}$  | $\frac{\pi}{2}$ | $\frac{\pi}{2}$  | $(0,1,0)$  |
| $\ket{-i}$ | $\frac{\pi}{2}$ | $\frac{3\pi}{2}$ | $(0,-1,0)$ |

