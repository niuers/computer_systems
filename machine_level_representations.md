# Table of Contents
* [Intel Processor x86 History](#intel-processor-x86-history)
* [](#)
* [](#)

> Machine Code: sequences of bytes encoding the low-level operations that manipulate data, manage memory, read and write data on storage devices, and communicate over networks.

* A compiler generates machine code through a series of stages, based on:
  * The rules of the programming language
  * The instruction set of the target machine
  * The conventions followed by the operating system

* Programmers seeking to maximize the performance of a critical section of code often try different variations of the source code, each time compiling and examining the generated assembly code to get a sense of how efficiently the program will run. 

* GCC C Compiler
  * Compile source code into *assembly code*, a textual representation of the machine code giving the individual instructions in the program.
  * *Assembler* and *Linker* generate the executable machine code from the assembly code.

* Python?

# Compile Life Cycle
## Programm Encodings



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

# Assembly Language

* x86-64 (IA32 the 32-bit predecessor to x86-64) is the most popular machine language for processors in laptops and desktops. 
  * Also called Intel64
