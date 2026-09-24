## Postać zespolona szeregu Fouriera
Ze wzorów Eulera możemy wyprowadzić następujące wzory na sinus i cosinus: $$ \sin nx = \frac{e^{inx} - e^{-inx}}{2i}, \quad \cos nx = \frac{e^{inx} + e^{-inx}}{2} $$
Dzięki tym wzorom możemy wprowadzić nowy sposób zapisu klasycznego szeregu Fouriera w postaci zespolonej: $$ \frac{a_0}{2} + \sum_{n=1}^{\infty} [a_n \cos nx + b_n \sin nx] = \sum_{n=-\infty}^{\infty} c_n e^{inx} $$
### Współczynniki zespolone
Współczynniki $c_n$ nazywamy współczynnikami zespolonymi szeregu Fouriera, co stanowi odzwierciedlenie współczynników $a_n$ i $b_n$ dla postaci zespolonej. Jeżeli funkcja $f$ jest okresowa na przedziale $[-\pi, \pi]$, to możemy je obliczyć ze wzoru:
$$ c_n = \frac{1}{2\pi} \int_{-\pi}^{\pi} f(x) \cdot e^{-inx} \, dx $$
W przypadku, gdy funkcja ta jest okresowa na innym przedziale $f(x) = f(x + 2L)$, musimy skorzystać z ogólniejszego wzoru:
$$ c_n = \frac{1}{2\pi} \int_{-L}^{L} f(x) \cdot e^{-ixn\frac{\pi}{L}} \, dx $$
W tym przypadku zmienia nam się również wzór na szereg do postaci $\sum_{n=-\infty}^{\infty} c_n e^{inx\frac{\pi}{L}}$.
## Transformata Fouriera
Transformata Fouriera pozwala na przedstawienie dowolnej funkcji (nie musi być okresowa) jako całki złożonej z funkcji sinus i cosinus. Transformację tę zapisujemy jako $\mathcal{F}$ i definiujemy wzorem:
$$ F(\omega) = \mathcal{F}[f(x)] = \frac{1}{\sqrt{2\pi}} \int_{-\infty}^{\infty} f(x) \cdot e^{-i\omega x} \, dx $$
### Transformata odwrotna
Transformacją $\mathcal{F}^{-1}$ nazywamy transformatę odwrotną do $\mathcal{F}$ i definiuje się ją wzorem:
$$ f(x) = \mathcal{F}^{-1}[F(\omega)] = \frac{1}{\sqrt{2\pi}} \int_{-\infty}^{\infty} F(\omega) \cdot e^{i\omega x} \, d\omega $$

> [!example] Przykład wyznaczenia transformaty
> Wyznacz $\mathcal{F}[f(x)]$ dla funkcji $f(x) = e^{-|x|}$:
> $$ \mathcal{F}[e^{-|x|}] = \frac{1}{\sqrt{2\pi}} \int_{-\infty}^{\infty} e^{-|x|} \cdot e^{-i\omega x} \, dx = \frac{1}{\sqrt{2\pi}} \int_{-\infty}^{\infty} e^{-|x| - i\omega x} \, dx $$
> Rozbijając całkę na dwa przedziały:
> $$ = \frac{1}{\sqrt{2\pi}} \left( \int_{-\infty}^{0} e^{x - i\omega x} \, dx + \int_{0}^{\infty} e^{-x - i\omega x} \, dx \right) $$
> Po obliczeniu całek otrzymujemy:
> $$ = \frac{1}{\sqrt{2\pi}} \left( \left[\frac{e^{(1-i\omega)t}}{1-i\omega}\right]_{-\infty}^{0} + \left[\frac{e^{(-1-i\omega)t}}{-1-i\omega}\right]_{0}^{\infty} \right) = \frac{1}{\sqrt{2\pi}} \left(\frac{1}{1-i\omega} + \frac{1}{1+i\omega}\right) = \frac{2}{\sqrt{2\pi} \cdot (1 + \omega^2)} $$
## Wzór Parsevala
Wzór Parsevala dla transformaty Fouriera mówi, że:
$$ \int_{-\infty}^{\infty} |f(x)|^2 \, dx = \int_{-\infty}^{\infty} |F(\omega)|^2 \, d\omega $$
A jeżeli mamy do czynienia z funkcją okresową, to zachodzi relacja:
$$ \frac{1}{\pi} \int_{-\infty}^{\infty} |f(x)|^2 \, dx = \frac{|a_0|^2}{2} + \sum_{n=1}^{\infty} (|a_n|^2 + |b_n|^2) $$
