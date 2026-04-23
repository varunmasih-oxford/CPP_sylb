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
