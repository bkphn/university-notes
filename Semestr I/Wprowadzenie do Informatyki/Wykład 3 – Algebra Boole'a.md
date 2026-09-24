## Logika
Logika jest jedną z podstawowych dziedzin filozofii. Jest to nauka o sposobach jasnego i ścisłego formułowania myśli, o regułach poprawnego rozumowania i uzasadniania twierdzeń. Podstawą pojęć są definicje, a wnioskowanie opiera się na dowodach. Głównymi elementami logiki są zatem: definicja, twierdzenie i dowód.

## Logika matematyczna
Przedmiotem badań logiki matematycznej są formalne teorie matematyczne, ich modele, dowody oraz zasięg matematycznych rozumowań. W badaniach stosuje się wyłącznie ścisłe i formalne metody matematyki.

Rachunkiem zdań nazywamy badanie związków logicznych pomiędzy zdaniami. Aby stosować logikę matematyczną, zdania muszą być albo prawdziwe, albo fałszywe.
## Tabele prawdy dla spójników logicznych
Zdania proste można łączyć w złożone za pomocą spójników logicznych.
1. **Negacja (*nieprawda, że*)**
	Oznaczana symbolem $\neg$ (rzadziej $\sim$).
$$\neg 0=1 \qquad \neg 1=0$$
2. **Koniunkcja (*i*)**
	Oznaczana symbolem $\wedge$.
$$0\land 0=0 \qquad 0\land 1=0$$ $$1\land 0=0 \qquad 1\land 1=1$$
3. **Alternatywa (*lub*)**
	Oznaczana symbolem $\vee$.
$$0\lor 0 =0 \qquad 0\lor 1=1$$$$1\lor 0=1 \qquad 0\lor 1 =1$$
4.  **Implikacja (*jeżeli... to...*)**
	Oznaczana symbolem $\Rightarrow$.
$$0\implies 0=1\qquad 0\implies 1=1$$ $$1\implies 0 =0 \qquad 1\implies 1 = 1$$
5. **Równoważność (*wtedy i tylko wtedy*)**
	Oznaczana symbolem $\Leftrightarrow$.
$$0\iff 0=0\qquad 0\iff 1=0$$ $$1 \iff 0=0\qquad 1\iff 1 = 1$$
## Algebra Boole'a
George Boole odkrył, że funkcja logiczna może być wyrażona w postaci algebraicznej. 
* Operację koniunkcji reprezentuje **mnożenie**.
* Operację alternatywy reprezentuje **dodawanie**.
* Negacja jest oddzielną operacją.

Zdaniom prawdziwym przyporządkowuje się wartość binarną $1$, a fałszywym $0$.

**Operatory Boole'owskie:**
1. **Negacja**
	$\bar{A}=\neg A$
2. **Suma**
	$A+B=A\land B$
3. **Iloczyn**
	$A\cdot B=A\lor B$

**Zawsze prawdziwe są następujące równości:**
* $0 + 1 = 1$
* $0 + A = A$
* $1 + A = 1$
* $A + A = A$
* $A + \overline{A} = 1$
* $0 \cdot 1 = 0$
* $0 \cdot A = 0$
* $1 \cdot A = A$
* $A \cdot A = A$
* $A \cdot \overline{A} = 0$
* $\overline{\overline{A}} = A$
## Prawa Algebry Boole'a
* **Przemienność:** $$A + B = B + A, \quad A \cdot B = B \cdot A$$
* **Łączność:** $$(A + B) + C = A + (B + C), \quad (A \cdot B) \cdot C = A \cdot (B \cdot C)$$
* **Rozdzielność:** $$A \cdot (B + C) = A \cdot B + A \cdot C, \quad
A + (B \cdot C) = (A + B) \cdot (A + C)$$
* **Prawa de Morgana:** $$\overline{A + B} = \overline{A} \cdot \overline{B}$$ $$\overline{A \cdot B} = \overline{A} + \overline{B}$$
## Bramki logiczne
Początkowo algebra Boole'a służyła do analizy procesów myślowych, a obecnie stanowi podstawę projektowania binarnych układów cyfrowych.

| Bramka            | Zależność Boole'owska                                          |
| :---------------- | :------------------------------------------------------------- |
| **Bufor cyfrowy** | $Q = A$                                                        |
| **NOT**           | $Q = \overline{A}$                                             |
| **AND**           | $Q = A \cdot B$                                                |
| **OR**            | $Q = A + B$                                                    |
| **NAND**          | $Q = \overline{A \cdot B}$                                     |
| **NOR**           | $Q = \overline{A + B}$                                         |
| **XOR**           | $Q = A \oplus B = \overline{A} \cdot B + A \cdot \overline{B}$ |
## Szyfrowanie danych XOR
Dzięki wykorzystaniu operacji alternatywy wykluczającej (XOR) możemy zdefiniować proste szyfrowanie. 
* Dla każdej litery $x$ odczytujemy jej kod ASCII i przekształcamy do postaci binarnej. 
* Definiujemy bajt $k$ będący kluczem szyfru. 
* Każdą literę szyfrujemy za pomocą operacji $x \oplus k$.

Ciekawą cechą operacji XOR jest to, że wywołana podwójnie z tym samym kluczem na danych, przywraca je do pierwotnej formy: $$(A \oplus B) \oplus B = A$$Dzięki temu operację tę można wykorzystać za pomocą jednego klucza zarówno do zaszyfrowania, jak i odszyfrowania ciągu znaków.