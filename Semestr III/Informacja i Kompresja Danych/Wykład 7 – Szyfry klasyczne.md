## Słownik pojęć kryptograficznych
* **Kryptografia:** Dziedzina współczesnej matematyki i informatyki zajmująca się przekazywaniem informacji w sposób zabezpieczony przed niepowołanym dostępem.
* **Tekst jawny:** Tekst dostępny dla wszystkich.
* **Tekst tajny (kryptogram / szyfrogram):** Informacja w postaci niezrozumiałej dla osób nieupoważnionych.
* **Szyfrowanie / Deszyfrowanie:** Procesy przekształcania tekstu jawnego w tajny i odwrotnie.
* **Atak brutalny (bruteforce):** Metoda łamania szyfru wykorzystująca wszystkie matematyczne kombinacje.
## Systemy kryptograficzne
Systemem kryptograficznym nazywamy piątkę $(\mathcal{M}, \mathcal{C}, \mathcal{K}, \mathcal{E}, \mathcal{D})$, gdzie:
* $\mathcal{M}$ – przestrzeń tekstów jawnych.
* $\mathcal{C}$ – przestrzeń kryptogramów.
* $\mathcal{K}$ – przestrzeń kluczy.
* $\mathcal{E} = \{E_k : k \in \mathcal{K}\}$ – przestrzeń funkcji szyfrujących $E_k : \mathcal{M} \rightarrow \mathcal{C}$.
* $\mathcal{D} = \{D_l : l \in \mathcal{K}\}$ – przestrzeń funkcji deszyfrujących $D_l : \mathcal{C} \rightarrow \mathcal{M}$.

Dla każdego klucza szyfrującego istnieje odpowiedni klucz deszyfrujący, co oznacza, że funkcje $E_k$ oraz $D_l$ są swoimi odwrotnościami ($E_k(D_l(c)) = c$).
## Szyfry podstawieniowe
Szyfry podstawieniowe są przykładem szyfru klasycznego. Wyróżniamy cztery główne podtypy:
* **Szyfry podstawieniowe proste:** Pojedynczy symbol alfabetu jawnego kodowany jest w pojedynczy symbol tekstu tajnego.
* **Szyfry podstawieniowe homofoniczne:** Pojedynczy symbol tekstu jawnego wybierany jest ze zbiorów homofonów.
* **Szyfry podstawieniowe wieloalfabetowe:** Każdy symbol tekstu jawnego korzysta z innej metody kodowania.
* **Szyfry podstawieniowe poligramowe:** Jednocześnie szyfrowany jest blok liter o ustalonej długości $n$.
### Szyfry afiniczne
Szyfr afiniczny to rodzaj szyfru podstawieniowego prostego operujący na alfabecie $\mathbb{Z}_l$. 
* **Wzór szyfrowania:** 
$$ E_k(m) \equiv am + b \pmod l $$
  gdzie kluczem jest para $k = (a, b) \in \mathbb{Z}_l^2$ przy koniecznym warunku $\text{NWD}(a, l) = 1$.
* **Wzór deszyfrowania:**   $$ D_l(c) \equiv a^{-1}(c - b) \pmod l $$
	 - Jeżeli $a = 1$, szyfr ten nazywamy **szyfrem Vigenére'a** (stosowanym m.in. w maszynie Enigma).
	* Jeżeli $a = 1$, a zamiast $+b$ występuje $-b$, szyfr nazywany jest **szyfrem Beauforta**.
## Pozostałe szyfry klasyczne

### Szyfr Playfair
Opiera się na tabeli $5 \times 5$ zawierającej litery alfabetu łacińskiego (przyjmując $\text{J} = \text{I}$), umieszczane losowo. Komunikaty w postaci par liter koduje się na podstawie ich względnego położenia w tabeli (w tym samym wierszu, kolumnie, na skos lub – w przypadku podwojenia liter – poprzez wstawienie dodatkowego znaku).
### Szyfr ADFGVX
Wykorzystuje tabelę $6 \times 6$, której wiersze i kolumny oznaczone są literami: $\text{A, D, F, G, V, X}$. Wewnątrz tabeli losowo umieszcza się litery alfabetu oraz wybrane symbole, a każdą literę komunikatu koduje się parą współrzędnych (wiersz i kolumna).