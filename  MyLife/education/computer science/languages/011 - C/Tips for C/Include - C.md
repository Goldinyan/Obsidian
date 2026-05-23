Date: 2026-01-02
Tags: {
#F 
[[%C]]
[[%Structure]]
}


# Include - C


Include just pasts the code from the file in the file where it is included, you could just include a json and it would just paste it in there, it wouldnt compile but still 


they can include variables 


**file.h**
```c
int global_variable = 5;
```

But lets say two indepent files include this *file.h*, one could end up with duplicate symbols, function definitions or even global variables.

Of course there are tricks and tool sets or even techniques, which help, but if one would not want use these, there is the ability to use *single translation unit*, also known as *unity build*.

## Unity build

This works by not compiling all C-Files separately, using headers to expose function prototypes and linking them all together, instead you just include all files *in order* at the top of your main file.

```c
// main.c
include "file2.c"
include "file3.c"
```

All functions and symbols are available for you to access at any time. Allowing to make a single call to the compiler and thats it.
# References