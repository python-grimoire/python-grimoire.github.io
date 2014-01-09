---
layout: default
title: Converting from Strings to Numbers
---

## Problem:

You have a string such as `'533'` and wish to convert it to the number 533. 

## Solution:

The built-in functions `int()`, `long()`, and `float()` can perform this conversion from string to a numeric type: 
 
`
>>> int( '533' )
533
>>> long( '37778931862957161709568' )
37778931862957161709568L
>>> float( '45e-3'), float('12.75')
(0.045, 12.75)
`
 
Note that these functions are restricted to decimal interpretation, so that `int('0144')` will return a result of 144, and `int('0x144')` will raise a `ValueError` exception. 
 
To support different bases, or for use with versions of Python earlier than 1.5, the [`string`][s] module contains the functions `atoi()`, `atol()`, and `atof()`, which convert from ASCII to integer, long integer, or floating point, respectively. 
 
```python
>>> import string
>>> string.atoi('45')
>>> string.atol( '37778931862957161709568' )
37778931862957161709568L
>>> string.atof('187.54')
187.54
```
 
`atoi()` and `atol()` have an optional second argument which can be used to specify the base for the conversion. If the specified base is 0, the functions will follow Python's rules for integer constants: a leading `0` will cause the string to be interpreted as an octal number, and a leading `0x` will cause base-16 to be used. 
 
```python
>>> string.atoi('255')
255
>>> string.atoi('255', 16) # 255 hex = 597 decimal
597
>>> string.atoi('0255', 0) # Assumed to be octal
173
>>> string.atol('0x40000000000000000000', 0)
302231454903657293676544L
```
 
While you could use the built-in function `eval()` instead of the above functions, this is not recommended, because someone could pass you a Python expression that might have unwanted side effects. 

For example, a caller might pass a string containing a call to `os.system()` to execute an arbitrary command; this is a serious danger for applications such as CGI scripts that need to handle data from an unknown source. `eval()` will also be slower than a more specialized conversion operation. 
 
[s]: http://docs.python.org/2.7/library/string.html
