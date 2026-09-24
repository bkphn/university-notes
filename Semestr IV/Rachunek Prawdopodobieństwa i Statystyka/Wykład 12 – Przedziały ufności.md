## Przedziały ufności
Przedziałem ufności parametru $\theta$ ze współczynnikiem ufności $1−\alpha$ nazywamy przedział $(\theta_-,\theta_+ )$ spełniający warunki:
- końce przedziału $θ_-,θ_+$ są funkcjami próby losowej i nie zależą od parametru $\theta$.
- prawdopodobieństwo pokrycia przez ten przedział nieznanego parametru $\theta$ jest równe $1-\alpha$: $$P(\theta_-<\theta<\theta_+ )=1−\alpha$$
## Konstrukcja przedziałów ufności
Przedziały ufności możemy konstruować za pomocą statystyk bądź za pomocą twierdzeń granicznych. 

Niech $T(\mathbf{x},θ)$ będzie statystyką taką, że:
- dla ustalonego $\mathbf{x}$ funkcja $T$ jest ciągła i monotoniczna względem $\theta$,
- rozkład $P(T(\mathbf{x},\theta)<x)=G(x)$ jest ciągły, znany i nie zależy od parametru $\theta$.

Zachodzi wtedy $P(z_{1}<T(\mathbf{x},\theta)<z_{2})=G(z_{2})-G(z_{1})$. Niech $k\left( \frac{\alpha}{2} \right), k\left( \frac{1-\alpha}{2} \right)$ będą kwantylami rzędu $\frac{\alpha}{2}, \frac{1-\alpha}{2}$ dla dystrybuanty $G(x)$, po podstawieniu: $$P\left(k\left(\frac{\alpha}{2}\right)<T(\mathbf{x},\theta)<k\left(\frac{1-\alpha}{2}\right)\right)=1-\frac{\alpha}{2}-\frac{\alpha}{2}=1-\alpha$$
Ponieważ zgodnie z założeniem, funkcja $T$ jest monotoniczna względem $\theta$ dla każdego $\mathbf{x}$ to dla nierówności $k\left(\frac{\alpha}{2}\right)<T(\mathbf{x},\theta)<k\left(\frac{1-\alpha}{2}\right)$ istnieje jedyne rozwiązanie względem $\theta$, które może być zapisane w postaci $\theta_{-}(\mathbf{x},\alpha)<\theta<\theta_{+}(\mathbf{x},\alpha)$, innymi słowy: $$k\left(\frac{\alpha}{2}\right)<T(\mathbf{x},\theta)<k\left(\frac{1-\alpha}{2}\right)\iff \theta_{-}(\mathbf{x},\alpha)<\theta<\theta_{+}(\mathbf{x},\alpha)$$
Stosując to rozwiązanie pod symbolem prawdopodobieństwa dostajemy: $$P(\theta_{-}(\mathbf{x},\alpha)<\theta<\theta_{+}(\mathbf{x},\alpha))=1-\alpha$$co daje szukany przedział ufności.

