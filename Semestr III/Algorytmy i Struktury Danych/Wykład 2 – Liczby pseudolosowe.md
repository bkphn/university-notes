## Liczby pseudolosowe
Liczby pseudolosowe nazywane są pseudolosowymi, ponieważ komputer nie jest w stanie wygenerować w pełni losowej liczby, zamiast tego używane są algorytmy imitujące losowość. Są to liczby, których rozkład ma ukryte regularności, lecz w praktyce nie są one rozróżnialne z liczbami losowymi. Liczby losowe powstają z generatorów mechanicznych i fizycznych (np. losowanie z urny, rozkład radioaktywny), podczas gdy liczby pseudolosowe tworzone są przez generatory (np. LFG).

## Ciąg Fibonacciego
Urodzony w 1175 roku Leonardo da Pisa, zwany Fibonaccim, był jednym z najlepszych włoskich matematyków na przełomie XII i XIII wieku. W pracy *Liber abaci* przedstawił model ciągu Fibonacciego jako rozwiązanie problemu o rozmnażaniu się królików. Nazwa ciąg Fibonacciego spopularyzowana została dopiero w XIX wieku.

Ciąg Fibonacciego określamy wzorem rekurencyjnym:

$$F_n = \begin{cases} 0, & n = 0 \\ 1, & n = 1 \\ F_{n-1} + F_{n-2}, & n > 1 \end{cases}$$

Zatem kilka kolejnych wyrazów ciągu to: $0, 1, 1, 2, 3, 5, 8, 13, \dots$

Fibonacci przedstawił następujące założenia dotyczące rozmnażania się królików:
* Zaczynami z jedną parą królików.
* Każda para po miesiącu dojrzewa.
* Każda para dorosłych królików rodzi co miesiąc jedną nową parę.
* Króliki nie umierają (idealizacja).

Rozwiązaniem problemu były liczby, z początku wyglądające na losowe, które w rzeczywistości były ciągiem rekurencyjnym $F_n$.

> [!example] Wyznaczenie 5 kolejnych wyrazów ciągu Fibonacciego
> * $F_n = F_{n-1} + F_{n-2}$
> * $F_0 = 0$
> * $F_1 = 1$
> * $F_2 = F_1 + F_0 = 1 + 0 = 1$
> * $F_3 = F_2 + F_1 = 1 + 1 = 2$
> * $F_4 = F_3 + F_2 = 1 + 2 = 3$
> * $F_5 = F_4 + F_3 = 2 + 3 = 5$

## Złota proporcja
Złotym podziałem nazywamy podział odcinka na dwie części tak, by stosunek długości dłuższej z nich do krótszej był taki sam jak całego odcinka do dłuższej:

$$\frac{a+b}{a} = \frac{a}{b}$$

Stosunek ten jest równy:

$$\frac{1+\sqrt{5}}{2} = 1.6180339887\dots$$

Liczbę tę nazywamy złotą proporcją i oznaczamy jako $\varphi$.

**Złota proporcja** jest ściśle powiązana z ciągiem Fibonacciego. Stosunek dwóch kolejnych wyrazów ciągu zbiega do liczby $\varphi$:
- $\frac{1}{1} = 1$
- $\frac{2}{1} = 2$
- $\frac{3}{2} = 1.5$
- $\frac{8}{5} = 1.6$
- $\frac{13}{8} = 1.625$
	$\vdots$
- $\lim_{n \to \infty} \frac{F_{n+1}}{F_n} = \varphi$

Granicę można uogólnić do postaci:

$$\lim_{n \to \infty} \frac{F_{n+a}}{F_n} = \varphi^a$$

## Opóźniony generator Fibonacciego (LFG)
Przykładem algorytmu generowania liczb pseudolosowych jest opóźniony generator Fibonacciego LFG. Generator ten korzysta z ciągu Fibonacciego.

Wzór na kolejne liczby pseudolosowe wygląda następująco:

$$X_n = (X_{n-1} + X_{n-2}) \pmod m$$

Wadą podstawowej wersji jest duża korelacja między kolejnymi wyrazami ciągu. Wady tej można się pozbyć, zastępując dwa kolejne wyrazy ciągu dwoma dowolnymi za pomocą opóźnień $p, q$. Tę wersję generatora nazywamy opóźnionym generatorem Fibonacciego i definiujemy wzorem:

$$X_n = (X_{n-p} + X_{n-q}) \pmod m$$

Kolejnym uogólnieniem jest zastąpienie operatora $+$ dowolnym innym operatorem (odejmowanie, mnożenie, XOR itp.). Wybrany operator oznaczymy jako $\diamond$, wtedy wzór przybierze postać:

$$X_n = (X_{n-p} \diamond X_{n-q}) \pmod m$$

Generator taki oznaczamy jako $F(p, q, \diamond)$.

> [!example] Przykład generowania LFG
> Wygeneruj LFG ciąg 5 liczb dla opóźnień $p=3, q=7$, mod $m=10$ oraz ciągu wejściowego $8, 9, 2, 1, 3, 4, 5, 5$:
> * $X_n = X_{n-3} + X_{n-7} \pmod{10}$
> * $X_9 = X_6 + X_2 = 4 + 9 = 13$
> * $X_{10} = X_7 + X_3 = 5 + 2 = 7$
> * $X_{11} = X_8 + X_4 = 5 + 1 = 6$
> * $X_{12} = X_9 + X_5 = 13 + 3 = 16$
> * $X_{13} = X_{10} + X_6 = 7 + 4 = 11$

## Opóźniony generator na zasadzie dodawania z przeniesieniem (AWCG)
Opóźniony generator na zasadzie dodawania z przeniesieniem AWCG został opracowany w 1991 roku przez G. Marsaglie'a oraz A. Zamana. Opisany jest następującym wzorem:

$$x_n = (x_{n-j} + x_{n-k} + c_{n-1}) \pmod m$$

$$c_n = \begin{cases} 0, & (x_{n-j} + x_{n-k} + c_{n-1}) < m \\ 1, & (x_{n-j} + x_{n-k} + c_{n-1}) \ge m \end{cases}$$

Jest to modyfikacja opóźnionego generatora Fibonacciego.

**Implementacja w języku Python:**
```python
m = int(input("Enter value for m: "))
j = int(input("Enter value for j: "))
k = int(input("Enter value for k: "))
c = 0
x = []

for w in range(k):
    x.append(int(input("Enter value for x: ")))

count_iteration = int(input("How many numbers you want to create? "))
c = 0
i = 0
while i < count_iteration:
    a = int((x[((k + i - j) % k)] + x[i % k] + c))
    x[i % k] = int((x[((k + i - j) % k)] + x[i % k] + c) % m)
    print(x[i % k], x)
    if a < m:
        c = 0
    else:
        c = 1
    i += 1
```

> [!example] Przykład generowania AWCG
> Wygeneruj AWCG ciąg 5 liczb dla opóźnień $3, 7$, zakresu $m = 10$ oraz ciągu wejściowego $8, 9, 2, 1, 3, 4, 5, 5$:
> * $c_0 = 0$
> * $x_9 = x_6 + x_2 + c_0 \pmod{10} = 4 + 9 + 0 \pmod{10} = 3$, $c_9 = 1$
> * $x_{10} = x_7 + x_3 + c_9 \pmod{10} = 5 + 2 + 1 \pmod{10} = 8$, $c_{10} = 0$
> * $x_{11} = x_8 + x_4 + c_{10} \pmod{10} = 5 + 1 + 0 \pmod{10} = 6$, $c_{11} = 0$
> * $x_{12} = x_9 + x_5 + c_{11} \pmod{10} = 3 + 3 + 0 \pmod{10} = 6$, $c_{12} = 0$
> * $x_{13} = x_{10} + x_6 + c_{12} \pmod{10} = 8 + 4 + 0 \pmod{10} = 2$, $c_{13} = 1$

## Liniowy generator kongruencyjny (LCG)
Liniowy generator kongruencyjny LCG określamy następującym wzorem:

$$x_{i+1} = (a \cdot x_i + c) \pmod m$$

gdzie:
* $m$ – zakres $\{0, \dots, m\}$ w którym generowane są liczby pseudolosowe.
* $a$ – współczynnik generujący liczbę, $a \in \{1, \dots, m-1\}$.
* $c$ – współczynnik przyrostu, $c \in \{0, \dots, m-1\}$.
* $x_0$ – ziarno, $x_0 \in \{0, \dots, m-1\}$.

Generator ten nie jest uważany za bezpieczny, ponieważ dla pewnych kombinacji parametrów jest praktycznie losowy, a dla innych bardzo szybko staje się okresowy.

**Implementacja w języku Python:**
```python
m = 1248935
a = 123132
c = 344566
seed = 543

def linearPRNG():
    global seed
    temp = (a * seed + c) % m
    seed = temp
    return temp

def main():
    A = []
    for i in range(10):
        A.append(linearPRNG())
    print("Losowe liczby: ")
    for i in range(10):
        print(f"{A[i]}")

if __name__ == "__main__":
    main()
```

> [!example] Przykład generowania LCG
> Wygeneruj LCG ciąg 5 liczb dla zakresu $m = 10$, $a = 7$, $c = 9$, $x_0 = 2$:
> * $x_{i+1} = (7 \cdot x_i + 9) \pmod{10}$
> * $x_1 = (7 \cdot 2 + 9) \pmod{10} = 23 \pmod{10} = 3$
> * $x_2 = (7 \cdot 3 + 9) \pmod{10} = 30 \pmod{10} = 0$
> * $x_3 = (7 \cdot 0 + 9) \pmod{10} = 9 \pmod{10} = 9$
> * $x_4 = (7 \cdot 9 + 9) \pmod{10} = 72 \pmod{10} = 2$
> * $x_5 = (7 \cdot 2 + 9) \pmod{10} = 23 \pmod{10} = 3$

## Generator Parka-Millera
Generator Parka-Millera, nazywany inaczej generatorem Lehmera, określamy następującym wzorem:

$$x_i = (a \cdot x_{i-1}) \pmod m$$

W przeciwieństwie do generatorów LCG, AWCG, współczynniki $a, m$ muszą być starannie dobrane:
* $m$ musi być liczbą pierwszą bądź jej wielokrotnością.
* $x_0$ musi być względnie pierwsze z $m$ ($\mathrm{NWD}(x_0, m) = 1$).
* $a$ musi być pierwiastkiem pierwotnym modulo $m$

$$\forall_{b \in \mathbb{Z}} : \mathrm{NWD}(b, m) = 1, \exists_{k \in \mathbb{Z}} : a^k \pmod m = b$$

Konieczne jest dopasowanie odpowiednich wartości, by uniknąć 0 w algorytmie, który wyzeruje następne wyniki.

> [!example] Przykład generowania Parka-Millera
> Wygeneruj Parkiem-Millerem ciąg 5 liczb dla zakresu $m = 7$, $a = 3$, $x_0 = 2$:
> * $x_i = (3 \cdot x_{i-1}) \pmod 7$
> * $x_1 = (3 \cdot 2) \pmod 7 = 6 \pmod 7 = 6$
> * $x_2 = (3 \cdot 6) \pmod 7 = 18 \pmod 7 = 4$
> * $x_3 = (3 \cdot 4) \pmod 7 = 12 \pmod 7 = 5$
> * $x_4 = (3 \cdot 5) \pmod 7 = 15 \pmod 7 = 1$
> * $x_5 = (3 \cdot 1) \pmod 7 = 3 \pmod 7 = 3$
