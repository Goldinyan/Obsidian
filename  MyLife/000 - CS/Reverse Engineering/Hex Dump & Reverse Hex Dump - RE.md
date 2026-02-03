Date: 2025-12-21
Tags: {
#F 
[[%Reverse Engineering]]
[[%Cyber Security]]
[[%Binary]]
[[%LowLevel]]
}


# Hex Dump & Reverse Hex Dump


##  What a Hex Dump Is  

A hex dump is a readable representation of the raw bytes inside a file or memory region.  
Each byte is shown as a two‑digit hexadecimal value, often with an ASCII preview on the right.

Example:
```
48 65 6C 6C 6F   Hello
```

Hex dumps are used for:
- Reverse engineering  
- Debugging  
- Inspecting binary formats (ELF, PE, etc.)  
- Finding strings or patterns  
- Understanding machine instructions  

---

## What Reversing a Hex Dump Means  
Reversing a hex dump converts the **textual hex representation back into the original binary file**.

Example:
```
48 65 6C 6C 6F  →  Hello
```

This is useful when:
- You patch a binary at the byte level  
- You edit a hex dump manually  
- You receive binary data encoded as hex  
- You rebuild modified crackme binaries  


## Using `xxd` on macOS  

macOS includes `xxd` by default.

### Create a hex dump:
```
xxd file.bin > dump.hex
```

### Reverse a hex dump:
```
xxd -r dump.hex > restored.bin
```

### Reverse plain hex (no offsets, no ASCII):
```
xxd -r -p hex.txt > out.bin
```

---

## Hex Editing in Vim  
Switch to hex view:
```
:%!xxd
```

Return to binary:
```
:%!xxd -r
```

---

## Why This Matters for Reverse Engineering  

Hex dumps let you inspect:
- ELF headers  
- Magic numbers  
- String tables  
- Instruction bytes  
- Padding and alignment  

Reversing a hex dump lets you patch binaries safely and precisely.

# References