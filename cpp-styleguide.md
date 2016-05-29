#C++ Code Style Guide
W.I.P - kolejność narazie losowa, mile widziane propozycje

###Brace Style
Bloki kodu oznaczamy klamrami "piramidkowymi"

**DOBRZE**
```cpp
void foo()
{
	...
}
```

**ŹLE**
```cpp
void foo()  {
	...
}
```

###Indendation
Wcięcia w kodzie robimy przy użyciu pojedynczego **tabulatora** a nie 2 lub 4 spacji!

**DOBRZE**
```cpp
void foo()
{
	// tab
}
```

**ŹLE**
```cpp
void foo()
{
    // 4 spacje
}

void bar()
{
  // 2 spacje
}
```

###Naming
Do nazywania stosujemy **pełnych i angielskich** nazw pisanych przy użyciu **CamelCase**.

**DOBRZE**
```cpp
int myLocalVariable;
void myFunction()
{
	// code
}
```

**ŹLE**
```cpp
int a;
void f()
{
	// code
}
```

###Naming - Classes
**Nazwy klas** rozpoczynamy dużą literą, np *MyClass*

**DOBRZE**
```cpp
class MyClass
{
	...
};
```

**ŹLE**
```cpp
// 1
class myclass
{
	...
};

// 2
class myClass
{
	...
};
```

**Pola publiczne** rozpoczynamy z małej litery, **metody publiczne** rozpoczynamy wielką literą. 

Z kolei **pola prywatne** rozpoczynamy prefiksem *"m_"* oraz małą literą, **metody prywatne** rozpoczynamy małą literą. Np.
```cpp
class MyClass
{
public:
	int myPublicVariable;
	
	MyClass();
	void MyPublicMethod();
	
private:
	int m_myPrivateVariable;
	void myPrivateMethod();
};
```

*todo ...*
