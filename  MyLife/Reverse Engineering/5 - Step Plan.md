When we do it, we always want to answer a question about this programm and with the ability of [[Hex Dump & Reverse Hex Dump]] we can get more view of the actual programm.

Also with the [[Strings Command - RE]]  gives us a much better insight in what is actually happening, it gives all ASCII printed, human readable text, which might reveal the underlying functionality of the programm.

The underlying question is, what does this programm do?

When a person writes code at the end of the day, error codes, names of source files, certain meta data is left behind in the programm. We, as reverse Engineers can look at this and infer what did the human mean to do when he wrote this programm 


If this doesn't get you enough we can do the next step

## Static Analysis 

The art is taking the programm you have questions about and going deep into the code, going into the binary and asm to figure out what it should do.

For this we need a software which allows us to see and use the assembly code, and understand what the machine instructions are, what did the cpu get told to do?
We can do this by doing [[objdump Command - RE]], which gives us every machine instruction byte by byte, this of course isn't really human readable, but it would be possible.
It gives us the ASM Instructions for the cpu, when something is compiled we can only get the binary which can be ran, then we are only left with the assembly. Now the RE has to infer the intention out of the assembly and think what could be the C Instruction. This view is pretty bad, luckily software like Ghidra give us a a very clean graph view of all the instructions. They help us with lifting the hard-to-read asm up and showing us Pseudo-C, a representation on what the C code could look like from the asm.