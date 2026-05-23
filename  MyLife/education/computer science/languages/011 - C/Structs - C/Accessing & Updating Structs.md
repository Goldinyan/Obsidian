Date: 2025-12-17
Tags: {
#W
[[%C]]
[[%Computer Science]]
[[%Structs]]
}


# Accessing & Updating Structs & TypeDef


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

