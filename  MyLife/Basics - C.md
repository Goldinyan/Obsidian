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
  Single character, stored internally as an integer (1 byte).  (Single Qoutes 'A')
  ```c
  char c = 'A';
  ```

- **char\***  
  Pointer to a character, often used for strings (arrays of characters).  (Double Qoutes "")
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
// Address of x = 0x7ffee3b2c8ac
```

- `*ptr` dereferences the pointer to get the value.  
- Central for memory management and arrays.
- adress of x → &x or ptr
- Value of x → x or *ptr (with star)

---

## Arrays

```c
int arr[3] = {1, 2, 3};
```
- Access with indices: `arr[0]`.  
- `char[]` is often used for strings.

---

## Functions

```c
float add(int a, int b) {
    return (float)(a + b); //cast to float
}
```

---

## Void

```c
int getInteger(void){
	return 42; 
	//takes nothing, no value 
	//btw null is a value
}

void printIntenger(int x){
	printf("this is an int %d", x)
	//returnes no value
}
```

## Array Length & Pointer

```c
int main(void) {

  int nums[5] = {4, 7, 10, 3, 6};
  int length = sizeof(nums) / sizeof(nums[0]);
  
  return 0;
}

float getAverage(int arr[], int lenght){
  int sum = 0;
  for(int i; i < lenght; i++){
    sum += arr[i];
  }
  return (float)sum / lenght;
}
```


`sizeof(nums)` gives the total number of bytes of the array, while `sizeof(nums[0])` gives the size of a single element. Dividing the two yields the element count. When you pass an array to a function, it decays into a pointer, so the compiler no longer knows its length. That is why you must pass the length as a separate parameter. Inside a function like `foo(int *arr)`, the parameter is just a pointer, and `sizeof(arr)` only returns the size of the pointer itself, for example 8 bytes on a 64‑bit system, not the size of the original array. 

```c
int arr[5] = {1,2,3,4,5};
int *p = arr

// *p = (1)
// *(p + 1) = 2
```
A pointer in C knows the address it points to and lets you read or write the value there, but it does not store the length of the memory block. Arrays in their own scope carry size information through `sizeof`, but once passed to a function they decay into pointers, and `sizeof` then only returns the size of the pointer itself. That’s why the array length must always be tracked or passed separately.

## Math Operators

```c
x + y
x - y
x * y
x / y

x++; // x += 1
x--; // x -=1

int x = 5
y = x++ // y is as
```
## Format Specifiers

%d - int (digit)
%c - chars
%f - float
%s- string (char *)

\n -> prints new Line

```c
printf("Hello, %s. You're %d years old. \n", name, age)
```

### constants

```c 
int main(){
	int x = 5;
	x = 10; // this is OK
}
```

```c
int main(){
	const int x = 5;
	x = 10; // ERROR
}
```

# References