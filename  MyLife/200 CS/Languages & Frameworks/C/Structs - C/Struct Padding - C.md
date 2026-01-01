Date: 2025-12-20
Tags: {
#W
[[%C]]
[[%Computer Science]]
[[%Structs]]
}


# Struct Padding - C






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



# References