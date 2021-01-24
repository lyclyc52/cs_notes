# Python MIT



### Everything is object.

**scalar object**: cannot be subdivided

int, float, bool, NoneType

**nonscalar object**: can be subdivided



use ***type()*** to show the type

To convert, e.g. *int(3.0), float(5)*

To print out, use ***print()***



**Operations on int and float**

+,-,*,/  / will always return a float

** power of 

// get the integer part of the division



**Change Binding**

can re-bind variable names using new assignment statements but previous value may still stored in memory but lost the handle for it









### Control Flow

#### Logic

```python
not, and, or
```



#### Condition Flow

```python
if <condition>:
	<expression>
    ...
elif <condition>:
    <expression>
    ...
else:
    <expression>
    ...
```



#### Repeat

*while* loop:

```python
while <condition>:
	<expression>
	...
```

*for* loop:

```python
for <variable> in range(<some_num>):
	<expression>
```

*range(start,stop,step)*   They have to be integers

Default values are *start = 0* and *step = 1* and loop stops until value is *stop - 1*



Both can end by *break*







### String

```python
x = 1
print(x)
x_str = str(x)
print("my fav num is", x, ".", "x =", x) # will add space between them
print("my fav num is " + x_str + ". " + "x = " + x_str)
```



**input**

```python
text = input("Type anything... ")
```

The program shows the things in "" and your input, which is always a string, becomes the value of text



**Built-in Func**

- *len()*  the length of the str

- []   indexing

  ```python
  s='abc'
  # s[0]=a
  # s[-1]=c
  # s[3] is error
  ```




### Function

• has a name 																																										• has parameters (0 or more) 																															               • has a docstring (optional but recommended)                                                                                                                 • has a body                                                                                                          														        • returns something

```python
def is_even( i ):
	"""								#docstring, like a multiline comment
	Input: i, a positive int
	Returns True if i is even, otherwise False
	"""
    print("inside is_even")
    return i%2 == 0
```

Default return value is None.

Function can be return or be an argument.

```python
def func_a():
	print ('inside func_a')
def func_b(y):
    print ('inside func_b')
    return y
def func_c(z):
	print ('inside func_c')
	return z()
print (func_a())
print( 5 + func_b(2))
print( func_c(func_a))
```



#### Scope

Inside a function, **can** access a variable defined outside 

Inside a function, **cannot** modify a variable defined outside -- can using global variables, but not recommended.

```python
def g(y):
    print(x)	#Doable
    print(x + 1)
x = 5
g(x)
print(x)


def h(y):
	x += 1		 #Error
x = 5
h(x)
print(x)
```





### Compound Data Type

#### Tuple

An ordered sequence   allowed mixed types   immutable

```python
te = ()
t = (2,"mit",3)
t[0] 
(2,"mit",3) + (5,6)  #can be added
t[1:2] 		#slice tuple, evaluates to ("mit",), the last comma means it is a tuple
t[1:3] 		#slice tuple, evaluates to ("mit",3)
```

To swap variable values

```python
(x, y) = (y, x)
```

Used to return more than one value from a function

```python
def quotient_and_remainder(x, y):
    q = x // y
    r = x % y
    return (q, r)
(quot, rem) = quotient_and_remainder(4,5)
```

An example:

```python
def get_data(aTuple):
    nums = ()
    words = ()
    for t in aTuple:  # Iterator
        nums = nums + (t[0],)
        if t[1] not in words:  # Check directly
        	words = words + (t[1],)
    min_n = min(nums)
    max_n = max(nums)
    unique_words = len(words)
    return (min_n, max_n, unique_words)
```







#### List

ordered sequence of information   denoted by square brackets, []     mutable

```python
L[2]+1 # Doable
```



**Some Operations on List**

add elements to end of list: *append()*  Only works for lists

```
L.append(element)
```



combine lists together: + operator

```python
L1 = [2,1,3]
L2 = [4,5,6]
L3 = L1 + L2 
```



delete element at a specific index: *del(L[index])*

remove element at end of list with: *L.pop()*

 remove a specific element: *L.remove(element)*

```python
L = [2,1,3,6,3,7,0] # do below in order
L.remove(2) # mutates L = [1,3,6,3,7,0]
L.remove(3) # mutates L = [1,6,3,7,0]
del(L[1]) # mutates L = [1,3,7,0]
L.pop() # returns 0 and mutates L = [1,3,7]
```



sort() and sorted() 

reverse()

```python
L=[9,6,0,3]
sorted(L) # returns sorted list, does not mutate L
L.sort() # mutates L=[0,3,6,9]
L.reverse() # mutates L=[9,6,3,0]
```



**Convert between lists and string**

convert string to list with: *list(s)*    returns a list with every character from s an element in L

can use *s.split()*, to split a string on a character parameter, splits on spaces if called without a parameter

use *''.join(L)* to turn a list of characters into a string, can give a character in quotes to add char between every element



**Aliases**

```python
a=['1','2']
b=a  # Changing a will always change b
```

create a new list and copy every element using

```python
a=['1','2']
b=a[:]  # Changing a will not change b
```



**Nested List**

```python
a=[1,2]
b=[3,4]
c=[a]
c.append(b) # change c[0] will change a as well
```



**Iterator**

```python
def remove_dups(L1, L2):
    for e in L1:
        if e in L2:
            L1.remove(e)
L1 = [1, 2, 3, 4]
L2 = [1, 2, 5, 6]
remove_dups(L1, L2)
print(L1)
```

The output is [2,3,4], not [3,4]

Because after *L1.remove(e)*, L1=[2,3,4] but the iterator will go to *L1[1]*, not *L1[0]*. We should avoid mutating list when using iteration.





### Dictionary

It stores pairs of values and keys

```python
my_dict = {}
grades = {'Ana':'B', 'John':'A+', 'Denise':'A', 'Katy':'A'}

grades['Sylvan'] = 'A' # add sth.
'John' in grades   # check if it is in the dictionary
del(grades['Ana'])   # delete sth.

grades.keys() # returns ['Denise','Katy','John','Ana'] in arbitrary order
grades.values() # returns ['A', 'A', 'A+', 'B'] in arbitrary order
```

The value can be anything and can be duplicates.                                  

The key need to be unique and immutable









### Testing, Debugging, Exceptions, Assertions

#### Exceptions

```python
try:
    a = int(input("Tell me one number:"))
    b = int(input("Tell me another number:"))
    print(a/b)
except:
	print("Bug in user input.")
```

exceptions raised by any statement in body of try are handled by the except statement.

can have separate except clauses to deal with a particular type of exception

```python
try:
    a = int(input("Tell me one number: "))
    b = int(input("Tell me another number: "))
    print("a/b = ", a/b)
    print("a+b = ", a+b)
except ValueError:
	print("Could not convert to a number.")
except ZeroDivisionError:
	print("Can't divide by zero")
except:
	print("Something went very wrong.")
```

**other exceptions**

*else*: executed when execution of associated try body completes with no exceptions

*finally*: always executed after try, else and except clauses, even if they raised another error or executed a break, continue or return



**raise**

It raises your own exception

*raise <exceptionName\>(\<arguments>)*

```python
raise ValueError("something is wrong")
```





#### Assertion

```python
def avg(grades):
    assert len(grades) != 0, 'no grades data'
    return sum(grades)/len(grades)
```

Function ends immediately if assertion not met









### Object Oriented Programming

```
class <name>(<class parent>):
	#define atrributes
```

Example:

```python
class Coordinate(object):
	def __init__(self, x, y): # double underscore means special method
		self.x = x			  # self is like *this
		self.y = y
    def distance(self, other):	# a method
        
        x_diff_sq = (self.x-other.x)**2
        y_diff_sq = (self.y-other.y)**2
        return (x_diff_sq + y_diff_sq)**0.5
        
c = Coordinate(3,4) 		# create an object
origin = Coordinate(0,0)
print(c.x)					# access x in c
print(origin.x)      
```

**Method**

```python
>>> c = Coordinate(3,4)
>>> print(c)
<__main__.Coordinate object at 0x7fa918510488>
```

When you call *print()*, the output is not expected.

Solution is to define a \__str__ method for a class. Then Python calls the \_\_str__ method when used with print on your class object

```python
def __str__(self):
	return "<"+str(self.x)+","+str(self.y)+">"
```

The output is 

```python
>>> c = Coordinate(3,4)
>>> print(c)
<3,4>
>>> print(type(c))
<class __main__.Coordinate>
```

**Special Operators**

```python
__add__(self, other) # self + other, return a relative object
__sub__(self, other) # self - other
__eq__(self, other)  # self == other
__lt__(self, other)  # self < other
__len__(self) 		 # len(self)
__str__(self) 		 # print self
# And others
```







### Python Class

```python
a.age
a.get_age()
#Data are "public" so they are equvilant
```

Python is not great at information hiding. Because it allows you to access data, write to data and create data attributes from outside class definition.

**default arguments** 

```python
def set_name(self, newname=""):
	self.name = newname
```





### Inheritance

```python
class Animal(object):#everythin is an object so it inherit object
    def __init__(self, age):
    	self.age = age
    	self.name = Non
    	return "animal:"+str(self.name)+":"+str(self.age)
class Person(Animal):# Cat inherit Animal
    def __init__(self, name, age):
        Animal.__init__(self, age)
        self.set_name(name)
        self.friends = []
```



**class variable**

class variables and their values are shared between all instances of a class

```python
class Rabbit(Animal):
    tag = 1		#class variable
    def __init__(self, age, parent1=None, parent2=None):
    #These are all instant variable
        Animal.__init__(self, age)
        self.parent1 = parent1
        self.parent2 = parent2
        self.rid = Rabbit.tag
        Rabbit.tag += 1
```







假如你嫌datetime这个包名称太长，想要给它取个别名，以后每次用到它的时候都用它的别名代替它，这时就需要用到import…as

```
import datetime as dt
print(dt.datetime.now())
```

