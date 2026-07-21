Date: 2025-12-20
Tags: {
#W
[[%Cpu]]
[[%LowLevel]]
[[%Hardware]]
[[%Computer Science]]
}


# Basics - Cpu


Inside the CPU there are many very small storage locations called **registers**.  
Registers are **extremely fast memory** that the CPU uses directly when performing operations.

The **size (width)** of a register depends on the CPU architecture.  
On a **64-bit CPU**, general-purpose registers are **64 bits wide**, so they can hold 64-bit values and operate on 64-bit data.

Registers like **RDI, RSI, and R8** are **64-bit registers** on x86-64 systems.

### Important clarifications

• Registers are **not variables** — they _store_ values, but variables live in memory  
• Registers are **fixed in number**, unlike variables  
• A 64-bit register can also access smaller parts:

- `rax` → 64 bits
    
- `eax` → lower 32 bits
    
- `ax` → lower 16 bits
    
- `al` → lower 8 bits


# References