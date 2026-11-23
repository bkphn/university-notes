## Tiny Machine Learning
**Tiny Machine Learning** (TinyML) to dziedzina uczenia maszynowego zajmująca się wdrażaniem i wykonywaniem modeli na urządzeniach o bardzo ograniczonych zasobach obliczeniowych, takich jak mikrokontrolery (ang. *microcontrollers*) MCU.

TinyML stanowi rozwinięcie koncepcji **Edge AI**, czyli wykonywania operacji sztucznej inteligencji bezpośrednio na urządzeniach brzegowych (ang. *edge devices*), zamiast przesyłania danych do zewnętrznych serwerów.

Wykonywanie modeli bezpośrednio na urządzeniach pozwala wyeliminować część ograniczeń charakterystycznych dla przetwarzania w chmurze (ang. *cloud computing*):
- **Ultra-Low Latency**: Podejmowanie decyzji lokalnie umożliwia uzyskiwanie bardzo niskich opóźnień, nawet poniżej jednej milisekundy, co ma szczególne znaczenie w systemach krytycznych, takich jak robotyka i systemy hamowania.
- **Bandwidth & Cost**: Przetwarzanie danych na urządzeniu eliminuje konieczność ciągłego przesyłania surowych danych z czujników, ograniczając wykorzystanie sieci i koszty transmisji.
- **Privacy by Construction**: Dane wrażliwe mogą pozostawać na mikrokontrolerze, bez konieczności przekazywania ich do zewnętrznej infrastruktury.
- **Offline Autonomy**: Urządzenia mogą podejmować decyzje również w środowiskach pozbawionych stabilnego połączenia z internetem.

## Architektura TinyML
Występują trzy poziomy ograniczeń i wymagań, które należy uwzględnić podczas projektowania autonomicznych systemów TinyML:
1. **Physical Harness**: Ograniczenia fizyczne sprzętu, takie jak pamięć, moc obliczeniowa, zużycie energii i odporność na ataki.
2. **Operational Harness**: Zdolność urządzenia do adaptowania modelu do zmieniających się warunków środowiskowych i współpracy z innymi urządzeniami.
3. **Governance Harness**: Zarządzanie zasobami sprzętowymi, integralnością modelu oraz procesami uczenia i aktualizacji w całym cyklu życia urządzenia.

Celem jest przejście od statycznych modeli wykonywanych na urządzeniach brzegowych do **autonomicznej Edge AI**, która potrafi samodzielnie dostosowywać swoje działanie do środowiska i dostępnych zasobów.

## Ograniczenia fizyczne
Wykonywanie sieci neuronowych na mikrokontrolerach wymaga uwzględnienia znacznie większych ograniczeń sprzętowych niż w przypadku standardowych komputerów.

Najważniejsze ograniczenia obejmują:
- **Memory Wall**: Mikrokontrolery mogą dysponować jedynie 16–256 KB pamięci SRAM na aktywacje modelu oraz mniej niż 1 MB pamięci Flash do przechowywania wag.
- **Compute Limits**: Urządzenia o częstotliwościach 80–240 MHz często obsługują jedynie ograniczony zestaw operacji, w szczególności arytmetykę całkowitoliczbową.
- **Energy & Radio Tax**: Transmisja bezprzewodowa może zużywać znacznie więcej energii niż wykonywanie obliczeń lokalnych.
- **Real-World Drift**: Zmiany warunków środowiskowych w czasie powodują pogorszenie skuteczności modeli wytrenowanych wcześniej na statycznych zbiorach danych.

Ograniczenia te sprawiają, że klasyczne modele głębokiego uczenia często wymagają kompresji, uproszczenia architektury lub zastosowania specjalistycznych metod uczenia.

## Mikroskopijne rekurencyjne sieci neuronowe
**Distributed Recurrent Trend Predictive Neural Network** (dTPNN) to architektura niewielkiej rekurencyjnej sieci neuronowej przeznaczonej do przewidywania trendów w danych pochodzących z czujników.

Architekturę przetestowano w systemie Smart Home IoT, składającym się z urządzeń:
- FireBeetle ESP8266.
- FireBeetle 2 ESP32-E.
- XIAO ESP32-C3.
- Raspberry Pi 5 pełniącego funkcję bramki MQTT.

**Message Queuing Telemetry Transport** (MQTT) to lekki protokół komunikacyjny oparty na modelu publikowania i subskrybowania wiadomości (ang. *publish-subscribe*), stosowany między innymi w systemach Internetu Rzeczy (IoT).

Model dTPNN wykorzystuje jedynie **8 parametrów** i przeprowadza aktualizację wag za pośrednictwem komunikacji MQTT co 16 próbek.

W eksperymencie porównano jakość predykcji modelu dTPNN z klasycznym perceptronem wielowarstwowym (ang. *Multilayer Perceptron*) MLP.

Wyniki przedstawiono za pomocą **Symmetric Mean Absolute Percentage Error** (SMAPE), czyli symetrycznego średniego bezwzględnego błędu procentowego.

Dla temperatury:
- dTPNN: 2,79% SMAPE.
- MLP: 12,77% SMAPE.
- Regresja liniowa: 39,00% SMAPE.

Dla wilgotności:
- dTPNN: 1,55% SMAPE.
- MLP: 5,26% SMAPE.
- Regresja liniowa: 12,31% SMAPE.

Wyniki wskazują, że w badanym scenariuszu niewielka rekurencyjna sieć neuronowa uzyskała lepszą skuteczność przewidywania trendów niż większe modele bazowe.

## Zużycie energii
Jednym z najważniejszych problemów TinyML jest zarządzanie energią urządzeń zasilanych bateryjnie.

Wykazano, że koszt energetyczny wykonywania bardzo małych modeli może być pomijalny w porównaniu z kosztem komunikacji bezprzewodowej.

W eksperymencie porównano dwa typy urządzeń:
- **Dummy Device**: Urządzenie wykonujące transmisję danych bez wykorzystywania modelu ML.
- **Smart Device**: Urządzenie wykonujące predykcje za pomocą dTPNN.

Przy komunikacji okresowej co 15 minut czas pracy na baterii wynosił odpowiednio:
- Dummy Device: 46 godzin i 33 minuty.
- Smart Device: 46 godzin i 34 minuty.

Oznacza to, że w przedstawionym eksperymencie wykonywanie dodatkowych obliczeń ML praktycznie nie wpłynęło na czas pracy urządzenia.

Zaobserwowano również zjawisko określone jako **Deep-Wake Trap**.

Polega ono na tym, że częste wybudzanie urządzenia i ponowne nawiązywanie połączenia Wi-Fi/MQTT może wymagać więcej energii niż utrzymywanie aktywnego połączenia.

W jednym z eksperymentów utrzymywanie stałego połączenia wydłużyło czas pracy czujnika ESP8266 z 16 godzin i 11 minut do 62 godzin i 20 minut.

Wyniki te wskazują, że **optymalizacja komunikacji może mieć większe znaczenie dla efektywności energetycznej niż dalsza optymalizacja obliczeń modelu**.

## Bezpieczeństwo TinyML
Modele działające na urządzeniach brzegowych są narażone zarówno na ataki dotyczące samej sieci neuronowej, jak i na ataki związane z infrastrukturą komunikacyjną.

**Parameter Injection** to atak polegający na nieautoryzowanej modyfikacji parametrów wyuczalnych modelu, co prowadzi do pogorszenia jego skuteczności.

W eksperymencie przeprowadzono atak poprzez dodanie szumu gaussowskiego (ang. *Gaussian Noise*) do parametrów modelu.

Wyniki:
- Temperatura: wzrost SMAPE z 9,55% do 78,43%.
- Wilgotność: wzrost SMAPE z 11,25% do 84,95%.

Pokazuje to, że nawet niewielkie modele mogą być bardzo podatne na manipulację parametrami.

**Denial of Service** (DoS) to atak polegający na zakłóceniu dostępności systemu poprzez przeciążenie jego zasobów.

W przypadku urządzeń TinyML atak może polegać na wysyłaniu bardzo dużej liczby wiadomości przez protokoły komunikacyjne.

W badanym systemie ciągłe zalewanie sieci wiadomościami MQTT prowadziło do 100% utraty pakietów w urządzeniach wykorzystujących Wi-Fi.

Jednocześnie urządzenia korzystające z okresowego wybudzania i komunikacji zachowały zdolność działania.

Wyniki wskazują, że optymalizacje energetyczne oraz komunikacyjne mogą również wpływać na bezpieczeństwo i odporność systemu.

## Adaptacja modeli do zmiennego środowiska
Tradycyjne modele uczenia maszynowego są zazwyczaj trenowane na wcześniej zgromadzonych danych, a następnie wdrażane na urządzeniach.

Takie podejście może prowadzić do problemu **Data Drift**, czyli zmiany rozkładu danych wejściowych w czasie.

W systemach IoT warunki środowiskowe oraz charakterystyka ruchu sieciowego mogą zmieniać się dynamicznie, powodując stopniowe pogorszenie jakości predykcji.

Wśród najważniejszych podejść do aktualizacji modeli możemy wyróżnić:
- **Offline Learning**: Model trenowany jest przed wdrożeniem. Brak aktualizacji może prowadzić do jego dezaktualizacji.
- **Naive Periodic Updates**: Model jest aktualizowany w stałych odstępach czasu. Takie podejście może powodować niepotrzebne obciążenie urządzenia albo zbyt późną reakcję na zmianę środowiska.
- **Trust-Gated Self-Supervision**: Aktualizacja następuje wtedy, gdy miara statystycznej wiarygodności modelu spadnie poniżej określonego progu.

Ostatnie podejście pozwala urządzeniom samodzielnie decydować o konieczności uczenia, bez konieczności stałego nadzoru człowieka.

## Self-Supervised Intrusion Detection
**Self-Supervised Intrusion Detection** (SSID) to metoda samonadzorowanego wykrywania włamań, która umożliwia uczenie modelu bez wcześniej przygotowanego zbioru treningowego.

System wykorzystuje mechanizm **Auto-Associative Memory** (AAM), którego zadaniem jest odtwarzanie charakterystycznych parametrów normalnego ruchu sieciowego.

AAM uczy się rekonstruować wektor cech pakietu:

$$\hat{\mathbf{x}}=f_{\theta}(\mathbf{x})$$

gdzie:
- $\mathbf{x}$ – wektor cech obserwowanego pakietu.
- $\hat{\mathbf{x}}$ – rekonstrukcja wektora wejściowego.
- $\theta$ – parametry wyuczalne modelu.

Różnica pomiędzy rzeczywistymi a odtworzonymi wartościami pozwala wykrywać anomalie.

System wykorzystuje trzy mechanizmy:
1. **Auto-Associative Memory**: Rekonstrukcja charakterystycznych cech pakietów, takich jak metryki nagłówków sieciowych.
2. **Self-Supervised Labeling**: Automatyczne przypisywanie etykiet próbkom przy wykorzystaniu predykcji modelu i statystycznej miary wiarygodności.
3. **Trust-Gated Updating**: Aktualizacja modelu jedynie wtedy, gdy zgromadzone informacje wskazują na konieczność dostosowania jego parametrów.

Istotną cechą SSID jest możliwość rozpoczęcia działania przy wykorzystaniu pojedynczego pakietu reprezentującego prawidłowy ruch sieciowy.

Oznacza to brak konieczności wcześniejszego przygotowania dużego zbioru uczącego.

## Trust Coefficient
**Trust Coefficient** to współczynnik określający statystyczną wiarygodność aktualnego modelu. Jego wartość jest wyznaczana na podstawie dwóch składników:

$$\Gamma=c_{\mathrm{rep}}\cdot c_{\mathrm{gen}}$$

gdzie:
- $c_{\mathrm{rep}}$ – składnik związany z reprezentatywnością danych.
- $c_{\mathrm{gen}}$ – składnik związany ze zdolnością generalizacji modelu.

Aktualizacja modelu jest uruchamiana, gdy współczynnik wiarygodności spadnie poniżej ustalonego progu:

$$\Gamma<\theta$$

W eksperymencie przyjęto:

$$\theta=0.95$$

Jednym z mechanizmów wykrywania zmian w danych jest **Kullback-Leibler Divergence** (KL-divergence), czyli dywergencja Kullbacka-Leiblera.

Dla dwóch dyskretnych rozkładów prawdopodobieństwa $P$ i $Q$ definiuje się ją następująco:

$$D_{\mathrm{KL}}(P\mid Q)=\sum_x P(x)\log\frac{P(x)}{Q(x)}$$

Miara ta pozwala określić stopień rozbieżności między rozkładami, np. pomiędzy wcześniejszym a aktualnym ruchem sieciowym.

### Wyniki eksperymentów
W prezentacji porównano podejście SSID z klasycznym uczeniem offline oraz uczeniem przyrostowym.

W zadaniu wykrywania złośliwego ruchu sieciowego w zbiorze Kitsune uzyskano:
- Accuracy: 99,80%.
- True Negative Rate (TNR): 99,94%.
- TNR dla uczenia przyrostowego: 98,19%.

W eksperymentach dotyczących identyfikowania zainfekowanych urządzeń IoT uzyskano również poprawę mediany balanced accuracy:
- DDoS TCP: wzrost z 73% do 91%.
- DDoS UDP: wzrost z 82% do 93%.

Wyniki sugerują, że automatyczna adaptacja modelu do lokalnego ruchu sieciowego może poprawiać skuteczność wykrywania zagrożeń.

## Resource-Aware Federated Learning
**Federated Learning** (FL), czyli uczenie federacyjne, to metoda trenowania modeli na wielu zdecentralizowanych urządzeniach, bez konieczności przesyłania ich surowych danych treningowych na centralny serwer.

Urządzenia lokalnie aktualizują parametry modeli, a następnie przekazują informacje potrzebne do ich agregacji.

W środowisku TinyML standardowe uczenie federacyjne może prowadzić do nadmiernego wykorzystania pamięci, procesora, energii i sieci.

Aby ograniczyć te problemy, w prezentacji zaproponowano mechanizm **QoS-Aware Federated Learning** (FedQoS), uwzględniający jakość usług (ang. *Quality of Service*) oraz dostępne zasoby urządzenia.

Pierwsza bramka **Resource-Aware Training Gate** kontroluje możliwość przeprowadzenia lokalnego treningu. Aktualizacja parametrów modelu następuje tylko wtedy, gdy:
- Zgromadzono wystarczającą ilość danych treningowych.
- Dostępny poziom energii przekracza ustalony próg bezpieczeństwa.

Pozwala to uniknąć sytuacji, w której uczenie modelu doprowadza do wyczerpania baterii lub ograniczenia działania podstawowych funkcji urządzenia.

Druga bramka **QoS Transmission Gate** odpowiada za decyzję o przesłaniu aktualizacji modelu do serwera.

Transmisja następuje jedynie wtedy, gdy korzyść wynikająca z aktualizacji przewyższa jej koszt energetyczny i komunikacyjny.

W prezentacji zastosowano warunek:

$$Z_i^t \geq \delta$$

gdzie $Z_i^t$ reprezentuje miarę opłacalności aktualizacji modelu.

## Wyniki eksperymentów
W badanym scenariuszu związanym z urządzeniami ubieralnymi (ang. _wearables_) oraz systemami pokładowymi pojazdów uzyskano:
- Redukcję liczby operacji FLOP nawet o 78,6%. 
- Zmniejszenie zużycia energii i odpowiadających mu emisji $\mathrm{CO}_{2}$ o około 69%.
- Redukcję przesyłanych danych o 63,9–76,7%.
- Dokładność rozpoznawania na poziomie 95–97%.

Oznacza to, że adaptacyjne zarządzanie procesami uczenia i komunikacji pozwala znacząco ograniczyć wykorzystanie zasobów przy zachowaniu wysokiej skuteczności modeli.

## Kompresja sieci neuronowych
**Model Compression**, czyli kompresja modelu, to zbiór technik służących do zmniejszenia pamięci i zasobów obliczeniowych wymaganych do wykonywania sieci neuronowej.

W kontekście TinyML kompresja pozwala uruchamiać modele na mikrokontrolerach o ograniczonej pamięci SRAM i Flash.

W prezentacji omówiono dwie techniki:
- **Pruning**: Usuwanie mniej istotnych parametrów lub połączeń sieci neuronowej.
- **Clustering**: Grupowanie parametrów o podobnych wartościach i reprezentowanie ich za pomocą wspólnych wartości.

W praktyce obie metody umożliwiają ograniczenie rozmiaru modelu, jednak mogą prowadzić do pogorszenia jego skuteczności.

W procesie kompresji należy więc uwzględnić ograniczenia dotyczące:
- Maksymalnego rozmiaru modelu.
- Dostępnej pamięci RAM.
- Opóźnienia wnioskowania (ang. _inference latency_).
- Minimalnej akceptowalnej dokładności.

## Agentic Model Compression
**Agentic Model Compression** to przedstawione w prezentacji podejście wykorzystujące model językowy do automatycznego projektowania strategii kompresji sieci neuronowej.

Zamiast przeszukiwać wszystkie możliwe konfiguracje kompresji metodą brute-force, system wykorzystuje LLM do proponowania parametrów optymalizacji.

Proces obejmuje:
1. **Weight Distribution Profiling**: Analizę rozkładu wag w poszczególnych warstwach modelu.
2. **Strategy Synthesis**: Wygenerowanie strategii kompresji, obejmującej m.in. pruning i clustering.
3. **Model Optimization**: Zastosowanie wybranych technik kompresji.
4. **Evaluation**: Weryfikację dokładności, rozmiaru i opóźnienia modelu.
5. **Iterative Optimization**: Powtarzanie procesu do osiągnięcia założonych ograniczeń sprzętowych lub wykorzystania dostępnego budżetu iteracji.

W przedstawionym podejściu model językowy uwzględnia preferencje użytkownika i ograniczenia sprzętowe jako warunki optymalizacji.

W eksperymencie uzyskano redukcję rozmiaru modeli o 72–92%, przy zachowaniu wartości AUC-PR.

Dodatkowo:
- Opóźnienie wnioskowania modeli MLP/CNN zmniejszono o około 50%.
- Rozmiar danych przesyłanych podczas aktualizacji OTA zmniejszono o 70–90%.
- Przykładowy rozmiar transferu zmniejszono ze 134 KB do 3,5 KB.

**Over-the-Air Updates** (OTA) to mechanizm zdalnego aktualizowania oprogramowania lub parametrów modeli urządzenia za pośrednictwem komunikacji bezprzewodowej.

W prezentacji wskazano również, że pojedyncza operacja kompresji wykonywana z pomocą LLM kosztowała około 4–498 dolarów, przy czym odpowiadająca jej deklarowana emisja CO₂ była mniejsza niż 0,1 grama.

## Weight Distribution Profiling
Rozkład wag sieci neuronowej może zawierać informacje przydatne podczas projektowania strategii kompresji.

W prezentacji zwrócono szczególną uwagę na **kurtozę** (ang. _kurtosis_), czyli statystyczną miarę kształtu rozkładu.

Dla zmiennej losowej $\xi$ o średniej $m$ i odchyleniu standardowym $\sigma$ kurtozę można zdefiniować jako:

$$\gamma_{3}=\frac{\mathbb{E}[(\xi-m)^4]}{\sigma^4}$$

Kurtoza jest związana z koncentracją rozkładu i znaczeniem wartości skrajnych.

W eksperymencie wykazano silną korelację między kurtozą rozkładu wag a degradacją skuteczności modelu podczas kompresji.

Współczynniki korelacji wynosiły:
- Clustering: $\rho=+0.88$.
- Pruning: $\rho=+0.64$.

Oznacza to, że rozkład wag może pomagać przewidywać, w jakim stopniu zastosowanie określonych metod kompresji wpłynie na skuteczność modelu.

Wyniki te stanowią podstawę do projektowania strategii kompresji zależnych od statystycznych właściwości poszczególnych warstw.

## Runtime Governance
**Runtime Governance** to zarządzanie zachowaniem systemu AI w czasie jego rzeczywistego działania.

W tradycyjnych systemach TinyML model jest zwykle trenowany, kompresowany i wdrażany na urządzeniu, po czym wykonuje predykcje bez większych zmian.

Takie podejście określa się jako *fire-and-forget deployment*.

W systemach autonomicznych konieczne staje się ciągłe monitorowanie warunków pracy i podejmowanie decyzji o wykorzystaniu zasobów.

Docelowa architektura obejmuje trzy elementy:

1. **Dynamic Environment**: Zmieniające się środowisko, z którego urządzenie otrzymuje dane.
2. **Runtime Resource Monitor**: Monitorowanie bieżącego zużycia pamięci, procesora oraz baterii.
3. **Self-Adapting TinyML**: Model, który samodzielnie dostosowuje swoje działanie do zmian środowiskowych i ograniczeń sprzętowych.

Problemem pozostaje zapewnienie, że procesy adaptacyjne nie zakłócą podstawowych funkcji urządzenia.

W prezentacji wskazano dwa otwarte problemy badawcze:
- Jak modelować w czasie rzeczywistym zużycie energii przez proces uczenia online bezpośrednio na mikrokontrolerach?
- Jak dynamicznie wyznaczać ograniczenia czasowe operacji, aby aktualizacje modelu nie blokowały zadań związanych z pomiarami i sterowaniem?

## ReSAF-TinyML
**ReSAF-TinyML** to koncepcja badawcza mająca na celu stworzenie autonomicznych systemów TinyML, które potrafią adaptować swoje modele bez zakłócania podstawowych zadań urządzenia.

Koncepcja opiera się na trzech filarach:
1. **Energy & Delay Modeling**: Modelowanie zużycia energii i opóźnień za pomocą modeli kolejkowych i dyfuzyjnych, wspieranych rzeczywistymi pomiarami sprzętowymi. Celem jest przewidywanie zużycia baterii oraz kosztów wykonywania operacji uczenia i wnioskowania.
2. **Adaptive Operational Scheduling**: Dynamiczne planowanie procesów wnioskowania i uczenia samonadzorowanego. Częstotliwość aktualizacji modelu ma być dostosowywana do:
	- Dostępnej mocy obliczeniowej.
	- Wolnej pamięci RAM.
	- Pozostałego poziomu energii.
	- Aktualnego obciążenia systemu.
3. **Zero-Downtime Priority**: Zapewnienie ciągłej dostępności podstawowych funkcji urządzenia. Procesy związane z uczeniem modelu nie mogą zakłócać zadań krytycznych, takich jak:
	- Monitorowanie infrastruktury przemysłowej.
	- Sterowanie systemami automatyki.
	-  Predykcyjne utrzymanie ruchu (ang. *predictive maintenance*).

Głównym założeniem ReSAF-TinyML jest więc podporządkowanie operacji uczenia i adaptacji wymaganiom niezawodności systemu.

## Podsumowanie
W prezentacji wyróżniono cztery najważniejsze kierunki rozwoju TinyML:
1. **Energy Paradox**: Bardzo małe sieci neuronowe mogą wykonywać obliczenia przy niemal pomijalnym koszcie energetycznym. Największe oszczędności można więc uzyskiwać poprzez optymalizację komunikacji.
2. **Automate Adaptation**: Mechanizmy samonadzorowanego uczenia i statystycznej oceny wiarygodności pozwalają urządzeniom samodzielnie dostosowywać modele do zmian środowiska.
3. **Gate Collaboration**: Adaptacyjne mechanizmy decyzyjne pozwalają ograniczyć liczbę zbędnych aktualizacji i transmisji, chroniąc zasoby urządzeń.
4. **Compress by Distribution**: Analiza rozkładów wag umożliwia projektowanie skuteczniejszych strategii kompresji modeli przeznaczonych do uruchamiania na mikrokontrolerach.

Docelowym kierunkiem rozwoju jest przejście od modeli wykonujących jedynie lokalne wnioskowanie do **samodzielnych, energooszczędnych i odpornych systemów Edge AI**, zdolnych do ciągłej adaptacji podczas pracy.