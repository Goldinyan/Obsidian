
C/Projects/dynamic_vector via C v17.0.0-clang 
❯ clang -fsanitize=address -g -O0 -o main.c main        
ld: unsupported mach-o filetype (only MH_OBJECT and MH_DYLIB can be linked) in 'main'
clang: error: linker command failed with exit code 1 (use -v to see invocation)

C/Projects/dynamic_vector 
❯ clang -fsanitize=address -g -O0 -o main main.c
clang: error: no such file or directory: 'main.c'
clang: error: no input files

C/Projects/dynamic_vector 
❯ clang -g  -o main main.c 
clang: error: no such file or directory: 'main.c'
clang: error: no input files

C/Projects/dynamic_vector 
❯ ls        
main

C/Projects/dynamic_vector 
❯ ls 
main    main.c

C/Projects/dynamic_vector via C v17.0.0-clang 
❯ clang -g  -o main main.c

C/Projects/dynamic_vector via C v17.0.0-clang 
❯ leaks --atExit -- ./main
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


C/Projects/dynamic_vector via C v17.0.0-clang 
❯ 
