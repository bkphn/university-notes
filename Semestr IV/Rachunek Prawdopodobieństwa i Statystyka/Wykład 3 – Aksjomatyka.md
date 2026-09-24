## Paradoks zbiorów nieprzeliczalnych
Jeżeli $\Omega$ jest zbiorem skończonym bądź przeliczalnym, czyli $|\Omega|≤\aleph_0$ to prawdziwe pozostają standardowe definicje:
- $p(\omega_i )\geq0$
- $\sum_{i=1}^\infty p(\omega_{i})=1$
- $P(A)=\sum_{\omega_{i}\in A}p(\omega_{i})$

W przypadku gdy zbiór $\Omega$ jest zbiorem nieprzeliczalnym, czyli $|\Omega|>\aleph_0$, to równania te nie zawsze są już spełnione. W zbiorze nieprzeliczalnym dowolne zdarzenie elementarne $\omega_i$ jest nieskończenie małe w stosunku do nieprzeliczalności zbioru $\Omega$. 

W związku z tym: $P(\{\omega_i \})=0=p(\omega_i)$, jako że prawdopodobieństwo zdarzenia $A$ definiowaliśmy dotychczas jako sumę prawdopodobieństw zdarzeń elementarnych to dochodzi do paradoksu, gdzie dla dowolnego $A$: $$P(A)=\sum_{\omega_{i}\in A}p(\omega_{i})=0$$
## $\sigma$-algebry
Aby zapobiec paradoksowi zbiorów nieprzeliczalnych musimy tak przedefiniować zdarzenia by dotychczasowe prawa się nie załamywały.

Klasę zbiorów $A_i\subseteq \Omega$ nazywamy **$\sigma$-algebrą**, bądź $\sigma$-ciałem i oznaczamy jako $\mathcal{U}$ jeśli spełnione są warunki: 
- $\emptyset\in\mathcal{U}$
- $\Omega\in \mathcal{U}$
- $A\in \mathcal{U}\implies \overline{A}\in \mathcal{U}$
- $A_1, A_2,\dots\in \mathcal{U}\implies \bigcup_{i=1}^\infty A_{i} ∈ \mathcal{U}$

Najmniejszą możliwą $\sigma$-algebrą jest zbiór $\mathcal{U}=\{\emptyset, \Omega\}$, natomiast największą $\mathcal{U}=\{A :A\subset \Omega\}$.
## Aksjomaty rachunku prawdopodobieństwa
Po tym jak zdefiniowaliśmy pojęcie $\sigma$-algebry możemy się zająć próbą aksjomatycznego uogólnienia znanych nam wzorów, tak by nie przestawały działać w sytuacji gdy $|\Omega|>\aleph_0$.

Prawdopodobieństwem będziemy nazywać funkcję $P$ określoną na $\sigma$-algebrze $\mathcal{U}$. Zdarzeniem będziemy nazywać dowolny element $A$ należący do klasy $\mathcal{U}$. Funkcja prawdopodobieństwa $P$ musi spełniać trzy warunki:
- **Aksjomat P1**: Prawdopodobieństwo dowolnego zdarzenia musi być liczbą nieujemną. $$P(A)≥0, \quad \forall_{A\in \mathcal{U}}$$
- **Aksjomat P2**: Prawdopodobieństwo zdarzenia pewnego musi wynosić $1$. $$P(\Omega)=1$$
- **Aksjomat P3**: Prawdopodobieństwo sumy przeliczalnego ciągu zdarzeń, które wzajemnie się wykluczają jest równe sumie ich prawdopodobieństw. $$P\left(\bigcup_{i=1}^\infty A_{i}\right)=\sum_{i=1}^\infty P(A_{i}), \qquad i\neq j\implies A_{i}\cap A_{j}\neq\emptyset$$
## Twierdzenia rachunku prawdopodobieństwa
Na podstawie trzech aksjomatów możemy udowodnić następujące twierdzenia:
>[!danger] Twierdzenie o prawdopodobieństwie zdarzenia niemożliwego
>$$P(\emptyset)=0$$

>[!danger] Twierdzenie o prawdopodobieństwie zdarzenia przeciwnego
> $$P(\overline{A})=1−P(A)$$

>[!danger] Twierdzenie o prawdopodobieństwie różnicy zdarzeń
> $$A\subset B \implies P(B\setminus A)=P(B)-P(A)$$

>[!danger] Twierdzenie o prawdopodobieństwie sumy zdarzeń
> $$P(A\cup B)=P(A)+P(B)-P(A\cap B)$$

>[!example] Udowonij, że $P(\emptyset)=0$
> $$1\overset{\text{P2}}{=}P(\Omega)= P(\Omega\cup\emptyset)\overset{\text{P3}}{=}P(\Omega)+P(\emptyset)=1+P(\emptyset)\implies P(\emptyset)=0$$

## Prawdopodobieństwo geometryczne
Dane są punkty $a,b$ leżące na osi geometrycznej, takie że $b>a$. Przez $\lambda([a,b])$ będziemy oznaczać długość odcinka $[a,b]$. Standardowo definiujemy ją jako: $$\lambda([a,b])=b−a$$
Niech $A\subset[a,b]$, aby wyznaczyć długość zdarzenia $\lambda(A)$ poszczególne podzbiory $A_i\subset A$ nie mogą na siebie nachodzić, matematycznie rzecz ujmując, dla każdego $A_i\cap A_j\neq \emptyset$ musi zachodzić: $$\lambda\left(\bigcup_{i=1}^\infty A_{i}\right)=\sum_{i=1}^\infty \lambda(A_{i})$$
Niech $A$ będzie zdarzeniem jednowymiarowym $A\subset[a,b]$, prawdopodobieństwo zdarzenia $A$ możemy obliczyć korzystając z funkcji $\lambda$ nazywanej **miarą Lebesgue'a**: $$P(A)=\frac{\lambda(A)}{\lambda([a,b])}$$
Niech $A\subset\Omega$ będzie zdarzeniem dwuwymiarowym. Przez $S(A)$ oznaczać będziemy pole powierzchni takiego zdarzenia, przy czym istotne jest by $P(\Omega)<\infty$. W przestrzeni dwuwymiarowej pole $S$ jest miarą Lebesgue'a zdarzeń, często zamiast $S(A)$ stosuje się zapis $\lambda_2 (A)$. Prawdopodobieństwo dwuwymiarowego zdarzenia $A$ obliczamy ze wzoru: $$P(A)=\frac{S(A)}{S(\Omega)}$$
## Zagadnienie Buffona dla Igły
Na płaszczyźnie dane są dwie proste umieszczone od siebie w odległości $2a$. Na płaszczyznę rzucamy igłę (oznaczoną kolorem czerwonym) o długości $2l$, gdzie $l<a$.

Niech zdarzenie $A$ oznacza fakt, że igła wyląduje na którejś z prostych. Przez $x$ oznaczmy odległość od środka igły $O$ do najbliższej prostej. Przez $\varphi$ oznaczmy kąt między igłą a prostą, a przez $C$ wierzchołek łączący koniec igły z jej środkiem.![[Pasted image 20260920172014.png|392]]
Widzimy, że $0\leq x\leq a$ oraz, że $0\leq \varphi \leq \pi$. Na podstawie tych faktów zdefiniujmy przestrzeń $\Omega$ w kartezjańskim układzie współrzędnych:![[Pasted image 20260920172045.png|218]]
Długość odcinka $|OC|$ możemy zdefiniować jako $|OC|=l\cdot\sin⁡\varphi$. Wiemy, że zdarzenie $A$ zajdzie tylko wtedy gdy $x<|OC|$, co możemy zapisać jako: $A=\{x<l\cdot\sin⁡ \varphi \}$. Spróbujmy w kartezjańskim układzie współrzędnym wyznaczyć zdarzenie $A$:![[Pasted image 20260920172142.png|230]]
Aby obliczyć prawdopodobieństwo zdarzenia $A$ musimy obliczyć pole powierzchni $S(\Omega)=a\cdot\pi$ oraz pole powierzchni pod krzywą opisaną za pomocą równania $x(\varphi)=l\cdot\sin⁡\varphi$, wykorzystamy do tego całkę oznaczoną: $$P(A)=\frac{S(A)}{S(\Omega)} =\frac{l\cdot\int_{0}^\pi \sin(\varphi) d\varphi}{a\pi}=\frac{-l[\cos(\varphi)]^\pi_{0}}{a\pi}=\frac{2l}{a\pi}$$
Równanie to po przekształceniu daje nam bardzo oryginalny wzór na przybliżenie liczby $\pi$: $$\pi\approx \frac{2l}{a\cdot P(A)}$$
## Trójkąt zdegenerowany
Trójkąt o bokach długości $x,y,z$, taki że: $x+y=z$ nazywamy **trójkątem zdegenerowanym**. Trójkąt zdegenerowany $\triangle$, o kątach $\alpha, \beta, \gamma$ spełnia własności:
- $P_\triangle=0$
- $\alpha=\beta=0\degree$
- $\gamma=180\degree$
