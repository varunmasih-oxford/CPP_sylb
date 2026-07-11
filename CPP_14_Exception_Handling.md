# C++ 14: Exception Handling

## Objectives

After completing this lesson, you will be able to:

- Understand the basics of exception handling.
- Use `try`, `catch`, and `throw` keywords.
- Handle multiple exceptions.
- Use standard exception classes.
- Create custom exception classes.

---

# 1. Basics of Exception Handling

## What is an Exception?

An **exception** is a runtime error that occurs while a program is executing. Instead of terminating the program abruptly, exceptions allow the program to handle errors gracefully.

### Common Runtime Errors

- Division by zero
- Invalid array index
- File not found
- Memory allocation failure
- Invalid user input

### Basic Syntax

```cpp
try
{
    // Code that may generate an exception
}
catch(exception_type variable)
{
    // Code to handle the exception
}
```

---

## Example 1: Division by Zero

```cpp
#include <iostream>
using namespace std;

int main()
{
    int numerator = 20;
    int denominator = 0;

    try
    {
        if (denominator == 0)
        {
            throw "Division by zero is not allowed.";
        }

        cout << numerator / denominator << endl;
    }
    catch (const char* message)
    {
        cout << "Exception: " << message << endl;
    }

    cout << "Program continues successfully." << endl;

    return 0;
}
```

### Output

```
Exception: Division by zero is not allowed.
Program continues successfully.
```

### Explanation

- The risky code is written inside the `try` block.
- The `throw` statement generates an exception.
- The `catch` block catches and handles the exception.
- The program continues executing after the exception is handled.

---

# 2. try, catch, and throw Keywords

## try

The `try` block contains the code that may generate an exception.

```cpp
try
{
    // Risky code
}
```

---

## throw

The `throw` keyword is used to generate an exception.

### Syntax

```cpp
throw value;
```

Example

```cpp
throw 100;
```

---

## catch

The `catch` block receives and handles the thrown exception.

```cpp
catch(int number)
{
    cout << number;
}
```

---

## Example 2: Throwing an Integer

```cpp
#include <iostream>
using namespace std;

int main()
{
    try
    {
        throw 100;
    }
    catch(int value)
    {
        cout << "Exception Caught: " << value << endl;
    }

    return 0;
}
```

### Output

```
Exception Caught: 100
```

---

## Example 3: Throwing a String

```cpp
#include <iostream>
#include <string>
using namespace std;

int main()
{
    try
    {
        throw string("File not found.");
    }
    catch(string message)
    {
        cout << message << endl;
    }

    return 0;
}
```

### Output

```
File not found.
```

---

# 3. Catching Multiple Exceptions

A program may throw different types of exceptions. Multiple `catch` blocks allow us to handle each type separately.

---

## Example 4

```cpp
#include <iostream>
using namespace std;

int main()
{
    int option = 2;

    try
    {
        if(option == 1)
            throw 10;

        else if(option == 2)
            throw 5.75;

        else
            throw "Unknown Error";
    }

    catch(int number)
    {
        cout << "Integer Exception: " << number << endl;
    }

    catch(double decimal)
    {
        cout << "Double Exception: " << decimal << endl;
    }

    catch(const char* message)
    {
        cout << "String Exception: " << message << endl;
    }

    return 0;
}
```

### Output

```
Double Exception: 5.75
```

---

## Example 5: Student Age Validation

```cpp
#include <iostream>
using namespace std;

int main()
{
    int age = 15;

    try
    {
        if(age < 18)
            throw "Student is not eligible.";

        if(age > 100)
            throw 100;

        cout << "Student is eligible." << endl;
    }

    catch(const char* message)
    {
        cout << message << endl;
    }

    catch(int value)
    {
        cout << "Invalid Age: " << value << endl;
    }

    return 0;
}
```

### Output

```
Student is not eligible.
```

---

# 4. Standard Exception Classes

The C++ Standard Library provides predefined exception classes in the `<exception>` and `<stdexcept>` headers.

| Exception Class | Description |
|-----------------|-------------|
| exception | Base class for all exceptions |
| runtime_error | Runtime errors |
| logic_error | Logical errors |
| invalid_argument | Invalid function argument |
| out_of_range | Index out of range |
| overflow_error | Arithmetic overflow |
| underflow_error | Arithmetic underflow |

---

## Example 6: runtime_error

```cpp
#include <iostream>
#include <stdexcept>
using namespace std;

int main()
{
    try
    {
        throw runtime_error("Unable to connect to database.");
    }
    catch(runtime_error &error)
    {
        cout << error.what() << endl;
    }

    return 0;
}
```

### Output

```
Unable to connect to database.
```

---

## Example 7: out_of_range

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main()
{
    vector<int> numbers = {10,20,30};

    try
    {
        cout << numbers.at(5);
    }
    catch(out_of_range &error)
    {
        cout << error.what() << endl;
    }

    return 0;
}
```

### Sample Output

```
vector::_M_range_check
```

*(The exact message depends on the compiler.)*

---

# 5. Creating Custom Exceptions

You can create your own exception classes to represent application-specific errors.

---

## Example 8: Simple Custom Exception

```cpp
#include <iostream>
using namespace std;

class InvalidAge
{
};

int main()
{
    int age = 15;

    try
    {
        if(age < 18)
        {
            throw InvalidAge();
        }
    }
    catch(InvalidAge)
    {
        cout << "Age must be at least 18 years." << endl;
    }

    return 0;
}
```

### Output

```
Age must be at least 18 years.
```

---

## Example 9: Custom Exception Using std::exception

```cpp
#include <iostream>
#include <exception>
using namespace std;

class InvalidSalary : public exception
{
public:

    const char* what() const noexcept override
    {
        return "Salary cannot be negative.";
    }
};

int main()
{
    int salary = -5000;

    try
    {
        if(salary < 0)
        {
            throw InvalidSalary();
        }
    }
    catch(exception &error)
    {
        cout << error.what() << endl;
    }

    return 0;
}
```

### Output

```
Salary cannot be negative.
```

---

# Real-World Example: ATM Withdrawal

```cpp
#include <iostream>
#include <stdexcept>
using namespace std;

int main()
{
    int balance = 5000;
    int withdrawAmount;

    cout << "Enter withdrawal amount: ";
    cin >> withdrawAmount;

    try
    {
        if(withdrawAmount > balance)
        {
            throw runtime_error("Insufficient balance.");
        }

        balance -= withdrawAmount;

        cout << "Withdrawal Successful" << endl;
        cout << "Remaining Balance: " << balance << endl;
    }
    catch(runtime_error &error)
    {
        cout << error.what() << endl;
    }

    return 0;
}
```

### Sample Output 1

```
Enter withdrawal amount: 2000
Withdrawal Successful
Remaining Balance: 3000
```

### Sample Output 2

```
Enter withdrawal amount: 7000
Insufficient balance.
```

---

# Key Points

- Exceptions handle runtime errors gracefully.
- `try` contains risky code.
- `throw` generates an exception.
- `catch` handles the exception.
- Multiple `catch` blocks can handle different exception types.
- Standard exception classes provide built-in error handling.
- Custom exception classes allow developers to define application-specific errors.
- The `what()` function returns a descriptive error message.

---

# Practice Questions

### Question 1

Write a program that throws an exception when a user enters zero as the denominator.

---

### Question 2

Write a program that throws an integer exception when the entered age is less than 18.

---

### Question 3

Create a program that catches both integer and string exceptions.

---

### Question 4

Write a program that uses `runtime_error` to display an "Invalid Login" message.

---

### Question 5

Create a custom exception named `NegativeNumberException` and throw it when a user enters a negative number.

---

# Summary

Exception handling improves program reliability by preventing unexpected crashes. Using `try`, `throw`, and `catch`, developers can detect runtime errors and handle them appropriately. C++ also provides standard exception classes and allows programmers to create custom exception classes for application-specific error handling.
