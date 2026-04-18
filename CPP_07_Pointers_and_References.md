# CPP 07: Pointers and References

---

## 1. Introduction to Pointers

A **pointer** is a variable that stores the **memory address** of another variable.

### Syntax

```cpp
int *ptr;
```

### Example

```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 10;
    int *ptr = &a;

    cout << "Value of a: " << a << endl;
    cout << "Address of a: " << &a << endl;
    cout << "Pointer value (address): " << ptr << endl;
    cout << "Value using pointer: " << *ptr << endl;

    return 0;
}
```

### Key Operators

* `&` → Address of variable
* `*` → Dereference (value at address)

---

## 2. Pointer Arithmetic

Pointers can perform arithmetic operations.

### Operations

* Increment: `ptr++`
* Decrement: `ptr--`
* Addition: `ptr + n`
* Subtraction: `ptr - n`

### Example

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[] = {10, 20, 30};
    int *ptr = arr;

    cout << *ptr << endl;     // 10
    ptr++;
    cout << *ptr << endl;     // 20

    return 0;
}
```

👉 Pointer moves based on **data type size**
(e.g., `int` = 4 bytes)

---

## 3. Pointers and Arrays

Array name itself acts as a pointer to the first element.

### Example

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[3] = {1, 2, 3};

    cout << arr << endl;        // Address of first element
    cout << *arr << endl;       // 1
    cout << *(arr + 1) << endl; // 2

    return 0;
}
```

### Key Concept

```cpp
arr[i] == *(arr + i)
```

---

## 4. Pointers to Functions

Pointers can store the address of a function.

### Syntax

```cpp
return_type (*ptr_name)(parameters);
```

### Example

```cpp
#include <iostream>
using namespace std;

int add(int a, int b) {
    return a + b;
}

int main() {
    int (*funcPtr)(int, int) = add;

    cout << funcPtr(2, 3);  // 5

    return 0;
}
```

---

## 5. Reference Variables

A **reference** is an alias (another name) for a variable.

### Syntax

```cpp
int &ref = variable;
```

### Example

```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 10;
    int &ref = a;

    ref = 20;

    cout << a;  // 20

    return 0;
}
```

### Key Points

* Must be initialized at declaration
* Cannot be NULL
* Cannot be changed to refer another variable

---

## 6. Dynamic Memory (new and delete)

Used to allocate memory at **runtime**.

### Syntax

```cpp
int *ptr = new int;
delete ptr;
```

---

### Example (Single Variable)

```cpp
#include <iostream>
using namespace std;

int main() {
    int *ptr = new int;

    *ptr = 50;
    cout << *ptr << endl;

    delete ptr;

    return 0;
}
```

---

### Example (Array)

```cpp
#include <iostream>
using namespace std;

int main() {
    int *arr = new int[3];

    arr[0] = 1;
    arr[1] = 2;
    arr[2] = 3;

    for(int i = 0; i < 3; i++) {
        cout << arr[i] << " ";
    }

    delete[] arr;

    return 0;
}
```

---

## Summary

| Concept            | Key Idea                |
| ------------------ | ----------------------- |
| Pointer            | Stores address          |
| Pointer Arithmetic | Move across memory      |
| Arrays & Pointers  | Array acts as pointer   |
| Function Pointer   | Stores function address |
| Reference          | Alias of variable       |
| new/delete         | Dynamic memory          |

