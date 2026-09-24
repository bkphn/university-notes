## Alfabet
**Alfabetem** $\mathcal{A}$ nazywamy niepusty, skończony zbiór. Elementy alfabetu $\mathcal{A}$ nazywamy **literami**, znakami bądź symbolami. Skończony ciąg liter alfabetu A nazywamy **słowem** bądź wektorem nad $\mathcal{A}$ i oznaczamy jako $\vec{a}$. 

**Liczbą liter w słowie** nazywamy długość słowa. Słowo niezawierające żadnej litery jest nazywane **słowem pustym** bądź **spacją** i zwyczajowo oznaczamy je przez $\varepsilon$.

Przez $\mathcal{A}^n$ oznaczamy zbiór wszystkich słów długości $n$ nad alfabetem $\mathcal{A}$. Zbiór zawierający wszystkie możliwe słowa nad alfabetem $\mathcal{A}$ oznaczamy jako $\mathcal{A}^*$ i definiujemy wzorem:
$$\mathcal{A}^* = \bigcup_{n \in \mathbb{N}} \mathcal{A}^n = \mathcal{A}^0 \cup \mathcal{A}^1 \cup \dots$$**Językiem** nazywamy dowolny podzbiór $L \subset \mathcal{A}^*$.
## Systemy niepozycyjne
Systemami niepozycyjnymi nazywamy systemy liczbowe, w których pozycja nie zmienia wartości symbolu.

Przykładem systemu niepozycyjnego może być **system rzymski**:
	$1$ - $\text{I}$
	$5$ - $\text{V}$
	$10$ - $\text{X}$
	$50$ - $\text{L}$
	$100$ - $\text{C}$
	$500$ - $\text{D}$
	$1000$ - $\text{M}$

Zasady systemu rzymskiego:
* Ten sam symbol może występować maksymalnie trzy raz obok siebie.
* Jeżeli mniejsza cyfra występuje po większej, to ich wartości się dodaje.
* Jeżeli mniejsza cyfra występuje przed większą, to jej wartość się odejmuje.
* Cyfra mniejsza niż następna musi występować pojedynczo.
* Ograniczenie: Największą liczbą możliwą do zapisania w tym systemie jest $3999$ ($\text{MMMCMXCIX}$).

*(Uwaga: prowadzący określa również systemy dwunastkowe i sześćdziesiętne jako niepozycyjne, jednak ze względów merytorycznych umieszczono je w sekcji pozycyjnych)*
## Systemy pozycyjne
Każdy układ pozycyjny składa się z podstawy $p$ i alfabetu $\mathcal{A}$.

Podstawa nie musi być liczbą naturalną; istnieją systemy oparte na ujemnych wartościach lub na liczbie $\varphi$. Alfabet $\mathcal{A} = \{a_1, a_2, \dots\}$ to zbiór cyfr określających całkowite liczby $a < p$.
Liczba $b \in \mathbb{N}$ ma postać $b = b_0b_1\dots b_n$, co odpowiada:
$$ b = b_0 \cdot p^n + b_1 \cdot p^{n-1} + \dots + b_n \cdot p^0 $$
gdzie $b_i \in \mathcal{A}$.

Wśród przykładowych systemów pozycyjnych możemy wyróżnić:
* **System dziesiętny** $p=10$, $\mathcal{A}=\{0,1,2,3,4,5,6,7,8,9\}$
	Powszechnie stosowany przez ludzi; litery to cyfry, a słowa to liczby dziesiętne.
	
* **System binarny** $p=2$, $\mathcal{A}=\{0,1\}$
	Używany przez komputery ($1$ oznacza przepływ prądu, $0$ brak); litery to bity, a słowa to ciągi binarne.

* **System heksadecymalny** $p=16$, $\mathcal{A}=\{0,1,2,3,4,5,6,7,8,9,\text{A,B,C,D,E,F}\}$
	Używany np. w adresacji MAC czy reprezentacji kolorów.

* **System sześćdziesiętny** $p=60$, $\mathcal{A}=\{0,1,2,\dots,59\}$
	Używany przy zapisie i operacjach na czasie.

* **System negabinarny** $p=-2$, $\mathcal{A}=\{0,1\}$
	Rzadko używany w eksperymentalnych systemach komputerowych.

* **System o złotej podstawie** $p=\varphi$, $\mathcal{A}=\{0,1\}$ 
	Stosowany w zaawansowanej matematyce.
## Przekształcenia między systemami liczbowymi
Podstawę systemu liczbowego często zapisuje się w indeksie dolnym, np. $2025_{10}, 110_2, \text{F}3_{16}$.

> [!abstract] Zamiana z systemu $10 \rightarrow p$
> 1. **Rozpisanie potęg podstawy** $p^n$ od $n=0$ wzwyż.
> 2. **Metoda zachłanna**: dodawaj potęgi od największej do osiągnięcia wartości liczby:
>    $a_{10} = b_1 \cdot p^n + b_2 \cdot p^{n-1} + \dots + b_n \cdot p^0$
> 3. **Konkatenacja**: wartości $b_i$ ułożone po kolei dają nową liczbę $(b_1b_2\dots b_n)_p$.

**Alternatywny sposób $10 \rightarrow p$ (dzielenie z resztą):**
Liczbę dzielimy kolejno przez podstawę $p$ i zapisujemy reszty z dzielenia. Reszty odczytane od tyłu stanowią liczbę w nowym systemie.

> [!example] Zamiana $53_{10}$ na system trójkowy ($p=3$)
> $53 : 3 = 17 \text{ r } 2$
> $17 : 3 = 5 \text{ r } 2$
> $5 : 3 = 1 \text{ r } 2$
> $1 : 3 = 0 \text{ r } 1$
> Zatem: $53_{10} = 1222_3$

> [!abstract] Zamiana z systemu $p \rightarrow 10$
> 1. **Rozpisanie potęg podstawy** $p^n$ dla poszczególnych pozycji.
> 2. **Mnożenie i sumowanie:** mnożymy każdą cyfrę przez odpowiadającą jej pozycję $p^{n-i}$ i sumujemy:
>    $b_p = b_1 \cdot p^n + b_2 \cdot p^{n-1} + \dots + b_n \cdot p^0 = a_{10}$

> [!example] Zamiana $\text{CCC}_{16}$ na postać dziesiętną
> 1. Potęgi $16^n$: $16^0 = 1, 16^1 = 16, 16^2 = 256$.
> 2. Sumowanie:
>    $\text{CCC}_{16} = \text{C} \cdot 16^2 + \text{C} \cdot 16^1 + \text{C} \cdot 16^0 = 12 \cdot 256 + 12 \cdot 16 + 12 \cdot 1 = 3267_{10}$.

