# CPP 16: Best Practices and Advanced Topics

## Learning Objectives

After completing this chapter, you will be able to:

- Understand Namespaces and the Scope Resolution Operator
- Learn Lambda Expressions
- Use the `auto` Keyword and Type Inference
- Work with Range-based for Loops
- Understand Move Semantics and Rvalue References
- Explore Modern C++ Features from C++11 to C++20
- Follow C++ Best Practices

---

# 1. Namespaces

## What is a Namespace?

A **Namespace** is used to organize code and prevent name conflicts.

Different libraries may contain functions with the same name. Namespaces help distinguish them.

---

## Syntax

```cpp
namespace NamespaceName
{
    // variables
    // functions
    // classes
}
```

---

## Example

```cpp
#include <iostream>
using namespace std;

namespace Math
{
    int value = 100;

    void display()
    {
        cout << "Inside Math Namespace" << endl;
    }
}

int main()
{
    cout << Math::value << endl;

    Math::display();

    return 0;
}
```

### Output

```
100
Inside Math Namespace
```

---

# 2. Scope Resolution Operator (::)

## What is the Scope Resolution Operator?

The **Scope Resolution Operator (`::`)** is used to access:

- Namespace members
- Global variables
- Class members
- Static members

---

## Example 1: Accessing Namespace Members

```cpp
#include <iostream>
using namespace std;

namespace College
{
    string name = "Oxford Institute";
}

int main()
{
    cout << College::name;

    return 0;
}
```

---

## Example 2: Accessing Global Variable

```cpp
#include <iostream>
using namespace std;

int number = 100;

int main()
{
    int number = 50;

    cout << "Local : " << number << endl;

    cout << "Global : " << ::number;

    return 0;
}
```

### Output

```
Local : 50
Global : 100
```

---

# 3. Lambda Expressions

## What is a Lambda Expression?

A **Lambda Expression** is an anonymous function.

It can be written directly where it is needed.

Introduced in **C++11**.

---

## Syntax

```cpp
[capture](parameters)
{
    // body
};
```

---

## Example 1

```cpp
#include <iostream>
using namespace std;

int main()
{
    auto greet = []()
    {
        cout << "Welcome to C++ Programming";
    };

    greet();

    return 0;
}
```

### Output

```
Welcome to C++ Programming
```

---

## Example 2

```cpp
#include <iostream>
using namespace std;

int main()
{
    auto add = [](int a, int b)
    {
        return a + b;
    };

    cout << add(10,20);

    return 0;
}
```

### Output

```
30
```

---

# 4. auto Keyword

## What is auto?

The **auto** keyword allows the compiler to automatically determine the data type.

---

## Example

```cpp
#include <iostream>
using namespace std;

int main()
{
    auto age = 20;

    auto salary = 45000.75;

    auto grade = 'A';

    auto name = "Rahul";

    cout << age << endl;

    cout << salary << endl;

    cout << grade << endl;

    cout << name;

    return 0;
}
```

---

## Advantages

- Less typing
- Cleaner code
- Useful with templates
- Useful with iterators

---

## Example with Iterator

```cpp
vector<int> numbers = {10,20,30};

for(auto it = numbers.begin(); it != numbers.end(); it++)
{
    cout << *it << " ";
}
```

---

# 5. Type Inference

Type Inference means the compiler automatically detects the variable type.

Example

```cpp
auto x = 50;

auto y = 6.75;

auto z = 'A';
```

Compiler interprets them as

```cpp
int x;

double y;

char z;
```

---

# 6. Range-based for Loop

## What is a Range-based for Loop?

Introduced in **C++11**.

Used to iterate through arrays and STL containers.

---

## Syntax

```cpp
for(dataType variable : collection)
{
    // statements
}
```

---

## Example with Array

```cpp
#include <iostream>
using namespace std;

int main()
{
    int marks[] = {75,82,91,68,88};

    for(int x : marks)
    {
        cout << x << " ";
    }

    return 0;
}
```

### Output

```
75 82 91 68 88
```

---

## Example with Vector

```cpp
#include <iostream>
#include <vector>

using namespace std;

int main()
{
    vector<int> numbers = {10,20,30,40};

    for(auto n : numbers)
    {
        cout << n << " ";
    }

    return 0;
}
```

### Output

```
10 20 30 40
```

---

# 7. Move Semantics

## What is Move Semantics?

Move Semantics allows resources (such as memory) to be transferred instead of copied.

Introduced in **C++11**.

Benefits:

- Faster execution
- Better memory management
- Less copying

---

## Copy Example

```cpp
string str1 = "Programming";

string str2 = str1;
```

Both strings have separate memory.

---

## Move Example

```cpp
#include <iostream>
#include <utility>

using namespace std;

int main()
{
    string str1 = "Programming";

    string str2 = move(str1);

    cout << str2;

    return 0;
}
```

### Output

```
Programming
```

---

# 8. Rvalue References

## What is an Rvalue Reference?

An **Rvalue Reference** uses `&&`.

It binds to temporary objects and enables move semantics.

---

## Syntax

```cpp
dataType&& variable = value;
```

---

## Example

```cpp
#include <iostream>
using namespace std;

int main()
{
    int &&x = 100;

    cout << x;

    return 0;
}
```

### Output

```
100
```

---

# 9. Modern C++ Features

## C++11

Introduced:

- auto
- nullptr
- Lambda Expressions
- Move Semantics
- Range-based for Loop
- Smart Pointers
- Thread Library

---

## C++14

Added:

- Generic Lambdas
- Improved constexpr
- Binary Literals
- Variable Templates

---

## C++17

Added:

- Structured Bindings
- if constexpr
- std::optional
- std::variant
- std::filesystem

---

## C++20

Added:

- Concepts
- Modules
- Coroutines
- Ranges Library
- Three-way Comparison Operator (`<=>`)

---

# 10. C++ Best Practices

## 1. Use Meaningful Variable Names

✔ Good

```cpp
int studentMarks;
```

✘ Bad

```cpp
int x;
```

---

## 2. Initialize Variables

```cpp
int age = 0;
```

---

## 3. Use const When Possible

```cpp
const double PI = 3.14159;
```

---

## 4. Prefer STL Containers

Instead of

```cpp
int arr[100];
```

Use

```cpp
vector<int> arr;
```

---

## 5. Avoid Global Variables

Prefer local variables or class members.

---

## 6. Keep Functions Small

Each function should perform one specific task.

---

## 7. Comment Complex Code

Write comments only where necessary.

---

## 8. Use Modern Features

Prefer:

- auto
- range-based loops
- smart pointers
- STL algorithms

instead of older approaches.

---

# Real-World Example

## Student Marks

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main()
{
    vector<int> marks = {85,72,91,66,88};

    sort(marks.begin(), marks.end());

    for(auto mark : marks)
    {
        cout << mark << " ";
    }

    return 0;
}
```

### Output

```
66 72 85 88 91
```

---

# Summary

- Namespaces prevent naming conflicts.
- `::` accesses namespace, class, and global members.
- Lambda Expressions create anonymous functions.
- `auto` enables automatic type detection.
- Range-based loops simplify iteration.
- Move Semantics improve performance.
- Rvalue References support efficient resource transfer.
- Modern C++ introduces safer, cleaner, and faster programming features.

---

# Interview Questions

1. What is a Namespace?
2. What is the Scope Resolution Operator?
3. What are Lambda Expressions?
4. What is the purpose of the `auto` keyword?
5. What is Type Inference?
6. What is a Range-based for Loop?
7. What is Move Semantics?
8. What is an Rvalue Reference?
9. What are the major features of C++11?
10. Name three features introduced in C++20.
11. Why should we use STL containers?
12. What are some C++ coding best practices?

---

# Practice Programs

1. Create your own namespace and access its members.
2. Demonstrate the use of the Scope Resolution Operator.
3. Write a Lambda Expression to multiply two numbers.
4. Use `auto` with different data types.
5. Traverse a vector using a Range-based for Loop.
6. Demonstrate Move Semantics using `std::move()`.
7. Create an example using an Rvalue Reference.
8. Sort a vector using STL and print it with a Range-based Loop.
9. Compare copy assignment and move assignment.
10. Build a small student management program using modern C++ features.

---

# Practice Exercises

## Easy

1. Create a namespace named `College`.
2. Print a global variable using `::`.
3. Write a simple lambda to display "Hello C++".
4. Declare five variables using `auto`.
5. Print an array using a Range-based for Loop.

---

## Medium

6. Create a lambda to calculate the square of a number.
7. Traverse a vector using `auto`.
8. Demonstrate `std::move()` with strings.
9. Use a Range-based Loop with a `set`.
10. Compare traditional loops with Range-based Loops.

---

## Advanced

11. Build a calculator using lambda expressions.
12. Create multiple namespaces in one program.
13. Compare copy semantics and move semantics using large vectors.
14. Explore features from C++11 to C++20 with code examples.
15. Build a mini project that uses namespaces, STL, lambdas, `auto`, and range-based loops together.
