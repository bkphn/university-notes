## Logika
**Logika** to nauka formalna zajmująca się badaniem reguł poprawnego rozumowania, jasnym formułowaniem myśli oraz uzasadnianiem twierdzeń. Wywodzi się z filozofii, a jej autorem jest grecki filozof Arystoteles (384 pne – 322 pne).

Podstawy logiki nazywamy **rachunkiem zdań**. Logika matematyczna rozwinęła się od XIX wieku za sprawą George'a Boole'a, Kurta Gödela czy Alana Turinga. Wykorzystuje sztuczny język sformalizowany, rachunek zdań i kwantyfikatory.

## Zdania logiczne
**Zdaniem logicznym** nazywamy każde zdanie, o którym można obiektywnie zdecydować czy jest **prawdziwe** czy **fałszywe**. Zdaniami logicznymi nie są pytania i rozkazy.

>[!example] Przykłady zdań logicznych
>- Zdanie *Warszawa leży nad Wisłą* jest zdaniem logicznym.
>- Zdanie *Piast Gliwice jest najlepszą drużyną* nie jest zdaniem logicznym.
>- Zdanie *Każda liczba parzysta jest podzielna przez trzy* jest nieprawdziwym zdaniem logicznym.

## Wartości logiczne
Zdaniom logicznym przyporządkowujemy dwie wartości: prawdę i fałsz. W logice matematycznej oznaczamy je za pomocą cyfr $1$ i $0$.

>[!example] Przykłady przypisania wartości logicznej
>Zdanie *Każda liczba podzielna przez dwa jest parzysta* ma wartość logiczną $1$.
>Zdanie *Istnieje liczba pierwsza podzielna przez sześć* ma wartość logiczną $0$.

## Spójniki logiczne
Mając zdania logiczne możemy tworzyć **zdania złożone**, czyli takie zawierające **spójniki logiczne**. Zdania logiczne ich pozbawione nazywamy **zdaniami prostymi**.

Podstawowymi spójnikami logicznymi są:
- **Negacja**: Oznaczana symbolem $\neg$ (rzadziej $\sim$), czytamy ją jako *nieprawda, że...*;
- **Alternatywa**: Oznaczana symbolem $\lor$, czytamy ją jako *... lub...*;
- **Koniunkcja**: Oznaczana symbolem $\land$, czytamy ją jako *... i...*;
- **Alternatywa wykluczająca** (XOR): Oznaczana symbolem $\veebar$ lub $\oplus$, czytamy ją jako *albo... albo...*;
- **Implikacja**: Oznaczana przez $\implies$, czytamy ją jako *z... wynika...*
- **Równoważność**: Oznaczana przez $\iff$, czytamy ją jako *wtedy i tylko wtedy, gdy...*

## Warunki konieczne i dostateczne
Niech $p,q$ będą pewnymi zdaniami logicznymi. Jeżeli zachodzi $p\implies q$, to $p$ nazywamy **warunkiem dostatecznym** dla $q$, a $q$ nazywamy **warunkiem koniecznym** dla $p$.

Jeżeli zachodzi $p\iff q$ to $p$ jest **warunkiem koniecznym i dostatecznym** dla $q$, a $q$ jest warunkiem koniecznym i dostatecznym dla $p$.

## Tabele wartości logicznych
**Tabelą wartości logicznych** nazywamy tabelaryczną reprezentację zdań logicznych. Dla spójników logicznych tabele przedstawiają się następująco:

| $p$ | $\neg p$ |
| --- | -------- |
| $0$ | $1$      |
| $1$ | $0$      |

| $p$ | $q$ | $p\land q$ | $p\lor q$ | $p\oplus q$ | $p\implies q$ | $p\iff q$ |
| --- | --- | ---------- | --------- | ----------- | ------------- | --------- |
| $0$ | $0$ | $0$        | $0$       | $0$         | $1$           | $1$       |
| $0$ | $1$ | $1$        | $0$       | $1$         | $1$           | $0$       |
| $1$ | $0$ | $1$        | $0$       | $1$         | $0$           | $0$       |
| $1$ | $1$ | $1$        | $1$       | $0$         | $1$           | $1$       |

## Tautologie
**Tautologią**, bądź **prawem rachunku zdań** nazywamy każde zdanie złożone, które jest prawdziwe niezależnie od prawdziwości lub fałszywości zdań składowych.

Z jednej strony tautologię można nazwać wyrażeniem jałowym, to znaczy takim, które nie wnosi nic do logicznego rozumowania. Z drugiej strony tautologie są ważnymi prawami, które pewne złożone wyrażenia pozwalają przekształcać na inne być może mniej złożone. Większość rozumowań logicznych opiera się na wykorzystaniu tych praw.

Wśród najważniejszych tautologii wyróżniamy:
- **Prawo wyłączonego środka**

$$p\land\neg p$$

- **Prawo tożsamości**

$$p\implies p$$

- **Prawa przemienności**

$$(p\lor q)\iff(q\lor p)$$
$$(p\land q)\iff(q\land p)$$

- **Prawa łączności**

$$(p\lor q)\lor r\iff p\lor(q\lor r)$$
$$(p\land q)\land r\iff p\land (q\land r)$$

- **Prawa rozdzielności**

$$p\land(q\lor r)\iff(p\land q)\lor(p\land r)$$
$$p\lor(q\land r)\iff(p\lor q)\land(p\lor r)$$

- **Prawa de Morgana**

$$\neg(p\lor q)\iff \neg p\land \neg q$$
$$\neg(p\land q)\iff \neg p\land \neg q$$

- **Reguła transpozycji**

$$(p\implies q)\iff(\neg q\implies \neg p)$$

- **Zaprzeczenie implikacji**

$$\neg(p\implies q)\iff p\land \neg q$$

- **Rozbicie równoważności**

$$(p\iff q) \implies (p\implies q)\land(q\implies p)$$

- **Sylogizm warunkowy**

$$(p\implies q)\land(q\implies r)\implies(p\implies r)$$

- **Reguła odrywania *modus ponens***

$$(p\implies q)\land p\implies q$$

- **Reguła odrywania *modus tollens***

$$(p\iff q)\land q \implies \neg p$$

## Sylogizmy
**Sylogizm** to klasyczny schemat wnioskowania dedukcyjnego, w którym z dwóch przesłanek wyprowadza się wniosek. Został sformułowany przez Arystotelesa i stanowi podstawę dawnej logiki formalnej

## Sprowadzenie do sprzeczności
**Sprowadzenie do sprzeczności** (łac. *reductio ad absurdum*) to metoda dowodzenia matematycznego, w której zakładamy, że teza, którą chcemy udowodnić, jest fałszywa, a następnie pokazujemy, że takie założenie prowadzi do sprzeczności (np. że pewne zdanie jest jednocześnie prawdziwe i nieprawdziwe). Innymi słowy: udowadniamy, że zaprzeczenie naszej tezy jest niemożliwe, więc sama teza musi być prawdziwa.

## Logika w nauce
Logika jest językiem, którym posługujemy się w dowolnej dziedzinie naukowej. Prawa naukowe są zdaniami logicznymi, wyrażanymi z użyciem spójników logicznych (choć nie zawsze w sposób oczywisty). Najczęściej używana jest implikacja lub równoważność.

W matematyce własności pewnych obiektów wyrażamy przy pomocy **twierdzeń** (lematów, wniosków), które uzasadniamy w dowodach. W twierdzeniu zapisanym w postaci implikacji $p\implies q$, zdanie $p$ nazywamy **założeniem** twierdzenia, a $q$ jego **tezą**.

Istnieją różne techniki dowodzenia twierdzeń typu $p \implies q$. Jedną z nich jest dowód **wprost** polegający na tym, że zaczynając od tego, że założenie jest zdaniem prawdziwym, a potem używając prawidłowych operacji logicznych dochodzimy do tego, że teza też jest zdaniem prawdziwym. Wtedy prawdziwa jest implikacja $p \implies q$.

Inną metodą dowodzenia jest dowód **nie wprost** (nazywany też dowodem apagogicznym), który opiera się na sprowadzeniu do sprzeczności. Taki dowód przeprowadzamy w różny sposób. Pierwszy z nich opiera się na tautologii $p \implies q \iff (\neg q \implies \neg p)$, więc zamiast udowadniać, że z $p$ wynika $q$ udowadniamy, że z $\neg q$ wynika $\neg p$. Inny sposób opiera się na wykazaniu, że niemożliwe jest zaprzeczenie implikacji $p \implies q$, a ponieważ $\neg(p \implies q) \iff (p\land \neg q)$, to w tym przypadku pokazujemy, że zdanie $p \land \neg q$ jest nieprawdziwe.
## Kontrprzykłady
Tautologia $\neg(p \implies q) \iff (p \land \neg q)$ jest używana również do konstruowania przykładów pokazujących, że implikacja $p \implies q$ jest nieprawdziwa. Takie przykłady nazywamy często **kontrprzykładami** na prawdziwość implikacji $p\implies q$.