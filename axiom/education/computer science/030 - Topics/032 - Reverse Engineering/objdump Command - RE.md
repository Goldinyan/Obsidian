Date: 2025-12-21
Tags: {
#F 
[[%Command]]
[[%Terminal]]
[[%Reverse Engineering]]
[[%Cyber Security]]
[[%Binary]]
[[%LowLevel]]
}

# objdump Command - RE

## Purpose  

`objdump` is a low‑level inspection tool for object files and executables.  
It can display assembly instructions, headers, sections, symbols, relocation entries, and more.  
It is essential for reverse engineering, binary analysis, and understanding how compiled programs are structured.

## Basic Usage  

```
objdump file
```

By default, this prints only minimal information. Most practical use comes from specific flags.

---

# Common and Important Options

## Disassemble the Entire Binary  

```
objdump -d file
```

Shows assembly instructions for all executable sections.  
Useful for examining compiled machine code.

## Disassemble with Source Code (if available)  

```
objdump -S file
```

Combines disassembly with interleaved source lines.  
Works only if the binary was compiled with debug information.

## Show All Information  

```
objdump -x file
```

Displays headers, section details, symbol tables, and more.  
Useful for understanding the structure of ELF or Mach‑O files.

(Doesn't work on Mac!)

## Show Symbols  

```
objdump -t file
```

Prints the symbol table.  
Shows function names, global variables, and addresses (if not stripped).

## Show Dynamic Symbols  

```
objdump -T file
```

Lists symbols used for dynamic linking.  
Useful for shared libraries and dynamically linked executables.

## Show Sections  

```
objdump -h file
```

Displays section headers, including offsets, sizes, and memory addresses.  
Helps identify where code, data, and strings are stored.

## Show Relocation Entries  

```
objdump -r file
```

Shows relocation information used by the linker.  
Useful for understanding how addresses are resolved.

## Show File Header  

```
objdump -f file
```

Displays architecture, entry point, and format information.

---

# Typical Reverse Engineering Workflow

1. Identify sections  

   ```
   objdump -h file
   ```
   
   Helps locate `.text`, `.data`, `.rodata`, and other relevant areas.

1. Inspect symbols  

   ```
   objdump -t file
   ```
   
   Reveals function names if the binary is not stripped.

2. Disassemble code  

   ```
   objdump -d file
   ```
   
   Allows examination of machine instructions.

3. Combine with source (if available)  

   ```
   objdump -S file
   ```
   
   Useful for debugging or analyzing your own compiled programs.

4. Examine dynamic behavior  

   ```
   objdump -T file
   ```
   
   Shows imported and exported symbols.

---

# Notes on Stripped Binaries  
If a binary is stripped, symbol names are removed.  
In that case:

- `objdump -t` shows almost nothing  
- `objdump -d` still works, but only raw addresses and assembly remain  
- No function names or labels are available  

This is common in crackmes and production binaries.

---

# Example  

```
objdump -d ./program
```

Disassembles the `.text` section and prints the assembly instructions with addresses and opcodes.

