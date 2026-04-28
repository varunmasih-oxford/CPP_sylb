# CPP 10 – OOP Concepts

## 1. Encapsulation

### Definition

Encapsulation is the process of **binding data and methods together** into a single unit (class) and restricting direct access using access specifiers.

### Example

```cpp
#include <iostream>
using namespace std;

class Student {
private:
    int marks;

public:
    void setMarks(int m) {
        marks = m;
    }

    int getMarks() {
        return marks;
    }
};

int main() {
    Student s;
    s.setMarks(85);
    cout << s.getMarks();
}
```

---

## 2. Abstraction

### Definition

Abstraction means **showing only essential details** and hiding internal implementation.

### Example

```cpp
#include <iostream>
using namespace std;

class Car {
public:
    void start() {
        cout << "Car Started";
    }
};

int main() {
    Car c;
    c.start();
}
```

---

## 3. Inheritance

### Definition

Inheritance allows one class to **reuse properties and behavior of another class**.

### Types of Inheritance

#### 1. Single Inheritance

```cpp
class Animal {
public:
    void eat() { cout << "Eating"; }
};

class Dog : public Animal {
public:
    void bark() { cout << "Barking"; }
};
```

#### 2. Multilevel Inheritance

```cpp
class Animal {
public:
    void eat() { cout << "Eating"; }
};

class Dog : public Animal {
public:
    void bark() { cout << "Barking"; }
};

class Puppy : public Dog {
public:
    void weep() { cout << "Weeping"; }
};
```

#### 3. Multiple Inheritance

```cpp
class A {
public:
    void showA() { cout << "Class A"; }
};

class B {
public:
    void showB() { cout << "Class B"; }
};

class C : public A, public B {};
```

#### 4. Hierarchical Inheritance

```cpp
class Animal {
public:
    void eat() { cout << "Eating"; }
};

class Dog : public Animal {};
class Cat : public Animal {};
```

---

## 4. Polymorphism

### (A) Compile-Time Polymorphism (Function Overloading)

Same function name with different parameters.

```cpp
#include <iostream>
using namespace std;

class Math {
public:
    int add(int a, int b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }
};

int main() {
    Math m;
    cout << m.add(2, 3) << endl;
    cout << m.add(2, 3, 4);
}
```

### (B) Runtime Polymorphism (Method Overriding)

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    virtual void sound() {
        cout << "Animal sound";
    }
};

class Dog : public Animal {
public:
    void sound() {
        cout << "Dog barks";
    }
};

int main() {
    Animal* a;
    Dog d;
    a = &d;

    a->sound();
}
```

---

## 5. Virtual Functions

### Definition

A virtual function ensures that the **derived class method is called** when using a base class pointer.

```cpp
class Base {
public:
    virtual void show() {
        cout << "Base class";
    }
};

class Derived : public Base {
public:
    void show() {
        cout << "Derived class";
    }
};
```

---

## 6. Abstract Classes

### Definition

An abstract class contains at least one **pure virtual function** and cannot be instantiated.

```cpp
#include <iostream>
using namespace std;

class Shape {
public:
    virtual void draw() = 0;
};

class Circle : public Shape {
public:
    void draw() {
        cout << "Drawing Circle";
    }
};

int main() {
    Shape* s;
    Circle c;
    s = &c;

    s->draw();
}
```

