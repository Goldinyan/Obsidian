
# **Directory Structure**

```
project/
│
├── include/
│   └── *.h
│
├── src/
│   └── *.c
│
├── Makefile
├── compile_flags.txt
└── .clangd
```

---

# **Makefile**

```Makefile
CC = gcc
CFLAGS = -Wall -Wextra -std=c11 -Iinclude

SRC = $(wildcard src/*.c)
OBJ = $(SRC:.c=.o)

TARGET = program

all: $(TARGET)

$(TARGET): $(OBJ)
	$(CC) $(OBJ) -o $(TARGET)

src/%.o: src/%.c
	$(CC) $(CFLAGS) -c $< -o $@

clean:
	rm -f src/*.o $(TARGET)
```

---

# **compile_flags.txt**

```
-Iinclude
-std=c11
```

---

# **.clangd**

```
CompileFlags:
  Add: [-Iinclude, -std=c11]
```

---

# **Header Template (include/module.h)**

```c
#ifndef MODULE_H
#define MODULE_H

void module_function(void);

#endif
```

---

# **Source Template (src/module.c)**

```c
#include "module.h"

void module_function(void) {
}
```

---

# **main.c Template**

```c
#include <stdio.h>
#include "module.h"

int main(void) {
    module_function();
    return 0;
}
```
