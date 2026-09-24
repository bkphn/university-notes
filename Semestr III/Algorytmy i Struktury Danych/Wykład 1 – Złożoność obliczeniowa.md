## Algorytmy i ich własności
**Zmienną** nazywamy wydzielone miejsce w pamięci, gdzie przechowujemy podstawowy typ danych w postaci bitowej.

**Strukturami danych** nazywamy zbiór pewnych typów danych, uporządkowanych w pewien sprecyzowany sposób.

**Algorytmem** nazywamy skończony opis przetwarzania danych wejściowych w dane wejściowe. Problem obliczeniowy możemy przedstawić za pomocą trójki $(I, O, f)$, gdzie:
* $I$ to zbiór danych wejściowych.
* $O$ to zbiór danych wyjściowych.
* $f$ to funkcja $f: I \rightarrow O$.

**Algorytm musi spełniać następujące założenia:**
 * **Adekwatność:** Wykonanie obliczeń zgodnie z założonym celem.
 * **Jednoznaczność:** Sprecyzowanie algorytmu w taki sposób, że każdy krok jest automatyczny i zgodny z założeniem.
 * **Powtarzalność:** Każde wykonanie algorytmu powinno przebiec w identyczny sposób.
 * **Własność stopu:** Kryterium zatrzymania algorytmu musi być dokładnie sprecyzowane dla warunków poprawnego i niepoprawnego przebiegu obliczeń.

Dany jest algorytm $A$, który rozwiązuje problem $\langle I, O, f \rangle$. Przez $A\vert{}x$ będziemy oznaczać, że dla wejścia $x$ algorytm $A$ się zatrzyma.
* **Algorytm częściowo poprawny** spełnia założenie: $$\forall_{i \in I} \exists_{o \in O} : A\vert{}i \Rightarrow f(i) = o$$
* **Algorytm poprawny** jest częściowo poprawny i oprócz tego spełnia własność stopu: $$\forall_{i \in I} A\vert{}i$$
Algorytmy możemy reprezentować w sposób:
* **Opisowy:** Przy użyciu języka naturalnego.
* **Graficzny:** Za pomocą schematu blokowego.
* **Pseudokod:** Za pomocą pseudokodu, łącząc język naturalny z językiem wyższego rzędu.
* **Kod:** Za pomocą kodu napisanego w wybranym języku programowania.
## Klasyfikacja algorytmów
Algorytmy możemy podzielić w zależności od różnych cech.
* **Klasyfikacja ze względu na sposób wykonywania:**
  * sekwencyjne,
  * iteracyjne,
  * rekurencyjne.

* **Klasyfikacja ze względu na paradygmat tworzenia:**
  * dziel i zwyciężaj,
  * programowanie dynamiczne,
  * metoda zachłanna,
  * programowanie liniowe,
  * wyszukiwanie wyczerpujące,
  * heurystyka.
## Złożoność obliczeniowa algorytmów
Złożoność obliczeniowa to nakład czasu / zasobów potrzebnych do prawidłowego wykonania wszystkich obliczeń. Opisuje ona, jak bardzo wydajność algorytmu zależy od rozmiaru danych wejściowych $n$ (z reguły analizuje się złożoność czasową bądź pamięciową).

Złożoność obliczeniowa mówi nam, jak szybko rośnie koszt wykonania danego algorytmu, gdy zwiększymy ilość danych. Złożoność obliczeniowa nie liczy ilości rzeczywistych sekund, lecz liczbę operacji wykonywanych wewnątrz algorytmu.
### Notacje asymptotyczne
W wyznaczaniu złożoności obliczeniowej stosuje się różne sposoby szacowania złożoności oznaczane kolejno symbolami: $\mathcal{O}$, $\Theta$, $\Omega$.
* **Notacja $\mathcal{O}$ (szacowanie górne):** Informuje nas o maksymalnym wzroście złożoności funkcji.
  $$\exists_{n_0 \in \mathbb{N}} \exists_{c \in \mathbb{R}} : \forall_{n > n_0} T(n) \le c \cdot f(n)$$
* **Notacja $\Theta$ (ograniczenie ścisłe):** Informuje o dokładnym rzędzie wzrostu funkcji.
  $$\exists_{c_1, c_2 \ge 0} \exists_{n_0 \in \mathbb{N}} : \forall_{n > n_0} c_1 f(n) \le T(n) \le c_2 f(n)$$
* **Notacja $\Omega$ (szacowanie dolne):** Opisuje minimalny wzrost funkcji.
  $$\exists_{c > 0} \exists_{n_0 \in \mathbb{N}} : \forall_{n \ge n_0} c \cdot f(n) \le T(n)$$

Aby wyznaczyć złożoność obliczeniową funkcji $T(n)$, musimy znaleźć funkcję, która ogranicza funkcję $T$ od góry, dla prawie wszystkich elementów dziedziny.
Jeżeli funkcja $T$ jest wielomianem w postaci $T(n) = a_q n^q + a_{q-1} n^{q-1} + \dots + a_1 n + a_0$, to dominować będzie wyraz o największym współczynniku $n^q$. Jeżeli funkcja $T(n)$ jest asymptotycznie równa $f(n) = n^q$, to możemy powiedzieć, że dla dużych $n$: $T(n) \approx f(n)$.
Jeżeli $T(n) \sim f(n)$, to możemy powiedzieć, że:
$$\begin{cases} T(n) = O(f(n)) \\ T(n) = \Omega(f(n)) \end{cases} \implies T(n) = \Theta(f(n))$$


> [!example] Przykład obliczenia złożoności
> Oblicz złożoność obliczeniową funkcji $T(n) = n^3 - 7n^2 + 2n + 16$.
> 1. Dla dużych $n$: $T(n) \approx n^3$.
> 2. Wyznaczenie złożoności: $T(n) = O(n^3), T(n) = \Omega(n^3) \implies T(n) = \Theta(n^3)$.
> 3. Wynik: $T(n) = \Theta(n^3)$.
## Algorytm Euklidesa
NWD oznacza największy wspólny dzielnik dwóch liczb całkowitych $a, b$. W angielskim zapisie funkcję $\operatorname{NWD}(a, b)$ zapisuje się jako $\operatorname{gcd}(a, b)$.
Algorytm Euklidesa to jeden z najstarszych znanych algorytmów; pozwala on na bardzo efektywne wyznaczanie wartości NWD, opierając się na własności:
$$\operatorname{NWD}(a, b) = \operatorname{NWD}(b, a \pmod b)$$

**Implementacja w języku Python:**
```python
def NWD(a, b):
    while b != 0:
        r = a % b
        a = b
        b = r
    return a
```
## Najmniejsza wspólna wielokrotność:
$\operatorname{NWW}$ oznacza najmniejszą wspólną wielokrotność dwóch liczb całkowitych $a,b$. W angielskim zapisie funkcję $\operatorname{NWW}(a,b)$ zapisuje się jako $\operatorname{lcm}(a,b)$.

Obliczając NWW korzystamy z zależności między NWW a NWD:
$$a\cdot b=\operatorname{NWD}(a,b)\cdot\operatorname{NWW}(a,b)$$
co po przekształceniu daje nam wzór na NWW:
$$\operatorname{NWW}(a,b)=\frac{a\cdot b}{\operatorname{NWD}(a,b)}$$
Jako, że cały algorytm NWW to jedno dzielenie i mnożenie, to złożoność obliczeniowa zależy tylko i wyłącznie od złożoności NWD, więc wynosi ona $\Theta(\log n)$.