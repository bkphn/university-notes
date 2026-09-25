## Język UML
Język UML jest zunifikowanym językiem modelowania. Diagramy klas UML pozwalają na przedstawienie struktury klasy oraz relacji zachodzących między klasami.  
  
Klasa reprezentowana jest przez prostokąt zawierający nazwę klasy, natomiast oddzielna sekcja zawiera składowe klasy: pola, własności, metody. Składowe klasy zazwyczaj opisane są poprzez podanie ich nazwy i zasięgu oraz określenie ich typu. Metody zazwyczaj bywają osobno oddzielone od pozostałych składowych klasy. Widoczność (zasięg) składowych oznaczone są znakami:
- `+` (składowa publiczna)
- `-` (składowa prywatna)
- `#` (składowa chroniona)
- `~` (składowa internal)

## Diagramy UML
Klasę `NazwaKlasy` zdefiniowaną poniżej:
```csharp
class NazwaKlasy
{
        private bool polePrywatne;
        public int Wlasnosc { get; set; } = 0;
        protected int WlasnoscChroniona { get; set; }
        public bool MetodaPubliczna() => true;
        protected void metodaChroniona() => Console.Write("UML");
}
```
możemy przedstawić za pomocą następującego diagramu:

| $\mathtt{NazwaKlasy}$                                                         |
| ----------------------------------------------------------------------------- |
| `-polePrywatne : bool`<br>`+Wlasnosc : int = 0`<br>`#WlasnoscChroniona : int` |
| `+MetodaPubliczna() : bool`<br>`#MetodaChroniona()`                           |

## Związki między klasami
Między klasami możemy wyróżnić następujące związki:
- **Zależność**: Najsłabszy związek pomiędzy dwiema klasami. Zachodzi wówczas, gdy jedna klasa „przelotnie” korzysta z obiektu innej klasy. Najczęściej z zależnością mamy do czynienia, gdy operacje jednej klasy przyjmują jako argument obiekt drugiej klasy.![[Pasted image 20260919165412.png|263]]
- **Asocjacja**: Zachodzi wówczas, gdy obiekt jednej klasy przez pewien czas korzysta z obiektów drugiej klasy. W przypadku asocjacji usunięcie jednego z obiektów nie powoduje usunięcia drugiego. ![[Pasted image 20260919165418.png|266]]
- **Agregacja częściowa**: Zachodzi wówczas, gdy obiekt jednej klasy zawiera odwołanie do obiektu innej klasy, ale oprócz tego współdzieli je z innymi obiektami. W tej relacji mamy istotnie wyróżnionego właściciela – obiekt nadrzędny i obiekt podrzędny.![[Pasted image 20260919165425.png|272]]
- **Agregacja całkowita**: Zachodzi wtedy, gdy obiekt jednej klasy w całości zawiera obiekt drugiej klasy. Obiekt części jest tworzony i zarządzany w całości przez właściciela. Obiekt ten nie może istnieć bez właściciela.![[Pasted image 20260919165433.png|284]]
- **Dziedziczenie**: Zachodzi gdy jedna klasa jest rodzaju innej klasy.![[Pasted image 20260919165443.png|283]]
- **Implementacja interfejsu**: Zachodzi gdy dana klasa implementuje dany interfejs.![[Pasted image 20260919165448.png|274]]
Przy rysowaniu zależności w diagramach UML należy pamiętać, że strzałka powinna być zwrócona w drugą stronę niż „każe intuicja”. Nie chodzi o to, że `czytelnik` jest klasą pochodną po `uzytkownik`, tylko o to, że `czytelnik` implementuje klasę `uzytkownik`.

## Krotność związków
Krotność związków określa minimalną i maksymalną liczbę obiektów, które mogą zostać powiązane w ramach danego związku. W diagramach UML używa się oznaczeń:

- `1   ` (dokładnie jeden obiekt)
- `0..1` (co najwyżej jeden obiekt)
- `0..*` (zero lub więcej obiektów)
- `1..*` (jeden lub więcej obiekt)
- `*   ` (dowolna liczba obiektów)

## Zależności
Zależność między klasami występuje wówczas, gdy jedna klasa musi posiadać informacje o drugiej klasie, aby móc skorzystać z obiektu tej klasy. Zmiana struktury jednej klasy może spowodować konieczność wprowadzenia zmian w drugiej klasie. Najczęściej z zależnością mamy do czynienia, gdy operacje jednej klasy przyjmują jako argument obiekt drugiej klasy.

## Asocjacje
Asocjacja jest związkiem silniejszym od zależności. Z asocjacją mamy do czynienia wówczas, gdy jedna klasa jest powiązana z drugą klasą przez pewien określony czas. W przypadku tego związku czas życia jednego obiektu nie zależy od drugiego. Ponadto w przypadku asocjacji usunięcie jednego z obiektów nie powoduje usunięcia drugiego.

W przypadku asocjacji jeden obiekt powiązany tą relacją z drugim obiektem posiada referencję do niego, może się do niego odwołać, ale nie tworzy go, nie zarządza nim.

## Agregacje częściowe
Silniejsza od asocjacji jest agregacja częściowa. Jest to relacja określana mianem „całość-część” przy czym, w przypadku tej relacji część może czasem wchodzić w skład wielu różnych całości. W tej relacji mamy istotnie wyróżnionego właściciela – obiekt nadrzędny i obiekt podrzędny. W przypadku agregacji częściowej, właścicieli obiektu podrzędnego jest więcej i zazwyczaj właściciele nie tworzą tych obiektów i ich nie usuwają.

## Agregacje całkowite
Silniejszą odmianą agregacji jest agregacja całkowita, nazywana również kompozycją. Jest to również relacja typu „całość-część”, ale tym razem całość jest jedynym właścicielem części, tworzy obiekt będący częścią i nim zarządza. Jest to niewątpliwie najsilniejszy rodzaj relacji łączącej klasy. Obiekt części jest tworzony i zarządzany w całości przez właściciela. Obiekt ten nie może istnieć bez właściciela. Zazwyczaj w przypadku tej relacji mówi się, że „obiekt jest częścią całości”.

## Uproszczony diagram UML
W uproszczonym diagramie UML jedynym elementem reprezentującym klasę jest jej nazwa. Pomijamy tutaj pola, metody i właściwości.
![[Pasted image 20260919165614.png|395]]

## Kompozycja
Naturalnym jest, że w wielu przypadkach tworzymy obiekty jako zbiór innych obiektów. W ten sposób wykorzystujemy istniejący już kod w tworzeniu nowych typów. O ile w przypadku dziedziczenia mieliśmy związaną z nim relację „jest”, to w przypadku kompozycji związek ten można nazwać „ma”. **Kompozycja** jest mechanizmem, który pozwala tworzyć rozbudowane systemy z mniejszych komponentów. Jeśliby zastanowić się głębiej, to właśnie w taki sposób ludzie rozwiązują problemy występujące w świecie rzeczywistym. O wiele łatwiej nam (ludziom) myśli się o czymś używając **abstrakcji**. Posługujemy się w naturalny sposób zdefiniowanymi abstrakcyjnymi „typami”, które nakreślają nam pewien zestaw konkretnych cech, składowych tego typu, dzięki czemu użycie samego słowa klucza (nazwy tego typu) jasno nam definiuje czego możemy się spodziewać. Takim eksploatowanym przez wielu autorów książek o programowaniu obiektowym przykładem jest termin *samochód*. Jedno słowo (*samochód*), kryje w sobie postać tego czego oczekujemy tzn. czterokołowego pojazdu, wyposażonego w silnik itd. Takie podejście ułatwia nam komunikację i jest naturalnym mechanizmem, na którym bazuje nasz sposób myślenia.

W podanym przykładzie samochodu w naturalny sposób mamy do czynienia z **kompozycją**. W skład dowolnego takiego konkretnego samochodu wchodzi wiele gotowych już innych **obiektów** np. silnik, układ hamulcowy, skrzynia biegów, układ kierowniczy itp. Każdy z tych obiektów również jest dużo bardziej złożonym układem, na który składa się szereg innych obiektów.

Kolejną zaletą kompozycji jest to, że możemy również pewne „części” wykorzystywać **zamiennie**, tzn. wystarczy, ze dany komponent, będzie danego typu a użyty w danym egzemplarzu konkretny obiekt nie ma znaczenia, ważne, żeby był tym czym ma być.

Kolejnymi zaletami wynikającymi z kompozycji jest możliwość projektowania i budowania systemu składającego się z **podsystemów**, dzięki czemu podsystemy wchodzące w jego skład mogą być realizowane oddzielnie i podobnie mogą być **testowane** i **konserwowane**. Aktualnie tworzone systemy informatyczne są bardzo złożone a co za tym idzie skomplikowane. Projektując je i realizując trzeba kierować się podstawową zasadą: twórz oprogramowanie, które będzie możliwie najprostsze. Żeby było to możliwe, trzeba system prawidłowo podzielić na mniejsze części.

Herbert A. Simon (laureat nagrody Nobla) przedstawił przemyślenia na temat stabilności systemów:
- Stabilne skomplikowane systemy najczęściej mają strukturę hierarchiczną. Każdy wchodzący w jej skład system składa się z prostszych, mniejszych podsystemów, a każdy z nich również składa się z jeszcze mniejszych.
- Stabilne złożone systemy można prawie całkowicie rozłożyć oznacza to, że można wyodrębnić składowe systemu i odróżnić interakcje między tymi elementami od interakcji w ich wnętrzu. W stabilnym systemie jest ”mało” powiązań pomiędzy jego elementami.
- Stabilne złożone systemy prawie zawsze składają się tylko z kilku różnych rodzajów podsystemów a te z kilku różnych rodzajów części.
- Stabilne systemy prawie zawsze powstają w wyniku ewolucji mniejszych systemów, które działały – zamiast budować system od początku lepiej rozwijać już istniejący sprawdzony.

