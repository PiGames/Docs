# C\# Style Guide
Poradnik wzorowany na [Unity C# Coding Guidelines](http://wiki.unity3d.com/index.php/Csharp_Coding_Guidelines)

## Bracing

Klamry powinny pojawiać się **zawsze** przy blokach kodu, klamra otwierająca **musi** być w nowej linii, podobnie klamra zamykająca blok kodu. 
Zawartość bloku powinna posiadać wcięcie o wielkości *1 tabulatora* lub *4 spacji*.
```csharp
void Foo()
{
	Bar();
}
```

Bloki `case` powinny wyglądać tak jak poniżej:
```csharp
switch(abc)
{
	case 1:
		DoSomethingInOneLine();
		break;
	// <- 1 pusta linia odstępu pomiędzy case'ami
	case 2:
	{
		Foo(); // <- wiele linii instrukcji = kod w klamrach
		Bar(); //
		break;
	}
	
	default:
		DoSomethingElse();
		break;
}
```

## Wyrażenia w jednej linii
Starajmy się unikać sytuacji w których tworzymy wyrażenie składające się z jednej linii, jeżeli takowe się pojawią to *muszą* być zawarte w klamrach

```csharp
public class Foo
{
	int _bar;
	
	int bar
	{
		get { return _bar; }
		set { _bar = value; }
	}
}
```

## Komentowanie
Komentujemy kod *wyłącznie* w języku angielskim. Do komentowania używamy `//` zarówno do bloków komentarzy, jak do krótkich komentarzy liniowych.

```csharp
// This is some class description
//
public class Spam
{
	public int foo; // var doing something
	
	void Test()
	{
		int bar = 2; // temporary variable
		
		// very important & complicated instruction
		//
		foo = bar + 7;
	}
}
```

## Spacing

Należy robić odstępy pomiędzy elementami wymieniamymi po przecinku, podobnie pomiędzy dwustronnymi operatorami
DOBRZE
```csharp
// ex1
Foo(a, 10, 0x32);

// ex2
if (a > 10 && b <= 32)
{
	...
}

// ex3
void Bar(int x, float b)
{
	...
}

// ex4
void Spam()
{

}
```

ŹLE
```csharp
// ex1
Foo(a,10 ,0x32); // brak odstępów pomiędzy argumentami, odstęp w złym miejscu

// ex2
if (a>10 && b<= 32) // brak odstępów pomiędzy >, brak odstępu z lewej strony <=
{
	...
}

// ex3
void Bar(int x,float b) // brak odstępu pomiędzy argumentami
{
	...
}

// ex4
void Spam () // odstęp pomiędzy nazwą funkcji, a nawiasami
{

}
```


## Nazewnictwo (naming)

- do nazw używamy **wyłącznie** języka *angielskiego*
- **unikaj** nazw typu: `void foo()`, `int a`, zamiast tego **używaj** pełnych nazw, które mówią same za siebie do czego służą, 
np `void spawnEnemy()`, `int strength`. Wyjątkiem są nazwy wchodzące "w standard"/konwencję, np `int i, n, k`.
- **używaj** prefiksów "_" do wyróżniania zmiennych `public` oraz `protected`, np `int _myPrivateVar
- **używaj** *camelCase* do nazywania:
	* członków klasy (class members)
	* parametrów (funkcji)
	* zmiennych lokalnych
	* parametrów (setters & getters)
- **używaj** *PascalCase* do nazywania:
	* funkcji
	* eventów
	* klas
- **używaj** prefików "I" do nazywania interfejsów
- **nie używaj** prefików do enumów, klas, delegatów
- stałe nazywaj używając wyłącznie dużych liter, np `MY_CONST`


## Organizacja pliku

* jeden plik źródłowy powinien zawierać tylko jedną deklarację i definicję **publicznej klasy**, 
jednakże dozwolone jest wiele klas **wewnętrznych**
* nazwa pliku = nazwa klasy publicznej
* członkowie klasy powinni być pogrupowani wg kolejności: 
	1. pola (publiczne, chronione, prywatne)
	2. parametry (setters, getters)
	3. konstruktory
	4. eventy
	5. metody
	6. prywatne implementacje interfejsów
	7. inne
	
```csharp
using System;
using UnityEngine;
 
public class MyClass : MonoBehavior
{
	// pola
	public int myPublicVar;
	float _myFloat;
	
	// setters & getters
	public float myFloat
	{
		get { return _myFloat + 7; }
		set { _myFloat = value - 7; }
	}
	
	// konstruktory
	void Awake() { ... }
	void Start() { ... }
	
	// eventy
	void OnEnable() { ... }
	
	// metody
	public void DoSomething()
	{
		_myFloat = 0.0f;
	}
	
	void DoSomethingElse()
	{
		int myVar = 0x41;
		_myFloat = myFloat - myVar;
	}
}
```

## ToDo
