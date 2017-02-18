# C++ Code Style Conventions

## Ogólnie

**Używaj tabulatora równemu 4 spacjom.**

**Używaj wszędzie następujących klamer (if, else, funkcje, struktury, definicje klas, itd.).**

```cpp
if ( x )
{
    // Kod
}
```
**Deklarację *else* lub *else if ( x )* rozpoczynaj w tej samej linii, gdzie znajduje się klamra zamykająca.**

```cpp
if ( x )
{
    // Kod
} else if ( x )
{
    // Kod
} else
{
    // Kod
}
```

**Rozdzielaj wyrażenia spacjami:**
```cpp
if ( x )
{
    // Kod
}
```
zamiast
```cpp
if (x)
{
    // Kod
}
```
oraz
```cpp
x = ( y * 0.5f );
```
zamiast
```cpp
x = (y * 0.5f);
```


**Precyzyjnie określaj typ liczby rzeczywistej *float* , chyba, że jest jakiś powód aby był to *double*.**
```cpp
float f = 0.5f;
```
zamiast
```cpp
float f = 0.5;
```
oraz
```cpp
float f = 1.0f;
```
zamiast
```cpp
float f = 1.f;
```

**Nazwy funkcji rozpoczynaj z wielkiej litery:**
```cpp
void Function();
```
**Jeśli nazwa funkcji składa się z wielu słów, każde słowo rozpoczynaj z wielkiej litery:**
```cpp
void VeryLongName();
```


**Standardowy nagłówek funkcji to:**
```cpp
/*
====================
Created by: NazwaTwórcy
NazwaFunkcji
    Opis
====================
*/
```


**Nazwy zmiennych i pól rozpoczynaj małą literą.**
```cpp
float myVariable;
```

**Nazwy stworzone za pomocą *using* nazywaj tak samo jak zmienne, a także zawsze dodawaj przyrostek *_t*.**
```cpp
using entityID_t = uint32_t;
```
**Struktury nazywaj tak samo jak zmienne, a także zawsze dodawaj przyrostek *_t*.**
```cpp
struct myStruct_t;
```
**Enumy nazywaj tak samo jak zmienne, a także zawsze dodawaj przyrostek *_t*. Stałe zapisuj wielką literą. Wiele słów rozdzielaj znakiem podkreślenia.**
```cpp
enum contact_t
{
    CONTACT_NONE,
    CONTACT_AABB
};
```
**Do nazw funkcji rekurencyjnych dodawaj przyrostek *_r***
```cpp
void SomeFunction_r( int something );
```
**Zmienne zdefiniowane za pomocą *constexpr* zapisuj wielką literą. Wiele słów rozdzielaj znakiem podkreślenia.**
```cpp
constexpr size_t MAX_ENTITY_COUNT = 512'000; 
```
**Używaj *const* zawsze gdy jest to możliwe.**
Pisz:
```cpp
const int *p;           // Wskaźnik na const int
int * const p;          // const wskaźnik na int
const int * const p     // const wskaźnik na const int
```
Nie pisz:
```cpp
int const *p;
```

## Klasy

**Standardowy nagłówek klasy to:**
```cpp
/*
===============================================================================
Created by: NazwaTwórcy
	Opis

===============================================================================
*/
```

**Klasy pisz w *namespace pi*.**
```cpp
namespace pi
{
    class Vec3;
}
```
**Pola klas mają takie same nazewnictwo jak zmienne.**
```cpp
class Vec3
{
    float x;
    float y;
    float z;
};
```

**Metody mają takie same nazewnictwo jak funkcje.**
```cpp
class Vec3 
{
    float Length() const;
}
```

**Kolejność pól i metod klasy powinna być następująca:**
1. przyjaźnie klasy (*friend*)
2. publiczne pola
3. publiczne metody
4. chronione pola
5. chronione metody
6. prywatne pola
7. prywatne metody
Pozwala to na łatwe odszukanie publicznego interfejsu klasy.

**Zwasze zaznaczaj metody klasy *const* jeśli nic nie modyfikują.**
**Omijaj *const_cast*. Gdy obiekt musi zostać zmodyfikowany, ale dostępne są tylko wersje *const*, napisz metodę, która w czytelny sposób udostępni modyfikowalną wersję obiektu. Pozwali to utrzymać kontrolę nad *stałością* w rękach obiektu, a nie użytkownika.**

**Zwracaj *const* chyba, że celem metody jest zmiana obiektu.**

**Przeładowanie metod powinno być omijane w większości przypadków. Na przykład:**
zamiast
```cpp
    const std::shared_ptr<Animation> GetAnimation( uint32_t index ) const;
    const std::shared_ptr<Animation> GetAnimation( const char *name ) const;
    const std::shared_ptr<Animation> GetAnimation( float randomDiversity ) const;
```
pisz
```cpp
    const std::shared_ptr<Animation> GetAnimationByIndex( uint32_t index ) const;
    const std::shared_ptr<Animation> GetAnimationByName( const char *name ) const;
    const std::shared_ptr<Animation> GetRandomAnimation( float randomDiversity ) const;
```
**Poprawnie nazwane metody będą tworzyły mniej błędów przez ich złe wywoływanie. Przykład:**
```cpp
const std::shared_ptr<Animation> GetAnimation( 0 );
```
**Może to być rozumiane jako prośba o losową animację, ale kompilator mógłby to zinterpretować jako prośba o animację o indeksie *0*.**

**Dozwolone jest przeciążanie funkcji ze względu na typ zwracany *const*:**
```cpp
class AnimatedEntity : public Entity
{
    std::shared_ptr<Animator> GetAnimator();
    const std::shared_ptr<Animator> GetAnimator() const;
};
```
**W tym przypadku stała wersja *GetAnimator* została stworzona w celu umożliwienia wywołania jej w metodach *const*. Ponieważ *AnimatedEntity* zazwyczaj nie jest stałym obiektem, jest to dozwolone.**

## Nazwy plików

**Każda klasa powinna znajdować się w oddzielnym pliku, o ile ma sens stworzenie kilku małych klas w jednym pliku.**
**Nazwa pliku powinna być taka sama jak nazwa klasy.**
```cpp
class MyClass;
```
pliki:
```
MyClass.cpp
MyClass.hpp
```
