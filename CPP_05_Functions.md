# CPP 05 Functions

- Defining and Calling Functions
- Function Prototypes and Parameters
- Inline Functions
- Default and Constant Arguments
- Function Overloading
- Recursion


# C++ Functions 

## 1. Defining and Calling Functions

A function is a block of code that performs a specific task.

### Syntax
```cpp
return_type function_name(parameters) {
    // body
}
````

### Example

```cpp
#include <iostream>
using namespace std;

// Function definition
int add(int a, int b) {
    return a + b;
}

int main() {
    int result = add(5, 3); // Function call
    cout << "Sum = " << result;
    return 0;
}
```

---

## 2. Function Prototypes and Parameters

### Function Prototype

Declaration of a function before main().

```cpp
int add(int, int); // prototype
```

### Example

```cpp
#include <iostream>
using namespace std;

// Prototype
int multiply(int, int);

int main() {
    cout << multiply(4, 5);
    return 0;
}

// Definition
int multiply(int a, int b) {
    return a * b;
}
```

### Types of Parameters

#### Value Parameters

```cpp
void change(int x) {
    x = 100;
}
```

#### Reference Parameters

```cpp
void change(int &x) {
    x = 100;
}
```

---

## 3. Inline Functions

Used to reduce function call overhead. The compiler replaces the function call with actual code.

### Example

```cpp
#include <iostream>
using namespace std;

inline int square(int x) {
    return x * x;
}

int main() {
    cout << square(5);
    return 0;
}
```

Note: Best for small functions.

---

## 4. Default and Constant Arguments

### Default Arguments

Provide default values to parameters.

```cpp
#include <iostream>
using namespace std;

int add(int a, int b = 10) {
    return a + b;
}

int main() {
    cout << add(5);     // b = 10
    cout << add(5, 3);  // b = 3
}
```

### Constant Arguments

Prevent modification using const.

```cpp
#include <iostream>
using namespace std;

void display(const int x) {
    // x = 10; // not allowed
    cout << x;
}

int main() {
    display(5);
}
```

---

## 5. Function Overloading

Same function name, different parameters.

### Example

```cpp
#include <iostream>
using namespace std;

int sum(int a, int b) {
    return a + b;
}

double sum(double a, double b) {
    return a + b;
}

int main() {
    cout << sum(3, 4) << endl;
    cout << sum(2.5, 3.5);
}
```

Compiler decides which function to call based on arguments.

---

## 6. Recursion

A function calling itself.

### Example: Factorial

```cpp
#include <iostream>
using namespace std;

int factorial(int n) {
    if (n == 0)
        return 1;
    else
        return n * factorial(n - 1);
}

int main() {
    cout << factorial(5);
}
```

### Key Points

* Must have a base case
* Prevents infinite recursion

---

## Summary

| Concept            | Key Idea                        |
| ------------------ | ------------------------------- |
| Function           | Reusable block of code          |
| Prototype          | Declaration before use          |
| Inline             | Faster for small functions      |
| Default Arguments  | Predefined values               |
| Constant Arguments | Prevent modification            |
| Overloading        | Same name, different parameters |
| Recursion          | Function calls itself           |
