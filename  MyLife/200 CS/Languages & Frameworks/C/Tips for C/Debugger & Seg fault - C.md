Date: 2026-01-02
Tags: {
#W
[[%Memory]]
[[%C]]
[[%Debugging]]
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

0 - 100
|-----------------------------------------------------------|

Your exe code gets loaded into memory somewhere, lets say 15, and whenever you call a memory allocation function like malloc().

```c
int *int_array = malloc(1024);
```

Underneath, the OS will map the memory you asked for somewhere into that virtual address space, for example from 60 to 80. If you try to write to an adress inside that allocated space, everything works fine. If you try to access memory outside of those mapped regions, for example 33 or 92, you will get a segmentation fault. 
This explains greatly, why writing to a null pointer throws a seg fault:

```c
int *int_array = NULL;
intArray[0] = 50; // seg fault
```

Although this is just one way to throw a seg fault in C, there is also 
- accessing array out of bounds,
- messing up pointer arithmetic
- or freeing memory then using it again
- ...

More is available in [[Ways for Seg faults - C]]

When writing code, that causes a seg fault and then compiling it, you will get this:

*segmentation fault*

No line number, no explantation, no idea of what caused the crash

Thats where [[lldb Command - RE]], comes into play also for debgging your own projects.


# Memory Corruption 

There are not many things more scary than  a seg fault, but memory corruption is one of them. Seg faults occur when accessing memory, which is outside of allocated memory, mapped memory created into your virtual address space by the operating system.

Sometimes instead of accessing memory outside of allocated area, you access memory of some other valid part of your program. This wont call a seg fault, because its technically a valid memory adress, but it will access memory, it shouldn't. Trust me, this is ***horror***. Its very hard to diagnose. 

Luckily there are tools for this, which is called [[Address Sanitisation - C]].


# References