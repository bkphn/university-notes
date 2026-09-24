## Rodzaje błędów
Numeryczne rozwiązania zagadnień na ogół zawierają błędy powstające przy formułowaniu zagadnienia i podczas obliczeń. Rozróżniamy:
 * **Błędy danych wejściowych:** Powstają na skutek błędów w argumentach. Można zminimalizować ich wpływ na wynik, jednak nie da się ich całkowicie pozbyć.
 * **Błędy zaokrągleń:** Wynikają ze skończonej długości reprezentacji liczb w komputerze. Mimo że same w sobie są niewielkie, ich suma może znacząco wpłynąć na końcowy wynik.
 * **Błędy metody:** Nazywane również błędami obcięcia; związane są z faktem, że polegamy na uproszczonych formułach.
## Liczby przybliżone i błędy przybliżenia
Liczbą przybliżoną $\overline{x}$ nazywamy liczbę, która nieznacznie odbiega wartością od dokładnej liczby $x$ i zastępuje $x$ w obliczeniach. Błędem przybliżenia nazywamy różnicę $\overline{x} - x$.

W podejściu matematycznym wyróżniamy dwa błędy przybliżenia:
* **Błąd bezwzględny:** Różnica w wartości bezwzględnej:$$ \overline{\Delta}x = |\overline{x} - x| $$
* **Błąd względny:** Jeśli $x \neq 0$, to błąd ten definiuje wielkość $\overline{\delta}x$: $$ \overline{\delta}x = \frac{|\overline{x} - x|}{x} $$Często podaje się go w procentach: $\overline{\delta}x \cdot 100\%$.
## Dokładność
W praktyce rzadko posługujemy się wartościami błędów (zwykle nie znamy dokładnej wartości $x$), lecz na podstawie analizy numerycznej możemy szacować ich wielkość poprzez definiowanie dokładności:
### Dokładność bezwzględna
Dokładnością bezwzględną $\Delta x$ wielkości przybliżonej $\overline{x}$ nazywamy każdą liczbę nie mniejszą od błędu bezwzględnego:
$$ \Delta x \ge \overline{\Delta}x $$
Dla wartości dokładnej $x$ przyjmuje się ją często jako jej różnicę $\Delta x = |\overline{x} - x|$ z wybraną dokładnością (np. przyjmując $\pi = 3.14$, wartość $\Delta\pi \in \{0.002, 0.0016, 0.00159, \dots\}$).
### Dokładność względna
Jeżeli $\overline{x} \neq 0$, to dokładnością względną $\delta x$ nazywamy liczbę:
$$ \delta x = \frac{\Delta x}{|\overline{x}|} $$
## Przenoszenie się dokładności
Niech będzie dana funkcja różniczkowalna $y = f(x_1, \dots, x_n)$. Zakładamy, że $\overline{x} = (\overline{x}_1, \dots, \overline{x}_n)$ jest przybliżeniem dokładnej wartości $x = (x_1, \dots, x_n)$ z dokładnością bezwzględną $\Delta x = (\Delta x_1, \dots, \Delta x_n)$ i względną $\delta x = (\delta x_1, \dots, \delta x_n)$.

**Wzór na przenoszenie dokładności bezwzględnych** (z wyprowadzenia za pomocą wzoru Taylora):
$$ \Delta y = \sum_{j=1}^n \left| \frac{\partial f(\overline{x})}{\partial x_j} \right| \cdot \Delta x_j $$

**Wzór na przenoszenie dokładności względnych** (dla $\overline{y}, \overline{x}_i \neq 0$):
$$ \delta y = \sum_{j=1}^n \left| \frac{|\overline{x}_j|}{|f(\overline{x})|} \right| \cdot \left| \frac{\partial f(\overline{x})}{\partial x_j} \right| \cdot \delta x_j $$

> [!example] Oszacowanie dokładności bezwzględnej objętości kuli
> Dane: $d = 3\text{ cm} \pm 0.1\text{ cm}$, przyjmij $\pi = 3.14$.
> 1. Wzór: $V(\pi, d) = \frac{1}{6} \pi d^3$
> 2. Pochodne cząstkowe: 
>    $\frac{\partial V}{\partial \pi} = \frac{1}{6} d^3 \Big|_{d=3} = 4.5$
>    $\frac{\partial V}{\partial d} = \frac{1}{6} \pi \cdot 3d^2 \Big|_{\pi=3.14} = 14.13$
> 3. Dokładność bezwzględna: 
>    $\Delta V = 4.5 \cdot \Delta \pi + 14.13 \cdot \Delta d = 4.5 \cdot 0.0016 + 14.13 \cdot 0.1 = 1.4202$
> 4. Wynik końcowy: $V = 14.13\text{ cm}^3 \pm 1.4202\text{ cm}^3$
## Zasada równego wpływu (Odwrotny problem dokładności)
Odwrotnym problemem jest badanie, jakie mogą być dokładności bezwzględne argumentów funkcji, aby dokładność wartości funkcji nie przekroczyła zadanej liczby $\varepsilon$:
$$ \Delta y \le \varepsilon $$
Zgodnie z **zasadą równego wpływu**, przyjmujemy, że wpływ dokładności poszczególnych zmiennych na wynik końcowy jest jednakowy:
$$ \left| \frac{\partial f(x)}{\partial x_1} \right| \Delta x_1 = \left| \frac{\partial f(x)}{\partial x_2} \right| \Delta x_2 = \dots = \left| \frac{\partial f(x)}{\partial x_n} \right| \Delta x_n $$
Na podstawie wzoru na przenoszenie dokładności uzyskujemy warunek dla poszczególnych zmiennych $j \in \{1, 2, \dots, n\}$:
$$ \Delta x_j \le \frac{\varepsilon}{n \left| \frac{\partial f(\overline{x})}{\partial x_j} \right|} $$

> [!example] Wyznaczanie dokładności argumentów
> Funkcja: $f(x, y, z) = x(y^2 + z)$ dla $\varepsilon = 10^{-3}$ oraz punktu $x=2, y=1, z=2$.
> 1. Pochodne cząstkowe:
>    * $\frac{\partial f}{\partial x} = (y^2 + z) = 3$
>    * $\frac{\partial f}{\partial y} = 2xy = 4$
>    * $\frac{\partial f}{\partial z} = x = 2$
> 2. Dokładności bezwzględne (gdzie $n=3$):
>    * $\Delta x \le \frac{\varepsilon}{3 \cdot 3} = \frac{1}{9} \cdot 10^{-3}$
>    * $\Delta y \le \frac{\varepsilon}{3 \cdot 4} = \frac{1}{12} \cdot 10^{-3}$
>    * $\Delta z \le \frac{\varepsilon}{3 \cdot 2} = \frac{1}{6} \cdot 10^{-3}$
