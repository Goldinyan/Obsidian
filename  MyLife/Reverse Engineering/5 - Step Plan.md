When we do it, we always want to answer a question about this programm and with the ability of [[Hex Dump & Reverse Hex Dump]] we can get more view of the actual programm.

Also with the [[Strings Command - RE]]  gives us a much better insight in what is actually happening, it gives all ASCII printed, human readable text, which might reveal the underlying functionality of the programm.

The underlying question is, what does this programm do?

When a person writes code at the end of the day, error codes, names of source files, certain meta data is left behind in the programm. We, as reverse Engineers can look at this and infer what did the human mean to do when he wrote this programm 


If this doesn't get you enough we can do the next step

## Static Analysis 

The art is taking the programm you have questions about and going deep into the code, going into the binary and asm to figure out what it should do.

For this we need a software which allows us to see and use the assembly code, and understand what the machine instructions are, what did the cpu get told to do?
We can do this by doing [[objdump Command - RE]], which gives us every machine instruction byte by byte, this of course isn't really human readable, but it would be possible.
It gives us the ASM Instructions for the cpu, when something is compiled we can only get the binary which can be ran, then we are only left with the assembly. Now the RE has to infer the intention out of the assembly and think what could be the C Instruction. This view is pretty bad, luckily software like Ghidra give us a a very clean graph view of all the instructions. They help us with lifting the hard-to-read asm up and showing us Pseudo-C, a representation on what the C code could look like from the asm. This looks a little odd, but when actually trying to understand its acctually pretty easy.

```c
float _getAverage(long param_1,int param_2)

{
  undefined4 local_14;
  undefined4 local_10;
  
  local_10 = 0;
  for (; local_14 < param_2; local_14 = local_14 + 1) {
    local_10 = local_10 + *(int *)(param_1 + (long)local_14 * 4);
  }
  return (float)local_10 / (float)param_2;
}
```

This function looks very odd, but with help of the name `getAverage`and a little help we can turn this into its original form:

We can see that we are adding `local_10`up and then divide it so we can convert it into the name sum, `undefined4`is just an int,  and `local_14`isn't initialised but used in the for loop, so we can convert it to `i`, that gives us:

```c
float _getAverage(long param_1, int param_2)

{
  int i; 
  int sum;
  
  sum = 0;
  for (i = 0; i < param_2; i++) {
    sum = sum + *(int *)(param_1 + (long)i * 4);
  }
  return (float) sum / param_2;
}
```

The name gives us a hint, so it would make sense to, at the end, divide the sum by the length of the array we want the average of. That means `param_2`is going to be the length. The part where we add something to sum looks tricky but isn' t really. First `param_1`isn't a long, but Ghidra only sees a pointer, so he choose long to fit everything in it.

```c
// dekompiliert:
sum = sum + *(int *)(param_1 + (long)i * 4);

// 1) param_1 ist eigentlich ein int*-Pointer
int *arr = (int *)param_1;

// 2) (long)i * 4 = Byte-Offset für ein int (4 Bytes)
int *element_ptr = arr + i;   // Pointerarithmetik macht *4 automatisch

// 3) *(...) dereferenziert → arr[i]
int value = element_ptr[i - i]; // äquivalent zu *element_ptr

// oder einfach:
value = arr[i];
```

So this just becomes:

```c
float _getAverage(int[] arr, int length)

{
  int i; 
  int sum;
  
  sum = 0;
  for (i = 0; i < length; i++) {
    sum = sum + arr[i];
  }
  return (float) sum / length;
}
```

Easy, right?

# Dynamic analysis

This is watching the programm run life, observing its functionality in real time, so you wont just guess what it does in static analysis you will watch it perfomance in action 
