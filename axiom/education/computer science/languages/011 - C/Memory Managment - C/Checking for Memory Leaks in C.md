## Checking for Memory Leaks in C
 

To check for ongoing Memory-Leaks in a program, you first have to 
enable `-fsanitize=address` while compiling.

This command allows for an overview of the programs memory leaks.

```bash
> leaks --atExit -- ./main
```

This could be an optional output

```bash
main(79259) MallocStackLogging: could not tag MSL-related memory as no_footprint, so those pages will be in
cluded in process footprint - (null)
main(79259) MallocStackLogging: recording malloc (and VM allocation) stacks using lite mode
Vector initialized with capacity 10 and element size 8
 Vector destroyed
Process 79259 is not debuggable. Due to security restrictions, leaks can only show or save contents of read
only memory of restricted processes.

Process:         main [79259]
Path:            /Users/USER/Desktop/*/main
Load Address:    0x1020c8000
Identifier:      main
Version:         0
Code Type:       ARM64
Platform:        macOS
Parent Process:  leaks [79258]
Target Type:     live task

Date/Time:       2026-02-17 14:33:35.998 +0100
Launch Time:     2026-02-17 14:33:35.489 +0100
OS Version:      macOS 15.6.1 (24G90)
Report Version:  7
Analysis Tool:   /usr/bin/leaks

Physical footprint:         2177K
Physical footprint (peak):  2177K
Idle exit:                  untracked
----

leaks Report Version: 4.0, multi-line stacks
Process 79259: 185 nodes malloced for 14 KB
Process 79259: 0 leaks for 0 total leaked bytes.
```
