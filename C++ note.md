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



```
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