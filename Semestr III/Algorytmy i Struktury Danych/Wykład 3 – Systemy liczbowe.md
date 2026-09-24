## Systemy liczbowe
System liczbowy to zbiór zasad określający sposób zapisywania i nazywania liczb.

System pozycyjny to metoda zapisywania liczb, w taki sposób, że w zależności od pozycji danej cyfry w ciągu oznacza ona wielokrotność potęgi pewnej liczby uznawanej za bazę danego systemu. System pozycyjny umożliwia też zapisywanie ułamków, przy czym liczby wymierne składają się albo z skończonej liczby znaków, albo są od pewnego miejsca okresowe. Informacja w jakim systemie liczbowym zapisana jest dana liczba najczęściej oznaczana jest poprzez indeks dolny.
## System rzymski
System rzymski zapisywania liczb wykorzystuje cyfry pochodzenia etruskiego, które Rzymianie przejęli i zmodyfikowali ok. 500 p.n.e. Nadaje się on, co prawda, do wygodnego zapisywania liczb, jest jednak niewygodny w prowadzeniu nawet prostych działań arytmetycznych oraz nie pozwala na zapis ułamków.

Do dziś system rzymski jest zwyczajowo używany do zapisywania liczb w pewnych szczególnych przypadkach. Na przykład w Polsce zapisuje się cyframi rzymskimi: numery liceów (ale nie szkół podstawowych), klas i lat studiów, tomów, pięter, wydziałów w instytucjach. Zwyczajowo stosuje się czasem liczby rzymskie do lat powstania budowli (na ich frontonach) oraz numeruje rozmaite grupy klasyfikacyjne (szczególnie na ich wyższych poziomach). Cyfry rzymskie stosuje się wobec wydarzeń powtarzanych rokrocznie, gdy są one częścią nazwy na jej początku.

Cyfry rzymskie powszechnie stosuje się również w numeracji stuleci (np. XIX wiek – nie dotyczy to tradycji anglosaskiej, gdzie powszechnie stosuje się cyfry arabskie), w imionach władców i papieży (np. Jan Paweł II), nazwach wydarzeń historycznych (II wojna światowa).

Podstawowe symbole systemu rzymskiego: 
	$1$ - $\text{I}$
	$5$ - $\text{V}$
	$10$ - $\text{X}$
	$50$ - $\text{L}$
	$100$ - $\text{C}$
	$500$ - $\text{D}$
	$1000$ - $\text{M}$

System niepozycyjny, o następujących zasadach:
- Ten sam symbol może występować maksymalnie trzy raz obok siebie,
- jeżeli mniejsza cyfra występuje po większej to ich wartości się dodaje,
- jeżeli mniejsza cyfra występuje przed większą, to jej wartość się odejmuje,
- cyfra mniejsza niż następna musi występować pojedynczo.

System ten ma duże ograniczenia – największą liczbą, jaką możemy przy jego pomocy zapisać, jest $3999 = \text{MMMCMXCIX}$.
## System dziesiętny
Dziesiętny system liczbowy jest podstawowym systemem stosowanym niemal we wszystkich krajach. Pochodzi on z Indii, skąd do Europy przynieśli go Arabowie. Od XVI wieku stosowany równolegle obok systemu rzymskiego. Początkowo w oficjalnych dokumentach nadal zamieniano liczby na system rzymski, jednak dość szybko system arabski całkowicie wyparł system Rzymski.

Liczby w systemie dziesiętnym przybierają postać:  $$ b = b_n \cdot 10^n + \dots + b_1 \cdot 10^1 + b_0 \cdot 10^0 $$gdzie cyfry spełniają warunek $b_i \in \{0, 1, 2, 3, 4, 5, 6, 7, 8, 9\}$.
## System dwójkowy
Dwójkowy system liczbowy lub też system binarny to pozycyjny system liczbowy, w którym podstawą jest liczba $2$, a do zapisu liczb używa się cyfr $0$ oraz $1$. System dwójkowy używany był już w XVI wieku przez Johna Napiera, chociaż używał on symboli $\text{a}$ oraz $\text{b}$ zamiast $0$ oraz $1$.

System ten jest powszechnie używany w informatyce i elektronice cyfrowej, gdzie minimalizacja stanów do dwóch pozwala na prostą implementację sprzętową, odpowiadającą stanom włączony i wyłączony.

Liczby w systemie dwójkowym mają postać:$$ b = b_n \cdot 2^n + \dots + b_1 \cdot 2^1 + b_0 \cdot 2^0 $$gdzie $b_i \in \{0, 1\}$.
## System ósemkowy
Ósemkowy system liczbowy to system o podstawie $8$. System ten nazywany jest również systemem oktalnym. Możemy go spotkać podczas przepisywania uprawnień w dystrybucjach Linux oraz w językach programowania C, C++, Java, Perl, PHP.

Liczby w systemie ósemkowym mają postać:
$$ b = b_n \cdot 8^n + \dots + b_1 \cdot 8^1 + b_0 \cdot 8^0 $$
gdzie $b_i \in \{0, 1, 2, 3, 4, 5, 6, 7\}$.
## System szesnastkowy
Szesnastkowy system liczbowy jest nazywany również systemem heksadecymalnym. Podstawą systemy jest liczba $16$. Najczęściej oprócz cyfr arabskich używa się sześciu pierwszych liter alfabetu łacińskiego.

Wiele parametrów układów elektronicznych (np. kategorie urządzeń PCI), adresy sprzętowe MAC czy reprezentację kodów kolorów podaje się w systemie szesnastkowym.

Liczby w systemie szesnastkowym mają postać:
$$ b = b_n \cdot 16^n + \dots + b_1 \cdot 16^1 + b_0 \cdot 16^0 $$
gdzie $b_i \in \{0, 1, 2, 3, 4, 5, 6, 7, 8, 9, \text{A}, \text{B}, \text{C}, \text{D}, \text{E}, \text{F}\}$.
## Przekształcanie systemów liczbowych
Podstawę systemu liczbowego często zapisuje się w indeksie dolnym danej liczby, np. $2025_{(10)}$, $110_{(2)}$, $\text{F}3_{(16)}$.

Kluczową umiejętnością jest zamiana liczb między różnymi systemami liczbowymi.

> [!abstract] Schemat zamiany systemów liczbowych $10\rightarrow p$
>1. Podzielenie z resztą liczby przez podstawę: $a : p = a_1 + b_1 \rightarrow b_1$.
>2. Bierzemy całkowitą część i powtarzamy algorytm: $a_1 : p = a_2 + b_2 \rightarrow b_2$.
>3. Powtarzamy do momentu, gdy $a_n = 0$: $a_{n-1} : p = 0 + b_n \rightarrow b_n$.
>4. Konkatenacja wartości $b_i$ stanowi liczbę w nowej podstawie: $b = b_n b_{n-1} \dots b_2 b_1$.


>[!abstract] Schemat zamiany systemów liczbowych $p \rightarrow 10$
>1. Rozpisanie potęg podstawy ($p^0, p^1, p^2, \dots, p^n$).
> 2. Dla dowolnej liczby $b = b_1 b_2 \dots b_n$ mnożymy każdą cyfrę przez odpowiadającą jej pozycję; suma wszystkich iloczynów stanowi liczbę w systemie dziesiętnym:
>   $$ b_p = b_1 \cdot p^n + b_2 \cdot p^{n-1} + \dots + b_n \cdot p^0 = a_{10} $$


>[!abstract] Schemat zamiany systemów liczbowych $p \rightarrow p^x$
>1. Grupujemy cyfry liczby w $x$-elementowe grupy: $a_1 \dots a_x \mid a_{x+1} \dots a_{2x} \mid \dots$.
>2. Każda z grup odpowiada jednej cyfrze w podstawie $p^x$, przekształcamy je w pamięci.
>3. Konkatenacja liczb $b_i$ stanowi liczbę w podstawie $p^x$: $b = b_1 b_2 \dots$.

>[!example] Przykładowe przekształcenie
>Przedstaw liczbę $1001011_{(2)}$ w postaci ósemkowej:
  >1. $001 \, 001 \, 011$
  >2. $001_{(2)} \mid 001_{(2)} \mid 011_{(2)} \rightarrow 1_{(8)} \, 1_{(8)} \, 3_{(8)}$
  >3. Wynik: $1001011_{(2)} = 113_{(8)}$
