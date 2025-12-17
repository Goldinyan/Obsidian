Date: 2025-12-17
Tags: {
#W 
[[%C]]
[[%Basics]]
[[%Computer Science]]
}

# Basics - C

### Basic Types

- **int**  
  Integer type. Size depends on the platform (commonly 4 bytes).
  ```c
  int a = 42;
  ```

- **float**  
  Single‑precision floating point number (commonly 4 bytes).  
  ```c
  float b = 3.14f;
  ```

- **char**  
  Single character, stored internally as an integer (1 byte).  
  ```c
  char c = 'A';
  ```

- **char\***  
  Pointer to a character, often used for strings (arrays of characters).  
  ```c
  char *str = "Hello";
  ```

---

## Structs
Structs group different data types under one name.  
```c
struct Point {
    int x;
    int y;
};

struct Point p1 = {10, 20};
```
- Access fields with `.`  
- Useful for modeling complex data.

---

## Enums
Enums define named integer constants.  
```c
enum Color {
    RED,
    GREEN,
    BLUE
};

enum Color c = GREEN;
```
- Values start at 0 by default and increase by 1.  
- You can assign custom values:  
  ```c
  enum Status { OK = 200, ERROR = 500 };
  ```

---

## Pointers
Pointers store memory addresses.  
```c
int x = 5;
int *ptr = &x;   // ptr points to x

printf("Address of x = %p\n", (void*)&x); 
```
- `*ptr` dereferences the pointer to get the value.  
- Central for memory management and arrays.

---

## Arrays
Collections of elements of the same type.  
```c
int arr[3] = {1, 2, 3};
```
- Access with indices: `arr[0]`.  
- `char[]` is often used for strings.

---

## Functions
Functions encapsulate reusable code.  
```c
int add(int a, int b) {
    return a + b;
}
```




# References