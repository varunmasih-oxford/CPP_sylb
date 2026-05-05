# CPP 11: Operator Overloading and Friend Functions

## 1. Introduction to Operator Overloading

**Operator Overloading** allows you to redefine how operators (like `+`, `-`, `*`, `==`) work for user-defined data types (classes).

### Why use it?

* Makes code more readable
* Enables intuitive operations on objects
* Mimics real-world behavior

### Example (Without Overloading)

```cpp
class Complex {
public:
    int real, imag;
};

Complex add(Complex c1, Complex c2) {
    Complex temp;
    temp.real = c1.real + c2.real;
    temp.imag = c1.imag + c2.imag;
    return temp;
}
```

### Example (With Operator Overloading)

```cpp
class Complex {
public:
    int real, imag;

    Complex operator + (Complex c) {
        Complex temp;
        temp.real = real + c.real;
        temp.imag = imag + c.imag;
        return temp;
    }
};
```

---

## 2. Overloading Unary and Binary Operators

### A. Unary Operator Overloading

Unary operators work on **one operand**.

#### Example: `++` Operator

```cpp
class Number {
public:
    int value;

    void operator ++() {
        value++;
    }
};

int main() {
    Number n;
    n.value = 5;

    ++n;
    cout << n.value; // Output: 6
}
```

---

### B. Binary Operator Overloading

Binary operators work on **two operands**.

#### Example: `+` Operator

```cpp
class Number {
public:
    int value;

    Number operator + (Number n) {
        Number temp;
        temp.value = value + n.value;
        return temp;
    }
};

int main() {
    Number n1, n2, result;
    n1.value = 10;
    n2.value = 20;

    result = n1 + n2;
    cout << result.value; // Output: 30
}
```

---

## 3. Friend Functions and Friend Classes

### A. Friend Function

A **friend function** is not a member of the class but can access its private and protected members.

### Syntax:

```cpp
class ClassName {
    friend return_type function_name(arguments);
};
```

### Example:

```cpp
class Box {
private:
    int length;

public:
    Box() { length = 10; }

    friend void display(Box b);
};

void display(Box b) {
    cout << "Length: " << b.length;
}
```

---

### B. Friend Class

A **friend class** can access private members of another class.

```cpp
class A {
private:
    int x = 10;

    friend class B;
};

class B {
public:
    void show(A a) {
        cout << a.x;
    }
};
```

---

## 4. Overloading Stream Operators (`<<` and `>>`)

These operators are used for **input/output**.

### A. Overloading `<<` (Insertion Operator)

```cpp
class Student {
public:
    int age;

    friend ostream & operator << (ostream &out, Student s) {
        out << "Age: " << s.age;
        return out;
    }
};
```

---

### B. Overloading `>>` (Extraction Operator)

```cpp
class Student {
public:
    int age;

    friend istream & operator >> (istream &in, Student &s) {
        in >> s.age;
        return in;
    }
};
```

---

### Complete Example

```cpp
#include <iostream>
using namespace std;

class Student {
public:
    int age;

    friend ostream & operator << (ostream &out, Student s) {
        out << "Age: " << s.age;
        return out;
    }

    friend istream & operator >> (istream &in, Student &s) {
        in >> s.age;
        return in;
    }
};

int main() {
    Student s;

    cout << "Enter age: ";
    cin >> s;

    cout << s;

    return 0;
}
```

