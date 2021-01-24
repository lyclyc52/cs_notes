# Python Stanford

Python strings are Unicode by default (yes – this means we can use emoji in Python strings! )



**List**

can use extend() func to append elements to the list

```python
>>> numbers = [1, 2, 3]
>>> numbers.extend(4)
>>> numbers
[1, 2, 3, 4]
>>> numbers.extend([5, 6, 7])
>>> numbers
[1, 2, 3, 4, 5, 6, 7]
```

List methods

```python
# Extend list by appending elements from the iterable
my_list.extend(iterable)

# Insert object before index
my_list.insert(index, object)

# Remove first occurrence of value, or raise ValueError
my_list.remove(value)

# Remove all items
my_list.clear()

# Return number of occurrences of value
my_list.count(value)

# Return first index of value, or raise ValueError
my_list.index(value, [start, [stop]])

# Remove, return item at index (def. last) or IndexError
my_list.pop([index])

# Stable sort *in place*
my_list.sort(key=None, reverse=False)

# Reverse *in place*.
my_list.reverse()

# Membership (in)
0 in [] # => False
'y' in 'python' # => True
'minutes' in [4, 5, 'seconds'] # => False
```







### Dictionary

Mutable map from hashable values to arbitrary objects

```python
#create a dictionary
empty = {}
type(empty) # => dict
empty == dict() # => True
a = dict(one=1, two=2, three=3)
b = {"one": 1, "two": 2, "three": 3}
a == b # => True

# Get
d['one'] # => 1
d['five'] # raises KeyError

# Set
d['two'] = 22 # Modify an existing key
d['four'] = 4 # Add a n
```

The key must be hashable table.

```python
d = {"CS":[106, 107, 110], "MATH": [51, 113]}
d["COMPSCI"] # raises KeyError
#get() function can avoid the KeyError
d.get("CS") # => [106, 107, 110]
d.get("PHIL") # => None (not a KeyError!)

english_classes = d.get("ENGLISH", [])# will return an empty list
num_english = len(english_classes)
```



delete

```python
d = {"one": 1, "two": 2, "three": 3}
del d["one"]
d.pop("three", default) # => 3
d.popitem() # => ("two", 2)
```



These functions reflect the statement of the dictionary

```python
d.keys()
d.values()
d.items()
#They are special types

len(d.keys()) # => 3
('one', 1) in d.items()
for value in d.values():
 	print(value)
keys_list = list(d.keys())
```

Methods

```python
len(d)
key in d # equiv. to `key in d.keys()`
value in d.values()
d.copy()
d.clear()
for key in d: # equiv. to `for key in d.keys():`
 	print(key)
```









### Tuples

Immutable Sequence

```python
t = (1, "cat")
t = 12345, 54321, 'hello!' # it can be unpacking
x, y, z = t #:P
x # => 12345
y # => 54321
z # => 'hello!'
```

Swap value

```
x=1
y=2
x,y=y,x
```

First, y, x is packed into the tuple (2,1). Then, (2, 1) is unpacked into the variables x and y respectively.

Another example

```python
for index, color in enumerate(['red','green','blue']):
	 print(index, color)
# =>
# 0 red
# 1 green
# 2 blue
```



```python
empty = ()
singleton = ("value",)#need a comma at the end
```



```
v = ([1, 2, 3], ['a', 'b', 'c'])
v[0].append(4) # It can be changed in this way
v # => ([1, 2, 3, 4], ['a', 'b', 'c'])
```







### Set

Unordered collection of distinct hashable elements

```python
s = {1, 3, 4}

empty_set = set() #distinguish from dict
set_from_list = set([1, 2, 1, 4, 3]) # => {1, 3, 4, 2}

basket = {"apple", "orange", "apple", "pear", "banana"}
len(basket) # => 4
"orange" in basket # => True
"crabgrass" in basket # => False
for fruit in basket:
 	print(fruit, end='/')
# => pear/banana/apple/orange/
```

Method

```python
a.add('r')
a.remove('m') # raises KeyError if 'm' is not present
a.discard('x') # same as remove, except no error
a.pop() # => 's' (or 'i' or 'p')
a.clear()
len(a) # => 0

a = set("abracadabra") # {'a', 'r', 'b', 'c', 'd'}
b = set("alacazam") # {'a', 'm', 'c', 'l', 'z'}
# Set difference
a - b # => {'r', 'd', 'b'}
# Union
a | b # => {'a', 'c', 'r', 'd', 'b', 'm', 'z', 'l'}
# Intersection
a & b # => {'a', 'c'}
# Symmetric Difference
a ^ b # => {'r', 'd', 'b', 'm', 'z', 'l'}
```







### Looping Techniques

In dict

```python
knights = {'gallahad': 'the pure', 'robin': 'the brave'}
for k, v in knights.items():
 print(k, v)
# =>
# gallahad the pure
# robin the brave
```



The zip() function generates pairs of entries from its arguments.

```python
questions = ['name', 'quest', 'favorite color']
answers = ['Lancelot', 'To seek the holy grail', 'Blue']
for q, a in zip(questions, answers):
 	print('What is your {0}? {1}.'.format(q, a))
```



To loop over a sequence in reverse, first specify the sequence in a forward direction and then call the reversed() function

```python
for i in reversed(range(1, 10, 2)):
 	print(i, end=', ')
# =>
# 9, 7, 5, 3, 1,
```



To loop over a sequence in sorted order, use the sorted() function which returns a new sorted list while leaving the source unaltered

```python
basket = ['pear', 'banana', 'orange', 'pear', 'apple']
for fruit in sorted(basket):
 	print(fruit)
# =>
# apple
# banana
# orange
# pear
# pear
```







### Comprehensive

```python
[f(xs) for xs in iter if pred(xs)]
```

f(xs) is the operation for each loop variables. [] means we are building a list. Then it is like a sentence in English.

We can also use two for

```python
[(i,j) for i in range(5) for j in range(i)]
```



**Other Comprehensive**

```
# Dictionary Comprehensions
{key_func(vars):val_func(vars) for vars in iterable}
{v:k for k, v in d.items()}


# Set Comprehensions
{func(vars) for vars in iterable}
{word for word in hamlet if is_palindrome(word.lower())}
```













## Function

No return statement or just return implicitly returns None.

### Function Execution and Scopes

Function execution introduces a new local symbol table (scope)  

Variable assignments (L-values) x = 5. Add entry to local symbol table (or overwrite an existing entry). 

Variable references (R-values) print(y).

- First, look in local symbol table 
- Next, check symbol tables of enclosing functions (unusual) 
- Then, search global (top-level) symbol table 
- Finally, check builtin symbols (print, input, etc)

```python
x = 2
def foo(y):
 x = 41
 z = 5
 print(locals())
 print(globals()['x'])
 print(x, y, z)
foo(3)
# {'x': 41, 'y': 3, 'z': 5}
# 2
# 41, 3, 5
```

if statements, for loops, while loops, with statements, etc. Do not introduce a new scope



Best to think of it as pass-by-object-reference. If a mutable object is passed, caller will see changes





### Default Parameters

Valid Calls

```python
def parrot(voltage, state='…', action='…', type='…')
# 1 positional argument
parrot(1000)
# 1 keyword argument
parrot(voltage=1000)
# 2 keyword arguments
parrot(voltage=1000000, action='VOOOOOM')
# 2 keyword arguments
parrot(action='VOOOOOM', voltage=1000000)
# 3 positional arguments
parrot('a million', 'bereft of life', 'jump')
# 1 positional, 1 keyword
parrot('a thousand', state='pushing up the daisies')
```

Keyword arguments must follow positional arguments All keyword arguments must identify some parameter





### Variadic Positional Arguments

A parameter of form *args captures excess positional args. These excess arguments are bundled into an args tuple

e.g.

```python
# product accepts any number of arguments
def product(*nums, scale=1):
     p = scale
     for n in nums:
     	p *= n
     return p 

# Suppose we want a product function that works as so:
product(3, 5) # => 15
product(3, 4, 2) # => 24
product(3, 5, scale=10) # => 150

#another way
primes=[2,3,5]
product(*primes)
```







### Variadic Keyword Arguments

A parameter of the form **kwargs captures all excess keyword arguments and put them in a dict

```python
def authorize(quote, **speaker_info):
     print(">", quote)
     print("-" * (len(quote) + 2))
     for k, v in speaker_info.items():
        print(k, v, sep=': ')
        
authorize(
 "If music be the food of love, play on.",
 playwright="Shakespeare",
 act=1,
 scene=1,
 speaker="Duke Orsino"
)

# > If music be the food of love, play on.
# ----------------------------------------
# act: 1
# scene: 1
# speaker: Duke Orsino
# playwright: Shakespeare

#another way
info = {
 'sonnet': 18,
 'line': 1,
 'author': "Shakespeare"
}
authorize("Shall I compare thee to a summer's day", **info)
```

Actually the format function is

```python
fstr.format(*args, **kwargs)
```

All variables are in local symbol table

```python
x = 3
foo = 'fighter'
y = 4
learn = 2, 'fly'
z = 5
print("{z}^2 = {x}^2 + {y}^2".format(x=x, y=y, z=z))
print("{z}^2 = {x}^2 + {y}^2".format(**locals()))
```

The print func also includes *args, **kwargs

### First-Class Functions

immediately return sth. 





### Map/Filter

```python
map(func(),iter)	#go through every item in iter

>>> def square(x) :         
...     return x ** 2
...
>>> map(square, [1,2,3,4,5])
>>> list(map(square, [1,2,3,4,5]))  
[1, 4, 9, 16, 25]
```



```python
filter(pred, iter) #filter proper item in iter


def is_odd(n):
    return n % 2 == 1
 
newlist = filter(is_odd, [1, 2, 3, 4, 5, 6, 7, 8, 9, 10])
print(newlist)
#[1, 3, 5, 7, 9]
```





### Lambda Functions

```python
lambda params: expr(params)

lambda val: val ** 2
lambda x, y: x * y
lambda pair: pair[0] * pair[1]
(lambda x: x > 3)(4) # create a func object and immediately call it
```





### Iterators 

Use *next(iterator)* to yield successive values 

Raises *StopIteration* error upon termination 

Use *iter(data)* to build an iterator over a data structure

```python
it = iter([1,2,3])
next(it) # => 1
next(it) # => 2
next(it) # => 3
next(it) # raises StopIteration error
```



```python
# Return a value
max(iterable) min(iterable)
val in iterable val not in iterable
all(iterable) any(iterable)

# Return an iterable
enumerate(iterable) zip(*iterables)
map(fn, iterable) filter(pred, iterable)
```







### Generators Expression

```python
(expensive_function(data) for data in iterable)
```







### Generators

```python
def generate_ints(n):
     for i in range(n):
     yield i
g = generate_ints(3) # Doesn't start the function!
type(g) # => <class 'generator'>
next(g) # => 0
next(g) # => 1
next(g) # => 2
next(g) # raises StopIteration
```

**Reason**

- Reduces in-memory buffering 
- Avoid expensive function calls 
- Describe (finite or infinite) streams of data







### Decorators

```python
def perform_twice(fn, *args, **kwargs):
     fn(*args, **kwargs)
     fn(*args, **kwargs)
perform_twice(print, 5, 10, sep='&', end='...')
# => 5&10...5&10...

def make_divisibility_test(n):
     def divisible_by_n(m):
     	return m % n == 0
     return divisible_by_n
div_by_3 = make_divisibility_test(3)
filter(div_by_3, range(10)) # generates 0, 3, 6, 9
make_divisibility_test(5)(10) # => True
```

Use func as arguments and as return values

Decorator will change the performance of a function

```python
def debug(function):
 	def wrapper(*args, **kwargs):
 		print("Arguments:", args, kwargs)
 		return function(*args, **kwargs) # the func in decorator needs return the argu
 	return wrapper

def foo(a, b, c=1):
 	return (a + b) * c
 	
foo = debug(foo)
foo(2, 3) # prints "Arguments: (2, 3) {}"
# => returns 5
foo(2, 1, c=3) # prints "Arguments: (2, 1) {'c': 3}"
# => returns 9
print(foo) # <function debug.<locals>.wrapper at 0x...>
```

The lines

```python
def foo(a, b, c=1):
 	return (a + b) * c
 	
foo = debug(foo)
```

are equal to

```python
@debug
def foo(a, b, c=1):
 	return (a + b) * c
```



It could

- Cache function return value (memoization) 
- Set timeout for blocking function 
- Mark class properties as readonly 
- Mark methods as static methods or class methods 
- Handle administrative logic (authorization, routing, etc)















## OOP

An object has identity 

A name is a reference to an object 

A namespace is an associative mapping from names to objects 

An attribute is any name following a dot ('.')

```python
class ClassName:
     <statement>
     <statement>
     ...
```

Statements are usually assignments or function definitions 

Entering a class definition creates a new "namespace"-ish

Exiting a class definition creates a class object 

Defining a class == creating a class object (like int, str) Defining a class != instantiating a class





### Class Objects

#### Class Attribute References

```python
class MyClass:
     """A simple example class."""
     num = 12345
     def greet(self):
     return "Hello world!"
```

#### Class Instantiation

```python
x = MyClass(args)

#It is sth. like
float('3.5')
```

Constructor

```
class Complex:
    def __init__(self, realpart=0, imagpart=0):
 		self.real = realpart
 		self.imag = imagpart
```

Class instantiation calls the special method *\__init__* if it exists, supplying a freshly-minted instance object as the first parameter

#### Instance Objects

```
class MyOtherClass:
    num = 12345
    def __init__(self):
    	self.num = 0
```



```python
class MyOtherClass:
    num = 12345
    def __init__(self):
    	self.num = 0
        
x = MyOtherClass()
print(x.num) # 0
del x.num
print(x.num) # 0
```

Attribute references first search the instance's *\__dict__* attribute, then the class object



```python
# You can set attributes on instance (and class) objects when ever you want
c.counter = 1
```





### Methods vs. Functions

A method is like a function attached to an object

```python
p = Pizza(14, ("Pepperoni", "Olives"), slices=12)
print(Pizza.eat_slice)
# => <function Pizza.eat_slice>

print(p.eat_slice)
# => <bound method Pizza.eat_slice of 14" Pizza>

method = p.eat_slice
print(method.__self__) # => 14" Pizza
print(method.__func__) # => <function Pizza.eat_slice>

p.eat_slice() # Implicitly calls Pizza.eat_slice(p)
```



### Class and Instance Attributes

```python
class Dog:
 # Let's try a default argument!
 def __init__(self, name='Mr. B', tricks=[]):
	self.name = name
	self.tricks = tricks

 def teach_trick(self, trick):
	self.tricks.append(trick)
```

In that case, trick is still share by all dogs

The solution is 

```python
class Dog:
	def __init__(self, name):
    self.name = name
    self.tricks = [] # New list for each dog

	def teach_trick(self, trick):
		self.tricks.append(trick)
```







### Privacy and Style

A method's first parameter should always be self

Prefix private attributes with an underscore (e.g. _spam)

Use double underscores (__spam) for more obfuscation

```python
class MyClass:
    CLASS_LEVEL_CONSTANT = 100

    def __init__(self, arg1, arg2=0):
    	self.foo = arg1
        self._bar = arg2
        self.baz = []
        
    def my_first_method(self, args):
    	do_something_with_self_and_args()
    	
    def my_second_method(self, args):
 	    do_something_else_with_self_and_args()
	def __str__(self):
 	    return string_representation_of_self
```







### Inheritance

```python
class DerivedClassName(BaseClassName):
```

All class objects inherit from object (default in Python 3) 

All attribute references start from derived class. This includes methods, as attributes of the class object!  Proceeds up the chain of base classes 

Derived methods override (shadow) base methods Similar to virtual in C++



```python
class Derived(Base1, Base2, …, BaseN): # Multiple Inheritance
```

Order matters



#### Attribute Resolution

Attribute lookup is (almost) breadth-first, left-to-right

Class objects have a (hidden) function attribute .mro() Shows linearization of base classes







### Magic Methods

```python
x = MagicClass()
y = MagicClass()
str(x) # => x.__str__()
x == y # => x.__eq__(y)
x < y # => x.__lt__(y)
x + y # => x.__add__(y)
iter(x) # => x.__iter__()
next(x) # => x.__next__()
len(x) # => x.__len__()
el in x # => x.__contains__(el)
```

Some builtins, like print and sort, implicitly use *\__str__* and *\_lt__*







### Handling Exceptions

```python
try:
	dangerous_code()
except SomeError:
	handle_the_error()
```

Example

```
try:
 distance = int(input("How far? "))
 time = car.speed / distance
 car.drive(time)
except ValueError as e: # Bind a name to the exception instance
 print(e)
except ZeroDivisionError:
 print("Division by zero!")
except (NameError, AttributeError): # Catch multiple exceptions
 print("Bad Car")
except: # catches everything else
 print("Car unexpectedly crashed!")
```





### Raising Exceptions

```python
>>> raise NameError('Why hello there!')
Traceback (most recent call last):
	File "<stdin>", line 1, in <module>
NameError: Why hello there!
```



#### Custom Exceptions

```python
class Error(Exception):
 """Base class for errors in this module."""
class BadLoginError(Error):
 """A user attempted to login with
 an incorrect password."""
```



### Else

```python
try:
 ...
except ...:
 ...
else: # Code that executes if the try clause does not raise an exception. Avoid accidentally catching an exception raised by something other than the code being protected
 do_something()
```



Just open a file instead of checking that it exists first! Handle exceptional cases with an except clause (or two) 

Just pop an element; don't check that a list is nonempty!







### Cleanup Actions

```python
try:
	raise NotImplementedError
finally:
	print('Goodbye, world!')
# Goodbye, world!
# Traceback (most recent call last):
# File "<stdin>", line 2, in <module>
# NotImplementedError
```

Always executed before leaving the try statement. 

Unhandled exceptions (not caught, or raised in except) are re-raised after finally executes. 

Also executed "on the way out" (break, continue, return)



***with* statement**

*with* statement in Python is used in exception handling to make the code cleaner and much more readable. There is no need to call `file.close()` when using `with` statement.

```python
with open(filename) as f:
	raw = f.read()

# is (almost) equivalent to
f = open(filename)
f.__enter__()
try:
 raw = f.read()
finally:
 f.__exit__() # Closes the file
```













## Python STL

### Importing from Modules

```python
# Import a module
import math

# Import symbols from a module into the local namespace
from math import ceil, floor

# Bind a module symbols to a new local symbol
from some_module import long_symbol_name as short_name

# Any python file (including your own) can be a module
from my_script import my_function, my_variable
```





### Importing from Packages

```python
import sound.effects.echo
sound.effects.echo.echofilter(input, output)

from sound.effects import echo
echo.echofilter(input, output, delay=0.7, atten=4)

from sound.effects.echo import echofilter
echofilter(input, output, delay=0.7, atten=4)
```





We can executing modules as scripts







### *collection*

*collections.namedtuple*   create tuple subclasses with named fields

```python
Point = collections.namedtuple('Point', ['x', 'y'])

p = Point(11, 22) # positional arguments…
q = Point(x=11, y=22) # or keyword arguments (or both!)

# Fields are accessible by name! "Readability counts."
-p.x, 2 * p.y # => -11, 44

# readable __repr__ with a name=value style
print(p) # Point(x=11, y=22)

# Subscriptable, like regular tuples
p[0] * p[1] # => 242
# Unpackable, like regular tuples
x, y = p # x == 11, y == 22
```





*collections.defaultdict*   dict subclass with factory function for missing values

```python
# Have:
input_data = [('yellow', 1), ('blue', 2),
 ('yellow', 3), ('blue', 4), ('red', 1)]
 
# Want:
output = {'blue': [2, 4], 'red': [1], 'yellow': [1, 3]}

output = collections.defaultdict(lambda: list())
for k, v in input_data:
    output[k].append(v) 
```

accepts one argument - a zero-argument factory function to supply missing keys

```python
# defaultdict with default value []
collections.defaultdict(lambda: list())
# equivalent to
collections.defaultdict(list)

# defaultdict with default value 0
collections.defaultdict(lambda: 0)
# equivalent to
collections.defaultdict(int)
```





*collections.Counter*   dict subclass for counting hashable objects

```python
# Have: s = 'mississippi'
# Want: [('s', 4), ('m', 1), ('i', 4), ('p', 2)]

s = 'mississippi'
count = collections.Counter(s) 




# Tally occurrences of words in a list
colors = ['red', 'blue', 'red', 'green', 'blue']

# One approach
counter = collections.Counter()
for color in colors:
	counter[color] += 1
print(counter)
# Counter({'blue': 2, 'green': 1, 'red': 2})

# A better approach
counter = collections.Counter(colors)
print(counter)
# Counter({'blue': 2, 'green': 1, 'red': 2})




# Get most common elements!
Counter('abracadabra').most_common(3)
# => [('a', 5), ('b', 2), ('r', 2)]

# Supports basic arithmetic
Counter('which') + Counter('witch')
# => Counter({'c': 2, 'h': 3, 'i': 2, 't': 1, 'w': 2})

Counter('abracadabra') - Counter('alakazam')
# => Counter({'a': 1, 'b': 2, 'c': 1, 'd': 1, 'r': 2})
```







### Regular Expression Operations--- *re*

```python
# Search for pattern match anywhere in string; return None if not found
m = re.search(r"(\w+) (\w+)", "Isaac Newton, Physicist")
m.group(0) # "Isaac Newton" - the entire match
m.group(1) # "Isaac" - first parenthesized subgroup
m.group(2) # "Newton" - second parenthesized subgroup

# Match pattern against start of string; return None if not found
m = re.match(r"(?P<fname>\w+) (?P<lname>\w+)", "Malcolm Reynolds")
m.group('fname') # => 'Malcolm'
m.group('lname') # => 'Reynolds'


# Substitute occurrences of one pattern with another
re.sub(r'@\w+\.com', '@stanford.edu', 'sam@go.com poohbear@bears.com')

# => sam@stanford.edu poohbear@stanford.edu
pattern = re.compile(r'[a-z]+[0-9]{3}') # compile pattern for fast ops
match = re.search(pattern, '@@@abc123') # pattern is first argument
match.span() # (3, 9)
```











### itertools

```python
def view(it): print(*map(''.join, it))

view(itertools.product('ABCD', 'EFGH'))
# => AE AF AG AH BE BF BG BH CE CF CG CH DE DF DG DH

view(itertools.product('ABCD', repeat=2))
# => AA AB AC AD BA BB BC BD CA CB CC CD DA DB DC DD

view(itertools.permutations('ABCD', 2))
# => AB AC AD BA BC BD CA CB CD DA DB DC

view(itertools.combinations('ABCD', 2))
# => AB AC AD BC BD CD

view(itertools.combinations_with_replacement('ABCD', 2))
# => AA AB AC AD BB BC BD CC CD DD
```



infinite iterator

```python
# start, [step] -> start, start + step, ...
itertools.count(10) # -> 10, 11, 12, 13, 14, ...
# Cycle through elements of an iterable
itertools.cycle('ABC') # -> 'A', 'B', 'C', 'A', ...
# Repeat a single element over and over.
itertools.repeat(10) # -> 10, 10, 10, 10, ...
```









### JSON encoder and decoder

```python
squares = {1:1, 2:4, 3:9, 4:16}

# Serialize to/from string
output = json.dumps(squares) # output == "{1:1, 2:4, 3:9, 4:16}"
json.loads(output) # => {1:1, 2:4, 3:9, 4:16}

# Serialize to/from file
with open('tmp.json', 'w') as outfile:
	json.dump(squares, outfile)
with open('tmp.json', 'r') as infile:
	input = json.load(infile)
 
# All variants support useful keyword arguments
json.dumps(data, indent=4, sort_keys=True, separators=(',', ': '))
```









### random

```python
# Random float x with 0.0 <= x < 1.0
random.random() # => 0.37444887175646646

# Random float x, 1.0 <= x < 10.0
random.uniform(1, 10) # => 1.1800146073117523

# Random integer from 1 to 6 (inclusive)
random.randint(1, 6) # => 4 (https://xkcd.com/221/)

# Random integer from 0 to 9 (inclusive)
random.randrange(10) # => 7

# Random even integer from 0 to 100 (inclusive)
random.randrange(0, 101, 2) # => 26
```







### Debugging Tools

```python
code...
breakpoint()
code...
```

