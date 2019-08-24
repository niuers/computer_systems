# Table of Contents
* [Intel Processor x86 History](#intel-processor-x86-history)
* [Programm Encodings](#programm-encodings)
* [](#)

> Machine Code: sequences of bytes encoding the low-level operations that manipulate data, manage memory, read and write data on storage devices, and communicate over networks.

* A compiler generates machine code through a series of stages, based on:
  * The rules of the programming language
  * The instruction set of the target machine
  * The conventions followed by the operating system

* Programmers seeking to maximize the performance of a critical section of code often try different variations of the source code, each time compiling and examining the generated assembly code to get a sense of how efficiently the program will run. 


* Python?

# Intel Processor x86 History
* The Intel processor line is colloquially referred to as x86. 
  * 8086 (1978, 29K transistors): 16-bit microprocessors. 
    * 8088 is a variant. 
    * 8087 established the floating-point model for the x86 line, often referred to as x87.
  * 80286 (1982, 134K transitors)
  * i386 (1985, 275K transistors): Expanded the architecture to 32bits. First machine that can fully support a UNIX operating system.
  * i486 (1989, 1.2M transistors)
  * Pentium (1993, 3.1M transistors)
  * PentiumPro (1995, 5.5M transistors): Introduced P6 microarchitecture
  * Pentium/MMX (1997, 4.5M transistors)
  * Pentium II (1997, 7 M transistors)
  * Pentium III (1999, 8.2M transistors): Introduced SSE, a class of instructions for manipulating vectors of integer or floating-point data.
  * Pentium 4 (2000 42 M transistors): SSE2
  * Pentium4E (2004, 125M transistors): Added hyperthreading
  * Core 2 (2006, 291M transistors): First multi-core Intel microprocessor, but no hyperthreading.
  * Core i7, Nehalem (2008, 781M transistors): hyperthreading + multi-core. 
  * Core i7, Sandy Bridge (2011, 1.17G transistors): 
  * Core i7, Haswell (2013, 1.4G transistors): 
* The number of transistors increases at an annual rate of approximately 37%, meaning that the number of transistors doubles about every 26 months.
* Moore's Law (1965, Gordon Moore): The number of transistors per chip would double every yearfor the next 10 years. (reality: double every 18 months)


# Programm Encodings
### GCC C Compiler Compile Process
* GCC Compiler invokes the *C Preprocessor* to expand the source code to include any files specified with `#include` commands and to expand any macros, specified with `#define` declarations.

* The *compiler* generates *assembly code* with names `*.s`.
> *Assembly code* is a textual representation of the machine code giving the individual instructions in the program.

* The *Assembler* converts the assembly code into binary *object-code* files `*.o`.
> *Object code* is one form of machine code: it contains binary representations of all of the instructions, but the addresses of global values are not yet filled in.

* The *Linker* merged these object-code files along with code implementing library functions (e.g. `printf`) and generate the final executable machine.
> *Executable code* is one form of machine code: it is the exact form of code that is executed by the processor.
  * The linker will shift the location of code to a different range of addresses.
  * The link matches function calls with the locations of the executable code for those functions. 


### Two important abstract models for machine-level programing. 
  * First, the format and behavior of a machine-level program is defined by the *instruction set architecture*, or ISA, defining the processor state, the format of the instructions, and the effect each of these instructions will have on the state. 
    * Most ISAs, including x86-64, describe the behavior of a program as if each instruction is executed in sequence. Although the processor hardware can execute many instructions concurrently, but it employs safeguards to ensure that the overall behavior matches the sequential operation dictated by the ISA.
  * Second, the memory addresses used by a machine-level program are virtual addresses, providing a memory model that appears to be a very large byte-addressable array.

### Differences of x86-64 machine code with C code
* Parts of the processor state are visible under machine code.
  * The *program counter* or PC (called *%rip* in x86-64) indicates the address in memory of the next instructions to be executed.
  * The integer *register file* contains 16 named locations storing 64-bit values. They can hold addresses (corresponding to C pointers) or integer data. For example, arguments, local variables, return values etc. 
  * The condition code registers hold status information about the most recently executed arithmetic or logic instruciton. They are used to implement, e.g. `if` and `while` statements.
  * A set of vector registers can each hold one or more integer or floating-point values.

### The Program Memory
* Contents of the Program Memory
  * It contains the executable machine code for the program
  * Some information required by the operating system
  * A run-time stack for managing procedure calls and returns
  * Blocks of memory allocated by the user (e.g. `malloc`)

* The program memory is addressed using virtual addresses. 
* At any given time, only limited subranges of virtual addresses are considered valid. 
* The operating system manages this virtual address space, translating virtual addresses into the physical addresses of values in the actual processor memory.

### The machine code and its disassembled Representation
* The program executed by the machine is simply a sequence of bytes encoding a series of instructions. The machine has very little information about the source code form which these instructions are generated. 
> disassemblers: These programs generate a format similar to assembly code from the machine code.



# Assembly Language

* x86-64 (IA32 the 32-bit predecessor to x86-64) is the most popular machine language for processors in laptops and desktops. 
  * Also called Intel64
