| Rodzaj     | Nazwa              |
| ---------- | ------------------ |
| Prowadzący | dr inż. Mert Nakıp |
| Sala       | CEK Aula C         |

| Nazwa programu | Link                       |
| -------------- | -------------------------- |
| mertnakip.com  | https://www.mertnakip.com/ |

## Egzamin
- Egzamin odbędzie się w okolicach **10 tygodnia**. Obejmować będzie wszystkie tematy, które do tego momentu pojawią się na wykładach.
- Na egzaminie nie można używać urządzeń elektrocznicznych, notatek, ani podręczników. W razie potrzeby można skorzystać z kalkulatora.
- Egzamin należy pisać ołówkiem, a nie długopisem.

## Projekt
- Grupy powinny być maksymalnie trzyosobowe.
- Projekt może być z ścieżki **commercial** bądź **research**.
- Musi implementować jedną z wymienionych niżej metodyk.
- Należy pracować na prywatnym repozytorium Github, na koniec zajęć będziemy rozmawiać o zmienieniu ich na repozytoria publiczne.
- Należy zweryfikować swoje podejście w realistycznych scenariuszach.
- Trzeba przestrzegać standardów inżynieryjnych tam.
- Należy wyraźnie przedstawić wkład poszczególnych członków grupy.

### Prezentacje
- **Tydzień 4 (maksymalnie 10 min, wliczając Q&A):** Prezentacja dotycząca problemu, pomysłu i planowania projektu. Powinniście przygotować definicję problemu, analizę rynku/literatury, zarys struktury pomysłu oraz plan projektu wykorzystujący wykres Gantta i przewidywane ryzyka.
- **Tydzień 8 (maksymalnie 15 min, wliczając Q&A):** Odbędzie się Wasza prezentacja śródsemestralna (ang. *midterm*). Musi ona obejmować szczegóły techniczne, dotychczasowe postępy, wyniki, obserwacje oraz ryzyka.
- **Tydzień 15 (maksymalnie 15 min + 5 min na demo, wliczając Q&A):** Będzie to prezentacja Waszego końcowego produktu w wersji MVP (Minimum Viable Product – produkt o minimalnej koniecznej funkcjonalności) lub prezentacja artykułu na sympozjum.

### Metodyka
Należy uwzględnić w swoim projekcie co najmniej jedną z poniższych metod:
#### 1. Modele bazowe (Foundation Models) i oszczędne pod względem parametrów dostrajanie (Parameter-Efficient Fine-Tuning - PEFT)
- **Opis:** Dostrajanie otwartych modeli bazowych w dziedzinach przetwarzania tekstu, obrazu, dźwięku, szeregów czasowych lub w domenach multimodalnych.
- **Przykładowe techniki:** LoRA, QLoRA, Prefix Tuning, Adaptery lub bezpośrednia optymalizacja preferencji (Direct Preference Optimization - DPO / RLHF).

#### 2. Edge AI, optymalizacja i wdrażanie
- **Opis:** Wdrażanie zoptymalizowanych modeli głębokiego uczenia na sprzęcie o ograniczonych zasobach lub systemach wbudowanych (np. NVIDIA Jetson, Raspberry Pi, urządzenia mobilne lub mikrokontrolery).
- **Przykładowe techniki:** Klasteryzacja, przycinanie sieci (ang. *pruning*), kwantyzacja (INT8/INT4, AWQ, GPTQ), przycinanie strukturalne/niestrukturalne, destylacja wiedzy (ang. *knowledge distillation*), ONNX Runtime, TensorRT lub TFLite wraz z konkretnym profilowaniem opóźnień (ang. *latency*), przepustowości (ang. *throughput*) i zużycia energii.

#### 3. Uczenie federacyjne (Federated Learning) i uczenie maszynowe chroniące prywatność
- **Opis:** Trenowanie rozproszonych modeli na zdecentralizowanych danych bez scentralizowanego dostępu.
- **Przykładowe techniki:** Prywatność różnicowa (Differential Privacy - DP-SGD), bezpieczne obliczenia wielostronne (Secure Multi-Party Computation - SMPC) lub szyfrowanie homomorficzne w przepływach pracy uczenia maszynowego.

#### 4. Przepływy pracy oparte na agentach (Agentic Workflows)
- **Opis:** Projektowanie autonomicznych systemów wieloagentowych z możliwościami wywoływania narzędzi, planowania i zarządzania pamięcią.
- **Przykładowe techniki:** Google ADK, GraphRAG, hybrydowe wyszukiwanie wektorowe/słowami kluczowymi, podejścia typu supermemory, destylacja wiedzy i kompresja kontekstu dla złożonych aplikacji domenowych.

#### 5. Modelowanie generatywne i architektury dyfuzyjne
- **Opis:** Tworzenie warunkowych modeli generatywnych do generacji danych syntetycznych, translacji między domenami lub tworzenia treści multimodalnych.
- **Przykładowe techniki:** Modele dyfuzji ukrytej (Latent Diffusion Models - LDMs), ControlNet, Flow Matching lub warianty VAE/GAN do specjalistycznych zadań związanych z obrazem, modelami 3D, dźwiękiem lub danymi tabelarycznymi.

#### 6. Samonadzorowane (Self-Supervised), internetowe samonadzorowane i multimodalne uczenie się reprezentacji
- **Opis:** Trenowanie lub adaptacja samouczących się modeli reprezentacji na nieetykietowanych danych domenowych.
- **Przykładowe techniki:** Uczenie kontrastowe (np. CLIP, SimCLR), zamaskowane autokodery (Masked Autoencoders - MAE) lub wyrównywanie między modalnościami (ang. *cross-modal alignment*) w strumieniach danych z czujników, obrazu i tekstu.

#### 7. Wyjaśnialna sztuczna inteligencja (XAI), bezpieczeństwo i odporność
- **Opis:** Projektowanie modeli z surowymi wymaganiami dotyczącymi interpretowalności lub bezpieczeństwa.
- **Przykładowe techniki:** Interpretowalność mechanistyczna, atrybucja cech (SHAP, LIME, Integrated Gradients), ewaluacje ataków/obrony adwersaryjnej, mechanizmy zabezpieczające (ang. *guardrailing*) lub ramy red-teamingu.

#### 8. Grafowe sieci neuronowe (GNNs) i uczenie maszynowe inspirowane fizyką (Physics-Informed ML)
- **Opis:** Zastosowanie specjalistycznych architektur do struktur nieeuklidesowych lub układów fizycznych.
- **Przykładowe techniki:** GNNs do przewidywania połączeń/klasyfikacji węzłów w złożonych sieciach lub sieci neuronowe inspirowane fizyką (Physics-Informed Neural Networks - PINNs) rozwiązujące równania różniczkowe w kontekstach inżynieryjnych.

#### 9. Adwersaryjna sztuczna inteligencja (Adversarial AI) i odporność modeli
- **Opis:** Ocenianie i wzmacnianie systemów AI przed celowym omijaniem, manipulacją lub wykorzystywaniem podatności.
- **Przykładowe techniki:** Metoda FGSM (Fast Gradient Sign Method), PGD (Projected Gradient Descent), ataki adwersaryjne typu black-box/white-box, bezpośrednie/pośrednie wstrzykiwanie promptów (ang. *prompt injection*), ramy red-teamingu, sanityzacja danych wejściowych i trening adwersaryjny.

#### 10. Bezpieczeństwo, prywatność i integralność AI
- **Opis:** Zabezpieczanie potoków (ang. *pipelines*) uczenia maszynowego, ochrona własności intelektualnej modelu oraz zapobieganie wyciekom danych w całym cyklu życia AI.
- **Przykładowe techniki:** Obrona przed inwersją modelu (ang. *model inversion*) i wnioskowaniem o przynależności (ang. *membership inference*), wykrywanie backdoorów i trojanów, cyfrowe znaki wodne i śledzenie pochodzenia treści, oduczanie maszynowe (ang. *machine unlearning*), dynamiczne maskowanie danych osobowych (PII) oraz poufne wnioskowanie z użyciem zaufanych środowisk wykonawczych (Trusted Execution Environments - TEEs).