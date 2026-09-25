## Delegaty
Delegatem w C# nazywamy specjalny typ referencyjny przechowujący wskaźnik do metody o określonej sygnaturze. Delegaty są wykorzystywane do obsługi zdarzeń.

Delegaty tworzymy przy użyciu słowa kluczowego delegate:
```csharp
public delegate int myDelegate(int a, int b);
```

Za pośrednictwem delegat możemy wywoływać, w sposób pośredni, metodę, na którą delegat pokazuje. W prezentowanym przykładzie `myDelegate` może przechowywać i wywoływać metody przyjmujące dwa parametry typu `int` oraz zwracające wartość typu `int`.
```csharp
// definicja
public delegate int myDelegate(int a, int b);

// definicje funkcji z odpowiednią sygnaturą
int plus(int a, int b) {
    return a + b;
}

int times(int a, int b) {
    return a * b;
}

// przypisanie delegatowi funkcji plus
myDelegate md = plus;

// wywołanie funkcji plus za pośrednictwem delegata
Console.WriteLine(md(5, 6));
md = times;
Console.WriteLine(md(5, 6));
```

## Rodzaje delegatów
W języku C# zostało określone kilka różnych rodzajów delegatów:
- `delegate void Action<TParams>`: Delegat `Action` reprezentuje metodę, która nie zwraca wartości, ale może przyjmować do 16 parametrów wejściowych.
- `delegate Func<TParams, TResult>`: Delegat `Func` jest ogólnym delegatem, który reprezentuje metodę, która zwraca wartość. Może przyjmować do 16 parametrów wejściowych.
- `delegate bool Predicate<TParam>`: Delegat `Predicate` reprezentuje metodę, która przyjmuje jeden argument i zwraca wartość logiczną. Zwykle używany jest do sprawdzania warunków.
- `delegate void EventHandler(object? sender, EventArgs e)`: Delegat `EventHandler` jest stosowany do obsługi zdarzeń w modelu programowania zdarzeniowego. Reprezentuje metodę, która przyjmuje dwa argumenty: obiekt wywołujący zdarzenie sender i obiekt zawierający informacje o zdarzeniu `e`.

## Zdarzenia
Zdarzeniem (ang. *event*) w języku C# nazywamy mechanizm, który umożliwia komunikację między obiektami w programie. Obiekt „nadawca” powiadamia o wystąpieniu określonego zdarzenia, aby inne obiekty „odbiorcy” mogły na nie zareagować. Mechanizm zdarzeń implementuje wzorzec obserwatora.

Mechanizm zdarzeń w ogólności zdefiniowany jest w dwóch częściach:
- **Deklaracja obiektu zdarzenia**: Określa (na podstawie delegata) jakie parametry przyjmie metoda obsługująca zdarzenie. Jest to zdefiniowane w klasie, która będzie działać jako nadawca zdarzenia. Przy definicji zdarzenia używamy słowa kluczowego event oraz odpowiedniej delegaty.
- **Wywołanie zdarzenia**: Najczęściej przy spełnieniu odpowiednich warunków, zdarzenie jest wywoływane przy użyciu metody `Invoke`.

```csharp
// definicja delegata
public delegate void Function (int balance);

// definicja zdarzenia o typie delegata Function
public event Function? Alert ;

// również tak - od razu definiujemy zdarzenie z
// wbudowanym delegatem Action
// public event Action<int>? Warn;

// wywołanie zdarzenia
Alert?.Invoke(balance);

// alternatywnie
if(Alert != null) { Alert.Invoke(saldo); }
```

## Interfejsy
**Interfejs** w C# to zbiór metod, właściowści i zdarzeń, które klasa musi zaimplementować, jeśli implementuje dany interfejs.

Interfejsy nie zawierają implementacji metod, tylko ich sygnatury. Oznacza to, że klasa implementująca dany interfejs musi dostarczyć własną implementację każdej metody w interfejsie. Od C# 8.0 wprowadzono metody domyślne w interfejsach. Klasa może implementować więcej niż jeden interfejs, w przeciwieństwie do dziedziczenia klas. W C# klasa może dziedziczyć co najwyżej po jedenej klasie.

Interfejs definiuje co klasa powinna robić, ale nie określa, jak to robi (jest tzw. kontraktem dla klasy). Każda klasa implementująca interfejs musi dostarczyć własną implementację zadeklarowanych metod. Interfejsy pozwalają na polimorfizm – różne klasy mogą implementować interfejs na swój sposób, ale w kodzie możemy je traktować tak samo
```csharp
public interface ISortingAlgorithm
{
        void Sort(int[] array);
}
```
Interfejsy są narzędziem abstrakcji, ponieważ pozwalają definiować, co klasa powinna robić, ale nie określają, jak ma to robić. Dzięki abstrakcji możemy zmieniać implementacje bez ingerencji w kod klienta.

