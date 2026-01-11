Date: 2026-01-11
Tags: {
#W
[[%C]]
[[%Pointers]]
[[%Arithmetic]]
}

# Pointer Arithmetic - C

Lets say we define a struct:

```c
typedef struct Person {
	char name[64];
	int age;
} person_t
```

And we define an array of them, and then a pointer pointing to the address of the base of people, so people[0].

```c
	person_t people[100]; 
	persont_t *p_person = &people 
	// people[0]
	```

If we would want to iterate over all people, most would do this:

```c
for(int i = 0; i < 100; i++){
	p_person->age = 0;
		
	p_person += sizeof(person_t)
}
```

Makes sense, right?
We increase by the size of the struct person to get to the new index.
*This will crash your program, instantly.*

The compiler know what you are talking about, and what you wanna do. So when doing `+= sizeof(person_t)`, we don‘t increase once by the size of the struct, we actually multiply it.

Right would be:
```c
for(int i = 0; i < 100; i++){
	p_person->age = 0;
		
	p_person += 1;
		
	// or
		
	p_person++;
}
```
The compiler knows what we are talking about, and then its enough to increment by 1.

# References