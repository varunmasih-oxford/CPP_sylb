# C++ Control Flow

## 1. Decision Making

### if Statement

Executes a block of code if condition is true.

```cpp
#include <iostream>
using namespace std;

int main() {
    int x = 10;

    if (x > 5) {
        cout << "x is greater than 5";
    }

    return 0;
}
```

### if-else Statement

```cpp
#include <iostream>
using namespace std;

int main() {
    int x = 3;

    if (x > 5) {
        cout << "Greater";
    } else {
        cout << "Smaller";
    }

    return 0;
}
```

### Nested if

```cpp
#include <iostream>
using namespace std;

int main() {
    int x = 10;

    if (x > 5) {
        if (x < 20) {
            cout << "x is between 5 and 20";
        }
    }

    return 0;
}
```

---

## 2. switch Statement

Used for multiple conditions.

```cpp
#include <iostream>
using namespace std;

int main() {
    int day = 2;

    switch (day) {
        case 1:
            cout << "Monday";
            break;
        case 2:
            cout << "Tuesday";
            break;
        case 3:
            cout << "Wednesday";
            break;
        default:
            cout << "Invalid day";
    }

    return 0;
}
```

---

## 3. Loops

### for Loop

Used when number of iterations is known.

```cpp
#include <iostream>
using namespace std;

int main() {
    for (int i = 1; i <= 5; i++) {
        cout << i << " ";
    }

    return 0;
}
```

### while Loop

```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 1;

    while (i <= 5) {
        cout << i << " ";
        i++;
    }

    return 0;
}
```

### do-while Loop

Executes at least once.

```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 1;

    do {
        cout << i << " ";
        i++;
    } while (i <= 5);

    return 0;
}
```

---

## 4. break and continue

### break

Terminates the loop.

```cpp
#include <iostream>
using namespace std;

int main() {
    for (int i = 1; i <= 5; i++) {
        if (i == 3)
            break;
        cout << i << " ";
    }

    return 0;
}
```

### continue

Skips current iteration.

```cpp
#include <iostream>
using namespace std;

int main() {
    for (int i = 1; i <= 5; i++) {
        if (i == 3)
            continue;
        cout << i << " ";
    }

    return 0;
}
```

---

## 5. goto Statement

Transfers control to a labeled statement.

```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 1;

start:
    if (i <= 5) {
        cout << i << " ";
        i++;
        goto start;
    }

    return 0;
}
```

---
