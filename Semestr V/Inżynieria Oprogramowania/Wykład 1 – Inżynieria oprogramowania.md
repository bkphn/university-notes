## Inżynieria oprogramowania
**Inżynieria oprogramowania** to dziedzina informatyki opisująca wszystkie fazy cyklu życia (produkcji) oprogramowania.

Opiera się ona na dążeniu do uzyskania wysokiej jakości produktu – oprogramowania.

## Dylemat wagonika
**Dylemat wagonika** (ang. *the trolley problem*) to jeden z najsłynniejszych eksperymentów myślowych w historii etyki i filozofii moralnej. Został sformułowany w 1967 roku przez brytyjską filozofkę Philippę Foot, a następnie rozwinięty i spopularyzowany przez badaczy takich jak Judith Jarvis Thomson.

*Rozpędzony wagonik kolejki wyrwał się spod kontroli i pędzi w dół torów. Na jego drodze znajduje się pięć osób, które są przywiązane do torów i nie mogą uciec. Stoisz obok zwrotnicy. Jeśli pociągniesz za dźwignię, skierujesz wagonik na boczny tor. Niestety, do bocznego toru przywiązana jest jedna osoba. Jedyne opcje to brak działania lub pociągnięcie dźwigni. Co robisz?*

Sytuacja ta wymusza na odbiorcy opowiedzenie się za jednym z dwóch głównych systemów etycznych:
- **Utylitaryzm**: według tej logiki pięć ludzkich istnień ma matematycznie i moralnie większe znaczenie niż jedno. Pociągnięcie za dźwignię jest więc moralnym obowiązkiem, ponieważ minimalizuje ogólne cierpienie.
- **Deontologia**: zwolennicy tego nurtu argumentują, że istnieje fundamentalna różnica między „pozwoleniem komuś umrzeć” a „aktywnym zabiciem kogoś”. Pociągnięcie za dźwignię to celowe, aktywne działanie prowadzące do czyjejś śmierci, co samo w sobie jest złe, niezależnie od ewentualnych zysków

**Dylemat kładki** (ang. *the footbridge dilemma*) to modyfikacja dylematu wagonika. W tej wersji stoisz na wiadukcie nad torami, a obok ciebie stoi bardzo ciężki człowiek. Aby zatrzymać wagonik i uratować pięć osób, musisz zepchnąć tego człowieka na tory. Choć matematyczny bilans jest identyczny jak przy dźwigni, reakcje ludzi drastycznie się różnią.

Do podobnych dylematów, ubranych w nieco inne szaty, może dochodzić każdego dnia. Kierowca mając do wyboru spowodowanie wypadku, bądź potrącenie pieszego działa instynktownie. W wypadku pojazdów autonomicznych takie zachowania muszą być z góry zdefiniowane – samochód nie ma instynktu. To inżynier musi podjąć decyzję, jak ma się zachować pojazd w takiej sytuacji.

## Jakość oprogramowania
Tworząc oprogramowanie inżynierowie muszą zapewnić jego wysoką jakość. Przez jakość oprogramowania rozumie się:
- spełnienie wymagań użytkownika,
- niezawodność,
- ergonomia,
- efektywność,
- łatwość konserwacji,
- efektowność

Tworząc program nie możemy zapewnić, że jest on bezbłędny. Celem inżyniera nie jest wyeliminowanie błędów, a dążenie do jak najmniejszego prawdopodobieństwa wystąpienia błędu. Sekwencyjne testowanie wszystkich możliwych scenariuszy wpada w **eksplozję przestrzeni stanów**, zwaną również eksplozją kombinatoryczną. Przez to zjawisko czas potrzebny na tzw. testowanie wyczerpujące (ang. _exhaustive testing_) nawet małych aplikacji rośnie wykładniczo i w praktyce operacyjnej dąży do nieskończoności.

Zasada Dijkstry mówi, że „Testowanie programów może dowodzić obecności błędów, ale nigdy ich braku”.

**Właściwość semantyczna** to zachowanie programu – to, co ten program robi (w przeciwieństwie do składni, czyli tego, jak kod jest napisany). **Nietrywialna właściwość semantyczna** oznacza właściwość, którą posiadają niektóre programy, a inne nie. Właściwość pod tytułem *ten program działa poprawnie* jest klasyczną nietrywialną właściwością semantyczną i zgodnie z twierdzeniem Rice'a:

>[!danger] Twierdzenie Rice'a
>Wszystkie nietrywialne właściwości semantyczne programów są nierozstrzygalne.

