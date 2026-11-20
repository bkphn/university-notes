## Stany Bella
**Splątanie kwantowe** (ang. *quantum entanglement*) jest właściwością stanu złożonego układu, który, w przypadku stanów czystych, nie daje się zapisać jako iloczyn tensorowy stanów jego podukładów.

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

## Splątanie a superpozycja
Parę bitów reprezentujemy przez:

$$\ket{\psi}=a\ket{00}+b\ket{01}+c\ket{10}+d\ket{11} $$

Rozważmy dwa kubity: $\ket{+}_{A}$ należący do osoby $A$ i $\ket{+}_{B}$ należący do osoby $B$. Możemy rozważyć ich iloczyn:

$$\ket{+}_{A}\otimes \ket{+}_{B}= \frac{\ket{00}+\ket{01}+\ket{10}+\ket{11}}{2}  $$

mamy tutaj do czynienia ze **stanem iloczynowym**, możemy osobno podać stan osoby $A$ i stan osoby $B$. Stany te są niezależne – znając wynik osoby $A$ nie możemy powiedzieć nic o wyniku osoby $B$.

Dla osoby $A$ stany $\ket{+}_{A}\otimes \ket{+}_{B}$ i $\ket{\Phi^+}$ są nierozróżnialne. W obu przypadkach, dla osoby $A$:

$$P(0)=P(1)=\frac{1}{2}$$

Różnica wychodzi dopiero przy analizie pary, w przypadku $\ket{+}_{A}\otimes \ket{+}_{B}$ mamy:

$$P(00)=P(01)=P(10)=P(11)=\frac{1}{4}$$

natomiast w przypadku $\ket{\Phi^+}$:

$$P(00)=P(11)=1, \qquad P(01)=P(10)=0$$

Znając wynik pomiaru osoby $A$ możemy z pewnością określić wynik jeszcze nie odbytego pomiaru osoby $B$, zakładając pomiar w tej samej bazie obliczeniowej.

## Tworzenie pary Bella
Parę Bella możemy stworzyć samodzielnie, korzystając z określonych bramek logicznych. Przykładowo ze stanu $\ket{00}$ możemy stworzyć stan $\ket{\Phi^+}$ przepuszczając parę kubitów przez obwód:

[]

$$\ket{00} \overset{H\otimes I}{\rightarrow} \frac{1}{\sqrt{ 2 }}\ket{00}+\frac{1}{\sqrt{ 2 }}\ket{10}\overset{\mathrm{CNOT}}{\rightarrow} \frac{1}{\sqrt{ 2 }}\ket{00}=\frac{1}{\sqrt{ 2 }}\ket{11}=\ket{\Phi^+}  $$

Zachodzi więc:

$$\mathrm{CNOT}((H\otimes I)\ket{00} )=\ket{\Phi^+} $$

Splątanie możemy usunąć, przepuszczając stan splątany przez bramki w odwrotnej kolejności:

$$(H\otimes I)(\mathrm{CNOT\ket{\Phi^+}})=\ket{00} $$

## Teleportacja kwantowa
**Teleportacja kwantowa** (ang. *quantum teleportation*) to proces przenoszenia stanu kwantowego jednego układu fizycznego na inny, przestrzennie oddalony układ, bez konieczności fizycznego transportowania cząstki, która pierwotnie znajdowała się w tym stanie.

Teleportacja kwantowa operuje na trzech kubitach:
- **Kubit** $Q$ – którego stan chcemy przeteleportować,
- **Kubit** $A$ – kubit pierwszej osoby, splątany z kubitem drugiej osoby,
- **Kubit** $B$ – kubit osoby drugiej, splątany z kubitem osoby pierwszej.

Schemat teleportacji kwantowej prezentuje się następująco:

[]

Górna linia odpowiada kubitowi $Q$, a dwie poniżej to kolejno kubit $A$ i splątany z nim kubit $B$:

$$\ket{\chi}_{Q}=\alpha \ket{0}+\beta \ket{1},\qquad \ket{\Phi^+}_{AB}=\frac{1}{\sqrt{ 2 }}\ket{00}+\frac{1}{\sqrt{ 2 }}\ket{11}    $$

Zaczynamy od iloczynu kubitów:

$$\ket{\chi}_{Q} \otimes \ket{\Phi^+}_{AB}=\frac{1}{\sqrt{ 2 }}(\alpha \ket{000}+\alpha \ket{011}+\beta \ket{100}+\beta \ket{111} )$$

Osoba pierwsza przepuszcza kubit $Q$ i kubit $A$ przez bramkę $\mathrm{CNOT}$, a następnie wykonuje na kubicie $Q$ operację $H$. Z tego powodu każdy składnik rozdziela się na dwa. Po zebraniu wyrazów według pierwszych dwóch bitów otrzymujemy cztery gałęzie wyniku. 

Osoba pierwsza mierzy $QA$ w bazie $Z$, każdy wynik ma prawdopodobieństwo $\frac{1}{4}$. Na podstawie wyniku otrzymanego z tego pomiaru, osoba druga musi zastosować adekwatną bramkę, doprowadzi wtedy swój kubit $B$ do stanu $\ket{\chi}_{Q}$ – tym samym doszło do przeteleportowania przez przestrzeń informacji o kubicie $Q$. 

Pierwotny stan kwantowy osoby $A$ został zniszczony w wyniku pomiaru.

>[!example] Przykład teleportacji kwantowej kubitu w stanie $\ket{\chi}_{Q}$
>0. **Dane**
>Stan teleportowany $\ket{\chi}_{Q}=\alpha\ket{0}+\beta\ket{1}$
>Stan splątany $\ket{\Psi^+}_{AB}=\frac{1}{\sqrt{ 2 }}\ket{01}+\frac{1}{\sqrt{ 2 }}\ket{10}$
>
>1. **Iloczyn stanów**
>
>$$\ket{\chi}_{Q}\otimes \ket{\Psi^+}_{AB} = \frac{1}{\sqrt{ 2 }}(\alpha \ket{001} + \alpha \ket{010} + \beta \ket{101} + \beta \ket{110}  )$$
>
>2. **Bramka CNOT na kubitach** $Q,A$
>   
> $$(\mathrm{CNOT}\otimes I)(\ket{\chi}_{Q}\otimes \ket{\Psi^+}_{AB})=\frac{1}{\sqrt{ 2 }}(\alpha \ket{001}  + \alpha \ket{010}  + \beta \ket{111} + \beta \ket{100}  )$$  
> 
>3. **Bramka Hadamarda na kubicie** $Q$
>  
>  $H\ket{0}=\frac{1}{\sqrt{ 2 }}(\ket{0}+\ket{1})$
>  $H\ket{1}=\frac{1}{\sqrt{ 2 }}(\ket{0}-\ket{1})$
>  
> $$(H\otimes I\otimes I)\left(\frac{1}{\sqrt{ 2 }}(\alpha \ket{001}  + \alpha \ket{010}  + \beta \ket{111} + \beta \ket{100}  )\right) = \\ \frac{1}{2} \bigg( \alpha \Big(\ket{0}+\ket{1}\Big)\ket{01} + \alpha\Big(\ket{0}+\ket{1}\Big)\ket{10}  + \beta \Big(\ket{0}-\ket{1}  \Big)\ket{11} + \beta\Big(\ket{0}-\ket{1}\Big)\ket{00}  \bigg)= \\ \frac{1}{2}\bigg( \alpha \ket{001} + \alpha \ket{101} + \alpha \ket{010} + \alpha \ket{110} + \beta \ket{011} - \beta \ket{111} + \beta \ket{000} - \beta \ket{100}\bigg)$$  
> 
> 4. **Grupowanie po parze** $QA$
>    
>  $$\frac{1}{2}\bigg( \alpha \ket{001} + \alpha \ket{101} + \alpha \ket{010} + \alpha \ket{110} + \beta \ket{011} - \beta \ket{111} + \beta \ket{000} - \beta \ket{100}\bigg) = \\ \frac{1}{2}\ket{00}\Big(\alpha\ket{1}+\beta \ket{0}\Big)+\frac{1}{2}\ket{01}\Big(\alpha\ket{0}+\beta \ket{1}\Big)+\frac{1}{2}\ket{10}\Big(\alpha\ket{1}-\beta \ket{0}\Big)+\frac{1}{2}\ket{11}\Big(\alpha\ket{0}-\beta \ket{1}\Big) $$  
>  
>  5. **Wyznaczenie bramek drugiej osoby**
>   
| Pomiar $QA$ | Stan $B$ | Przekształcenie | Bramka $U$ | 
|-|-|-|-|
|$00$| $\begin{bmatrix}\beta\\\alpha\end{bmatrix}$| $\begin{bmatrix}\beta\\ \alpha\end{bmatrix}\overset{X}{\rightarrow}\begin{bmatrix}\alpha\\\beta\end{bmatrix}$|$X$|
|$01$|$\begin{bmatrix}\alpha\\ \beta\end{bmatrix}$| $\begin{bmatrix}\alpha\\ \beta\end{bmatrix}$|$I$|
|$10$|$\begin{bmatrix}-\beta \\ \alpha\end{bmatrix}$|$\begin{bmatrix}-\beta\\\alpha\end{bmatrix}\overset{X}{\rightarrow}\begin{bmatrix}\alpha\\-\beta\end{bmatrix}\overset{Z}{\rightarrow}\begin{bmatrix}\alpha\\\beta\end{bmatrix}$|$ZX$|
|$11$|$\begin{bmatrix}\alpha\\-\beta\end{bmatrix}$|$\begin{bmatrix}\alpha\\-\beta\end{bmatrix}\overset{Z}{\rightarrow}\begin{bmatrix}\alpha\\\beta\end{bmatrix}$|$Z$|

Po wykonaniu pomiaru na kubitach $Q,A$ i przesłaniu wyniku drugiej osobie, stosuje odpowiednią operację unitarną $U$ i otrzymuje stan kubitu $Q$, który fizycznie znajdował się u pierwszej osoby.

$$\ket{\chi}_{Q} \xrightarrow{\text{teleportacja}}
\ket{\chi}_{B}$$
