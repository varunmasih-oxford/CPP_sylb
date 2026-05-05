# CPP 13: File Handling in C++

## 1. Introduction to File Streams

File handling in C++ is done using the **fstream library**.

### Header File:

```cpp
#include <fstream>
```

### File Stream Classes:

| Class      | Purpose        |
| ---------- | -------------- |
| `ifstream` | Read from file |
| `ofstream` | Write to file  |
| `fstream`  | Read + Write   |

---

### Basic Example:

```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    ofstream file("example.txt"); // Create & write

    file << "Hello File Handling!";
    file.close();

    return 0;
}
```

---

## 2. Reading and Writing Text Files

### A. Writing to a File

```cpp
#include <fstream>
using namespace std;

int main() {
    ofstream file("data.txt");

    file << "This is a test file.";
    file.close();
}
```

---

### B. Reading from a File

```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    ifstream file("data.txt");
    string line;

    while (getline(file, line)) {
        cout << line << endl;
    }

    file.close();
}
```

---

### C. Read & Write using `fstream`

```cpp
#include <fstream>
using namespace std;

int main() {
    fstream file("data.txt", ios::in | ios::out | ios::app);

    file << "\nNew Data Added";

    file.close();
}
```

---

## 3. File Modes and Pointers

### A. File Modes

| Mode          | Description             |
| ------------- | ----------------------- |
| `ios::in`     | Read mode               |
| `ios::out`    | Write mode              |
| `ios::app`    | Append mode             |
| `ios::ate`    | Move to end immediately |
| `ios::trunc`  | Delete old data         |
| `ios::binary` | Binary file mode        |

---

### Example with Modes:

```cpp
ofstream file("data.txt", ios::app);
file << "Appending new line";
file.close();
```

---

### B. File Pointers

There are two pointers:

| Pointer | Purpose          |
| ------- | ---------------- |
| `get`   | Reading position |
| `put`   | Writing position |

---

### Pointer Functions:

| Function  | Description        |
| --------- | ------------------ |
| `seekg()` | Move read pointer  |
| `seekp()` | Move write pointer |
| `tellg()` | Get read position  |
| `tellp()` | Get write position |

---

### Example:

```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    fstream file("data.txt", ios::in | ios::out);

    file.seekp(0, ios::end);
    file << "\nEnd Data";

    file.close();
}
```

---

## 4. Error Handling in File Operations

Handling errors is very important in file handling.

---

### A. Checking if File Opened Successfully

```cpp
ifstream file("data.txt");

if (!file) {
    cout << "Error opening file!";
}
```

---

### B. Using `.is_open()`

```cpp
if (file.is_open()) {
    cout << "File opened successfully";
} else {
    cout << "Failed to open file";
}
```

---

### C. Detecting End of File

```cpp
while (!file.eof()) {
    string line;
    getline(file, line);
    cout << line << endl;
}
```

---

### D. Handling Read Errors

```cpp
if (file.fail()) {
    cout << "Read error occurred!";
}
```

---

## Complete Example

```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    fstream file("data.txt", ios::out);

    if (!file) {
        cout << "Error creating file";
        return 1;
    }

    file << "Hello C++ File Handling";
    file.close();

    file.open("data.txt", ios::in);

    string line;
    while (getline(file, line)) {
        cout << line << endl;
    }

    file.close();
    return 0;
}
```

---

## Key Points to Remember

* Always `close()` files after use.
* Use correct file modes for operations.
* Check file status before reading/writing.
* Use `getline()` for full-line reading.
* Use file pointers for advanced operations.

