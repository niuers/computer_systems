# Table of Contents
* [Information Storage](#information-storage)
  * [Data Sizes](#data-sizes)
* [Integer Representation](#integer-representation)
  * [Integer Data Types](#integer-data-types)
  * [Unsigned Integer Encodings](#unsigned-integer-encodings)
  * [Signed Integer Representation](#signed-integer-representation)
  * [Integer Arithmetic](#integer-arithmetic)
* []()
* []()
* []()
* []()

# Information Storage
* The Smallest Addressable Unit: most computers use blocks of **8-bits** or **bytes**, as the smallest addressable unit of memory.

## Data Sizes

### Word Size
* Every computer uses word size to indicate the nominal size of pointer data. A virtual address is encoded by such a word.

### Virtual Address Space
* The most important system parameter determined by the word size is the maximum size of the virtual address space.

### Examples
* The C language allocate different number of bytes for different C data types. 
  * However the exact numbers of bytes for some data types depends on how the program is compiled for(32-bit or 64-bit).
    * Data type `char *` (a pointer) and `long` commonly have 4 bytes in 32-bit programs and 8 bytes in 64-bit programs.
    
### Implications

* Programmers should strive to make their programs portable across different machines and compilers. 
  * Make the program insensitive to the exact sizes of the different data types.
    * Ex1. Programs that enable communications over the Internet need to have data types compatible with the standard protocol.

# Integer Representations

## Integer Data Types

#### Integer Data Types in C
* Variable-Size Data Types
  * Each type can specify a size with keyword `char`, `short`, `int`, `long`, as well as an indication of whether the represented numbers are all nonegative (`unsigned`) or possibly negative (the default). 
  
* Fixed-Size Data Types
  * Their data sizes and range of values are fixed regardless of compiler and machine settings.
  * Example: `int32_t`, `int64_t`
  
## Unsigned Integer Encodings
* The range of values that can be represented as a `w-bit` vector: [0, 2<sup>w</sup>-1]
* Every number between `0` and 2<sup>w</sup>-1 has a unique encoding as a `w-bit` value

## Signed Integer Representation

### Two's-Complement Encodings
> It's defined by interpreting the most significant bit (i.e. x<sub>w-1</sub>, also called the 'sign bit') of the word to have negative weight.

* The range of values that can be represented as a `w-bit` two’s-complement number: [-2<sup>w-1</sup>, 2<sup>w-1</sup>-1]
  * The range is asymmetric: There's no positive counterpart of the minimum negative value.
  * The maximum unsigned value is just one over twice the maximum two's-complement value. 
* For nonnegative `x`, the `w-bit` representation of `-x` is: 2<sup>w</sup> - x. (???)
* Nearly all machines represent signed integers in two's-complement form.

* Implications
  * The C standards do not require signed integers to be represented in two's-complement form, but nearly all machines do so.
  * The Java standard requires a two's-complement representation with the exact same ranges as in 64-bit case.
    * In Java the single-byte type is called `byte` instead of `char`.


###  NuAlternative Representations of Signedmbers
* Ones' Complement
* Sign Magnitude

### Conversions between Signed and Unsigned
#### C Language
* C allows casting between different numeric data types.
* For most implementations of C, the effects of casting signed value to unsigned (or vice versa) is based on a bit-level perspective, rather than on a numeric one.
  * General rule of most C implementations in handling conversions between signed and unsigned numbers with the same word size: The numeric values might change, but the bit patterns do not.
    * Ex1. 
    ```
    short int v = -12345;
    unsigned short uv = (unsigned short) v; 
    printf("v = %d, uv = %u\n", v, uv);
    # v = -12345, uv = 53191
    ```
  * The maximum value of unsigned integer has the same bit representation as does `-1` in two's-complement form.
* Some possibly nonintuitive behavior arises due to C's handling of expressions containing combinations of signed and unsiged quantities.
  * When either operand of a comparison is unsigned, the other operand is implicitly cast to unsigned. 
  
* Implications
  * Java supports only **signed integers**.
  * Java requires that they be implemented with two’s-complement arithmetic. The normal right shift operator >> is guaranteed to perform an arithmetic shift. The special operator >>> is defined to perform a logical right shift.
  * Unsigned values can still be useful when we want to think of words as just collections of bits with no numeric interpretation
    * Packing a word with `flags` describing various Boolean conditions
    * To represent addresses
    * To implement mathematical packages for modular arithmetic
    * To implement multiprecision arithmetic in which numbers are represented by arrays of words.
    
### Expanding the Bit Representation of a Number
* Zero Extension: To convert an **unsigned number** to a larger data type, we can add leading zeros to the representation.
* Sign Extension: To convert a **two's-complement number** to a larger data type, adding copies of the most significant bit to the representation. 

### Truncating Numbers
* Truncating a number can alter its value --- a form of overflow.

## Integer Arithmetic
