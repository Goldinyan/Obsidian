Date: 2025-12-20
Tags: {
#W 
[[%C]]
[[%Structs]]
[[%Computer Science]]
}


# Basic Structs - C

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

