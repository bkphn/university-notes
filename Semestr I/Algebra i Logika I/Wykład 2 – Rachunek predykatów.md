## Zbiory liczbowe
**Zbiorem liczbowym** nazywamy grupę liczb o pewnych określonych własnościach.

Możemy wyróżnić cztery najważniejsze zbiory liczbowe:
- **Zbiór liczb naturalnych**

$$\mathbb{N}=\{0, 1, 2,3 ,\dots\}$$

- **Zbiór liczb całkowitych**

$$\mathbb{Z}=\{\dots, -2,-1,0,1,2,\dots\}$$

- **Zbiór liczb wymiernych**

$$\mathbb{Q}=\left\{ \frac{p}{q} : p,q\in\mathbb{Z}, q\neq 0 \right\}$$

- **Zbiór liczb rzeczywistych**

$$\mathbb{R}=(-\infty, \infty)$$

## Iloczyn kartezjański
Niech $X,Y$ będą zbiorami. **Iloczynem kartezjańskim** nazywamy zbiór wszystkich par uporządkowanych $(x,y)$, gdzie $x\in X$ i $y\in Y$. Elementy $x,y$ nazywamy kolejno pierwszą i drugą współrzędną pary $(x,y)$. Iloczyn kartezjański zbiorów $X,Y$ oznaczamy jako $X\times Y$ i definiujemy następująco:

$$X\times Y=\{(x,y) : x\in X, y\in Y\}$$

Iloczyn kartezjański $X\times X$ będziemy oznaczać jako $X^2$. Zbiór $\mathbb{R}\times\mathbb{R}=\mathbb{R}^2$ utożsamiamy ze zbiorem wszystkich punktów z płaszczyzny kartezjańskiej.

Iloczyn kartezjański $X_{1}\times X_{2}\times\dots\times X_{n}$ jest zbiorem wszystkich ciągów uporządkowanych $(x_{1},x_{2},\dots,x_{n})$:

$$X_{1}\times \dots\times X_{n}=\{(x_{1},\dots,x_{n}):x_i\in X_{i},i\in\{1,\dots,n\}\}$$

Iloczyn kartezjański $n$ kopii zbioru $X$ oznaczamy jako $X^n=X\times X\times\dots\times X$. Przy czym $X^0=\emptyset$.

## Predykaty
Dowolne wyrażenie $\phi(x)$, gdzie $x\in X$ nazywamy **predykatem** lub **funkcją zdaniową** w zbiorze $X$.

>[!example] Przykłady
> 1. $\phi(x)\iff x>0$ jest funkcją zdaniową w $\mathbb{R}$.
> 2. $\phi(x)\iff \text{miasto }x \text{ jest stolicą Polski}$ jest funkcją zdaniową w zbiorze polskich miast.

Wyrażenie $\phi(x_{1},x_{2},\dots,x_{n})$ jest funkcją zdaniową w zbiorze $X_{1}\times X_{2}\times\dots\times X_{n}$. 

**Wykresem funkcji zdaniowej** $\phi(x_{1},x_{2},\dots,x_{n})$ nazywamy zbiór wszystkich $(a_{1},a_2,\dots,a_{n})\in X_{1},X_{2,}\dots,X_{n}$ dla których zdanie $\phi(x_{1},x_{2},\dots ,x_{n})$ jest prawdziwe. Wykres funkcji zdaniowej $\phi(x_{1},x_{2},\dots,x_{n})$ oznaczamy jako $W_{\phi(x_{1},\dots,x_{n})}$, lub w skrócie $W_{\phi}$ i definiujemy jako:

$$W_{\phi(x_{1},\dots,x_{n})}=\{(a_{1},\dots,a_{n})\in X_{1}\times \dots \times X_{n}:\phi(a_{1},\dots,a_{n})\}$$

Funkcję zdaniową $\phi(x_{1},x_{2},\dots,x_{n})$ nazywamy czasem **własnością** elementów zbioru $X_{1}\times X_{2}\times\dots\times X_{n}$, mówimy wtedy, że $(a_{1},a_{2},\dots,a_{n})$ spełnia własność $\phi$ jeśli zdanie $\phi(a_{1},a_{2},\dots,a_{n})$ jest prawdziwe. W przeciwnym wypadku mówimy, że $(a_{1},a_{2},\dots,a_{n})$ nie spełnia $\phi$.

## Kwantyfikatory
**Kwantyfikatory** określają zakres obowiązywania wyrażenia. W logice wyróżniamy dwa najważniejsze kwantyfikatory:
- **Kwantyfikator ogólny** $\forall$, który oznacza *dla każdego...*. 
- **Kwantyfikator szczegółowy** $\exists$, który oznacza *istnieje...*.

Dodając $!$ do kwantyfikatora szczegółowego otrzymujemy kwantyfikator $\exists!$, co odczytujemy jako *istnieje dokładnie jeden...*. W starszych publikacjach można spotkać się z oznaczeniami $\bigwedge$ zamiast $\forall$ oraz $\bigvee$ zamiast $\exists$.

Jeśli $\phi(x)$ jest funkcją zdaniową w zbiorze $X$, to kwantyfikatory interpretujemy następująco:
- $\forall_{x\in X} \phi(x)$, co oznacza *dla każdego $x\in X$ zachodzi $\phi(x)$*.
- $\exists_{x\in X} \phi(x)$, co oznacza *istnieje $x\in X$ taki, że zachodzi $\phi(x)$*
- $\exists!_{x\in X} \phi(x)$, co oznacza *istnieje dokładnie jeden $x\in X$ taki, że zachodzi $\phi(x)$*.

Kwantyfikatory w połączeniu z predykatem są zdaniami logicznymi.

## Łączenie kwantyfikatorów
Kwantyfikatory możemy ze sobą łączyć tworząc bardziej rozbudowane zdania logiczne:
- $\forall_{x\in X}\forall_{y\in Y} \phi(x)$, co oznacza *dla każdego $x\in X$ i dla każdego $y\in Y$ zachodzi $\phi(x)$*,
- $\forall_{x\in X}\exists_{y\in Y} \phi(x)$ co oznacza *dla każdego $x\in X$ istnieje $y\in Y$ taki, że zachodzi $\phi(x)$*.
- $\exists_{x\in X}\forall_{y\in Y}\phi(x)$ co oznacza *istnieje $x\in X$ taki, że dla każdego $y\in Y$ zachodzi $\phi(x)$*.

Wyrażenia $\exists_{x}\forall_{y}$ oraz $\forall_{y}\exists_{x}$ nie są równoważne, tych kwantyfikatorów nie można zamieniać miejscami. Natomiast wyrażenia $\forall_{x}\forall_{y}$ oraz $\forall_{y}\forall_{x}$ są równoważne, co w skrócie zapisujemy jako $\forall_{x,y}$. Podobna sytuacja dotyczy wyrażeń $\exists_{x}\exists_{y}$ oraz $\exists_{y}\exists_{x}$ co zapisujemy jako $\exists_{x,y}$.

Zdanie $\forall_{x\in X} \phi(x)$ jest prawdziwe wtedy i tylko wtedy, gdy $W_{\phi}=X$. Zdanie $\exists_{x\in X} \phi(x)$ jest fałyszwe wtedy i tylko wtedy, gdy $W_{\phi}\neq \emptyset$.

## Prawa kwantyfikatorów
Wykorzystując kwantyfikatory możemy uzasadniać **prawa kwantyfikatorów**, będące tautologiami rachunku zdań.

Jednym z prawem kwantyfikatorów są **reguły zaprzeczeń**, będące odpowiednikami praw de Morgana:
- **Pierwsza reguła zaprzeczeń**

$$\neg\forall_{x\in X}\phi(x)\iff\exists_{x\in X}\neg\phi(x)$$

- **Druga reguła zaprzeczeń**

$$\neg\exists_{x\in X} \phi(x) \iff \forall_{x\in X} \neg\phi(x)$$

Funkcje zdaniowe możemy łączyć spójnikami logicznymi tworząc złożone funkcje zdaniowe. Używając ich możemy tworzyć inne prawa kwantyfikatorów, np.:

$$\forall_{x\in X} \phi(x)\land\psi(x)\iff\forall_{x\in X}\phi(x)\land \forall_{x\in X} \psi(x)$$
