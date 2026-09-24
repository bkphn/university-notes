## Jednostka urojona $i$
Jednostka urojona $i$ to liczba wykraczająca poza zbiór liczb rzeczywistych $\mathbb{R}$. Jest to taka liczba, której kwadrat jest równy $-1$: $$ i^2 = -1, \quad i \in \mathbb{C} $$Zbiór liczb zespolonych $\mathbb{C}$ jest rozszerzeniem zbioru liczb rzeczywistych $\mathbb{R}$ ($\mathbb{R} \subset \mathbb{C}$). Struktura $(\mathbb{C}, +, \cdot)$ jest ciałem. Rozszerzenie to pozwala na rozwiązywanie wszystkich równań kwadratowych.

> [!example] Przykład
> Obliczyć miejsca zerowe funkcji $f(x) = x^2 + x + 1$:
> $$ x^2 + x + 1 = 0 $$
> $$ \Delta = 1 - 4 = -3 \implies \sqrt{\Delta} = \sqrt{3}i $$
> $$ x = \frac{-1 \pm \sqrt{3}i}{2} $$
## Liczby zespolone
Liczby zespolone to pary liczb zapisywane w postaci $a + bi$, gdzie $a, b \in \mathbb{R}$ oraz $i^2 = -1$.
* $a$ nazywamy częścią rzeczywistą liczby $a + bi$ i zapisujemy jako $\operatorname{Re}(a + bi)$ lub $\mathfrak{R}(a + bi)$.
* $b$ nazywamy częścią urojoną liczby $a + bi$ i zapisujemy jako $\operatorname{Im}(a + bi)$ lub $\mathfrak{I}(a + bi)$.

Dwie liczby zespolone $a + bi$ oraz $c + di$ są równe wtedy i tylko wtedy, gdy $a = c$ oraz $b = d$. Często liczbę zespoloną zapisujemy jako $z$, taka że $z = a + bi$.

Liczbę zespoloną $(a, b)$ zapisujemy za pomocą postaci algebraicznej $a + bi$. Stosuje się uproszczoną formę zapisu takich sum:
* $a + (-b)i = a - bi$
* $a + bi = a + ib$
* $0 + bi = bi$
* $a + 0i = a$
## Operacje na liczbach zespolonych
### Dodawanie i odejmowanie
$$ (a + bi) \pm (c + di) = (a \pm c) + (b \pm d)i $$ 
### Mnożenie
$$ (a + bi) \cdot (c + di) = ac + bd(i^2) + (ad + bc)i = ac - bd + (ad + bc)i $$

> [!example] Przykład
> Wyznaczyć $x$ dla $(5x + 3i)x = -2 + 5i$:
> $$ x = \frac{-2 + 5i}{5x + 3i} $$
> $$ x = \frac{-2 + 5i}{5x + 3i} \cdot \frac{5x - 3i}{5x - 3i} $$
> $$ x = \frac{-10x + 6i + 25ix + 15}{(5x)^2 - (3i)^2} \dots $$
> *(Należy zawsze wyciągać współczynniki $a, b$, by nie zostawiać niewymierności w mianowniku).* Ostatecznie:
> $$ x = \frac{5}{34} + \frac{31}{34}i $$

Ponieważ $\mathbb{C}$ jest rozszerzeniem $\mathbb{R}$, wewnątrz ciała liczb zespolonych możemy skorzystać ze wszystkich operacji ze zbioru liczb rzeczywistych, np.:
* $(a + bi)^2 = a^2 + 2abi - b^2$
* $(a + bi)^3 = a^3 - 3ab^2 + (3a^2b - b^3)i$ (ponieważ $(a + b)^3 = a^3 + 3a^2b + 3ab^2 + b^3$)
### Pierwiastki zespolone
Wyjątkiem są pierwiastki $\sqrt{r}$ dla $r \in \mathbb{R}$, nazywane pierwiastkami arytmetycznymi. Według konwencji przyjętej w ciele $\mathbb{R}$ pierwiastek taki zwraca tylko wartość dodatnią, tj. $\sqrt{4} = 2$. W ciele liczb zespolonych niemożliwe jest stwierdzenie, który z pierwiastków jest ujemny, a który dodatni, więc wynikiem równania są oba pierwiastki.

Aby obliczyć pierwiastek kwadratowy z liczby $a + bi$, korzystamy ze schematu:
$$ \sqrt{a + bi} = x + yi $$
$$ a + bi = (x + yi)^2 $$
$$ a + bi = x^2 - y^2 + 2xyi $$
Stąd otrzymujemy układ równań:
$$ \begin{cases} a = x^2 - y^2 \\ b = 2xy \end{cases} $$
a następnie rozwiązujemy go.

>[!danger] Zasadnicze Twierdzenie Algebry
> Każdy wielomian o współczynnikach zespolonych stopnia dodatniego posiada pierwiastek w ciele liczb zespolonych: każde równanie $a_n x^n + a_{n-1} x^{n-1} + \dots + a_1 x^1 + a_0 = 0$, *gdzie* $a_n, a_{n-1}, \dots, a_0 \in \mathbb{C}$ *oraz* $n \ge 1$, *ma rozwiązanie* $x \in \mathbb{C}$.
## Liczby sprzężone
Liczbę sprzężoną do liczby $z \in \mathbb{C}$ zapisujemy jako $\overline{z} = \overline{a + bi} = a - bi$.

**Własności liczb sprzężonych**:
* $\overline{z + w} = \overline{z} + \overline{w}$
* $\overline{z \cdot w} = \overline{z} \cdot \overline{w}$
* $\overline{\overline{z}} = z$
* $\overline{\left(\frac{z}{w}\right)} = \frac{\overline{z}}{\overline{w}}$ dla $w \neq 0$
* $z \cdot \overline{z} = a^2 + b^2$ (gdzie $z = a + bi$)

> [!example] Przykład
> Obliczyć $z = \overline{z}$:
> $$ z = \overline{z} \iff b = 0 \iff z \in \mathbb{R} $$
## Interpretacja geometryczna
Liczbę zespoloną jesteśmy w stanie zaznaczyć na układzie współrzędnych złożonym z osi $\mathfrak{I}$ (Imaginaris) oraz $\mathfrak{R}$ (Realis). 

Współrzędne punktu na płaszczyźnie możemy zapisać w jednym z dwóch sposobów:
1. **Prostokątnym (kartezjańskim):** Współrzędne $(a, b)$ w postaci $a + bi$, gdzie $a$ to część rzeczywista ($a = r \cdot \cos \varphi$), a $b$ to część urojona ($b = r \cdot \sin \varphi$).
2. **Biegunowym:** Współrzędne $(r, \varphi)$ w postaci $r(\cos \varphi + i \cdot \sin \varphi)$, gdzie $r$ to moduł liczby zespolonej ($r = |a + bi| = \sqrt{a^2 + b^2}$), a $\varphi$ to argument liczby zespolonej.

**Argument główny liczby zespolonej** to wartość kąta ograniczona w przedziale $(0, 2\pi)$ (często stosujemy też $\langle -\pi, \pi \rangle$). Argument główny możemy obliczyć ze wzoru:
$$ \operatorname{Arg}(a + bi) = \arctan\left(\frac{b}{a}\right) = \operatorname{atan2}(b, a) $$
W przypadku liczenia funkcją tangens należy pamiętać, by wartość przesunąć o odpowiedni okres, aby zmieścić się w przedziale. Funkcja $\operatorname{atan2}$ ma już uwzględnione odpowiednie przesunięcia ćwiartkowe. Na płaszczyźnie zespolonej powstaje trójkąt prostokątny, więc by obliczyć $\cos \varphi$ oraz $\sin \varphi$, wystarczy obliczyć stosunek poszczególnych boków.

> [!example] Przykład
> Wyznaczyć $\arg(i)$ oraz $\operatorname{Arg}(i)$:
> $$ \arg(i) = \left\{\frac{\pi}{2} + 2k\pi : k \in \mathbb{Z}\right\} $$
> $$ \operatorname{Arg}(i) = \frac{\pi}{2} $$
## Moduł liczby zespolonej
Moduł liczby zespolonej $z$ zapisujemy jako $|z|$. Można go rozumieć jako odległość liczby zespolonej od początku układu współrzędnych. Z twierdzenia Pitagorasa:
$$ |z| = \sqrt{a^2 + b^2} $$
**Własności modułu liczby zespolonej:**
* $|z| \cdot |w| = |z \cdot w|$
* $|z + w| \le |z| + |w|$
* $|z|^2 = z \cdot \overline{z}$
* $\left|\frac{z}{w}\right| = \frac{|z|}{|w|}$ dla $w \neq 0$
## Operacje w postaci biegunowej i wykładniczej
Każdą liczbę zespoloną $z$ można zapisać w postaci biegunowej: $|z|(\cos \varphi + i \sin \varphi)$.
### Iloczyn
$$ [|z|(\cos \varphi + i \sin \varphi)] \cdot [|w|(\cos \theta + i \sin \theta)] = |z \cdot w| \cdot (\cos[\varphi + \theta] + i \sin[\varphi + \theta]) $$
Wykorzystuje się przy tym wzory na sumę funkcji trygonometrycznych:
* $\sin(\alpha \pm \beta) = \sin \alpha \cos \beta \pm \cos \alpha \sin \beta$
* $\cos(\alpha \pm \beta) = \cos \alpha \cos \beta \mp \sin \alpha \sin \beta$

W postaci kartezjańskiej iloczyn wygląda następująco:
$$ z \cdot w = (a_z + b_z i) \cdot (a_w + b_w i) = a_z a_w - b_z b_w + (a_z b_w + b_z a_w)i $$
### Iloraz
W postaci biegunowej:
$$ \frac{|z|(\cos \varphi + i \sin \varphi)}{|w|(\cos \theta + i \sin \theta)} = \left|\frac{z}{w}\right| \cdot (\cos[\varphi - \theta] + i \sin[\varphi - \theta]) $$
W postaci kartezjańskiej $\frac{a_z + b_z i}{a_w + b_w i}$ należy pomnożyć licznik i mianownik przez sprzężenie mianownika.
## Wzór Eulera
Wzór Eulera mówi, że:
$$ \cos \varphi + i \cdot \sin \varphi = e^{i\varphi} $$
Znając ten wzór, możemy zapisać liczbę zespoloną za pomocą jej postaci wykładniczej:
$$ z = |z| \cdot e^{i\varphi} $$
Ponieważ $\operatorname{Arg}(-1) = \pi$ oraz $|-1| = 1$, dla liczby $-1$ wzór ten przyjmuje postać:
$$ -1 = 1 \cdot e^{i\pi} \implies e^{i\pi} + 1 = 0 $$
Jest to tzw. *najpiękniejszy wzór matematyki*, ponieważ łączy najważniejsze stałe i liczby: $e, \pi, i, 1, 0$.

Iloczyn w postaci wykładniczej:
$$ |z|e^{i\varphi} \cdot |w|e^{i\theta} = |wz| \cdot e^{i(\varphi + \theta)} $$
Operacja potęgowania działa podobnie jak w ciele liczb rzeczywistych, np. $e^z = e^{a+bi} = e^a \cdot e^{bi} \implies e^z = e^a(\cos b + i \sin b)$.
## Wzór de Moivre'a
Wzór de Moivre'a mówi, że dla $\forall_{n \in \mathbb{Z}}$ oraz $z = |z|(\cos \varphi + i \sin \varphi)$ zachodzi:
$$ z^n = |z|^n(\cos n\varphi + i \sin n\varphi) $$
### Metoda wyznaczania pierwiastków zespolonych
Ze wzoru de Moivre'a możemy wyznaczyć wzór na konkretne pierwiastki stopnia $n$ z liczby zespolonej $z$:
$$ z_k = \sqrt[n]{|z|} \left( \cos\left[\frac{\varphi + 2k\pi}{n}\right] + i \sin\left[\frac{\varphi + 2k\pi}{n}\right] \right) $$
Gdzie $k \in \{0, 1, \dots, n-1\}$, a $n$ to stopień równania wyjściowego. Każde równanie $n$-tego stopnia ma dokładnie $n$ pierwiastków zespolonych (wyjątkiem jest równanie $z^n = 0$, gdzie jedynym rozwiązaniem jest $z = 0$).