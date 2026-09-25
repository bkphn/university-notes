## Grafy planarne
**Grafem planarnym** nazywamy graf, który można narysować na płaszczyźnie bez przecięć. 

Przykładowo zarówno grafy $K_4$  jak i $K_{2,3}$ są grafami planarnymi, natomiast grafy $K_5$ oraz $K_{3,3}$ nie są grafami planarnymi. Ten drugi fakt odgrywa centralną rolę w twierdzeniu polskiego matematyka Kazimierza Kuratowskiego od nazwiska którego, kliki $K_n$ zawdzięczają literę *K* w nazwie. 

>[!danger] Twierdzenie Kuratowskiego
> Niech $G$ będzie grafem. Graf $G$ nie jest planarny, jeżeli zawiera podgraf homeomorficzny do $K_{3,3}$ bądź $K_5$.

## Grafy homeomorficzne
Grafami homeomorficznymi nazywamy parę grafów $G, G'$, w którym jeden powstaje przez wygładzenie wierzchołków stopnia $2$ drugiego z grafów. Oznacza to, że jeżeli $\deg ⁡v=2$ oraz istnieje para krawędzi $uv$ oraz $vw$, to $G'=G+uw−v$.

## Kolorowanie grafów
Niech $G=(V,E)$ będzie grafem i niech istnieje zbiór $C$ taki, że $|C|=k$. Funkcję $c: V\rightarrow C$ nazywamy **$k$-kolorowaniem** grafu $G$, zbiór $C$ nazywamy zbiorem kolorów, a elementy zbioru $C$
**kolorami**.

Reprezentując $k$-kolorowanie grafu $G$ na rysunku, często wierzchołki oznacza się za pomocą odpowiadających kolorów ze zbioru $C$. Chcąc zachować oryginalne poetykietowanie wierzchołków każdemu elementowi z ze zbioru $C$ przypisuje się barwę, którą koloruje się wierzchołki na rysunku.
![[Pasted image 20260919143852.png|305]]

## Kolorowanie właściwe
Niech $G$ będzie grafem, a $c$ $k$-kolorowaniem grafu $G$. Kolorowanie $c$ nazywamy **właściwym $k$-kolorowaniem** grafu $G$, jeżeli dla każdej pary sąsiednich wierzchołków przyjmuje ono różne wartości:

$$\forall_{u,v\in V}  :uv\in E\implies c(u)\neq c(v)$$

Graf nazywamy **$k$-kolorowalnym**, jeżeli istnieje $k$-kolorowanie właściwe tego grafu.

Dowolny graf $G$ taki, że $|G|=n$ jest $n$-kolorowalny. Takie kolorowanie nazywamy **kolorowaniem naiwnym**.

## Liczby chromatyczne
Liczbą chromatyczną $\chi(G)$ grafu $G$ nazywamy najmniejszą liczbę $k$ taką, że istnieje właściwe $k$-kolorowanie $c$. Nietrudno zauważyć, że dla dowolnego grafu prostego $G$ zachodzi:

$$1\leq \chi(G)\leq|G|$$

Innymi mniej lub bardziej oczywistymi obserwacjami są:
- $G$ jest grafem pełnym wtedy i tylko wtedy, gdy $\chi (G)=|G|$
- $G$ jest grafem pustym wtedy i tylko wtedy, gdy $\chi (G)=1$
- $G$ jest grafem dwudzielnym wtedy i tylko wtedy, gdy $\chi (G)=2$
- $G$ zawiera cykl nieparzystej długości wtedy i tylko wtedy, gdy $\chi (G)\geq 3$

Przydatnymi twierdzeniami w analizowaniu liczb chormatycznych grafów są:

>[!danger] Twierdzenie o kolorowaniu zachłannym
> Jeżeli $G$ jest grafem prostym, to:
>
> $$\chi (G)\leq \Delta(G)+1$$
>

oraz zaproponowane w 1941 przez R. Leonarda Brooksa:

>[!danger] Twierdzenie Brooksa
> Jeżeli $G$ jest spójnym grafem prostym, nie będącym cyklem nieparzystej długości ani grafem pełnym, to:
>
> $$\chi (G)\leq \Delta(G)$$
>

Dla dowolnej ścieżki $C_n$ zachodzi:

$$\chi(C_{n})=\begin{cases}
2, \qquad 2\mid |G| \\
3, \qquad 2 \not\mid |G|
\end{cases}$$

## Liczby klikowe grafu
Kliką nazywamy podgraf pewnego grafu $G$, w którym każda para wierzchołków połączona jest krawędziami. Klika tworzy graf pełny $K_n$.

Klikę nazywamy największą, jeśli w danym grafie nie istnieje klika o większej liczbie wierzchołków. Rząd największej kliki będącej podgrafem grafu $G$ nazywamy **liczbą klikową grafu** $G$ i oznaczamy jako $\omega(G)$.

Graf, którego liczba chromatyczna jest równa rozmiarowi największej kliki $\chi (G)=\omega(G)$  nazywamy **grafem doskonałym**.

## Twierdzenie o czterech barwach
Jednym z najsłynniejszych twierdzeń teorii grafów jest tzw. twierdzenie o czterech barwach:

>[!danger] Twierdzenie o czterech barwach
> Jeżeli $G$ jest planarnym grafem prostym, to:
>
> $$\chi (G)\leq4$$
>

Oznacza to, że dowolną mapę na płaszczyźnie jesteśmy w stanie pokolorować zaledwie czterema kolorami, zapewniając przy tym, że żadne sąsiadujące regiony nie będą pokryte tym samym kolorem. 
![[Pasted image 20260919155435.png|382]]
Hipotezę tą po raz pierwszy wysnuł August Ferdinand Möbius w 1840 roku, tej samej obserwacji dokonał niezależnie 12 lat później student University College London Francis Guthrie, w trakcie kolorowania map hrabstw Anglii. Zaczął eksperymentować z rysowaniem bardziej skomplikowanych, fikcyjnych układów granic, jednak bez względu na to, jak bardzo się starał, nigdy nie potrzebował piątego koloru.

Wieść o problemie trafiła do matematyka Augustusa De Morgana, który zafascynował się hipotezą. Tego samego dnia napisał słynny list do genialnego irlandzkiego matematyka, sir Williama Rowana Hamiltona, pytając go, czy zna ten problem i czy potrafi go dowieść. Hamilton odpisał krótko, że problem go nie interesuje.

Przez ponad sto lat hipoteza ta pozbawiona była dowodu, zmieniło się to dopiero w 1936 roku za sprawą Wolfganga Hakena i Kennetha Appela, którym udało się zredukować liczbę przypadków do pewnej ogromnej, ale skończonej liczby, każdy z nich został zweryfikowany przy pomocy komputera.

Jest to pierwsze wielkie twierdzenie, które udowodnione zostały przy pomocy komputera, do dzisiaj nie jest znany dowód w pełni weryfikowalny przez człowieka.

## Kolorowanie krawędziowe
Niech $G$ będzie grafem i niech dany będzie zbiór $C$ taki, że $|C|=k$. Funkcję $c':E\rightarrow C$ nazywamy $k$-kolorowaniem krawędziowym grafu $G$.

Kolorowanie $c'$ nazywamy **właściwym $k$-kolorowaniem krawędziowym** grafu $G$, jeżeli dla każdej pary sąsiednich krawędzi przyjmuje ono różne wartości:

$$\forall_{uv,vw\in E} : u\neq w\implies c'(uv)\neq c'(vw)$$

## Indeks chromatyczny
Indeksem chromatycznym $\chi' (G)$ grafu $G$ nazywamy najmniejszą liczbę $k$ taką, że istnieje właściwe $k$-kolorowanie krawędziowe $c'$.

Dla gwiazd $K_{1,n}$ zachodzi: $\chi' (K_{1,n})=n$ oraz $\chi (K_{1,n})=2$

Dany jest graf prosty $G$. W wierzchołku o maksymalnym stopniu $\Delta(G)$ spotyka się dokładnie $\Delta(G)$ krawędzi. Każde dwie z tych krawędzi są sąsiednie, więc w poprawnym kolorowaniu krawędziowym muszą mieć różne kolory. Potrzeba więc co najmniej $\Delta(G)$ kolorów, więc zachodzi:

$$\chi'(G)\geq\Delta(G)$$

W 1964 roku Vizing zauważył, że istnieje także ograniczenie górne ograniczenie indeksu chromatycznego grafu:
>[!danger] Twierdzenie Vizinga
> Jeżeli $G$ jest grafem prostym, to:
>
> $$\Delta(G)\leq\chi' (G)\leq\Delta(G)+1$$
>

## Klasy grafowe
Dzięki twierdzeniu Vizinga możemy zauważyć, że indeks chromatyczny może przyjąć jedynie dwie wartości:

$$\chi' (G)=\Delta(G)\lor \chi' (G)=\Delta(G)+1$$

Na podstawie powyższej obserwacji możemy zdefiniować klasy grafowe:
- **Klasa I**: Jeżeli $\chi' (G)=\Delta(G)$, to graf $G$ nazywamy grafem klasy I.
- **Klasa II**: Jeżeli $\chi' (G)=\Delta(G)+1$, to graf $G$ nazywamy grafem klasy II.

Vadim Vizign zauważył również, że jeżeli $G$ jest grafem klasy II, to co najmniej trzy wierzchołki tego grafu mają maksymalny stopień.

Niech $\mathcal{G}(n)$ oznacza zbiór wszystkich grafów prostych o $n$ wierzchołkach, a $\mathcal{G}_{\text{I}}(n)$ zbiór wszystkich takich grafów należących do klasy pierwszej. Zgodnie z twierdzeniem Erdősa-Wilsona:

$$\lim_{ n \to \infty } \frac{|\mathcal{G}_{\text{I}}(n)|}{\mathcal{G}(n)}=1$$

## Problem Hadwigera-Nelsona
**Grafem geometrycznym** nazywamy pewien graf osadzony w $n$-wymiarowej przestrzeni. Każdy wierzchołek grafu reprezentowany jest przez pewien wektor $\mathbf{v}$, natomiast krawędzie są odcinkami łączącymi te wektory.

**Kolorowaniem płaszczyzny** $A$ nazywamy takie kolorowanie, że dwa dowolne punkty $x_1,x_2\in A$ o odległości $d$ równej $1$ miały różne kolory:

$$d(x_1,x_2 )=1⇒c(x_1 )\neq c(x_2 )$$

Niech $\chi_A$ oznacza liczbę chromatyczną pewnej przestrzeni $A$, czyli najmniejszą liczbę kolorów potrzebnych do pokolorowania przestrzeni $A$.

Łatwo można zauważyć, że dla osi $\mathbb{R}$ wystarczą jedynie dwa kolory (kolorujemy naprzemiennie domykając przedziały jednostronnie):

$$\chi_{\mathbb{R}}=2$$

**Problem Hadwigera-Nelsona** mówi, że nie jest znana liczba chromatyczna płaszczyzny $\mathbb{R}^2$. Łatwo wykazać, że liczba ta musi być niemniejsza od $4$ i niewiększa od $9$, dzieląc płaszczyznę na 9 przystających kwadratów. Od 2018 roku dzięki pracy Aubreya de Greya posiadamy znacznie lepsze ograniczenia:

$$\chi_{\mathbb{R}^2}\in\{5, 6, 7\}$$

