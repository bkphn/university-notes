## Kubity
**Bitem** (z ang. *binary digit*) nazywamy najmniejszą jednostkę w teorii informacji i informatyce. Klasyczny bit $b$ może przyjmować jedną z dwóch wartości: `False` albo `True` reprezentowanych zazwyczaj przez cyfry $0,1$:

$$b\in\{0,1\}$$

Losowy bit możemy opisać rozkładem klasycznym:

$$P(0)=p \qquad P(1)=1-p$$

**Kubitem** (ang. *qubit*) nazywamy podstawową jednostkę informacji kwantowej – jest to odpowiednik bitu w komputerach kwantowych. Dowolny kubit
może znajdować się w **superpozycji** stanów $\ket{0}$ i $\ket{1}$.

## Stan kwantowy
**Stan kwantowy** (ang. *quantum state*) to matematyczny opis układu fizycznego, który pozwala przewidywać prawdopodobieństwa wyników pomiarów wykonywanych na tym układzie. Najprostszym możliwym układem dwupoziomowym jest kubit.

**Superpozycja kwantowa** (ang. *quantum superposition*) to możliwość przedstawienia czystego stanu kwantowego jako kombinacji stanów. W przypadku kubitu możemy reprezentować jego stan $\ket{\psi}$ jako kombinację stanów $\ket{0}$ i $\ket{1}$:

$$\ket{\psi}=\alpha \ket{0}+\beta \ket{1}   $$

gdzie $\alpha,\beta\in\mathbb{C}$ są **amplitudami** (nie prawdopodobieństwami). Stan przed pomiarem nie musi mieć jednej wartości – może być w superpozycji stanów $\ket{0}$ i $\ket{1}$. Wynik pomiaru kubitu w bazie obliczeniowej jest klasyczny i może przyjmować wartość $0$ albo $1$. W przypadku idealnego pomiaru projekcyjnego stan kwantowy po pomiarze odpowiada otrzymanemu wynikowi: $\ket{0}$ albo $\ket{1}$.

## Reguła Borna
**Reguła Borna** (ang. *Born rule*) to jedna z fundamentalnych zasad mechaniki kwantowej, która pozwala obliczyć prawdopodobieństwo otrzymania określonego wyniku pomiaru na podstawie stanu kwantowego układu.

Została sformułowana przez Maxa Borna w 1926 roku, a najważniejsza idea brzmi:

>[!danger] Reguła Borna
> Prawdopodobieństwo otrzymania określonego wyniku pomiaru jest równe kwadratowi modułu odpowiadającej mu amplitudy prawdopodobieństwa

Amplitudy $\alpha,\beta$ muszą spełniać warunek normalizacji:

$$|\alpha|^2+|\beta|^2=1$$

wtedy prawdopodobieństwo, że wynik pomiaru kubitu $\ket{\psi}=\alpha \ket{0}+\beta \ket{1}$ przyjmie wartości $0$ i $1$ wynoszą kolejno:

$$P(0)=|\alpha|^2, \qquad P(1)=|\beta|^2$$

>[!example] Przykład normalizacji
>0. Dany jest nieznormalizowany wektor: 
>   
>   $$\ket{\phi}=3\ket{0}+4i\ket{1}$$
>   
>1. Obliczamy jego normę: 
>   
>  $$\|\phi\|=\sqrt{ |3|^2  + |4i|^2}=\sqrt{ 9+16 }=5$$ 
>  
> 2. Stan znormalizowany
>    
>    $$\ket{\psi} = \frac{\ket{\phi}}{\|\phi\|} = \frac{3}{5}\ket{0} + \frac{4i}{5} \ket{1}  $$
>    
> 3. Kontrola:
>   
 > $$\left|\frac{3}{5}\right|^2+\left| \frac{4i}{5}\right|^2 = \frac{9}{25}+\frac{16}{25}=1$$

## Liczby zespolone
Dowolną amplitudę $\alpha$ możemy przedstawić w postaci iloczynowej jako $r e^{i\varphi}$, gdzie $r$ jest modułem, $\varphi$ fazą, $e$ to liczba Eulera, a $i$ to jednostka urojona.

Liczby $1, -1, i, -i$ mają ten sam moduł równy $1$, ale ich fazy $0, \pi, \frac{\pi}{2}, -\frac{\pi}{2}$ są różne. Faza nie zmienia bezpośrednio prawdopodobieństwa $|\alpha|^2$ ale wpływa na interferencję.

## Dualizm korpuskularno-falowy
**Dualizm korpuskularno-falowy** (ang. *wave-particle duality*) to właściwość układów kwantowych, takich jak fotony czy elektrony, polegająca na tym, że w zależności od sposobu przeprowadzenia eksperymentu wykazują one cechy charakterystyczna zarówno dla fal, jak i dla cząstek.

**Eksperyment Younga** (ang. *Young's double-slit experiment*), nazywany również **doświadczeniem z dwiema szczelinami**, to eksperyment fizyczny demonstrujący zjawisko interferencji fal. Jego kwantowa wersja stanowi jeden z najważniejszych przykładów ilustrujących dualizm korpuskularno-falowy.

Układ eksperymentalny składa się z trzech podstawowych elementów:
1. **Źródła** – emituje światło lub cząstki, np. fotony albo elektrony.
2. **Przegrody z dwiema szczelinami** – umożliwia przejście przez jedną z dwóch dróg.
3. **Ekranu detekcyjnego** – rejestruje miejsca trafienia cząstek.

Niech: $A_1(x)$ oznacza amplitudę kwantową związaną z pierwszą szczeliną, $A_2(x)$ amplitudę kwantową związaną z drugą szczeliną, a $A(x)$ całkowitą amplitudę detekcji w punkcie $x$.

Jeżeli nie dokonujemy pomiaru, amplitudy sumują się:

$$ A(x)=A_1(x)+A_2(x) $$

Zgodnie z regułą Borna prawdopodobieństwo detekcji w punkcie $x$ wynosi:

$$P(x)=|A_1(x)+A_2(x)|^2=|A_1(x)|^2+|A_2(x)|^2+
2\cdot\mathfrak{R}\left(A_1^*(x)A_2(x)\right)$$

gdzie $\mathfrak{R}$ oznacza część rzeczywistą liczby zespolonej, a $A_1^*$ jej sprzężenie zespolone.

Składnik $2\mathfrak{R}(A_{1}^*(x)A_{2}(x))$ odpowiada za rodzaj interferencji:
- **Interferencja konstruktywna** – amplitudy wzmacniają się, zwiększając prawdopodobieństwo detekcji.
- **Interferencja destruktywna** – amplitudy znoszą się, zmniejszając prawdopodobieństwo detekcji.

Właśnie w ten sposób powstają charakterystyczne prążki interferencyjne.

## Równomierna superpozycja


## Bazy


## Twierdzenie o nieklonowaniu


## Dwa kubity


## Stan splątany Bella


## 

*Wprowadzane są podstawowe idee mechaniki kwantowej wykorzystywane w przetwarzaniu informacji: dualizm korpuskularno-falowy, superpozycja, interferencja, pomiar kwantowy, zasada nieoznaczoności, splątanie oraz twierdzenie o niemożności klonowania nieznanego stanu kwantowego.*
