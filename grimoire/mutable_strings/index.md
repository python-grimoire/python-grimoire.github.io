---
layout: default
title: Mutable Strings
---

# Problem:
 
Python's strings are immutable, so you can't change a single character of the string without constructing a new string. Sometimes this is a problem, particularly when dealing with very large strings; constructing a new string will require copying most of the original string, and can be slow. 
 
# Solution:
 
Use the [`array`][array] module, which provides a mutable array data type that can only hold values of a single type. If used to hold only characters, an array behaves similarly to a mutable string.
 
```python
import array

A = array.array('c')
A.fromstring('hello there!')
print A
```
 
This prints: 
 
```python
array('c', 'hello there!')
```
 
The array object `A` is mutable, so you can modify an element in place: 
 
```python
A[0] = 'j'
print A
```
 
This will print: 
 
```python
array('c', 'jello there!')
```
 
Most functions that require strings, such as `string.split()`, won't accept array objects, so you'll have to convert the array to a string in order to pass the data to certain functions: 
 
```python
print string.split(A.tostring())
```

But since both strings and arrays are [sequence types][seq], several forms of indexing and slicing can be performed on either.

[array]: http://docs.python.org/2.7/library/array.html
[seq]: http://docs.python.org/2/library/stdtypes.html#sequence-types-str-unicode-list-tuple-bytearray-buffer-xrange