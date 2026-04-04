# CPP 01 Fundamentals

- Introduction to C++
- History and Features of C++
- Structure of a C++ Program
- Input and Output using cin and cout
- Compilation and Execution Process
- Comments and Syntax Rules

# Introduction to C++

C++ is a general-purpose programming language developed as an extension of the C language. It supports multiple programming paradigms including procedural, object-oriented, and generic programming. C++ is widely used for system/software development, game development, and performance-critical applications.

---

# History and Features of C++

## History
- Developed by Bjarne Stroustrup in the early 1980s.
- Initially called "C with Classes".
- Renamed to C++ in 1983.
- Designed to add object-oriented features to C while maintaining efficiency.

## Features of C++
- Object-Oriented Programming (OOP)
- Encapsulation, Inheritance, Polymorphism
- Function and Operator Overloading
- Rich Standard Library (STL)
- Low-level memory manipulation
- High performance and efficiency
- Platform portability

---

# Structure of a C++ Program

A basic C++ program consists of the following parts:

```cpp
#include <iostream>   // Header file

using namespace std;  // Namespace

int main() {          // Main function
    cout << "Hello, World!";  // Output statement
    return 0;         // Exit status
}
````

## Explanation

* `#include <iostream>`: Includes input-output stream library
* `using namespace std;`: Allows use of standard names without prefix
* `int main()`: Entry point of the program
* `cout`: Used to display output
* `return 0;`: Ends the program

---

# Input and Output using cin and cout

```cpp
#include <iostream>
using namespace std;

int main() {
    int age;
    
    cout << "Enter your age: ";
    cin >> age;

    cout << "Your age is: " << age;
    
    return 0;
}
```

## Explanation

* `cout`: Output stream (prints to screen)
* `cin`: Input stream (reads from keyboard)
* `>>`: Extraction operator
* `<<`: Insertion operator

---

# Compilation and Execution Process

## Steps

1. Write source code (e.g., `program.cpp`)
2. Compile using a compiler (like g++)
3. Fix errors if any
4. Run the executable file

## Example (Command Line)

```bash
g++ program.cpp -o program
./program
```

## Process Flow

* Source Code → Compiler → Object Code → Linker → Executable → Output

---

# Comments and Syntax Rules

## Comments

### Single-line Comment

```cpp
// This is a single-line comment
```

### Multi-line Comment

```cpp
/* This is a
   multi-line comment */
```

---

## Syntax Rules

* Every statement ends with a semicolon `;`
* C++ is case-sensitive (`age` and `Age` are different)
* Keywords (int, return, etc.) have special meaning
* Variables must be declared before use
* Blocks of code are enclosed in `{ }`

---

## Example Demonstrating Syntax Rules

```cpp
#include <iostream>
using namespace std;

int main() {
    int number = 10;   // Variable declaration

    if (number > 5) {
        cout << "Number is greater than 5";
    }

    return 0;
}
```

---

# Difference Between C and C++

## Core Philosophy
- C: Procedural programming (focus on functions and step-by-step logic)
- C++: Multi-paradigm (procedural + object-oriented + generic programming)

## Key Differences

### 1. Programming Style
- C: Uses functions and structures  
- C++: Supports classes and objects (OOP concepts like encapsulation, inheritance, polymorphism)

### 2. Data Security
- C: No access modifiers  
- C++: Has private, protected, public (better data hiding)

### 3. Functions
- C: No function overloading  
- C++: Supports function overloading and operator overloading  

### 4. Memory Management
- C: Uses malloc() and free()  
- C++: Uses new and delete (with constructors/destructors)

### 5. Input/Output
- C: printf(), scanf()  
- C++: cout, cin (iostream)

### 6. Structures vs Classes
- C: struct (no methods inside)  
- C++: class (data + functions together)

### 7. Standard Libraries
- C: Smaller standard library  
- C++: Rich library including STL (vectors, maps, etc.)

### 8. Exception Handling
- C: No built-in support  
- C++: Supports try, catch, throw  

### 9. Namespaces
- C: Not available  
- C++: Uses namespace to avoid naming conflicts  

### 10. Compatibility
- C++ is largely backward-compatible with C, but not all C code works perfectly in C++

## Example

### C
```c
#include <stdio.h>

int main() {
    printf("Hello World");
    return 0;
}
````

### C++

```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Hello World";
    return 0;
}
```

## When to Use

* C: System programming, embedded systems, OS-level work
* C++: Game development, applications, competitive programming, large-scale systems

