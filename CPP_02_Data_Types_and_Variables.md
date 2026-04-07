# C++ Data Types and Variables

## 1. Basic Data Types

These define what kind of data a variable can store.

| Data Type | Description                | Example     |
| --------- | -------------------------- | ----------- |
| int       | Integer numbers            | 10, -5      |
| float     | Decimal (single precision) | 3.14        |
| double    | Decimal (high precision)   | 3.141592    |
| char      | Single character           | 'A'         |
| bool      | True/False                 | true, false |

### Example

```cpp
#include <iostream>
using namespace std;

int main() {
    int age = 20;
    float price = 99.99;
    double pi = 3.1415926535;
    char grade = 'A';
    bool isPassed = true;

    cout << "Age: " << age << endl;
    cout << "Price: " << price << endl;
    cout << "Pi: " << pi << endl;
    cout << "Grade: " << grade << endl;
    cout << "Passed: " << isPassed << endl;

    return 0;
}
```

---

## 2. Type Modifiers and Constants

### Type Modifiers

They modify the size or range of data types.

| Modifier | Example      |
| -------- | ------------ |
| short    | short int    |
| long     | long int     |
| unsigned | unsigned int |

### Example

```cpp
#include <iostream>
using namespace std;

int main() {
    short int a = 10;
    long int b = 100000;
    unsigned int c = 50;

    cout << a << " " << b << " " << c;
    return 0;
}
```

### Constants

Values that cannot be changed.

```cpp
#include <iostream>
using namespace std;

int main() {
    const float PI = 3.14;

    cout << "PI: " << PI;
    return 0;
}
```

---

## 3. Variable Declaration and Initialization

### Declaration

```cpp
int a;
```

### Initialization

```cpp
int a = 10;
```

### Multiple Variables

```cpp
int x = 5, y = 10, z = 15;
```

### Example

```cpp
#include <iostream>
using namespace std;

int main() {
    int num = 25;
    float value = 10.5;

    cout << num << endl;
    cout << value;

    return 0;
}
```

---

## 4. Type Conversion and Casting

### Implicit Conversion (Automatic)

```cpp
int a = 10;
float b = a;

cout << b;
```

### Explicit Casting (Manual)

```cpp
#include <iostream>
using namespace std;

int main() {
    float x = 5.7;
    int y = (int)x;

    cout << "Original: " << x << endl;
    cout << "After casting: " << y << endl;

    return 0;
}
```

---

## 5. Scope and Lifetime of Variables

### Local Variables

Declared inside a function and accessible only within it.

```cpp
#include <iostream>
using namespace std;

void test() {
    int x = 10;
    cout << x << endl;
}

int main() {
    test();
    return 0;
}
```

### Global Variables

Declared outside all functions and accessible everywhere.

```cpp
#include <iostream>
using namespace std;

int globalVar = 100;

int main() {
    cout << globalVar;
    return 0;
}
```
