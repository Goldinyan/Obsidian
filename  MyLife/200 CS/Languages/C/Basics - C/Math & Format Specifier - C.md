Date: 2025-12-20
Tags: {
#W
[[%C]]
[[%Basics]]
[[%Computer Science]]
}





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
%f - double

\n -> prints new Line

```c
printf("Hello, %s. You're %d years old. \n", name, age)
```
