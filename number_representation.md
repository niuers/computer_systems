# Table of Contents
* [Integer Representation](#integer-representation)
* []()
* []()
* []()
* []()

# Integer Data Types

## Unsigned Integer Encodings
* The range of values that can be represented as a `w-bit` vector: [0, 2<sup>w</sup>-1]
* Every number between `0` and 2<sup>w -1</sup> has a unique encoding as a `w-bit` value

## Signed Integer Representation

### Two's-Complement Encodings
> It's defined by interpreting the most significant bit (i.e. x<sub>w-1</sub>, also called the 'sign bit') of the word to have negative weight.

* The range of values that can be represented as a `w-bit` two’s-complement number: [-2<sup>w-1</sup>, 2<sup>w-1</sup>-1]
  * The range is asymmetric: There's no positive counterpart of the minimum negative value.
  * The maximum unsigned value is just one over twice the maximum two's-complement value. 
  



