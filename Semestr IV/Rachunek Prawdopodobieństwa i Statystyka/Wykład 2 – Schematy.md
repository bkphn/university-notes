## Prawdopodobieństwo warunkowe
Dany jest eksperyment stochastyczny $S$, który daje zdarzenie elementarne $\omega$ oraz dwa zdarzenia $A,B\subseteq \Omega$. Jeżeli wiemy, że zaszło zdarzenie $B$, którego $P(B)>0$ i chcemy policzyć prawdopodobieństwo zdarzenia $A$ posługujemy się tzw. **prawdopodobieństwem warunkowym**, które pozwala nam na wyznaczenie prawdopodobieństwa $A$ pod warunkiem, że zaszło zdarzenie $B$. Prawdopodobieństwo warunkowe oznaczamy jako $P(A \mid B)$ i definujemy wzorem: $$P(A \mid B)=\frac{P(A\cap B)}{P(B)}$$
Jeżeli zdarzenia $A,B$ są niezależne, to zachodzi równość:
$$\frac{P(A\cap B)}{P(B)} = \frac{P(A)\cdot P(B)}{P(B)} =P(A)$$

Przekształcając wzór na prawdopodobieństwo warunkowe możemy wyznaczyć wzór na prawdopodobieństwo iloczynu zdarzeń: $$P(A\cap B)=P(B)\cdot P(A \mid B)=P(A)⋅P(B \mid A)$$
## Wzór Bayesa
W przypadku gdy prawdopodobieństwo zdarzenia $A$ jest trudne do policzenia, możemy rozbić je na mniejsze rozłączne zdarzenia. Podzielimy przestrzeń zdarzeń $\Omega$ na zdarzenia $B_i\neq \emptyset$, takie że $\Omega=\bigcup_{i=1}^n B_i$, na ich podstawie wyznaczymy prawdopodobieństwo zdarzenia $A$. W tym przypadku $P(A)$ nazywamy **prawdopodobieństwem całkowitym** i definiujemy wzorem: $$P(A)=\sum_{i=1}^n P(B_{i})\cdot P(A\mid B_{i})$$
Po przekształceniu tej równości otrzymujemy tzw. wzór Bayesa, który w odróżnieniu do wzoru na prawdopodobieństwo całkowite pozwala nam na podstawie skutku wyznaczyć przyczynę: $$\frac{{P(B_{i})\cdot P(A\mid B_{i})}}{P(A)}=\frac{P(B_{i})\cdot \frac{P(A\cap B_{i})}{P(B_{i})}}{P(A)}=\frac{P(A\cap B_{i})}{P(A)}=P(B_{i} \mid A)$$
Co w postaci uogólnionej prezentuje się następująco: $$P(B \mid A) =\frac{P(B)\cdot P(A\mid B)}{P(A)}$$
## Schematy
Niech $P(A)=p$. Schematem rachunku prawdopodobieństwa nazywamy uporządkowane metody wyznaczania prawdopodobieństw zdarzeń. Modele te pozwalają na wyznaczanie prawdopodobieństwa złożonych zdarzeń bez konieczności rozpatrywania każdej możliwości w $\Omega$. 

Do najpopularniejszych schematów należą:
- **Schemat 0 - 1**: W schemacie 0 - 1 mamy do czynienia z pewnym doświadczeniem $S$ z dokładnie dwoma możliwymi wynikami: $A$ oraz $\overline{A}$. Wynik $A$ tradycyjnie nazywamy sukcesem, a $\overline{A}$ porażką. W schemacie tym zachodzą wzory:  $$P(A)=p\in[0, 1]$$ $$P(\overline{{A}})=1-p=q\in[0,1]$$
- **Schemat geometryczny**: Schemat geometryczny opisuje sytuację, w której powtarzamy niezależne próby schematu 0 - 1 aż do momentu wystąpienia pierwszego zdarzenia przerywającego ciąg. Przez $A_n$ będziemy oznaczać fakt, że uzyskaliśmy dokładnie $n$ sukcesów z rzędu, a w próbie o numerze $n+1$ wypadła porażka: $$A_n = \underbrace{A \ldots A}_{n \text{ razy}} \overline{A}$$ Ponieważ poszczególne próby są niezależne, prawdopodobieństwo uzyskania wystąpienia ciągu $A_n$ wyrażana jest wzorem: $$P(A_n )=p^n (1−p)$$
- **Schemat Bernoulliego**: Schematem Bernoulliego nazywamy schemat, w którym w celu uzyskania prawdopodobieństwa wykonujemy dokładnie $n$ niezależnych prób. Przyjmijmy, że wśród tych $n$ prób uzyskaliśmy dokładnie $k$ sukcesów, zdarzenie takie będziemy oznaczać jako $A(n,k)$. 
  
  Prawdopodobieństwo takie zdarzenia wyznaczać będziemy ze wzoru: $$P(A(n,k))=C_n^k p^k (1−p)^{n−k}$$ gdzie $C_n^k$ jest czynnikiem odpowiadajcym dwumianowi Newtona, co po podstawieniu daje: $$P(A(n,k))=\binom{n}{k} p^k (1−p)^{n−k}$$
## Twierdzenie Poissona
Przez $a\gg b$ oznaczać będziemy fakt, iż liczba $a$ jest znacznie większa od $b$, a przez $a\ll b$ oznaczać będziemy fakt, iż $a$ jest znacznie mniejsze od $b$.

> [!danger] Twierdzenie Poissona
> Niech prawdopodobieństwo $P(A)=p$ będzie znikome $p\ll 1$. Wówczas, jeżeli liczba prób $n$ dąży do nieskończoności ($n \to \infty$) w taki sposób, że iloczyn $n \cdot p$ dąży do stałej dodatniej wartości $\lambda$, to zachodzi równość: $$\lim_{n \to \infty} P(A(n,k)) = \frac{\lambda^k}{k!} e^{-\lambda}$$

Granica ta jest bardzo dobrym przybliżeniem wartości prawdopodobieństwa dla przypadku gdy $n\gg1$, $p\ll1$. Z reguły, dla bezpieczeństwa, możemy posługiwać się tym przybliżeniem gdy iloczyn $p\cdot n\in(0, 20)$. $$P(A(n,k))\approx e^{-pn} \frac{(pn)^k}{k!}$$
