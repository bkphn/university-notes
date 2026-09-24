## Sztuczna inteligencja
Sztuczna inteligencja jest dziedziną wiedzy obejmująca sieci neuronowe, logikę rozmytą, obliczenia ewolucyjne, sztuczne życie i robotykę.

W sensie matematyczym rozumiemy AI jako tworzenie modeli symulujących inteligentne zachowania. W sensie informatycznym rozumiemy AI jako tworzenie programów komputerowych symulujących te zachowania.
## Podstawy biologiczne
Systemy sztucznej inteligencji odwozrowują budowę ludzkiego mózgu.

Nasz mózg ma objętość $1400\text{ cm}^3$ i powierzchnię $2000\text{ cm}^2$. Masa mózgu wynosi $1.5 \text{ kg}$, przykładowo kula o tej samej objętości ma zaledwie $600 \text{cm}^2$.

Zdolności intelektualne zależą od kory mózgowej, średnio w $3 \text{ mm}$ zawiera się 1010 komórek nerwowych i 1012 komórek glejowych. Komórki nerwowe wysyłają i przyjmują impulsy o częstotliwości od $1\text{ Hz}$ do $100\text{ Hz}$, czasie trwania od $1$ do $2 \text{ ms}$, napięciu $100\text{ mV}$ i szybkości propagacji od $1$ do $100 \text{ m/s}$. Szybkość pracy to 1018 operacji na sekundę. Wykonanie typowej operacji to nie więcej niż 100 kroków. 

Pojemności kanałów zymsłow:
- wzrok: $100 \text{ Mb/s}$
- dotyk: $1 \text{ Mb/s}$
- słuch: $15 \text{ kb/s}$
- węch: $1 \text{ kb/s}$
- smak: $100 \text{ b/s}$
## Historia uczenia maszynowego
W 1943 roku McCuloch i Pitts przedstawiają matematyczny model sztucznego neuronu z ludzkiego mózgu. W 1949 roku Hebb przedstawia regułę uczenia bez nadzoru, jako pierwszy zaproponował metodę uczenia sieci polegającą na zamianach wag połączeń między neuronami. W latach 50-tych zaczęto budować pierwsze sieci neuronowe. W 1958 Rosenblatta przedstawia pierwszą implementację perceptronu z SN w postaci elektroniczno-elektromechanicznego układu o architekturze warstwy wejściowej i warstwy wyjściowej.

 W latach 1952-1962 powstaje projekt Arthura Samuela z IBM, polegający na szkoleniu modelu na zawodnikach szachowych. W 1960 roku Widrow i Hoffp przedstawiają tzw. Madaline. Był to pierwszy neurokomputer oferowany komercyjnie do przetwarzania sygnałów, np. w radarach, sonarach, modemach i liniach telefonicznych. W 1965 powstaje system ekspercki Dendral na Uniwersytecie Stanforda, który zajmuje się automatyzowaniem analizą i identyfikacją molekuł związków organicznych dotychczas nieznanych chemikom. W 1969 Minsky i Papert publikują książkę Perceptrons, która przedstawiała formalny dowód, że sieci jednowarstwowe mają bardzo ograniczony zakres zastosowań.

W 1974 Werbos przedstawia wstępne zasady nowego schematu uczenia sieci warstwowej.
W 1977 roku Anderson z Uniwersytetu Browna przedstawia sieć Brain State in Box będącą odpowiednikiem pamięci asocjacyjnej z dwustronnym dostępem, która działa nieiteracyjnym procesem poszukiwania, ale analizie zależnościach typu wejście - wyjście. W tym samym roku powstaje program AM do zautomatyzowanego poszukiwania praw matematycznych na podstawie algorytmów heurystycznych.

W latach 80 pojawiają się pierwsze sieci ze sprzężeniem zwrotnym, w którym rozwiązanie zadań polegało na poszukiwaniu przez sieć stanu równowagi w iteracyjnym procesie. W 1982 Kohonen przedstawia sieci do wydobywania cech, uczące się bez nauczyciela. W tym samym roku Hopfield przedstawia sieć odtwarzającą obrazy z ich fragmentów, a także rozwiązującą zadania optymalizacyjne – problem komiwojażera. W 1986 McClelland i Rumelhart przedstawiają monografię nt. równoległego przetwarzania rozproszonego, co otwiera erę sieci warstwowych. 

W latach 90 pojawia się program TD-Gammom, potrafiący konkurować w grze Backgammom z mistrzami świata. Program uczył się swojej strategii grając jako przeciwnik w ponad milionie gier. 
W 1997 roku Garri Kasparow, mistrz świata w szachach, został pokonany w tzw. miniaturze przez komputer Deep Blue firmy IBM. Kasparow zarzucił firmie IBM oszustwo, gdyż odmówiono mu dostępu do poprzednich gier Deep Blue. Koniec lat 90 to stosowanie algorytmów uczenia maszynowego w rozwoju internetowego i wyszukiwarek internetowych.
## Metody uczenia maszynowego
Możemy wyróżnić różne metody uczenia maszynowego, między innymi:
- **Sieci neuronowe**: Struktury matematyczne odwzorowujące przepływ informacji w mózgu człowieka do podejmowania decyzji na podstawie modelu matematycznego uczonego w kolejnych iteracjach z danych wejściowych.
- **Systemy rozmyte**: Modele matematyczne odwozrowujące sposób podejmowania decyzji przez człowieka, które dzięki swej budowie dają możliwość wyrażania decyzji „nieostrych”.
- **Maszyna wektorów wspomagających**: Model matematyczny pozwalający wyodrębnić zbiory w przestrzeni decyzji, dzięki czemu porównania są dokonywane w poszczególnych podprzestrzeniach.
- **Zbiór reguł uczących**: Zbiór reguł w postaci klauzul Hornowskich interpretowanych jako poszczególne decyzje.	
- **Drzewa decyzyjne**: Metoda graficzna wspomagania podejmowania decyzji lub pozyskiwania wiedzy. Jest to schemat o strukturze drzewa opisujący możliwe decyzje i ich konsekwencje.
- **Uczenie bayesowskie**: Metody oparte na prawdopodobieństwie warunkowym Thomasa Bayesa. Wzór Bayesa jest podstawą różnych form wnioskowania probabilistycznego.
- **Uczenie z przykładów**: W odróżnieniu od metod uczenia, które konstruują ogólny, tzw. jawny opis funkcji docelowej, uczenie tego typu po prostu zapamiętuje przykłady.
- **Uczenie przez wzmacnianie**: Metoda wyznaczania optymalnej polityki sterowania przez agenta w nieznanym mu środowisku na podstawie interakcji z tym środowiskiem.
## Zastosowania AI
Sztuczna inteligencja jest powszechnie wykorzystywana we wszystkich dziedzinach nauki. W technice stosuje się ją do rozpoznawania kontekstowego, klasyfikacji oraz analizy obrazów, przetwarzania sygnałów oraz przy robotyce, automatyce i teorii sterowania. Aby sklasyfikować i rozpoznawać wzorce, sieć uczy się podstawowych cech: odwzorowywania geometrycznego, pikselowego układu wzorca, rozkładu składników wzorca, składników transformacji Fouriera czy innych właściwości zależnych od typu wzorca.

W medycynie stosuje się AI do diagnozy schorzeń, analizy zdjęć medycznych, systemów wspomagania życia czy analizy czynników środowiskowych. W ekonomii z kolei wykorzystuje się do przewidywania rozwiązań modeli ekonomicznych, prognozowania danych, takich jak bessy i hossy na giełdzie, klasyfikacji danych bilansowych czy branży.
