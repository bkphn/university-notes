## Wykorzystane biblioteki
Podczas laboratorium wykorzystujemy trzy podstawowe biblioteki:

- **NumPy (`numpy`)** – umożliwia reprezentowanie stanów kwantowych jako wektorów amplitud zespolonych, ich normalizację oraz obliczanie prawdopodobieństw pomiaru.
- **Matplotlib (`matplotlib.pyplot`)** – pozwala wizualizować wyniki symulowanych pomiarów kwantowych, np. za pomocą histogramów.
- **Qiskit (`qiskit.quantum_info`)** – biblioteka przeznaczona do obliczeń kwantowych. Udostępnia m.in. klasę `Statevector`, pozwalającą reprezentować stany kwantowe i symulować ich pomiary.

``` python
import numpy as np
import matplotlib.pyplot as plt
from qiskit.quantum_info import Statevector
```

## Reprezentacja stanów kwantowych za pomocą NumPy
Biblioteka **NumPy** pozwala reprezentować stan kubitu jako dwuelementową tablicę liczb zespolonych, której elementy odpowiadają amplitudom stanów $\ket{0}$ i $\ket{1}$.

``` python
psi = np.array([np.sqrt(3)/2, 1j/2], dtype=complex)
```

Do wykonywania operacji na stanie kwantowym możemy wykorzystać polecenia:
- `np.abs(psi)**2` – oblicza prawdopodobieństwa pomiaru zgodnie z regułą Borna.
- `np.vdot(psi, psi).real` – oblicza kwadrat normy stanu, pozwalając sprawdzić jego normalizację.
- `psi / np.linalg.norm(psi)` – normalizuje niezerowy wektor amplitud.
- `np.exp(1j * np.pi / 3)` – pozwala reprezentować amplitudę o określonej fazie.

## Symulacja pomiarów za pomocą NumPy Random
Moduł **`numpy.random`** pozwala symulować pomiary kwantowe poprzez losowanie wyników zgodnie z prawdopodobieństwami wynikającymi z reguły Borna.

``` python
psi = np.array([np.sqrt(3)/2, 1j/2], dtype=complex)p = np.abs(psi)**2rng = np.random.default_rng(42)wyniki = rng.choice([0, 1], size=1000, p=p)
```

Najważniejsze parametry `rng.choice()` w tym zastosowaniu:
- `[0, 1]` – możliwe wyniki pomiaru kubitu w bazie obliczeniowej.
- `size=1000` – liczba symulowanych pomiarów (ang. *shots*).
- `p=p` – rozkład prawdopodobieństwa wyznaczony przez regułę Borna.

`numpy.random` symuluje statystykę wyników pomiarów, ale nie odwzorowuje automatycznie zmiany stanu kwantowego po pomiarze.

## Reprezentacja stanu kwantowego za pomocą biblioteki Statevector
Klasa `Statevector` z biblioteki `qiskit.quantum_info` służy do reprezentowania **czystego stanu kwantowego** za pomocą wektora amplitud zespolonych.

``` python
from qiskit.quantum_info import Statevector
```

Utworzenie stanu pojedynczego kubitu:

``` python
psi = Statevector([np.sqrt(3)/2, 1j/2])
```

Metoda `.probabilities_dict()` zwraca **prawdopodobieństwa uzyskania poszczególnych wyników pomiaru** w bazie obliczeniowej w postaci słownika.

``` python
psi.probabilities_dict()

# Out: {'0': 0.75, '1': 0.25}
```

Metoda `.is_valid()` sprawdza, czy wektor amplitud reprezentuje **poprawnie znormalizowany stan kwantowy**.

``` python
psi.is_valid()

# Out: True 
```

Metoda `.probabilities()` zwraca **prawdopodobieństwa pomiaru w bazie obliczeniowej** w postaci tablicy NumPy.

``` python
psi.probabilities()

# Out: array([0.75, 0.25])
```

Metoda `.sample_counts()` symuluje wielokrotny pomiar stanu kwantowego i zwraca **liczbę wystąpień poszczególnych wyników**.

Parametr `shots` określa liczbę powtórzeń pomiaru.

``` python
psi.sample_counts(shots=1000)
# Out: {'0': 753, '1': 247}
```

Metoda `.sample_memory()` symuluje wielokrotne pomiary, zwracając **wyniki poszczególnych prób**, zamiast ich zagregowanych liczebności.

``` python
psi.sample_memory(shots=5)

# Out: array(['0', '0', '1', '0', '1'])
```

Metoda `.seed()` ustawia ziarno generatora liczb pseudolosowych wykorzystywanego przez metody symulujące pomiary.

``` python
psi.seed(42)psi.sample_counts(shots=1000)
```

Pozwala odtwarzać wyniki losowania w tym samym środowisku.