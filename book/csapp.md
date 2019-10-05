## CSAPP
### Basic
**The compilation system** : Programs Are Translated by Other Programs into Different Forms
- Preprocessor
- Compiler
- Assembler
- Linker
**Hardware Organization of a System**
- Buses
- I/O Devices
- Main Memory
- Processor
**Storage Devices Form a Hierarchy**
Regs - > L1 -> L2 -> L3 -> Main Memory -> Local secondary storage -> Remote secondary storage
*L1_L3 SRAM, MM(DRAM)*
**The Operating System Manages the Hardware**
- Processes
- Threads
- Virtual Memory
- Files
> This is the major insight of Amdahl's law - to significantly speed up the entire system, we must improve the speed of a very large fraction of the overall system.

```mathjax
T_{new} = (1- \alpha) T_{old} + (\alpha T_{old}) / k \\
S = \frac 1  {(1-\alpha) + \alpha / k }
```
Practice Problem done at September 19th
**Concurrency and Parallelism**
- Thread-Level Concurrency
- Instruction-Level Parallelism
- Single-Instruction, Multiple-Data(SIMD) Parallelism
- The Importance of Abstractions in Computer Systems
### Part 1: Program Structure and Execution
> Our exploration of computer systems starts by studying the computer itself, comprising a processor and a memory subsystem.

#### Representing and Manipulating Information
*Unsigned* encodings | *Two's-complement* encodings | *Floating-point* encodings
```c
printf("%d\n", 200 * 300 * 400 * 500) // -884901888
```