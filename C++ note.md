## Setting Out to C++ I

### The C++ Preprocessor and the iostream File 

Here’s the short version of what you need to know. If your program is to use the usual C++ input or output facilities, you provide these two lines: 

```c++
#include <iostream>
using namespace std;
```



#### Header File

![image-20200622185700874](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200622185700874.png)



#### Namespaces

If you use iostream instead of iostream.h, you should use the namespace directive to make the definitions in iostream available to your program:

Namespace support is a C++ feature designed to simplify the writing of large programs and of programs that combine pre-existing code from several vendors and to help organize programs.

the classes, functions,and variables that are a standard component of C++ compilers are now placed in a namespace called std.This takes place in the h-free header files.This means, for example, that the cout variable used for output and defined in iostream is really called std::cout and that endl is really std::endl.Thus, you can omit the using directive and, instead, code in the following style:

```c++
std::cout << "Come up and C++ me some time.";
std::cout << std::endl;
```

This using directive makes all the names in the std namespace available.





### C++ Output with cout

![image-20200622190512470](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200622190512470.png)











## Dealing with data

### The sizeof Operator and the climits Header File 

<img src="C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200622203610614.png" alt="image-20200622203610614" style="zoom:80%;" />



### Initialization

C++ has an initialization syntax that is not shared with C:

```c++
int wrens(432); // alternative C++ syntax, set wrens to 432
```

#### Initialization with C++11

```c++
int emus{7}; // set emus to 5
int rheas = {12}; // set rheas to 12

int rocs = {}; // set rocs to 0
int psychics{}; // set psychics to 0
```



### Type Conversions

#### Conversion on Initialization and Assignment

For example, suppose so_long is type long, thirty is type short,and you have the following statement in a program:

```
so_long = thirty; // assigning a short to a long
```

The program takes the value of thirty (typically a 16-bit value) and expands it to a long value (typically a 32-bit value) upon making the assignment. 

Assigning a value to a type with a greater range usually poses no problem. For example,assigning a short value to a long variable doesn’t change the value; it just gives the value a few more bytes in which to laze about.

However,assigning a large long value such as 2111222333 to a float variable results in the loss of some precision. Because float can have just six significant figures, the value can be rounded to 2.11122E9.

![image-20200622211019900](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200622211019900.png)



#### Initialization Conversions When {} Are Used (C++11)

C++11 calls an initialization that uses braces a list-initialization.That’s because this form can be used more generally to provide lists of values for more complicated data types.

```c++
const int code = 66;
int x = 66;
char c1 {31325}; // narrowing, not allowed
char c2 = {66}; // allowed because char can hold 66
char c3 {code}; // ditto
char c4 = {x}; // not allowed, x is not constant
x = 31325;
char c5 = x; // allowed by this form of initialization
```



#### Type Casts

C++ empowers you to force type conversions explicitly via the type cast mechanism.

```c++
(long) thorn // returns a type long conversion of thorn
long (thorn) // returns a type long conversion of thorn
```

The static_cast<> operator, can be used for converting values from one numeric type to another. For example, using it to convert thorn to a type long value looks like this: 

```c++
static_cast (thorn) // returns a type long conversion of thorn
```



#### auto Declarations in C++11

C++11 introduces a facility that allows the compiler to deduce a type from the type of an initialization value. For this purpose it redefines the meaning of auto,a keyword dating back to C, but one hardly ever used.

```c++
auto n = 100; // n is int
auto x = 1.5; // x is double
auto y = 1.3e12L; // y is long double
```









## Compound Types 

### Array



### String

#### Reading String Input a Line at a Time

##### Line-Oriented Input with getline()

The getline() function reads a whole line, using the newline character transmitted by the Enter key to mark the end of input.You invoke this method by using cin.getline() as a function call.

The first argument is the name of the target (that is, the array destined to hold the line of input),and the second argument is a limit on the number of characters to be read.

##### Line-Oriented Input with get()

But rather than read and discard the newline character, get() leaves that character in the input queue.

Another way to use get() is to concatenate, or join, the two class member functions,as follows: 

```c++
cin.get(name, ArSize).get(); // concatenate member functions
```

What makes this possible is that cin.get(name, ArSize) returns the cin object, which is then used as the object that invokes the get() function. This is equivlent to use two separate get() function.

Similarly, the following statement reads two consecutive input lines into the arrays name1 and name2; it’s equivalent to making two separate calls to cin.getline(): 

```c++
cin.getline(name1, ArSize).getline(name2, ArSize);
```

##### Empty Lines and Other Problems

The current practice is that after get() (but not getline()) reads an empty line, it sets something called the failbit. The implications of this act are that further input is blocked, but you can restore input with the following command: 

```c++
cin.clear(); //回复输入
```

Another potential problem is that the input string could be longer than the allocated space. If the input line is longer than the number of characters specified, both getline() and get() leave the remaining characters in the input queue. However, getline() additionally sets the failbit and turns off further input.



#### Mixing String and Numeric Input



#### Introducing the string Class 

The ISO/ANSI C++98 Standard expanded the C++ library by adding a string class. So now, instead of using a character array to hold a string, you can use a type string variable (or object, to use C++ terminology).

To use the string class,a program has to include the string header file.The string class is part of the std namespace, so you have to provide a using directive or declaration or else refer to the class as std::string.

##### Initialization

```c++
string third_date = {"The Bread Bowl"};
string fourth_date {"Hank's Fine Eats"};
```

##### Assignment, Concatenation, and Appending

```c++
char charr1[20]; // create an empty array
char charr2[20] = "jaguar"; // create an initialized array
string str1; // create an empty string object
string str2 = "panther"; // create an initialized string
charr1 = charr2; // INVALID, no array assignment
str1 = str2; // VALID, object assignment ok
```

##### More string Class Operations

For example, the C library equivalent of 

```c++
str3 = str1 + str2;
```

 is this: 

```c++
strcpy(charr3, charr1); 
strcat(charr3, charr2);
```

```c++
int len1 = str1.size(); // obtain length of str1
int len2 = strlen(charr1); // obtain length of charr1
```



##### Other Forms of String Literals

C++, recall, has the wchar_t type in addition to char.(Unicode字符类型) And C++11 adds the char16_t and char32_t types. It’s possible to create arrays of these types and string literals of these types. C++ uses the L, u,and U prefixes, respectively, for string literals of these types.

```
wchar_t title[] = L"Chief Astrogator"; // w_char string
char16_t name[] = u"Felonia Ripova"; // char_16 string
char32_t car[] = U"Humber Super Snipe"; // char_32 string
```





### Structure

```c
struct inflatable goose; // keyword struct required in C
inflatable vincent; // keyword struct not required in C++
```

 To intialize:

```c++
struct perks
{
	int key_number;
	char car[12];
} mr_glitz =
{
	7, // value for mr_glitz.key_number member
	"Packard" // value for mr_glitz.car member
};
```





### Union





### Enumerations 





### Pointers and the Free Store 

#### Pointer Danger

```c++
long * fellow; // create a pointer-to-long
*fellow = 223323; // place a value in never-never land
```

Sure, fellow is a pointer. But where does it point? The code failed to assign an address to fellow. So where is the value 223323 placed? We can’t say. Because fellow wasn’t initialized, it could have any value.Whatever that value is, the program interprets it as the address at which to store 223323. If fellow happens to have the value 1200, then the computer attempts to place the data at address 1200, even if that happens to be an address in the middle of your program code. Chances are that wherever fellow points, that is not where you want to put the number 223323.This kind of error can produce some of the most insidious and hard-to-trace bugs.

#### Pointers and Numbers

```c++
int * pt;
pt = 0xB8000000; // type mismatch
pt = (int *) 0xB8000000; // types now match
```





### Allocating Memory with new

new operator: allocate

delete: free





### Array Alternative

#### The vector Template Class

First, to use a vector object, you need to include the *vector* header file. Second, the vector identifier is part of the std namespace, so you can use a using directive,a using declaration, or std::vector.Third, templates use a different syntax to indicate the type of data stored. Fourth, the vector class uses a different syntax to indicate the number of elements.

```c++
#include <vector>
...
using namespace std;
vector<int> vi; // create a zero-size array of int
int n;
cin >> n;
vector<double> vd(n); // create an array of n doubles
```

```c++
vector<typeName> vt(n_elem);
```



#### The array Template Class (C++11)

The vector class has more capabilities than the built-in array type, but this comes at a cost of slightly less efficiency.

If all you need is a fixed-size array, it could be advantageous to use the built-in type. However, that has its own costs of lessened convenience and safety. C++11 responded to this situation by adding the array template class, which is part of the std namespace. Like the built-in type,an array object has a fixed size and uses the stack (or else static memory allocation) instead of the free store, so it shares the efficiency of built-in arrays.To this it adds convenience and additional safety.To create an array object, you need to include the array header file.

```c++
array<double, 4> a3 = {3.14, 2.72, 1.62, 1.41};
```



You can use the at() member function with objects of the vector or array type:

```c++
a2.at(1) = 2.3; // assign 2.3 to a2[1]
```

The difference between using bracket notation and the at() member function is that if you use at(),an invalid index is caught during runtime and the program, by default, aborts.





















## Loops and Relational Expression

### Building a Time-Delay Loop

The ANSI C and the C++ libraries have a function to help you do this.The function is called clock(),and it returns the system time elapsed since a program started execution.There are a couple complications, though. First, clock() doesn’t necessarily return the time in seconds. Second, the function’s return type might be long on some systems, unsigned long on others,and perhaps some other type on others.

But the ctime header file (time.h on less current implementations) provides solutions to these problems. First, it defines a symbolic constant, CLOCKS_PER_SEC, that equals the number of system time units per second. So dividing the system time by this value yields seconds. Or you can multiply seconds by CLOCKS_PER_SEC to get time in the system units. Second, ctime establishes clock_t as an alias for the clock() return type. (See the sidebar “Type Aliases,” later in this chapter.) This means you can declare a variable as type clock_t,and the compiler converts it to long or unsigned int or whatever is the proper type for your system.





### Loops and Text Input 

#### Using Unadorned cin for Input

```c++
char ch;
cin<<ch;//will ignore all white space
```



#### cin.get(char) to the Rescue

```c++
char ch;
cin.get(ch);
```

(similar to getchar() in C#)



```c++
char name[ArSize];
cout << "Enter your name:\n";
cin.get(name, ArSize).get();
```

The last line is equivalent to two consecutive function calls:

```c++
cin.get(name, ArSize);
cin.get();
```

You can do so in C++ because the language supports an OOP feature called function overloading.



When cin detects the EOF, it sets two bits (the eofbit and the failbit) to 1.You can use a member function named eof() to see whether the eofbit has been set; the call cin.eof() returns the bool value true if the EOF has been detected and false otherwise. Similarly, the fail() member function returns true if either the eofbit or the failbit has been set to 1 and false otherwise.

However, the istream class provides a function that can convert an istream object such as cin to a bool value; this conversion function is called when cin occurs in a location where a bool is expected, such as in the test condition of a while loop. Furthermore, the bool value for the conversion is true if the last attempted read was successful and false otherwise.This means you can rewrite the while test to look like this:

```
while (cin) // while input is successful
```

you can use the cout.put() function (see Chapter 3,“Dealing with Data”) to display the character: 

```c++
cout.put(ch);
```

The Standard also calls for a single prototype. However, some C++ implementations provide three prototypes: put(char), put(signed char), and put(unsigned char).





### Simple File Input/Output 



























## Functions: C++’s Programming Modules 

### Functions and array Objects

```c++
void show(std::array<double, 4> da); // da an object
void fill(std::array<double, 4> * pa); // pa a pointer to an object
```





### Pointers to Functions

```c++
process(think); // passes address of think() to process()
thought(think()); // passes return value of think() to thought()
```



#### Variations on the Theme of Function Pointers 

```c++
const double * f1(const double ar[], int n);
const double * f2(const double [], int);
const double * f3(const double *, int);

const double * (*p1)(const double *, int) = f1;
const double * (*pa[3])(const double *, int) = {f1,f2,f3};
```

Why put the [3] there?Well, pa is an array of three things,and the starting point for declaring an array of three things is this: pa[3].The rest of the declaration is about what kind of thing is to be placed in the array. Operator precedence ranks [] higher than *, so *pa[3] says pa is an array of three pointers.























## Adventures in Functions 

### C++ Inline Functions 

Inline functions are a C++ enhancement designed to speed up programs.The primary distinction between normal functions and inline functions is not in how you code them but in how the C++ compiler incorporates them into a program.





### Reference Variables 

```c++
int rats;
int & rodents = rats; // makes rodents an alias for rats
```

In this context, & is not the address operator. Instead, it serves as part of the type identifier. Just as char * in a declaration means pointer-to-char, int & means reference-toint.The reference declaration allows you to use rats and rodents interchangeably; both refer to the same value and the same memory location.



#### Return a Reference

```c++
dup = accumulate(team,five);
```

If accumulate() returned a structure instead of a reference to a structure, this could involve copying the entire structure to a temporary location and then copying that copy to dup. But with a reference return value, team is copied directly to dup,a more efficient approach.





### Function Overloading 

```c++
void staff(double & rs); // matches modifiable lvalue
voit staff(const double & rcs); // matches rvalue, const lvalue
void stove(double & r1); // matches modifiable lvalue
void stove(const double & r2); // matches const lvalue

void stove(double && r3); // matches rvalue

double x = 55.5;
const double y = 32.0;
stove(x); // calls stove(double &)
stove(y); // calls stove(const double &)
stove(x+y); // calls stove(double &&)
```





### Function Templates 

A function template is a generic function description; that is, it defines a function in terms of a generic type for which a specific type, such as int or double, can be substituted. Because templates let you program in terms of a generic type instead of a specific type, the process is sometimes termed generic programming.

EX:

```c++
template <typename AnyType>
void Swap(AnyType &a, AnyType &b)
{
	AnyType temp;
	temp = a;
	a = b;
	b = temp;
}
```

The first line specifies that you are setting up a template and that you’re naming the arbitrary type AnyType.The keywords template and typename are obligatory, except that you can use the keyword class instead of typename.

The type name (AnyType, in this example) is your choice,as long as you follow the usual C++ naming rules; many programmers use simple names such as T, which, one must admit, is simple indeed.

The template does not create any functions.Instead, it provides the compiler with directions about how to define a function. If you want a function to swap ints, then the compiler creates a function following the template pattern, substituting int for AnyType. Similarly, if you need a function to swap doubles, the compiler follows the template, substituting the double type for AnyType.



An EX:

```c++
// funtemp.cpp -- using a function template
#include <iostream>
// function template prototype
template <typename T> // or class T
void Swap(T &a, T &b);
int main()
{
    using namespace std;
    int i = 10;
    int j = 20;
    cout << "i, j = " << i << ", " << j << ".\n";
    cout << "Using compiler-generated int swapper:\n";
    Swap(i, j); // generates void Swap(int &, int &)
    cout << "Now i, j = " << i << ", " << j << ".\n";
    double x = 24.5;
    double y = 81.7;
    cout << "x, y = " << x << ", " << y << ".\n";
    cout << "Using compiler-generated double swapper:\n";
    Swap(x, y); // generates void Swap(double &, double &)
    cout << "Now x, y = " << x << ", " << y << ".\n";
    // cin.get();
    return 0;
}
// function template definition
template <typename T> // or class T, and it is necessarry
void Swap(T &a, T &b)
{
    T temp; // temp a variable of type T
    temp = a;
    a = b;
    b = temp;
}
```

The first Swap() function has two int arguments, so the compiler generates an int version of the function.That is, it replaces each use of T with int, producing a definition that looks like this:

```c++
void Swap(int &a, int &b)
{
	int temp;
	temp = a;
	a = b;
	b = temp;
}
```

You don’t see this code, but the compiler generates and then uses it in the program



#### Overloaded Templates

```c++
template <typename T> // original template
void Swap(T &a, T &b);

template <typename T> // new template
void Swap(T *a, T *b, int n);
```



#### Template Limitations

Often the code makes assumptions about what operations are possible for the type. For instance, the following statement assumes that assignment is defined,and this would not be true if type T is a built-in array type:

```c++
a = b;
```

Similarly, the following assumes > is defined, which is not true if T is an ordinary structure:

```c++
if (a > b)
```



#### Explicit Specializations

Suppose you only want to swap the salary and floor members, keeping the name members unchanged.This requires different code, but the arguments to Swap() would be the same as for the first case (references to two job structures), so you can’t use template overloading to supply the alternative code. 

However, you can supply a specialized function definition, called an explicit specialization, with the required code. If the compiler finds a specialized definition that exactly matches a function call, it uses that definition without looking for templates.

```c++
// non template function prototype
void Swap(job &, job &);
// template prototype
template <typename T>
void Swap(T &, T &);
// explicit specialization for the job type
template <> void Swap<job>(job &, job &);
```

As mentioned previously, if more than one of these prototypes is present, the compiler chooses the non template version over explicit specializations and template versions,and it chooses an explicit specialization over a version generated from a template.



Keep in mind that including a function template in your code does not in itself generate a function definition. It’s merely a plan for generating a function definition. When the compiler uses the template to generate a function definition for a particular type, the result is termed an instantiation of the template.

The template is not a function definition, but the specific instantiation using int is a function definition.This  type of instantiation is termed implicit instantiation

Now C++ allows for explicit instantiation.That means you can instruct the compiler to create a particular instantiation.

The syntax is to declare the particular variety you want, using the <> notation to indicate the type and prefixing the declaration with the keyword template: 

```c++
template void Swap(int, int); // explicit instantiation
```

A compiler that implements this feature will, upon seeing this declaration, use the
Swap() template to generate an instantiation, using the int type.That is, this declaration
means “Use the Swap() template to generate a function definition for the int type.”

```c++
//These two are equvilent
template <> void Swap<int>(int &, int &); // explicit specialization
template <> void Swap(int &, int &); // explicit specialization
```

The difference is that these last two declarations mean “Don’t use the Swap() template to generate a function definition. Instead, use a separate, specialized function definition explicitly defined for the int type.”

It is an error to try to use both an explicit instantiation and an explicit specialization for the same type(s) in the same file, or, more generally, the same translation unit.



```c++
int m = 5;
double x = 14.3;
Swap<double>(m, x); // almost works
```

This generates an explicit instantiation for type double. Unfortunately, in this case, the code won’t work because the first formal parameter, being type double &, can’t refer to the type int variable m. If it is double type, it will work because it will have a type cast.





#### Which Function Version Does the Compiler Pick?

In general, the ranking from best to worst is this:

1. Exact match, with regular functions outranking templates 

2. Conversion by promotion (for example, the automatic conversions of char and short to int and of float to double) 
3. Conversion by standard conversion (for example, converting int to char or long to double) 
4. User-defined conversions, such as those defined in class declarations



<img src="C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200629222802340.png" alt="image-20200629222802340" style="zoom:80%;" />

```c++
struct blot {int a; char b[10];};
template <class Type> void recycle (Type t); // template
template <> void recycle<blot> (blot & t); // specialization for blot
...
blot ink = {25, "spots"};
...
recycle(ink); // use specialization
```

EX:

```c++
template <class Type> void recycle (Type t); // #1
template <class Type> void recycle (Type * t); // #2

struct blot {int a; char b[10];};
blot ink = {25, "spots"};
...
recycle(&ink); // address of a structure
```

The recycle(&ink) call matches Template #1, with Type interpreted as blot *.The recycle(&ink) function call also matches Template #2, this time with Type being ink.

Of these two template functions, recycle(blot *) is considered the more specialized because it underwent fewer conversions in being generated. In Template #2, Type was already specialized as a pointer, hence it is “more specialized.”

The rules for finding the most specialized template are called the partial ordering rules for function templates.



##### Making Your Own Choices

```c++
#include <iostream>
template<class T> // or template <typename T>
T lesser(T a, T b) // #1
{
	return a < b ? a : b;
}
int lesser (int a, int b) // #2
{
	a = a < 0 ? -a : a;
	b = b < 0 ? -b : b;
	return a < b ? a : b;
}
int main()
{
	using namespace std;
	int m = 20;
	int n = -30;
	double x = 15.5;
	double y = 25.9;
	cout << lesser(m, n) << endl; // use #2
	cout << lesser(x, y) << endl; // use #1 with double
	cout << lesser<>(m, n) << endl; // use #1 with int
	cout << lesser<int>(x, y) << endl; // use #1 with int
}
```



#### Template Function Evolution

```c++
template<class T1, class T2>
void ft(T1 x, T2 y)
{
...
	?type? xpy = x + y;
...
}
```

What should the type for xpy be? We don’t know in advance how ft() might be used becaue x and y can be different types.



##### The decltype Keyword (C++11)

```c++
int x;
decltype(x) y; // make y the same type as x

decltype(x + y) xpy; // make xpy the same type as x + y
xpy = x + y;

decltype(x + y) xpy = x + y;//combine
```

EX:

```c++
template<class T1, class T2>
void ft(T1 x, T2 y)
{
	...
	decltype(x + y) xpy = x + y;
	...
}
```



Here’s a somewhat simplified version of the list.

1. If expression is an unparenthesized identifier (that is, no additional parentheses), then var is of the same type as the identifier, including qualifiers such as const

2. If expression is a function call, then var has the type of the function return type

3. If expression is an lvalue, then var is a reference to the expression type. This might seem to imply that earlier examples such as w should have been reference types, given that w is an lvalue. However, keep in mind that case was already captured in Stage 1. For this stage to apply, expression can’t be an unparenthesized identifier.

   ```c++
   double xx = 4.4;
   decltype ((xx)) r2 = xx; // r2 is double &
   decltype(xx) w = xx; // w is double
   ```

4. If none of the preceding special cases apply, var is of the same type as expression:

If you need more than one declaration, you can use typedef with decltype:

```c++
typedef decltype(x + y) xytype;
```



##### Alternative Function Syntax

```c++
//These are the same
double h(int x, float y);
auto h(int x, float y) -> double;

//combine this with template
template<class T1, class T2>
auto gt(T1 x, T2 y) -> decltype(x + y)
{
...
	return x + y;
}
```

The combination -> double is called a trailing return type. Here, auto, in another new C++11 role, is a placeholder for the type provided by the trailing return type.



























## Memory Models and Namespaces

### Separate Compilation 

#### Header File Management

You should include a header file just once in a file. That might seem to be an easy thing to remember, but it’s possible to include a header file several times without knowing you did so. To solve that:

```c++
#ifndef COORDIN_H_
#define COORDIN_H_
// place include file contents here
#endif
```

Note that this method doesn’t keep the compiler from including a file twice. Instead, it makes the compiler ignore the contents of all but the first inclusion. Most of the standard C and C++ header files use this guarding scheme. Otherwise you might get the same structure defined twice in one file, and that will produce a compile error.





### Storage Duration, Scope, and Linkage 

C++ goes a step beyond C by offering the scope-resolution operator (::).When it is prefixed to the name of a variable, this operator means to use the global version of that variable. Thus, local() displays warming as 0.8, but it displays ::warming as another value.

In a multifile program, you can define an external variable in one and only one file. All other files using that variable have to declare that variable with the extern keyword.





#### Specifiers and Qualifiers

```c++
auto (eliminated as a specifier in C++11)
register
static
extern
thread_local (added by C++11)
mutable
```

You can use no more than one of them in a single declaration, except that thread_local can be used with static or extern.

##### Cv-Qualifiers

const and volatile

##### mutable

You can use it to indicate that a particular member of a structure (or class) can be altered even if a particular structure (or class) variable is a const.

```c++
struct data
{
	char name[30];
	mutable int accesses;
...
};
const data veep = {"Claybourne Clodde", 0, ... };
strcpy(veep.name, "Joye Joux"); // not allowed
veep.accesses++; // allowed
```

The const qualifier to veep prevents a program from changing veep’s members, but the mutable specifier to the accesses member shields accesses from that restriction.

##### const

In C++ (but not C), the const modifier alters the default storage classes slightly.Whereas a global variable has external linkage by default,a const global variable has internal linkage by default. C++ treats a global const definition as if the static specifier had been used

Internal linkage also means that each file gets its own set of constants rather than sharing them. Each definition is private to the file that contains it.This is why it’s a good idea to put constant definitions in a header file.That way,as long as you include the same header file in two source code files, they receive the same set of constants.



#### Language Linking

A linker needs a different symbolic name for each distinct function. In C, this is simple to implement because there can be only one C function with a given name. So for internal purposes,a C compiler might translate a C function name such as spiff to _spiff. C approach is termed C language linkage.

In C, this is simple to implement because there can be only one C function with a given name. So for internal purposes,a C compiler might translate a C function name such as spiff to _spiff. C approach is termed C language linkage.

However, C++ can have several functions with the same C++ name that have to be translated to separate symbolic names.Thus, the C++ compiler indulges in the process of name mangling or name decoration (as discussed in Chapter 8) to generate different symbolic names for overloaded functions. For example, it could convert spiff(int) to, say, _spiff_i,and spiff(double, double) to _spiff_d_d.

```c++
extern "C" void spiff(int); // use C protocol for name look-up
extern void spoff(int); // use C++ protocol for name look-up
extern "C++" void spaff(int); // use C++ protocol for name look-up
```



#### Storage Schemes and Dynamic Allocation

lthough the storage scheme concepts don’t apply to dynamic memory, they do apply to automatic and static pointer variables used to keep track of dynamic memory. 

For example:

```c++
float * p_fees = new float [20];
```



##### Initialization with the new Operator

```c++
int *pi = new int (6); // *pi set to 6
double * pd = new double (99.99); // *pd set to 99.99

struct where {double x; double y; double z;};
where * one = new where {2.5, 5.3, 7.2}; // C++11
int * ar = new int [4] {2,4,6,7}; // C++11
```



##### When new Fails

It may be that new can’t find the requested amount of memory. 





### Namespaces 

When programming projects grow large, the potential for name conflicts increases.When you use class libraries from more than one source, you can get name conflicts.

#### Traditional C++ Namespaces

One term you need to be aware of is declarative region.A declarative region is a region in which declarations can be made. For example, you can declare a global variable outside any function.The declarative region for that variable is the file in which it is declared. 

A second term you need to be aware of is potential scope.The potential scope for a variable begins at its point of declaration and extends to the end of its declarative region. So the potential scope is more limited than the declarative region because you can’t use a variable above the point where it is first defined.



#### New Namespace Features

C++ now adds the ability to create named namespaces by defining a new kind of declarative region, one whose main purpose is to provide an area in which to declare names.

The names in one namespace don’t conflict with the same names declared in other namespaces,and there are mechanisms for letting other parts of a program use items declared in a namespace.

EX:

```c++
namespace Jack {
	double pail; // variable declaration
	void fetch(); // function prototype
	int pal; // variable declaration
	struct Well { ... }; // structure declaration
}

namespace Jill {
	double bucket(double n) { ... } // function definition
	double fetch; // variable declaration
	int pal; // variable declaration
	struct Hill { ... }; // structure declaration
}

Jack::pail = 12.34; // use a variable
Jill::Hill mole; // create a type Hill structure
Jack::fetch(); // use a function
```

Namespaces can be located at the global level or inside other namespaces, but they cannot be placed in a block.

In addition to user-defined namespaces, there is one more namespace, the global namespace.This corresponds to the file-level declarative region, so what used to be termed global variables are now described as being part of the global namespace.

The names in any one namespace don’t conflict with names in another namespace. Thus, the fetch in Jack can coexist with the fetch in Jill



#### using Declarations and using Directives

A using declaration adds a particular name to the declarative region in which it occurs.

EX:

```c++
namespace Jill {
	double bucket(double n) { ... }
	double fetch;
	struct Hill { ... };
}
char fetch;
int main()
{
	using Jill::fetch; // put fetch into local namespace
	double fetch; // Error! Already have a local fetch
	cin >> fetch; // read a value into Jill::fetch
	cin >> ::fetch; // read a value into global fetch
}
```



A using declaration, then, makes a single name available. In contrast, the using directive makes all the names available.

```c++
using namespace Jack; // make all the names in Jack available

#include <iostream> // places names in namespace std
using namespace std; // make names available globally

int main()
{
	using namespace jack; // make names available in main()
...
}
```



One thing to keep in mind about using directives and using declarations is that they increase the possibility of name conflicts.That is, if you have both namespace jack and namespace jill available,and you use the scope-resolution operator, there is no ambiguity:

```c++
jack::pal = 3;
jill::pal =10;
```



#### using Directives Versus using Declarations

However, namespace proponents hope that you will be more selective and use either the scope-resolution operator or the using declaration.That is, you shouldn’t use the following: 

```c++
using namespace std; // avoid as too indiscriminate
```

 One other point of note is that although a using directive in a function treats the namespace names as being declared outside the function, it doesn’t make those names available to other functions in the file. Hence in the preceding example, the foom() function can’t use the unqualified Hill identifier. Instead, you should use this: 

```c++
int x; 
std::cin >> x; 
std::cout << x << std::endl;
```



#### More Namespace Features

You can nest namespace declarations, like this:

```c++
namespace elements
{
	namespace fire
	{
		int flame;
		...
	}
	float water;
}
```



You can create an alias for a namespace. For example, suppose you have a namespace defined as follows:

```c++
namespace my_very_favorite_things { ... };
namespace mvft = my_very_favorite_things;
```



#### Unnamed Namespaces

```c++
namespace // unnamed namespace
{
	int ice;
	int bandycoot;
}
```

However, if a namespace has no name, you can’t explicitly use a using directive or using declaration to make the names available elsewhere. You can’t use names from an unnamed namespace in a file other than the one that contains the namespace declaration.This provides an alternative to using static variables with internal linkage.



#### Namespaces and the Future

1. Use variables in a named namespace instead of using external global variables.

2. Use variables in an unnamed namespace instead of using static global variables
3. If you develop a library of functions or classes, place them in a namespace. Indeed, C++ currently already calls for placing standard library functions in a namespace called std.This extends to functions brought in from C. For example, the math.c header file, which is C-compatible, doesn’t use namespaces, but the C++ cmath header file should place the various math library functions in the std namespace.
4. Don’t use using directives in header files; for one thing, doing so conceals which names are being made available.Also the ordering of header files may affect behavior. If you use a using directive, place it after all the preprocessor #include directives.
5. Preferentially use local scope instead of global scope for using declarations.

















## Objects and Classes 

### Procedural and Object-Oriented Programming 





### Abstraction and Classes 

- A class declaration, which describes the data component, in terms of data members, and the public interface, in terms of member functions, termed methods 
- The class method definitions, which describe how certain class member functions are implemented

An interface is a shared framework for interactions between two systems

e.g.

```c++
// stock00.h -- Stock class interface
// version 00
#ifndef STOCK00_H_
#define STOCK00_H_
#include <string>
class Stock // class declaration
{
private:
	std::string company;
	long shares;
	double share_val;
	double total_val;
	void set_tot() { total_val = shares * share_val; }
public:
	void acquire(const std::string & co, long n, double 	pr);
	void buy(long num, double price);
	void sell(long num, double price);
	void update(double price);
	void show();
}; // note semicolon at the end
#endif
```



You don’t have to use the keyword private in class declarations because that is the default access control for class objects:





### Class Constructors and Destructors 

If you create a static storage class object, its destructor is called automatically when the program terminates. 



#### C++11 List Initialization

```c++
Stock hot_tip = {"Derivatives Plus Plus", 100, 45.0};
Stock jock {"Sport Age Storage, Inc"};
Stock temp {};
```

The braced lists in the first two declarations match the following constructor: 

```c++
Stock::Stock(const std::string & co, long n = 0, double pr = 0.0);
```



#### const Member Functions

```c++
const Stock land = Stock("Kludgehorn Properties");
land.show();
```

With current C++, the compiler should object to the second line.Why? Because the code for show() fails to guarantee that it won’t modify the invoking object, which, because it is const, should not be altered.



```c++
void stock::show() const // promises not to change invoking object
```





### The *this* Pointer 





### An Array of Objects 

You can use a constructor to initialize the array elements. In that case, you have to call the constructor for each individual element.





### Class Scope 

#### Class Scope Constants

```c++
class Bakery
{
private:
const int Months = 12; // declare a constant? FAILS
double costs[Months];
...
```

But this won’t work because declaring a class describes what an object looks like but doesn’t create an object. Hence, until you create an object, there’s no place to store a value.

A couple ways to achieve essentially the same desired effect.

First, you can declare an enumeration within a class.

C++ has a second way of defining a constant within a class—using the keyword static:

```c++
class Bakery
{
private:
	static const int Months = 12;
	double costs[Months];
```





#### Scoped Enumerations (C++11)

```c++
enum egg {Small, Medium, Large, Jumbo};
enum t_shirt {Small, Medium, Large, Xlarge};
```

This won’t fly because the egg Small and the t_shirt Small would both be in the same scope,and the names conflict. C++11 provides a new form of enumeration that avoids this problem by having class scope for its enumerators.

C++11 provides a new form of enumeration that avoids this problem by having class scope for its enumerators.The declarations for this form look like this(Alternatively, you can use the keyword struct instead of class):

```c++
enum class egg {Small, Medium, Large, Jumbo};
enum class t_shirt {Small, Medium, Large, Xlarge};

egg choice = egg::Large; // the Large enumerator of the egg enum
t_shirt Floyd = t_shirt::Large; // the Large enumerator of the t_shirt enum
```

C++11 also tightens up type security for scoped enumerations. Regular enumerations get converted to integer types automatically in some situations, such as assignment to an int variable or being used in a comparison expression, but scoped enumerations have no implicit conversions to integer types.

```c++
enum egg_old {Small, Medium, Large, Jumbo}; // unscoped
enum class t_shirt {Small, Medium, Large, Xlarge}; // scoped
egg_old one = Medium; // unscoped
t_shirt rolf = t_shirt::Large; // scoped
int king = one; // implicit type conversion for unscoped
int ring = rolf; // not allowed, no implicit type conversion
if (king < Jumbo) // allowed
	std::cout << "Jumbo converted to int before 			comparison.\n";
if (king < t_shirt::Medium) // not allowed
	std::cout << "Not allowed: < not defined for scoped 	enum.\n";
	
int Frodo = int(t_shirt::Small); // do an explicit type conversion, Frodo set to 0
```







### Abstract Data Types 



























## Working with Classes 

### Operator Overloading 

C++ lets you extend operator overloading to user-defined types, permitting you, say, to use the + symbol to add two objects.

EX:

```c++
for (int i = 0; i < 20; i++)
	evening[i] = sam[i] + janet[i]; // add element by element
```

But in C++, you can define a class that represents arrays and that overloads the + operator so that you can do this:

```c++
evening = sam + janet; // add two array objects
```

if district2, sid,and sara are all objects of the Salesperson class, you can write this equation:

```c++
district2 = sid + sara;
```

To overload an operator, you use a special function form called an operator function.An operator function has the following form, where op is the symbol for the operator being overloaded:

```c++
operatorop(argument-list)
```

The compiler, recognizing the operands as belonging to the Salesperson class, replaces the operator with the corresponding operator function:

```c++
district2 = sid.operator+(sara);
```





### Time on Our Hands: Developing an Operator Overloading Example 

```c++
Time Time::Sum(const Time & t) const
{
	Time sum;
	sum.minutes = minutes + t.minutes;
	sum.hours = hours + t.hours + sum.minutes / 60;
	sum.minutes %= 60;
	return sum;
}
```

Adding an Addition Operator:

```c++
#ifndef MYTIME1_H_
#define MYTIME1_H_
class Time
{
private:
	int hours;
	int minutes;
public:
	Time();
	Time(int h, int m = 0);
	void AddMin(int m);
	void AddHr(int h);
	void Reset(int h = 0, int m = 0);
	Time operator+(const Time & t) const;
	void Show() const;
};
#endif

Time Time::operator+(const Time & t) const
{
	Time sum;
	sum.minutes = minutes + t.minutes;
	sum.hours = hours + t.hours + sum.minutes / 60;
	sum.minutes %= 60;
	return sum;
}


total = coding.operator+(fixing); // function notation
total = coding + fixing; // operator notation
```



#### Overloading Restrictions

Overloaded operators (with some exceptions) don’t necessarily have to be member functions. However,at least one of the operands has to be a user-defined type.

1. The overloaded operator must have at least one operand that is a user-defined type. Thus, you can’t redefine the minus operator (-) so that it yields the sum of two double values instead of their difference.

2. You can’t use an operator in a manner that violates the syntax rules for the original operator. For example, you can’t overload the modulus operator (%) so that it can be used with a single operand:

3. You can’t create new operator symbols.

4. You cannot overload the following operators:

![image-20200707214142688](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200707214142688.png)

5. Most of the operators in Table 11.1 can be overloaded by using either member or nonmember functions. However, you can use only member functions to overload the following operators:

![image-20200707214450875](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200707214450875.png)





### Introducing Friends 

By making a function a friend to a class, you allow the function the same access privileges that a member function of the class has.

```c++
A = B * 2.75; 
```

translates to the following member function call: 

```c++
A = B.operator*(2.75); 
```

But this does not match.

```c++
A = 2.75 * B; // cannot correspond to a member function
```



There is another possibility—using a nonmember function. (Remember, most operators can be overloaded using either member or nonmember functions.) A nonmember function is not invoked by an object; instead,any values it uses, including objects,are explicit arguments.

to the following nonmember function call: 

```c++
A = operator*(2.75, B);
```

The function would have this prototype: 

```c++
Time operator*(double m, const Time & t);
```

Using a nonmember function solves the problem of getting the operands in the desired order (first double and then Time), but it raises a new problem: Nonmember functions can’t directly access private data in a class. But there is a special category of nonmember functions, called friends, that can access private members of a class.



#### Creating Friends

```c++
friend Time operator*(double m, const Time & t); // goes in class declaration
```

Although the operator*() function is declared in the class declaration, it is not a member function. So it isn’t invoked by using the membership operator. 

Although the operator*() function is not a member function, it has the same access rights as a member function

The second step is to write the function definition. Because it is not a member function, you don’t use the Time:: qualifier.Also you don’t use the friend keyword in the definition.

```c++
Time operator*(double m, const Time & t) // friend not used in definition
{
	Time result;
	long totalminutes = t.hours * mult * 60 +t.minutes * mult;
	result.hours = totalminutes / 60;
	result.minutes = totalminutes % 60;
	return result;
}
```

And then both M*t and t\*M is OK.



Actually, you can write this particular friend function as a non-friend by altering the definition so that it switches which value comes first in the multiplication:

```c++
Time operator*(double m, const Time & t)
{
	return t * m; // use t.operator*(m)
}
```



#### A Common Kind of Friend: Overloading the << Operator

```c++
void operator<<(ostream & os, const Time & t)
{
	os << t.hours << " hours, " << t.minutes << " 		minutes";
}
```

This lets you use 

```c++
cout << trip;
```

The new Time class declaration makes the operator<<() function a friend function to the Time class. But this function, although not inimical to the ostream class, is not a friend to that class. Because operator<<() accesses private Time object members directly, it has to be a friend to the Time class. But because it does not directly access private ostream object members, the function does not have to be a friend to the ostream class. 



But the implementation doesn’t allow you to combine the redefined << operator with the ones cout normally uses: 

```c++
cout << "Trip time: " << trip << " (Tuesday)\n"; // can't do
```

You can take the same approach with the friend function.You just revise the operator<<() function so that it returns a reference to an ostream object:

```c++
ostream & operator<<(ostream & os, const Time & t)
{
	os << t.hours << " hours, " << t.minutes << " 		minutes";
	return os;
}
```

Note that the return type is ostream &. Recall that this means that the function returns a reference to an ostream object.



For example:

```c++
cout << "Trip time: " << trip << " (Tuesday)\n"; // can do
```

becomes

```c++
cout << trip << " (Tuesday)\n";
```

and then:

```c++
cout << " (Tuesday)\n";
```



You use the friend keyword only in the prototype found in the class declaration. You don’t use it in the function definition unless the definition is also the prototype.







### Overloaded Operators: Member Versus Nonmember Functions 







### More Overloading: A Vector Class 

has two demension





### Automatic Conversions and Type Casts for Classes 

```c++
int * p = (int *) 10; // ok, p and (int *) 10 both pointers
```

This sets a pointer to the address 10 by type casting 10 to type pointer-to-int (that is, type int *).Whether this assignment makes sense is another matter.



```c++
Stonewt::Stonewt(double lbs)
{
	stone = int (lbs) / Lbs_per_stn; // integer division
	pds_left = int (lbs) % Lbs_per_stn + lbs - int(lbs);
	pounds = lbs;
}

Stonewt myCat; // create a Stonewt object
myCat = 19.6; // use Stonewt(double) to convert 19.6 to Stonewt

Stonewt wolfe(285.7); // same as Stonewt wolfe = 285.7;
```

The program uses the Stonewt(double) constructor to construct a temporary Stonewt object, using 19.6 as the initialization value.Then memberwise assignment copies the contents of the temporary object into myCat.



C++ added a new keyword, explicit, to turn off the automatic aspect. That is, you can declare the constructor this way:

```c++
explicit Stonewt(double lbs); // no implicit conversions allowed

Stonewt myCat; // create a Stonewt object
myCat = 19.6; // not valid if Stonewt(double) is declared as explicit
mycat = Stonewt(19.6); // ok, an explicit conversion
mycat = (Stonewt) 19.6; // ok, old form for explicit typecast
```



#### Conversion Functions

```c++
Stonewt wolfe(285.7);
double host = wolfe;
```

You can do this—but not by using constructors. Constructors only provide for converting another type to the class type.To do the reverse, you have to use a special form of a C++ operator function called a conversion function.

To convert to type typeName, you use a conversion function in this form:

```c++
operator typeName();
```

- The conversion function must be a class method. 
- The conversion function must not specify a return type.  
- The conversion function must have no arguments.



For example:

```c++
operator double();
```

The typeName part (in this case typeName is double) tells the conversion the type to which to convert, so no return type is needed.The fact that the function is a class method means it has to be invoked by a particular class object,and that tells the function which value to convert.Thus, the function doesn’t need arguments.

```c++
#ifndef STONEWT1_H_
#define STONEWT1_H_
class Stonewt
{
private:
	enum {Lbs_per_stn = 14}; // pounds per stone
	int stone; // whole stones
	double pds_left; // fractional pounds
	double pounds; // entire weight in pounds
public:
	Stonewt(double lbs); // construct from double pounds
	Stonewt(int stn, double lbs); // construct from stone, lbs
	Stonewt(); // default constructor
	~Stonewt();
	void show_lbs() const; // show weight in pounds format
	void show_stn() const; // show weight in stone format
	// conversion functions
	operator int() const;
	operator double() const;
};
#endif

// conversion functions
Stonewt::operator int() const
{
	return int (pounds + 0.5);
}

Stonewt::operator double()const
{
	return pounds;
}
```



##### Applying Type Conversions Automatically

```c++
cout << "Poppins: " << poppins << " pounds.\n";//ambiguous
long gone = poppins; // ambiguous
```

Nothing indicates whether the conversion should be to int or to double. Facing this lack of information, the compiler would complain that you were using an ambiguous conversion.



```c++
long gone = (double) poppins; // use double conversion
long gone = int (poppins); // use int conversion
```

The first of these statements converts poppins weight to a double value,and then assignment converts the double value to type long. Similarly, the second statement converts poppins first to type int and then to long.



With C++11, you can declare a conversion operator as explicit.

```c++
class Stonewt
{
...
// conversion functions
	explicit operator int() const;
	explicit operator double() const;
};
```



#### Conversions and Friends





























## Classes and Dynamic Memory Allocation 

### Dynamic Memory and Classes 

#### Static Class Members

```c++
class StringBad
{
private:
	char * str; // pointer to string
	int len; // length of string
	static int num_strings; // number of objects
public:
	StringBad(const char * s); // constructor
	StringBad(); // default constructor
	~StringBad(); // destructor
	// friend function
	friend std::ostream & operator<<(std::ostream & os,
	const StringBad & st);
};
```

You should note two points about this declaration. First, it uses a pointer-to-char instead of a char array to represent a name.This means that the class declaration does not allocate storage space for the string itself. Instead, it uses new in the constructors to allocate space for the string.

Second, the definition declares the num_strings member as belonging to the static storage class.A static class member has a special property:A program creates only one copy of a static class variable, regardless of the number of objects created.

```c++
// initializing static class member
int StringBad::num_strings = 0;
```

Recall that the class str member is just a pointer, so the constructor has to provide the memory for holding a string





#### Special Member Functions

In particular, C++ automatically provides the following member functions:

- A default constructor if you define no constructors  

- A default destructor if you don’t define one 

- A copy constructor if you don’t define one 

- An assignment operator if you don’t define one 

- An address operator if you don’t define one

##### Copy Constructors

A copy constructor for a class normally has this prototype:

```c++
Class_name(const Class_name &);
```

usage:

```c++
StringBad ditto(motto); // calls StringBad(const StringBad &)
StringBad metoo = motto; // calls StringBad(const StringBad &)
StringBad also = StringBad(motto);
// calls StringBad(const StringBad &)
StringBad * pStringBad = new StringBad(motto);
// calls StringBad(const StringBad &)
```



```c++
StringBad sailor = sports;
//This is equal to 
StringBad sailor;
sailor.str = sports.str;
sailor.len = sports.len;
```

![image-20200709005033700](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200709005033700.png)



##### Where the Copy Constructor Goes Wrong

The copy constructor is used to initialize the formal parameter of callme2() when that function is called,and it is used to initialize the object sailor to sports.The default copy constructor doesn’t vocalize its activities, so it doesn’t announce its creations,and it doesn’t increment the num_strings counter

```
sailor.str = sport.str;
```

This does not copy the string; it copies the pointer to a string.That is,after sailor is initialized to sports, you wind up with two pointers to the same string. It is a problem when the destructor is called. Recall that the StringBad destructor frees the memory pointed to by the str pointer.

```c++
delete [] sailor.str; // delete the string that ditto.str points to
delete [] sports.str; // effect is undefined
```

Here, sports.str points to the same memory location that has already been freed by the destructor for sailor,and this results in undefined, possibly harmful, behavior. In the case of Listing 12.3, the program produces mangled strings, which is usually a sign of memory mismanagement.

##### Fixing the Problem by Defining an Explicit Copy Constructor

```c++
StringBad::StringBad(const StringBad & st)
{
	num_strings++; // handle static member update
	len = st.len; // same length
	str = new char [len + 1]; // allot space
	std::strcpy(str, st.str); // copy string to new location
	cout << num_strings << ": \"" << str
	<< "\" object created\n"; // For Your Information
}
```



#### More Stringbad Problems: Assignment Operators

```c++
Class_name & Class_name::operator=(const Class_name &);
```

If a member is itself an object of some class, the program uses the assignment operator defined for that class to do the copying for that particular member. Static data members are unaffected.





### The New, Improved String Class

#### Static Class Member Functions

First,a static member function doesn’t have to be invoked by an object; in fact, it doesn’t even get a this pointer to play with. If the static member function is declared in the public section, it can be invoked using the class name and the scope-resolution operator. For instance:

```c++
static int HowMany() { return num_strings; }
//It could be invoked like this:
int count = String::HowMany(); // invoking a static member function
```







### Things to Remember When Using new in Constructors 

#### NULL or 0 or nullptr?

Historically, the null pointer can be represented by 0 or by NULL, a symbolic constant defined as 0 in several header files. C programmers often use NULL instead of 0 as a visual reminder that the value is a pointer value, just as they use '\0' instead of 0 for the null character as a visual reminder that this value is a character. The C++ tradition, however, has favored a simple 0 instead of the equivalent NULL. And, as mentioned earlier, C++11 offers the nullptr keyword as a better alternative.



You should define a copy constructor that initializes one object to another by doing deep copying.

You should define an assignment operator that copies one object to another by doing deep copying.







### Observations About Returning Objects 

#### Returning a Reference to a const Object

There are three important points here. First, recall that returning an object invokes the copy constructor, whereas returning a reference doesn’t.

```c++
const Vector & Max(const Vector & v1, const Vector & v2)
{
	if (v1.magval() > v2.magval())
		return v1;
	else
		return v2;
}
```



#### Returning a Reference to a Non-const Object

using a reference allows the function to avoid calling the String copy constructor to create a new String object. 



#### Returning an Object

If the object being returned is local to the called function, then it should not be returned by reference because the local object has its destructor called when the function terminates.







### Using Pointers to Objects 

```c++
Class_name * pclass = new Class_name(value);
```

If an object is created by new, its destructor is called only when you explicitly use delete on the object.



```c++
char * buffer = new char[BUF]; // get a block of memory
JustTesting *pc1, *pc2;
pc1 = new (buffer) JustTesting; // place object in buffer
pc2 = new JustTesting("Heap1", 20); // place object on heap
```

The program uses new to create a memory buffer of 512 bytes.It then uses new to create two objects of type JustTesting on the heap and attempts to use placement new to create two objects of type JustTesting in the memory buffer.

Using delete with pc2 automatically invokes the destructors for the object that pc2 point to. But using delete [] with buffer does not invoke the destructors for the objects created with placement new.







































## Class Inheritance 

### Beginning with a Simple Base Class 

 TableTennisPlayer class

```c++
class TableTennisPlayer
{
private:
	string firstname;
	string lastname;
	bool hasTable;
public:
	TableTennisPlayer (const string & fn = “none",
	const string & ln = “none", bool ht = false);
	void Name() const;
	bool HasTable() const { return hasTable; };
	void ResetTable(bool v) { hasTable = v; };
};
```



#### Deriving a Class

Some members of the Webtown Social Club have played in local table tennis tournaments,and they demand a class that includes the point ratings they’ve earned through their play. Rather than start from scratch, you can derive a class from the TableTennisPlayer class.

```c++
class RatedPlayer : public TableTennisPlayer
{
private:
	unsigned int rating; // add a data member
public:
	RatedPlayer (unsigned int r = 0, const string & fn = "none",
	const string & ln = "none", bool ht = false);
	RatedPlayer(unsigned int r, const TableTennisPlayer & tp);
	unsigned int Rating() const { return rating; } // add a method
	void ResetRating (unsigned int r) {rating = r;} // add a method
};
```



The colon indicates that the RatedPlayer class is based on the TableTennisPlayer class.This particular heading indicates that TableTennisPlayer is a public base class; this is termed public derivation. With public derivation, the public members of the base class become public members of the derived class.The private portions of a base class become part of the derived class, but they can be accessed only through public and protected methods of the base class. 

- An object of the derived type has stored within it the data members of the base type. (The derived class inherits the base-class implementation.) 
- An object of the derived type can use the methods of the base type. (The derived class inherits the base-class interface.)

- A derived class needs its own constructors. 
- A derived class can add additional data members and member functions as needed.



##### Constructors: Access Considerations

A derived class does not have direct access to the private members of the base class; it has to work through the base-class methods.

When a program constructs a derived-class object, it first constructs the base-class object. Conceptually, that means the base-class object should be constructed before the program enters the body of the derived-class constructor. C++ uses the member initializer list syntax to accomplish this.

```c++
RatedPlayer::RatedPlayer(unsigned int r, const string & fn, const string & ln, bool ht) : TableTennisPlayer(fn, ln, ht)
{
	rating = r;
}
```



The base-class object must be created first, so if you omit calling a base-class constructor, the program uses the default base-class constructor



You may, if you like,also use member initializer list syntax for members of the derived class. In this case, you use the member name instead of the class name in the list.Thus, the second constructor can also be written in this manner: 

```c++
// alternative version 
RatedPlayer::RatedPlayer(unsigned int r, const TableTennisPlayer & tp) : TableTennisPlayer(tp), rating(r) 
{ 
}
```



#### Special Relationships Between Derived and Base Classes



```c++
TableTennisPlayer player("Betsy", "Bloop", true);
RatedPlayer & rr = player; // NOT ALLOWED
RatedPlayer * pr = &player; // NOT ALLOWED

RatedPlayer rplayer1(1140, "Mallory", "Duck", true);
TableTennisPlayer & rt = rplayer; //ALLOWED
TableTennisPlayer * pt = &rplayer; //ALLOWED
```

In this case, the program uses the implicit overloaded assignment operator: 

```c++
TableTennisPlayer & operator=(const TableTennisPlayer &) const;
```







### Inheritance: An Is-a Relationship 

C++ has three varieties of inheritance: public, protected,and private.







### Polymorphic Public Inheritance 

Brass and BrassPlus Classes:

BrassPlus Class has some additional items of information, but two operations need to be implemented differently

```c++
class Brass
{
private:
	std::string fullName;
	long acctNum;
	double balance;
public:
	Brass(const std::string & s = "Nullbody", long an = -1, double bal = 0.0);
	void Deposit(double amt);
	virtual void Withdraw(double amt);
	double Balance() const;
	virtual void ViewAcct() const;
	virtual ~Brass() {}
};

class BrassPlus : public Brass
{
private:
	double maxLoan;
	double rate;
	double owesBank;
public:
	BrassPlus(const std::string & s = "Nullbody", long an = -1,
	double bal = 0.0, double ml = 500, double r = 0.11125);
	BrassPlus(const Brass & ba, double ml = 500, double r = 0.11125);
	virtual void ViewAcct()const;
	virtual void Withdraw(double amt);
	void ResetMax(double m) { maxLoan = m; }
	void ResetRate(double r) { rate = r; };
	void ResetOwes() { owesBank = 0; }
};
```

- The BrassPlus class adds three new private data members and three new public member functions to the Brass class. 
-  Both the Brass class and the BrassPlus class declare the ViewAcct() and Withdraw() methods; these are the methods that will behave differently for a BrassPlus object than they do with a Brass object.
- The Brass class uses the new keyword virtual in declaring ViewAcct() and Withdraw().These methods are now termed virtual methods.
- The Brass class also declares a virtual destructor, even though the destructor does nothing.



If you don’t use the keyword virtual, the program chooses a method based on the reference type or pointer type. If you do use the keyword virtual, the program chooses a method based on the type of object the reference or pointer refers to.

In the definition, we don't need virtual key word.



```c++
void BrassPlus::ViewAcct() const
{
...
	Brass::ViewAcct(); // display base portion
	cout << "Maximum loan: $" << maxLoan << endl;
	cout << "Owed to bank: $" << owesBank << endl;
	cout << "Loan Rate: " << 100 * rate << "%\n";
...
}
```

We cawn use scope operator to choose which version to use.







### Static and Dynamic Binding 

The compiler has to generate code that allows the correct virtual method to be selected as the program runs; this is called dynamic binding



#### Pointer and Reference Type Compatibility

```c++
double x = 2.5;
int * pi = &x; // invalid assignment, mismatched pointer types
long & rl = x; // invalid assignment, mismatched reference type
```

However, a reference or a pointer to a base class can refer to a derivedclass object without using an explicit type cast.

Converting a base-class pointer or reference to a derived-class pointer or reference, is called downcasting,and it is not allowed without an explicit type cast.



#### Virtual Member Functions and Dynamic Binding

```c++
BrassPlus ophelia; // derived-class object
Brass * bp; // base-class pointer
bp = &ophelia; // Brass pointer to BrassPlus object
bp->ViewAcct(); // which version?
```

As discussed before, if ViewAcct() is not declared as virtual in the base class, bp- >ViewAcct() goes by the pointer type (Brass *) and invokes Brass::ViewAcct().The pointer type is known at compile time, so the compiler can bind ViewAcct() to Brass::ViewAcct() at compile time. In short, the compiler uses static binding for nonvirtual methods.

If ViewAcct() is declared as virtual in the base class, bp->ViewAcct() goes by the object type (BrassPlus) and invokes BrassPlus::ViewAcct(). In this example, you can see that the object type is BrassPlus, but, in general, (as in Listing 13.10) the object type might only be determined when the program is running.Therefore, the compiler generates code that binds ViewAcct() to Brass::ViewAcct() or BrassPlus::ViewAcct(), depending on the object type, while the program executes. In short, the compiler uses dynamic binding for virtual methods.

In most cases, dynamic binding is a good thing because it allows a program to choose the method designed for a particular type.



If dynamic binding allows you to redefine class methods but static binding makes a partial botch of it, why have static binding at all? There are two reasons: efficiency and a conceptual model



##### How Virtual Functions Work

The usual way compilers handle virtual functions is to add a hidden member to each object. The hidden member holds a pointer to an array of function addresses. Such an array is usually termed a virtual function table (vtbl). The vtbl holds the addresses of the virtual functions declared for objects of that class. If the derived class provides a new definition of a virtual function, the vtbl holds the address of the new function.

For example:

![image-20200712143949212](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200712143949212.png)



#### Things to Know About Virtual Methods

If a virtual method is invoked by using a reference to an object or by using a pointer to an object, the program uses the method defined for the object type rather than the method defined for the reference or pointer type.This is called dynamic, or late, binding.This behavior is important because it’s always valid for a base-class pointer or reference to refer to an object of a derived type.



```c++
Employee * pe = new Singer; // legal because Employee is base for Singer
...
delete pe; // ~Employee() or ~Singer()?
```

If the default static binding applies, the delete statement invokes the ~Employee() destructor.This frees memory pointed to by the Employee components of the Singer object but not memory pointed to by the new class members. However, if the destructors are virtual, the same code invokes the ~Singer() destructor, which frees memory pointed to by the Singer component,and then calls the ~Employee() destructor to free memory pointed to by the Employee component.

Note that this implies that even if a base class doesn’t require the services of an explicit destructor, you shouldn’t rely on the default constructor. Instead, you should provide a virtual destructor, even if it has nothing to do

Friends can’t be virtual functions because friends are not class members,and only members can be virtual functions. 

If a derived class fails to redefine a function (virtual or not), the class will use the base class version of the function. If a derived class is part of a long chain of derivations, it will use the most recently defined version of the function.



##### Redefinition Hides Methods

```c++
class Dwelling
{
public:
	virtual void showperks(int a) const;
...
};
class Hovel : public Dwelling
{
public:
	virtual void showperks() const;
...
};
```

This causes a problem. You might get a compiler warning.

Or perhaps you won’t get a warning. Either way, the code has the following implications:

```c++
Hovel trump;
trump.showperks(); // valid
trump.showperks(5); // invalid
```

Rather than resulting in two overloaded versions of the function, this redefinition hides the base class version that takes an int argument. In short, redefining inherited methods is not a variation of overloading. If you redefine a function in a derived class, it doesn’t just override the base class declaration with the same function signature.Instead, it hides all baseclass methods of the same name, regardless of the argument signatures.

This fact of life leads to a couple rules of thumb. First, if you redefine an inherited method, you need to make sure you match the original prototype exactly. One relatively new exception to this rule is that a return type that is a reference or pointer to a base class can be replaced by a reference or pointer to the derived class.This feature is termed covariance of return type because the return type is allowed to vary in parallel with the class type







### Access Control: protected 

The difference between private and protected comes into play only within classes derived from the base class.

```c++
class Brass
{
protected:
	double balance;
...
};
```

In this case, the BrassPlus class could access balance directly without using Brass methods.

Using protected data members may simplify writing the code, but it has a design defect.









### Abstract Base Classes 

C++ has a way to provide an unimplemented function by using a pure virtual function.A pure virtual function has = 0 at the end of its declaration.

e.g.

```c++
virtual double Area() const = 0; // a pure virtual function
```

When a class declaration contains a pure virtual function, you can’t create an object of that class.The idea is that classes with pure virtual functions exist solely to serve as base classes. 

In the case of the Area() method, the function has no definition, but C++ allows even a pure virtual function to have a definition.

In short, the = 0 in the prototype indicates that the class is an abstract base class and that the class doesn’t necessarily have to define the function.

Now you can derive the Ellipse class and Circle class from the BaseEllipse class, adding the members needed to complete each class.

A program using these classes would be able to create Ellipse objects and Circle objects but no BaseEllipse objects. Because Circle and Ellipse objects have the same base class,a collection of such objects can be managed with an array of BaseEllipse pointers.



#### Applying ABC

```c++
// acctabc.h -- bank account classes
#ifndef ACCTABC_H_
#define ACCTABC_H_
#include <iostream>
#include <string>
// Abstract Base Class
class AcctABC
{
private:
	std::string fullName;	
	long acctNum;
	double balance;
protected:
	struct Formatting
	{
		std::ios_base::fmtflags flag;
		std::streamsize pr;
	};
	const std::string & FullName() const {return fullName;}
	long AcctNum() const {return acctNum;}
	Formatting SetFormat() const;
	void Restore(Formatting & f) const;
public:
	AcctABC(const std::string & s = "Nullbody", long an = -1,
	double bal = 0.0);
	void Deposit(double amt) ;
	virtual void Withdraw(double amt) = 0; // pure virtual function
	double Balance() const {return balance;};
	virtual void ViewAcct() const = 0; // pure virtual function
	virtual ~AcctABC() {}
};

// Brass Account Class
class Brass :public AcctABC
{
public:
	Brass(const std::string & s = "Nullbody", long an = -1,
	double bal = 0.0) : AcctABC(s, an, bal) { }
	virtual void Withdraw(double amt);
	virtual void ViewAcct() const;
	virtual ~Brass() {}
};

//Brass Plus Account Class
class BrassPlus : public AcctABC
{
private:
	double maxLoan;
	double rate;
	double owesBank;
public:
	BrassPlus(const std::string & s = "Nullbody", long an = -1,
	double bal = 0.0, double ml = 500,
	double r = 0.10);
	BrassPlus(const Brass & ba, double ml = 500, double r = 0.1);
	virtual void ViewAcct()const;
	virtual void Withdraw(double amt);
	void ResetMax(double m) { maxLoan = m; }
	void ResetRate(double r) { rate = r; };
	void ResetOwes() { owesBank = 0; }
};
#endif
```





The constructor methods are not inherited, the destructor is not inherited, the assignment operator is not inherited, and friends are not inherited.































## Reusing Code in C++ 

### Classes with Object Members 

#### The valarray Class: A Quick Look

```c++
valarray<int> q_values; // an array of int
valarray<double> weights; // an array of double
```



```c++
double gpa[5] = {3.1, 3.5, 3.8, 2.9, 3.3};
valarray<double> v1; // an array of double, size 0
valarray<int> v2(8); // an array of 8 int elements
valarray<int> v3(10,8); // an array of 8 int elements,
						// each set to 10
valarray<double> v4(gpa, 4); // an array of 4 elements
							 // initialized to the first 4 elements of gpa
```

-  The operator[]() method provides access to individual elements. 
- The size() method returns the number of elements. 
- The sum() method returns the sum of the elements. 
- The max() method returns the largest element. n The min() method returns the smallest element



#### The Student Class Design

A student has a name,and a student has an array of quiz scores.The usual C++ technique for modeling has-a relationships is to use composition or containment—that is, to create a class composed of, or containing, members that are objects of another class.

```c++
#ifndef STUDENTC_H_
#define STUDENTC_H_
#include <iostream>
#include <string>
#include <valarray>
class Student
{
private:
    typedef std::valarray<double> ArrayDb;//To simplify
    std::string name; // contained object
    ArrayDb scores;   // contained object
    // private method for scores output

    std::ostream &arr_out(std::ostream &os) const;

public:
    Student() : name("Null Student"), scores() {}
    explicit Student(const std::string &s)
        : name(s), scores() {}
    explicit Student(int n) : name("Nully"), scores(n) {}
    Student(const std::string &s, int n)
        : name(s), scores(n) {}
    Student(const std::string &s, const ArrayDb &a)
        : name(s), scores(a) {}
    Student(const char *str, const double *pd, int n)
        : name(str), scores(pd, n) {}
    ~Student() {}
    double Average() const;
    const std::string &Name() const;
    double &operator[](int i);
    double operator[](int i) const;
    // friends
    // input
    friend std::istream &operator>>(std::istream &is,
                                    Student &stu); // 1 word
    friend std::istream &getline(std::istream &is,
                                 Student &stu); // 1 line
    // output
    friend std::ostream &operator<<(std::ostream &os,
                                    const Student &stu);
};
#endif
```



Recall that a constructor that can be called with one argument serves as an implicit conversion function from the argument type to the class type.This often is not a good idea. In the second constructor, for instance, the first argument represents the number of elements in an array rather than a value for the array, so having the constructor serve as an int-to-Student conversion function does not make sense. Using explicit turns off implicit conversions, such as = operator conversion.



##### Initializing Contained Objects

```c++
Student(const char * str, const double * pd, int n): name(str), scores(pd, n) {}
```

When you have a member initializer list that initializes more than one item, the items are initialized in the order in which they were declared, not in the order in which they appear in the initializer list. The name member would always be initialized first because it is declared first in the class definition.







### Private Inheritance 

With private inheritance, the public methods of the base class become private methods of the derived class.

EX:

```c++
class Student : private std::string, private std::valarray<double>
{
public:
...
};
```

Having more than one base class is called multiple inheritance (MI). In general, MI, particularly public MI, can lead to problems that have to be resolved with additional syntax rules.

Note that the new class doesn’t need private data.That’s because the two inherited base classes already provide all the needed data members. The containment version of this example provides two explicitly named objects as members. Private inheritance, however, provides two nameless subobjects as inherited members.This is the first of the main differences in the two approaches.



#### Initializing Base-Class Components

```c++
Student(const char * str, const double * pd, int n)
: std::string(str), ArrayDb(pd, n) {} // use class names for inheritance
```

e.g.

```c++
#ifndef STUDENTC_H_
#define STUDENTC_H_
#include <iostream>
#include <valarray>
#include <string>
class Student : private std::string, private std::valarray<double>
{
private:
    typedef std::valarray<double> ArrayDb;
    // private method for scores output
    std::ostream &arr_out(std::ostream &os) const;

public:
    Student() : std::string("Null Student"), ArrayDb() {}
    explicit Student(const std::string &s)
        : std::string(s), ArrayDb() {}
    explicit Student(int n) : std::string("Nully"), ArrayDb(n) {}
    Student(const std::string &s, int n)
        : std::string(s), ArrayDb(n) {}
    Student(const std::string &s, const ArrayDb &a)
        : std::string(s), ArrayDb(a) {}
    Student(const char *str, const double *pd, int n)
        : std::string(str), ArrayDb(pd, n) {}
    ~Student() {}
    double Average() const;
    double &operator[](int i);
    double operator[](int i) const;
    const std::string &Name() const;
    // friends
    // input
    friend std::istream &operator>>(std::istream &is,
                                    Student &stu); // 1 word
    friend std::istream &getline(std::istream &is,
                                 Student &stu); // 1 line
    // output
    friend std::ostream &operator<<(std::ostream &os,
                                    const Student &stu);
};
#endif
```



#### Accessing Base-Class Methods

using :: operator



#### Accessing Base-Class Objects

Because Student is derived from string, it’s possible to type cast a Student object to a string object; the result is the inherited string object. To avoid invoking constructors to create new objects, you use the type cast to create a reference

```c++
const string & Student::Name() const
{
	return (const string &) *this;
}
```



#### Containment or Private Inheritance?

Most C++ programmers prefer containment. First, it’s easier to follow.When you look at the class declaration, you see explicitly named objects representing the contained classes,and your code can refer to these objects by name. Using inheritance makes the relationship appear more abstract. Second, inheritance can raise problems, particularly if a class inherits from more than one base class.You may have to deal with issues such as separate base classes having methods with the same name or of separate base classes sharing a common ancestor.

However, private inheritance does offer features beyond those provided by containment. Suppose, for example, that a class has protected members, which could either be data members or member functions. Such members are available to derived classes but not to the world at large. If you include such a class in another class by using composition, the new class is part of the world at large, not a derived class. Hence it can’t access protected members.



#### Protected Inheritance

With protected inheritance, public and protected members of a base class become protected members of the derived class.As with private inheritance, the interface for the base class is available to the derived class but not to the outside world.

![image-20200714185325663](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200714185325663.png)



#### Redefining Access with using

Suppose you want to make a particular base-class method available publicly in the derived class. One option is to define a derived-class method that uses the base-class method

There is an alternative to wrapping one function call in another: use a using declaration (such as those used with namespaces) to announce that a particular base-class member can be used by the derived class, even though the derivation is private.

```c++
class Student : private std::string, private std::valarray<double>
{
...
public:
	using std::valarray<double>::min;
	using std::valarray<double>::max;
...
};
```







### Multiple Inheritance

MI describes a class that has more than one immediate base class.

MI can introduce new problems for programmers.The two chief problems are inheriting different methods with the same name from two different base classes and inheriting multiple instances of a class via two or more related immediate base classes.

 e.g.

```c++
#ifndef WORKER0_H_
#define WORKER0_H_
#include <string>
class Worker // an abstract base class
{
private:
    std::string fullname;
    long id;

public:
    Worker() : fullname("no one"), id(0L) {}
    Worker(const std::string &s, long n)
        : fullname(s), id(n) {}
    virtual ~Worker() = 0; // pure virtual destructor
    virtual void Set();
    virtual void Show() const;
};
class Waiter : public Worker
{
private:
    int panache;

public:
    Waiter() : Worker(), panache(0) {}
    Waiter(const std::string &s, long n, int p = 0)
        : Worker(s, n), panache(p) {}//use panache() to initialize panache
    Waiter(const Worker &wk, int p = 0)
        : Worker(wk), panache(p) {}
    void Set();
    void Show() const;
};
class Singer : public Worker
{
protected:
    enum
    {
        other,
        alto,
        contralto,
        soprano,
        bass,
        baritone,
        tenor
    };
    enum
    {
        Vtypes = 7
    };

private:
    static char *pv[Vtypes]; // string equivs of voice types
    int voice;

public:
    Singer() : Worker(), voice(other) {}
    Singer(const std::string &s, long n, int v = other)
        : Worker(s, n), voice(v) {}
    Singer(const Worker &wk, int v = other)
        : Worker(wk), voice(v) {}
    void Set();
    void Show() const;
};
#endif
```



Suppose you begin by publicly deriving SingingWaiter from Singer and Waiter:

```c++
class SingingWaiter: public Singer, public Waiter {...};
```

However:

```c++
SingingWaiter ed;
Worker * pw = &ed; // ambiguous
```



#### Virtual Base Classes

Virtual base classes allow an object derived from multiple bases that themselves share a common base to inherit just one object of that shared base class. You would make Worker a virtual base class to Singer and Waiter by using the keyword virtual in the class declarations (virtual and public can appear in either order):

```c++
class Singer : virtual public Worker {...};
class Waiter : public virtual Worker {...};

class SingingWaiter: public Singer, public Waiter {...};
```

Now a SingingWaiter object will contain a single copy of a Worker object. In essence, the inherited Singer and Waiter objects share a common Worker object instead of each bringing in its own copy.

C++ merely recycled the keyword virtual for the new facility—a bit of keyword overloading.



##### New Constructor Rules

```c++
SingingWaiter(const Worker & wk, int p = 0, int v = Singer::other)
: Worker(wk), Waiter(wk,p), Singer(wk,v) {}
```

Here the code explicitly invokes the Worker(const Worker &) constructor. Note that this usage is legal and often necessary for virtual base classes,and it is illegal for nonvirtual base classes.



#### Which Method?

You can use the scope-resolution operator to clarify what you mean: 

```c++
SingingWaiter newhire("Elise Hawks", 2005, 6, soprano); 
newhire.Singer::Show(); // use Singer version
```

However,a better approach is to redefine Show() for SingingWaiter and to have it specify which Show() to use.

```c++
void SingingWaiter::Show()
{
	Singer::Show();
}
```

But it ignores Waiter component. To solve it, one way is to use a modular approach instead of an incremental approach.

```c++
void Worker::Data() const
{
    cout << "Name: " << fullname << "\n";
    cout << "Employee ID: " << id << "\n";
}
void Waiter::Data() const
{
    cout << "Panache rating: " << panache << "\n";
}
void Singer::Data() const
{
    cout << "Vocal range: " << pv[voice] << "\n";
}
void SingingWaiter::Data() const
{
    Singer::Data();
    Waiter::Data();
}
void SingingWaiter::Show() const
{
    cout << "Category: singing waiter\n";
    Worker::Data();
    Data();
}
```

With this approach, objects would still use the Show() method publicly.The Data() methods, on the other hand, should be internal to the classes; they should be helper methods used to facilitate the public interface. However, making the Data() methods private would prevent, say, Waiter code from using Worker::Data(). Here is just the kind of situation for which the protected access class is useful. If the Data() methods are protected, they can by used internally by all the classes in the hierarchy while being kept hidden from the outside world.

Another approach would be to make all the data components protected instead of private, but using protected methods instead of protected data puts tighter control on the allowable access to the data.







### Class Templates 

C++’s class templates provide a better way to generate generic class declarations. Templates provide parameterized types—that is, they are capable of passing a type name as an argument to a recipe for building a class or a function.

The C++ library provides several template classes. Earlier in this chapter, you worked with the valarray template class,and Chapter 4 introduced the vector and array template classes. C++’s Standard Template Library (STL)



```c++
template <typename Type> // newer choice
```

Then replace the type of type-changable variable with Type



Similarly, you can replace the class methods of the original class with template member functions. Each function heading will be prefaced with the same template announcement:

```c++
template <class Type> // or template <typename Type>
bool Stack<Type>::push(const Type & item)
{
...
}
```

It’s important to realize that these templates are not class and member function definitions. Rather, they are instructions to the C++ compiler about how to generate class and member function definitions.

```c++
#ifndef STACKTP_H_
#define STACKTP_H_
template <class Type>
class Stack
{
private:
    enum
    {
        MAX = 10
    };               // constant specific to class
    Type items[MAX]; // holds stack items
    int top;         // index for top stack item
public:
    Stack();
    bool isempty();
    bool isfull();
    bool push(const Type &item); // add item to stack
    bool pop(Type &item);        // pop top into item
};
template <class Type>
Stack<Type>::Stack()
{
    top = 0;
}
template <class Type>
bool Stack<Type>::isempty()
{
    return top == 0;
}
template <class Type>
bool Stack<Type>::isfull()
{
    return top == MAX;
}
template <class Type>
bool Stack<Type>::push(const Type &item)
{
    if (top < MAX)
    {
        items[top++] = item;
        return true;
    }
    else
        return false;
}
template <class Type>
bool Stack<Type>::pop(Type &item)
{
    if (top > 0)
    {
        item = items[--top];
        return true;
    }
    else
        return false;
}
#endif
```



#### Using a Template Class

```
Stack<int> kernels; // create a stack of ints
Stack<string> colonels; // create a stack of string objects
```



```c++
#include <iostream>
#include <string>
#include <cctype>
#include "stacktp.h"
using std::cin;
using std::cout;
int main()
{
    Stack<std::string> st; // create an empty stack
    char ch;
    std::string po;
    cout << "Please enter A to add a purchase order,\n"
         << "P to process a PO, or Q to quit.\n";
    while (cin >> ch && std::toupper(ch) != 'Q')
    {
        while (cin.get() != '\n')
            continue;
        if (!std::isalpha(ch))
        {
            cout << '\a';
            continue;
        }
        switch (ch)
        {
        case 'A':
        case 'a':
            cout << "Enter a PO number to add: ";
            cin >> po;
            if (st.isfull())
                cout << "stack already full\n";
            else
                st.push(po);
            break;
        case 'P':
        case 'p':
            if (st.isempty())
                cout << "stack already empty\n";
            else
            {
                st.pop(po);
                cout << "PO #" << po << " popped\n";
                break;
            }
        }
        cout << "Please enter A to add a purchase order,\n"
             << "P to process a PO, or Q to quit.\n";
    }
    cout << "Bye\n";
    return 0;
}
```



##### Using a Stack of Pointers Incorrectly

```c++
Stack<char *> st;
```

1. using char * po;

The idea is to use a char pointer instead of a string object to receive the keyboard input.This approach fails immediately because merely creating a pointer doesn’t create space to hold the input strings. 

2. char po[40];

This allocates space for an input string. Furthermore, po is of type char *, so it can be placed on the stack. But an array is fundamentally at odds with the assumptions made for the pop() method.

First, the reference variable item has to refer to an lvalue of some sort, not to an array name. Second, the code assumes that you can assign to item. Even if item could refer to an array, you can’t assign to an array name.

3. char * po = new char[40];

Here, however, you come up against the most fundamental problem:There is only one po variable,and it always points to the same memory location.



##### Using a Stack of Pointers Correctly

```c++
Type * items; 
```

and then use new operator



#### An Array Template Example and Non-Type Arguments

```c++
//arraytp.h -- Array Template
#ifndef ARRAYTP_H_
#define ARRAYTP_H_
#include <iostream>
#include <cstdlib>
template <class T, int n>
class ArrayTP
{
private:
    T ar[n];

public:
    ArrayTP(){};
    explicit ArrayTP(const T &v);
    virtual T &operator[](int i);
    virtual T operator[](int i) const;
};
template <class T, int n>
ArrayTP<T, n>::ArrayTP(const T &v)
{
    for (int i = 0; i < n; i++)
        ar[i] = v;
}

template <class T, int n>
T &ArrayTP<T, n>::operator[](int i)
{
    if (i < 0 || i >= n)
    {
        std::cerr << "Error in array limits: " << i
                  << " is out of range\n";
        std::exit(EXIT_FAILURE);
    }
    return ar[i];
}
template <class T, int n>
T ArrayTP<T, n>::operator[](int i) const
{
    if (i < 0 || i >= n)
    {
        std::cerr << "Error in array limits: " << i
                  << " is out of range\n";
        std::exit(EXIT_FAILURE);
    }
    return ar[i];
}
#endif
```



The keyword class (or, equivalently in this context, typename) identifies T as a type parameter, or type argument. int identifies n as being an int type.This second kind of parameter, one that specifies a particular type instead of acting as a generic name for a type, is called a non-type, or expression, argument.

Expression arguments have some restrictions.An expression argument can be an integer type,an enumeration type,a reference, or a pointer. Also the template code can’t alter the value of the argument or take its address.Thus, in the ArrayTP template, expressions such as n++ or &n would not be allowed.



The main drawback to the expression argument approach is that each array size generates its own template.

```c++
//Two class declarations
ArrayTP<double, 12> eggweights;
ArrayTP<double, 13> donuts;
```

But the following declarations generate just one class declaration,and the size information is passed to the constructor for that class:

```c++
Stack<int> eggs(12);
Stack<int> dunkers(13);
```

Another difference is that the constructor approach is more versatile because the array size is stored as a class member rather than being hard-coded into the definition.This makes it possible, for example, to define assignment from an array of one size to an array of another size or to build a class that allows resizable arrays.



#### Template Versatility

Template classes can serve as base classes,and they can be component classes.They can themselves be type arguments to other templates.

```c++
template <typename T> // or <class T>
class Array
{
private:
    T entry;
    ...
};
template <typename Type>
class GrowArray : public Array<Type>
{
    ...
}; // inheritance
template <typename Tp>
class Stack
{
    Array<Tp> ar; // use an Array<> as a component
    ...
};

Array<Stack<int>> asi;
```



##### Using a Template Recursively

```c++
ArrayTP< ArrayTP<int,5>, 10> twodee;
```

This makes twodee an array of 10 elements, each of which is an array of five ints.The equivalent ordinary array would have this declaration:

```c++
int twodee[10][5];
```



##### Default Type Template Parameters

```c++
template <class T1, class T2 = int> class Topo {...};
```



#### Template Specializations

##### Implicit Instantiations

```c++
ArrayTP<int, 100> stuff; // implicit instantiation
```

The compiler doesn’t generate an implicit instantiation of the class until it needs an object.



##### Explicit Instantiations

The compiler generates an explicit instantiation of a class declaration when you declare a class by using the keyword template and indicating the desired type or types.The declaration should be in the same namespace as the template definition.

```c++
template class ArrayTP<string, 100>; // generate ArrayTP<string, 100> class
```



##### Explicit Specializations

An explicit specialization is a definition for a particular type or types that is to be used instead of the general template.

```c++
template <> class Classname<specialized-type-name> { ... };
```

e.g.

```c++
template <typename T>
class SortedArray
{
	...// details omitted
};

template <> class SortedArray<const char char *>
{
	...// details omitted
};
```



##### Partial Specializations

C++ allows for partial specializations, which partially restrict the generality of a template

```c++
// general template
template <class T1, class T2> class Pair {...};
// specialization with T2 set to int
template <class T1> class Pair<T1, int> {...};
// specialization with T1 and T2 set to int
template <> class Pair<int, int> {...};

Pair<double, double> p1; // use general Pair template
Pair<double, int> p2; // use Pair<T1, int> partial specialization
Pair<int, int> p3; // use Pair<int, int> explicit specialization
```



#### Member Templates

```c++
template <typename T>
class beta
{
private:
    template <typename V> // nested template class member
    class hold	//The definition of class hold can be outside the class beta
    {
    private:
        V val;

    public:
        hold(V v = 0) : val(v) {}
        void show() const { cout << val << endl; }
        V Value() const { return val; }
    };
    hold<T> q;   // template object
    hold<int> n; // template object
public:
    beta(T t, int i) : q(t), n(i) {}
    template <typename U> // template method
    U blab(U u, T t)
    {
        return (n.Value() + q.Value()) * u / t;
    }
    void Show() const
    {
        q.show();
        n.show();
    }
};
```



#### Templates As Parameters

```c++
template <template <typename T> class Thing>
class Crab{}
private:
	Thing<int> s1;
	Thing<double> s2;
public:
	Crab() {};
// assumes the thing class has push() and pop() members
	bool push(int a, double x) { return s1.push(a) && s2.push(x); }
	bool pop(int & a, double & x){ return s1.pop(a) && s2.pop(x); }
};
```

Here template class is the type,and Thing is the parameter. What does this imply? Suppose you have this declaration:

```c++
Crab<King> legs;
```

For this to be accepted, the template argument King has to be a template class whose declaration matches that of the template parameter Thing:

```c++
template <typename T>
class King {...};
```



#### Template Classes and Friends

##### Non-Template Friend Functions to Template Classes

```c++
template <class T>
class HasFriend
{
public:
	friend void counts(); // friend to all HasFriend instantiations
...
};
```



```c++
friend void report(HasFriend &); // possible?
```

This is wrong. The reason is that there is no such thing as a HasFriend object.There are only particular specializations, such as HasFriend. However, you can use this prototype:

```c++
template <class T>
class HasFriend
{
	friend void report(HasFriend<T> &); // bound template friend
...
};
```



```c++
void report(HasFriend<short> &) {...}; // explicit specialization for short
void report(HasFriend<int> &) {...}; // explicit specialization for int
```



#### Bound Template Friend Functions to Template Classes

For the first step, you declare each template function before the class definition:

```c++
template <typename T> void counts();
template <typename T> void report(T &);
```

Next, you declare the templates again as friends inside the function.These statements declare specializations based on the class template parameter type:

```c++
template <typename TT>
class HasFriendT
{
...
	friend void counts<TT>();
	friend void report<>(HasFriendT<TT> &);
};
```

The <> in the declarations identifies these as template specializations. In the case of report(), the <> can be left empty because the following template type argument can be deduced from the function argument

The third requirement the program must meet is to provide template definitions for the friends.

```c++
template <typename T>
void counts()
{
	cout << "template size: " << sizeof(HasFriendT<T>) << "; ";
	cout << "template counts(): " << HasFriendT<T>::ct << 	endl;
}
template <typename T>
void report(T & hf)
{
	cout << hf.item << endl;
}
```

Because the count() function calls have no function parameter from which the compiler can deduce the desired specialization, these calls use the count() and count() forms to indicate the specialization. For the calls to report(), however, the compiler can use the argument type to deduce the specialization.You could use the <> form to the same effect:

```c++
report<HasFriendT<int> >(hfi2); // same as report(hfi2);
```



##### Unbound Template Friend Functions to Template Classes

By declaring a template inside a class, you can create unbound friend functions for which every function specialization is a friend to every class specialization.

```c++
template <typename T>
class ManyFriend
{
...
	template <typename C, typename D> friend void show2(C &, D &);
};
```



#### Template Aliases (C++11)

It can be convenient, especially in template design, to create aliases for types.You can use typedef to create aliases for template specializations.

```c++
// define three typedef aliases
typedef std::array<double, 12> arrd;
typedef std::array<int, 12> arri;
typedef std::array<std::string, 12> arrst;
arrd gallons; // gallons is type std::array<double, 12>
arri days; // days is type std::array<int, 12>
arrst months; // months is type std::array<std::string, 12>
```

C++11 provides a feature previously missing—a way to use a template to provide a family of aliases.

```c++
template<typename T>
using arrtype = std::array<T,12>; // template to create multiple aliases
```

This makes arrtype a template alias that can be used as a type,as follows:

```c++
arrtype<double> gallons; // gallons is type std::array<double, 12>
arrtype<int> days; // days is type std::array<int, 12>
arrtype<std::string> months; // months is type std::array<std::string, 12>
```



































## Friends, Exceptions, and More

### Friends 

#### Friend Classes

Remote control can modify the state of a television,and this suggests making the Remote class a friend to the Tv class.

A friend declaration can appear in a public, private, or protected section; the location makes no difference. Because the Remote class mentions the Tv class, the compiler has to know about the Tv class before it can handle the Remote class.The simplest way to accomplish this is to define the Tv class first. Alternatively, you can use a forward declaration.

```c++
#ifndef TV_H_
#define TV_H_
class Tv
{
public:
    friend class Remote; // Remote can access Tv private parts
    enum
    {
        Off,
        On
    };
    enum
    {
        MinVal,
        MaxVal = 20
    };
    enum
    {
        Antenna,
        Cable
    };
    enum
    {
        TV,
        DVD
    };
    Tv(int s = Off, int mc = 125) : state(s), volume(5),
                                    maxchannel(mc), channel(2), mode(Cable), input(TV) {}
    void onoff() { state = (state == On) ? Off : On; }
    bool ison() const { return state == On; }
    bool volup();
    bool voldown();
    void chanup();
    void chandown();
    void set_mode() { mode = (mode == Antenna) ? Cable : Antenna; }
    void set_input() { input = (input == TV) ? DVD : TV; }
    void settings() const; // display all settings
private:
    int state;      // on or off
    int volume;     // assumed to be digitized
    int maxchannel; // maximum number of channels
    int channel;    // current channel setting
    int mode;       // broadcast or cable
    int input;      // TV or DVD
};

class Remote
{
private:
    int mode; // controls TV or DVD
public:
    Remote(int m = Tv::TV) : mode(m) {}
    bool volup(Tv &t) { return t.volup(); }
    bool voldown(Tv &t) { return t.voldown(); }
    void onoff(Tv &t) { t.onoff(); }
    void chanup(Tv &t) { t.chanup(); }
    void chandown(Tv &t) { t.chandown(); }
    void set_chan(Tv &t, int c) { t.channel = c; }
    void set_mode(Tv &t) { t.set_mode(); }
    void set_input(Tv &t) { t.set_input(); }
};
#endif
```

Note that each Remote method other than the constructor takes a reference to a Tv object as an argument.This reflects that a remote has to be aimed at a particular TV



#### Friend Member Functions

You do have the option of making just selected class members friends to another class rather than making the entire class a friend, but that’s a bit more awkward. You need to be careful about the order in which you arrange the various declarations and definitions.

```c++
class Tv
{
	friend void Remote::set_chan(Tv & t, int c);
...
};
```

TV needs to appear behind Remote.



#### Shared Friends

```c++
class Analyzer; // forward declaration
class Probe
{
	friend void sync(Analyzer & a, const Probe & p); // sync a to p
	friend void sync(Probe & p, const Analyzer & a); // sync p to a
...
};
class Analyzer
{
	friend void sync(Analyzer & a, const Probe & p); // sync a to p
	friend void sync(Probe & p, const Analyzer & a); // sync p to a
...
}
```







### Nested Classes 

```c++
class Queue
{
private:
// class scope definitions
// Node is a nested structure definition local to this class
	struct Node {Item item; struct Node * next;};
...
};
```

Because a structure is a class whose members are public by default, Node really is a nested class.

This example defines the constructor in the class declaration. Suppose you wanted to define it in a methods file, instead. In that case, the definition must reflect that the Node class is defined within the Queue class.This is accomplished by using the scope-resolution operator twice:

```c++
Queue::Node::Node(const Item & i) : item(i), next(0) { }
```



#### Nested Classes and Access

##### Scope

If a nested class is declared in a private section of a second class, it is known only to that second class. If you were to derive a class from Queue, Node would be invisible to that class, too, because a derived class can’t directly access the private parts of a base class

If the nested class is declared in a protected section of a second class, it is visible to that class but invisible to the outside world. However, in this case,a derived class would know about the nested class and could directly create objects of that type.

If a nested class is declared in a public section of a second class, it is available to the second class, to classes derived from the second class.



```c++
class Team
{
public:
	class Coach { ... };
...
};
```

Now suppose you have an unemployed coach, one who belongs to no team.To create a Coach object outside the Team class, you can use this:

```c++
Team::Coach forhire; // create a Coach object outside the Team class
```



##### Access Control

Declaring the Node class in the Queue class declaration does not grant the Queue class any special access privileges to the Node class, nor does it grant the Node class any special access privileges to the Queue class.Thus,a Queue class object can access only the public members of a Node object explicitly.







### Exceptions 

Programs sometimes encounter runtime problems that prevent them from continuing normally. For example,a program may try to open an unavailable file, or it may request more memory than is available, or it may encounter values it cannot abide. Usually, programmers try to anticipate such calamities. C++ exceptions provide a powerful and flexible tool for dealing with these situations.

```c++
2.0 × x × y / (x + y)
```

Note that if y is the negative of x, this formula results in division by zero,a rather undesirable operation. Many newer compilers handle division by zero by generating a special floating-point value that represents infinity; cout displays this value as Inf, inf, INF, or something similar. Other compilers may produce programs that crash when division by zero occurs. It is best to write code that behaves in the same controlled fashion on all systems.



#### Calling abort()

One way to handle this is to have the function call the abort() function if one argument is the negative of the other.The abort() function has its prototype in the cstdlib (or stdlib.h) header file.A typical implementation, if called, sends a message such as “abnormal program termination” to the standard error stream (the same as the one used by cerr) and terminates the program. It also returns an implementation-dependent value that indicates failure to the operating system or, if the program was initiated by another program, to the parent process.Whether abort() flushes file buffers (that is, memory areas used to store material for transfers to and from files) depends on the implementation. If you prefer, you can use exit(), which does flush file buffers, but without displaying a message.

e.g.

```c++
double hmean(double a, double b)
{
	if (a == -b)
	{
    	std::cout << "untenable arguments to hmean()\n";
		std::abort();
	}
	return 2.0 * a * b / (a + b);
}
```

Note that calling the abort() function from hmean() terminates the program directly, without returning first to main(). In general, different compilers issue different abort messages.



#### Returning an Error Code

A more flexible approach than aborting is to use a function’s return value to indicate a problem. For example, the get(void) member of the ostream class ordinarily returns the ASCII code for the next input character, but it returns the special value EOF if it encounters the end-of-file



#### The Exception Mechanism

There are three steps to use exception mechanism.

1. Throwing an exception 
2. Catching an exception with a handler 
3. Using a try block

```c++
#include <iostream>
double hmean(double a, double b);
int main()
{
    double x, y, z;
    std::cout << "Enter two numbers: ";
    while (std::cin >> x >> y)
    {
        try
        { // start of try block
            z = hmean(x, y);
        }                     // end of try block
        catch (const char *s) // start of exception handler
        {
            std::cout << s << std::endl;
            std::cout << "Enter a new pair of numbers: ";
            continue;
        } // end of handler
        std::cout << "Harmonic mean of " << x << " and " << y
                  << " is " << z << std::endl;
        std::cout << "Enter next set of numbers <q to quit>: ";
    }
    std::cout << "Bye!\n";
    return 0;
}
double hmean(double a, double b)
{
    if (a == -b)
        throw "bad hmean() arguments: a = -b not allowed";
    return 2.0 * a * b / (a + b);
}
```

If any statement in the try block leads to an exception being thrown, the catch blocks after this block will handle the exception. If the program calls hmean() somewhere else outside this (and any other) try block, it won’t have the opportunity to handle an exception

In this case, the thrown exception is the string "bad hmean() arguments: a = -b not allowed".The exception type can be a string,as in this case, or other C++ types. Executing the throw is a bit like executing a return statement in that it terminates function execution. However, instead of returning control to the calling program,a throw causes a program to back up through the sequence of current function calls until it finds the function that contains the try block.

The catch block looks a bit like a function definition, but it’s not.The keyword catch identifies this as a handler,and char * s means that this handler matches a thrown exception that is a string.This declaration of s acts much like a function argument definition in that a matching thrown exception is assigned to s.Also, if an exception does match this handler, the program executes the code within the braces.

If a program completes executing statements in a try block without any exceptions being thrown, it skips the catch block or blocks after the try block and goes to the first statement following the handlers.



#### Using Objects as Exceptions

Typically, functions that throw exceptions throw objects. One important advantage of this is that you can use different exception types to distinguish among different functions and situations that produce exceptions. Also an object can carry information with it,and you can use this information to help identify the conditions that caused the exception to be thrown.Also in principle a catch block could use that information to decide which course of action to pursue.

e.g.

```c++
#include <iostream>
#include <cmath> // or math.h, unix users may need -lm flag
#include "exc_mean.h"
// function prototypes
double hmean(double a, double b);
double gmean(double a, double b);
int main()
{
    using std::cin;
    using std::cout;
    using std::endl;
    double x, y, z;
    cout << "Enter two numbers: ";
    while (cin >> x >> y)
    {
        try
        { // start of try block
            z = hmean(x, y);
            cout << "Harmonic mean of " << x << " and " << y
                 << " is " << z << endl;
            cout << "Geometric mean of " << x << " and " << y
                 << " is " << gmean(x, y) << endl;
            cout << "Enter next set of numbers <q to quit>: ";
        }                     // end of try block
        catch (bad_hmean &bg) // start of catch block
        {
            bg.mesg();
            cout << "Try again.\n";
            continue;
        }
        catch (bad_gmean &hg)
        {
            cout << hg.mesg();
            cout << "Values used: " << hg.v1 << ", "
                 << hg.v2 << endl;
            cout << "Sorry, you don't get to play any more.\n";
            break;
        } // end of catch block
    }
    cout << "Bye!\n";
    return 0;
}
double hmean(double a, double b)
{
    if (a == -b)
        throw bad_hmean(a, b);
    return 2.0 * a * b / (a + b);
}
double gmean(double a, double b)
{
    if (a < 0 || b < 0)
        throw bad_gmean(a, b);
    return std::sqrt(a * b);
}
```



#### Exception Specifications Meet C++11

C++11 does allow for one special specification—the new keyword noexcept can be used to indicate a function that does not throw an exception:

```c++
double marm() noexcept; // marm() doesn't throw an exception
```

There is some debate about the necessity and usefulness of this specification, with some feeling it’s better to avoid using it (at least, in most cases). But others felt strongly enough about the need to introduce a new keyword.

There also is a noexcept() operator (see Appendix E) that reports on whether or not its operand could throw an exception.



#### Unwinding the Stack

Suppose a try block doesn’t contain a direct call to a function that throws an exception but that it calls a function that calls a function that throws an exception. Execution still jumps from the function in which the exception is thrown to the function that contains the try block and handlers. Doing so involves unwinding the stack.

C++ typically handles function calls by placing information on a stack. In particular,a program places the address of a calling function instruction (a return address) on the stack.When the called function completes, the program uses that address to determine where to continue with program execution.Also the function call places any function arguments on the stack, where they are treated as automatic variables. If the called function creates any new automatic variables, they, too,are added to the stack. If a called function calls another function, its information is added to the stack,and so on.When a function terminates, program execution passes to the address stored when the function was called,and the top of the stack is freed.



Suppose a function terminates via a thrown exception instead of via a return call. Again, the program frees memory from the stack. But instead of stopping at the first return address on the stack, the program continues freeing the stack until it reaches a return address that resides in a try block. Control then passes to the exception handlers at the end of the block rather than to the first statement following the function call.This process is called unwinding the stack. However,a function return just processes objects put on the stack by that function, whereas the throw statement processes objects put on the stack by the entire sequence of function calls between the try block and the throw.

![image-20200718233536004](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200718233536004.png)





#### More Exception Features

Another difference is that the compiler always creates a temporary copy when throwing an exception, even if the exception specifier and catch blocks specify a reference.

```c++
class problem
{
    ...
};
... void super() throw(problem)
{
    ... if (oh_no)
    {
        problem oops; // construct object
        throw oops;   // throw it
        ...
    }
    ...
    try
    {
        super();
    }
    catch (problem &p)
    {
        // statements
    }
}
```

Here, p would refer to a copy of oops rather than to oops.That’s a good thing because oops no longer exists after super() terminates. By the way, it is simpler to combine construction with the throw:

```c++
throw problem(); // construct and throw default problem object
```

You might wonder why the code uses a reference if the throw generates a copy.After all, the usual reason for using a reference return value is the efficiency of not having to make a copy.The answer is that references have another important property:A base-class reference can also refer to derived-class objects. Suppose you have a collection of exception types that are related by inheritance. In that case, the exception specification need only list a reference to the base type,and that would also match any derived objects thrown.



```c++
class bad_1
{
    ...
};
class bad_2 : public bad_1
{
    ...
};
class bad_3 : public bad 2
{
    ...
};
... void duper()
{
    ... if (oh_no) throw bad_1();
    if (rats)
        throw bad_2();
    if (drat)
        throw bad_3();
}
...
try
{
    duper();
}
catch (bad_3 &be)
{ 
	// statements
}
catch (bad_2 &be)
{ 
	// statements
}
catch (bad_1 &be)
{ 
	// statements
}
```

If the bad_1 & handler were first, it would catch the bad_1, bad_2,and bad_3 exceptions.With the inverse order,a bad_3 exception would be caught by the bad_3 & handler.

You can still catch the exception even if you don’t know the type.The trick to catching any exception is to use an ellipsis(省略号) for the exception type:

```c++
catch (...) { 
    // statements 
} // catches any type exception
```







#### The exception Class

The main intent for C++ exceptions is to provide language-level support for designing fault-tolerant programs.

Newer C++ compilers are incorporating exceptions into the language. For example, the exception header file (formerly exception.h or except.h) defines an exception class that C++ uses as a base class for other exception classes used to support the language.

Your code, too, can throw an exception object or use the exception class as a base class. One virtual member function is named what(),and it returns a string, the nature of which is implementation dependent.

```c++
#include <exception>
class bad_hmean : public std::exception
{
public:
    const char *what() { return "bad arguments to hmean()"; }
    ...
};
class bad_gmean : public std::exception
{
public:
    const char *what() { return "bad arguments to gmean()"; }
    ...
};
```

If you don’t want to handle these derived exceptions differently from one another, you can catch them with the same base-class handler:

```c++
try
{
    ...
}
catch (std::exception &e)
{
    cout << e.what() << endl;
    ...
}
```



##### The stdexcept Exception Classes

The stdexcept header file defines several more exception classes. First, the file defines the logic_error and runtime_error classes, both of which derive publicly from exception:

```c++
class logic_error : public exception
{
public:
    explicit logic_error(const string &what_arg);
    ...
};
class domain_error : public logic_error
{
public:
    explicit domain_error(const string &what_arg);
    ...
};
```



In principle, sound programming could avoid such errors, but in practice, such errors might show up. The name of each class indicates the sort of error it is intended to report:

domain_error 

invalid_argument 

length_error 

out_of_bounds

Each class has a constructor like that of logic_error that allows you to provide the string to be returned by the what() method.

The domain consists of the values for which the function is defined,and the range consists of the values that a function returns. For example, the domain of the sine function is from negative infinity to positive infinity because the sine is defined for all real numbers. But the range of the sine function is from -1 to +1 because those are the extreme possible values of the sine of an angle.

The invalid_argument exception alerts you that an unexpected value has been passed to a function. For example, if a function expects to receive a string for which each character is either a '0' or '1', it could throw the invalid_argument exception if some other character appeared in the string. 

The length_error exception is used to indicate that not enough space is available for the desired action. For example, the string class has an append() method that throws a length_error exception if the resulting string would be larger than the maximum possible string length. 

The out_of_bounds exception is typically used to indicate indexing errors. For example, you could define an array-like class for which operator()[] throws the out_of_bounds exception if the index used is invalid for that array



The runtime_error family describes errors that might show up during runtime but that could not easily be predicted and prevented.

range_error 

overflow_error 

underflow_error

Each class has a constructor like that of runtime_error that allows you to provide the string to be returned by the what() method.

An underflow error can occur in floating-point calculations. In general, there is a smallest nonzero magnitude that a floating-point type can represent.A calculation that would produce a smaller value would cause an underflow error.An overflow error can occur with either integer or floating-point types when the magnitude of the result of a calculation would exceed the largest representable value for that type.A computational result can lie outside the valid range of a function without being an underflow or overflow,and you can use the range_error exception for such situations.



##### The bad_alloc Exception and new

The current C++ way to handle memory allocation problems with new is to have new throw a bad_alloc exception.The new header includes a declaration for the bad_alloc class, which is publicly derived from the exception class.

```c++
// newexcp.cpp -- the bad_alloc exception
#include <iostream>
#include <new>
#include <cstdlib> // for exit(), EXIT_FAILURE
using namespace std;
struct Big
{
    double stuff[20000];
};
int main()
{
    Big *pb;
    try
    {

        cout << "Trying to get a big block of memory:\n";
        pb = new Big[10000]; // 1,600,000,000 bytes
        cout << "Got past the new request:\n";
    }
    catch (bad_alloc &ba)
    {
        cout << "Caught the exception!\n";
        cout << ba.what() << endl;
        exit(EXIT_FAILURE);
    }
    cout << "Memory successfully allocated\n";
    pb[0].stuff[0] = 4;
    cout << pb[0].stuff[0] << endl;
    delete[] pb;
    return 0;
}
```

Sample Output:

*Trying to get a big block of memory:* 

*Caught the exception!* 

*std::bad_alloc*

In this case, the what() method returns the string "std::bad_alloc".



##### The Null Pointer and new

Much code was written when new (the old new) returned a null pointer upon failure.

Currently, the standard provides for an alternative form of new that still returns a null pointer. 

```c++
int * pi = new (std::nothrow) int;
int * pa = new (std::nowthrow) int[500];
```

So the core code in last case could be changed in this way:

```c++
Big * pb;
pb = new (std::nothrow) Big[10000]; // 1,600,000,000 bytes
if (pb == 0)
{
	cout << "Could not allocate memory. Bye.\n";
	exit(EXIT_FAILURE);
}
```



#### Exceptions, Classes, and Inheritance

First, you can derive one exception class from another,as the standard C++ library does. Second, you can incorporate exceptions into classes by nesting exception class declarations inside a class definition. Third, such nested declarations can be inherited and can serve as base classes themselves.



#### When Exceptions Go Astray

 If the exception doesn’t match the specification, the unmatched exception is branded an unexpected exception,and, by default, it causes the program to abort. However, you can alter a program’s response to unexpected and uncaught exceptions. 

An uncaught exception doesn’t initiate an immediate abort. Instead, the program first calls a function called terminate(). By default, terminate() calls the abort() function. You can modify the behavior of terminate() by registering a function that terminate() should call instead of abort().To do this, you call the set_terminate() function. Both set_terminate() and terminate() are declared in the exception header fil

```c++
typedef void (*terminate_handler)();
terminate_handler set_terminate(terminate_handler f) throw(); // C++98
terminate_handler set_terminate(terminate_handler f) noexcept; // C++11
void terminate(); // C++98
void terminate() noexcept; // C++11
```

EX:

```c++
void myQuit()
{
	cout << "Terminating due to uncaught exception\n";
    exit(5);
}

set_terminate(myQuit);
```

Now, if an exception is thrown and not caught, the program calls terminate(),and terminate() calls MyQuit().



In principle, the exception specification should include exceptions thrown by functions called by the function in question. For example, if Argh() calls a Duh() function that can throw a retort object exception, then retort should appear in the Argh() exception specification as well as in the Duh() exception specification.

The behavior is much like that for uncaught exceptions. If there is an unexpected exception, the program calls the unexpected() function. This function, in turn, calls terminate(), which, by default, calls abort(). Just as there is a set_terminate() function that modifies the behavior of terminate(), there is a set_unexpected() function that modifies the behavior of unexpected().

```c++
typedef void (*unexpected_handler)();
unexpected_handler set_unexpected(unexpected_handler f) throw(); // C++98
unexpected_handler set_unexpected(unexpected_handler f) noexcept; // C++11
void unexpected(); // C++98
void unexpected() noexcept; // C+0x
```

In particular, the unexpected_handler function has the following choices:

1. It can end the program by calling terminate() (the default behavior), abort(), or exit(). 

2. It can throw an exception.



#### Exception Cautions

```c++
void test2(int n)
{
	double * ar = new double[n];

	if (oh_no)
		throw exception();

	delete [] ar;
	return;
}
```

Here there is a problem. Unwinding the stack removes the variable ar from the stack. But the premature termination of the function means that the delete [] statement at the end of the function is skipped.The pointer is gone, but the memory block it pointed to is still intact and inaccessible.

The leak can be avoided.

```c++
void test3(int n)
{
	double * ar = new double[n];
	...
	try {
	if (oh_no)
		throw exception();
	}
	catch(exception & ex)
	{
		delete [] ar;
		throw;
	}
	...
	delete [] ar;
	return;
}
```







### Runtime Type Identification(RTTI)

#### What Is RTTI For?

C++ has three components supporting RTTI:

- The dynamic_cast operator generates a pointer to a derived type from a pointer to a base type, if possible. Otherwise, the operator returns 0, the null pointer.
- The typeid operator returns a value identifying the exact type of an object.
- A type_info structure holds information about a particular type.

RTTI works only for classes that have virtual functions.



##### The dynamic_cast Operator

```c++
class Grand { // has virtual methods};
class Superb : public Grand { ... };
class Magnificent : public Superb { ... };
    
Grand * pg = new Grand;
Grand * ps = new Superb;
Grand * pm = new Magnificent;
    
Magnificent * p1 = (Magnificent *) pm; // #1
Magnificent * p2 = (Magnificent *) pg; // #2
Superb * p3 = (Magnificent *) pm; // #3
```

#1 and #3 are safe, #2 is not safe.



```c++
Superb * pm = dynamic_cast<Superb *>(pg);
```

This code asks whether the pointer pg can be type cast safely (as described previously) to the type Superb *. If it can, the operator returns the address of the object. Otherwise it returns 0, the null pointer.

In this case, only pm and ps could succeed.

dynamic_cast throws a type bad_cast exception, which is derived from the exception class and defined in the typeinfo header file.Thus, the operator can be used as follows:

```c++
#include <typeinfo> // for bad_cast
...
try {
	Superb & rs = dynamic_cast<Superb &>(rg);
	...
}
catch(bad_cast &){
	...
};
```



##### The typeid Operator and type_info Class

The typeid operator lets you determine whether two objects are the same type. Somewhat like sizeof, it accepts two kinds of arguments:

- The name of a class 
- An expression that evaluates to an object

The typeid operator returns a reference to a type_info object, where type_info is a class defined in the typeinfo header file (formerly typeinfo.h).The type_info class overloads the == and != operators so that you can use these operators to compare types.

EX:

```c++
typeid(Magnificent) == typeid(*pg)
```

If pg happens to be a null pointer, the program throws a bad_typeid exception.This exception type is derived from the exception class and is declared in the typeinfo header file.

The implementation of the type_info class varies among vendors, but it includes a name() member that returns an implementation-dependent string that is typically (but not necessarily) the name of the class.

EX:

```c++
cout << "Now processing type " << typeid(*pg).name() << ".\n";
```







### Type Cast Operators 

```c++
struct Data
{
    double data[200];
};
struct Junk
{
    int junk[100];
};
Data d = {2.5e33, 3.5e-19, 20.2e32};
char *pch = (char *)(&d); // type cast #1 – convert to string
char ch = char(&d);       // type cast #2 - convert address to a char
Junk *pj = (Junk *)(&d);  // type cast #3 - convert to Junk pointer
```

 In C,all of them are. Stroustrup’s response to this laxity was to tighten up what is allowable for a general type cast and to add four type cast operators that provide more discipline for the casting process:

- dynamic_cast 
- const_cast 
- static_cast 
- reinterpret_cast

Instead of using a general type cast, you can select an operator that is suited to a particular purpose.



Suppose High and Low are two classes, that ph is type High *,and that pl is type Low *.Then the following statement assigns a Low * pointer to pl only if Low is an accessible base class (direct or indirect) to High:

```c++
pl = dynamic_cast<Low *> ph;
```



The const_cast operator is for making a type cast with the sole purpose of changing whether a value is const or volatile. It has the same syntax as the dynamic_cast operator. The result of making such a type cast is an error if any other aspect of the type is altered.That is, type_name and expression must be of the same type, except that they can differ in the presence or absence of const or volatile.

```c++
High bar;
const High * pbar = &bar;
...
High * pb = const_cast<High *> (pbar); // valid
const Low * pl = const_cast<const Low *> (pbar); // invalid
```

The first type cast makes *pb a pointer that can be used to alter the value of the bar object; it removes the const label.



The static_cast operator has the same syntax as the other operators. It’s valid only if type_name can be converted implicitly to the same type that expression has, or vice versa. Otherwise, the type cast is an error. Suppose that High is a base class to Low and that Pond is an unrelated class.Then conversions from High to Low and Low to High are valid, but a conversion from Low to Pond is disallowed. Similarly, because an enumeration value can be converted to an integral type without a type cast,an integral type can be converted to an enumeration value with static_cast. Also you can use static_cast to convert double to int, to convert float to long,and to perform the various other numeric conversions.



The reinterpret_cast operator is for inherently risky type casts. It doesn’t let you cast away const, but it does allow other unsavory things. The reinterpret_cast operator doesn’t allow just anything, however. For example, you can cast a pointer type to an integer type that’s large enough to hold the pointer representation, but you can’t cast a pointer to a smaller integer type or to a floatingpoint type.Another restriction is that you can’t cast a function pointer to a data pointer or vice versa



The plain type cast in C++ is also restricted. Basically, it can do anything the other type casts can do, plus some combinations, such as a static_cast or reinterpret_cast followed by a const_cast, but it can’t do anything else.Thus, the following type cast is allowed in C but, typically, not in C++ because for most C++ implementations the char type is too small to hold a pointer implementation:

```c++
char ch = char (&d); // type cast #2 - convert address to a char
```



































## The string Class and the Standard Template Library 

### The string Class 

#### Constructing a String

![image-20200722183733320](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200722183733320.png)

![image-20200722183753953](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200722183753953.png)



#### The string Class Input

```c++
string stuff;
cin >> stuff; // read a word
getline(cin, stuff); // read a line, discard \n
```

The automatic sizing feature allows the string version of getline() to dispense(分配) with the numeric parameter that limits the number of input characters to be read.

Let’s examine the string input functions a bit more closely. Both,as mentioned, size the target string to fit the input.There are limits.The first limiting factor is the maximum allowable size for a string, represented by the constant string::npos.This, typically, is the maximum value of an unsigned int, so it doesn’t pose a practical limit for ordinary, interactive input. It could be a factor, however, if you attempt to read the contents of an entire file into a single string object.The second limiting factor is the amount of memory available to a program.



#### Working with Strings

You can compare strings.All six relational operators are overloaded for string objects, with one object being considered less than another if it occurs earlier in the machine collating sequence. If the machine collating sequence is the ASCII code, that implies that digits are less than uppercase characters and uppercase characters are less than lowercase characters. Each relational operator is overloaded three ways so that you can compare a string object with another string object, compare a string object with a C-style string,and compare a C-style string with a string object:

```++
string snake1("cobra");
string snake2("coral");
char snake3[20] = "anaconda";
if (snake1 < snake 2) // operator<(const string &, const string &)
...
if (snake1 == snake3) // operator==(const string &, const char *)
...
if (snake3 != snake2) // operator!=(const char *, const string &)
...
```



You can determine the size of a string. Both the size() and length() member functions return the number of characters in a string:

![image-20200722193750010](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200722193750010.png)

The string library also provides the related methods rfind(), find_first_of(), find_last_of(), find_first_not_of(), and find_last_not_of(), each with the same set of overloaded function signatures as the find() method. The rfind() method finds the last occurrence of a substring or character.The find_first_of() method finds the first occurrence in the invoking string of any of the characters in the argument.



#### What Else Does the string Class Offer?

It can’t necessarily just grow the string in place because it might run into neighboring memory that is already in use. So it may have to allocate a new block and then copy the old contents to a new location. It would be inefficient to do this a lot, so many C++ implementations allocate a block of memory larger than the actual string, giving the string room to grow.Then if the string eventually exceeds that size, the program allocates a new block twice the size to afford more room to grow without continuous resizing.

The capacity() method returns the size of the current block,and the reserve() method allows you to request a minimum size for the block.

```c++
#include <iostream>
#include <string>
int main()
{
    using namespace std;
    string empty;
    string small = "bit";
    string larger = "Elephants are a girl's best friend";
    cout << "Sizes:\n";
    cout << "\tempty: " << empty.size() << endl;
    cout << "\tsmall: " << small.size() << endl;
    cout << "\tlarger: " << larger.size() << endl;
    cout << "Capacities:\n";
    cout << "\tempty: " << empty.capacity() << endl;
    cout << "\tsmall: " << small.capacity() << endl;
    cout << "\tlarger: " << larger.capacity() << endl;
    empty.reserve(50);
    cout << "Capacity after empty.reserve(50): "
         << empty.capacity() << endl;
    return 0;
}
```

Sample output:

```
Sizes:
	empty: 0
	small: 3
	larger: 34
Capacities:
	empty: 15
	small: 15
	larger: 47
Capacity after empty.reserve(50): 63
```



#### String Varieties

This section treats the string class as if it were based on the char type. In fact,as mentioned earlier, the string library really is based on a template class:

```c++
template<class charT, class traits = char _traits<charT>,class Allocator = allocator<charT> >
basic_string {...};
```

EX:

```c++
typedef basic_string<char> string;
typedef basic_string<wchar_t> wstring;
typedef basic_string<char16_t> u16string; // C++11
typedef basic_string<char32_t> u32string ; // C++11
```







### Smart Pointer Template Classes 

#### Using Smart Pointers

These three smart pointer templates (auto_ptr, unique_ptr,and shared_ptr ) each defines a pointer-like object intended to be assigned an address obtained (directly or indirectly) by new.

When the smart pointer expires, its destructor uses delete to free the memory.Thus, if you assign an address returned by new to one of these objects, you don’t have to remember to free the memory later; it will be freed automatically when the smart pointer object expires. 

The auto_ptr template, for instance, includes the following constructor:

```c++
template<class X> class auto_ptr {
public:
	explicit auto_ptr(X* p =0) throw();
...};
```

(The throw() notation, recall, means this constructor doesn’t throw an exception. Like auto_ptr, it is deprecated.)

![image-20200722232615846](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200722232615846.png)



The other two smart pointers use the same syntax:

```c++
unique_ptr<double> pdu(new double); // pdu an unique_ptr to double
shared_ptr<string> pss(new string); // pss a shared_ptr to string
```

EX:

```c++
#include <memory>
void remodel(std::string &str)
{
    std::auto_ptr<std::string> ps(new std::string(str));
    ... if (weird_thing()) throw exception();
    str = *ps;
    // delete ps; NO LONGER NEEDED
    return;
}
```

Note that smart pointers belong to the std namespace.

```c++
#include <iostream>
#include <string>
#include <memory>
class Report
{
private:
    std::string str;

public:
    Report(const std::string s) : str(s)
    {
        std::cout << "Object created!\n";
    }
    ~Report() { std::cout << "Object deleted!\n"; }
    void comment() const { std::cout << str << "\n"; }
};
int main()
{
    {
        std::auto_ptr<Report> ps(new Report("using auto_ptr"));
        ps->comment(); // use -> to invoke a member function
    }
    {
        std::shared_ptr<Report> ps(new Report("using shared_ptr"));
        ps->comment();
    }
    {
        std::unique_ptr<Report> ps(new Report("using unique_ptr"));
        ps->comment();
    }
    return 0;
}
```

Sample output:

```
Object created!
using auto_ptr
Object deleted!
Object created!
using shared_ptr
Object deleted!
Object created!
using unique_ptr
Object deleted!
```

Each of these classes has an explicit constructor taking a pointer as an argument. Thus, there is no automatic type cast from a pointer to a smart pointer object:

```c++
shared_ptr<double> pd;
double *p_reg = new double;
pd = p_reg; // not allowed (implicit conversion)
pd = shared_ptr<double>(p_reg); // allowed (explicit conversion
shared_ptr<double> pshared = p_reg; // not allowed (implicit conversion)
shared_ptr<double> pshared(p_reg); // allowed (explicit conversion)
```



#### Smart Pointer Considerations

```c++
auto_ptr<string> ps (new string("I reigned lonely as a cloud."));
auto_ptr<string> vocation;
vocation = ps;
```

If ps and vocation were ordinary pointers, the result would be two pointers pointing to the same string object.That is not acceptable here because the program would wind up attempting to delete the same object twice—once when ps expires,and once when vocation expires.



```c++
#include <iostream>
#include <string>
#include <memory>
int main()
{
    using namespace std;
    auto_ptr<string> films[5] = {auto_ptr<string>(new string("Fowl Balls")),
                                 auto_ptr<string>(new string("Duck Walks")),
                                 auto_ptr<string>(new string("Chicken Runs")),
                                 auto_ptr<string>(new string("Turkey Errors")),
                                 auto_ptr<string>(new string("Goose Eggs"))};
    auto_ptr<string> pwin;
    pwin = films[2]; // films[2] loses ownership
    cout << "The nominees for best avian baseball film are\n";
    for (int i = 0; i < 5; i++)
        cout << *films[i] << endl;
    cout << "The winner is " << *pwin << "!\n";
    cin.get();
    return 0;
}
```

Sample output:

```c++
The nominees for best avian baseball film are
Fowl Balls
Duck Walks
Segmentation fault (core dumped)
```

The “core dumped” message should help fix in your memory that a misused auto_ptr can be a problem. (The behavior for this sort of code is undefined, so you might encounter different behavior, depending on your system.) Here the problem is that the following statement transfers ownership from films[2] to pwin:

```
pwin = films[2]; // films[2] loses ownership
```

Suppose you go back to the code but use shared_ptr instead of auto_ptr. Then the program runs fine.

```c++
shared_ptr<string> pwin;
pwin = films[2];
```

This time both pwin and films[2] point to the same object,and the reference count is upped from 1 to 2. At the end of the program, pwin, which was declared last, is the first object to have its destructor called.The destructor decreases the reference count to 1. Then the members of the array of shared_ptrs are freed.The destructor for films[2] decrements the count to 0 and frees the previously allocated space.



#### Why unique_ptr Is Better than auto_ptr

```c++
auto_ptr<string> p1(new string("auto"); //#1
auto_ptr<string> p2; //#2
p2 = p1; //#3
                    
unique_ptr<string> p3(new string("auto"); //#4
unique_ptr<string> p4; //#5
p4 = p3; //#6
```

When, in statement #3, p2 takes over ownership of the string object, p1 is stripped of ownership. However, the compiler does not allow statement #6, so we avoid the problem of p3 not pointing to valid data.



```c++
unique_ptr<string> demo(const char * s)
{
	unique_ptr<string> temp(new string(s));
	return temp;
}

unique_ptr<string> ps;
ps = demo("Uniquely special");
```

Here, demo() returns a temporary unique_ptr,and then ps takes over ownership of the object originally owned by the returned unique_ptr.Then the returned unique_ptr is destroyed.That’s okay because ps now has ownership of the string object.

In short, if a program attempts to assign one unique_ptr to another, the compiler allows it if the source object is a temporary rvalue and disallows it if the source object has some duration.

```c++
using namespace std;
unique_ptr< string> pu1(new string "Hi ho!");
unique_ptr< string> pu2;
pu2 = pu1; //#1 not allowed
unique_ptr<string> pu3;
pu3 = unique_ptr<string>(new string "Yo!"); //#2 allowed
```



You should use an auto_prt or shared_ptr object only for memory allocated by new, not for memory allocated by new []. You should not use auto_ptr, shared_ptr, or unique_ptr for memory not allocated via new or, in the case of unique_ptr, via new or new[].



#### Selecting a Smart Pointer







### The Standard Template Library 

The STL is not an example of object-oriented programming. Instead, it represents a different programming paradigm called generic programming.

#### The vector Template Class

To create a vector template object, you use the usual  notation to indicate the type to be used.Also the vector template uses dynamic memory allocation,and you can use an initialization argument to indicate how many vector elements you want:

```c++
#include vector
using namespace std;
vector<int> ratings(5); // a vector of 5 ints
int n;
cin >> n;
vector<double> scores(n); // a vector of n doubles
```

After you create a vector object, operator overloading for [] makes it possible to use the usual array notation for accessing individual elements:



Like the string class, the various STL container templates take an optional template argument that specifies what allocator object to use to manage memory. For example, the vector template begins like this:

```c++
template <class T, class Allocator = allocator<T> >
class vector {...
```

If you omit a value for this template argument, the container template uses the allocator class by default. This class uses new and delete.



##### Things to Do to Vectors

All the STL containers provide certain basic methods, including size(), which returns the number of elements in a container, swap(), which exchanges the contents of two containers, begin(), which returns an iterator that refers to the first element in a container,and end(), which returns an iterator that represents past-the-end for the container.

What’s an iterator(迭代器)? It’s a generalization of a pointer. In fact, it can be a pointer. Or it can be an object for which pointer-like operations such as dereferencing

Generalizing pointers to iterators allows the STL to provide a uniform interface for a variety of container classes, including ones for which simple pointers wouldn’t work. Each container class defines a suitable iterator.The type name for this iterator is a class scope typedef called iterator. For example, to declare an iterator for a type double specialization of vector, you would use this:

```c++
vector<double>::iterator pd; // pd an iterator

vector<double> scores;
pd = scores.begin(); // have pd point to the first element
*pd = 22.3; // dereference pd and assign value to first element
++pd; // make pd point to the next element
```

you can use this:

```
auto pd = scores.begin(); // C++11 automatic type deduction
```

If you set an iterator to the first element in a container and keep incrementing it, eventually it will reach past-the-end,and you will have traversed the entire contents of the container.Thus, if scores and pd are defined as in the preceding example, you can display the contents with this code:

```c++
for (pd = scores.begin(); pd != scores.end(); pd++)
	cout << *pd << endl;;
```



```c++
//Each loop cycle adds one more element to the scores object
vector<double> scores; // create an empty vector
double temp;
while (cin >> temp && temp >= 0)
	scores.push_back(temp);
cout << "You entered " << scores.size() << " scores.\n";
```

The erase() method removes a given range of a vector. It takes two iterator arguments that define the range to be removed.(include the first and last elements)



##### More Things to Do to Vectors

The STL takes a broader view, defining nonmember functions for these operations. Thus, instead of defining a separate find() member function for each container class, it defines a single find() nonmember function that can be used for all container classes.

On the other hand, the STL sometimes defines a member function even if it also defines a nonmember function for the same task.The reason is that for some actions, there is a class-specific algorithm that is more efficient than the more general algorithm.Therefore, the vector swap() will be more efficient than the nonmember swap().

Let’s examine three representative STL functions: for_each(), random_shuffle(),and sort().The for_each() function can be used with any container class. It takes three arguments.The first two are iterators that define a range in the container,and the last is a pointer to a function. n. (More generally, the last argument is a function object; you’ll learn about function objects shortly.) The for_each() function then applies the pointed-to function to each container element in the range.The pointed-to function must not alter the value of the container elements.You can use the for_each() function instead of a for loop. For example, you can replace the code

```c++
vector<Review>::iterator pr;
for (pr = books.begin(); pr != books.end(); pr++)
	ShowReview(*pr);
```

with the following:

```c++
for_each(books.begin(), books.end(), ShowReview);
```



The random_shuffle() function takes two iterators that specify a range and rearranges the elements in that range in random order. For example, the following statement randomly rearranges the order of all the elements in the books vector: 

```c++
random_shuffle(books.begin(), books.end());
```



The sort() function, too, requires that the container support random access. It comes in  two versions.The first version takes two iterators that define a range,and it sorts that range by using the < operator defined for the type element stored in the container. 

Because Review is a structure, its members are public,and a nonmember function like this would serve:

```c++
bool operator<(const Review & r1, const Review & r2)
{
	if (r1.title < r2.title)
		return true;
	else if (r1.title == r2.title && r1.rating < r2.rating)
		return true;
	else
		return false;
}
```

With a function like this in place, you could then sort a vector of Review objects (such as books):

```c++
vector<int> coolstuff;
...
sort(coolstuff.begin(), coolstuff.end());
```

If two objects have the same title members, they are then sorted in ratings order. But suppose you want to sort in decreasing order or in order of ratings instead of titles.

```c++
bool WorseThan(const Review & r1, const Review & r2)
{
	if (r1.rating < r2.rating)
		return true;
	else
		return false;
}
```

With this function in place, you can use the following statement to sort the books vector of Review objects in order of increasing rating values:

```c++
sort(books.begin(), books.end(), WorseThan);
```



#### The Range-Based for Loop (C++11)

The contents of the parentheses for the for loop declare a variable of the type stored in a container and then the name of the container. Next, the body of the loop uses the named variable to access each container element in turn. 

```c++
for_each(books.begin(), books.end(), ShowReview);
```

It can be replaced with the following range-based for loop:

```c++
for (auto x : books) ShowReview(x);
```

The compiler will use the type of books, which is vector, to deduce that x is type Review,and the loop will pass each Review object in books to ShowReview() in turn.

Unlike for_each(), the range-based for can alter the contents of a container.



### Generic Programming 

The main things the two approaches have in common are abstraction and the creation of reusable code, but the philosophies are quite different.

#### Why Iterators?

The goal of generic programming in this case would be to have a single find function that would work with arrays or linked lists or any other container type.That is, not only should the function be independent of the data type stored in the container, it should be independent of the data structure of the container itself.Templates provide a generic representation for the data type stored in a container.



What properties should an iterator have in order to implement a find function? 

- You should be able to dereference an iterator in order to access the value to which it refers.That is, if p is an iterator, *p should be defined.
- You should be able to assign one iterator to another.That is, if p and q are iterators, the expression p = q should be defined.
- You should be able to compare one iterator to another for equality.That is, if p and q are iterators, the expressions p == q and p != q should be defined.
- You should be able to move an iterator through all the elements of a container.This can be satisfied by defining ++p and p++ for an iterator p.





An example:

```c++
struct Node
{
    double item;
    Node *p_next;
};

class iterator
{
    Node *pt;

public:
    iterator() : pt(0) {}
    iterator(Node *pn) : pt(pn) {}
    double operator*() { return pt->item; }
    iterator &operator++() // for ++it
    {
        pt = pt->p_next;
        return *this;
    }
    iterator operator++(int) // for it++
    {
        iterator tmp = *this;
        pt = pt->p_next;
        return tmp;
    }
    // ... operator==(), operator!=(), etc.
};

iterator find_ll(iterator head, const double & val)
{
	iterator start;
	for (start = head; start!= 0; ++start)
	if (*start == val)
		return start;
	return 0;
}
```

(To distinguish between the prefix and postfix versions of the ++ operator, C++ adopted the convention of letting operator++() be the prefix version and operator++(int) be the suffix version; the argument is never used and hence needn’t be given a name.)



To use a container class, you don’t need to know how its iterators are implemented nor how past-the-end is implemented. It’s enough to know that it does have iterators, that begin() returns an iterator to the first element,and that end() returns an iterator to pastthe-end. For example, suppose you want to print the values in a vector object. In that case, you can use this:

```c++
vector<double>::iterator pr;
for (pr = scores.begin(); pr != scores.end(); pr++)
	cout << *pr << endl;
```

If you used the list class template instead to store scores, you could use this code:

```c++
list<double>::iterator pr;
for (pr = scores.begin(); pr != scores.end(); pr++)
	cout << *pr << endl;
```



The STL follows the approach just outlined. First, each container class (vector, list, deque,and so on) defines an iterator type appropriate to the class. For one class, the iterator might be a pointer; for another, it might be an object.Whatever the implementation, the iterator will provide the needed operations, such as * and ++.



#### Kinds of Iterators

Different algorithms have different requirements for iterators.

The STL defines five kinds of iterators and describes its algorithms in terms of which kinds of iterators it needs.The five kinds are the input iterator, output iterator, forward iterator, bidirectional iterator,and random access iterator. 

For example, the find() prototype looks like this:

```c++
template<class InputIterator, class T>
InputIterator find(InputIterator first, InputIterator last, const T& value);
```



All five kinds of iterators can be dereferenced (that is, the * operator is defined for them) and can be compared for equality (using the == operator, possibly overloaded) and inequality (using the != operator, possibly overloaded). If two iterators test as equal, then dereferencing one should produce the same value as dereferencing the second.That is, if

```c++
iter1 == iter2 
```

is true, then the following is also true: 

```c++
*iter1 == *iter2
```



##### Input Iterators

An input iterator is one that a program can use to read values from a container. In particular, dereferencing an input iterator must allow a program to read a value from a container, but it needn’t allow a program to alter that value. So algorithms that require an input iterator are algorithms that don’t change values held in a container.



##### Output Iterators

In STL usage, the term output indicates that the iterator is used for transferring information from a program to a container. An output iterator is similar to an input iterator, except that dereferencing is guaranteed to allow a program to alter a container value but not to read it.



##### Forward Iterators

Like input and output iterators, forward iterators use only the ++ operators for navigating through a container. So a forward iterator can only go forward through a container one element at a time. However, unlike input and output iterators, it necessarily goes through a sequence of values in the same order each time you use it.

A forward iterator can allow you to both read and modify data.



##### Bidirectional Iterators

Suppose you have an algorithm that needs to be able to traverse a container in both directions. A bidirectional iterator has all the features of a forward iterator and adds support for the two decrement operators (prefix and postfix).



##### Random Access Iterators

Some algorithms, such as standard sort and binary search, require the ability to jump directly to an arbitrary element of a container. This type of iterator has all the features of a bidirectional iterator, plus it adds operations (such as pointer addition) that support random access and relational operators for ordering the elements.

![image-20200725003023484](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200725003023484.png)



#### Iterator Hierarchy

![image-20200725003237854](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200725003237854.png)

![image-20200725003327020](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200725003327020.png)



#### Concepts, Refinements, and Models

The STL has several features, such as kinds of iterators, that aren’t expressible in the C++ language.That is,although you can design, say,a class that has the properties of a forward iterator, you can’t have the compiler restrict an algorithm to using only that class.

An STL algorithm works with any iterator implementation that meets its requirements. STL literature uses the word concept to describe a set of requirements.Thus, there is an input iterator concept,a forward iterator concept,and so on. By the way, if you do need iterators for, say,a container class you’re designing, you can look to the STL, which include iterator templates for the standard varieties.



##### The Pointer As Iterator

Iterators are generalizations of pointers,and a pointer satisfies all the iterator requirements.



##### copy(), ostream_iterator, and istream_iterator

```c++
int casts[10] = {6, 7, 2, 9 ,4 , 11, 8, 7, 10, 5};
vector<int> dice[10];
copy(casts, casts + 10, dice.begin()); // copy array to vector
```

The first two iterator arguments to copy() represent a range to be copied,and the final iterator argument represents the location to which the first item is copied.



You can create an iterator of this kind by including the iterator (formerly iterator.h) header file and making a declaration:

```c++
#include <iterator>
...
ostream_iterator<int, char> out_iter(cout, " ");
```

The out_iter iterator now becomes an interface that allows you to use cout to display information.The first template argument (int, in this case) indicates the data type being sent to the output stream.The second template argument (char, in this case) indicates the character type used by the output stream. The first constructor argument (cout, in this case) identifies the output stream being used. It could also be a stream used for file output.The final character string argument is a separator to be displayed after each item sent to the output stream.

```c++
*out_iter++ = 15; // works like cout << 15 << " ";
```

For a regular pointer, this would mean assigning the value 15 to the pointed-to location and then incrementing the pointer. For this ostream_iterator, however, the statement means send 15 and then a string consisting of a space to the output stream managed by cout.Then it should get ready for the next output operation.You could use the iterator with copy() as follows:

```c++
copy(dice.begin(), dice.end(), out_iter); // copy vector to output stream
```



Similarly, the iterator header file defines an istream_iterator template for adapting istream input to the iterator interface. It is a model of the input iterator concept.You could use two istream_iterator objects to define an input range for copy():

```c++
copy(istream_iterator<int, char>(cin),
istream_iterator<int, char>(), dice.begin());
```



##### Other Useful Iterators

The iterator header file provides some other special-purpose predefined iterator types in addition to ostream_iterator and istream_iterator.They are reverse_iterator, back_insert_iterator, front_insert_iterator,and insert_iterator.

```c++
copy(dice.rbegin(), dice.rend(), out_iter); // display in reverse order
```

Both rbegin() and end() return the same value (past-the-end), but as a different type (reverse_iterator versus iterator). Similarly, both rend() and begin() return the same value (an iterator to the first element), but as a different type.

```c++
#include <iostream>
#include <iterator>
#include <vector>
int main()
{
    using namespace std;
    int casts[10] = {6, 7, 2, 9, 4, 11, 8, 7, 10, 5};
    vector<int> dice(10);
    // copy from array to vector
    copy(casts, casts + 10, dice.begin());
    cout << "Let the dice be cast!\n";
    // create an ostream iterator
    ostream_iterator<int, char> out_iter(cout, " ");
    // copy from vector to output
    copy(dice.begin(), dice.end(), out_iter);
    cout << endl;
    cout << "Implicit use of reverse iterator.\n";
    copy(dice.rbegin(), dice.rend(), out_iter);
    cout << endl;
    cout << "Explicit use of reverse iterator.\n";
    vector<int>::reverse_iterator ri;
    for (ri = dice.rbegin(); ri != dice.rend(); ++ri)
        cout << *ri << ' ';
    cout << endl;
    return 0;
}
```

The output:

```
Let the dice be cast!
6 7 2 9 4 11 8 7 10 5
Implicit use of reverse iterator.
5 10 7 8 11 4 9 2 7 6
Explicit use of reverse iterator.
5 10 7 8 11 4 9 2 7 6
```



The other three iterators (back_insert_iterator, front_insert_iterator,and insert_iterator) also increase the generality of the STL algorithms. Many STL functions are like copy() in that they send their results to a location indicated by an output iterator.

The three insert iterators solve these problems by converting the copying process to an insertion process. Insertion adds new elements without overwriting existing data,and it uses automatic memory allocation to ensure that the new information fits.A back_insert_iterator inserts items at the end of the container,and a front_insert_iterator inserts items at the front. Finally, the insert_iterator inserts items in front of the location specified as an argument to the insert_iterator constructor.All three of these iterators are models of the output container concept

There are restrictions.A back_insert_iterator can be used only with container types that allow rapid insertion at the end. (Rapid refers to a constant time algorithm; the section “Container Concepts,” later in this chapter, discusses the constant time concept further.) The vector class qualifies.A front_insert_iterator can be used only with container types that allow constant time insertion at the beginning. Here the vector class doesn’t qualify, but the queue class does.The insert_iterator doesn’t have these restrictions.

```c++
#include <iostream>
#include <string>
#include <iterator>
#include <vector>
#include <algorithm>
void output(const std::string &s) { std::cout << s << " "; }
int main()
{
    using namespace std;
    string s1[4] = {"fine", "fish", "fashion", "fate"};
    string s2[2] = {"busy", "bats"};
    string s3[2] = {"silly", "singers"};
    vector<string> words(4);
    copy(s1, s1 + 4, words.begin());
    for_each(words.begin(), words.end(), output);
    cout << endl;
    // construct anonymous back_insert_iterator object
    copy(s2, s2 + 2, back_insert_iterator<vector<string>>(words));
    for_each(words.begin(), words.end(), output);
    cout << endl;
    // construct anonymous insert_iterator object
    copy(s3, s3 + 2, insert_iterator<vector<string>>(words, words.begin()));
    for_each(words.begin(), words.end(), output);
    cout << endl;
    return 0;
}
```

The output:

```
fine fish fashion fate
fine fish fashion fate busy bats
silly singers fine fish fashion fate busy bats
```



#### Kinds of Containers

The STL has both container concepts and container types.The concepts are general categories with names such as container, sequence container,and associative container.The container types are templates you can use to create specific container objects.The original 11 container types are deque, list, queue, priority_queue, stack, vector, map, multimap, set, multiset,and bitset.



A container is an object that stores other objects, which are all of a single type.The stored objects may be objects in the OOP sense, or they may be values of built-in types. Data stored in a container is owned by the container.That means when a containered in the container. 

You can’t store just any kind of object in a container. In particular, the type has to be copy constructable and assignable. Basic types satisfy these requirements,as do class types— unless the class definition makes one or both of the copy constructor and the assignment operator private or protected.

![image-20200726004056395](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200726004056395.png)

![image-20200726004733391](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200726004733391.png)

![image-20200726004758181](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200726004758181.png)

(X represents a container type (such as vector), T represents the type of object stored in the container, a and b represent values of type X, r is a value of type X&,and u represents an identifier of type X)

 

If the complexity is compile time, the action is performed during compilation and uses no execution time.A constant complexity means the operation takes place during runtime but doesn’t depend on the number of elements in an object.A linear complexity means the time is proportional to the number of elements。



##### Sequences

You can refine the basic container concept by adding requirements.The sequence is an important refinement because several of the STL container types—deque, forward_list (C++11), list, queue, priority_queue, stack,and vector—are sequences.

![image-20200726010856514](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200726010856514.png)



![image-20200726011301212](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200726011301212.png)



###### vector

The class provides automatic memory management that allows the size of a vector object to vary dynamically, growing and shrinking as elements are added or removed. It provides random access to elements. Elements can be added to or removed from the end in constant time, but insertion and removal from the beginning and the middle are linear-time operations



###### deque

The deque template class (declared in the deque header file) represents a double-ended queue,a type often called a deque (pronounced “deck”), for short. The main difference is that inserting and removing items from the beginning of a deque object are constanttime operations instead of being linear-time operations the way they are for vector. So if most operations take place at the beginning and ends of a sequence, you should consider using a deque data structure.

The goal of constant-time insertion and removal at both ends of a deque makes the design of a deque object more complex than that of a vector object.Thus,although both offer random access to elements and linear-time insertion and removal from the middle of a sequence, the vector container should allow faster execution of these operations.



###### list

The list template class (declared in the list header file) represents a doubly linked list. Each element, other than the first and last, is linked to the item before it and the item following it, implying that a list can be traversed in both directions.The crucial difference between list and vector is that list provides for constant-time insertion and removal of elements at any location in the list.

Like vector, list is a reversible container. Unlike vector, list does not support array notation and random access. Unlike a vector iterator,a list iterator remains pointing to the same element even after items are inserted into or removed from a container. 



The list template class has some list-oriented member functions in addition to those that come with sequences and reversible containers.Table 16.9 lists many of them. (For a complete list of STL methods and functions, see Appendix G.) The Alloc template parameter is one you normally don’t have to worry about because it has a default value.

![image-20200726014249591](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200726014249591.png)



###### forward_list (C++11)

C++11 adds forward_list as a container class.This class implements a singly linked list. In this kind of list, each item is linked just to the next item, but not to the preceding item. Therefore, the class requires just a forward iterator, not a bidirectional one.



###### queue

The queue template class (declared in the queue—formerly queue.h—header file) is an adapter class. Recall that the ostream_iterator template is an adapter that allows an output stream to use the iterator interface. Similarly, the queue template allows an underlying class (deque, by default) to exhibit the typical queue interface.

The queue template is more restrictive than deque. Not only does it not permit random access to elements of a queue, the queue class doesn’t even allow you to iterate through a queue. 

The queue template is more restrictive than deque. Not only does it not permit random access to elements of a queue, the queue class doesn’t even allow you to iterate through a queue. Instead, it limits you to the basic operations that define a queue.

![image-20200726192151343](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200726192151343.png)



###### priority_queue

The priority_queue template class (declared in the queue header file) is another adapter class. It supports the same operations as queue.The main difference between the two is that with priority_queue, the largest item gets moved to the front of the queue.



###### stack

Like queue, stack (declared in the stack—formerly stack.h—header file) is an adapter class. It gives an underlying class (vector, by default) the typical stack interface.

You can alter the comparison used to determine what gets to the head of the queue by providing an optional constructor argument:

```c++
priority_queue<int> pq1; // default version
priority_queue<int> pq2(greater<int>); // use greater<int> to order
//talk about greater later
```

The stack template is more restrictive than vector. Not only does it not permit random access to elements of a stack, the stack class doesn’t even allow you to iterate through a stack. Instead, it limits you to the basic operations that define a stack.You can push a value onto the top of a stack, pop an element from the top of a stack, view the value at the top of a stack, check the number of elements,and test whether the stack is empty.

![image-20200726194223361](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200726194223361.png)



###### array





#### Associative Containers

An associative container associates a value with a key and uses the key to find the value. For example, the values could be structures representing employee information, such as name,address, office number, home and work phones, health plan,and so on,and the key could be a unique employee number.To fetch the employee information,a program would use the key to locate the employee structure.

Associative containers typically are implemented using some form of tree.

The STL provides four associative containers: set, multiset, map,and multimap

The simplest of the bunch is set; the value type is the same as the key type,and the keys are unique, meaning there is no more than one instance of a key in a set. Indeed, for set, the value is the key.The multiset type is like the set type except that it can have more than one value with the same key. For example, if the key and value type are int, a multiset object could hold, say 1, 2, 2, 2, 3, 5, 7,and 7. For the map type, the value type is different from the key type,and the keys are unique, with only one value per key.The multimap type is similar to map, except one key can be associated with multiple values.



##### A set Example

The STL set models several concepts. It is an associative set, it is reversible, it is sorted, and the keys are unique, so it can hold no more than one of any given value. Like vector and list, set uses a template parameter to provide the type stored:

```c++
set<string> A; // a set of string objects
```

An optional second template argument can be used to indicate a comparison function or object to be used to order the key. By default, the less<> template (discussed later) is used. Older C++ implementations may not provide a default value and thus require an explicit template parameter:

```
set<string, less<string> > A; // older implementation
```

This provides a simple way to initialize a set to the contents of an array. Remember that the last element of a range is one past-the-end,and s1 + N points to one position past-the-end of array s1.The output for this code fragment illustrates that keys are unique (the string "for" appears twice in the array but once in the set) and that the set is sorted:

```c++
buffoon can for heavy thinkers
```



Mathematics defines some standard operations for sets. For example, the union of two sets is a set that combines the contents of the two sets. If a particular value is common to both sets, it appears just once in the union because of the unique key feature.The intersection of two sets is a set that consists of the elements that are common to both sets.The difference between two sets is the first set minus the elements common to both sets.

The STL provides algorithms that support these operations.They are general functions rather than methods, so they aren’t restricted to set objects. However,all set objects automatically satisfy the precondition for using these algorithms—namely, that the container be sorted.The set_union() function takes five iterators as arguments.The first two define a range in one set, the second two define a range in a second set,and the final iterator is an output iterator that identifies a location to which to copy the resultant set. 

```c++
// setops.cpp -- some set operations
#include <iostream>
#include <string>
#include <set>
#include <algorithm>
#include <iterator>
int main()
{
    using namespace std;
    const int N = 6;
    string s1[N] = {"buffoon", "thinkers", "for", "heavy", "can", "for"};
    string s2[N] = {"metal", "any", "food", "elegant", "deliver", "for"};
    set<string> A(s1, s1 + N);
    set<string> B(s2, s2 + N);
    
    ostream_iterator<string, char> out(cout, " ");
    cout << "Set A: ";
    copy(A.begin(), A.end(), out);
    cout << endl;
    cout << "Set B: ";
    copy(B.begin(), B.end(), out);
    cout << endl;
    
    cout << "Union of A and B:\n";
    set_union(A.begin(), A.end(), B.begin(), B.end(), out);
    cout << endl;
    
    cout << "Intersection of A and B:\n";
    set_intersection(A.begin(), A.end(), B.begin(), B.end(), out);
    cout << endl;
    
    cout << "Difference of A and B:\n";
    set_difference(A.begin(), A.end(), B.begin(), B.end(), out);
    cout << endl;
    
    set<string> C;
    cout << "Set C:\n";
    set_union(A.begin(), A.end(), B.begin(), B.end(),
              insert_iterator<set<string>>(C, C.begin()));
    copy(C.begin(), C.end(), out);
    cout << endl;
    string s3("grungy");
    C.insert(s3);
    cout << "Set C after insertion:\n";
    copy(C.begin(), C.end(), out);
    cout << endl;
    cout << "Showing a range:\n";
    copy(C.lower_bound("ghost"), C.upper_bound("spook"), out);
    cout << endl;
    return 0;
}
```

Sample output:

```c++
Set A: buffoon can for heavy thinkers
Set B: any deliver elegant food for metal
Union of A and B:
any buffoon can deliver elegant food for heavy metal thinkers
Intersection of A and B:
for
Difference of A and B:
buffoon can heavy thinkers
Set C:
any buffoon can deliver elegant food for heavy metal thinkers
Set C after insertion:
any buffoon can deliver elegant food for grungy heavy metal thinkers
Showing a range:
grungy heavy metal
```



##### A multimap Example

The basic multimap declaration specifies the key type and the type of value, stored as template arguments. For example, the following declaration creates a multimap object that uses int as the key type and string as the type of value stored:

```c++
multimap<int,string> codes;
```

An optional third template argument can be used to indicate a comparison function or an object to be used to order the key. By default, the less<> template (discussed later) is used with the key type as its parameter

To keep information together, the actual value type combines the key type and the data type into a single pair.To do this, the STL uses a pair template class for storing two kinds of values in a single object. If keytype is the key type and datatype is the type of the stored data, the value type is pair.

Suppose that you want to store city names, using the area code as a key.This happens to fit the codes declaration, which uses an int for a key and a string as a data type. One approach is to create a pair and then insert it into the multimap object:

```c++
pair<const int, string> item(213, "Los Angeles");
codes.insert(item);
```

Or you can create an anonymous pair object and insert it in a single statement:

```c++
codes.insert(pair<const int, string> (213, "Los Angeles"));
```

Given a pair object, you can access the two components by using the first and second members:

```c++
pair<const int, string> item(213, "Los Angeles");
cout << item.first << ' ' << item.second << endl;
```



The count() member function takes a key as its argument and returns the number of items that have that key. The lower_bound() and upper_bound() member functions take a key and work as they do for set.Also the equal_range() member function takes a key as its argument and returns iterators representing the range matching that key. In order to return two values, the method packages them into a pair object, this time with both template arguments being the iterator type.

For example, the following would print a list of cities in the codes object with area code 718:

```c++
pair<multimap<KeyType, string>::iterator,
multimap<KeyType, string>::iterator> range
= codes.equal_range(718);
cout << "Cities with area code 718:\n";
std::multimap<KeyType, std::string>::iterator it;
for (it = range.first; it != range.second; ++it)
cout << (*it).second << endl;
```

Also, we can use an auto type.



An example:

```c++
#include <iostream>
#include <string>
#include <map>
#include <algorithm>
typedef int KeyType;
typedef std::pair<const KeyType, std::string> Pair;
typedef std::multimap<KeyType, std::string> MapCode;
int main()
{
    using namespace std;
    MapCode codes;
    codes.insert(Pair(415, "San Francisco"));
    codes.insert(Pair(510, "Oakland"));
    codes.insert(Pair(718, "Brooklyn"));
    codes.insert(Pair(718, "Staten Island"));
    codes.insert(Pair(415, "San Rafael"));
    codes.insert(Pair(510, "Berkeley"));
    cout << "Number of cities with area code 415: "
         << codes.count(415) << endl;
    cout << "Number of cities with area code 718: "
         << codes.count(718) << endl;
    cout << "Number of cities with area code 510: "
         << codes.count(510) << endl;
    cout << "Area Code City\n";
    MapCode::iterator it;
    for (it = codes.begin(); it != codes.end(); ++it)
        cout << " " << (*it).first << " "
             << (*it).second << endl;
    pair<MapCode::iterator, MapCode::iterator> range = codes.equal_range(718);
    cout << "Cities with area code 718:\n";
    for (it = range.first; it != range.second; ++it)
        cout << (*it).second << endl;
    return 0;
}
```





#### Unordered Associative Containers (C++11)

An unordered associative container is yet another refinement of the container concept. Like an associative container,an unordered associative container associates a value with a key and uses the key to find the value.The underlying difference is that associative containers are based on tree structures, whereas unordered associative containers are based on another form of data structure called a hash table.The intent is to provide containers for which adding and deleting elements is relatively quick and for which there are efficient search algorithms.The four unordered associative containers are called unordered_set, unordered_multiset, unordered_map,and unordered_multimap.







### Function Objects (a.k.a. Functors) 

Many STL algorithms use function objects,also known as functors.A functor is any object that can be used with () in the manner of a function.This includes normal function names, pointers to functions,and class objects for which the () operator is overloaded—that is, classes for which the peculiar-looking function operator()() is defined.

e.g.

```c++
class Linear
{
private:
    double slope;
    double y0;

public:
    Linear(double sl_ = 1, double y_ = 0)
        : slope(sl_), y0(y_) {}
    double operator()(double x) { return y0 + slope * x; }
};
```

The overloaded () operator then allows you to use Linear objects like functions:

```c++
Linear f1;
Linear f2(2.5, 10.0);
double y1 = f1(12.5); // right-hand side is f1.operator()(12.5)
double y2 = f2(0.4);
```



Remember the for_each function? It applied a specified function to each member of a range:

```c++
for_each(books.begin(), books.end(), ShowReview);
```

In general, the third argument could be a functor, not just a regular function. Actually, this raises a question: How do you declare the third argument? You can’t declare it as a function pointer because a function pointer specifies the argument type. Because a container can contain just about any type, you don’t know in advance what particular argument type should be used.



#### Functor Concepts

- A generator is a functor that can be called with no arguments. 
- A unary function is a functor that can be called with one argument. 
- A binary function is a functor that can be called with two arguments.

For example, the functor supplied to for_each() should be a unary function because it is applied to one container element at a time.

A unary function that returns a bool value is a predicate. A binary function that returns a bool value is a binary predicate.



The list template has a remove_if() member that takes a predicate as an argument. It applies the predicate to each member in the indicated range, removing those elements for which the predicate returns true. For example, the following code would remove all elements greater than 100 from the list three:

```c++
bool tooBig(int n){ return n > 100; }
list<int> scores;
...
scores.remove_if(tooBig);
```

Suppose you want to remove every value greater than 200 from a second list. It would be nice if you could pass the cut-off value to tooBig() as a second argument so you could use the function with different values, but a predicate can have but one argument. If, however, you design a TooBig class, you can use class members instead of function arguments to convey additional information:

```c++
template <class T>
class TooBig
{
private:
    T cutoff;

public:
    TooBig(const T &t) : cutoff(t) {}
    bool operator()(const T &v) { return v > cutoff; }
};
```

Here one value (v) is passed as a function argument,and the second argument (cutoff) is set by the class constructor. Given this definition, you can initialize different TooBig objects to different cut-off values to be used in calls to remove_if().

```c++
TooBig<int> f100(100); // limit = 100
int vals[10] = {50, 100, 90, 180, 60, 210, 415, 88, 188, 201};
list<int> yadayada(vals, vals + 10); // range constructor
list<int> etcetera(vals, vals + 10);

yadayada.remove_if(f100); // use a named function object
etcetera.remove_if(TooBig<int>(200)); // construct a function object
```



#### Predefined Functors

The STL defines several elementary functors.They perform actions such as adding two values and comparing two values for equality.They are provided to help support STL functions that take functions as arguments. 

For example, consider the transform() function. It has two versions.The first version takes four arguments.The first two arguments are iterators that specify a range in a container. (By now you must be familiar with that approach.) The third is an iterator that specifies where to copy the result.The final is a functor that is applied to each element in the range to produce each new element in the result.

```c++
const int LIM = 5;
double arr1[LIM] = {36, 39, 42, 45, 48};
vector<double> gr8(arr1, arr1 + LIM);
ostream_iterator<double, char> out(cout, " ");
transform(gr8.begin(), gr8.end(), out, sqrt);
```

This code calculates the square root of each element and sends the resulting values to the output stream.The destination iterator can be in the original range. For example, replacing out in this example with gr8.begin() would copy the new values over the old values. Clearly, the functor used must be one that works with a single argument.



The second version uses a function that takes two arguments,applying the function to one element from each of two ranges. It takes an additional argument, which comes third in order, identifying the start of the second range. For example, if m8 were a second vector object and if mean(double, double) returned the mean of two values, the following would output the average of each pair of values from gr8 and m8:

Now suppose you want to add the two arrays.You can’t use + as an argument because, for type double, + is a built-in operator, not a function.You could define a function to add two numbers and use it:

```c++
double add(double x, double y) { return x + y; }
...
transform(gr8.begin(), gr8.end(), m8.begin(), out, add);
```

But then you’d have to define a separate function for each type. It would be better to define a template, except that you don’t have to because the STL already has.The functional (formerly function.h) header defines several template class function objects, including one called plus<>(). Using the plus<> class for ordinary addition is possible, if awkward:

```c++
#include <functional>
...
plus<double> add; // create a plus<double> object
double y = add(2.2, 3.4); // using plus<double>::operator()()

transform(gr8.begin(), gr8.end(), m8.begin(), out, plus<double>() );
```



#### Adaptable Functors and Function Adapters

Actually, the STL has five related concepts:adaptable generators,adaptable unary functions,adaptable binary functions, adaptable predicates,and adaptable binary predicates.

What makes a functor adaptable is that it carries typedef members identifying its argument types and return type.The members are called result_type, first_argument_type,and second_argument_type,and they represent what they sound like.

The significance of a functor being adaptable is that it can then be used by function adapter objects, which assume the existence of these typedef members. For example,a function with an argument that is an adaptable functor can use the result_type member to declare a variable that matches the function’s return type.



Indeed, the STL provides function adapter classes that use these facilities. For example, suppose you want to multiply each element of the vector gr8 by 2.5.That calls for using the transform() version with a unary function argument, like the example shown earlier:

```c++
transform(gr8.begin(), gr8.end(), out, sqrt);
```

The multiplies() functor can do the multiplication, but it’s a binary function. So you need a function adapter that converts a functor that has two arguments to one that has one argument. The STL has automated the process with the binder1st and binder2nd classes, which convert adaptable binary functions to adaptable unary functions.

Suppose you have an adaptable binary function object f2(). You can create a binder1st object that binds a particular value, called val, to be used as the first argument to f2():

```c++
binder1st(f2, val) f1;
```

Then, invoking f1(x) with its single argument returns the same value as invoking f2() with val as its first argument and f1()’s argument as its second argument.That is, f1(x) is equivalent to f2(val, x), except that it is a unary function instead of a binary function. The f2() function has been adapted.Again, this is possible only if f2() is an adaptable function.

 You can also do something like this:

```c++
transform(gr8.begin(), gr8.end(), out,
bind1st(multiplies<double>(), 2.5));
```





### Algorithms 

The STL contains many nonmember functions for working with containers.You’ve seen a few of them already: sort(), copy(), find(), for_each(), random_shuffle(), set_union(), set_intersection(), set_difference(),and transform().

There are two main generic components to the algorithm function designs. First, they use templates to provide generic types. Second, they use iterators to provide a generic representation for accessing data in a container.

#### Algorithm Groups

The STL divides the algorithm library into four groups:

- Nonmodifying sequence operations 
- Mutating sequence operations
- Sorting and related operations 
- Generalized numeric operations

The first three groups are described in the algorithm (formerly algo.h) header file, and the fourth group, being specifically oriented toward numeric data, gets its own header file, called numeric. (Formerly, they, too, were in algo.h.)



#### Functions Versus Container Methods

Sometimes you have a choice between using an STL method and an STL function. Usually, the method is the better choice. First, it should be better optimized for a particular container. Second, being a member function, it can use a template class’s memory management facilities and resize a container when needed.







### Other Libraries 

C++ provides some other class libraries that are more specialized than the examples covered so far in this chapter. 



#### vector, valarray, and array

The vector template class is part of a system of container classes and algorithms.The vector class supports container-oriented activities, such as sorting, insertion, rearrangement, searching, transferring data to other containers,and other manipulations.The valarray class template, on the other hand, is oriented toward numeric computation,and it is not part of the STL. It doesn’t have push_back() and insert() methods, for example, but it does provide a simple, intuitive interface for many mathematical operations. Finally, array is designed as a substitute for the built-in array type, combining the compactness and efficiency of that type with a better, safer interface. Being of fixed size, array doesn’t support push_back() and insert(), but it does offer several other STL methods.These include begin(), end(), rbegin(),and rend(), making it easy to apply STL algorithms to array objects.

For example:

```c++
vector<double> ved1(10), ved2(10), ved3(10);
array<double, 10> vod1, vod2, vod3;
valarray<double> vad1(10), vad2(10), vad3(10);
```

Suppose you want to assign the sum of the first elements of two arrays to the first element of a third array,and so on.

```c++
transform(ved1.begin(), ved1.end(), ved2.begin(), ved3.begin(), plus<double>());
transform(vod1.begin(), vod1.end(), vod2.begin(), vod3.begin(), plus<double>());
```

However, the valarray class overloads all the arithmetic operators to work with valarray objects, so you would use this:

```c++
vad3 = vad1 + vad2; // + overloaded
```



Suppose you want to replace every value in an array with that value multiplied by 2.5. The STL approach is this:

```c++
transform(ved3.begin(), ved3.end(), ved3.begin(), bind1st(multiplies<double>(), 2.5));
```

The valarray class overloads multiplying a valarray object by a single value,and it also overloads the various computed assignment operators, so you could use either of the following:

```c++
vad3 = 2.5 * vad3; // * overloaded
vad3 *= 2.5; // *= overloaded
```



Suppose you want to take the natural logarithm of every element of one array and store the result in the corresponding element of a second array.The STL approach is this:

```c++
transform(ved1.begin(), ved1.end(), ved3.begin(), log);
```

The valarray class overloads the usual math functions to take a valarray argument and to return a valarray object, so you can use this:

```c++
vad3 = log(vad1); // log() overloaded
```

Or you could use the apply() method, which also works for non-overloaded functions:

```c++
vad3 = vad1.apply(log);
```

The apply() method doesn’t alter the invoking object; instead, it returns a new object that contains the resulting values.



The simplicity of the valarray interface is even more apparent when you do a multistep calculation:

```c++
vad3 = 10.0* ((vad1 + vad2) / 2.0 + vad1 * cos(vad2));
```



The valarray class also provides a sum() method that sums the contents of a valarray object,a size() method that returns the number of elements,a max() method that returns the largest value in an object,and a min() method that returns the smallest value. 

There are no methods for inserting values, searching, sorting,and the like. In short, the valarray class is more limited than the vector class, but its narrower focus allows a much simpler interface.



C++11 remedies the situation by providing begin() and end() template functions that take a valarray object as an argument. So you would use begin(vad) instead of vad.begin().These functions return values that are compatible with STL range requirements:

```c++
sort(begin(vad), end(vad)); // C++11 fix!
```





There are extended versions of subscripting. Let’s look at one—the slice class.A slice class object can be used as an array index, in which case it represents, in general, not just one value but a subset of values.A slice object is initialized to three integer values: the start, the number,and the stride.The start indicates the index of the first element to be selected, the number indicates the number of elements to be selected,and the stride represents the spacing between elements. For example, the object constructed by slice(1,4,3) means select the four elements whose indexes are 1, 4, 7,and 10.That is, start with the start element,add the stride to get the next element,and so on until four elements are selected.

If, say, varint is a vararray object, then the following statement would set elements 1, 4, 7,and 10 to the value 10:

```c++
varint[slice(1,4,3)] = 10; // set selected elements to 10
```

This special subscripting facility allows you to use a one-dimensional valarray object to represent two-dimensional data. For example, suppose you want to represent an array with 4 rows and 3 columns.You can store the information in a 12-element valarray object.Then a slice(0,3,1) object used as a subscript would represent elements 0, 1, and 2—that is, the first row. Similarly,a slice(0,4,3) subscript would represent elements 0, 3, 6,and 9—that is, the first column.



An example:

```c++
// vslice.cpp -- using valarray slices
#include <iostream>
#include <valarray>
#include <cstdlib>
const int SIZE = 12;
typedef std::valarray<int> vint; // simplify declarations
void show(const vint &v, int cols);
int main()
{
    using std::cout;
    using std::slice;  // from <valarray>
    vint valint(SIZE); // think of as 4 rows of 3
    int i;
    for (i = 0; i < SIZE; ++i)
        valint[i] = std::rand() % 10;
    cout << "Original array:\n";
    show(valint, 3);                   // show in 3 columns
    vint vcol(valint[slice(1, 4, 3)]); // extract 2nd column
    cout << "Second column:\n";
    show(vcol, 1);                     // show in 1 column
    vint vrow(valint[slice(3, 3, 1)]); // extract 2nd row
    cout << "Second row:\n";
    show(vrow, 3);
    valint[slice(2, 4, 3)] = 10; // assign to 2nd column
    cout << "Set last column to 10:\n";
    show(valint, 3);
    cout << "Set first column to sum of next two:\n";
    // + not defined for slices, so convert to valarray<int>
    valint[slice(0, 4, 3)] = vint(valint[slice(1, 4, 3)]) + vint(valint[slice(2, 4, 3)]);
    show(valint, 3);
    return 0;
}
void show(const vint &v, int cols)
{
    using std::cout;
    using std::endl;
    int lim = v.size();
    for (int i = 0; i < lim; ++i)
    {
        cout.width(3);
        cout << v[i];
        if (i % cols == cols - 1)
            cout << endl;
        else
            cout << ' ';
    }
    if (lim % cols != 0)
        cout << endl;
}
```

Sample Output:

```
Original array:
  1   7   4    
  0   9   4    
  8   8   2    
  4   5   5    
Second column: 
  7
  9
  8
  5
Second row:
  0   9   4
Set last column to 10:
  1   7  10
  0   9  10
  8   8  10
  4   5  10
Set first column to sum of next two:
 17   7  10
 19   9  10
 18   8  10
 15   5  10
```



#### The initializer_list Template (C++11)

The initializer_list template is another C++11 addition to the C++ library.You can use the initializer-list syntax to initialize an STL container to a list of values:

```c++
std::vector<double> payments {45.99, 39.23, 19.95, 89.01};
```

t.A vector object, for example, has a constructor that accepts an initializer_list argument,and the previous declaration is the same as this:

```c++
std::vector<double> payments({45.99, 39.23, 19.95, 89.01});
```



##### Using initializer_list

You can use initializer_list objects in your code by including the initializer_list header file.The template class has begin() and end() members,and you can use them to access list elements. It also has a size() member that returns the number of elements.

```c++
// ilist.cpp -- use initializer_list (C++11 feature)
#include <iostream>
#include <initializer_list>
double sum(std::initializer_list<double> il);
double average(const std::initializer_list<double> &ril);
int main()
{
    using std::cout;
    cout << "List 1: sum = " << sum({2, 3, 4})
         << ", ave = " << average({2, 3, 4}) << '\n';
    std::initializer_list<double> dl = {1.1, 2.2, 3.3, 4.4, 5.5};
    cout << "List 2: sum = " << sum(dl)
         << ", ave = " << average(dl) << '\n';
    dl = {16.0, 25.0, 36.0, 40.0, 64.0};
    cout << "List 3: sum = " << sum(dl)
         << ", ave = " << average(dl) << '\n';
    return 0;
}
double sum(std::initializer_list<double> il)
{
    double tot = 0;
    for (auto p = il.begin(); p != il.end(); p++)
        tot += *p;
    return tot;
}
double average(const std::initializer_list<double> &ril)
{
    double tot = 0;
    int n = ril.size();
    double ave = 0.0;
    if (n > 0)
    {
        for (auto p = ril.begin(); p != ril.end(); p++)
            tot += *p;
        ave = tot / n;
    }
    return ave;
}
```

You can pass an initializer_list object by value or by reference,as shown by sum() and average().The object itself is small, typically two pointers (one to the beginning and one past end) or a pointer to the beginning and an integer representing the size, so the choice is not a major performance issue.



The iterator types for initializer_list are const, so you can’t change the values in a list:

```c++
*dl.begin() = 2011.6; // not allowed
```

But,as Listing 16.22 shows, you can attach a list variable to a different list:

```
dl = {16.0, 25.0, 36.0, 40.0, 64.0}; // allowed
```





















## Input, Output, and Files 

### An Overview of C++ Input and Output 

#### Streams and Buffers

A C++ program views input or output as a stream of bytes. A stream acts as an intermediary between the program and the stream’s source or destination.This approach enables a C++ program to treat input from a keyboard in the same manner it treats input from a file; the C++ program merely examines the stream of bytes without needing to know where the bytes come from. Similarly, by using streams,a C++ program can process output in a manner independent of where the bytes are going

<img src="C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200729000155816.png" alt="image-20200729000155816" style="zoom:67%;" />



#### Streams, Buffers, and the iostream File

The business of managing streams and buffers can get a bit complicated, but including the iostream (formerly iostream.h) file brings in several classes designed to implement and manage streams and buffers for you.

- The streambuf class provides memory for a buffer,along with class methods for filling the buffer,accessing buffer contents, flushing the buffer,and managing the buffer memory. 
- The ios_base class represents general properties of a stream, such as whether it’s open for reading and whether it’s a binary or a text stream. 
- The ios class is based on ios_base,and it includes a pointer member to a streambuf object. 
- The ostream class derives from the ios class and provides output methods. n The istream class derives from the ios class and provides input methods. 
- The iostream class is based on the istream and ostream classes and thus inherits both input and output methods.

<img src="C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200729000801850.png" alt="image-20200729000801850" style="zoom:80%;" />

The C++ iostream class library takes care of many details for you. For example, including the iostream file in a program creates eight stream objects (four for narrow character streams and four for wide character streams) automatically:

- The cin object corresponds to the standard input stream. By default, this stream is associated with the standard input device, typically a keyboard.The wcin object is similar but works with the wchar_t type.
- The cout object corresponds to the standard output stream. By default, this stream is associated with the standard output device, typically a monitor.The wcout object is similar but works with the wchar_t type. 
- The cerr object corresponds to the standard error stream, which you can use for displaying error messages. By default, this stream is associated with the standard output device, typically a monitor,and the stream is unbuffered.This means that information is sent directly to the screen, without waiting for a buffer to fill or for a newline character.The wcerr object is similar but works with the wchar_t type. 
- The clog object also corresponds to the standard error stream. By default, this stream is associated with the standard output device, typically a monitor,and the stream is buffered.The wclog object is similar but works with the wchar_t type



A statement such as the following places the characters from the string "Bjarne free" into the buffer managed by cout via the pointed-to streambuf object:

```c++
cout << "Bjarne free";
```



#### Redirection

The standard input and output streams normally connect to the keyboard and the screen. But many operating systems, including Unix, Linux,andWindows, support redirection,a facility that lets you change the associations for the standard input and the standard output.

A sample run might look like this:

```c++
C>counter
Hello
and goodbye!
Control-Z << simulated end-of-file
Input contained 19 characters.
C>
```

In this case, input came from the keyboard,and output went to the screen.

With input redirection (<) and output redirection (>), you can use the same program to count the number of characters in the oklahoma file and to place the results in the cow_cnt file:

```c++
C>counter <oklahoma >cow_cnt
C>
```

The cow_cnt part of the command line associates the standard output with the cow_cnt file, causing cout to send output to that file instead of to the screen.



If redirection is not in effect, whichever message is selected is displayed onscreen. If, however, the program output has been redirected to a file, the first message, if selected, would go to the file but the second message, if selected, would go to the screen。





### Output with cout 

One of the most important tasks facing the ostream class is converting numeric types, such as int or float, into a stream of characters that represents the values in text form.That is, the ostream class translates the internal representation of data as binary bit patterns to an output stream of character bytes. To perform these translation tasks, the ostream class provides several class methods.

#### The Overloaded << Operator

In C++,as in C, by default the << operator is used as the bitwise left-shift operator 

But the ostream class redefines the << operator through overloading to output for the ostream class. In this guise, the << operator is called the insertion operator instead of the left-shift operator.



##### Output and Pointers

The ostream class defines insertion operator functions for the following pointer types:

- const signed char * 
- const unsigned char * 
- const char * 
- void *

C++ represents a string, don’t forget, by using a pointer to the location of the string. The pointer can take the form of the name of an array of char or of an explicit pointerto-char or of a quoted string.Thus,all the following cout statements display strings:

```c++
char name[20] = "Dudly Diddlemore";
char * pn = "Violet D'Amore";
cout << "Hello!";
cout << name;
cout << pn;
```



##### Output Concatenation



#### The Other ostream Methods

Besides the various operator<<() functions, the ostream class provides the put() method for displaying characters and the write() method for displaying strings.

Here cout is the invoking object and put() is the class member function. Like the << operator functions, this function returns a reference to the invoking object, so you can concatenate output with it:

```c++
cout.put('I').put('t'); // displaying It with two put() calls
```



The write() method writes an entire string and has the following template prototype:

```c++
basic_ostream<charT,traits>& write(const char_type* s, streamsize n);
```

The first argument to write() provides the address of the string to be displayed,and the second argument indicates how many characters to display. Using cout to invoke write() invokes the char specialization, so the return type is ostream &.



#### Flushing the Output Buffer

Because the ostream class buffers output handled by the cout object, output isn’t sent to its destination immediately. Instead, it accumulates in the buffer until the buffer is full. Then the program flushes the buffer, sending the contents on and clearing the buffer for new data. Typically,a buffer is 512 bytes or an integral multiple thereof. Buffering is a great time-saver when the standard output is connected to a file on a hard disk.After all, you don’t want a program to access the hard disk 512 times to send 512 bytes. It’s much more effective to collect 512 bytes in a buffer and write them to a hard disk in a single disk operation.

If your implementation doesn’t flush output when you want it to, you can force flushing by using one of two manipulators.The flush manipulator flushes the buffer,and the endl manipulator flushes the buffer and inserts a newline character.You use these manipulators the way you would use a variable name:

```c++
cout << "Hello, good-looking! " << flush;
cout << "Wait just a moment, please." << endl;
```

Manipulators are, in fact, functions. For example, you can flush the cout buffer by calling the flush() function directly:

```c++
flush(cout);
```

However, the ostream class overloads the << insertion operator in such a way that the following expression gets replaced with the flush(cout) function call:

```c++
cout << flush;
```



#### Formatting with cout

The ostream insertion operators convert values to text form. By default, they format values as follows:

- A type char value, if it represents a printable character, is displayed as a character in a field one character wide. 
- Numeric integer types are displayed as decimal integers in a field just wide enough to hold the number and, if present,a minus sign. 
- Strings are displayed in a field equal in width to the length of the string.

Floating-point types are displayed with a total of six digits, except that trailing zeros aren’t displayed. (Note that the number of digits displayed has no connection with the precision to which the number is stored.) The number is displayed in fixed-point notation or else in E notation (see Chapter 3,“Dealing with Data”), depending on the value of the number. In particular, E notation is used if the exponent is 6 or larger or -5 or smaller.Again, the field is just wide enough to hold the number and, if present,a minus sign.The default behavior corresponds to using the standard C library function fprintf() with a %g specifier.



Example:

```c++
#include <iostream>
int main()
{
    using std::cout;
    cout << "12345678901234567890\n";
    char ch = 'K';
    int t = 273;
    cout << ch << ":\n";
    cout << t << ":\n";
    cout << -t << ":\n";
    double f1 = 1.200;
    cout << f1 << ":\n";
    cout << (f1 + 1.0 / 9.0) << ":\n";
    double f2 = 1.67E2;
    cout << f2 << ":\n";
    f2 += 1.0 / 9.0;
    cout << f2 << ":\n";
    cout << (f2 * 1.0e4) << ":\n";
    double f3 = 2.3e-4;
    cout << f3 << ":\n";
    cout << f3 / 10 << ":\n";
    return 0;
}
```

Sample Output:

```c++
12345678901234567890
K:
273:
-273:
1.2:
1.31111:
167:
167.111:
1.67111e+006:
0.00023:
2.3e-005:
```



##### Changing the Number Base Used for Display

The ostream class inherits from the ios class, which inherits from the ios_base class. The ios_base class stores information that describes the format state. For example, certain bits in one class member determine the number base used, whereas another member determines the field width. By using manipulators, you can control the number base used to display integers. By using ios_base member functions, you can control the field width and the number of places displayed to the right of the decimal.

Let’s look at how to set the number base to be used in displaying integers.To control whether integers are displayed in base 10, base 16, or base 8, you can use the dec, hex,and oct manipulators. For example, the following function call sets the number base format state for the cout object to hexadecimal

```c++
hex(cout);
```

Although the manipulators really are functions, you normally see them used this way:

```c++
cout << hex;
```



##### Adjusting Field Widths

You can use the width member function to place differently sized numbers in fields that have equal widths.The method has these prototypes:

```c++
int width();
int width(int i);
```

The width() method affects only the next item displayed,and the field width reverts to the default value afterward. 

```c++
cout << '#';
cout.width(12);
cout << 12 << "#" << 24 << "#\n";
```

Sample output:

```c++
#          12#24#
```



##### Fill Characters

By default, cout fills unused parts of a field with spaces.You can use the fill() member function to change that. For example, the following call changes the fill character to an asterisk(星号):

```c++
cout.fill('*');
```

Example:

```c++
#include <iostream>
int main()
{
    using std::cout;
    cout.fill('*');
    const char *staff[2] = {"Waldo Whipsnade", "Wilmarie Wooper"};
    long bonus[2] = {900, 1350};
    for (int i = 0; i < 2; i++)
    {
        cout << staff[i] << ": $";
        cout.width(7);
        cout << bonus[i] << "\n";
    }
    return 0;
}
```

Sample Output:

```c++
Waldo Whipsnade: $****900
Wilmarie Wooper: $***1350
```



##### Setting Floating-Point Display Precision

The meaning of floating-point precision depends on the output mode. In the default mode, it means the total number of digits displayed. In the fixed and scientific modes, to be discussed soon, precision means the number of digits displayed to the right of the decimal place.The precision default for C++,as you’ve seen, is 6.

For example, the following statement causes cout to set the precision to 2:

```c++
cout.precision(2);
```



##### Printing Trailing Zeros and Decimal Points

Certain forms of output, such as prices or numbers in columns, look better if trailing zeros are retained.

The iostream family of classes doesn’t provide a function whose sole purpose is to accomplish that. However, the ios_base class provides a setf() (for set flag) function that controls several formatting features.

For example, the following function call causes cout to display trailing decimal points:

```c++
cout.setf(ios_base::showpoint);
```

In the default floating-point format, it also causes trailing zeros to be displayed.That is, instead of displaying 2.00 as 2, cout will display it as 2.00000 if the default precision of 6 is in effect.



##### More About setf()

The setf() method controls several other formatting choices besides when the decimal point is displayed, so let’s take a closer look at it.The ios_base class has a protected data member in which individual bits (called flags in this context) control different formatting aspects, such as the number base and whether trailing zeros are displayed. Turning a flag on is called setting the flag (or bit) and means setting the bit to 1. (Bit flags are the programming equivalent to setting DIP switches to configure computer hardware.) 

The setf() function has two prototypes.

```c++
fmtflags setf(fmtflags);
```

Here fmtflags is a typedef name for a bitmask type used to hold the format flags.The name is defined in the ios_base class.This version of setf() is used for setting format information controlled by a single bit.The argument is a fmtflags value that indicates which bit to set.The return value is a type fmtflags number that indicates the former settings of all the flags.

<img src="C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200729215707691.png" alt="image-20200729215707691" style="zoom:80%;" />

A bitmask type is a type that is used to store individual bit values. It could be an integer type, an enum, or an STL bitset container. The main idea is that each bit is individually accessible and has its own meaning. The iostream package uses bitmask types to store state information. 



Example:

```c++
#include <iostream>
int main()
{
    using std::cout;
    using std::endl;
    using std::ios_base;
    int temperature = 63;
    cout << "Today's water temperature: ";
    cout.setf(ios_base::showpos); // show plus sign
    cout << temperature << endl;
    cout << "For our programming friends, that's\n";
    cout << std::hex << temperature << endl; // use hex
    cout.setf(ios_base::uppercase);          // use uppercase in hex
    cout.setf(ios_base::showbase);           // use 0X prefix for hex
    cout << "or\n";
    cout << temperature << endl;
    cout << "How " << true << "! oops -- How ";
    cout.setf(ios_base::boolalpha);
    cout << true << "!\n";
    return 0;
}
```

Sample Output:

```c++
Today's water temperature: +63
For our programming friends, that's
3f
or
0X3F
How 0X1! oops -- How true!
```



The second setf() prototype takes two arguments and returns the prior setting:

```c++
fmtflags setf(fmtflags , fmtflags );
```

The first argument,as before, is a fmtflags value that contains the desired setting.The second argument is a value that first clears the appropriate bits. For example, suppose setting bit 3 to 1 means base 10, setting bit 4 to 1 means base 8,and setting bit 5 to 1 means base 16. Suppose output is in base 10,and you want to set it to base 16. Not only do you have to set bit 5 to 1, you also have to set bit 3 to 0; this is called clearing the bit.The clever hex manipulator does both tasks automatically. Using the setf() function requires a bit more work because you use the second argument to indicate which bits to clear and then use the first argument to indicate which bit to set.

![image-20200729234558113](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200729234558113.png)

The second argument clears a batch of related bits; then the first argument sets one of those bits to 1.



The setf() function is a member function of the ios_base class. Because that’s a base class for the ostream class, you can invoke the function by using the cout object. For example, to request left-justification, you use this call:

```c++
ios_base::fmtflags old = cout.setf(ios::left, ios::adjustfield);
```



The effects of calling setf() can be undone with unsetf(), which has the following prototype:

```c++
void unsetf(fmtflags mask);
```

Here mask is a bit pattern.All bits set to 1 in mask cause the corresponding bits to be unset.That is, setf() sets bits to 1,and unsetf() sets bits back to 0. Here’s an example:

```c++
cout.setf(ios_base::showpoint); // show trailing decimal point
cout.unsetf(ios_base::boolshowpoint); // don't show trailing decimal point
cout.setf(ios_base::boolalpha); // display true, false
cout.unsetf(ios_base::boolalpha); // display 1, 0
```

You may have noticed that there is no special flag to indicate the default mode for displaying floating-point numbers. Here’s how the system works. Fixed notation is used if the fixed bit,and only the fixed bit is set. Scientific notation is used if the scientific bit and only the scientific bit is set.Any other combination, such as no bits set or both bits set, results in the default mode being used. So one way to invoke the default mode is this:

```c++
cout.setf(0, ios_base::floatfield); // go to default mode
```



##### Standard Manipulators

Using setf() is not the most user-friendly approach to formatting, so C++ offers several manipulators to invoke setf() for you,automatically supplying the right arguments. You’ve already seen dec, hex,and oct.

<img src="C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200730001258637.png" alt="image-20200730001258637" style="zoom:70%;" />![image-20200730001333951](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200730001333951.png)

![image-20200730001333951](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200730001333951.png)

![image-20200730001446438](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200730001446438.png)



##### The iomanip Header File

C++ supplies additional manipulators in the iomanip header file.They provide the same services already discussed, but in a notationally more convenient manner.The three most commonly used are setprecision() for setting the precision, setfill() for setting the fill character,and setw() for setting the field width.

EX:

```C++
#include <iostream>
#include <iomanip>
#include <cmath>
int main()
{
    using namespace std;
    // use new standard manipulators
    cout << fixed << right;
    // use iomanip manipulators
    cout << setw(6) << "N" << setw(14) << "square root"
         << setw(15) << "fourth root\n";
    double root;
    for (int n = 10; n <= 100; n += 10)
    {
        root = sqrt(double(n));
        cout << setw(6) << setfill('.') << n << setfill(' ')
             << setw(12) << setprecision(3) << root
             << setw(14) << setprecision(4) << sqrt(root)
             << endl;
    }
    return 0;
}
```

Sample output:

```
	 N   square root  fourth root
....10    	3.162 		1.7783
....20 		4.472 		2.1147
....30 		5.477 		2.3403
....40 		6.325 		2.5149
....50 		7.071 		2.6591
....60 		7.746 		2.7832
....70 		8.367 		2.8925
....80 		8.944 		2.9907
90 		9.487 		3.0801 ...
100 	10.000 		3.1623
```







### Input with cin 

#### How cin >> Views Input

The various versions of the extraction operator share a common way of looking at the input stream.They skip over white space (blanks, newlines,and tabs) until they encounter a non-white-space character.This is true even for the single-character modes (those in which the argument is type char, unsigned char, or signed char. It reads everything from the initial non-white-space character up to the first character that doesn’t match the destination type.

For example, consider the following code:

```c++
int elevation;
cin >> elevation;
```

Suppose you type the following characters:

```c++
-123Z
```

The operator will read the -, 1, 2,and 3 characters because they are all valid parts of an integer. But the Z character isn’t valid, so the last character accepted for input is the 3.The Z remains in the input stream,and the next cin statement will start reading at that point. Meanwhile, the operator converts the character sequence -123 to an integer value and assigns it to elevation.

It can happen that input fails to meet a program’s expectation. For example, suppose you enter Zcar instead of -123Z. In that case, the extraction operator leaves the value of elevation unchanged and returns the value 0. (More technically,an if or while statement evaluates an istream object as false if it’s had an error state set; we’ll discuss this in more depth later in this chapter.) The false return value allows a program to check whether input meets the program requirements.



#### Stream States

A cin or cout object contains a data member (inherited from the ios_base class) that describes the stream state. A stream state (defined as type iostate, which, in turn, is a bitmask type, such as described earlier) consists of the three ios_base elements: eofbit, badbit,and failbit. Each element is a single bit that can be 1 (set) or 0 (cleared).

When a cin operation reaches the end of a file, it sets eofbit.When a cin operation fails to read the expected characters,as in the earlier example, it sets failbit. I/O failures, such as trying to read a non-accessible file or trying to write to a write-protected disk,also can set failbit to 1. The badbit element is set when some undiagnosed failure may have corrupted the stream. (Implementations don’t necessarily agree about which events set failbit and which set badbit.)

![image-20200730004559628](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200730004559628.png)

![image-20200730004610577](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200730004610577.png)



##### Setting States

Two of the methods in Table 17.4, clear() and setstate(),are similar. Both reset the state, but they do so in a different fashion.The clear() method sets the state to its argument.Thus, the following call uses the default argument of 0, which clears all three state bits (eofbit, badbit,and failbit).

Similarly, the following call makes the state equal to eofbit; that is, eofbit is set,and the other two state bits are cleared:

```c++
clear(eofbit);
```

The setstate() method, however,affects only those bits that are set in its argument. Thus, the following call sets eofbit without affecting the other bits:

```c++
setstate(eofbit);
```



Why would you reset the stream state? For a program writer, the most common reason is to use clear() with no argument to reopen input after encountering mismatched input or end-of-file; whether doing so makes sense depends on what the program is trying to accomplish.You’ll see some examples shortly.The main purpose for setstate() is to provide a means for input and output functions to change the state.



##### I/O and Exceptions

Suppose that an input function sets eofbit. Does this cause an exception to be thrown? By default, the answer is no. However, you can use the exceptions() method to control how exceptions are handled.

The default setting for exceptions() is goodbit—that is, no exceptions thrown. However, the overloaded exceptions(iostate) function gives you control over the behavior:

```c++
cin.exceptions(badbit); // setting badbit causes exception to be thrown
```

The bitwise OR operator (|) allows you to specify more than one bit. For example, the following statement results in an exception being thrown if either badbit or eofbit is subsequently set:

```c++
cin.exceptions(badbit | eofbit);
```

EX:

```c++
#include <iostream>
#include <exception>
int main()
{
    using namespace std;
    // have failbit cause an exception to be thrown
    cin.exceptions(ios_base::failbit);
    cout << "Enter numbers: ";
    int sum = 0;
    int input;
    try
    {
        while (cin >> input)
        {
            sum += input;
        }
    }
    catch (ios_base::failure &bf)
    {
        cout << bf.what() << endl;
        cout << "O! the horror!\n";
    }
    cout << "Last value entered = " << input << endl;
    cout << "Sum = " << sum << endl;
    return 0;
}
```

The ios_base::failure exception class derives from the std::exception class and thus has a what() method.

Sample Output:

```
Enter numbers: 20 30 40 pi 6
ios_base failure in clear
O! the horror!
Last value entered = 40.00
Sum = 90.00
```



##### Stream State Effects

An if or while test such as the following tests as true only if the stream state is good (all bits cleared):

```c++
while (cin >> input)
```



If you want a program to read further input after a stream state bit has been set, you have to reset the stream state to good.This can be done by calling the clear() method

```c++
while (cin >> input)
{
sum += input;
}
cout << "Last value entered = " << input << endl;
cout << "Sum = " << sum << endl;
cout << "Now enter a new number: ";
cin.clear(); // reset stream state
while (!isspace(cin.get()))
	continue; // get rid of bad input
cin >> input; // will work now
```

Note that it is not enough to reset the stream state.The mismatched input that terminated the input loop is still in the input queue,and the program has to get past it. One way is to keep reading characters until reaching white space.The isspace() function (see Chapter 6,“Branching Statements and Logical Operators”) is a cctype function that returns true if its argument is a white-space character. Or you can discard the rest of the line instead of just the next word:

```c++
while (cin.get() != '\n')
	continue; // get rid rest of line
```

This example assumes that the loop terminated because of inappropriate input. Suppose, instead, that the loop terminated because of end-of-file or because of a hardware failure.Then the new code disposing of bad input makes no sense.You can fix matters by using the fail() method to test whether the assumption was correct. Because for historical reasons, fail() returns true if either failbit or eofbit is set, the code has to exclude the latter case.The following code shows an example of such exclusion:

```c++
while (cin >> input)
{
    sum += input;
}
cout << "Last value entered = " << input << endl;
cout << "Sum = " << sum << endl;
if (cin.fail() && !cin.eof()) // failed because of mismatched input
{
    cin.clear(); // reset stream state
    while (!isspace(cin.get()))
        continue; // get rid of bad input
}
else // else bail out
{
    cout << "I cannot go on!\n";
    exit(1);
}
cout << "Now enter a new number: ";
cin >> input; // will work now
```



#### Other istream Class Methods

##### Single-Character Input

###### The get(char &) Member Function

```c++
int ct = 0;
char ch;
cin.get(ch);
while (ch != '\n')
{
	cout << ch;
	ct++;
	cin.get(ch);
}
cout << ct << endl;
```

Pressing the Enter key sends this input line to the program.The program fragment reads the I character, displays it with cout,and increments ct to 1. Next, it reads the space character following the I, displays it,and increments ct to 2.This continues until the program processes the Enter key as a newline character and terminates the loop.The main point here is that, by using get(ch), the code reads, displays,and counts the spaces as well as the printing characters.

The get(char &) member function returns a reference to the istream object used to invoke it.This means you can concatenate other extractions following get(char &).

If cin.get(char &) encounters the end of a file, either real or simulated from the keyboard (Ctrl+Z for DOS and Windows command prompt mode, Ctrl+D at the beginning of a line for Unix), it does not assign a value to its argument.This is quite right because if the program has reached the end of the file, there is no value to be assigned. Furthermore, the method calls setstate(failbit), which causes cin to test as false.



###### The getchar() Member Function

The get(void) member function also reads white space, but it uses its return value to communicate input to a program.

Here cin.get() returns a type int value. Because that return value is not a class object, you can’t apply the membership operator to it.

If you want a program to examine every character, you should use one of the get() methods. For example,a word-counting program could use white space to determine when a word came to an end. Of the two get() methods, the get(char &) method has the classier interface.The main advantage of the get(void) method is that it closely resembles the standard C getchar() function, which means you can convert a C program to a C++ program by including iostream instead of stdio.h, globally replacing getchar() with cin.get(),and globally replacing C’s putchar(ch) with cout.put(ch).



##### String Input: getline(), get(), and ignore()

The getline() member function and the string-reading version of get() both read strings,and both have the same function signatures (here simplified from the more general template declaration):

```c++
istream & get(char *, int, char);
istream & get(char *, int);
istream & getline(char *, int, char);
istream & getline(char *, int);
```



ignore() takes two arguments:a number specifying a maximum number of characters to read and a character that acts as a delimiter character for input.

The prototype provides defaults of 1 and EOF for the two arguments,and the function return type is istream &:

```c++
istream & ignore(int = 1, int = EOF);
```



###### Unexpected String Input

If either method fails to extract any characters, the method places a null character into the input string and uses setstate() to set failbit.

One possibility is if an input method immediately encounters endof-file. For get(char *, int),another possibility is if you enter an empty line:



##### Other istream Methods

read() does not append a null character to input, so it doesn’t convert input to string form.The read() method is not intended for keyboard input. Instead, it is most often used in conjunction with the ostream write() function for file input and output.The method’s return type is istream &.



The peek() function returns the next character from input without extracting from the input stream.That is, it lets you peek at the next character. Suppose you want to read input up to the first newline or period, whichever comes first.You can use peek() to peek at the next character in the input stream in order to judge whether to continue.



The gcount() method returns the number of characters read by the last unformatted extraction method.That means characters read by a get(), getline(), ignore(), or read() method but not by the extraction operator (>>), which formats input to fit particular data types.



The putback() function inserts a character back in the input string.The inserted character then becomes the first character read by the next input statement.The putback() method takes one char argument, which is the character to be inserted,and it returns type istream &, which allows the call to be concatenated with other istream methods. Using peek() is like using get() to read a character and then using putback() to place the character back in the input stream.







### File Input and Output 

#### Simple File I/O

Suppose you want a program to write to a file.You must do the following:

1. Create an ofstream object to manage the output stream. 
2. Associate that object with a particular file. 
3. Use the object the same way you would use cout; the only difference is that output goes to the file instead of to the screen.

```c++
ofstream fout; // create an ofstream object named fout
ofstream fout("jar.txt"); // create fout object, associate it with jar.txt
fout << "Dull Data";//put some words into the file
```



To read a file is similar.

EX:

```c++
// two statements
ifstream fin; // create ifstream object called fin
fin.open("jellyjar.txt"); // open jellyjar.txt for reading
// one statement
ifstream fis("jamjar.txt"); // create fis and associate with jamjar.txt
char ch;
fin >> ch; // read a character from the jellyjar.txt file
char buf[80];
fin >> buf; // read a word from the file
fin.getline(buf, 80); // read a line from the file
string line;
getline(fin, line); // read from a file to a string object
```



The connections with a file are closed automatically when the input and output stream objects expire—for example, when the program terminates.Also you can close a connection with a file explicitly by using the close() method:

```c++
fout.close(); // close output connection to file
fin.close(); // close input connection to file
```





#### Stream Checking and is_open()

The C++ file stream classes inherit a stream-state member from the ios_base class.This member,as discussed earlier, stores information that reflects the stream status:All is well, end-of-file has been reached, I/O operation failed,and so on.

Attempting to open a non-existent file for input sets failbit. So you could check this way:

```c++
fin.open(argv[file]);
if (fin.fail()) // open attempt failed
{
...
}

fin.open(argv[file]);
if (!fin) // open attempt failed
{
...
}

if (!fin.is_open()) // open attempt failed
{
...
}
```



#### Opening Multiple Files

You may plan to process a group of files sequentially



#### Command-Line Processing

Using argv[] as file names



#### File Modes

The file mode describes how a file is to be used: read it, write to it,append it,and so on.

When you associate a stream with a file, either by initializing a file stream object with a filename or by using the open() method, you can provide a second argument that specifies the file mode:

```c++
ifstream fin("banjo", mode1); // constructor with mode argument
ofstream fout();
fout.open("harp", mode2); // open() with mode arguments
```

**File Mode Constants**

<img src="C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200730170146966.png" alt="image-20200730170146966" style="zoom:80%;" />



The prototypes for these class member functions provide default values for the second argument (the file mode argument).

The ifstream open() method and constructor use ios_base::in (open for reading) as the default value for the mode argument,and the ofstream open() method and constructor use ios_base::out | ios_base::trunc (open for writing and truncate the file) as the default. The fstream class doesn’t provide a mode default, so you have to provide a mode explicitly when creating an object of that class.

Using "|" operator if you want to use two or more modes.

<img src="C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200730171248038.png" alt="image-20200730171248038" style="zoom:80%;" />

Unlisted combinations, such as ios_base::in | ios_base::trunc, prevent the file from being opened.The is_open() method detects this failure.



##### Appending to a File



#### Random Access

Random access means moving directly to any location in the file instead of moving through it sequentially.The random access approach is often used with database files.A program will maintain a separate index file, giving the location of data in the main data file.Then it can jump directly to that location, read the data there,and perhaps modify it.

You need a way to move through a file. The fstream class inherits two methods for this: seekg() moves the input pointer to a given file location, and seekp() moves the output pointer to a given file location. You can also use seekg() with an ifstream object and seekp() with an ofstream object. Here are the seekg() prototypes:

```c++
basic_istream<charT,traits>& seekg(off_type, ios_base::seekdir);
basic_istream<charT,traits>& seekg(pos_type);
```

For the char specialization, the two prototypes are equivalent to the following:

```c++
istream & seekg(streamoff, ios_base::seekdir);
istream & seekg(streampos);
```



For the first prototype, values of the streamoff type are used to measure offsets, in bytes, from a particular location in a file. The streamoff argument represents the file position, in bytes, measured as an offset from one of three locations. The seek_dir argument is another integer type that is defined,along with three possible values, in the ios_base class.The constant ios_base::beg means measure the offset from the beginning of the file.The constant ios_base::cur means measure the offset from the current position.The constant ios_base::end means measure the offset from the end of the file.

For the second prototype, a streampos value represents an absolute location in a file, measured from the beginning of the file.You can treat a streampos position as if it measures a file location in bytes from the beginning of a file, with the first byte being byte 0. So the following statement locates the file pointer at byte 112, which would be the 113th byte in the file:

```c++
fin.seekg(112);
```

If you want to check the current position of a file pointer, you can use the tellg() method for input streams and the tellp() methods for output streams. Each returns a streampos value representing the current position, in bytes, measured from the beginning of the file. When you create an fstream object, the input and output pointers move in tandem, so tellg() and tellp() return the same value. But if you use an istream object to manage the input stream and an ostream object to manage the output stream to the same file, the input and output pointers move independently of one another,and tellg() and tellp() can return different values.



```c++
if (finout.eof())
finout.clear(); // clear eof flag
else
{
	cerr << "Error in reading " << file << ".\n";
	exit(EXIT_FAILURE);
}
```

The problem this code addresses is that when the program finishes reading and displaying the entire file, it sets the eofbit element.This convinces the program that it’s finished with the file and disables any further reading of or writing to the file. Using the clear() method resets the stream state, turning off eofbit. Now the program can once again access the file.



##### Working with Temporary Files

 First of all, you need to come up with a naming scheme for your temporary file(s). How can you ensure that each file is assigned a unique name? The tmpnam() standard function declared in cstdio has you covered:

```c++
char* tmpnam( char* pszName );
```

The tmpnam() function creates a temporary name and places it in the C-style string that is pointed to by pszName. The constants L_tmpnam and TMP_MAX, both defined in cstdio, limit the number of characters in the filename and the maximum number of times tmpnam() can be called without generating a duplicate filename in the current directory.

EX:

```c++
#include <cstdio>
#include <iostream>
int main()
{
    using namespace std;
    cout << "This system can generate up to " << TMP_MAX
         << " temporary names of up to " << L_tmpnam
         << " characters.\n";
    char pszName[L_tmpnam] = {'\0'};
    cout << "Here are ten names:\n";
    for (int i = 0; 10 > i; i++)
    {
        tmpnam(pszName);
        cout << pszName << endl;
    }
    return 0;
}
```

More generally, by using tmpnam(), you can now generate TMP_NAM unique filenames with up to L_tmpnam characters per name. 





### Incore Formatting 

he iostream family supports I/O between a program and a terminal.The fstream family uses the same interface to provide I/O between a program and a file.The C++ library also provides an sstream family, which uses the same interface to provide I/O between a program and a string object.

The sstream header file defines an ostringstream class that is derived from the ostream class. (There is also a wostringstream class based on wostream, for wide character sets.) If you create an ostringstream object, you can write information to it, which it stores.You can use the same methods with an ostringstream object that you can with cout.



The formatted text goes into a buffer,and the object uses dynamic memory allocation to expand the buffer size as needed.The ostringstream class has a member function, called str(), that returns a string object initialized to the buffer’s contents:

```c++
string mesg = outstr.str(); // returns string with formatted information
```

EX:

```c++
#include <iostream>
#include <sstream>
#include <string>
int main()
{
    using namespace std;
    ostringstream outstr; // manages a string stream
    string hdisk;
    cout << "What's the name of your hard disk? ";
    getline(cin, hdisk);
    int cap;
    cout << "What's its capacity in GB? ";
    cin >> cap;
    // write formatted information to string stream
    outstr << "The hard disk " << hdisk << " has a capacity of "
           << cap << " gigabytes.\n";
    string result = outstr.str(); // save result
    cout << result;               // show contents
    return 0;
}
```

Sample Output:

```
What's the name of your hard disk? Datarapture
What's its capacity in GB? 2000
The hard disk Datarapture has a capacity of 2000 gigabytes
```



The istringstream class lets you use the istream family of methods to read data from an istringstream object, which can be initialized from a string object.

Suppose facts is a string object.To create an istringstream object associated with this string, you can use the following:

```c++
istringstream instr(facts); // use facts to initialize stream
```

EX:

```c++
#include <iostream>
#include <sstream>
#include <string>
int main()
{
    using namespace std;
    string lit = "It was a dark and stormy day, and "
                 " the full moon glowed brilliantly. ";
    istringstream instr(lit); // use buf for input
    string word;
    while (instr >> word) // read a word a time
        cout << word << endl;
    return 0;
}
```

Sample Output:

```c++
It
was
a
dark
and
stormy
day,
and
the
full
moon
glowed
brilliantly.
```



































## Visiting with the New C++ Standard

### C++11 Features Revisited 

#### New Types

C++11 adds the long long and unsigned long long types to support 64-bit integers (or wider) and the char16_t and char32_t types to support 16-bit and 32-bit character representations, respectively



#### Uniform Initialization

C++11 extends the applicability of the brace-enclosed list (list-initialization) so that it can be used with all built-in types and with user-defined types (that is, class objects).The list can be used either with or without the = sign

##### Narrowing

The initialization-list syntax provides protection against narrowing—that is,against assigning a numeric value to a numeric type not capable of holding that value. Ordinary initialization allows you to do things that may or may not make sense

##### std::initializer_list

The initializer_list header file provides support for this template class.The class has begin() and end() member functions specifying the range of the list.You can use an initializer_list argument for regular functions as well as for constructors



#### Declarations

C++11 implements several features that simplify declarations, particularly for situations arising when templates are used.

##### auto

##### decltype

The decltype keyword creates a variable of the type indicated by an expression.The following statement means “make y the same type as x,”

```c+_+
decltype(x) y;
```



##### Trailing Return Type

C++11 introduces a new syntax for declaring functions, one in which the return type comes after the function name and parameter list instead of before them:

```C++
double f1(double, int); // traditional syntax
auto f2(double, int) -> double; // new syntax, return type is double
```

double f1(double, int); // traditional syntax auto f2(double, int) -> double; // new syntax, return type is double

```C++
template<typename T, typename U)
auto eff(T t, U u) -> decltype(T*U)
{
	...
}
```



##### Template Aliases: using =

It’s handy to be able to create aliases for long or complex type identifiers. C++ already had typedef for that purpose:

```C++
typedef std::vector<std::string>::iterator itType;
```



#### Smart Pointers

####  ……







### Move Semantics and the Rvalue Reference 

#### The Need for Move Semantics

```c++
vector<string> vstr;
// build up a vector of 20,000 strings, each of 1000 characters
...
vector<string> vstr_copy1(vstr); // make vstr_copy1 a copy of vstr
```



Suppose:

```c++
vector<string> allcaps(const vector<string> & vs)
{
	vector<string> temp;
	// code that stores an all-uppercase version of vs in temp
	return temp;
}

vector<string> vstr;
// build up a vector of 20,000 strings, each of 1000 characters
vector<string> vstr_copy1(vstr); // #1
vector<string> vstr_copy2(allcaps(vstr)); // #2
```

Superficially, statements #1 and #2 are similar; each uses an existing object to initialize a new vector object. If we take this code at face value, allcaps() creates a temp object managing 20,000,000 characters, the vector and string copy constructors go through the effort of creating a 20,000,000-character duplicate, then the program deletes the temporary object returned by allcaps(). The main point is that a lot of effort is wasted here. Because the temporary object is deleted, wouldn’t it be better if the compiler could just transfer ownership of the data to vstr_copy2?That is, instead of copying 20,000,000 characters to a new location and then deleting the old location, just leave the characters in place and attach the vstr_copy2 label to them.This would be similar to what happens when you move a file from one directory to another:The actual file stays where it is on the hard drive,and just the bookkeeping is altered. Such an approach is called move semantics