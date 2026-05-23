Date: 2025-12-20
Tags: {
#W
[[%C]]
[[%Structs]]
[[%Computer Science]]
}


# Initializing Structs - C

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

