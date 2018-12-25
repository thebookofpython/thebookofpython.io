## Values

## Methods

## Functions

Parameter, arguments, aliases

### Code Blocks

An indented section of code belonging to the header above it. Are opening `if` and other non-function openings called 'headers'?

## Scope

### Global Scope

Variables that are defined in the module outside of any function.

## Types

### Collections

### Iterables

Iterables are objects that contain one or more members that can each be processed one by one. Examples of Python types that are iterable include lists, strings (the characters are iterable), tuples, file objects and dictionaries.

Loops provide us with the means to  over it. Every loop can inspect each designated element of the list and either use it for something, change it or skip it, depending on the progrmmer's instructions in the loop block. Loops are contained in an indented block of code called a block. Code blocks are important because they are like little fenced in lots with rules called *scope* that determine what they can affect and be affected by, elsewhere in the program.

### Lists

Lists are a Python object type that can hold a collection of values of any type, which themselves can be nested collections. Lists usually hold groups of data related in some way, e.g., a list of the planets, a list of each of the lines from a text file, a store's list of daily sandwich sales for the past year. 

If you were collecting information on daily high temperatures in your city over a week you could create seven variables, each with the name of a weekday, and assign your temperature every day to each respective variable's value. It's clear that this would get challenging beyond a week of days since variables have to be unique for each day collected; this is the type purpose that lists were devised for. 

...

## Looping Through Collections

A 'loop' is a programming mechanism that allows us to iterate through the members of a collection (e.g., a list, a dictionary, a string of characters, the lines in a file object) and if we wish, do something with each, one at a time. There are two types of loops in Python, `for` loops, and `while` loops.  

### `for` Loops

Say we have a list of seven temperatures, one for each day of the past week, and we want to know the average for the week. The `for` loop is ideal when the number of loops to make is known or can be acquired. We will use `for` and its assistant `in` to loop through our list seven times and on each loop we'll add the current value to a total we are keeping of all of the previous values. Let's look at our program:

```py
temps = [48, 53, 51, 47, 51, 55, 49]
total = 0
avg = 0

for temp in temps:
    total = total + temp
avg = total / len(temps)
print(avg)
> 50.57142857142857
```

Break down each line...
- Visualizor, make a gif
- `in`
- The *loop variable*, `temp` vs. `temps`, if exists will be overwritten, at the end of the last loop will continue to have the last value that went through it.
- Code blocks
- *iterations*, *iterables*
- *accumumulators*
- `len()`
- `print()`
- `sum` 
- Loops
- Scope
- Objects
- Types and classes
- Is `for` an operator?

### Looping Lists by Indices or by Items

In the example above we looped over the value of each temperature using the loop variable `temp` with the list `temps` as the target of the `in` operator. We can do this if we are *not* modifying the elements of the list in place, but are using them to create a new value, like our temperature average. If however we wanted to convert our list of temperatures from fahrenheit to celsius, that is to say permanently modify each of the values in our list, `temps`, we must use list indices to iterate through the list. We have in our list of temperatures seven values, they are `temps[0]` through `temps[6]`. If we did not know this we could simply query the list using the built-in function `len()`. 

We will now use the built-in function `range()` as the object of our `for` loop (to provide our indices), where we referenced the list, `temps`, above, and then access each element individually using its index, inside the loop block.

```py
temps = [48, 53, 51, 47, 51, 55, 49]
total = 0
avg = 0

# Note the different object on which we are iterating, namely, `range()`.
for i in range(7): 
    total = total + temps[i] # We now reference each item by list index
avg = total / len(temps)
print(avg)
```

Another example:

```py

values = [4, 10, 3, 8, -6]
for num in values:
    num *= 2
    print(num)
print(values)
8
20
6
16
-12
[4, 10, 3, 8, -6]

values = [4, 10, 3, 8, -6]
for i in range(len(values)):
    values[i] *= 2
    print(values[i])
print(values)
8
20
6
16
-12
[8, 20, 6, 16, -12]
```

### `range()`

To get the numbers from the sequence all at once, we can use built-in function `list()` along with the `range()` function to create a list of those numbers:

```py
my_list = list(range(10))

print(my_list)
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

The `range()` function can be used with up to three arguments, the *start* number (inclusive), the *stop* number (exclusive), and a step (by default 0). At minimum we must give a stop number for the end of the range and the last number within the range will be one less than the stop number. The "stop number" *is* however the exact number of elements that will be given by the range if the start and step are defaults. If only one number is given (the stop number) then the start number is 0 by default. This will create a range that is consistent with how indexes are sequenced in lists as well as slicing. 

If two parameters are provided, the first of the two is taken as the start number:

```py
my_list = list(range(1, 11))
print(my_list)
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

If three parameters are passed the third is used as the step:

```py
my_list = list(range(0, 105, 5))
print(my_list)
[0, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50, 55, 60, 65, 70, 75, 80, 85, 90, 95, 100]
```

Note that in order to include a step (a third parameter), the start number must be given even if it is 0.

Range will iterate in decending order as well:

```py
my_list = list(range(105, 0, -5))
print(my_list)
[105, 100, 95, 90, 85, 80, 75, 70, 65, 60, 55, 50, 45, 40, 35, 30, 25, 20, 15, 10, 5]
```

But notice that the "stop" number is still exclusive.

### Parallel Lists

*Parallel lists* are two (or more) lists with related values at the same indices. That is to say that our list `days` might contain a set of dates and our list `temps` might have the high temperatures collected for those dates. The temperature in `temps[0]` belongs to the date at `days[0]`.

```py

```

## Nested Loops

Loops can be nested. Say you want to print a skeleton test outline to fill in later; it will require three main sections numbered 1 through 3, each with three subsections using te letters a, b and c: 

```py
main = range(1, 4) # print our section headings 1-3
sub = range(97, 100) # The Unicode digits for the lowercase letters a, b, and c

for i in main:
    print(i)
    for j in sub:
        print(chr(j))
    print()
```

## Objects

All objects have at least three properties: 
    1. A type
    2. An ID
    3. A value (even if it is `None` or `Null`)

## The `open()` Method
Built-in function `open()` opens a file (much like you open a book when you want to read it) and returns an object that knows how to get information from the file, how much you’ve read, and which part of the file you’re about to read next. The marker that keeps track of the current location in the file is called a file cursor and acts much like a bookmark. The file cursor is initially at the beginning of the file, but as we read or write data it moves to the end of what we just read or wrote.

The first argument is the name of the file to open, and the second is the *mode* in which to open it. The mosdes are: `r` for *read*, `w` for *write*, and `a` for *append*. Ommitting the mode defaults to read.

```py
file = open('file_example.txt', 'r')
contents = file.read()
print(contents)
file.close()

# Output
First line of text
Second line of text
Third line of text
```