---
layout: default
title: Introduction to numbers
---

Python offers a variety of different numeric types: integers, which are fast but limited in size; long integers, which are slower but can be of arbitrary size; floating-point numbers; and complex numbers. 
 
The simplest and most basic type are integers, which are represented as a C `long`. Their size is therefore dependent on the platform you're using; on a 32-bit machine, they can range from -2147483647 to 2147483647. Python programs can determine the highest possible value for an integer by looking at `sys.maxint`; the lowest possible value will usually be `-sys.maxint - 1`. 
 
Long integers are an arbitrary-precision integer type. They're slower than regular integers, but don't have the size limitations. Long integer literals have the letter `L` as a suffix; a lowercase `l` is also legal, but should be avoided because it's often difficult to distinguish a lowercase letter `l` from the numeral `1`. If integers and long integers are combined in an expression, the regular integer is converted to a long integer automatically: 
 
    2L + 3 5L  5L ** 100 7888609052210118054117285652827862296732064351090230047702789306640625L 
 
Python's floating point numbers are represented as C's `double` type, and behave pretty much as you'd expect: 
 
    5.4 / 2.3 2.34782608696  6.4 * 2 12.8  7.5 % 5 2.5 
 
In operations that mix floating-point numbers and integers, the integers will be converted to floating-point before computing the result, which will be left as a float. 
 
Python also supports a complex number type. (It's possible to compile the Python interpreter without complex numbers, but few people bother to do so; saving 20K of code isn't that important.) Complex numbers are represented by a floating point constant with a suffix of `j`or `J` suffix, `j` being used to represent the square root of -1 in many engineering contexts. 
 
    1j * 1J (-1+0j)  (3 - 7j) + (2 + 1j) (5-6j)  (1 + 3j) / (2 - 4j) (-0.5+0.5j) 
 
Note that an expression like `1 + 3j` isn't a constant, but an expression that adds two constants: `1` and `3j`. This is a minor semantic quibble, whose major significance is that you should make liberal use of parentheses in complex expressions. `1+3j / 2-4j` is not the same as `(1+3j) / (2-4j)`, because the first expression will evaluate `3j/2` first. 
 
