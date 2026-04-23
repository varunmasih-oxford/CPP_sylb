# CPP 09: Classes and Objects

## 1. Introduction to Classes and Objects

A class is a blueprint, and an object is an instance of that class.

```cpp
#include <iostream>
using namespace std;

class Student {
public:
    string name;
    int age;

    void display() {
        cout << "Name: " << name << endl;
        cout << "Age: " << age << endl;
    }
};

int main() {
    Student s1;
    s1.name = "Varun";
    s1.age = 21;

    s1.display();
    return 0;
}
````

---


# Access Specifiers in C++

Access specifiers define **how the members (variables & functions) of a class can be accessed**.

There are three types:
- public
- private
- protected

---

## 1. public Access Specifier

### Definition:
Members declared as `public` can be accessed **from anywhere**:
- Inside the class
- Outside the class
- From other classes

### Example:
```cpp
#include <iostream>
using namespace std;

class Student {
public:
    string name;

    void show() {
        cout << "Name: " << name << endl;
    }
};

int main() {
    Student s1;
    s1.name = "Varun";   // Accessible
    s1.show();           // Accessible
    return 0;
}
````

### Key Point:

* No restriction on access

---

## 2. private Access Specifier

### Definition:

Members declared as `private` can be accessed **only inside the class**.

They **cannot be accessed directly outside the class**.

### Example:

```cpp
#include <iostream>
using namespace std;

class BankAccount {
private:
    int balance;

public:
    void setBalance(int b) {
        balance = b;
    }

    void showBalance() {
        cout << "Balance: " << balance << endl;
    }
};

int main() {
    BankAccount acc;

    // acc.balance = 5000; ❌ Error (not accessible)

    acc.setBalance(5000);   // ✔ Allowed
    acc.showBalance();      // ✔ Allowed

    return 0;
}
```

### Key Points:

* Used for **data hiding**
* Access through **public functions (getter/setter)**

---

## 3. protected Access Specifier

### Definition:

Members declared as `protected`:

* Can be accessed **inside the class**
* Can be accessed **by derived (child) classes**
* Cannot be accessed directly outside the class

### Example:

```cpp
#include <iostream>
using namespace std;

class Parent {
protected:
    int value;

public:
    void setValue(int v) {
        value = v;
    }
};

class Child : public Parent {
public:
    void show() {
        cout << "Value: " << value << endl; // Accessible here
    }
};

int main() {
    Child c1;
    c1.setValue(10);
    c1.show();

    // c1.value = 5; ❌ Not allowed
    return 0;
}
```

### Key Points:

* Important for **inheritance**
* Allows controlled access in child classes

---

## 4. Comparison Table

| Access Specifier | Same Class | Outside Class | Derived Class |
| ---------------- | ---------- | ------------- | ------------- |
| public           | ✔          | ✔             | ✔             |
| private          | ✔          | ✘             | ✘             |
| protected        | ✔          | ✘             | ✔             |

---

## 5. Default Access Specifier

* In `class` → default is **private**
* In `struct` → default is **public**

### Example:

```cpp
class Demo {
    int x;  // private by default
};

struct Test {
    int y;  // public by default
};
```

---

## 6. Real-Life Analogy

Think of a **bank system**:

* public → ATM access (anyone with card can use)
* private → vault (only bank system can access)
* protected → manager access (special authorized roles)

---

## 7. When to Use What?

* Use `private` → for sensitive data (best practice)
* Use `public` → for methods users interact with
* Use `protected` → when working with inheritance

---

## Summary

Access specifiers help in:

* Data security
* Encapsulation
* Controlled access
* Better program design

---

```


---

## 3. Constructors and Destructors

* Constructor: Automatically called when object is created
* Destructor: Called when object is destroyed

```cpp
#include <iostream>
using namespace std;

class Demo {
public:
    Demo() {
        cout << "Constructor called" << endl;
    }

    ~Demo() {
        cout << "Destructor called" << endl;
    }
};

int main() {
    Demo d1;
    return 0;
}
```

---

## 4. this Pointer

The `this` pointer refers to the current object.

```cpp
#include <iostream>
using namespace std;

class Student {
private:
    int age;

public:
    void setAge(int age) {
        this->age = age;
    }

    void display() {
        cout << "Age: " << age << endl;
    }
};

int main() {
    Student s1;
    s1.setAge(22);
    s1.display();
    return 0;
}
```

---

## 5. Static Members and Methods

* Shared among all objects
* Accessed using class name

```cpp
#include <iostream>
using namespace std;

class Counter {
public:
    static int count;

    Counter() {
        count++;
    }

    static void showCount() {
        cout << "Total objects: " << count << endl;
    }
};

int Counter::count = 0;

int main() {
    Counter c1, c2, c3;

    Counter::showCount();
    return 0;
}
```

