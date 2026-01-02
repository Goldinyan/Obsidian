Date: 2026-01-02
Tags: {
#W
}


# Debugger - C

If used to a modern scripting language, that features a garbage collector and Interpreter, you. might come to the conclusion, you can just use print statements to do my debugging. *That will work fine... right?....*

```c
int main(void) {
	// more code
	printf("got here");
	
	// more code
	printf("got here 2");
	
}
```
This *will not* work in C, to stay productive or, more importantly, happy, you will need a debugger. Even if you never coded in C, you definently heard of the term called: *segmentation fault*, short *seg fault*.

When the programm starts, your operating system assigns your programm a very large virtual address space that starts off completely empty, and all pointers are just indexes into this address space.

Lets just label these adresses from 0 to 100 for the simplicity:

0 _______________________________________________100
|-----------------------------------------------------------|


# References