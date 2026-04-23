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

## 2. Access Specifiers (public, private, protected)

Access specifiers control visibility of class members.

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
    acc.setBalance(5000);
    acc.showBalance();

    // acc.balance = 1000; ❌ Not allowed
    return 0;
}
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

