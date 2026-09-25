## Zbiór miękki
Większość z tradycyjnych narzędzi służących do formalnego modelowania, wnioskowania i przetwarzania danych ma precyzyjny charakter. Jednak wiele skomplikowanych problemów zawiera dane, które nie zawsze są jasne i oczywiste. Niedoskonałość parametryzacji często uniemożliwia wnioskowanie. 

Dmitri Molodstov wprowadził pojęcie zbioru miękkiego, jako modelu matematycznego służącego do wnioskowania w warunkach niepewności. Teoria zbiorów miękkich jest bardzo podobna do teorii zbiorów rozmytych, jednakże w pewien sposób znacznie uproszczona.

W zbiorach miękkich początkowy opis obiektu ma jedynie charakter przybliżony. 

## Definicja zbioru miękkiego
Niech $U$ będzie klasą wszystkich rozpatrywanych elementów. Przez $E$ oznaczamy zbiór parametrów, a interesujące nas parametry, które akurat poddajemy analizie oznaczamy jako $A\subseteq E$

Para $(F,A)$ jest nazywana **zbiorem miękkim**, gdzie $F$ jest funkcją przyporządkowującą:

$$F:A\rightarrow \mathcal{P}(U)$$

przez $\mathcal{P}(U)$ rozumiemy zbiór potęgowy klasy $U$.

Klasę $U$ będziemy nazywać **uniwersum**. W klasycznym rozumieniu zbiór miękki nie jest zbiorem.

Niech $U$ będzie klasą domów $h_{i}$, $U=\{h_1,h_2,h_3,h_4,h_5,h_6\}$. Niech $E$ będzie zbiorem wszystkich cech określających atrakcyjność domu. Wybieramy $A\subseteq E$ załóżmy, że interesują nas cztery parametry $A=\{\varepsilon_1,\varepsilon_2,\varepsilon_3,\varepsilon_4 \}$, przykładowo:
- $\varepsilon_1$= $\mathtt{drogi}$
- $\varepsilon_2$= $\mathtt{piękny}$
- $\varepsilon_3$ = $\mathtt{drewniany}$
- $\varepsilon_4$ = $\mathtt{nowoczesny}$

Załóżmy, że funkcja $F$ przyporządkowuje parametry do konkretnych domów:
- $F(\varepsilon_1 )=\{h_2,h_6 \}$
- $F(\varepsilon_2 )=\{h_1,h_4 \}$
- $F(\varepsilon_3 )=\{h_1,h_5,h_6 \}$
- $F(\varepsilon_4 )=\{h_3\}$

Zbiór miękki $(F,A)$ formalnie zapisujemy jako zbiór par uporządkowanych:

$$(F,A)=\{(\varepsilon_1,\{h_2,h_6 \}), (\varepsilon_2,\{h_1,h_4 \}),(\varepsilon_3,\{h_1,h_5,h_6 \}),(\varepsilon_4,\{h_3 \})\}$$

## Podzbiory miękkie
Zbiór miękki $(F,A)$ jest podzbiorem $(G,B)$, jeżeli $A\subseteq B$ oraz $\forall_{\varepsilon\in A}  F(\varepsilon)=G(\varepsilon)$, zależność tą oznaczamy jako:

$$(F,A) \widetilde{\subseteq} (G,B)$$

Dwa zbiory miękkie są równe, jeżeli $(F,A) \widetilde{\subseteq} (G,B)$ oraz $(G,B) \widetilde{\subseteq}(F,A)$ co klasycznie oznaczamy jako $(F,A)=(G,B)$.

## Rodzaje zbiorów miękkich
Niech $A\subseteq E$ będzie zbiorem wybranych parametrów $A=\{\varepsilon_1,\cdots,\varepsilon_n \}$ przez zbiór $\neg A$ rozumiemy zaprzeczenie zbioru $A$ i definiujemy go jako $\neg A=\{\neg\varepsilon_1,\cdots,\neg\varepsilon_n \}$. Przykładowo jeżeli $\varepsilon$ oznacza $\mathtt{ładny}$ to $\neg \varepsilon= \mathtt{nie\text{-}ładny}$. Zaprzeczenie zbioru $A$ spełnia własności:
- $\neg (\neg A)=A$
- $\neg (A\cup B)=\neg A\cup \neg B$
- $\neg (A\cap B)=\neg A\cap \neg B$

Dopełnienie zbioru miękkiego $(F,A)$ oznaczamy jako $(F,A)^c$ i definiujemy jako:

$$(F,A)^c=(F^c, \neg A)$$

gdzie $F^c:\neg A\rightarrow \mathcal{P}(U)$ jest funkcją zdefiniowaną wzorem:

$$F^c(\alpha)=U\setminus F(\neg\alpha)$$

Obecnie jednak powszechniej stosuje się uwspółcześnioną redefinicję uzupełnienia:

$$(F,A)^c=(F^c,A)$$

gdzie $F^c:A\rightarrow \mathcal{P}(U)$:

$$F^c (\alpha)=U\setminus F(\alpha)$$

Zbiór miękki $(F,A)$ nazywamy **zbiorem pustym**, jeżeli spełniony jest warunek:

$$\forall_{\varepsilon\in A}   :F(\varepsilon)=\emptyset$$

Miękki zbiór pusty oznaczamy zwyczajowo symbolem $\Phi$, inną rzadziej spotykaną notacją jest $\widetilde{\emptyset}$.

Zbiór miękki $(F,A)$ nazywamy **całkowitym zbiorem miękkim**, jeżeli spełniony jest warunek:

$$\forall_{\varepsilon\in A}   :F(\varepsilon)=U$$

Całkowity zbiór miękki oznaczamy jako $\widetilde{A}$.

## Operacje na zbiorach miękkich
**Sumę zbiorów miękkich** $(F,A), (G,B)$ oznaczamy jako $(F,A) \widetilde{\cup} (G,B)$ i definiujemy jako:

$$(F,A)\widetilde{\cup}(G,B)=(H,A\cup B)$$

gdzie funkcja $H$ dana jest wzorem:

$$H=\begin{cases}
F(\varepsilon), \qquad \varepsilon\in A\setminus B \\
G(\varepsilon), \qquad \varepsilon\in B\setminus A \\
F(\varepsilon)\cup G(\varepsilon), \quad \varepsilon\in A\cap B
\end{cases}$$

**Przekrój zbiorów miękkich** (nazywany również częścią wspólną bądź iloczynem) oznaczamy jako $(F,A) \widetilde{\cap} (G,B)$ i definiujemy jako:

$$(F,A) \widetilde{\cap} (G,B)=(H, A\cap B)$$

gdzie $H(\varepsilon)=F(\varepsilon)\cap G(\varepsilon)$ (w starszych definicjach przyjmowano, że spełniony musi być warunek $F(\varepsilon)=G(\varepsilon)$)

Podstawowe operacje na zbiorach miękkich spełniają własności:
- $(F,A) \widetilde{\cup} (F,A)=(F,A)$
- $(F,A) \widetilde{\cap} (F,A)=(F,A)$
- $(F,A) \widetilde{\cup} \Phi=(F,A)$
- $(F,A) \widetilde{\cap} \Phi=\Phi$
- $(F,A) \widetilde{\cup} \widetilde{A}  =\widetilde{A}$
- $(F,A) \widetilde{\cap} \widetilde{A}  =(F,A)$
- $((F,A) \widetilde{\cup} (G,B))^c=(F,A)^c \widetilde{\cap} (G,B)^c$
- $((F,A) \widetilde{\cap} (G,B))^c=(F,A)^c \widetilde{\cup} (G,B)^c$

## Operacje logiczne
W przypadku zbiorów miękkich operatory logiczne $\lor$, $\land$ działają inaczej od operatorów teoriomnogościowych $\widetilde{\cup}$, $\widetilde{\cap}$. Kluczową różnicą jest to, że zamiast na pojedynczych zbiorach, operatory logiczne działają na uporządkowanych parach $(\alpha,\beta)\in A\times B$.

**Operację AND** zbiorów miękkich $(F,A)$ i $(G,B)$ definiujemy jako:

$$(F,A)\land(G,B)=(H, A\times B)$$

gdzie funkcja $H$ dana jest wzorem:

$$H(\alpha,\beta)=F(\alpha)\cap G(\beta), \qquad \forall_{(\alpha,\beta)\in A \times B}$$

**Operację OR** zbiorów miękkich $(F,A)$ i $(G,B)$ definiujemy jako:

$$(F,A)\lor (G,B)=(O, A\cap B)$$

gdzie funkcja $O$ dana jest wzorem:

$$O(\alpha,\beta)=F(\alpha)\cup G(\beta),\qquad  \forall_{(\alpha,\beta)\in A\times B}$$

Korzystając z operatorów logicznych, możemy zdefiniować prawa de Morgana:
- **Pierwsze prawo de Morgana**

$$((F,A)\lor(G,B))^c=(F,A)^c\land (G,B)^c$$

- **Drugie prawo de Morgana**

$$(F,A)\land(G,B))^c=(F,A)^c\lor(G,B)^c$$

## Tabela binarna
Zbiór miękki możemy reprezentować za pomocą tabeli binarnej, której komórki przybierają wartości $0,1$ w zależności od tego czy dany element $h\in U$ spełnia atrybut $h\in F(\varepsilon)$.

Przykładowo na podstawie zbioru miękkiego 
$(F,A)= \{ (\varepsilon_1,\{h_2,h_6 \}), (\varepsilon_2,\{h_1,h_4 \}),(\varepsilon_3,\{h_1,h_5,h_6 \}),(\varepsilon_4,\{h_3 \})\}$ możemy stworzyć tabelę:

| $U$       | $\varepsilon_1$ | $\varepsilon_2$ | $\varepsilon_3$ | $\varepsilon_4$ |
| --------- | --------------- | --------------- | --------------- | --------------- |
| **$h_1$** | $0$             | 1               | 1               | 0               |
| **$h_2$** | 1               | 0               | 0               | 0               |
| **$h_3$** | 0               | 0               | 0               | 1               |
| **$h_4$** | 0               | 1               | 0               | 0               |
| **$h_5$** | 0               | 0               | 1               | 0               |
| **$h_6$** | 1               | 0               | 1               | 0               |

## Tabele zredukowane
Często zwykłe tabele binarne są mocno nadmiarowe, zawierają one wiele zbędnych danych, które nie niosą żadnej nowej informacji. W tym celu często redukujemy tabele do postaci zredukowanej.

Reduktem nazywamy najmniejszy możliwy podzbiór $Q\subseteq E$, który grupuje elementy w sposób identyczny do wyjściowych parametrów $e_i\in E$. Fakt ten oznaczamy jako $\mathrm{IND}(Q)=\mathrm{IND}(E)$.

Jeżeli $Q$ jest reduktem $E$ to miękki zbiór $(F,Q)$ nazywamy zredukowanym miękkim zbiorem w miękkim zbiorze $(F,E)$.

Przez $c_i$ oznaczamy wartość wyboru obiektu $h_i\in U$, gdzie:

$$c_{i}=\sum_{j=1}^{|Q|}h_{ij}$$

Przykładowo dane jest uniwersum $U=\{h_1,h_2,h_3 \}$ oraz zbiór parametrów $E=\{e_1,e_2,e_3,e_4,e_5 \}$. Dane są dwa redukty $Q_1=\{e_1,e_2,e_4,e_5 \}$ oraz $Q_2=\{e_2,e_3,e_4,e_5 \}$, spośród nich wybieramy dowolny, przyjmijmy $Q=Q_1$.

Na podstawie reduktu $Q=Q_1$ tworzymy zredukowaną tabelę o jedynie czterech kolumach, następnie do każdego z wierszy obliczamy $c_i$:

| $U$ | $e_1$ | $e_2$ | $e_4$ | $e_5$ | $c_i$ |
|---|---|---|---|---|---|
| **$h_1$** | 0 | 1 | 1 | 0 | $0 + 1 + 1 + 0 = 2$ |
| **$h_2$** | 1 | 0 | 0 | 0 | $1 + 0 + 0 + 0 = 1$ |
| **$h_3$** | 0 | 0 | 0 | 1 | $0 + 0 + 0 + 1 = 1$ |

Korzystając z tabeli zredukowanej możemy powiedzieć, że najlepszy jest obiekt $h_1$ ponieważ jego wartość $c_1$ jest najwyższą spośród wszystkich $c_i$.

## Tabele ważone
Każdemu parametrowi $e_j\in Q$ przypisujemy wagę $w_j\in (0, 1]$. Ta waga określa, jak istotny jest dla nas parametr $e_j$. Przez $d_{ij}$ oznaczmy ważone dane wejściowe dla konkretnego $h_{ij}$. Dane te obliczamy ze wzoru:

$$d_{ij}=w_j\cdot h_{ij}$$

W przypadku danych ważonych wzór na wartość wyboru obiektu $c_i$ zostaje zmodyfikowany o tą wagę:

$$c_{i}=\sum_{j=1}^{|Q|}h_{ij}\cdot w_{j}=\sum_{j=1}^{|Q|}d_{ij}$$

Przykładowo dane jest uniwersum $U=\{h_1,h_2,h_{3}\}$, zbiór parametrów $E=\{e_1,e_2,e_3,e_4,e_5 \}$ oraz redukt $Q=\{e_1,e_2,e_4,e_5 \}$ przy czym do kolejnych parametrów przypisujemy wagi:
- $w_1=0.8$
- $w_2=0.7$
- $w_4=0.5$
- $w_5=0.3$
 
Dane te możemy przedstawić w następującej tabeli:

| $U$ | $e_1, w_1 = 0.8$ | $e_2, w_2 = 0.7$ | $e_4, w_4 = 0.5$ | $e_5, w_5 = 0.3$ | $c_i$ |
|---|---|---|---|---|---|
| **$h_1$** | 0 | 1 | 1 | 0 | 1.2 |
| **$h_2$** | 1 | 0 | 0 | 0 | 0.8 |
| **$h_3$** | 0 | 0 | 0 | 1 | 0.3 |

