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
Dowolną amplitudę $\alpha$ możemy przedstawić w postaci wykładniczej jako $r e^{i\varphi}$, gdzie $r$ jest modułem, $\varphi$ fazą, $e$ to liczba Eulera, a $i$ to jednostka urojona.

Liczby $1, -1, i, -i$ mają ten sam moduł równy $1$, ale ich fazy $0, \pi, \frac{\pi}{2}, -\frac{\pi}{2}$ są różne. Faza nie zmienia bezpośrednio prawdopodobieństwa $|\alpha|^2$ ale wpływa na interferencję.

## Dualizm korpuskularno-falowy
**Dualizm korpuskularno-falowy** (ang. *wave-particle duality*) to właściwość układów kwantowych, takich jak fotony czy elektrony, polegająca na tym, że w zależności od sposobu przeprowadzenia eksperymentu wykazują one cechy charakterystyczne zarówno dla fal, jak i dla cząstek.

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

Składnik $2\cdot\mathfrak{R}(A_{1}^*(x)A_{2}(x))$ odpowiada za rodzaj interferencji:
- **Interferencja konstruktywna** – amplitudy wzmacniają się, zwiększając prawdopodobieństwo detekcji.
- **Interferencja destruktywna** – amplitudy znoszą się, zmniejszając prawdopodobieństwo detekcji.

Wielokrotne detekcje tworzą prążki interferencyjne. Gdy informacje o drodze pozwalają w pełni rozróżnić szczeliny, interferencja zanika. Nie jest do tego potrzebna obecność świadomego obserwatora: istotna jest fizyczna dostępność informacji o drodze.

## Interpretacja wielu światów
**Interpretacja wielu światów** (ang. *Many-Worlds Interpretation*) MWI, nazywana również **interpretacją Everetta**, to jedna z interpretacji mechaniki kwantowej, zaproponowana przez Hugh Everetta III w 1957 roku.

Zakłada ona, że funkcja falowa całego układu ewoluuje zgodnie z równaniami mechaniki kwantowej, bez fizycznego kolapsu funkcji falowej podczas pomiaru.

W przeciwieństwie do standardowego opisu pomiaru z postulatem kolapsu, interpretacja Everetta zakłada, że wszystkie możliwe wyniki pomiaru o niezerowych amplitudach występują w różnych gałęziach stanu kwantowego.

## Równomierna superpozycja
**Równomierna superpozycja** dwóch stanów bazowych oznacza jednakowe moduły odpowiadających im amplitud. Przykładami równomiernych superpozycji są:

$$\ket{+}=\frac{1}{\sqrt{ 2 }}\ket{0}+\frac{1}{\sqrt{ 2 }}\ket{1}=\frac{\ket{0} + \ket{1}  }{\sqrt{ 2 }}$$

$$\ket{-}=\frac{1}{\sqrt{ 2 }}\ket{0}-\frac{1}{\sqrt{ 2 }}\ket{1}=\frac{\ket{0} - \ket{1}  }{\sqrt{ 2 }}$$

Pomiar stanu $\ket{+}$ w bazie obliczeniowej $\{\ket{0}, \ket{1}\}$ daje:

$$P(0)=P(1)=\frac{1}{2}$$

Stany $\ket{+}$ i $\ket{-}$ mają taki sam rozkład wyników w bazie obliczeniowej $\{\ket{0},\ket{1}\}$, ale różnią się **fazą względną** i można je bezbłędnie rozróżnić przy pomiarze w bazie $\{\ket{+},\ket{-}\}$.

## Bazy
**Baza pomiarowa** określa, jakie rozłączne wyniki można uzyskać w danym pomiarze projekcyjnym i którym stanom one odpowiadają. Bazę pomiarową kubitu w przypadku pomiaru projekcyjnego stanowi para ortonormalnych stanów kwantowych, wśród najważniejszych baz wyróżniamy:
- **Baza obliczeniowa** $Z$:  

$$ \mathcal{B}_{Z}=\{\ket{0}, \ket{1}  \} $$

- **Baza diagonalna** $X$:
  
$$\mathcal{B}_{X}=\{\ket{+}, \ket{-}  \}$$
  
Ten sam stan może dawać różne prawdopodobieństwa zależnie od wybranej bazy. Na przykład pomiar $\ket{+}$ w bazie $Z$ daje $0$ lub $1$ z prawdopodobieństwem $0.5$, a w bazie $X$ daje wynik $+$ z prawdopodobieństwem $1$

W przypadku polaryzacji fotonu możemy utożsamić:

$$\ket{H}\equiv\ket{0},\qquad \ket{V}\equiv\ket{1},$$

$$\ket{D}=\frac{\ket{H}+\ket{V}}{\sqrt2},\qquad
\ket{A}=\frac{\ket{H}-\ket{V}}{\sqrt2}.$$

Litery $H,V$ oznaczają polaryzacje poziomą i pionową, a $D,A$ – dwie prostopadłe polaryzacje diagonalne. Pomiar stanu $\ket{H}$ w bazie $\{\ket{D},\ket{A}\}$ daje każdy wynik z prawdopodobieństwem $0.5$.

## Twierdzenie o nieklonowaniu
**Twierdzenie o nieklonowaniu** (ang. *no-cloning theorem*) mówi, że:

>[!danger] Twierdzenie o nieklonowaniu
> Nie istnieje uniwersalna operacja kwantowa $U$ pozwalająca utworzyć idealną kopię dowolnego nieznanego stanu kwantowego, pozostawiając oryginał.

Hipotetyczna uniwersalna operacja kopiująca $U$ musiałaby dla każdego stanu $\ket\psi$ spełniać:

$$U\ket{\psi}\ket{0}=\ket\psi\ket\psi.$$

Nie może to zachodzić dla dowolnej pary różnych, nieortogonalnych stanów. Nieklonowanie nie zabrania kopiowania znanych stanów ani rozróżnialnych stanów ortogonalnych.

W kryptografii kwantowej podsłuchująca osoba nie może po prostu zachować doskonałej kopii każdego przesyłanego, nieznanego kubitu. Próba zdobycia informacji przez pomiar w niewłaściwej bazie może zaburzyć transmisję i ujawnić podsłuch.

## Dwa kubity
Układ pary kubitów $A,B$ ma cztery stany bazowe:

$$\{\ket{00}, \ket{01}, \ket{10}, \ket{11}    \}$$
Przykładowo $\ket{01}$ oznacza stan, w którym pierwszy kubit $A$ jest w stanie $\ket0$, a drugi $B$ w stanie $\ket1$.

Dowolny **czysty stan** dwóch kubitów można zapisać jako:

$$\ket\Psi=a\ket{00}+b\ket{01}+c\ket{10}+d\ket{11},$$

gdzie $a,b,c,d\in\mathbb C$ oraz $|a|^2+|b|^2+|c|^2+|d|^2=1$.

Nie każdy wspólny czysty stan można przedstawić jako kombinację dwóch niezależnie określonych czystych stanów kubitów. Stan, który **można** zapisać jako $\ket\psi_A\otimes\ket\phi_B$, nazywamy **separowalnym**. Jeśli takiego rozkładu nie ma, stan jest **splątany**. Symbol $\otimes$ oznacza iloczyn tensorowy.

## Stan splątany Bella
**Splątanie kwantowe** (ang. *quantum entanglement*) jest właściwością stanu złożonego układu, który – w przypadku stanów czystych – nie daje się zapisać jako iloczyn tensorowy stanów jego podukładów.

Przykładem jest jeden ze **stanów Bella**:

$$\ket{\Phi^+}=\frac{\ket{00}+\ket{11}}{\sqrt2}.$$

W przypadku pomiaru obu kubitów w bazie obliczeniowej $Z$:

$$P(00)=P(11)=\frac12,\qquad P(01)=P(10)=0.$$

Oznacza to, że wynik pomiaru każdego kubitu osobno jest losowy, ale wyniki obu kubitów są doskonale skorelowane: zawsze są równe.

Sama zgodność wyników w jednej bazie nie dowodzi splątania, ponieważ podobne korelacje mogą powstawać również w klasycznych mieszaninach. Kwantowy charakter tego stanu jest związany z jego nierozkładalnością na stany pojedynczych kubitów i korelacjami dostępnymi w różnych bazach.

Jeśli Alicja i Bob otrzymają po jednym kubicie takiej pary, nie mogą za jej pomocą przesłać użytecznej informacji szybciej od światła: każde z nich otrzymuje lokalnie losowe wyniki.

Stany Bella to cztery wzajemnie ortogonalne, maksymalnie splątane czyste stany układu dwóch kubitów:

$$
\begin{aligned}
\ket{\Phi^+}&=\frac{\ket{00}+\ket{11}}{\sqrt2}\\[6pt]
\ket{\Phi^-}&=\frac{\ket{00}-\ket{11}}{\sqrt2}\\[6pt]
\ket{\Psi^+}&=\frac{\ket{01}+\ket{10}}{\sqrt2}\\[6pt]
\ket{\Psi^-}&=\frac{\ket{01}-\ket{10}}{\sqrt2}
\end{aligned}
$$

## Paradoks EPR
**Paradoks EPR** (ang. _Einstein–Podolsky–Rosen paradox_) to eksperyment myślowy zaproponowany w 1935 roku przez Alberta Einsteina, Borisa Podolskiego i Nathana Rosena, którego celem było zakwestionowanie kompletności mechaniki kwantowej.

Paradoks opiera się na trzech podstawowych założeniach:
1. **Realizm** – wielkości fizyczne mogą mieć określone wartości niezależnie od ich pomiaru.
2. **Lokalność** – działania wykonywane na jednym układzie nie mogą natychmiastowo wpływać na odległy układ.
3. **Kompletność teorii** – teoria fizyczna powinna opisywać wszystkie elementy rzeczywistości fizycznej.

Rozważmy dwa kubity znajdujące się w stanie splątanym Bella:

$$
\ket{\Phi^+}=
\frac{\ket{00}+\ket{11}}{\sqrt2}
$$

Następnie rozdzielmy je między dwie osoby:
- **Alicja** otrzymuje pierwszy kubit.
- **Bob** otrzymuje drugi kubit.

Załóżmy, że Alicja i Bob znajdują się bardzo daleko od siebie.

Jeżeli oboje wykonają pomiar w bazie obliczeniowej: $\mathcal B_Z=\{\ket0,\ket1\}$ otrzymają doskonale skorelowane wyniki:

$$
P(00)=P(11)=\frac12
$$
$$
P(01)=P(10)=0
$$

Oznacza to, że jeśli Alicja uzyska wynik $0$, może przewidzieć, że Bob również otrzyma $0$. Analogicznie, jeśli Alicja otrzyma $1$, Bob również otrzyma $1$. Paradoks EPR nie dowodzi możliwości przesyłania informacji szybciej od światła.

## Nierówności Bella
**Nierówności Bella** (ang. _Bell inequalities_) to zależności matematyczne ograniczające możliwe korelacje między wynikami pomiarów w teoriach spełniających określone założenia lokalności i realizmu. Zostały wprowadzone przez Johna Stewarta Bella w 1964 roku.

Naruszenie odpowiedniej nierówności Bella oznacza, że zaobserwowanych korelacji nie można wyjaśnić za pomocą lokalnych modeli zmiennych ukrytych spełniających założenia wykorzystane przy jej wyprowadzeniu.

## Nierówność CHSH
**Nierówność CHSH** (ang. _Clauser–Horne–Shimony–Holt inequality_) to szczególna postać nierówności Bella, sformułowana w 1969 roku przez Johna Clausera, Michaela Horne'a, Abnera Shimony'ego i Richarda Holta.

Pozwala sprawdzić, czy korelacje między wynikami pomiarów dwóch odległych układów mogą zostać opisane przez lokalny model zmiennych ukrytych.

Załóżmy, że Alicja i Bob otrzymują parę splątanych kubitów. Alicja może wybrać jedno z dwóch ustawień pomiarowych: $a,a'$. Bob również może wybrać jedno z dwóch ustawień: $b, b'$ Każdy pomiar daje wynik ze zbioru: $\{-1,+1\}$.

Dla ustalonych ustawień pomiarowych $a,b$ definiujemy korelację:

$$E(a,b)=P(A=B)-P(A\neq B)$$

gdzie $A,B\in\{-1,+1\}$ to wyniki pomiarów.

Korelacja spełnia:

$$-1\le E(a,b)\le1$$
Interpretacja:
- $E(a,b)=1$ – wyniki są zawsze zgodne
- $E(a,b)=-1$ – wyniki są zawsze przeciwne.
- $E(a,b)=0$ – brak korelacji mierzonej tą wielkością.

Na podstawie czterech korelacji definiujemy parametr CHSH $S$:

$$
S=
E(a,b)-E(a,b')
+E(a',b)+E(a',b')
$$

Parametr $S$ pozwala porównać przewidywania lokalnych modeli zmiennych ukrytych z przewidywaniami mechaniki kwantowej.

Dla lokalnych modeli zmiennych ukrytych zachodzi:

$$|S|\le2$$

Oznacza to, że niezależnie od doboru ustawień pomiarowych lokalny model spełniający założenia CHSH nie może przekroczyć wartości $2$.

Mechanika kwantowa dopuszcza:

$$|S|\le2\sqrt2$$

Wartość $2\sqrt2\approx2{,}828$ nazywamy **granicą Tsirelsona** (ang. _Tsirelson bound_).

Ponieważ:

$$2\sqrt2>2$$

mechanika kwantowa przewiduje korelacje, których nie można odtworzyć za pomocą lokalnych modeli zmiennych ukrytych.