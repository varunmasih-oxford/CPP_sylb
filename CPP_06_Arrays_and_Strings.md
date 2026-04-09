# CPP 06 Arrays and Strings

- Introduction to Arrays
- Single and Multi-dimensional Arrays
- Passing Arrays to Functions
- C-Style Strings
- String Functions (strlen, strcpy, strcat, strcmp, etc.)
- Using std::string Class

# CPP 06: Arrays and Strings

## 1. Introduction to Arrays
An **array** is a collection of elements of the same data type stored in contiguous memory locations.

### Example:
```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[5] = {10, 20, 30, 40, 50};

    for(int i = 0; i < 5; i++) {
        cout << arr[i] << " ";
    }
    return 0;
}
````

**Output:**

```
10 20 30 40 50
```

---

## 2. Single and Multi-dimensional Arrays

### (a) Single-Dimensional Array

```cpp
int arr[3] = {1, 2, 3};
```

### (b) Multi-Dimensional Array (2D Array)

```cpp
#include <iostream>
using namespace std;

int main() {
    int matrix[2][3] = {
        {1, 2, 3},
        {4, 5, 6}
    };

    for(int i = 0; i < 2; i++) {
        for(int j = 0; j < 3; j++) {
            cout << matrix[i][j] << " ";
        }
        cout << endl;
    }
    return 0;
}
```

**Output:**

```
1 2 3
4 5 6
```

---

## 3. Passing Arrays to Functions

Arrays are passed by reference (address) by default.

### Example:

```cpp
#include <iostream>
using namespace std;

void printArray(int arr[], int size) {
    for(int i = 0; i < size; i++) {
        cout << arr[i] << " ";
    }
}

int main() {
    int arr[4] = {5, 10, 15, 20};
    printArray(arr, 4);
    return 0;
}
```

---

## 4. C-Style Strings

C-style strings are arrays of characters ending with `'\0'` (null character).

### Example:

```cpp
#include <iostream>
using namespace std;

int main() {
    char str[] = "Hello";

    cout << str;
    return 0;
}
```

---

## 5. String Functions (`<cstring>`)

Include:

```cpp
#include <cstring>
```

### (a) strlen() – length of string

```cpp
char str[] = "Hello";
cout << strlen(str);   // Output: 5
```

### (b) strcpy() – copy string

```cpp
char src[] = "Hello";
char dest[10];

strcpy(dest, src);
cout << dest;
```

### (c) strcat() – concatenate strings

```cpp
char str1[20] = "Hello ";
char str2[] = "World";

strcat(str1, str2);
cout << str1;   // Hello World
```

### (d) strcmp() – compare strings

```cpp
char str1[] = "apple";
char str2[] = "banana";

cout << strcmp(str1, str2);
```

**Output Meaning:**

* `0` → equal
* `<0` → str1 < str2
* `>0` → str1 > str2

---

## 6. Using `std::string` Class

Modern C++ uses `string`, which is easier and safer.

### Example:

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string str1 = "Hello";
    string str2 = "World";

    // Concatenation
    string result = str1 + " " + str2;
    cout << result << endl;

    // Length
    cout << str1.length() << endl;

    // Access character
    cout << str1[0] << endl;

    return 0;
}
```

---

## Common `std::string` Functions

| Function  | Description       |
| --------- | ----------------- |
| length()  | Returns length    |
| append()  | Adds string       |
| +         | Concatenation     |
| compare() | Compare strings   |
| substr()  | Extract substring |

### Example:

```cpp
string s = "Programming";

cout << s.substr(0, 6);  // Progra
```

---

## Key Differences: C-String vs `std::string`

| Feature     | C-String   | std::string |
| ----------- | ---------- | ----------- |
| Ease of use | Hard       | Easy        |
| Safety      | Less safe  | Safer       |
| Functions   | Manual     | Built-in    |
| Flexibility | Fixed size | Dynamic     |

---

## Summary

* Arrays store multiple values of the same type.
* Multi-dimensional arrays are like tables (rows and columns).
* Arrays passed to functions behave like pointers.
* C-style strings use `char[]` and `'\0'`.
* `<cstring>` provides string functions.
* `std::string` is modern, safer, and recommended.

