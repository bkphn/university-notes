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

*Wprowadzane są podstawowe idee mechaniki kwantowej wykorzystywane w przetwarzaniu informacji: dualizm korpuskularno-falowy, superpozycja, interferencja, pomiar kwantowy, zasada nieoznaczoności, splątanie oraz twierdzenie o niemożności klonowania nieznanego stanu kwantowego.*
