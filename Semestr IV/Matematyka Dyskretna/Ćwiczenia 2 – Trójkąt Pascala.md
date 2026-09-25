## Trójkąt Pascala
Przy obliczaniu kolejnych wyrazów rozwinięcia wzoru $(x+y)^n$ możemy skorzystać z tzw. Trójkąta Pascala. Trójkąt ten tworzymy wpisując na jego szczycie jedynkę $1$, następnie w drugim wierszu wpisujemy dwa elementy, będące sumą dwóch powyżej $0+1=1$ oraz $1+0=1$, dla kolejnych wierszy kontynuujemy konstrukcję, za każdym razem dodając jeden element.

Jako wynik powyższego algorytmu dostaniemy Trójkąt Pascala, nazwany tak na cześć francuskiego matematyka Blaise'a Pascala.

## Zasada plastra miodu
Jedną z ciekawszych cech Trójkąta Pascala jest tzw. zasada plastra miodu. Na początku wybieramy dowolną liczbę z trójkąta Pascala, będzie ona centrum naszego plastra miodu. Następnie każdą z sześciu otaczających ją liczb otaczamy pięciokątem.

Zasada plastra miodu, mówi że iloczyn trzech niestykających się elementów plastra miodu jest równy iloczynowi trzech pozostałych. W ujęciu matematycznym zasadę plastra miodu możemy zapisać jako:

$$\binom{n-1}{k-1}\binom{n}{k+1}\binom{n+1}{k}=\binom{n-1}{k}\binom{n}{k+1}\binom{n+1}{k+1}$$

## Zasada kija hokejowego
Kolejną ciekawą zależną jest tzw. zasada kija hokejowego. Mówi ona nam o tym, że suma elementów na dowolnej przekątnej do pewnego momentu jest równa elementowi po przeciwnej stronie. Matematycznie zasadę tą możemy zdefiniować następująco:

$$\sum_{i=r}^n \binom{n}{r}=\binom{n+1}{r+1}$$

