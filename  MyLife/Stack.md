

```C
int foo() {
	int x = 1;
	int y = 1;
	printf("I'm in foo rwar xd\n");
	
	return x + y;
}

int main(){
	printf("tehee I'm in main\n");
	int z = foo();
}
```

Every function that is not naked, which is true by default, will create its own stack frame.

What does a stack frame do:

It creates room for local variables, like for variable z. When calling function `foo()`, the assembly instructions under the hood are going to create a new stack frame for `foo()`, to create room for these local variables. 
In here we will disassemble this programm and we're going to walk step by step, to talk about how a stack frame is created. 
Before that we have to understand basics of the cpu, to understand what is going on in the creation of a stack frame. 

Inside the cpu, there are hyper fast variables, called registers, with some being GP (general purpose registers), where they can contain any kind of data. 
One of them is `ebx`, extended `bx`, in which we can put any data we want, which serves no purpose to the CPU other than genereal purpose.
There are also others, names special purpose registers, one of them being `esp`(extended stack pointer), which points to the top of our stack frame.
Furthermore there is also `ebp`, which points to the bottom of our stack frame. 

```markdown
CPU

gp -> ebx 
// can contain any kind of data

esp -> top # s -> top
// points to the top of the stack frame

ebp -> bottom # b -> bottom
// points to the bottom of the stack frame

```

Now when talking about the stack, one can imagine a stack of plates, when we push additional variables onto the stack, sp will go up, because we push additional plates higher and higher onto the stack 
Its important to understand, as sp goes up, the values becomes more negative, which also means, the more negative sp is, the taller our stack is. 

###### When we push something on the stack, sp goes up, the value becoming more negative, meaning our stack grows up negatively.

All while SP is going up, in this case we have BP, keeping track of the bottom of our stack frame.

### What even is a "Stack Frame"

In the code snippet we have two functions `main()`and `foo()`, but before `main()`actually called `foo()`, it already had a stack frame established.
You can picture it as a box, in which ESP points to the top of the box, and EBP points to the bottom of the stack. 
This box is referred as Main's stack frame, this contains stuff like argc and argv, all the variables that are in scope relative to main.
When calling `foo()`, what really happens, we go through a process of the function `foo()`creating a new stack frame, a box, that is now above the stack frame of  `main`, the box of `main`.
So eventually `foo()`will create a stack frame, with its own local variables, like `int x`and `int y`.
When the stack frame of `foo()`collapses, the `main`stack frame is now the stack frame in scope again. 





Now we will look at the asm instructions and work out what and when the instructions are passed, which lead to more room being on the stack, that are in scope to the function `foo()`.

###### It creates the room for `foo()'s` variables, it can do things with those variables and eventually it will call the function prologue, collapsing the stack and getting rid of that room and get back to the state, where `main()'s` stack frame is in scope again. 

```asm
endbr32
push ebp 
mov ebp,esp
push ebx
sub esp,0x14
call 8049dd4
```

```asm
push ebp
```
First were going to push EBP, the old base pointer, creating a new box ontop, right now bp points to the bottom of the main stack frame, we have to preserve that, so we can put it back to bp once the function is over.

```asm
mov ebp, esp
```
We move EBP i




















































































# Stack in C

## Eigenschaften
- Automatische Speicherverwaltung
- LIFO-Prinzip (Last In, First Out)
- Sehr schneller Zugriff (contiguous memory)
- Wird für:
  - lokale Variablen
  - Funktionsaufrufe
  - Rücksprungadressen
  - Parameterübergabe
  genutzt

## Lebensdauer
- Variablen existieren nur innerhalb ihres Scopes
- Speicher wird beim Verlassen des Blocks automatisch freigegeben

## Typische Fehler
- Rückgabe von Zeigern auf lokale Variablen → **undefiniertes Verhalten**
- Zu tiefe Rekursion → **Stack Overflow**

## Beispiel
```c
void foo() {
    int x = 10; // liegt auf dem Stack
} // x ist hier ungültig
```

## Merksatz
Stack = schnell, automatisch, begrenzt, scope‑gebunden.





