Date: 2025-12-20
Tags: {
#W 
[[%ASM]]
[[%LowLevel]]
[[%Computer Science]]
}


# Basics - ASM

Before we can work with assembly, we need a basic understanding of how the CPU operates.

With the registers explained in [[Basics - Cpu]], we can perform simple operations such as moving values.

```nasm
mov rdi, 8
```

This moves the constant value 8 into the register rdi.

```nasm
mov rdi, rsi
```

This moves the value currently stored in rsi into rdi.

Memory operations are equally important.

```nasm
mov rdi, qword ptr [rsi]
```

Here, the value in rsi is treated as a pointer. The instruction reads a qword (8 bytes) from the memory address stored in rsi and places that value into rdi.

The reverse operation is also possible.

```nasm
mov qword ptr [rsi], rdi
```

This stores the value in rdi into the memory location pointed to by rsi.

The first example loads data from memory into a register, which is a load operation. The second example writes data from a register into memory, which is a store operation.


# References

