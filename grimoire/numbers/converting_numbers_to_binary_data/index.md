---
layout: default
title: Converting Numbers to and from Binary Data
---

## Problem:

You need to convert an integer value `V` to a 2-byte or 4-byte string representation.

For example, the number `1` would be the bytes `0,1`; `1956` would be `164,7` because `1956 = 7 * 256 + 164`. This is often needed when reading or writing binary data files, or implementing network protocols. 
 
''Solution:'' 
 
You can write code to perform the conversion by taking the low byte of `V`, shifting `V` down 8 bits and taking the low byte of the result, and so forth. However, the code is long and relatively slow: 
 
```python
s = (chr( (V)        255) +
     chr( (V >> 8)   255) +
     chr( (V >> 16)  255) +
     chr( (V >> 24)  255))
```
 
A faster and simpler solution uses the [`struct`][s] module, which is intended for such conversions: 
 
```python
import struct
s = struct.pack('i', V )
```
 
To reverse the conversion, and go from a binary string to a tuple of integers, use `struct.unpack()`:
 
```python
byte, short = struct.unpack('BH', '\377\000\377\377')
```
 
## Discussion:
 
You're not limited to only packing a single value at time. Instead, the `pack()` function in the [`struct`][s] module takes a format string containing several characters, along with the values to be packed: 
 
```python
>>> struct.pack('iii',  127, 1972, 1234567890)
'\177\000\000\000\264\007\000\000\322\002\226I'
```
 
Repeated format characters can be written as a single character preceded by an integer repeat count; the previous example could have been written as `struct.pack('3i', ...)`, and would produce identical results. 
 
Different-sized values can be packed using several different format characters, whose output will vary in size. For example, the `b` (byte) character will produce a single byte of output, and therefore is limited to values between -128 and 127. `h` (short) produces 2 bytes, `i` (int) produces 4 bytes, and `l` (long) will be 4 bytes on 32-bit machines, and 8 bytes on most 64-bit machines. 
 
Here's a table of some of the more commonly used format characters supported by `pack()` and `unpack()`. Consult the Library Reference's section on the [`struct`][s] module for a complete list:

| Format | C Type          | Python  |
|:------ |:---------------:| -------:|
| b      | `signed char`   | integer |
| B      | `unsigned char` | integer |
| h      | `short`         | integer |
| i      | `int`           | integer |
| l      | `long`          | integer |
| f      | `float`         | float   |

Because the [`struct`][s] module is often used for packing and unpacking C `structs`, it obeys the compiler's alignment rules. This means that padding bytes may be inserted between format characters of different types. For example, the zero byte in the following example is padding: 
 
```python
>>> struct.pack('BH',  255, 65535)
'\377\000\377\377'
```


[s]: http://docs.python.org/2.7/library/struct.html
