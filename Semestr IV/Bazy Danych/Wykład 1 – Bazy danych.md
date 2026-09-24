## Bazy danych
Baza danych to zbiór powiązanych ze sboą danych, które można w jakiś sposób zarejestrować i które mają konkretne znaczenie.

Ta definicja jest jednak zbyt ogólna, w ścisłym ujęciu należy uszczegółowić definicję. Od bazy danych oczekuje się następujących właściwości:
- opisuje jakiś wybrany aspekt świata rzeczywistego nazywanym mini-światem bądź **dziedziną problemu**;
- jest logicznie spójnym zbiorem danych, tzn. spełnia ograniczenia nałożone na dane;
- jest projektowana, konstruowana i wypełniana danymi w określonym celu,
- do bazy danych powinna być przypisana grupa użytkowników.
## System zarządzania bazą danych
System zarządzania bazą danych, w skrócie DBMS (ang. *Database Management System*) jest zbiorem programów organizujących dane w bazie. Wśród najpopularniejszych DBMS można wyróżnić:
- Oracle Database,
- MySQL,
- Access,
- PostgreSQL,
- MongoDB,
- Redis.

Bazy danych odgrywają kluczową rolę w życiu codziennym współczesnego społeczeństwa. Bazy danych są stosowane między innymi w: systemach bankowych, obsługach hoteli, katalogach bibliotecznych, sklepach internetowych, marketach.
## Historia baz danych
Pierwsze profesjonalne systemy zarządzania bazami danych, pojawiły się pod koniec lat sześćdziesiątnych. Początkowo były to systemy oparte na zwykłych systemach plików. Mankamentem była trudność w szybkim dostępnie do danych oraz ryzyko ich utraty. System nie dostarczał możliwości wykonywania zapytań. Problem był również z jednoczesną pracą kilku użytkowników modyfikujące te same dane. W pierwszych systemach zarządzania bazą danych dominowały dwa modele danych: hierarchiczny i sieciowy. Systemy te nie dawały możliwości korzystania z języka zapytań wysokiego poziomu.

W 1970 roku Ted Codd wprowadził relacyjny model bazy danych. Dane reprezentowane były w postaci czytelnych dla użytkownika tabel. Wewnątrz systemu istnieje złożona struktura danych, pozwalająca błyskawicznie wykonywać różnego rodzaju zapytania. Użytkownik nie musi nic wiedzieć o wewnętrznej strukturze danych, operuje jedynie wysokopoziomowym językiem zapytań.
## Moduły baz danych
Zadaniem modułu zarządzania pamięcią jest wybieranie właściwych danych z pamięci i w razie potrzeby dostosowanie ich do wymagań modułów z wyższych poziomów. Składa się z dwóch części:
- **Moduł zarządzania plikami**: Przechowuje informacje o miejscu zapisania plików na dysku i przekazuje zawartość bloku lub bloków, gdzie zapisany jest żądany plik modułowi zarządzania buforem.
- **Moduł zarządzania buforami**: Obsługuje pamięć operacyjną, blokom przekazanym przez moduł zarządzania pamięcią przydziela obszar.

Kolejnym z modułów jest **moduł przetwarzania zapytań**. Obsługuje on nie tylko zapytania, ale również aktualizacje danych czy też metadanych. Zadaniem tego modułu jest znalezienie optymalnego sposobu wykonania zadanych operacji i wydanie poleceń do modułu zarządzania pamięcią. Najtrudniejszym zadaniem, które musi wykonać ten moduł jest optymalizacja zapytań, tak żeby czas dostępu do danych był jak najkrótszy.

Ostatnim wartym wspomnienia modułem jest **moduł zarządzania transakcjami**. Odpowiada on za spójność systemu – musi zagwarantować, że kilka jednocześnie zapytań nie będzie sobie wzajemnie przeszkadzać oraz, że żadne dane nie zostaną utracone. Poprawność przeprowadzania transakcji opisują właściowości **ACID**:
- **Niepodzielność** (ang. *Atomicity*): Transakcja zostanie wykonana w całości albo żadne jej polecenie nie zostanie uwzględnione – brak częściowego wykonania poleceń.
- **Spójność** (ang. *Consistency*): Dane muszą być przypisywane spójnie z wymogami.
- **Izolacja** (ang. *Isolation*): Dwie transakcje przeprowadzone jednocześnie nie mogą na siebie wpłynąć.
- **Trwałość** (ang. *Durability*): Jeśli transakcja zostanie zakończona to nawet w sytuacji awarii systemu wynik transakcji nie może zostać utracony.
## Wejścia
Mamy trzy wejścia do systemu zarządzania bazą danych:
- **Zapytania** Zapytaniami nazywamy pytania o dane. Można je wykonywać przez system zapytań bezpośrednich wbudowany w DBMS lub przez interfejsy programów użytkownika.
- **Aktualizacje**: Aktualizacją nazywamy operację zmiany danych w bazie danych.
- **Modyfikacje schematu**: Czynności związane ze zmianą schematu bazy danych wykonuje administrator bazy danych.
## Architektury
Większość systemów baz danych oparta jest na architekturze **klient-serwer**. Na serwerze znajduje się DBMS, do którego dostęp posiada kilku użytkowników – klientów. Po stronie klienta znajduje się aplikacja stanowiąca interfejs graficzny użytkownika, umożliwający w czytelny sposób interpretację danych zawartych w bazie.

We współczensych rozwiązaniach systemowych często do czynienia mamy z architekturą trójwarstwową – pomiędzy klientem a serwerem istnieje jeszcze jeden element, a mianowicie serwer WWW. W tego typu rozwiązaniach najczęściej interfejsem użytkownika jest strona internetowa generowana w obrębie serwera WWW.