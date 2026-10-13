## Kubity

**Bitem** (ang. *binary digit*) nazywamy podstawową jednostkę informacji klasycznej. Bit $b$ przyjmuje jedną z dwóch wartości, zwykle oznaczanych jako $0$ i $1$:

$$b\in\{0,1\}.$$

Losowy bit można opisać rozkładem prawdopodobieństwa:

$$P(b=0)=p,\qquad P(b=1)=1-p,\qquad p\in[0,1].$$

**Kubitem** (ang. *qubit*) nazywamy podstawową jednostkę informacji kwantowej, reprezentowaną przez układ dwupoziomowy. Czysty stan kubitu może być **superpozycją** stanów $\ket{0}$ i $\ket{1}$.

## Stan kwantowy

**Stan kwantowy** (ang. *quantum state*) to matematyczny opis układu fizycznego, pozwalający przewidywać prawdopodobieństwa wyników pomiarów. Przykładem układu dwupoziomowego jest kubit.

**Superpozycja kwantowa** (ang. *quantum superposition*) to możliwość przedstawienia czystego stanu jako kombinacji liniowej wektorów stanów. Czysty stan kubitu możemy zapisać jako:

$$\ket{\psi}=\alpha\ket{0}+\beta\ket{1},$$

gdzie $\alpha,\beta\in\mathbb C$ są **amplitudami prawdopodobieństwa**, a nie samymi prawdopodobieństwami. Kubit nie musi mieć przed pomiarem jednej ustalonej wartości klasycznego bitu. Pomiar w bazie obliczeniowej daje klasyczny wynik $0$ lub $1$. Po idealnym pomiarze projekcyjnym stan kubitu odpowiada uzyskanemu wynikowi: jest to $\ket{0}$ albo $\ket{1}$.

## Reguła Borna

**Reguła Borna** (ang. *Born rule*) pozwala obliczać prawdopodobieństwa wyników pomiaru z amplitud. Sformułował ją Max Born w 1926 roku.

> [!important] Reguła Borna
> Prawdopodobieństwo danego wyniku pomiaru jest kwadratem modułu odpowiadającej mu amplitudy prawdopodobieństwa.

Wektor stanu kubitu musi spełniać **warunek normalizacji**:

$$|\alpha|^2+|\beta|^2=1.$$

W przypadku pomiaru w bazie obliczeniowej $\{\ket{0},\ket{1}\}$:

$$P(0)=|\alpha|^2,\qquad P(1)=|\beta|^2.$$

> [!example] Przykład normalizacji
> Nieznormalizowany wektor:
>
> $$\ket{\phi}=3\ket{0}+4i\ket{1}.$$
>
> Jego norma:
>
> $$\|\phi\|=\sqrt{|3|^2+|4i|^2}=\sqrt{9+16}=5.$$
>
> Stan znormalizowany:
>
> $$\ket{\psi}=\frac{\ket{\phi}}{\|\phi\|}=\frac35\ket{0}+\frac{4i}{5}\ket{1}.$$
>
> Kontrola:
>
> $$\left|\frac35\right|^2+\left|\frac{4i}{5}\right|^2=\frac9{25}+\frac{16}{25}=1.$$

## Liczby zespolone

Amplitudę zespoloną $\alpha$ można przedstawić w **postaci wykładniczej**:

$$\alpha=re^{i\varphi},$$

gdzie $r=|\alpha|$ jest modułem, $\varphi$ fazą, a $i$ jednostką urojoną.

Liczby $1$, $-1$, $i$, $-i$ mają moduł równy $1$, lecz różne fazy: odpowiednio $0$, $\pi$, $\pi/2$, $-\pi/2$ (z dokładnością do wielokrotności $2\pi$). Faza amplitudy nie zmienia jej kwadratu modułu, ale **różnice faz** wpływają na interferencję.

## Dualizm korpuskularno-falowy

**Dualizm korpuskularno-falowy** (ang. *wave-particle duality*) to właściwość obiektów kwantowych (np. fotonów i elektronów), które mogą wykazywać cechy falowe, takie jak interferencja, oraz cechy korpuskularne, takie jak pojedyncze, zlokalizowane zdarzenia detekcji.

**Eksperyment Younga** (ang. *Young's double-slit experiment*), czyli doświadczenie z dwiema szczelinami, ilustruje interferencję i dualizm korpuskularno-falowy. Układ składa się ze źródła, przegrody z dwiema szczelinami oraz ekranu detekcyjnego.

Niech $A_1(x)$ i $A_2(x)$ oznaczają amplitudy prowadzące do detekcji w punkcie $x$ przez odpowiednie szczeliny. **Jeżeli drogi są nierozróżnialne**, amplitudy dodają się:

$$A(x)=A_1(x)+A_2(x).$$

Kwadrat modułu całkowitej amplitudy wyznacza gęstość prawdopodobieństwa detekcji (przy odpowiedniej normalizacji amplitud):

$$p(x)=|A_1(x)+A_2(x)|^2$$

$$=|A_1(x)|^2+|A_2(x)|^2+2\operatorname{Re}(A_1^*(x)A_2(x)).$$

Ostatni wyraz jest **składnikiem interferencyjnym**:

- **Interferencja konstruktywna** – amplitudy wzmacniają się, zwiększając gęstość prawdopodobieństwa detekcji.
- **Interferencja destruktywna** – amplitudy częściowo lub całkowicie się znoszą, zmniejszając gęstość prawdopodobieństwa detekcji.

Wielokrotne detekcje tworzą prążki interferencyjne. Gdy informacje o drodze pozwalają w pełni rozróżnić szczeliny, interferencja zanika. Nie jest do tego potrzebna obecność świadomego obserwatora: istotna jest fizyczna dostępność informacji o drodze.

> [!note] Uwaga probabilistyczna
> Dla ciągłego położenia $x$ ściślej mówi się o **gęstości prawdopodobieństwa** $p(x)$, a nie o prawdopodobieństwie trafienia dokładnie w punkt $x$. Prezentacja stosuje uproszczony zapis $P(x)$.

## Równomierna superpozycja

**Równomierna superpozycja** dwóch stanów bazowych oznacza jednakowe moduły odpowiadających im amplitud. Przykładem jest stan:

$$\ket{+}=\frac{\ket{0}+\ket{1}}{\sqrt2}.$$

Jego pomiar w bazie obliczeniowej daje:

$$P(0)=P(1)=\frac12.$$

Stan $\ket{+}$ **nie jest klasyczną mieszaniną**, w której połowę układów przygotowano w stanie $\ket{0}$, a drugą połowę w stanie $\ket{1}$. Oba przygotowania dają wyniki $50\%/50\%$ w bazie obliczeniowej, ale różnią się przy pomiarze w innej bazie, ponieważ superpozycja zachowuje fazę względną, umożliwiając interferencję.

Podobnym stanem jest:

$$\ket{-}=\frac{\ket{0}-\ket{1}}{\sqrt2}.$$

Stany $\ket{+}$ i $\ket{-}$ mają taki sam rozkład wyników w bazie obliczeniowej, ale różnią się **fazą względną** i można je bezbłędnie rozróżnić przy pomiarze w bazie $\{\ket{+},\ket{-}\}$.

## Bazy

**Baza pomiarowa** określa, jakie rozłączne wyniki można uzyskać w danym pomiarze projekcyjnym i którym stanom one odpowiadają. Dla kubitu rozważamy między innymi dwie bazy:

- **Baza obliczeniowa $Z$:** $\{\ket{0},\ket{1}\}$.
- **Baza diagonalna $X$:** $\{\ket{+},\ket{-}\}$.

Ten sam stan może dawać różne prawdopodobieństwa zależnie od wybranej bazy. Na przykład pomiar $\ket{+}$ w bazie $Z$ daje $0$ lub $1$ z prawdopodobieństwem $1/2$, a w bazie $X$ daje wynik $+$ z prawdopodobieństwem $1$.

W przypadku polaryzacji fotonu możemy utożsamić:

$$\ket{H}\equiv\ket{0},\qquad \ket{V}\equiv\ket{1},$$

$$\ket{D}=\frac{\ket{H}+\ket{V}}{\sqrt2},\qquad
\ket{A}=\frac{\ket{H}-\ket{V}}{\sqrt2}.$$

Litery $H,V$ oznaczają polaryzacje poziomą i pionową, a $D,A$ – dwie prostopadłe polaryzacje diagonalne. Pomiar stanu $\ket{H}$ w bazie $\{\ket{D},\ket{A}\}$ daje każdy wynik z prawdopodobieństwem $1/2$.

## Pomiar kwantowy

**Pomiar kwantowy** (ang. *quantum measurement*) to fizyczna procedura, która dostarcza klasycznego wyniku zależnego od stanu kwantowego i rodzaju pomiaru.

Dla kubitu $\ket{\psi}=\alpha\ket0+\beta\ket1$ pomiar w bazie obliczeniowej daje:

$$P(0)=|\alpha|^2,\qquad P(1)=|\beta|^2.$$

W przypadku **idealnego pomiaru projekcyjnego** uzyskanie wyniku $0$ pozostawia kubit w stanie $\ket0$, a wyniku $1$ – w stanie $\ket1$. Pomiar może więc zmienić stan; nie musi go jednak zmieniać, jeśli układ już znajduje się w stanie odpowiadającym wynikowi.

Informacja o drodze w eksperymencie Younga pokazuje, że pomiar umożliwiający rozróżnienie alternatyw może usunąć interferencję.

## Zasada nieoznaczoności

> [!warning] Uzupełnienie spoza prezentacji
> Zasada nieoznaczoności występuje w sylabusie wykładu 1, ale **nie ma jej osobnego omówienia na slajdach**. Poniższy fragment opiera się na dodatkowych źródłach akademickich.

**Zasada nieoznaczoności Heisenberga** głosi, że w żadnym stanie kwantowym rozrzuty wyników pomiaru pewnych par wielkości fizycznych, np. położenia i pędu, nie mogą być jednocześnie dowolnie małe.

Dla położenia $x$ i odpowiadającej mu składowej pędu $p_x$:

$$\Delta x\,\Delta p_x\geq\frac{\hbar}{2},\qquad \hbar=\frac{h}{2\pi},$$

gdzie $\Delta x$ i $\Delta p_x$ oznaczają odchylenia standardowe rozkładów wyników pomiarów w danym stanie, a $h$ jest stałą Plancka.

Im węższy jest rozkład położenia, tym szerszy musi być rozkład pędu. **Nie wynika to wyłącznie z niedoskonałości aparatury pomiarowej**: ograniczenie dotyczy właściwości samych stanów kwantowych. Nie należy utożsamiać tego związku z prostym twierdzeniem, że każdy pomiar jednej wielkości mechanicznie zaburza drugą.

Źródła zewnętrzne: [Stanford Encyclopedia of Philosophy, *The Uncertainty Principle*, §2.5 i §6](https://plato.stanford.edu/entries/qt-uncertainty/); [MIT OpenCourseWare, *Quantum Physics I*, Lecture 4: Expectations, Momentum, and Uncertainty](https://ocw.mit.edu/courses/8-04-quantum-physics-i-spring-2013/resources/mit8_04s13_lec04/).

## Twierdzenie o nieklonowaniu

**Twierdzenie o nieklonowaniu** (ang. *no-cloning theorem*) mówi, że **nie istnieje uniwersalna operacja kwantowa pozwalająca utworzyć idealną kopię dowolnego nieznanego stanu kwantowego, pozostawiając oryginał**.

Hipotetyczna operacja kopiująca musiałaby dla każdego stanu $\ket\psi$ spełniać:

$$U\bigl(\ket\psi\ket0\bigr)=\ket\psi\ket\psi.$$

Na slajdzie 18 wykładowca wskazuje, że zachowanie iloczynów skalarnych przez operację unitarną prowadziłoby dla dwóch kopiowanych stanów do warunku:

$$\langle\psi|\phi\rangle=\bigl(\langle\psi|\phi\rangle\bigr)^2.$$

Nie może on zachodzić dla dowolnej pary różnych, nieortogonalnych stanów. **Nieklonowanie nie zabrania** kopiowania znanych stanów ani rozróżnialnych stanów ortogonalnych.

W kryptografii kwantowej podsłuchująca osoba nie może po prostu zachować doskonałej kopii każdego przesyłanego, nieznanego kubitu. Próba zdobycia informacji przez pomiar w niewłaściwej bazie może zaburzyć transmisję i ujawnić podsłuch.

## Dwa kubity

Układ dwóch kubitów ma **cztery stany bazowe**:

$$\{\ket{00},\ket{01},\ket{10},\ket{11}\}.$$

Przykładowo $\ket{01}$ oznacza stan, w którym pierwszy kubit jest w stanie $\ket0$, a drugi w stanie $\ket1$.

Dowolny **czysty stan** dwóch kubitów można zapisać jako:

$$\ket\Psi=a\ket{00}+b\ket{01}+c\ket{10}+d\ket{11},$$

gdzie $a,b,c,d\in\mathbb C$ oraz:

$$|a|^2+|b|^2+|c|^2+|d|^2=1.$$

Nie każdy wspólny czysty stan można przedstawić jako kombinację dwóch niezależnie określonych czystych stanów kubitów. Stan, który **można** zapisać jako $\ket\psi_A\otimes\ket\phi_B$, nazywamy **separowalnym**. Jeśli takiego rozkładu nie ma, stan jest **splątany**. Symbol $\otimes$ oznacza iloczyn tensorowy; jego formalne własności będą omówione na kolejnym wykładzie.

## Stan splątany Bella

**Splątanie kwantowe** (ang. *quantum entanglement*) jest właściwością stanu złożonego układu, który – w przypadku stanów czystych – nie daje się zapisać jako iloczyn stanów jego podukładów.

Przykładem jest jeden ze **stanów Bella**:

$$\ket{\Phi^+}=\frac{\ket{00}+\ket{11}}{\sqrt2}.$$

W przypadku pomiaru obu kubitów w bazie obliczeniowej:

$$P(00)=P(11)=\frac12,\qquad P(01)=P(10)=0.$$

Oznacza to, że wynik pomiaru każdego kubitu osobno jest losowy, ale **wyniki obu kubitów są doskonale skorelowane**: zawsze są równe.

Sama zgodność wyników w jednej bazie nie dowodzi splątania, ponieważ podobne korelacje mogą powstawać również w klasycznych mieszaninach. Kwantowy charakter tego stanu jest związany z jego nierozkładalnością na stany pojedynczych kubitów i korelacjami dostępnymi w różnych bazach.

Jeśli Alicja i Bob otrzymają po jednym kubicie takiej pary, nie mogą za jej pomocą przesłać użytecznej informacji szybciej od światła: każde z nich otrzymuje lokalnie losowe wyniki.

## Źródła

1. **Materiał podstawowy:** *Elementy kryptografii kwantowej i komputerów kwantowych, Wykład 1 – Wprowadzenie do świata kwantowego*, slajdy 4–22 (podstawowe pojęcia, Young, superpozycja, bazy, pomiar, nieklonowanie i splątanie).
2. **Uzupełnienie spoza prezentacji:** [Stanford Encyclopedia of Philosophy, *The Uncertainty Principle*](https://plato.stanford.edu/entries/qt-uncertainty/) – zwłaszcza §2.5 (nierówność dla rozrzutów położenia i pędu) oraz §6 (odróżnienie nieoznaczoności przygotowania od zaburzenia pomiarowego).
3. **Niezależne źródło akademickie:** [MIT OpenCourseWare, *Quantum Physics I*, Lecture 4: Expectations, Momentum, and Uncertainty](https://ocw.mit.edu/courses/8-04-quantum-physics-i-spring-2013/resources/mit8_04s13_lec04/) – wykładowe omówienie pędu i nieoznaczoności.
