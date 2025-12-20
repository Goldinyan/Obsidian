Date: 2025-12-17
Tags: {
#W
[[%C]]
[[%Basics]]
[[%Computer Science]]
}


# Structs - C

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







# References