## Alan Turing
Urodzony w 1912 roku matematyk, kryptolog i ojciec współczesnej informatyki teoretycznej. Był prekursorem sztucznej inteligencji oraz twórcą teorii automatów, stanowiącej matematyczne podstawy teorii obliczeń. 

Największe znaczenie miała jego praca podająca teoretyczny model komputera, nazwanego **automatem (maszyną) Turinga**.
## Maszyna Turinga
Zgodnie z założeniami autora, Maszyna Turinga składa się z:
*   nieskończonej taśmy podzielonej na komórki zawierające symbole,
*   ruchomej głowicy zapisująco-odczytującej (odczytuje, zapisuje i porusza się w prawo lub lewo nad taśmą),
*   układu sterowania głowicą.

W ujęciu formalnym maszynę Turinga $M_T$ definiujemy jako siódemkę:
$$ M_T = \langle Q, \Gamma, b, \Sigma, \delta, q_0, F \rangle $$
Gdzie:
*   $Q$ – skończony zbiór stanów $q_i$ maszyny.
*   $\Gamma$ – skończony zbiór symboli taśmowych (przy czym $\Sigma \subseteq \Gamma$).
*   $b$ – symbol pusty, wypełniający początkową taśmę.
*   $\Sigma$ – skończony zbiór symboli wejściowych.
*   $\delta$ – funkcja przejścia zdefiniowana jako $\delta(q_i, X) = (q_j, Y, \pm)$. Oznacza to, że będąc w stanie $q_i$ i napotykając symbol $X$, głowica zapisze znak $Y$, przejdzie do stanu $q_j$ i przesunie się o jedną komórkę w wybraną stronę ($\pm$).
*   $q_0$ – stan początkowy maszyny.
*   $F$ – zbiór stanów akceptujących ($F \subset Q$), po osiągnięciu których maszyna kończy działanie.

Maszyna $M_T$ działa, dopóki nie osiągnie stanu akceptującego $f \in F$ lub nie napotka symbolu $X \notin \Sigma$ (co skutkuje błędem).
### Język Maszyny Turinga
Językiem maszyny Turinga $M_T$  nazwiemy zbiór słów wejściowych, dla których całe obliczenia maszyny zakończą się w stanie akceptującym $f∈F$. Będziemy mówić wtedy, że maszyna Turinga $M_T$  rozpoznaje język, oznaczany jako $\mathcal{L}(M_T)$.

Język $\mathcal{L}$ nazywamy częściowo rozstrzygalnym, jeżeli istnieje taka maszyna $M_T$, że $\mathcal{L}=\mathcal{L}(M_T)$.

Mówimy, że $M_T$ ma własność stopu, jeżeli dla dowolnego słowa $X\in\Sigma$ obliczenia $M_{T}$ się zakończą. 
### Reprezentacja i parametry maszyny
Działanie maszyny $M_T$ definiujemy za pomocą tabeli instrukcji zawierającej wartości funkcji przejścia dla poszczególnych stanów i odczytanych liter z alfabetu. Zwykle symbol pusty $b$ określa się znakiem `#`.

Czas obliczeń maszyny $M_T$ na konkretnym słowie wejściowym $\sigma$ oznaczamy jako $T(M_T, \sigma)$, jako wartość zwraca on liczbę kroków wykonanych zanim maszyna się zatrzymała. Jeżeli $M_{T}$ nigdy się nie zatrzyma, mówimy że jej czas obliczeń jest nieskończony i oznaczamy jako $T(M_T, σ)=∞$.

Pamięć potrzebną do obliczeń maszyny $M_T$ na słowie wejściowym $\sigma$ oznaczamy jako $S(M_T, \sigma)$ i definiujemy jako liczbę komórek taśmy, które zostały odwiedzone przez głowicę zanim maszyna się zatrzymała.
## Pracowity Bóbr (Busy Beaver)
**Pracowitym Bobrem** nazywamy maszynę Turinga o zadanej z góry liczbie stanów $N$, która zaczynając od pustej taśmy wykonuje **jak największą** liczbę kroków, po czym samoczynnie się zatrzymuje.

Funkcja pracowitego bobra $\Sigma(N)$ (lub $\text{BB}(N)$) przyjmuje jako argument liczbę stanów $N$ i zwraca maksymalną liczbę kroków do wykonania przed zatrzymaniem. 

**Znane wartości i szacowania dolne:**
*   $\Sigma(2) = 4$
*   $\Sigma(3) = 6$
*   $\Sigma(4) = 13$
*   $\Sigma(5) = 4098$
*   $\Sigma(6) > 2^{111^5}$
*   $\Sigma(7) > 2^{111^{2^{111^3}}}$

Tibor Rado udowodnił, że funkcja $\Sigma$ jest **nieobliczalna** – nie istnieje jakakolwiek funkcja obliczalna, która mogłaby ograniczyć $\Sigma$ od góry:
$$ \forall_f \exists_n : f(n) < \Sigma(n) $$
## Procedury i Obliczalność
**Algorytmem** nazywamy procedurę spełniającą trzy ścisłe założenia:
 1. **Skończoność:** Musi zatrzymać się po wykonaniu skończonej liczby kroków.
 2. **Determinizm:** Dla tych samych danych wejściowych algorytm zawsze musi dać ten sam, jasno określony wynik.
 3. **Efektywność:** Każdy krok musi być na tyle prosty, by mógł zostać wykonany (np. przez człowieka z kartką) w skończonym czasie.

**Funkcją nieobliczalną** nazywamy funkcję $g$, dla której nie istnieje algorytm (a co za tym idzie program komputerowy), który byłby w stanie obliczyć wartość funkcji $g(x)$ dla dowolnego argumentu wejściowego $x$ w **skończonym** czasie.

Tym samym funkcję $f$ nazywamy **funkcją obliczalną**, jeżeli istnieje algorytm, który dla dowolnego argumentu wejściowego $y$, zwróci nam wartość funkcji $f(y)$.