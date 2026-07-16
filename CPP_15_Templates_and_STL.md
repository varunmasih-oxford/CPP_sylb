# CPP 15: Templates and STL

## Learning Objectives

After completing this chapter, you will be able to:

- Understand Function Templates
- Understand Class Templates
- Learn the Standard Template Library (STL)
- Use STL Containers
- Work with Iterators
- Apply STL Algorithms
- Build generic and reusable programs

---

# 1. Function Templates

## What is a Function Template?

A **Function Template** allows us to write a single function that works with different data types.

Instead of writing separate functions for `int`, `float`, and `double`, we write one generic function.

### Syntax

```cpp
template <typename T>

return_type functionName(parameters)
{
    // code
}
```

`typename` and `class` mean the same thing in templates.

Example:

```cpp
template <typename T>
```

or

```cpp
template <class T>
```

Both are correct.

---

## Example 1: Maximum of Two Numbers

```cpp
#include <iostream>
using namespace std;

template <typename T>

T maximum(T a, T b)
{
    return (a > b) ? a : b;
}

int main()
{
    cout << maximum(10,20) << endl;

    cout << maximum(5.6,9.8) << endl;

    cout << maximum('A','Z') << endl;

    return 0;
}
```

### Output

```
20
9.8
Z
```

---

## Example 2: Minimum of Two Numbers

```cpp
#include <iostream>
using namespace std;

template <class T>

T minimum(T a, T b)
{
    return (a < b) ? a : b;
}

int main()
{
    cout << minimum(45,32) << endl;

    cout << minimum(7.5,3.1) << endl;

    return 0;
}
```

### Output

```
32
3.1
```

---

## Advantages of Function Templates

- Code Reusability
- Generic Programming
- Less Duplicate Code
- Easy Maintenance
- Type Safe

---

# 2. Class Templates

## What is a Class Template?

A **Class Template** allows a class to work with different data types.

Instead of creating multiple classes for different data types, one template class can handle them all.

---

## Syntax

```cpp
template <class T>

class ClassName
{
    // members
};
```

---

## Example 1: Calculator Class

```cpp
#include <iostream>
using namespace std;

template <class T>

class Calculator
{
    T num1, num2;

public:

    Calculator(T a, T b)
    {
        num1 = a;
        num2 = b;
    }

    T add()
    {
        return num1 + num2;
    }
};

int main()
{
    Calculator<int> c1(20,30);

    Calculator<float> c2(2.5,4.3);

    cout << c1.add() << endl;

    cout << c2.add() << endl;

    return 0;
}
```

### Output

```
50
6.8
```

---

## Example 2: Generic Box

```cpp
#include <iostream>
using namespace std;

template <class T>

class Box
{
    T value;

public:

    void setValue(T x)
    {
        value = x;
    }

    T getValue()
    {
        return value;
    }
};

int main()
{
    Box<int> b1;

    b1.setValue(100);

    cout << b1.getValue() << endl;

    Box<string> b2;

    b2.setValue("Hello STL");

    cout << b2.getValue();

    return 0;
}
```

---

## Advantages of Class Templates

- Generic Classes
- Reusable Code
- Better Flexibility
- Easy Maintenance

---

# 3. Introduction to STL

## What is STL?

**STL** stands for **Standard Template Library**.

It provides ready-made classes and functions to simplify programming.

STL consists of:

- Containers
- Iterators
- Algorithms
- Function Objects

---

## STL Structure

```
              STL
       ___________________

      Containers
      Algorithms
      Iterators
      Function Objects
```

---

# 4. STL Containers

Containers store collections of data.

Some commonly used containers are:

- vector
- list
- map
- set
- queue
- stack
- deque

---

# 5. Vector

## What is a Vector?

A **Vector** is a dynamic array.

Its size automatically grows when new elements are added.

---

## Creating a Vector

```cpp
#include <iostream>
#include <vector>

using namespace std;

int main()
{
    vector<int> numbers;

    numbers.push_back(10);
    numbers.push_back(20);
    numbers.push_back(30);

    for(int n : numbers)
        cout << n << " ";

    return 0;
}
```

### Output

```
10 20 30
```

---

## Common Vector Functions

| Function | Description |
|----------|-------------|
| push_back() | Add element |
| pop_back() | Remove last element |
| size() | Number of elements |
| empty() | Checks if vector is empty |
| clear() | Removes all elements |
| front() | First element |
| back() | Last element |
| at() | Access by index |

---

## Example

```cpp
vector<int> v;

v.push_back(5);
v.push_back(10);
v.push_back(15);

cout << v.front() << endl;

cout << v.back() << endl;

cout << v.size();
```

---

# 6. List

## What is a List?

A List stores data using a **Doubly Linked List**.

Insertion and deletion are very fast.

---

## Example

```cpp
#include <iostream>
#include <list>

using namespace std;

int main()
{
    list<int> l;

    l.push_back(10);
    l.push_back(20);
    l.push_front(5);

    for(int x : l)
        cout << x << " ";

    return 0;
}
```

### Output

```
5 10 20
```

---

# 7. Map

## What is a Map?

A Map stores data as:

```
Key  ->  Value
```

Each key must be unique.

---

## Example

```cpp
#include <iostream>
#include <map>

using namespace std;

int main()
{
    map<int,string> student;

    student[101] = "Rahul";
    student[102] = "Aman";
    student[103] = "Priya";

    for(auto x : student)
    {
        cout << x.first << " " << x.second << endl;
    }

    return 0;
}
```

### Output

```
101 Rahul
102 Aman
103 Priya
```

---

# 8. Set

## What is a Set?

A Set stores only unique values.

Duplicate values are automatically removed.

The data is stored in sorted order.

---

## Example

```cpp
#include <iostream>
#include <set>

using namespace std;

int main()
{
    set<int> s;

    s.insert(50);
    s.insert(20);
    s.insert(10);
    s.insert(20);

    for(int x : s)
        cout << x << " ";

    return 0;
}
```

### Output

```
10 20 50
```

---

# 9. Iterators

## What is an Iterator?

An Iterator is used to traverse elements of a container.

It works like a pointer.

---

## Example

```cpp
#include <iostream>
#include <vector>

using namespace std;

int main()
{
    vector<int> v = {10,20,30,40};

    vector<int>::iterator it;

    for(it = v.begin(); it != v.end(); it++)
    {
        cout << *it << " ";
    }

    return 0;
}
```

### Output

```
10 20 30 40
```

---

## Using auto

```cpp
for(auto it = v.begin(); it != v.end(); it++)
{
    cout << *it << " ";
}
```

---

# 10. STL Algorithms

Include:

```cpp
#include <algorithm>
```

---

## sort()

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main()
{
    vector<int> v = {50,10,30,20};

    sort(v.begin(),v.end());

    for(int x : v)
        cout << x << " ";

    return 0;
}
```

### Output

```
10 20 30 50
```

---

## reverse()

```cpp
reverse(v.begin(),v.end());
```

---

## find()

```cpp
auto it = find(v.begin(),v.end(),30);

if(it != v.end())
    cout << "Found";
else
    cout << "Not Found";
```

---

## count()

```cpp
vector<int> v = {1,2,3,2,4,2};

cout << count(v.begin(),v.end(),2);
```

### Output

```
3
```

---

## max_element()

```cpp
cout << *max_element(v.begin(),v.end());
```

---

## min_element()

```cpp
cout << *min_element(v.begin(),v.end());
```

---

# Real-World Example

## Student Marks Analysis

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main()
{
    vector<int> marks = {78,65,92,84,55};

    sort(marks.begin(),marks.end());

    cout << "Highest = "
         << *max_element(marks.begin(),marks.end())
         << endl;

    cout << "Lowest = "
         << *min_element(marks.begin(),marks.end());

    return 0;
}
```

### Output

```
Highest = 92
Lowest = 55
```

---

# Summary

- Templates make programs generic.
- Function Templates work with functions.
- Class Templates work with classes.
- STL provides reusable data structures and algorithms.
- Vector is a dynamic array.
- List is a linked list.
- Map stores key-value pairs.
- Set stores unique values.
- Iterators traverse containers.
- Algorithms simplify programming.

---

# Interview Questions

1. What is a Template?
2. Difference between Function Template and Class Template?
3. What is STL?
4. Name the four components of STL.
5. What is a Vector?
6. Difference between Vector and List?
7. Difference between Map and Set?
8. What is an Iterator?
9. Difference between begin() and end()?
10. What are STL Algorithms?
11. Explain sort(), find(), reverse(), and count().
12. What is the advantage of generic programming?

---

# Practice Programs

1. Write a Function Template to swap two numbers.
2. Create a Class Template to calculate the larger of two values.
3. Store employee IDs in a vector.
4. Store city names in a list.
5. Create a student record using a map.
6. Store unique numbers using a set.
7. Sort a vector of marks.
8. Find the maximum element in a vector.
9. Count duplicate values using count().
10. Reverse a vector using reverse().

---

# Practice Exercises

## Easy

1. Create a template function for multiplication.
2. Create a vector containing 10 integers.
3. Print vector elements using iterators.
4. Store five names in a list.
5. Store five unique numbers in a set.

---

## Medium

6. Create a map of employee IDs and names.
7. Sort student marks in ascending order.
8. Reverse a vector.
9. Find an element using find().
10. Count duplicate values using count().

---

## Advanced

11. Create a generic Stack class using templates.
12. Create a generic Box class.
13. Read student marks and display highest and lowest marks.
14. Create a Phone Book using map.
15. Build a Student Management System using vector, map, iterators, and STL algorithms.
