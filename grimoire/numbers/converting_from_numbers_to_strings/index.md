---
layout: default
title: Converting from Numbers to Strings
---

You wish to convert a number to the corresponding string representation. For example, you want to convert a number like `144` to the string `'144'`. 
 
The simplest way is to use the built-in function `str()`, or the backquote notation `144`. Both solutions will convert the number to a string in the most straightforward way. 
 
```python
V = 187.5
S = str(V)  # Produces '187.5'
```
 
If `V` contains an integer or long integer, and you want to convert the number to hexadecimal or octal representation, use the built-in functions `hex()` or `oct()`. 
 
```python
>>> hex(187)
'0xbb'
>>> oct(187)
'0273'
```
 
If fancier formatting is required, such as rounding a floating-point number to a given number of decimal places, or padding a number with zeros, use the % operator on strings, which allows more precise control of the output. 
 
```python
>>> "%04d" % (87,)
'0087'
>>> "%.2f" % (187.375,)
'187.38'
```
 
(See the Library Reference manual for the complete details of the available format characters.) 
 
There's no library function to convert a number to its base-2 representation, so here's a function to do the job. 
 
```python
def atob(number):
   """Returns a string containing the binary representation of a number"""
   if number < 0:
       prefix = "-" ; number = -number
   elif number == 0: return "0"
   else:
       prefix = ""

   # Loop, looking at the lowest bit of the number an
   s = ""
   while number > 0:
       s = chr( 48+ (number  1) ) + s
       number = number >> 1
   return prefix + s
```
