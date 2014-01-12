---
layout: default
title: Strings
---

Relatively few tasks can be performed by only dealing with numbers; programs will usually print out reports, modify the contents of text files, parse [HTML][html] and [XML][xml] documents, and perform other operations on strings of characters. Strings are therefore an important data type in modern programming languages, and Python is no exception. 
 
In the source code for a Python program, strings can be written in several ways. They can be surrounded by either single or double quotes: 
 
```python
if version[:5] != 'HTTP/':
   send_error(400, "Bad request version(%s)" % `version`)
```
 
Strings are one of Python's sequence types. This means that strings can be sliced, and the `for` statement can be used to iterate over the individual characters in a string: 
 
```python
>>> s = "Hello, world"
>>> s[0:5]
'Hello'
>>> s[-5:]
'world'
>>> for char in s:
...   print char,
...
H e l l o ,   w o r l d
```
 
Strings are immutable; once a string has been created, whether as a literal in a program's source code or in the course of a program's operation, you can't modify the string in-place. Trying to change the first character of a string by slicing, as in the code `s[0] = 'Y'`, fails; to create a modified version of the string, you have to assemble a whole new string with code like `s = 'Y' + s[1:]`. 

This means that Python has to make temporary copies of the string, which will be slow and memory-consuming if you're modifying very large strings. 

See the [Mutable Strings][mutable] section for a way around this by using the [`array`][array] module, and the [`UserString`][userstring] <PythonModule module for a `MutableString` type (deprecated from 2.6 onwards) which may be useful if you absolutely must modify strings in-place and still use some of [`string`][string]  methods.

[html]: search#html
[xml]: search#xml
[array]: http://docs.python.org/2.7/library/array.html
[mutable] #todo
[userstring]: http://docs.python.org/release/2.4/lib/module-UserString.html
[string]: http://docs.python.org/2.7/library/string.html