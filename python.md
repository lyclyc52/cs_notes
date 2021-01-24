# Learning Python



## Getting Started

The standard implementations of Python today compile (i.e., translate) source code statements to an intermediate format known as byte code and then interpret the byte code. Byte code provides portability, as it is a platform-independent format. However, because Python is not normally compiled all the way down to binary machine code (e.g. , instructions for an Intel chip), some programs will run more slowly in Python than in a fully compiled language like C.

Whether you will ever care about the execution speed difference depends on what kinds of programs you write. Python has been optimized numerous times, and Python code runs fast enough by itself in most application domains.



### How Python Runs Programs

#### Python Interpreter

An interpreter is a kind of program that executes other programs. In effect, the interpreter is a layer of software logic between your code and the computer hardware on your machine.

When the Python package is installed on your machine, it generates a number of components—minimally, an interpreter and a support library. Depending on how you use it, the Python interpreter may take the form of an executable program, or a set of libraries linked into another program. Depending on which flavor of Python you run, the interpreter itself may be implemented as a C program, a set of Java classes, or something else. Whatever form it takes, the Python code you write must always be run by this interpreter.



#### Execution

##### Compilation

Internally, and almost completely hidden from you, when you execute a program
Python first compiles your source code (the statements in your file) into a format known
as byte code. 

If the Python process has write access on your machine, it will store the byte code
of your programs in files that end with a .pyc extension (“.pyc” means compiled “.py”
source).

##### The Python Virtual Machine (PVM)

Once your program has been compiled to byte code (or the byte code has been loaded
from existing .pyc files), it is shipped off for execution to something generally known
as the Python Virtual Machine (PVM, for the more acronym-inclined among you).

##### Performance implications

Python byte
code is not binary machine code (e.g., instructions for an Intel or ARM chip). Byte code
is a Python-specific representation.

##### Development implications

Another ramification of Python’s execution model is that there is really no distinction
between the development and execution environments. That is, the systems that compile
and execute your source code are really one and the same.



#### Execution Model Variations

##### Python Implementation Alternatives

The original, and standard, implementation of Python is usually called CPython.

The Jython system (originally known as JPython) is an alternative implementation of
the Python language, targeted for integration with the Java programming language.
Jython consists of Java classes that compile Python source code to Java byte code and
then route the resulting byte code to the Java Virtual Machine (JVM).

IronPython is designed to allow Python programs to integrate with applications coded to work
with Microsoft’s .NET Framework for Windows, as well as the Mono open source
equivalent for Linux.

The Stackless Python system is an enhanced version and reimplementation of the standard
CPython language oriented toward concurrency(并发性).

The PyPy system is another standard CPython reimplementation, focused on performance.



##### Execution Optimization Tools

The Cython system (based on work done by the Pyrex project) is a hybrid language that
combines Python code with the ability to call C functions and use C type declarations
for variables, parameters, and class attributes.

Shed Skin is an emerging system that takes a different approach to Python program
execution—it attempts to translate Python source code to C++ code, which your computer’s
C++ compiler then compiles to machine code.

The Psyco system is not another Python implementation, but rather a component that
extends the byte code execution model to make programs run faster.



##### Frozen Binaries

With the help of third-party tools that you can fetch off the Web, it is possible to turn your Python programs into true executables, known as frozen binaries in the Python world. These programs can be run without requiring a Python installation.

Apart from a possible startup improvement, frozen binaries run at the same speed as the original source files. Frozen binaries are also not generally small (they contain a PVM), but by current standards they are not unusually large either. Because Python is embedded in the frozen binary, though, it does not have
to be installed on the receiving end to run your program. Moreover, because your code is embedded in the frozen binary, it is more effectively hidden from recipients.





### How You Run Programs

#### The Interactive Prompt

We can run python in terminal directly. 

```python
% python
>>> print('Hello world!')
Hello world!
>>> print(2 ** 8)
256
```

Anytime you see the >>> prompt, you’re in an interactive Python interpreter session—you can type any Python statement or expression here and run it immediately.

```python
>>> lumberjack = 'okay'
>>> lumberjack
'okay'
>>> 2 ** 8
256
>>> ^Z # Use Ctrl-D (on Unix) or Ctrl-Z (on Windows) to exit
%
```

##### Entering multiline statements

```python
>>> for x in 'spam': #One Enter here
... print(x) # Press Enter twice here to make this loop run
...
```

Reminder: the ... continuation line prompt in the preceding is printed by Python automatically as a visual guide.

#### System Command Lines and Files

To save programs permanently, you need to write your code in files, which are usually known as modules. Modules are simply text files containing Python statements.

Once you’ve saved this text file, you can ask Python to run it by listing its full filename as the first argument to a python command like the following typed at the system shell prompt.

```
python script1.py
```



##### Command-Line Usage Variations

```
% python script1.py > saveit.txt
```

In this case, the output lines are stored in the file saveit.txt instead of being printed.



```
c:\code> py −3 script1.py
```

if you’re using the Windows launcher new in Python 3.3 (described earlier), a py command will have the same effect, but does not require a directory path or PATH settings, and allows you to specify Python version numbers on the command line







## Types and Operators

### Python Core Data Types

Just as importantly, once you create an object, you bind its operation set for all time—you can perform only string operations on a string and list operations on a list. In formal terms, this means that Python is dynamically typed, a model that keeps track of types for you automatically instead of requiring declaration code, but it is also strongly typed, a constraint that means you can perform on an object only operations that are valid for its type.

#### Numbers

integer, float, complex number

two stars (**) are used for exponentiation

```python
>>> len(str(2 ** 1000000)) 
301030
```

First converting the ** result’s number to a string of digits with the built-in str function, and then getting the length of the resulting string with len.



```python
>>> 3.1415 * 2 # repr: as code (Pythons < 2.7 and 3.1)
6.2830000000000004
>>> print(3.1415 * 2) # str: user-friendly
6.283
```

Formally, the first form is known as an object’s as-code repr, and the second is its user-friendly str.



#### Strings

```python
>>> S = 'Spam' # Make a 4-character string, and assign it to a name
>>> len(S) # Length
4
>>> S[0] # The first item in S, indexing by zero-based position
'S'
>>> S[1] # The second item from the left
'p'
>>> S[-1] # The last item from the end in S
'm'
>>> S[-2] # The second-to-last item from the end
'a'
>>> S # A 4-character string
'Spam'
>>> S[1:3] # Slice of S from offsets 1 through 2 (not 3)
'pa'
>>> S[1:] # Everything past the first (1:len(S))
'pam'
>>> S[0:3] # Everything but the last
'Spa'
>>> S[:3] # Same as S[0:3]
'Spa'
>>> S[:-1] # Everything but the last again, but simpler (0:-1)
'Spa'
>>> S[:] # All of S as a top-level copy (0:len(S))
'Spam'
>>> S + 'xyz' # Concatenation
'Spamxyz'
>>> S # S is unchanged
'Spam'
>>> S * 8 # Repetition
'SpamSpamSpamSpamSpamSpamSpamSpam'
```

Strings are immutable in Python—they cannot be changed in place after they are created. You can’t change a string by assigning to one of its
positions, but you can always build a new one and assign it to the same name.

Strictly speaking, you can change text-based data in place if you either expand it into a **list** of individual characters and join it back together with nothing between, or use the newer **bytearray** type available in Pythons 2.6, 3.0, and later:

```python
>>> S = 'shrubbery'
>>> L = list(S) # Expand to a list: [...]
>>> L
['s', 'h', 'r', 'u', 'b', 'b', 'e', 'r', 'y']
>>> L[1] = 'c' # Change it in place
>>> ''.join(L) # Join with empty delimiter
'scrubbery'
>>> B = bytearray(b'spam') # A bytes/list hybrid (ahead)
>>> B.extend(b'eggs') # 'b' needed in 3.X, not 2.X
>>> B # B[i] = ord(c) works here too
bytearray(b'spameggs')
>>> B.decode() # Translate to normal string
'spameggs'
```

##### Type-Specific Methods

```python
>>> S = 'Spam'
>>> S.find('pa') # Find the offset of a substring in S
1
>>> S
'Spam'
>>> S.replace('pa', 'XYZ') # Replace occurrences of a string in S with another
'SXYZm'
>>> S
'Spam'
```

Again, despite the names of these string methods, we are not changing the original strings here, but creating new strings as the results—because strings are immutable, this is the only way this can work.

Other method

```python
>>> line = 'aaa,bbb,ccccc,dd'
>>> line.split(',') # Split on a delimiter into a list of substrings
['aaa', 'bbb', 'ccccc', 'dd']
>>> S = 'spam'
>>> S.upper() # Upper- and lowercase conversions
'SPAM'
>>> S.isalpha() # Content tests: isalpha, isdigit, etc.
True
>>> line = 'aaa,bbb,ccccc,dd\n'
>>> line.rstrip() # Remove whitespace characters on the right side
'aaa,bbb,ccccc,dd'
>>> line.rstrip().split(',') # Combine two operations
['aaa', 'bbb', 'ccccc', 'dd']

>>> '%s, eggs, and %s' % ('spam', 'SPAM!') # Formatting expression (all)
'spam, eggs, and SPAM!'
>>> '{0}, eggs, and {1}'.format('spam', 'SPAM!') # Formatting method (2.6+, 3.0+)
'spam, eggs, and SPAM!'
>>> '{}, eggs, and {}'.format('spam', 'SPAM!') # Numbers optional (2.7+, 3.1+)
'spam, eggs, and SPAM!'

>>> '{:,.2f}'.format(296999.2567) # Separators, decimal digits
'296,999.26'
>>> '%.2f | %+05d' % (3.14159, −42) # Digits, padding, signs
'3.14 | −0042'
```

The methods introduced in the prior section are a representative, but small, sample of what is available for string objects. In general, this book is not exhaustive in its look at object methods. For more details, you can always call the built-in dir function. This function lists variables assigned in the caller’s scope when called with no argument.

The dir function simply gives the methods’ names. To ask what they do, you can pass them to the help function.

```python
>>> help(S.replace)
```

Special characters can be represented as backslash escape sequences, which Python displays in \xNN hexadecimal escape notation.

```python
>>> S = 'A\nB\tC' # \n is end-of-line, \t is tab
>>> len(S) # Each stands for just one character
5
>>> ord('\n') # \n is a byte with the binary value 10 in ASCII
10
>>>S
'A\nB\tC'

>>> S = 'A\0B\0C' # \0, a binary zero byte, does not terminate string
>>> len(S)
5
>>> S # Non-printables are displayed as \xNN hex escapes
'A\x00B\x00C'
```

Python allows strings to be enclosed in single or double quote characters—they mean the same thing but allow the other type of quote to be embedded with an escape (most programmers prefer single quotes). It also allows multiline string literals enclosed in triple quotes (single or double)—when this form is used, all the lines are concatenated together, and end-of-line characters are added where line breaks appear.

```python
>>> msg = """
aaaaaaaaaaaaa
bbb'''bbbbbbbbbb""bbbbbbb'bbbb
cccccccccccccc
"""
>>> msg
'\naaaaaaaaaaaaa\nbbb\'\'\'bbbbbbbbbb""bbbbbbb\'bbbb\ncccccccccccccc\n'
```

##### Unicode Strings

Python’s strings also come with full Unicode support required for processing text in internationalized character sets.

```python
>>> 'sp\xc4m' # 3.X: normal str strings are Unicode text
'spÄm'
>>> b'a\x01c' # bytes strings are byte-based data
b'a\x01c'
>>> u'sp\u00c4m' # The 2.X Unicode literal works in 3.3+: just str
'spÄm'

>>> 'spam' # Characters may be 1, 2, or 4 bytes in memory
'spam'
>>> 'spam'.encode('utf8') # Encoded to 4 bytes in UTF-8 in files
b'spam'
>>> 'spam'.encode('utf16') # But encoded to 10 bytes in UTF-16
b'\xff\xfes\x00p\x00a\x00m\x00'
```



#### Lists

##### Sequence Operations

Because they are sequences, lists support all the sequence operations we discussed for strings; the only difference is that the results are usually lists instead of strings.

##### Type-Specific Operations

They have no fixed type constraint—the list we just looked at, for example, contains three objects of completely different types

Further, lists have no fixed size.

```python
>>> L.append('NI') # Growing: add object at end of list
>>> L
[123, 'spam', 1.23, 'NI']
>>> L.pop(2) # Shrinking: delete an item in the middle
1.23
>>> L # "del L[2]" deletes from a list too
[123, 'spam', 'NI']
```

Other list methods insert an item at an arbitrary position (insert), remove a given item by value (remove), add multiple items at the end (extend), and so on. 

Because lists are mutable, most list methods also change the list object in place, instead of creating a new one. The list sort method, for example, orders the list in ascending fashion by default, and reverse reverses it—in both cases, the methods modify the list directly.

##### Bounds Checking

Python still doesn’t allow us to reference items that are not present. Indexing off the end of a list is always a mistake, but so is assigning off the end.

##### Nesting

```python
>>> M = [[1, 2, 3], # A 3 × 3 matrix, as nested lists
		[4, 5, 6], # Code can span lines if bracketed
		[7, 8, 9]]
>>> M
[[1, 2, 3], [4, 5, 6], [7, 8, 9]]

>>> M[1] # Get row 2
[4, 5, 6]
>>> M[1][2] # Get row 2, then get item 3 within the row
6
```

##### Comprehensions

Python includes a more advanced operation known as a list comprehension expression, which turns out to be a powerful way to process structures like our matrix.

```python
>>> col2 = [row[1] for row in M] # Collect the items in column 2
>>> col2
[2, 5, 8]
>>> [row[1] + 1 for row in M] # Add 1 to each item in column 2
[3, 6, 9]
>>> [row[1] for row in M if row[1] % 2 == 0] # Filter out odd items
[2, 8]
```

It can also use iterator.

```python
>>> diag = [M[i][i] for i in [0, 1, 2]] # Collect a diagonal from matrix
>>> diag
[1, 5, 9]
>>> doubles = [c * 2 for c in 'spam'] # Repeat characters in a string
>>> doubles
['ss', 'pp', 'aa', 'mm']
```

**range** function

```python
>>> list(range(4)) # 0..3 (list() required in 3.X)
[0, 1, 2, 3]
>>> list(range(−6, 7, 2)) # −6 to +6 by 2 (need list() in 3.X)
[−6, −4, −2, 0, 2, 4, 6]
>>> [[x ** 2, x ** 3] for x in range(4)] # Multiple values, "if" filters
[[0, 0], [1, 1], [4, 8], [9, 27]]
>>> [[x, x / 2, x * 2] for x in range(−6, 7, 2) if x > 0]
[[2, 1, 4], [4, 2, 8], [6, 3, 12]]
```

Comprehension syntax can also be used to create sets and dictionaries



#### Dictionaries

Dictionaries, the only mapping type in Python’s core objects set, are also mutable: like lists, they may be changed in place and can grow and shrink on demand. Also like lists, they are a flexible tool for representing collections.

##### Mapping Operations

Dictionaries are useful anytime we need to associate a set of values with keys.

```python
>>> D = {'food': 'Spam', 'quantity': 4, 'color': 'pink'}

>>> D['food'] # Fetch value of key 'food'
'Spam'
>>> D['quantity'] += 1 # Add 1 to 'quantity' value
>>> D
{'color': 'pink', 'food': 'Spam', 'quantity': 5}
```



Dictionaries built up in different ways

```python
>>> D = {}
>>> D['name'] = 'Bob' # Create keys by assignment
>>> D['job'] = 'dev'
>>> D['age'] = 40
>>> D
{'age': 40, 'job': 'dev', 'name': 'Bob'}
>>> print(D['name'])
Bob
```

As we’ll learn later, we can also make dictionaries by passing to the dict type name either keyword arguments.

```python
>>> bob1 = dict(name='Bob', job='dev', age=40) # Keywords
>>> bob1
{'age': 40, 'name': 'Bob', 'job': 'dev'}
>>> bob2 = dict(zip(['name', 'job', 'age'], ['Bob', 'dev', 40])) # Zipping
>>> bob2
{'job': 'dev', 'name': 'Bob', 'age': 40}
```

Notice how the left-to-right order of dictionary keys is scrambled



##### Nesting Revisited

```python
>>> rec = {'name': {'first': 'Bob', 'last': 'Smith'},
'jobs': ['dev', 'mgr'],
'age': 40.5}
```

Here, we again have a three-key dictionary at the top (keys “name,” “jobs,” and “age”), but the values have become more complex: a nested dictionary for the name to support multiple parts, and a nested list for the jobs to support multiple roles and future expansion.

```python
>>> rec['name'] # 'name' is a nested dictionary
{'last': 'Smith', 'first': 'Bob'}
>>> rec['name']['last'] # Index the nested dictionary
'Smith'
>>> rec['jobs'] # 'jobs' is a nested list
['dev', 'mgr']
>>> rec['jobs'][-1] # Index the nested list
'mgr'
>>> rec['jobs'].append('janitor') # Expand Bob's job description in place
>>> rec
{'age': 40.5, 'jobs': ['dev', 'mgr', 'janitor'], 'name': {'last': 'Smith',
'first': 'Bob'}}
```

Just as importantly, in a lower-level language we would have to be careful to clean up all of the object’s space when we no longer need it. In Python, when we lose the last reference to the object—by assigning its variable to something else, for example—all of the memory space occupied by that object’s structure is automatically cleaned up for us

```python
>>> rec = 0 # Now the object's space is reclaimed
```



##### Missing Keys: if Tests

It’s usually a programming error to fetch something that isn’t really in the dictionary.

The dictionary **in** membership expression allows us to query the existence of a key and branch on the result with a Python **if** statement.

```python
>>> 'f' in D
False

if not 'f' in D: # Python's sole selection statement
	print('missing')
```

There are a variety of ways to avoid accessing nonexistent keys in the dictionaries

```python
>>> value = D.get('x', 0) # Index but with a default
>>> value
0
>>> value = D['x'] if 'x' in D else 0 # if/else expression form
>>> value
0
```



##### Sorting Keys: for Loops

To impose an ordering on a dictionary’s items

```python
>>> D = {'a': 1, 'b': 2, 'c': 3}
>>> D
{'a': 1, 'c': 3, 'b': 2}

>>> Ks = list(D.keys()) # Unordered keys list
>>> Ks # A list in 2.X, "view" in 3.X: use list()
['a', 'c', 'b']

>>> Ks.sort() # Sorted keys list
>>> Ks
['a', 'b', 'c']

>>> for key in Ks: # Iterate though sorted keys
		print(key, '=>', D[key]) # <== press Enter twice here (3.X print)
a => 1
b => 2
c => 3
```



##### Iteration and Optimization

```python
>>> squares = [x ** 2 for x in [1, 2, 3, 4, 5]]
>>> squares
[1, 4, 9, 16, 25]

>>> squares = []
>>> for x in [1, 2, 3, 4, 5]: # This is what a list comprehension does
squares.append(x ** 2) # Both run the iteration protocol internally
>>> squares
[1, 4, 9, 16, 25]
```

The list comprehension, though, and related functional programming tools like map and filter, will often run faster than a for loop today on some types of code





#### Tuples

The tuple object (pronounced “toople” or “tuhple,” depending on whom you ask) is roughly like a list that cannot be changed

```python
>>> T = (1, 2, 3, 4) # A 4-item tuple
>>> len(T) # Length
4
>> T + (5, 6) # Concatenation
(1, 2, 3, 4, 5, 6)
>>> T[0] # Indexing, slicing, and more
1

>>> T.index(4) # Tuple methods: 4 appears at offset 3
3
>>> T.count(4) # 4 appears once
1

>>> T[0] = 2 # Tuples are immutable
...error text omitted...
TypeError: 'tuple' object does not support item assignment
>>> T = (2,) + T[1:] # Make a new tuple for a new value
>>> T
(2, 2, 3, 4)
```

Like lists and dictionaries, tuples support mixed types and nesting, but they don’t grow and shrink because they are immutable







#### Files

To create a file object, you call the built-in open function, passing in an external filename and an optional processing mode as strings.

```python
>>> f = open('data.txt', 'w') # Make a new file in output mode ('w' is write)
>>> f.write('Hello\n') # Write strings of characters to it
6
>>> f.write('world\n') # Return number of items written in Python 3.X
6
>>> f.close()

>>> f = open('data.txt') # 'r' (read) is the default processing mode
>>> text = f.read() # Read entire file into a string
>>> text
'Hello\nworld\n'
>>> print(text) # print interprets control characters
Hello
world
>>> text.split() # File content is always a string
['Hello', 'world']
```

We use 

```python
>>> dir(f)
```

to check all the method.



##### Binary Bytes Files

**Text files** represent content as normal str strings and perform Unicode encoding and decoding automatically when writing and reading data, while **binary files** represent content as a special bytes string and allow you to access file content unaltered.

```python
>>> import struct
>>> packed = struct.pack('>i4sh', 7, b'spam', 8) # Create packed binary data
>>> packed # 10 bytes, not objects or text
b'\x00\x00\x00\x07spam\x00\x08'
>>>
>>> file = open('data.bin', 'wb') # Open binary output file
>>> file.write(packed) # Write packed binary data
10
>>> file.close()

>>> data = open('data.bin', 'rb').read() # Open/read binary data file
>>> data # 10 bytes, unaltered
b'\x00\x00\x00\x07spam\x00\x08'
>>> data[4:8] # Slice bytes in the middle
b'spam'
>>> list(data) # A sequence of 8-bit bytes
[0, 0, 0, 7, 115, 112, 97, 109, 0, 8]
>>> struct.unpack('>i4sh', data) # Unpack into objects again
(7, b'spam', 8)
```



##### Unicode Text Files

```python
>>> S = 'sp\xc4m' # Non-ASCII Unicode text
>>> S
'spÄm'
>>> S[2] # Sequence of characters
'Ä'
>>> file = open('unidata.txt', 'w', encoding='utf-8') # Write/encode UTF-8 text
>>> file.write(S) # 4 characters written
4
>>> file.close()
>>> text = open('unidata.txt', encoding='utf-8').read() # Read/decode UTF-8 text
>>> text
'spÄm'
>>> len(text) # 4 chars (code points)
4
```





#### Other Core Types

##### Sets

You create sets by calling the built-in set function or using new set literals and expressions.

```python
>>> X = set('spam') # Make a set out of a sequence in 2.X and 3.X
>>> Y = {'h', 'a', 'm'} # Make a set with set literals in 3.X and 2.7
>>> X, Y # A tuple of two sets without parentheses
({'m', 'a', 'p', 's'}, {'m', 'a', 'h'})
>>> X & Y # Intersection
{'m', 'a'}
>>> X | Y # Union
{'m', 'h', 'a', 'p', 's'}
>>> X - Y
{'p', 's'}
>>> X > Y # Superset
False
>>> {n ** 2 for n in [1, 2, 3, 4]} # Set comprehensions in 3.X and 2.7
{16, 1, 4, 9}

>>> list(set([1, 2, 1, 3, 1])) # Filtering out duplicates (possibly reordered)
[1, 2, 3]
>>> set('spam') - set('ham') # Finding differences in collections
{'p', 's'}
>>> set('spam') == set('asmp') # Order-neutral equality tests (== is False)
True
```

It support **in** member function

```python
>>> 'p' in set('spam'), 'p' in 'spam', 'ham' in ['eggs', 'spam', 'ham']
(True, True, True)
```



##### decimal numbers

fixed-precision floating-point numbers, and fraction numbers

```python
>>> 1 / 3 # Floating-point (add a .0 in Python 2.X)
0.3333333333333333
>>> (2/3) + (1/2)
1.1666666666666665
>>> import decimal # Decimals: fixed precision
>>> d = decimal.Decimal('3.141')
>>> d + 1
Decimal('4.141')
>>> decimal.getcontext().prec = 2
>>> decimal.Decimal('1.00') / decimal.Decimal('3.00')
Decimal('0.33')
>>> from fractions import Fraction # Fractions: numerator+denominator
>>> f = Fraction(2, 3)
>>> f + 1
Fraction(5, 3)
>>> f + Fraction(1, 2)
Fraction(7, 6)
```



##### Booleans

it has long supported a special placeholder object called **None** commonly used to initialize names and objects.

```python
>>> 1 > 2, 1 < 2 # Booleans
(False, True)
>>> bool('spam') # Object's Boolean value
True
>>> X = None # None placeholder
>>> print(X)
None
>>> L = [None] * 100 # Initialize a list of 100 Nones
>>> L
[None, None, None, None, None, None, None, None, None, None, None, None,
None, None, None, None, None, None, None, None, ...a list of 100 Nones...]
```



##### How to Break Your Code’s Flexibility

The **type** object, returned by the **type** built-in function, is an object that gives the type of another object.

```python
>>> type(L) # 3.X: types are classes, and vice versa
<class 'list'>
>>> type(type(L)) # See Chapter 32 for more on class types
<class 'type'>

>>> if type(L) == type([]): # Type testing, if you must...
print('yes')
yes
>>> if type(L) == list: # Using the type name
print('yes')
yes
>>> if isinstance(L, list): # Object-oriented tests
print('yes')
yes
```



##### User-Defined Classes

```python
class Worker:
		def __init__(self, name, pay): # Initialize when created
			self.name = name # self is the new object
            self.pay = pay
        def lastName(self):
            return self.name.split()[-1] # Split string on blanks
        def giveRaise(self, percent):
            self.pay *= (1.0 + percent) # Update pay in place
```







### Numeric Types

It includes:

• Integer and floating-point objects
• Complex number objects(3+4j, 3.0+4.0j, 3J)
• Decimal: fixed-precision objects
• Fraction: rational number objects
• Sets: collections with numeric operations
• Booleans: true and false
• Built-in functions and modules: round, math, random, etc.
• Expressions; unlimited integer precision; bitwise operations; hex, octal, and binary formats
• Third-party extensions: vectors, libraries, visualization, plotting, etc.



#### Numeric Type Basic

##### Built-in Numeric Tools

Expression operators
	+, -, *, /, >>, **, &, etc.
Built-in mathematical functions
	pow, abs, round, int, hex, bin, etc.
Utility modules
	random, math, etc.



##### Python Expression Operators

| Operators | Description                                    |
| --------- | ---------------------------------------------- |
| x or y    | Logical OR (y is evaluated only if x is false) |
| x and y   | Logical AND (y is evaluated only if x is true) |
| not x     | Logical negation                               |
| x is y    | x is not y Object identity tests               |
| x in y    | x not in y Membership (iterables, sets)        |
|           |                                                |
|           |                                                |
|           |                                                |
|           |                                                |



##### Mixed types are converted up

Python first converts operands up to the type of the most complicated operand, and then performs the math on same-type operands. This behavior is similar to type conversions in the C language.

In general, Python does not convert across any other type boundaries automatically.







#### Numbers in Action

##### Variables and Basic Expressions

```python
>>> a = 3 # Name created: not declared ahead of time
>>> b = 4
```



##### Numeric Display Formats

There are more ways to display the bits of a number inside your computer than using print and automatic echoes.

```python
>>> num = 1 / 3.0
>>> num # Auto-echoes
0.3333333333333333
>>> print(num) # Print explicitly
0.3333333333333333
>>> '%e' % num # String formatting expression
'3.333333e-01'
>>> '%4.2f' % num # Alternative floating-point format(4 is the total length and 2 is the 					 digit after the point)
'0.33'
>>> '{0:4.2f}'.format(num) # String formatting method: Python 2.6, 3.0, and later
'0.33'
```



##### Comparisons: Normal and Chained

Python also allows us to chain multiple comparisons together to perform range tests.

The expression (A < B < C), for instance, tests whether B is between A and C; it is equivalent to the Boolean test (A < B and B < C) .

```python
>>> 1 == 2 < 3 # Same as: 1 == 2 and 2 < 3
False # Not same as: False < 3 (which means 0 < 3, which is true!)
```

Floating-point numbers may not always work as you’d expect, and may require conversions or other massaging to be compared meaningfully:

```python
>>> 1.1 + 2.2 == 3.3 # Shouldn't this be True?...
False
>>> 1.1 + 2.2 # Close to 3.3, but not exactly: limited precision
3.3000000000000003
>>> int(1.1 + 2.2) == int(3.3) # OK if convert: see also round, floor, trunc ahead
True # Decimals and fractions (ahead) may help here too
```



##### Division: Classic, Floor, and True

**X / Y**: Classic and true division. It performs true division, always keeping remainders in floating-point results, regardless of types.

**X // Y**: Floor division. This operator always truncates fractional remainders down to their floor, regardless of types.

```python
>>> 10 / 4 # Differs in 3.X: keeps remainder
2.5
>>> 10 / 4.0 # Same in 3.X: keeps remainder
2.5
>>> 10 // 4 # Same in 3.X: truncates remainder
2
>>> 10 // 4.0 # Same in 3.X: truncates to floor
2.0
```



##### Other Built-in Numeric Tools

```python
>>> import math
>>> math.pi, math.e # Common constants
(3.141592653589793, 2.718281828459045)
>>> math.sin(2 * math.pi / 180) # Sine, tangent, cosine
0.03489949670250097
>>> math.sqrt(144), math.sqrt(2) # Square root
(12.0, 1.4142135623730951)
>>> pow(2, 4), 2 ** 4, 2.0 ** 4.0 # Exponentiation (power)
(16, 16, 16.0)
>>> abs(-42.0), sum((1, 2, 3, 4)) # Absolute value, summation
(42.0, 10)
>>> min(3, 1, 2, 4), max(3, 1, 2, 4) # Minimum, maximum
(1, 4)
```



```python
>>> import random
>>> random.random()
0.5566014960423105
>>> random.random() # Random floats, integers, choices, shuffles
0.051308506597373515
>>> random.randint(1, 10)
5
>>> random.randint(1, 10)
9

>>> random.choice(['Life of Brian', 'Holy Grail', 'Meaning of Life'])
'Holy Grail'
>>> random.choice(['Life of Brian', 'Holy Grail', 'Meaning of Life'])
'Life of Brian'
>>> suits = ['hearts', 'clubs', 'diamonds', 'spades']
>>> random.shuffle(suits)
>>> suits
['spades', 'hearts', 'diamonds', 'clubs']
>>> random.shuffle(suits)
>>> suits
['clubs', 'diamonds', 'hearts', 'spades']
```



#### Other Numeric Types

##### Decimal Type

Decimals are fixed-precision floating-point values. 

Floating-point math is less than exact because of the limited space used to store values.

```python
>>> print(0.1 + 0.1 + 0.1 - 0.3) # Pythons < 2.7, 3.1
5.55111512313e-17
```

However, with decimals, the result can be dead-on:

```python
>>> Decimal('0.1') + Decimal('0.10') + Decimal('0.10') - Decimal('0.30')
Decimal('0.00')
```

As shown here, we can make decimal objects by calling the Decimal constructor function in the decimal module and passing in strings that have the desired number of decimal digits for the resulting object (using the **str** function to convert floating-point values to strings if needed). When decimals of different precision are mixed in expressions, Python converts up to the largest number of decimal digits automatically.

```python
>>> Decimal(0.1) + Decimal(0.1) + Decimal(0.1) - Decimal(0.3)
Decimal('2.775557561565156540423631668E-17') #convert from float
```



###### Setting decimal precision globally

```python
>>> import decimal
>>> decimal.Decimal(1) / decimal.Decimal(7) # Default: 28 digits
Decimal('0.1428571428571428571428571429')
>>> decimal.getcontext().prec = 4 # Fixed precision
>>> decimal.Decimal(1) / decimal.Decimal(7)
Decimal('0.1429')
>>> Decimal(0.1) + Decimal(0.1) + Decimal(0.1) - Decimal(0.3) # Closer to 0
Decimal('1.110E-17')
```

It’s also possible to reset precision temporarily by using the with context manager statement.(More knowledge in Chapter 34)



##### Fraction Type

```python
>>> from fractions import Fraction
>>> x = Fraction(1, 3) # Numerator, denominator
>>> y = Fraction(4, 6) # Simplified to 2, 3 by gcd
>>> x
Fraction(1, 3)
>>> y
Fraction(2, 3)
>>> print(y)
2/3

>>> x + y
Fraction(1, 1)
>>> x − y # Results are exact: numerator, denominator
Fraction(−1, 3)
>>> x * y
Fraction(2, 9)
```

Fraction objects can also be created from floating-point number strings.

```python
>>> Fraction('.25')
Fraction(1, 4)
>>> Fraction('1.25')
Fraction(5, 4)
>>>
>>> Fraction('.25') + Fraction('1.25')
Fraction(3, 2)
```



###### Fraction conversions and mixed types

```python
>>> (2.5).as_integer_ratio() # float object method
(5, 2)
>>> f = 2.5
>>> z = Fraction(*f.as_integer_ratio()) # Convert float -> fraction: two args
>>> z # Same as Fraction(5, 2)
Fraction(5, 2)
>>> x # x from prior interaction
Fraction(1, 3)
>>> x + z
Fraction(17, 6) # 5/2 + 1/3 = 15/6 + 2/6
>>> float(x) # Convert fraction -> float
0.3333333333333333
>>> float(z)
2.5
>>> float(x + z)
2.8333333333333335
>>> 17 / 6
2.8333333333333335
>>> Fraction.from_float(1.75) # Convert float -> fraction: other way
Fraction(7, 4)
```



##### Sets

an unordered collection of unique and immutable objects that supports operations corresponding to mathematical set theory.

```python
>>> x = set('abcde')
>>> y = set('bdxyz')
>>> x
set(['a', 'c', 'b', 'e', 'd'])

>>> x − y # Difference
set(['a', 'c', 'e'])
>>> x | y # Union
set(['a', 'c', 'b', 'e', 'd', 'y', 'x', 'z'])
>>> x & y # Intersection
set(['b', 'd'])
>>> x ^ y # Symmetric difference (XOR)
set(['a', 'c', 'e', 'y', 'x', 'z'])
>>> x > y, x < y # Superset, subset
(False, False)

>>> 'e' in x # Membership (sets)
True
>>> 'e' in 'Camelot', 22 in [11, 22, 33] # But works on other types too
(True, True)

>>> z = x.intersection(y) # Same as x & y
>>> z
set(['b', 'd'])
>>> z.add('SPAM') # Insert one item
>>> z
set(['b', 'd', 'SPAM'])
>>> z.update(set(['X', 'Y'])) # Merge: in-place union
>>> z
set(['Y', 'X', 'b', 'd', 'SPAM'])
>>> z.remove('b') # Delete one item
>>> z
set(['Y', 'X', 'd', 'SPAM'])
```

As iterable containers, sets can also be used in operations such as len, for loops, and list comprehensions. Because they are unordered, though, they don’t support sequence operations like indexing and slicing:

```python
>>> for item in set('abc'): print(item * 3)
aaa
ccc
bbb
```



```python
>>> S = set([1, 2, 3])
>>> S | set([3, 4]) # Expressions require both to be sets
set([1, 2, 3, 4])
>>> S | [3, 4]
TypeError: unsupported operand type(s) for |: 'set' and 'list'
>>> S.union([3, 4]) # But their methods allow any iterable
set([1, 2, 3, 4])
>>> S.intersection((1, 3, 5))
set([1, 3])
>>> S.issubset(range(-5, 5))
True
```

###### Set in Python 3.X and 2.7

```python
{1, 2, 3, 4} # Newer set literals (2.7, 3.X)
```

**comprehensions**

```python
>>> {x ** 2 for x in [1, 2, 3, 4]} # 3.X/2.7 set comprehension
{16, 1, 4, 9}

>>> {x for x in 'spam'} # Same as: set('spam')
{'m', 's', 'p', 'a'}
>>> {c * 4 for c in 'spam'} # Set of collected expression results
{'pppp', 'aaaa', 'ssss', 'mmmm'}
>>> {c * 4 for c in 'spamham'}
```

###### Practical

Because items are stored only once in a set, sets can be used to **filter duplicates** out of other collections. (items may be reordered in the process)

```python
>>> L = [1, 2, 1, 3, 2, 4, 5]
>>> set(L)
{1, 2, 3, 4, 5}
>>> L = list(set(L)) # Remove duplicates
>>> L
[1, 2, 3, 4, 5]
```

Sets can be used to **isolate differences** in lists, strings, and other iterable objects

```python
>>> set([1, 3, 5, 7]) - set([1, 2, 4, 5, 6]) # Find list differences
{3, 7}
>>> set('abcdefg') - set('abdghij') # Find string differences
{'c', 'e', 'f'}
>>> set('spam') - set(['h', 'a', 'm']) # Find differences, mixed
{'p', 's'}
>>> set(dir(bytes)) - set(dir(bytearray)) # In bytes but not bytearray
{'__getnewargs__'}
>>> set(dir(bytearray)) - set(dir(bytes))
{'append', 'copy', '__alloc__', '__imul__', 'remove', 'pop', 'insert', ...more...]
```

You can also use sets to perform **order-neutral equality** tests by converting to a set before the test, because order doesn’t matter in a set.

```python
>>> L1, L2 = [1, 3, 5, 2, 4], [2, 5, 3, 4, 1]
>>> L1 == L2 # Order matters in sequences
False
>>> set(L1) == set(L2) # Order-neutral equality
True
>>> sorted(L1) == sorted(L2) # Similar but results ordered
True
>>> 'spam' == 'asmp', set('spam') == set('asmp'), sorted('spam') == sorted('asmp')
(False, True, True)
```



##### Booleans

```python
>>> type(True)
<class 'bool'>
>>> isinstance(True, int)
True
>>> True == 1 # Same value
True
>>> True is 1 # But a different object: see the next chapter
False
>>> True or False # Same as: 1 or 0
True
>>> True + 4 # (Hmmm)
5
```









### The Dynamic Typing Interlude

#### The Case of the Missing Declaration Statements

In Python, types are determined automatically at runtime, not in response to declarations in your code.

##### Variables, Objects, and References

Variables are created when assigned, can reference any type of object, and must be assigned before they are referenced.

```python
>>> a = 3 # Assign a name to an object
```

Python will perform three distinct steps to carry out the request.

1. Create an object to represent the value 3.
2. Create the variable a, if it does not yet exist.
3. Link the variable a to the new object 3.

##### Types Live with Objects, Not Variables

```python
>>> a = 3 # It's an integer
>>> a = 'spam' # Now it's a string
>>> a = 1.23 # Now it's a floating point
```

Names have no types; as stated earlier, types live with objects, not names. In the preceding listing, we’ve simply changed a to reference different objects.

##### Objects Are Garbage-Collected

The answer is that in Python, whenever a name is assigned to a new object, the space held by the prior object is reclaimed if it is not referenced by any other name or object. This automatic reclamation of objects’ space is known as **garbage collection**.

##### Shared References

```python
>>> a = 3
>>> b = a
```

The second command causes Python to create the variable b; the variable a is being used and not assigned here, so it is replaced with the object it references (3), and b is made to reference that object. The net effect is that the variables a and b wind up referencing the **same** object.

Note that the names a and b are not linked to each other directly when this happens; in fact, there is no way to ever link a variable to another variable in Python.

##### Shared References and In-Place Changes

```python
>>> L1 = [2, 3, 4]
>>> L2 = L1
>>> L1[0] = 24 # An in-place change
>>> L1 # L1 is different
[24, 3, 4]
>>> L2 # But so is L2!
[24, 3, 4]
```

This behavior only occurs for mutable objects that support in-place changes. It’s also just the default: if you don’t want such behavior, you can request that Python **copy objects** instead of making references.

```python
>>> L1 = [2, 3, 4]
>>> L2 = L1[:] # Make a copy of L1 (or list(L1), copy.copy(L1), etc.)
>>> L1[0] = 24
>>> L1
[24, 3, 4]
>>> L2 # L2 is not changed
[2, 3, 4]
```

Note that this slicing technique won’t work on the other major mutable core types, dictionaries and sets, because they are not sequences. To copy a dictionary or set, instead use their X.copy() method call (lists have one as of Python 3.3 as well), or pass the original object to their type names, dict and set.

```python
import copy
X = copy.copy(Y) # Make top-level "shallow" copy of any object Y
X = copy.deepcopy(Y) # Make deep copy of any object Y: copy all nested parts
```

##### Shared References and Equality

```python
>>> L = [1, 2, 3]
>>> M = L # M and L reference the same object
>>> L == M # Same values
True
>>> L is M # Same objects
True
```

The first technique here, the == operator, tests whether the two referenced objects have the same values.

The second method, the is operator, instead tests for object identity—it returns True only if both names point to the exact same object. It returns False if the names point to equivalent but different objects

```python
>>> L = [1, 2, 3]
>>> M = [1, 2, 3] # M and L reference different objects
>>> L == M # Same values
True
>>> L is M # Different objects
False

>>> X = 42
>>> Y = 42 # Should be two different objects
>>> X == Y
True
>>> X is Y # Same object anyhow: caching at work!
True
```

In fact, if you really want to look under the hood, you can always ask Python how many references there are to an object: the **getrefcount** function in the standard **sys** module returns the object’s reference count.









### String Fundamentals

Python has no distinct type for individual characters; instead, you just use one-character strings.

| operation          | Interpretation           |
| ------------------ | ------------------------ |
| S = 's\np\ta\x00m' | Escape sequences         |
| S = r'\temp\spam'  | Raw strings (no escapes) |
| B = b'sp\xc4m'     | Byte strings             |
| U = u'sp\u00c4m'   | Unicode strings          |

#### String in Actions

##### Indexing and Slicing

X[1:10:2] will fetch every other item in X from offsets 1–9; that is, it will collect the items at offsets 1, 3, 5, 7, and 9.

```python
>>> S = 'abcdefghijklmnop'
>>> S[1:10:2] # Skipping items
'bdfhj'
>>> S[::2]
'acegikmo'
```

X[::-1] gains the string in reverse order

```python
>>> S = 'hello'
>>> S[::−1] # Reversing items
'olleh'

>>> S = 'abcedfg'
>>> S[5:1:−1] # Bounds roles differ
'fdec'
```



##### String Conversion Tools

```python
>>> int("42"), str(42) # Convert from/to string
(42, '42')
>>> repr(42) # Convert to as-code string
'42'

>>> S = "42"
>>> I = 1
>>> S + I
TypeError: Can't convert 'int' object to str implicitly
>>> int(S) + I # Force addition
43
>>> S + str(I) # Force concatenation
'421'
```



##### Changing Strings

```python
>>> S = 'spam'
>>> S = S + 'SPAM!' # To change a string, make a new one
>>> S
'spamSPAM!'

>>> S = S[:4] + 'Burger' + S[−1]  # Replace four chars
>>> S
'spamBurger!'

>>> S = 'splot'
>>> S = S.replace('pl', 'pamal')
>>> S
'spamalot'
```

It’s also possible to build up new text values with string formatting expressions.

```python
>>> 'That is %d %s bird!' % (1, 'dead') # Format expression: all Pythons
That is 1 dead bird!
>>> 'That is {0} {1} bird!'.format(1, 'dead') # Format method in 2.6, 2.7, 3.X
'That is 1 dead bird!'
```



#### String Methods

##### Method Call Syntax

```python
object.method(arguments)
```

##### Changing Strings

1. ```python
   >>> S = 'spammy'
   >>> S = S[:3] + 'xx' + S[5:] # Slice sections from S
   >>> S
   'spaxxy'
   ```

2. ```python
   >>> S = 'xxxxSPAMxxxxSPAMxxxx'
   >>> where = S.find('SPAM') # Search for position
   >>> where # Occurs at offset 4
   4
   >>> S = S[:where] + 'EGGS' + S[(where+4):]
   >>> S
   'xxxxEGGSxxxxSPAMxxxx'
   ```

3. ```python
   >>> S = 'spammy'
   >>> L = list(S)
   >>> L
   ['s', 'p', 'a', 'm', 'm', 'y']
   >>> L[3] = 'x' # Works for lists, not strings
   >>> L[4] = 'x'
   >>> L
   ['s', 'p', 'a', 'x', 'x', 'y']
   >>> S = ''.join(L)  # converts back to a string
   >>> S
   'spaxxy'
   ```

##### Parsing Text

The string split method chops up a string into a list of substrings, around a delimiter
string.

```python
>>> line = 'aaa bbb ccc'
>>> cols = line.split()
>>> cols
['aaa', 'bbb', 'ccc']

>>> line = 'bob,hacker,40'
>>> line.split(',')
['bob', 'hacker', '40']

>>> line = "i'mSPAMaSPAMlumberjack"
>>> line.split("SPAM")
["i'm", 'a', 'lumberjack']
```

##### Other Common String Methods in Action

```python
>>> line = "The knights who say Ni!\n"
>>> line.rstrip()
'The knights who say Ni!'
>>> line.upper()
'THE KNIGHTS WHO SAY NI!\n'
>>> line.isalpha()
False
>>> line.endswith('Ni!\n')
True
>>> line.startswith('The')
True

>>> line
'The knights who say Ni!\n'
>>> line.find('Ni') != −1 # Search via method call or expression
True
>>> 'Ni' in line
True
>>> sub = 'Ni!\n'
>>> line.endswith(sub) # End test via method call or slice
True
>>> line[-len(sub):] == sub
True
```



#### String Formatting Expressions

String formatting expressions: *'...%s...' % (values)*

```python
>>> exclamation = 'Ni'
>>> 'The knights who say %s!' % exclamation # String substitution
'The knights who say Ni!'
>>> '%d %s %g you' % (1, 'spam', 4.0) # Type-specific substitutions
'1 spam 4 you'
>>> '%s -- %s -- %s' % (42, 3.14159, [1, 2, 3]) # All types match a %s target
'42 -- 3.14159 -- [1, 2, 3]'
```

- **s** String (or any object’s str(X) string)
- **r** Same as s, but uses repr, not str
- **c** Character (int or str)
- **d** Decimal (base-10 integer)
- **i** Integer
- **u** Same as d (obsolete: no longer unsigned)
- **o** Octal integer (base 8)
- **x** Hex integer (base 16)
- **X** Same as x, but with uppercase letters
- **e** Floating point with exponent, lowercase
- **E** Same as e, but uses uppercase letters
- **f** Floating-point decimal
- **F** Same as f, but uses uppercase letters
- **g** Floating-point e or f
- **G** Floating-point E or F
- **%** Literal % (coded as %%)

The general structure of conversion targets looks like this:

*%\[(keyname)]\[flags]\[width][.precision]typecode*

Provide a key name for indexing the dictionary used on the right side of the expression
List flags that specify things like left justification (−), numeric sign (+), a blank before positive numbers and a – for negatives (a space), and zero fills (0)
Give a total minimum field width for the substituted text
Set the number of digits (precision) to display after a decimal point for floating-point numbers

e.g.

```

```



##### Dictionary-Based Formatting Expressions

*'%([key])...' %[dictionary]*

```python
>>> '%(qty)d more %(food)s' % {'qty': 1, 'food': 'spam'}
'1 more spam'
```





#### String Formatting Method Calls

```python
>>> template = '{0}, {1} and {2}' # By position
>>> template.format('spam', 'ham', 'eggs')
'spam, ham and eggs'
>>> template = '{motto}, {pork} and {food}' # By keyword
>>> template.format(motto='spam', pork='ham', food='eggs')
'spam, ham and eggs'
>>> template = '{motto}, {0} and {food}' # By both
>>> template.format('ham', motto='spam', food='eggs')
'spam, ham and eggs'
>>> template = '{}, {} and {}' # By relative position
>>> template.format('spam', 'ham', 'eggs') # New in 3.1 and 2.7
'spam, ham and eggs'

>>> template = '%s, %s and %s' # Same via expression
>>> template % ('spam', 'ham', 'eggs')
'spam, ham and eggs'
>>> template = '%(motto)s, %(pork)s and %(food)s'
>>> template % dict(motto='spam', pork='ham', food='eggs')
'spam, ham and eggs'
```

Just as with the % expression and other string methods, format creates and returns a new string object, which can be printed immediately or saved for further work



##### Adding Keys, Attributes, and Offsets

Square brackets name dictionary keys and dots denote object attributes of an item referenced by position or keyword.

```python
>>> import sys
>>> 'My {1[kind]} runs {0.platform}'.format(sys, {'kind': 'laptop'})
'My laptop runs win32'

>>> 'My {map[kind]} runs {sys.platform}'.format(sys=sys, map={'kind': 'laptop'})
'My laptop runs win32'
```





