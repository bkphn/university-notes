## Statystyka
Sieciami probabilistycznymi nazywamy sieci neuronowe oparte na klasycznej teorii statystyki. Teoria statystyki jest przydatna w sieciach probabilistycznych, ponieważ klasyfikowane wektory cech są obarczone zakłóceniami powstałymi w wyniku przetwarzaniu wstępnego.

Najczęściej zakłócenia są złożeniami niezależnych zakłóceń elementarnych, zatem wynikowe zakłócenia charakteryzują się rozkładem normalnym $\mathcal{N}(m,\sigma^2 )$. Z powodu tych zakłóceń, w przestrzeni decyzyjnej regiony należące do poszczególnych klas nachodzą na siebie, całkowicie bezbłędna klasyfikacja jest ideałem niemożliwym do spełnienia w praktyce.

## Architektura sieci PNN
Sieć PNN (ang. *Probabilistic Neural Network*) jest klasyfikatorem. Budowa PNN pozwala rozwiązać problemy multi-klasyfikacji. Wektor wejściowy jest porównywany do każdego elementu z rozważanych klas abstrakcji. Każda z podsieci odzwierciedla estymację w tzw. oknie Parzena dla odpowiedniej z klasy.

Sieć PNN jest dedykowana problemom multiklasyfikacji i w klasycznym ujęciu składa się z czterech warstw:
- **Warstwa wejściowa**: Neurony w tej warstwie bezpośrednio pobierają elementy badanego wektora cech. Są to węzły dystrybucyjne, które przekazują pełny wektor wejściowy do kolejnej warstwy.
- **Warstwa wzorców**: Każdy węzeł reprezentuje jeden fizyczny element uczący z danej klasy abstrakcji. Obliczają one nieliniowe wartości przy użyciu funkcji Gaussa. Odzwierciedla to estymację gęstości prawdopodobieństwa w oknie Parzena dla konkretnej klasy.
- **Warstwa sumacyjna**: Znajdują się tu neurony, które przypisane są do konkretnych klas abstrakcji i sumują sygnały ze wszystkich należących do nich wzorców.
- **Warstwa wyjściowa**: Pełni rolę decyzyjną, wybierając przynależność wektora wejściowego do jednej z klas abstrakcji na podstawie najwyższego zsumowanego prawdopodobieństwa.

Diagram sieci PNN:
![[Pasted image 20260918181716.png|402]]

## Aproksymacja sieci PNN
Porównanie wektora do klasy abstrakcji na neuronach opisuje się najczęściej funkcją Gaussa. Dla jednego wymiaru wygląda ona następująco:

$$g_{n}(x)=\frac{1}{\sigma\sqrt{2\pi}}\cdot e^{-\frac{(x-c)^2}{2\sigma^2}}$$

W praktyce porównujemy wielowymiarowy wektor wejściowy $\mathbf{x}$ z każdym zapisanym elementem $\mathbf{x}_n$ dla klasy abstrakcji $C_p$ za pomocą odległości:

$$g_{n}^p(\mathbf{x})= \frac{1}{\sigma\sqrt{2\pi}}\cdot e^{-\frac{{\parallel \mathbf{x}-\mathbf{x}_{n}\parallel}^2}{2\sigma^2}}$$

Ostateczna wartość funkcji sumy na warstwie sumacyjnej dla badanej klasy abstrakcji $C_p$  wynosi:

$$G^p(\mathbf{x})=\frac{1}{N\sigma\sqrt{2\pi}}\cdot\sum_{n=1}^N e^{-\frac{{\parallel \mathbf{x}-\mathbf{x}_{n} \parallel}^2}{2\sigma^2}}$$

## Uczenie sieci PNN
Uczenie sieci PNN odbywa się na zasadzie odwzorowania całego zbioru uczącego w sieci:
1. jeśli pojawia się nowy element w zbiorze uczącym:
	- przyporządkowujemy go do danej klasy abstrakcji,
	- powiększamy odpowiedni klaster PNN o kolejny neuron odpowiadający temu elementowi.
2. Jeśli pojawia się więcej nowych elementów to reorganizujemy klastry PNN albo tworzymy nowe.
3. Jeśli usuwamy jakiś element uczący to usuwamy odpowiadający mu neuron z danego klastra.

## Plusy i minusy sieci PNN
**Zalety sieci PNN:**
- Ekstremalnie szybki proces uczenia (wymaga zaledwie jednego przejścia przez dane).
- Zbieżność do optymalnego klasyfikatora probabilistycznego – rośnie ona proporcjonalnie do ilości wprowadzonych elementów uczących.
- Bardzo prosta modyfikacja bazy wiedzy (łatwe dodawanie/usuwanie nowych elementów uczących bez resetowania algorytmu).

**Wady sieci PNN:**
- Ogromne wymagania pamięciowe, ponieważ optymalne działanie wymaga przechowania wszystkich danych uczących wewnątrz pamięci sieci.
- Bardzo wolne działanie podczas fazy wdrożeniowej (klasyfikacji) w stosunku do standardowych sieci MLP (*Multi-Layer Perceptron*).
- Ryzyko słabszej generalizacji niż w sieciach wielowarstwowych w przypadku błędnego oszacowania stałej wygładzania $\sigma$.
- Bardzo wysokie wymagania co do jakości i pełnej reprezentatywności danych uczących.

