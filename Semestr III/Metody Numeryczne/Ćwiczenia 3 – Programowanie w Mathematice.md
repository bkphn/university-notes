## Programowanie w Mathematice
W programie Wolfram Mathematica mamy możliwość pracowania na zmiennych, definiowania własnych funkcji oraz korzystania z elementów języka programowania funkcyjnego, takich jak pętle, instrukcje warunkowe czy moduły z lokalnymi zmiennymi. 

## Przypisanie danych do zmiennych
W Mathematice najczęściej korzystamy z dwóch operatorów przypisania: `=` lub `:=`.
* Operator `=` przypisuje do zmiennej **wartość** wyrażenia w momencie przypisania.
* Operator `:=` (przypisanie opóźnione) przypisuje do zmiennej **samo wyrażenie**, które jest na nowo obliczane przy każdym wywołaniu.

```mathematica
In[1]:= a = 3
Out[1]= 3

In[2]:= b = a + 7
Out[2]= 10

In[3]:= c := a + 7
Out[3]= 10

In[4]:= {b, c}
Out[4]= {10, 10}

In[5]:= a = 1
Out[5]= 1

In[6]:= {b, c}
Out[6]= {10, 8}
```

## Funkcje matematyczne
W Mathematice możemy definiować własne funkcje wybranej zmiennej. Przy definicji funkcji należy pamiętać, by korzystać z operatora `:=` oraz umieścić symbol podkreślnika `_` zaraz po nazwie zmiennej w nawiasach kwadratowych. Z tak zdefiniowanych funkcji można liczyć pochodne oraz wykorzystywać je przy rysowaniu wykresów.

```mathematica
In[1]:= f[x_] := x^2 + 3

In[2]:= f[3]
Out[2]= 12

In[3]:= f[t]
Out[3]= 3 + t^2
```

## Pętle warunkowe
Jako że Mathematica posiada język programowania funkcyjnego, możemy wykorzystywać pętle do obliczeń.

### Pętla Do
Odpowiednikiem klasycznej pętli `for` jest pętla `Do`, działająca według składni: `Do[treść, {iterator, start, koniec, krok}]`.
```mathematica
In[1]:= s = 0
In[2]:= Do[s += i^2, {i, 1, 100, 2}]
In[3]:= s
Out[3]= 166650
```

### Pętla While
Działa w następujący sposób: `While[warunek, treść]`.
```mathematica
In[1]:= s = 0
In[2]:= i = 0
In[3]:= While[i! < 10^6, s += i!; i++]
In[4]:= {i, s}
Out[4]= {10, 409114}
```

## Suma iterowana
Zamiast klasycznych pętli można także korzystać z dużego operatora sumy $\Sigma$ (który posiada dedykowany symbol w interfejsie).
```mathematica
In[1]:= \sum_{i=1}^{20} i^3
Out[1]= 44100
```

## Liczby pseudolosowe
Liczby pseudolosowe mają imitować liczby losowe, jednak są obliczane według ścisłego algorytmu, zazwyczaj na podstawie czasu odliczanego wewnątrz urządzenia.
* Aby uzyskać pseudolosową liczbę całkowitą, korzystamy z funkcji `RandomInteger[a]`, gdzie `a` to ograniczenie górne.
* Aby uzyskać pseudolosową liczbę rzeczywistą, korzystamy z funkcji `RandomReal[]`.

## Instrukcje warunkowe
Najpopularniejszą instrukcją warunkową w Mathematice jest `If`. Jej składnia to: `If[warunek, prawda, fałsz, nieokreślony]`.

```mathematica
In[1]:= If[z == 2, Print["P"], Print["F"], Print["?"]]
Out[1]= ?
```

Instrukcje warunkowe można zagnieżdżać jedna w drugiej:
```mathematica
In[1]:= b = 3
In[2]:= If[b == 1, Print["1"], If[b == 0, Print["0"], Print["X"]]]
Out[2]= X
```

## Deklaracje funkcji (Moduły)
W Mathematice możemy deklarować rozbudowane, własne funkcje z użyciem zmiennych lokalnych i kończyć je komendą `Return[]`. Służy do tego struktura `Module`, która deklaruje zmienne istniejące tylko wewnątrz funkcji (zadeklarowanie zmiennej w ciele funkcji bez modułu sprawiłoby, że stałaby się ona globalna).

**Ogólna struktura:**
```mathematica
nazwa[argument_] := Module[{zmienne_lokalne},
    treść;
    Return[]
]
```

**Przykład 1 - Prosta funkcja dodająca:**
```mathematica
In[1]:= add[a_, b_] := Module[{c},
    c = a + b;
    Return[c]
]
In[2]:= add[2, 3]
Out[2]= 5
```

**Przykład 2 - Funkcja modyfikująca wektor (łączenie z pętlą i warunkiem):**
Taka struktura idealnie nadaje się do łączenia funkcji z pętlami i instrukcjami warunkowymi.
```mathematica
In[1]:= nonNegativeVector[v_] := Module[{w = v, i, n},
    n = Length[w];
    Do[If[w[[i]] < 0, w[[i]] = 0], {i, 1, n}];
    Return[w]
]
In[2]:= nonNegativeVector[{-2, -1, 0, 1, 2}]
Out[2]= {0, 0, 0, 1, 2}
```
