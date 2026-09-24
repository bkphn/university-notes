## Architektury 3-warstwowe
Architekturą 3-warstwową nazywamy klasyczny wzorzec podziału aplikacji. Oddziela UI od logiki biznesowej i danych, zmniejsza zależności między komponentami oraz ułatwia testowanie i rozwój.

Możemy wyróżnić trzy warstwy takiej architektury:
- **Presentation Layer**: Odpowiada za UI (np. WindowsForms, WPF, Web) oraz interakcja z użytkownikiem.
- **Business Logic Layer**: Odpowiada za reguły biznesowe oraz obliczenia.
- **Data Access Layer**: Odpowiada za bazę danych oraz repozytoria.
## Wzorzec MVC
Wzorzec MVC (Model-View-Controller) powstał w latach 70., został on opracowany w projekcie Smalltalk w Xerox PARC, jego głównym twórcą był norweski informatyk Trygve Reenskaug. Celem MVC od początku było oddzielenie logiki od interfejsu użytkownika oraz umożliwienie wielu widoków tych samych danych. MVC był jednym z pierwszych wzorców wspierających GUI.

W latach 90. nastąpiła największa popularyzacja wzorca w aplikacjach desktopowych, a od 2000 roku zaczęto szeroko go stosować w aplikacjach webowych. Współcześnie MVC jest podstawą wielu frameworków webowych, a on sam ewoluował w bardziej złożone wzorce:
- MVP Model-View-Presenter
- MVVM Model-View-ViewModel

Wzorzec MVC dzieli się na:
- **Model**: Model przechowuje dane aplikacji, zawiera logikę biznesową oraz jest niezależny od UI.
- **View**: Widok odpowiada za prezentację danych, wyświetla podstawowe informacje użytkownikowi.
- **Controller**: Kontroler obsługuje wejście użytkownika, interpretuje akcje oraz steruje aplikacją.
## Wzorzec MVP
Jedną z pochodnych wzorca MVC jest wzorzec MVP (Model-View-Presenter), który jest lepiej przystosowany do aplikacji desktopowych. W MVP widok emituje zdarzenia, prezenter je odbiera, następnie przetwarza dane i aktualizuje widok.

W MVP prezenter nie należy od żadnej konkretnej implementacji widoku, używa on interfejsu. Prezenter przechowuje stan aplikacji: aktualną wartość, wybraną operację czy flagę nowego wejścia.

Przy pisaniu aplikacji zgodnie ze wzorcem MVP należy uważać na najczęstsze błędy:
- umiezczanie logiki w widoku,
- bezpośredni dostęp do kontrolek w prezenterze,
- brak interfejsu widoku,
- zbyt duży prezenter;
zamiast tego:
- należy używać interfejsów,
- widok powinien tylko przekazywać zdarzenia
- prezenter nie powinien mieć dostępu do kontrolek,
- logika powinna znajdować się tylko w prezenterze.
## Wzorzec MVVM
Innym wzorcem pochodnym od wzorca MVC jest wzorzec MVVM (Model-View-ViewModel), jest to rozwinięcie MVP dostosowane do technologii z data-bindingiem. Najczęściej używany jest w WPF, UWP oraz Xamarin. Kluczową ideą MVVM jest eliminacja kodu w widoku oraz wykorzystanie mechanizmu wiązania danych. Warstwa ViewModel zastępuje Presenter i udostępnia dane dla View.

**Data Binding** odpowiada za automatyczne powiązanie warstw View i ViewModel. Brak tutaj ręcznego aktualizowania UI. Możemy wyróżnić trzy typy bindingu:
- OneWay,
- TwoWay,
- OneTime.

W MVVM zamiast eventów używa się komend, co pozwala na oddzielenie logiki od UI.