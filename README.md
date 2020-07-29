# bitHelpers

Arduino library with functions on bit level

## Description

This library contains functions to manipulate bits and bitpatterns in an 
efficient way. 
For most functions a 8 - 64 bit optimized version exist. 

The library is tested on ESP32 and Arduino UNO but not for all possible values. 
other platforms are expected to work without modification. 
If they don't please let me know.

New bit functions can be added or investigated, please post an issue.


## Interface

BitCount, several implementations to compare performance.
- **bitCountReference(uint32_t val)** returns nr of bits set in a value.
- **bitCountKR(uint32_t val)** Kerningham bitCount
- **bitCountArray(uint32_t val)** count per nybble with lookup table
- **bitCountF1(uint32_t val)** SWAG algorithm variant
- **bitCountF2(uint32_t val)** SWAG algorithm variant

BitCount - fastest version: uint8_t .. uint64_t
- **bitCount(val)**  

Reverse: uint8_t .. uint64_t
- **bitReverse()**    reverses bits in a uint8_t .. uint64_t
- **nybbleReverse()** reverses nybbles (4 bit) in a uint8_t .. uint64_t
- **byteReverse()**   reverses bytes (8 bit) in a uint16_t .. uint64_t
- **wordReverse()**   reverses words (16 bit) in uint32_t and uint64_t

Swap upper and lower half: uint8_t .. uint64_t
- **swap()** 0x12345678 ==> 0x56781234

Rotate Left / Right: uint8_t .. uint64_t
- **bitRotateLeft(value, pos)**
- **bitRotateRight(value, pos)** 

BitFlip: uint8_t .. uint64_t
- **bitFlip(value, pos)** flips a single bit at pos

BitRot: uint8_t .. uint64_t
- **bitRot(value, chance)** random damage to a value, chance = float 0.0 .. 1.0  
bitRot is a function that can be used to mimic single bit errors in communication protocols.

## Future

- bit based function to efficiently set/clear single bits in 64 bit values
- besides **bitRot()** one can also have timing issues when clocking in bits. 
A function could be created to mimic such timing error, by shifting bits from a 
specific position. e.g. parShiftLeft(00001010, 4) ==> 00011010  
- optimize e.g. smart shift.
- **bitsNeeded(n)** how many bits need a number.
- many more :)

## Operations

See examples.
