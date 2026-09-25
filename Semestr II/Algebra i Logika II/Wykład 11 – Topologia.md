## Prowadzący
Wykład był prowadzony przez prof. Pawła Dłotko z Centrum Diosciuri w Topologicznej Analizie Danych.

## Niedokładności klasycznej statystyki
Analizując dane, często korzystamy ze znanych statystyk opisowych, takich jak średnia, wariancja, korelacja liniowa, regresja liniowa, odchylenie standardowe czy mediana. Matematycy zdali sobie jednak sprawę, że w wielu sytuacjach to zbyt mało, a statystyki takie nie oddają prawdziwej natury danych. 

Istnieją zestawy danych (np. cztery diametralnie różne zbiory danych na wykresach), które posiadają identyczne statystyki opisowe. Te niedoskonałości klasycznej statystyki zmusiły matematyków do szukania alternatywnych metod analitycznych, co poskutkowało narodzinami całkowicie nowej gałęzi matematyki – topologii.

## Topologia
Topologia jest działem matematyki zajmującym się badaniem przestrzeni topologicznych, czyli obiektów, w których można zdefiniować pojęcia ciągłych przekształceń. 

Topologia bada obiekty nie przez ich dokładne wymiary (długości, kąty, objętości), ale przez to, jak można je przekształcać bez rozrywania i sklejania. Mówimy, że dwa obiekty są **równoważne topologicznie**, jeśli można je przekształcić jeden w drugi za pomocą takiej deformacji. Topologiczne podejście pozwala na alternatywne patrzenie na dane, ignorując dokładne odległości między punktami, a skupiając się bardziej na globalnym kształcie.

## Operacje na przestrzeniach topologicznych
Zbiór $n$-wymiarowych punktów oddalonych o 1 od środka przestrzeni $\mathbb{R}^{n+1}$ nazywamy $n$-wymiarową **sferą** i oznaczamy jako $S^n$ bądź $\mathbb{S}^n$:

$$S^n = \{(x_0, \dots, x_n) \in \mathbb{R}^{n+1} : x_0^2 + \dots + x_n^2 = 1\}$$

Na przestrzeniach topologicznych (obiektach) możemy wykonywać operacje, tworząc z nich nowe przestrzenie:
* **Iloczyn kartezjański ($X \times Y$):** Każdy punkt to para $(x, y)$. Przykładowo, $S^1 \times S^1$ to **torus**.
* **Suma rozłączna ($X \cup Y$):** Łączy dwa obiekty w jedną przestrzeń topologiczną. Przykładowo, $S^1 \cup S^1$ to dwa okręgi rozłączne.
* **Kompaktowe sklejenie ($X \vee Y$):** Sklejenie dwóch przestrzeni w jednym punkcie. Przykładowo, $S^1 \vee S^1$ to dwa okręgi styczne w jednym punkcie.
* **Iloczyn smash ($X \wedge Y$):** Zmodyfikowany iloczyn kartezjański, w którym wszystkie punkty bazowe są "ściskane" do jednego punktu. Zachodzi izomorfizm: $S^m \wedge S^n \cong S^{m+n}$.

Przykładem obiektów równoważnych topologicznie może być torus i kubek.

## Liczby Bettiego
Liczbę $n$-wymiarowych dziur w obiekcie nazywamy $n$-tą **liczbą Bettiego** i oznaczamy jako $b_n$.
* $b_0$ oznacza, z ilu odseparowanych kawałków składa się obiekt.
* $b_1$ informuje o tym, ile jednowymiarowych dziur znajduje się w obiekcie.
* $b_2$ informuje o tym, ile pustych, dwuwymiarowych przestrzeni znajduje się w obiekcie.

> [!example] Liczby Bettiego na przestrzeni $S^1 \times S^1$ (torus)
> * $b_0 = 1$
> * $b_1 = 1 + 1 = 2$
> * $b_2 = 1$
> * $b_{n > 2} = 0$

Liczby Bettiego są powszechnie stosowane w topologicznej analizie danych, gdzie liczba $b_0$ pozwala zobaczyć, z ilu osobnych grup składają się dane, $b_1$ wykrywa dziury w tych danych itd.

## Homologie
**Homologia** to narzędzie topologii, które służy do badania kształtu i struktury obiektu za pomocą struktur algebraicznych. Homologia przypisuje przestrzeni topologicznej ciąg grup abelowych $H_n$, które opisują jej dziury w $n$-tym wymiarze.

Jeżeli przestrzeni topologicznej $X$ nie da się podzielić na dwa niepuste, rozłączne, otwarte podzbiory, to mówimy, że przestrzeń $X$ jest **spójna**. Składowa spójności punktu $x \in X$ to największy spójny podzbiór $C \subset X$ taki, że $x \in C$. Składową spójności określa zerowa liczba Bettiego $b_0$.

Każda $n$-ta liczba Bettiego jest rangą grupy homologii $H_n$:

$$\operatorname{rank}(H_n) = b_n$$

## Odporność na zaszumienie i inne pojęcia
Klasyczna statystyka ma bardzo małą odporność na zaszumienie – dodanie losowych punktów do wykresu może całkowicie zmienić jej statystyki opisowe, wpływając na odbiór danych. Topologia podchodzi do tego problemu inaczej, badając globalny kształt danych.

* **Charakterystyka Eulera:** 

  $$\chi = V - E + F = 2$$

  $$\chi(K) = \sum_{n \ge 0} (-1)^n |K_n| = \sum_{n \ge 0} (-1)^n \beta_n(K)$$

* **Metryka $p$-Wassersteina:** 

  $$W_p(C, D) = \left[ \inf_{\eta: C \to D} \sum_{(b,d) \in C} \|(b, d) - \eta(b, d)\|_\infty^p \right]^{\frac{1}{p}}$$

* **Pozostałe zagadnienia z wykładu:** Jednopróbkowe testy zgodności (Test Kolmogorova-Smirnova, TopoTest), moc testu, mapowanie wielowymiarowych obiektów oraz algorytm Ball Mapper (uzyskanie pokrycia danych).
