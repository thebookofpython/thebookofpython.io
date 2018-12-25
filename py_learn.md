
### Integer Division

Also called *floored division*. Uses the `//` operator and takes the floor of the result of the division, which means that it rounds down to the nearest integer:

```python
>>> 17 // 10
1
```

This was previously the behavior of the division operation in Python before version 3. Pyton 3 now creates a float for all division operations. Note that negative operands will return one lower than you might expect.

### The Modulo, Modulus, or Remainder Operator

An operator, denoted with a percent sign (%), that works on integers and yields the remainder when one number is divided by another. Uses can include 

Examples of its uses include determining if a number is odd or even, factoring numbers, and extracting trailing digits from numbers.

```py
# Determine if a number is odd or even
if i % 2 == 0:
    print('Your number is even')
> Your number is even
    
# Extract the right-most digit or digits from a number
print(int(41.23 * 100 % 100))
> 23

# Factor a number
divisor = 99
factors = []

while divisor > 0:
    if i % divisor == 0:
        factors.append(divisor)
    divisor -= 1
if len(factors) == 2:
    print(i, 'is prime')
print(factors)
[99, 33, 11, 9, 3, 1]
```

### 3.7 Catching Exceptions Using Try and Except

The idea of `try` and `except` is that you know that some sequence of instruction(s) may have a problem and you want to add some statements to be executed if an error occurs. These extra statements (the `except` block) are ignored if there is no error and executed if the code in the `try` block fails.

```py
inp = input('Enter Fahrenheit Temperature:')
try:
    fahr = float(inp)
    cel = (fahr - 32.0) * 5.0 / 9.0
    print(cel)
except:
    print('Please enter a number')
```

### 3.8 Short-Circuiting Logical Expressuons and the Guardian Pattern

When Python detects that there is nothing to be gained by evaluating the rest of a logical expression, it stops its evaluation and does not do the computations in the rest of the logical expression. This is called *short-circuiting* the evaluation. This short-circuit behavior leads to a clever technique called the *guardian pattern*. 

We can construct the logical expression to strategically place a guard evaluation just before the evaluation that might cause an error as follows:

```py
>>> x = 1
>>> y = 0
>>> x >= 2 and y != 0 and (x/y) > 2
False

>>> x = 6
>>> y = 0
>>> x >= 2 and y != 0 and (x/y) > 2
False

>>> x >= 2 and (x/y) > 2 and y != 0
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ZeroDivisionError: division by zero
>>>
```

In the first logical expression, `x >= 2` is `False` so the evaluation stops at the `and`. In the second logical expression, `x >= 2` is `True` but `y != 0` is `False` so we never reach `(x/y)`.

In the third logical expression, the `y != 0` is after the `(x/y)` calculation so the expression fails with an error.

In the second expression, we say that `y != 0` acts as a *guard* to insure that we only execute `(x/y)` if `y` is non-zero.

## Using Help Documentation

There are two approaches to Help Documentation in interactive mode.

One is to use the `help()` function:

```py
# Help for a string method
>>> help(str.lower)
Help on method_descriptor:

lower(...)
    S.lower() -> str

    Return a copy of the string S converted to lowercase.

# Help for a built-in function
>>> help(sum)
Help on built-in function sum in module builtins:

sum(iterable, start=0, /)
    Return the sum of a 'start' value (default: 0) plus an iterable of numbers
    
    When the iterable is empty, return the start value.
    This function is intended specifically for use with numeric values and may
    reject non-numeric types.
```

Or you can use Python's *Help Utility* by invoking the `help()` function without an argument:

```py
>>> help()

Welcome to Python 3.6's help utility!

If this is your first time using Python, you should definitely check out
the tutorial on the Internet at http://docs.python.org/3.6/tutorial/.

Enter the name of any module, keyword, or topic to get help on writing
Python programs and using Python modules.  To quit this help utility and
return to the interpreter, just type "quit".

To get a list of available modules, keywords, symbols, or topics, type
"modules", "keywords", "symbols", or "topics".  Each module also comes
with a one-line summary of what it does; to list the modules whose name
or summary contain a given string such as "spam", type "modules spam".


help> sum
Help on built-in function sum in module builtins:

sum(iterable, start=0, /)
    Return the sum of a 'start' value (default: 0) plus an iterable of numbers
    
    When the iterable is empty, return the start value.
    This function is intended specifically for use with numeric values and may
    reject non-numeric types.


help> 
```

Another useful feature of Python is the `dir()` function to get a module's contents:

```py
>>> dir(__builtins__)
['ArithmeticError',
 'AssertionError',
 'AttributeError',
 'BaseException',
 'BlockingIOError',
 'BrokenPipeError',
 'BufferError',
 'BytesWarning',
 'ChildProcessError',
 'ConnectionAbortedError',
 'ConnectionError',
 'ConnectionRefusedError',
 'ConnectionResetError',
 'DeprecationWarning',
 'EOFError',
 'Ellipsis',
 'EnvironmentError',
 'Exception',
 'False',
 'FileExistsError',
 'FileNotFoundError',
 'FloatingPointError',
 'FutureWarning',
 'GeneratorExit',
 'IOError',
 'ImportError',
 'ImportWarning',
 'IndentationError',
 'IndexError',
 'InterruptedError',
 'IsADirectoryError',
 'KeyError',
 'KeyboardInterrupt',
 'LookupError',
 'MemoryError',
 'ModuleNotFoundError',
 'NameError',
 'None',
 'NotADirectoryError',
 'NotImplemented',
 'NotImplementedError',
 'OSError',
 'OverflowError',
 'PendingDeprecationWarning',
 'PermissionError',
 'ProcessLookupError',
 'RecursionError',
 'ReferenceError',
 'ResourceWarning',
 'RuntimeError',
 'RuntimeWarning',
 'StopAsyncIteration',
 'StopIteration',
 'SyntaxError',
 'SyntaxWarning',
 'SystemError',
 'SystemExit',
 'TabError',
 'TimeoutError',
 'True',
 'TypeError',
 'UnboundLocalError',
 'UnicodeDecodeError',
 'UnicodeEncodeError',
 'UnicodeError',
 'UnicodeTranslateError',
 'UnicodeWarning',
 'UserWarning',
 'ValueError',
 'Warning',
 'WindowsError',
 'ZeroDivisionError',
 '__IPYTHON__',
 '__build_class__',
 '__debug__',
 '__doc__',
 '__import__',
 '__loader__',
 '__name__',
 '__package__',
 '__spec__',
 'abs',
 'all',
 'any',
 'ascii',
 'bin',
 'bool',
 'bytearray',
 'bytes',
 'callable',
 'chr',
 'classmethod',
 'compile',
 'complex',
 'copyright',
 'credits',
 'debugfile',
 'delattr',
 'dict',
 'dir',
 'display',
 'divmod',
 'enumerate',
 'eval',
 'exec',
 'filter',
 'float',
 'format',
 'frozenset',
 'get_ipython',
 'getattr',
 'globals',
 'hasattr',
 'hash',
 'help',
 'hex',
 'id',
 'input',
 'int',
 'isinstance',
 'issubclass',
 'iter',
 'len',
 'license',
 'list',
 'locals',
 'map',
 'max',
 'memoryview',
 'min',
 'next',
 'object',
 'oct',
 'open',
 'ord',
 'pow',
 'print',
 'property',
 'range',
 'repr',
 'reversed',
 'round',
 'runfile',
 'set',
 'setattr',
 'slice',
 'sorted',
 'staticmethod',
 'str',
 'sum',
 'super',
 'tuple',
 'type',
 'vars',
 'zip']

>>> import math
>>> dir(math)
['__doc__',
 '__loader__',
 '__name__',
 '__package__',
 '__spec__',
 'acos',
 'acosh',
 'asin',
 'asinh',
 'atan',
 'atan2',
 'atanh',
 'ceil',
 'copysign',
 'cos',
 'cosh',
 'degrees',
 'e',
 'erf',
 'erfc',
 'exp',
 'expm1',
 'fabs',
 'factorial',
 'floor',
 'fmod',
 'frexp',
 'fsum',
 'gamma',
 'gcd',
 'hypot',
 'inf',
 'isclose',
 'isfinite',
 'isinf',
 'isnan',
 'ldexp',
 'lgamma',
 'log',
 'log10',
 'log1p',
 'log2',
 'modf',
 'nan',
 'pi',
 'pow',
 'radians',
 'sin',
 'sinh',
 'sqrt',
 'tan',
 'tanh',
 'tau',
 'trunc']
```

## 4.2 Built-in Functions

Built-in functions can seem mysterious to a new programmer. The difference between the more general use built-in functions and the type specific methods for strings, lists, ints, etc., can be subtle and confusing. Methods however are a property of a class and therefore 1) use dot notation; 2) can only be used on its own class; and 3) must designate a class member to act on. Built-in functions are provided by Python to complete common tasks, often across multiple value types (e.g., `len()`), without having to write a new function definition every time. 

## 4.4 Importing Math

A *module* is a group of related functions. External modules are not automatically included in Python's functionality when it runs. Many commonly used modules are 'packaged' with Python and if needed can be easily imported. Math is one of these modules. To use a function from the `math` module we import it and then use dot notation to call the needed function like this:

```py
>>> import math

>>> math.sqrt(2) / 2.0
0.7071067811865476
```

## 4.5 Importing Random

The *random* module provides functions that generate pseudorandom numbers
(which we will simply call “random” from here on). The function random returns a random float between 0.0 and 1.0 (including 0.0 but not 1.0). Each time you call random, you get the next number in a long series.

To see a sample, run this loop:

```py
import random
for i in range(10):
     x = random.random()
     print(x)

0.11132867921152356
0.5950949227890241
0.04820265884996877
0.841003109276478
0.997914947094958
0.04842330803368111
0.7416295948208405
0.510535245390327
0.27447040171978143
0.028511805472785867
```

This program produces the above list of 10 random numbers between 0.0 and
up to but not including 1.0.

The random function is only one of many functions that handle random numbers. The function randint takes the parameters low and high, and returns an integer between low and high (including both).

```py
>>> random.randint(5, 10)
5
>>> random.randint(5, 10)
9
```

To choose an element from a sequence at random, you can use choice:

```py
>>> t = [1, 2, 3]
>>> random.choice(t)
2
>>> random.choice(t)
3
```

## 4.8 Building Functions

The program below contains two function definitions: `print_lyrics` and `repeat_lyrics`. Function definitions get executed just like other statements, but the effect is to create function objects. The statements inside the function do not get executed until the function is called, and the function definition generates no output.

```py
def print_lyrics():
    print("I'm a lumberjack, and I'm okay.")
    print('I sleep all night and I work all day.')
    
def repeat_lyrics():
    print_lyrics()
    print_lyrics()
```

The output of executing `print(print_lyrics)` before executing the above program is:

```py
print(print_lyrics)
Traceback (most recent call last):

  File "<ipython-input-1-08f2b8e9b2d5>", line 1, in <module>
    print(print_lyrics)

NameError: name 'print_lyrics' is not defined
```

You have to create a function before you can call it, that is to say, place the function object in memory. Therefore the function definition has to be executed before the first time it is called. After executing the script, which gives no output because no function is *called*, this is the output:

```py
print(print_lyrics)
<function print_lyrics at 0x0000028D8F50B6A8>

print(repeat_lyrics)
<function repeat_lyrics at 0x0000028D9602B510>
```

Both functions now have *function objects* with memory addresses even though neither has actually done anything.

## 7.9

The built-in function `repr()` takes any object as an argument and returns a string representation of the object. For strings, it represents whitespace
characters with backslash sequences. Locating whitespace characters can be helpful for debugging.

```py
>>> s = '1 2\t 3\n 4'
>>> print(s)
1 2 3
4
>>> print(repr(s))
'1 2\t 3\n 4'
```

## Notes on Opening and Handling Files

Using a `with`/`as` statement block to open and process a file asks Python to Iautomatically.

```py
with open('mbox-short.txt', 'r') as file:
    for line in file:
        print(line.rstrip().upper())
```

## 8 Lists

### Methods

   append(...)
       L.append(object) -> None -- append object to end
   
   clear(...)
       L.clear() -> None -- remove all items from L
   
   copy(...)
       L.copy() -> list -- a shallow copy of L
   
   count(...)
       L.count(value) -> integer -- return number of occurrences of value
   
   extend(...)
       L.extend(iterable) -> None -- extend list by appending elements from the iterable
   
   index(...)
       L.index(value, [start, [stop]]) -> integer -- return first index of value.
       Raises ValueError if the value is not present.
   
   insert(...)
       L.insert(index, object) -- insert object before index
   
   pop(...)
       L.pop([index]) -> item -- remove and return item at index (default last).
       Raises IndexError if list is empty or index is out of range.
   
   remove(...)
       L.remove(value) -> None -- remove first occurrence of value.
       Raises ValueError if the value is not present.
   
   reverse(...)
       L.reverse() -- reverse *IN PLACE*
   
   sort(...)
       L.sort(key=None, reverse=False) -> None -- stable sort *IN PLACE*
   
### 8.7 Deleting Items

There are several ways to delete elements from a list. If you know the index of the
element you want, you can use `pop`:

```py
>>> t = ['a', 'b', 'c']
>>> x = t.pop(1)
>>> print(t)
['a', 'c']
>>> print(x)
b
```

`pop` modifies the list and returns the element that was removed. If you don’t
provide an index, it deletes and returns the last element.

If you don’t need the removed value, you can use the `del` operator:

```py
>>> t = ['a', 'b', 'c']
>>> del t[1]
>>> print(t)
['a', 'c']
```

If you know the element you want to remove (but not the index), you can use
`remove`:

```py
>>> t = ['a', 'b', 'c']
>>> t.remove('b')
>>> print(t)
['a', 'c']
```

The return value from `remove` is `None`.

To remove more than one element, you can use `del` with a slice index:

```py
>>> t = ['a', 'b', 'c', 'd', 'e', 'f']
>>> del t[1:5]
>>> print(t)
['a', 'f']
```

## 8.9 Using `join`

`join` is the inverse of `split`. It takes a list of strings and concatenates the elements. `join` is a string method, so you have to invoke it on the delimiter and pass the list as a parameter:

```py
t = ['pining', 'for', 'the', 'fjords']   

print(' '.join(t))
pining for the fjords

print(t)
['pining', 'for', 'the', 'fjords'] # Note that t is unmodified
```

In this case the delimiter is a space character, so join puts a space between words.
To concatenate strings without spaces, you can use the empty string, “”, as a
delimiter.

## 8.11- Objects, Values, References, Equality, Identity

Different object types have different rules about what happens when they are replicated or referenced. This is at least partly due to whether or not an object is mutable. 

In the following example Python assigns the same ID (memory address) to both `a` and `b`, which are strings: 

```py
a = 'apple'
b = 'apple'

print(a is b)
print(id(a))
print(id(b))

True
1974196538704
1974196538704
```

An object's 'contents' are its *value(s)*, or the information it is being used to hold. Values for two references (a reference is an object's name, a single object can have more than one reference) may be equivalent without their objects being *identical*. To be identical is to point to the same memory address and therefore have the same ID. Two separately created *lists* with equivalent values will not be identical. This is just how lists work.

If `a` refers to an object and you assign `b = a`, then both variables refer to the same object:

```py
>>> a = [1, 2, 3]
>>> b = a
>>> b is a
True
```

The association of a variable with an object is called a *reference*. In this example, there are two references to the same object. An object with more than one reference has more than one name, so we say that the object is *aliased*.

If the aliased object is mutable, changes made with one alias affect the other:

```py
>>> b[0] = 17
>>> print(a)
[17, 2, 3]
```

This is not so much an issue with immutable objects like strings. One place this can sometimes be surprising however is passing a list as an argument to a function for some manner of modification. 

When you pass a list to a function, the function gets a reference to the list. If the function modifies a list parameter, the caller sees the change. For example delete_head removes the first element from a list:

```py
def delete_head(t):
    del t[0]

>>> letters = ['a', 'b', 'c']
>>> delete_head(letters)
>>> print(letters)
['b', 'c']
```

The parameter t and the variable letters are aliases for the same object.

## List Methods and `None` Returns

It is important to distinguish between operations that modify lists and retun `None` and operations that create new lists. For example, the append method modifies a list, but the + operator creates a new list:

```py
>>> t1 = [1, 2]
>>> t2 = t1.append(3)
>>> print(t1)
[1, 2, 3]
>>> print(t2)
None
>>> t3 = t1 + [3]
>>> print(t3)
[1, 2, 3]
>>> t2 is t3
False
```

This difference is important when you write functions that are supposed to modify lists. For example, this function does not delete the head of a list:

```py
def bad_delete_head(t):
    t = t[1:] # WRONG!
```

The slice operator creates a new list and the assignment makes t refer to it, but none of that has any effect on the list that was passed as an argument.

An alternative is to write a function that creates and returns a new list. For example, tail returns all but the first element of a list:

```py
def tail(t):
    return t[1:]
```

This function leaves the original list unmodified. Here’s how it is used:

```py
>>> letters = ['a', 'b', 'c']
>>> rest = tail(letters)
>>> print(rest)
['b', 'c']
```

On p. 109

REMEMBER: Most list methods modify the argument and return `None`. This is the opposite of the string methods, which return a new string and leave the original alone.

If you are used to writing string code like this:

```py
word = word.strip()
```

It is tempting to write list code like this: 

```py
t = t.sort() # WRONG!
```

In this statement, `t.sort()` has a return value of `None`. `None` is therefore now *assigned* to `t`. This is the result:

```py
t = [5, 3, 9, 1, 0]
print(t)
[5, 3, 9, 1, 0]

# If you assign the output of method or funtion that explicitely returns `None`
# the assigment will be 'None`.
t = t.sort()
print(t)
None

# List methods generally modify in place
t = [5, 3, 9, 1, 0]
t.sort()
print(t)
[0, 1, 3, 5, 9]

# The built-ins `sorted()` and `reversed()` do NOT modify the argument, 
# they return new lists
sorted(t) 
[0, 1, 3, 5, 9]

t
[5, 3, 9, 1, 0]
```

## Lists Methods and Built-in Functions

### Built-in Functions

Function    | Description 
------------|---------------------------------------------
len(L)      | Returns the number of items in list L
max(L)      | Returns the maximum value in list L
min(L)      | Returns the minimum value in list L
sum(L)      | Returns the sum of the values in list L
sorted(L)   | Returns a copy of list L where the items are in order from smallest to largest (This does not mutate L.)

## Notes

Slicing will only work with an assignment operator or while being printed. Does slicing operate differently on lists and strings regarding modification of the original?

Why doesn't this work?

```py
z = [5, 3, 9, 1, 0]
print('original z =', z)

def bad_delete_head(t):
    x = t[1:] # WRONG!
    print('Inside the function:', t)
    return x

if __name__ == '__main__':
    bad_delete_head(z)
    print('Outside the function:', z)
```

