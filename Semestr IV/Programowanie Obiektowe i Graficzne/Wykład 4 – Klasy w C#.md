## Klasa
**Klasą** w C# nazywamy szablon do wytwarzania nowych obiektów. Klasa jest najczęściej używanym rodzajem typów referencyjnych. Nową klasę zawsze tworzymy w nowym pliku o takiej samej nazwie jak nazwa klasy.

W języku C# klasa niewyposażona w żaden konstruktor, posiada konstruktor domniemany bezargumentowy. Domyślnym modifikatorem dostępu do klasy jest `internal` — zasięg w obrębie jednego projektu. Oprócz modyfikatoru dostępu, klasa może być wyposażona w następujące modyfikatory:
- `sealed`: Zamknięcie klasy ze względu na dziedziczenie.
- `static`: Klasa statyczna, wszystkie składowe klasy muszą być wówczas statyczne.
- `abstract`: Klasa abstrakcyjna, ma przynajmniej jedną składową abstrakcyjną, służy jedynie do dziedziczenia.
- `partial`: Oznacza, że jest to tylko częściowa implementacja tej klasy.
## Pola
**Pola** reprezentują stan obiektu. Zgodnie z paradygmatem hermetyzacji dostęp do pól powinien być zamknięty spoza klasy. Domyślnym modyfikatorem dostępu dla pola jest `private`.

Modyfikator `readonly` uniemożliwia zmianę wartości po utworzeniu obiektu. Wartość takiemu polu można przypisać tylko w trakcie deklaracji lub w konstrutkorze. Modyfikator `const` wymaga inicjalizacji w trakcie deklarowania, nie można go więc łączyć z modyfikatorem `static`. Stałe `const` mogą być tylko typu liczbowego, `bool`, `char`, `string` oraz wyliczeniem.
## Własności
Bardzo ważną składową klasy jest **własność** (ang. *property*). Cechuje ją to, że na zewnątrz klasy wygląda jak pole, ale wewnątrz zachowuje się jak metoda. Podstawowa składnia własności wygląda następująco:
```csharp
private int cena;
public int Cena
{
        get { return cena; }
        set { cena = value; }
}
```
W powyższej składni pojawiają się dwa akcesory: `get` i `set`, metody wykonawcze. Ich ciało może zawierać logikę działania. Akcesor `get` musi zawierać instrukcję `return`, zawierającą zwracaną wartość, ewentualnie zmienną referencyjną. W obrębie akcesora `set` dostępną mamy przypisywaną wartość własności oznaczoną słowem kluczowym `value`.
## Metody
Domyślnym modyfikatorem metody w C# jest `private`. Od C# 6 można tworzyć metody wyrażeniowe. Jeśli metoda zawiera tylko wyrażenie możemy zapisać ją zwięźlej:
```csharp
public int Metoda(int argument) => 12;
public void Drukuj(string tekst) => Console.WriteLine(tekst);
```
Od C# 7 możliwe jest definiowanie metod lokalnych, zdefiniowanych w odrębie innej metody. Zasięgiem metody lokalnej jest ciało metody, w której jest zdefiniowana:
```csharp
public void PrintCubed(int n)

{

        for (int i = 0; i < n; i++)

                Console.WriteLine($"{i}^3 = {Cubed(i)}");

        int Cubed(int i) => i * i * i;

}
```
## Indeksatory
Indeksatory są naturalnym rozwiązaniem, gdy klasa implementuje słownik wartości bądź listę:
```csharp
private int[] stanPol = new int[] {1, 21, 5, 4, 1, 2, 9};
// indeksator
public int this[int n]
{
        get
        { 
                if(n > -1 && n < stanPol.Length)
                        return stanPol[i];
                else
                        throw new IndexOutOfRangeException("Zły indeks");
        }
        set
        {
                if(n > -1 && n < stanPol.Length)
                        stanPol[i] = value;
                else
                        throw new IndexOutOfRangeException("Zły indeks");
        }
}
```
## Konstruktory
Konstruktor nie musi być publiczny. Zazwyczaj konstruktor niepubliczny tworzy się po to, żeby kontrolować proces tworzenia egzemplarzy klasy poprzez wywołanie metod/własności statycznych. Wykorzystywany we wzorcu singleton, który gwarantuje stworzenie tylko jednego egzemplarza danej klasy:
```csharp
public class Singleton
{
        private static Singleton instancja = null;
        // statyczna własność zwracająca instancję
        public static Singleton Instancja
        {
                get
                {
                        if(instancja is null)
                                instancja = new Singleton();
                        return instancja;
                }
        }
        //prywatny konstruktor
        private Singleton() {}
}
```
