## Suma w wykładniku
Dla dowolnych $m,n\in\mathbb{N}$ zachodzi:

$$x^{m+n}=x^m\cdot x^n$$

Możemy zdefiniować podobne własności dla silnii dolnej i górnej, prezentują się one następująco:

$$x^{\overline{m+n}}=x^\overline{m}⋅(x+m)^\overline{n}$$

$$x^\underline{m+n}=x^\underline{m}⋅(x−m)^\underline{n}$$

## Własności liczb Stirlinga
Dla dowolnego $n\in\mathbb{N}_{+}$ zachodzą wzory:
- Dla $k=n$

$$\left[\begin{matrix} n \\ n \end{matrix} \right]=\left\{\begin{matrix} n \\ n \end{matrix} \right\}=\binom{n}{n}=1$$

Wybierając $n$ cykli z $n$-elementowego zbioru mamy tylko jedną możliwość utworzenia takowych: $[1], [2],\dots,[n−1],[n]$. Analogicznie możemy ułożyć n rozłącznych podzbiorów tylko na jeden sposób: $\{1\},\{2\},\dots,\{n−1\},\{n\}$.

- Dla $k=n−1$

$$\left[\begin{matrix} n \\ n-1 \end{matrix} \right]=\left\{\begin{matrix} n \\ n-1 \end{matrix} \right\}=\binom{n}{2}$$

Wybierając $n−1$ podzbiorów bądź cyklów z $n$-elementowego zbioru zawsze jeden zestaw składać się będzie z dwóch elementów. Jako, że zarówno dla podzbiorów jak i dla cyklów kolejność dwuelementowego zestawu nie ma znaczenia: $[a, b]=[b,a]$, $\{a,b\}=\{b,a\}$ to zaczynamy od wybrania dwóch elementów, które zostaną połączone w parę. Wyboru takiego możemy dokonać na $\binom{n}{2}$ sposobów. Pozostałe elementy trywialnie tworzą jednoelementowe cykle/podzbiory. 

