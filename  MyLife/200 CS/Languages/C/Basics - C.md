Date: 2025-12-17
Tags: {
#W 
[[%C]]
[[%Basics]]
[[%Computer Science]]
}

# Basics - C

### Basic Types


>The actual size of these can vary between different computers, (32-Bit, 64-Bit, etc) , but can be determinted using *sizeof()* in C.

```c
printf("sizeof(char) = %zu\n", sizeof(char));
```

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

- **double**
	Double-Precision floating point number (8 bytes)
	```c
	double d = 2.31233;
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
- Have no behaviour like classes. (Inheritance or Methods)
- just data
- Access fields with *.* or if its a pointer with the *->* operator
- Useful for modeling complex data.

The order matters! 
We tell C to make this data and place it next to each other in Memory and operate on them via struct. 

name | age | isAlive

Like a block, and this can be bigger or smaller depending on the order.
Everything is stored in Bytes, 0's and 1's and in C we tell the computer which data we want to save where in memory and what we want to do with them. C doesn't know about Capsulation or Methods or any other stuff.


### Initializer

```c
struct City {
	char *name;
	int lat;
	int lon;
}
```

### Zero Initialiter

```c
int main(void){
	struct City c = {0};
	return 0;
}
```

Sets all Fields to value 0!

## Position Initializer 

```c 
int main(void) {
	struct City c = {"Berlin", 73, -122}; 
	return 0;
}
```

### Designed Initializer

```c
int main(void){
	struct City c = {
		.name = "Berlin",
		.lat = 73,
		.lot = -122
	}
	return 0;
}
```

My preferred way, because its easy to understand and if they fields change you don‘t have to worry about the ordering.


### Accessing Fields 

Normal way

```c
struct City c;
c.lat = 73; //Setting value
printf("%d\n", c.lat);
```

If it is a pointer then:






### Updating Structs

```c
struct Coordinate {
	int x;
	int y;
	int z;
};

struct Coordinate scaleCoord(struct Coordinate c, int scale) {
	struct Coordinate scaled = {
	.x = c.x * scale,
	.y = c.y * scale,
	.z = c.z * scale,
	};
	
	return scaled;
}
```


### Typedef

Why does one have to wait struct Coordinate everytime, can‘t this be easier? Yes of course. Coordinate is not a type, its struct coordinate is a type so what we can do is this with typedef:

```c
typedef struct Pastry {
	char *name;
	float weight;
} pastry_t //_t indicator for type

//This now makes a type called: pastry_t

//Now we don‘t have to do this:


struct Pastry newPastry(char *name, float weight){}

//instead we can do this:

pastry_t newPastry(char *name, float weight){}

```

### sizeof

Structs are like a way to talk about or name different 
relative locations within a block of memory.
We know an int is 4 Bytes and if we have a struct with 3 ints (x, y, z), then sizeof(struct) will return 12 Bytes.

Important is to not forget padding, if there is a struct for example: 

```c
typedef struct Human {
	char firstIntial;
	int age;
	doouble height;
} 
```

A char is 1 Byte, int is 4 Bytes and double is 8 Bytes, and because its faster for the computer to access age when its on a 4 Byte aligned address than it would be on the 1 of char, so it gives char 3 Bytes of padding to be faster. So sizeof(struct) involves the padding so it isn't always exactly the sum of sizeof all his values.
It alway wants a multiple of the highest Byte value.


Without padding this:     (every v is 1 Byte)

   char   age      height 
	v | v v v v | v v v v v v v v  

then with padding:

  char  padding   age          height
	v | v v v | v v v v | v v v v v v v v 


#### Struct Padding

A easy go to role is from largest to smallest, but thinking about it is best for perfomance.
It alway wants a multiple of the highest Byte value.

```c
typedef struct x {
	char a; // 1 B
	double b; // 8 B
	char c // 1 B
	char d // 1 B
	long e // 4 B
	char f // 1 B
} poorlyAssigned_t;

typedef struct y {
	double b; // 8 B
	long e // 4 B
	char a; // 1 B
	char c // 1 B
	char d // 1 B
	char f // 1 B
}
```

### Example Code for Structs 

```c
struct Coordinate {
	int x;
	int y;
	int z;
}

struct Coordinate newCoord(int x, int y, int z) {
	struct Coordinate c = {
	.x = x,
	.y = y,
	.z = z,
	}
	return c;
} // returns a new Coordinate
```













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

//there can also be one line Functions

if(x > 10) return ERROR;

//is the same as

if(x > 10){
	return ERROR;
}
```

---

## Loops

```c

for(int i = 0; i < 5; i++){
	printf("%d\n", i);
}

int i = 0
while(i < 5){
	printf("%d\n", i);
	i++;
}

int y = 0
do{
	printf("%d\n", i);
	y++;
}while(y < 5)

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

// PREFIX (before)

int x = 5;
y = x++; // y is assigned first and then 
		 // x is added 1, like in Java so
		 // y = 5, x = 6
		
// POSTFIX (after)

int x = 5;
y = ++x; // x is added before and then 
		 // being assigned to y, so
		 // x = 6, y = 6
		
```
## Format Specifiers

%d - int (digit)
%c - chars
%f - float
%s - string (char *)
%zu - sizeof() -> is an operator not a function

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