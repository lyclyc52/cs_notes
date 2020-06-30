## Introduction

Did the output for this program briefly flash onscreen and then disappear? Some windowing environments run the program in a separate window and then automatically close the window when the program finishes. In this case, you can supply extra code to make the window stay open until you strike a key. One way is to add the following line before the return statement: 

 	getchar();  

​                                             

 

The basic strategy in C programming is to use programs that convert your source code file to an executable file, which is a file containing ready-to-run machine language code. C implementations typically do this in two steps: compiling and linking. The compiler converts your source code to an intermediate code, and the linker combines this with other code to produce the executable file. C uses this two-part approach to facilitate the modularization of programs. You can compile individual modules separately and then use the linker to combine the compiled modules later. That way, if you need to change one module, you don’t have to recompile the other ones. Also, the linker combines your program with precompiled library code.

 

​                             ![image-20200610221657877](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200610221657877.png)  

startup code: code that acts as an interface between your program and the operating system.

 

The role of the linker is to bring together these three elements—your object code, the standard startup code for your system, and the library code.

 

In short, an object file and an executable file both consist of machine language instructions. However, the object file contains the machine language translation only for the code you used, but the executable file also has machine code for the library routines you use and for the startup code. 

 

 

GNU Project: GNU Compiler Collection, or GCC, which includes the GCC C compiler.

The GCC C compiler can be invoked with the gcc command. And many systems using gcc will make cc an alias for gcc . 

 

LLVM Project: Its Clang compiler processes C code and can be invoked as clang .

 

C compilers are not part of the standard Windows package, so you may need to obtain and install a C compiler. Cygwin and MinGW are free downloads that make the GCC compiler available for command-line use on a PC.

 

Windows-based integrated development environments, or IDEs

  

The #include statement is an example of a C preprocessor directive

 

The first line passes the phrase I am a simple to the printf() function. Such information is called the argument or, more fully, the actual argument of a function (see F igure  2.3  ).

![image-20200610221802969](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200610221802969.png) 

 

 

 

## Data and C 

### scanf();

The scanf() function provides keyboard input to the program. The %f instructs scanf() to read a floating-point number from the keyboard, and the &weight tells scanf() to 

assign the input value to the variable named weight . The scanf() function uses the & notation to indicate where it can find the weight variable. The next chapter discusses & further; meanwhile, trust us that you need it here.  

 

3.Data type keyword:

![image-20200610222132766](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200610222132766.png)

 

A word is the natural unit of memory for a given computer design. For 8-bit microcomputers, such as the original Apples, a word is just 8 bits. Since then, personal computers moved up to 16-bit words, 32-bit words, and, at the present, 64-bit words. Larger word sizes enable faster transfer of data and allow more memory to be accessed.  

 

### number

A prefix of 0x or 0X (zero-ex) means that you are specifying a hexadecimal value

To display an integer in octal notation, use %o. To display an integer in hexadecimal,

use %x .

you can use specifiers %#o , %#x , and %#X to generate the 0 , 0x , and 0X prefixes respectively.

 

 

■ The type short int or, more briefly, short may use less storage than int , thus saving space when only small numbers are needed. Like int , short is a signed type.  

■  The type long int , or long , may use more storage than int , thus enabling you to express larger integer values. Like int , long is a signed type.    

■  The type long long int , or long long (introduced in the C99 standard), may use more storage than long . At the minimum, it must use at least 64 bits. Like int , long long is a signed type.   

■  The type unsigned int , or unsigned , is used for variables that have only nonnegative values. This type shifts the range of numbers that can be stored. For example, a 16-bit unsigned int allows a range from 0 to 65535 in value instead of from –32768 to 32767 . The bit used to indicate the sign of signed numbers now becomes another binary digit, allowing the larger number.   

■  The types unsigned long int , or unsigned long , and unsigned short int , or unsigned short , are recognized as valid by the C90 standard. To this list, C99 adds unsigned long long int , or unsigned long long .   

■  The keyword signed can be used with any of the signed types to make your intent explicit. For example, short , short int , signed short , and signed short int are all names for the same type.

 

​                                   

Notation to print different number type(better in lowercase)

| unsigned int               | %u           |
| -------------------------- | ------------ |
| long in decimal format     | %ld          |
| long in octal format       | %lo          |
| long in hexadecimal format | %lx          |
| shot                       | %h(d、o、x)  |
| unsigned long              | %lu          |
| long long                  | %lld or %llu |
| int                        | %d           |

 

%#x:带格式的16位输出(前面有0x)

 

using suffix(后缀) to claim data type:

e.g. 1l or 1L represent 1 is long type

​       1ll represent 1 is long long

​       1ul represent 1 is unsigned long

 

When the specifier does not match the variable, the result will have some problems. 

e.g. If using “%hd” to call int, it will just print the first 16 bits.



That’s because C automatically expands a type short value to a type int value when it’s passed as an argument to a function.

 



### character: using char

For the nonprinting characters(such as backspacing or going to the next line or making the 

terminal bell ring), three ways to represent:

1)   ASCII code

2)   special symbol sequences

​    

A backspace ( \b ) moves the active position back one space on the current line. A form feed character ( \f ) advances the active position to the start of the next page. A newline character ( \n ) sets the active position to the beginning of the next line. A carriage return ( \r ) moves the active position to the beginning of the current line. A horizontal tab character ( \t ) moves the active position to the next horizontal tab stop (typically, these are found at character positions 1, 9, 17, 25, and so on). A vertical tab ( \v ) moves the active position to the next vertical tab position.

 

print char: %c



 

### portable type: stdint.h and inttypes.h

the same type name doesn’t necessarily mean the same thing on different systems. It would be nice if C had types that had the same meaning regardless of the system. 

What C has done is create more names for the existing types. The trick is to define these new names in a header file called stdint.h. For example, int32_t represents the type for a 32-bit signed integer.

The alternative names we just discussed are examples of *exact-width integer types* (精确宽度的整数类型)

If the smallest type on a particular system were 16 bits, the int8_t type would not be defined. However, the int_least8_t type would be available, perhaps implemented as a 16-bit integer.

 

Of course, some programmers are more concerned with speed than with space. For them, 

C99 and C11 define a set of types that will allow the fastest computations. These are called 

The *fastest minimum width* types. For example, the int_fast8_t will be defined as an alternative

name for the integer type on your system that allows the fastest calculations for 8-bit signed

values.

 

Finally, for some programmers, only the biggest possible integer type on a system will do;

intmax_t stands for that type, a type that can hold any valid signed integer value.



 

### double, float and long double

The C standard provides that a float has to be able to represent at least six significant

figures and allow a range of at least e–37 to e+37 .

 

Often, systems use 32 bits to store a floating-point number. Eight bits are used to give the 

exponent its value and sign, and 24 bits are used to represent the nonexponent part, called

the mantissa or  significand , and its sign.

 

double representations use 64 bits instead of 32

 

Here are some more valid floating point constants: 

 3.14159 .2 4e16 .8E-5 100.

 

 

C enables you to override this default by using an f or F suffix to make the compiler treat a floating-point constant as type float ; examples are 2.3f and 9.11E9F . An l or L suffix makes a number type long double ; examples are 54.3l and 4.32e4L

 

C allows for a third floating-point type: long double . The intent is to provide for even more

precision than double . However, C guarantees only that long double is at least as precise as

double .

 

Since C99, C has a new format for expressing floating-point constants. It uses a hexadecimal prefix ( 0x or 0X ) with hexadecimal digits, a p or P instead of e or E , and an exponent that is a power of 2 instead of a power of 10. Here’s what such a number might look like: 

 0xa.1fp10 

The a is 10 in hex, the .1f is 1/16th plus 15/256 th ( f is 15 in hex), and the p10 is 2 10 , or 1024, making the complete value (10 + 1/16 + 15/256) x 1024, or 10364.0 in base 10 notation. 

 

to print them:

| decimal float and double | %f                    |
| ------------------------ | --------------------- |
| long double              | %Lf ,   %Le , and %La |
| hex float and double     | %a                    |

 

Floating-Point Overflow and Underflow

For overflow, C specifies that the variable gets assigned a special value that stands for infinity and that printf() displays either inf or infinity (or some variation on that theme) for the value.

For underflow, the computer moves the bits in the mantissa over, vacating the first position and losing the last binary digit. An analogy would be taking a base 10 value with four significant digits, such as 0.1234E-10, dividing by 10, and getting 0.0123E-10.

 

Floating-Point Round-off Errors

e.g. b = 2.0e20 + 1.0;   

a = b - 2.0e20;   

printf("%f \n", a);

output is not 1. The reason for these odd results is that the computer doesn’t keep track of enough decimal places to do the operation correctly. The number 2.0e20 is 2 followed by 20 zeros and, by adding 1 at the 21st digit. A float number is typically just six or seven digits scaled to bigger or smaller numbers with an exponent.

 

 

### complex(复数) and imaginary type(虚数)

three complex type: float _Complex , double _Complex , and long double _Complex .

three imaginary type: float _Imaginary , double _Imaginary , and long double _Imaginary . 

 

Including the complex.h header file lets you substitute the word complex for _Complex and the word imaginary for _Imaginary 

Use “I” to represent the square root of -1

 

 

### type size

sizeof() to give the type in bytes.  %zd specifier for this type

 



### using data type

When you initialize a variable of one numeric type to a value of a different type, C converts the value to match the variable. This means you may lose some data.

e.g. int cost=12.99;//cost=12

 

When using backspace, the cursor(光标) will move and if you enter something, those you print before will be replaced.

 

### flushing and output 

(Sending the output from the buffer to the screen or file is called flushing the buffer)

printf() statements send output to an intermediate storage area called a buffer . Every now and then, the material in the buffer is sent to the screen. The standard C rules for when output is sent from the buffer to the screen are clear: It is sent when the buffer gets full, when a newline character is encountered, or when there is impending input.

 



#### key concept

C does allow you to write an expression with mixed data types, but it will make automatic conversions so that the actual calculation uses just one data type. 

  

 

### some tips in exercise

1)there must be some number before e10

2)%f:浮点类型输出

 %e:指数类型输出

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

## Character Strings and Formatted Input/ Output

 

### Type char Arrays and the Null Character

C has no special variable type for strings. Instead, strings are stored in an array of type char .

 

The character \0 in the last array position. This is the null character , and C uses it to mark the end of a string. The null character is not the digit zero; it is the nonprinting character whose ASCII code value (or equivalent) is 0

 

specifier:%s

define:char variable[\some number]

 

After scanf() starts to read input, it stops reading at the first whitespace (blank, tab, or newline) it encounters.





### constant

claim: #define <constant-valve>

usually use capital form as a constant name

Other, less common, naming conventions include prefixing a name with a c_ or k_ to indicate a constant, producing names such as c_level or k_line . 

 

#### The const Modifier 

C90 added a second way to create symbolic constants—using the const keyword to convert a declaration for a variable into a declaration for a constant: 

const int MONTHS = 12;  // MONTHS a symbolic constant for 12  

 

#### Manifest Constants

The C header files limits.h and float.h supply detailed information about the size limits of integer types and floating types, respectively. Each file defines a series of manifest constants that apply to your implementation.

 

 

### printf() function

We have used the %d notation when printing an integer and the %c notation when printing a character. These notations are called conversion specifications because they specify how the data is to be converted into displayable form.

 ![image-20200610224353768](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200610224353768.png)

 ![image-20200610224400807](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200610224400807.png)

 

Conversion Specification Modifiers for printf() :

You can modify a basic conversion specification by inserting modifiers between the % and the defining conversion character.

 <img src="C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200610224644291.png" alt="image-20200610224644291" style="zoom:100%;" />

​     ![image-20200610224705132](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200610224705132.png)   

 ![image-20200610224711573](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200610224711573.png)



For digits: 代表全部的位数（包括小数）

如果实际位数小于设置位数，以实际位数为准 

 

size_t value is suitable for every system. But actually it is an int, long or long long int according to different systems.   

![image-20200610224741295](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200610224741295.png)

![image-20200610224754796](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200610224754796.png)

e.g.

```c#
/* width.c -- field widths */  
#include <stdio.h>  #define PAGES 959  
int main(void) 
{      
	printf("*%d*\n", PAGES);      
	printf("*%2d*\n", PAGES);      
	printf("*%10d*\n", PAGES);      
	printf("*%-10d*\n", PAGES);        
	return 0;  
} 

```



Listing 4.7prints the same quantity four times using four different conversion specifications. It uses an asterisk ( * ) to show you where each field begins and ends. The output looks as follows: 

\*959* 

\*959* 

\*    959* 

*959    * 

The second conversion specification is %2d . This should produce a field width of 2, but because the integer is three digits long, the field is expanded automatically to fit the number.

 

2)Listing 4.10  The stringf.c Program 

```c#
 /* stringf.c -- string formatting */ 

#include <stdio.h> 
#define BLURB "Authentic imitation!" 
int main(void) 
{   
	printf("[%2s]\n", BLURB);   
	printf("[%24s]\n", BLURB);   
	printf("[%24.5s]\n", BLURB);   
	printf("[%-24.5s]\n", BLURB);    
	return 0; 
}  
```

Here is the output: 

[Authentic imitation!] 

[  Authentic imitation!] 

[                   Authe] 

[Authe                   ] 

 

3) Listing 4.12  The floatcnv.c Program 

```c#
 /* floatcnv.c -- mismatched floating-point conversions */ 

\#include <stdio.h> 
int main(void) 
{   
	float n1 = 3.0;   
	double n2 = 3.0;   
	long n3 = 2000000000;   
	long n4 = 1234567890;    
	printf("%.1e %.1e %.1e %.1e\n", n1, n2, n3, n4);   
	printf("%ld %ld\n", n3, n4);   
	printf("%ld %ld %ld %ld\n", n1, n2, n3, n4);    
	return 0; 
}  
```

On one system, Listing  4.12  produces the following output: 

 3.0e+00 3.0e+00 3.1e+46 1.7e+266 

2000000000 1234567890 

0 1074266112 0 1074266112  

The output of the third line is wrong. Here is the reason.

**Passing Arguments** 

The mechanics of argument passing depend on the implementation. This is how argument passing works on one system. The function call looks as follows: 

 printf("%ld %ld %ld %ld\n", n1, n2, n3, n4);  

This call tells the computer to hand over the values of the variables n1 , n2 , n3 , and n4 to the computer. Here’s one common way that’s accomplished. The program places the values in an area of memory called the stack(栈) . When the computer puts these values on the stack, it is guided by the types of the variables, not by the conversion specifiers. Consequently, for n1 , it places 8 bytes on the stack ( float is converted to double ). Similarly, it places 8 more bytes for n2 , followed by 4 bytes each for n3 and n4 . Then control shifts to the printf() function. This function reads the values off the stack but, when it does so, it reads them according to the conversion specifiers. The %ld specifier indicates that printf() should read 4 bytes, so 

 printf() reads the first 4 bytes in the stack as its first value. This is just the first half of n1 , and it is interpreted as a long integer. The next %ld specifier reads 4 more bytes; this is just the second half of n1 and is interpreted as a second long integer (see F igure  4.9  ). Similarly, the third and fourth instances of %ld cause the first and second halves of n2 to be read and to be interpreted as two more long integers, so although we have the correct specifiers for n3 and n4 ,  printf() is reading the wrong bytes.

 

 

### The Return Value of printf() 

The printf() function also has a return value; it returns the number of characters it printed. If there is an output error, printf() returns a negative value.

Listing 4.13  The prntval.c Program 

```c#
 /* prntval.c -- finding printf()'s return value */ 
#include <stdio.h> 
int main(void) 
{   
	int bph2o = 212;   
	int rv;    
	rv = printf("%d F is water's boiling point.\n", bph2o);   
	printf("The printf() function printed %d characters.\n", rv);   
	return 0; 
}  
```

The output is as follows: 

 212 F is water's boiling point. The printf() function printed 32 characters.  

First, the program used the form rv = printf(...); to assign the return value to rv . This statement therefore performs two tasks: printing information and assigning a value to a variable. Second, note that the count includes all the printed characters, including the spaces and the unseen newline character.

The following three forms are equivalent: 

printf("Hello, young lovers, wherever you are."); 

printf("Hello, young "  "lovers" ", wherever you are."); 

printf("Hello, young lovers"     ", wherever you are.");  

 

 

###  scanf() function

 ![image-20200610230507644](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200610230507644.png)

​    ![image-20200610230520831](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200610230520831.png)



![image-20200610230556342](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200610230556342.png)

![image-20200610230606297](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200610230606297.png)

how it works:

The scanf() function begins reading input a character at a time. It skips over whitespace characters (spaces, tabs, and newlines) until it finds a non-whitespace character. If it finds a digit or a sign, it saves that character and then reads the next character. If that is a digit, it saves the digit and reads the next character. scanf() continues reading and saving characters until it encounters a nondigit. It then concludes that it has reached the end of the integer.

 

 

### key concept

To represent a sequence of characters, C uses the character string.

Except when in the %c mode (which reads just the next character), scanf() skips over

whitespace characters to the first non-whitespace character when reading input. It then keeps reading characters either until encountering whitespace or until encountering a character that doesn’t fit the type being read.





### problem

%输出：%%

\41：表示八进制的41的ASCII

 

 







 

## Operators, Expressions, and Statements

### Loops

data object: a general term for a region of data storage that can be used to hold values

 

lvalue: any such name or expression that identifies a particular data object

And C added the term modifiable lvalue to identify an object whose value can be changed.

Therefore, the left side of an assignment operator should be a modifiable lvalue.

 

rvalue: can be constants, variables, or any other expression that yields a value, such as a function call. Indeed, the current standard uses value of an expression instead of

rvalue .

 

Operands: what operators operate on

 

 

### operator

7\. represents 7 in float type

truncation: any fraction resulting from integer division is discarded. 



sizeof operator: returns the size, in bytes, of its operand

 

size_t Type: C says that **sizeof** returns a value of type size_t . This is an unsigned integer type, but not a brand-new type. C99 goes a step further and supplies %zd as a printf() specifier for displaying a size_t value. If your system doesn’t implement %zd , you can try using %u or %lu instead.

 

```c#
int num=5;

printf("%10d %10d\n", num, num*num++);
```

it might evaluate the last argument first and increment num before getting to the other argument. it may print    6  25

It even might work from right to left, using 5 for the rightmost num and 6 for the next two So the output is  6 30

 

```c#
int ans = num/2 + 5*(1 + num++);
```

Again, the problem is that the compiler may not do things in the same order you have in

mind. You would think that it would find num/2 first and then move on, but it might do the

last term first, increase num , and use the new value in num/2 . There is no guarantee.

 

 

 

### Expressions and Statements

An expression consists of a combination of operators and operands

Every Expression Has a Value

 

Statements are the primary building blocks of a program. A program is a series of statements with some necessary punctuation. A statement is a complete instruction to the computer.

```c#
int count, sum; /* declaration statement */

count = 0; /* assignment statement */
```

 

#### Side Effects(副作用) and Sequence Points(序列点):

A side effect is the modification of a data object or file.

A sequence point is a point in program execution at which all side effects are evaluated before going on to the next step. In C, the semicolon in a statement marks a sequence point. That means all changes made by assignment operators, increment operators, and decrement operators in a statement must take place before a program proceeds to the next statement. Some operators that we’ll discuss in later chapters have sequence points.

A compound statement is two or more statements grouped together by enclosing them in braces; it is also called a block .

 

### type conversion

#### basic rules:

1.When appearing in an expression, char and short , both signed and unsigned , are automatically converted to int or, if necessary, to unsigned int . (If short is the same size as int , unsigned short is larger than int ; in that case, unsigned short is converted to unsigned int .)

2.In any operation involving two types, both values are converted to the higher ranking of the two types.

3.The ranking of types, from highest to lowest, is long double , double , float , unsignedlong long , long long , unsigned long , long , unsigned int , and int . One possible exception is when long and int are the same size, in which case unsigned intoutranks long . The short and char types don’t appear in this list because they would have been already promoted to int or perhaps unsigned int .

 4.In an assignment statement(赋值), the final result of the calculations is converted to the type of the variable being assigned a value. This process can result in promotion, as described in rule 1, or demotion

5.When passed as function arguments, char and short are converted to int , and float is converted to double . This automatic promotion is overridden by function prototyping, as discussed in Chapter 9 , “Functions.”



the rules for when the assigned value doesn’t fit into the destination type:

1.When the destination is some form of unsigned integer and the assigned value is an integer, the extra bits that make the value too big are ignored.

2.If the destination type is a signed integer and the assigned value is an integer, the result is implementation-dependent.

3.If the destination type is an integer and the assigned value is floating point, the behavior

is undefined.

 

#### Cast Operator

It is possible for you to demand the precise type conversion that you want or else document that you know you’re making a type conversion. 

The parentheses and type name together constitute a cast operator. This is the general form of a cast operator: 

( <data type>)

Consider the next two code lines, in which mice is an int variable. The second line contains two casts to type int . 

```c#
 mice = 1.6 + 1.7;
 mice = (int) 1.6 + (int) 1.7; 
```

The first example uses automatic conversion. First, 1.6 and 1.7 are added to yield 3.3. This number is then converted through truncation to the integer 3 to match the int variable. In the second example, 1.6 is converted to an integer ( 1) before addition, as is 1.7, so that mice is assigned the value 1+1, or 2.

 

### Function with Arguments 



### Tips in Problem

1. int/int 只能是int，float需要1.0/int















## C Control Statement: Loop

### The Comma Operator

The comma operator is not restricted to for loops, but that’s where it is most often used. The operator has two further properties. 

First, it guarantees that the expressions it separates are evaluated in a left-to-right order. (In other words, the comma is a sequence point, so all side effects to the left of the comma take place before the program moves to the right of the comma.) 

For example:

```c#
ounces++, cost = ounces * FIRST_OZ 
```

This would increment ounces and then use the new value for ounces in the second subexpression.



Second, the value of the whole comma expression is the value of the right-hand member. The effect of the statement

```c#
x = (y = 3, (z = ++y + 2) + 5); 
```

is to first assign 3 to y, increment y to 4, and then add 2 to 4 and assign the resulting value of 6 to z, next add 5 to z, and finally assign the resulting value of 11 to x. 

```c#
 houseprice = 249,500; 
```

This is not a syntax error. Instead, C interprets this as a comma expression, with houseprice = 249 being the left subexpression and 500 the right subexpression. C interprets this as a comma expression, with houseprice = 249 being the left subexpression and 500 the right subexpression. Therefore, the value of the whole comma expression is the value of the right-hand expression, and the left substatement assigns the value 249 to the houseprice variable. Therefore, the effect is the same as the following code: 

```c#
houseprice = 249;
500; 
```

Remember that any expression becomes a statement with the addition of a semicolon, so 500; is a statement that does nothing. 

On the other hand, the statement 

```c#
houseprice = (249,500); 
```

assigns 500, the value of the right subexpression, to houseprice . 





### Arrays

(comp2011)

















## C Control Statement: Branching and Jumps

### *if*  Statement

(comp2011)



### *getchar()* and *putchar()*

The getchar() function takes no arguments, and it returns the next character from input. (similar to scanf())

The putchar() function prints its argument.(similar to printf())



```c#
 while ((ch = getchar()) != '\n')
```

Assign ch first, and then compare ch with '/n'. All the parentheses are necessary.

the content of putchar() will put in the buffer and put in the terminial until getchar() encounter '\n'.





### The ctype.h Family of Character Functions

The ctype.h Character-Testing Functions

| Name True  | If the Argument Is                                           |
| ---------- | :----------------------------------------------------------- |
| isalnum()  | Alphanumeric (alphabetic or numeric)                         |
| isalpha()  | Alphabetic                                                   |
| isblank()  | A standard blank character (space, horizontal tab, or newline) or any additional locale-specific character so specified |
| iscntrl()  | A control character, such as Ctrl+B                          |
| isdigit()  | A digit                                                      |
| isgraph()  | Any printing character other than a space                    |
| islower()  | A lowercase character                                        |
| isprint()  | A printing character                                         |
| ispunct()  | A punctuation character (any printing character other than a space or an alphanumeric character) |
| isspace()  | A whitespace character (a space, newline, formfeed, carriage return, vertical tab, horizontal tab, or, possibly, other locale-defined character) |
| isupper()  | An uppercase character                                       |
| isxdigit() | A hexadecimal-digit character                                |

​	

The ctype.h Character-Mapping Functions 

| Name      | Action                                                       |
| --------- | ------------------------------------------------------------ |
| tolower() | If the argument is an uppercase character, this function returns the lowercase version; otherwise, it just returns the original argument. |
| toupper() | If the argument is a lowercase character, this function returns the uppercase version; otherwise, it just returns the original argument. |





### Logic

#### Alternate Spellings: The iso646.h Header File C

 If you use this header file, you can use and instead of &&, or instead of ||, and not instead of

<img src="C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200612120806404.png" alt="image-20200612120806404" style="zoom:67%;" />



####  Precedence 

The && operator has higher precedence than ||, and both rank below the relational operators and above assignment in precedence. 



### The Conditional Operator: ?



### Multiple Choice: switch and break 



### The *goto* Statement T

The goto statement has two parts—the goto and a label name. The label is named following the same convention used in naming a variable, as in this example: 

```c#
goto part2; 
```

For the preceding statement to work, the function must contain another statement bearing the part2 label. This is done by beginning a statement with the label name followed by a colon: 

```c#
part2: printf("Refined analysis:\n"); 
```

#### Avoiding *goto* 





























## Character Input/Output and Input Validation

###  Buffers 

The immediate echoing of input characters is an instance of unbuffered (or direct) input, meaning that the characters you type are immediately made available to the waiting program. 

The delayed echoing, on the other hand, illustrates buffered input, in which the characters you type are collected and stored in an area of temporary storage called a buffer. Pressing Enter causes the block of characters you typed to be made available to your program. 

Why have buffers? First, it is less time-consuming to transmit several characters as a block than to send them one by one. Second, if you mistype, you can use your keyboard correction features to fix your mistake. When you finally press Enter, you can transmit the corrected version

 Many compilers for IBM PC compatibles, for example, supply a special family of functions, supported by the conio.h header file, for unbuffered input. These functions include getche() for echoed unbuffered input and getch() for unechoed unbuffered input. ( Echoed input means the character you type shows onscreen, and unechoed input means the keystrokes don’t show.)

Unix systems use a different approach, for Unix itself controls buffering. With Unix, you use the ioctl() function (part of the Unix library but not part of standard C) to specify the type of input you want, and getchar() behaves accordingly. 



### Terminating Keyboard Input 

The echo.c program halts when # is entered, which is convenient as long as you exclude that character from normal input.

#### Files, Streams, and Keyboard Input 

On one level, it can deal with files by using the basic file tools of the host operating system. This is called low-level I/O. 

However, C also deals with files on a second level called the standard I/O package. This involves creating a standard model and a standard set of I/O functions for dealing with files. At this higher level, differences between systems are handled by specific C implementations so that you deal with a uniform interface. 



Conceptually, the C program deals with a stream instead of directly with a file. A stream is an idealized flow of data to which the actual input or output is mapped. 

Keyboard input is represented by a stream called stdin, and output to the screen (or teletype or other output device) is represented by a stream called stdout. 



#### The End of File 

One method to detect the end of a file is to place a special character in the file to mark the end, for example, in CP/M, IBM-DOS, and MS-DOS text files. Today, these operating systems may use an embedded Ctrl+Z character to mark the ends of files.

A second approach is for the operating system to store information on the size of the file. 

C handles this variety of methods by having the getchar() function return a special value when the end of a file is reached, regardless of how the operating system actually detects the end of file. The name given to this value is EOF (end of file). Therefore, the return value for getchar() when it detects an end of file is EOF. The scanf() function also returns EOF on detecting the end of a file. Typically, EOF is defined in the stdio.h file as follows: #define EOF (-1) 

The fact that getchar() is type int is why some compilers warn of possible data loss if you assign the getchar() return value to a type char variable. 

To use this program on keyboard input, you need a way to type the EOF character. No, you can’t just type the letters E O F, and you can’t just type –1. (Typing -1 would transmit two characters: a hyphen and the digit 1.) Instead, you have to find out what your system requires. On most Unix and Linux systems, for example, pressing Ctrl+D at the beginning of a line causes the end-of-file signal to be transmitted. Many microcomputing systems recognize Ctrl+Z at the beginning of a line as an end-of-file signal; some interpret a Ctrl+Z anywhere as an end-of-file signal. 

#### Simulated EOF and Graphical Interfaces 

The concept of simulated EOF arose in a command-line environment using a text interface. In such an environment, the user interacts with a program through keystrokes, and the operating system generates the EOF signal. 

Some practices don’t translate particularly well to graphical interfaces



### Redirection and Files

There are two ways to get a program to work with files. One way is to explicitly use special functions that open files, close files, read files, write in files, and so forth. The second way is to use a program designed to work with a keyboard and screen, but to redirect input and output along different channels—to and from files, for example. In other words, you reassign the stdin stream to a file. This approach (redirection) is more limited in some respects than the first, but it is much simpler to use, and it allows you to gain familiarity with common file-processing techniques. 

#### Redirecting Input

Suppose you have compiled the echo_eof.c program and placed the executable version in a file called echo_eof (or echo_eof.exe on a Windows system). To run the program, type the executable file’s name: 

*echo_eof* 

A text file is one containing text—that is, data stored as human-readable characters. It could be an essay or a program in C, for example. A file containing machine language instructions, such as the file holding the executable version of a program, is not a text file. Because the program works with characters, it should be used with text files. All you need to do is enter this command instead of the previous one: 

*echo_eof < words*

The < symbol is a Unix and Linux and DOS/Windows redirection operator.  It causes the words file to be associated with the stdin stream, channeling the file contents into the echo_eof program. 

#### Redirecting Output

Now suppose you want to have echo_eof send your keyboard input to a file called mywords . Then you can enter the following and begin typing: 

*echo_eof > mywords*

#### Combined Redirection

Now suppose you want to make a copy of the file mywords and call it savewords. Just issue this next command, 

*echo_eof < mywords > savewords* 

and the deed is done. The following command would have worked as well, because the order of redirection operations doesn’t matter: 

*echo_eof > savewords < mywords* 



### Creating a Friendlier User Interface 

#### Working with Buffered Input 

Buffered input is often a convenience to the user, providing an opportunity to edit input before sending it on to a program, but it can be bothersome to the programmer when character input is used. The problem is that buffered input requires you to press the Enter key to transmit your input. This act also transmits a newline character that the program must handle. 

For example:

```c#
/* guess.c -- an inefficient and faulty number-guesser */
 #include <stdio.h>
 int main(void)
 {
 	int guess = 1;
 	printf("Pick an integer from 1 to 100. I will try to guess ");
 	printf("it.\nRespond with a y if my guess is right and with");
 	printf("\nan n if it is wrong.\n");
 	printf("Uh...is your number %d?\n", guess);
 	while (getchar() != 'y') /* get response, compare to y */
 		printf("Well, then, is it %d?\n", ++guess);
 	printf("I knew I could do it!\n");
 	return 0;
 } 
```

getchar() will get 'n' or 'y' and a '\n' so the output is like this:

*Pick an integer from 1 to 100.* 

*I will try to guess it.* 

*Respond with a y if my guess is right and with an n if it is wrong.* 

*Uh...is your number 1?* 

*n* 

*Well, then, is it 2?*

*Well, then, is it 3?* 

*y* 

*I knew I could do it!* 



#### Mixing Numeric and Character Input 

Suppose your program requires both character input using getchar() and numeric input using scanf(). Each of these functions does its job well, but the two don’t mix together well. That’s because getchar() reads every character, including spaces, tabs, and newlines, whereas scanf(), when reading numbers, skips over spaces, tabs, and newlines. 

For example:

```c#
#include <stdio.h>
 void display(char cr, int lines, int width);
 int main(void)
 {
 	int ch; /* character to be printed */
 	int rows, cols; /* number of rows and columns */
 	printf("Enter a character and two integers:\n");
 	while ((ch = getchar()) != '\n')
 	{
 		scanf("%d %d", &rows, &cols);
 		display(ch, rows, cols);
 		printf("Enter another character and two integers;\n");
 		printf("Enter a newline to quit.\n");
 	}
 	printf("Bye.\n");
 	return 0;
 }
```

After typing ch and two int, you will use Enter. But the next loop will read this Enter.



### Menu Browsing

Many computer programs use menus as part of the user interface. 

Modern applications typically use graphical interfaces—buttons to click, boxes to check, icons to touch—instead of the command-line approach of our examples, but the general process remains much the same: Offer the user choices, detect and act upon the user’s response, and protect against possible misuse.



























## Function

### Reveiwing Functions

#### The Black-Box Viewpoint 

The fact that ch, num, and count are local variables private to the show_n_char() function is an essential aspect of the black box approach. If you were to use variables with the same names in main(), they would be separate, independent variables. That is, if main() had a count variable, changing its value wouldn’t change the value of count in show_n_char(), and vice versa. 

#### Prototyping a Function with Arguments 

We used an ANSI C prototype to declare the function before it is used: 

void show_n_char(char ch, int num); 

When a function takes arguments, the prototype indicates their number and type by using a comma-separated list of the types. If you like, you can omit variable names in the prototype: 

void show_n_char(char, int); 

Using variable names in a prototype doesn’t actually create variables. It merely clarifies the fact that char means a char variable, and so on. Again, ANSI C also recognizes the older form of declaring a function, which is without an argument list: 

void show_n_char(); 



### ANSI C Function Prototyping T



### Recursion

#### Pros and Cons 

One good point is that recursion offers the simplest solution to some programming problems. One bad point is that some recursive algorithms can rapidly exhaust a computer’s memory resources. Also, recursion can be difficult to document and maintain. 



### Compiling Programs with Two or More Source Code Files



### Finding Addresses: The & Operator

The unary & operator gives you the address where a variable is stored. 

%p is used in printf() to print address.



### Pointers: A First Look 















## Array and Pointer

### Array

#### Using const with Arrays 

Sometimes you might use an array that’s intended to be a read-only array. That is, the program will retrieve values from the array, but it won’t try to write new values into the array.

e.g.  const int days[MONTHS] = {31,28,31,30,31,30,31,31,30,31,30,31}; 

What if you fail to initialize an array? 

The compiler is allowed to just use whatever values were already present at those memory locations, which is why your results may vary from these. 



#### Designated Initializers (C99) 

This feature allows you to pick and choose which elements are initialized. Suppose, for example, that you just want to initialize the last element in an array. With traditional C initialization syntax, you also have to initialize every element preceding the last one: 

int arr[6] = {0,0,0,0,0,212}; // traditional syntax

With C99, you can use an index in brackets in the initialization list to specify a particular element: 

int arr[6] = {[5] = 212}; // initialize arr[5] to 212 

As with regular initialization, after you initialize at least one element, the uninitialized elements are set to 0. 

For example:

```c#
 #include <stdio.h>
 #define MONTHS 12
 int main(void)
 {
    int days[MONTHS] = {31,28, [4] = 31,30,31, [1] = 29};
 	int i;
 	return 0;
 } 
```

 In the sequence [4] = 31,30,31, these further values are used to initialize the subsequent elements. The start of the initialization list initializes days[1] to 28, but that is overridden by the [1] = 29 designated initialization later. 

#### Array Bounds

The compiler doesn’t check to see whether the indices are valid.

You might wonder why C allows nasty things like that to happen. It goes back to the C philosophy of trusting the programmer. Not checking bounds allows a C program to run faster. The compiler can’t necessarily catch all index errors because the value of an index might not be determined until after the resulting program begins execution. Therefore, to be safe, the compiler would have to add extra code to check the value of each index during runtime, and that would slow things down. 



### Multidimensional Arrays 



### Pointers and Arrays 

An array name is also the address of the first element of the array. That is, if flizny is an array, the following is true: 

flizny == &flizny[0]; // name of array is the address of the first element 

Because prototypes allow you to omit a name, all four of the following prototypes are equivalent: 

int sum(int *ar, int n); 

int sum(int *, int); 

int sum(int ar[], int n); 

int sum(int [], int); 



### Pointer Operations 

**Adding an integer to a pointer**  You can use the + operator to add an integer to a pointer or a pointer to an integer. In either case, the integer is multiplied by the number of bytes in the pointed-to type, and the result is added to the original address. This makes ptr1 + 4 the same as &urn[4]. 

**Incrementing a pointer**  Incrementing a pointer to an array element makes it move to the next element of the array. Therefore, ptr1++ increases the numerical value of ptr1 by 4 (4 bytes per int on our system) and makes ptr1 point to urn[1].

 **Differencing**  You can find the difference between two pointers.  For example, in the output from Listing 10.13 , ptr2 - ptr1 has the value 2, meaning that these pointers point to objects separated by two ints, not by 2 bytes. 

**Comparisons**  You can use the relational operators to compare the values of two pointers, provided the pointers are of the same type. 

#### Dereferencing an Uninitialized Pointer

 Do not dereference an uninitialized pointer.

```c#
int * pt; // an uninitialized pointer
*pt = 5; // a terrible error 
```

The second line means store the value 5 in the location to which pt points. But pt, being uninitialized, has a random value, so there is no knowing where the 5 will be placed.



### Protecting Array Contents 

Arrays in functions are always passed by reference.

#### Using const with Formal Parameters 



### Pointers and Multidimensional Arrays 

 int zippo[4][2\];

Because both the integer and the array of two integers begin at the same location, both zippo and zippo[0] have the same numeric value.



#### C const and C++ const

C and C++ use const similarly, but not identically. One difference is that C++ allows using a const integer value to declare an array size and C is more restrictive. Another is that C++ has stricter rules about pointer assignments: 

```c#
 const int y;
 const int * p2 = &y;
 int * p1;
 p1 = p2; // error in C++, possible warning in C 
```



### Variable-Length Arrays (VLAs) 

If you really want to create a single function that will work with any size two-dimensional array, you can, but it’s awkward to do. (You have to pass the array as a one-dimensional array and have the function calculate where each row starts.) 

This need was the primary impulse for C99 introducing variable-length arrays, which allow you to use variables when dimensioning an array. 

The term variable in variable-length array does not mean that you can modify the length of the array after you create it. Once created, a VLA keeps the same size. What the term variable does mean is that you can use a variable when specifying the array dimensions when first creating the array. 



declare a function with a two-dimensional VLA argument: 

Note that the first two parameters ( rows and cols) are used as dimensions for declaring the array parameter ar.

```c#
int sum2d(int rows, int cols, int ar[rows][cols]);
int sum2d(int ar[rows][cols], int rows, int cols); // invalid order 
```

The C99/C11 standard says you can omit names from the prototype; but in that case, you need to replace the omitted dimensions with asterisks: 

```c#
int sum2d(int, int, int ar[*][*]); 
```

One point to note is that a VLA declaration in a function definition parameter list doesn’t actually create an array. Just as with the old syntax, the VLA name really is a pointer. 



### Compound Literals 

Literals are constants that aren’t symbolic. For example, 5 is a type int literal, 81.3 is a type double literal, 'Y' is a type char literal, and "elephant" is a string literal. 

For arrays, a compound literal looks like an array initialization list preceded by a type name that is enclosed in parentheses. For example, here’s an ordinary array declaration: 

```c#
int diva[2] = {10, 20}; 
```

And here’s a compound literal that creates a nameless array containing the same two int values: 

```c#
(int [2]){10, 20} // a compound literal 
```

Just as you can leave out the array size if you initialize a named array, you can omit it from a compound literal, and the compiler will count how many elements are present: 

```c#
(int []){50, 20, 90} // a compound literal with 3 elements 
```

Because these compound literals are nameless, you can’t just create them in one statement and then use them later. Instead, you have to use them somehow when you make them. One way is to use a pointer to keep track of the location. That is, you can do something like this:

```c#
int * pt1; 
pt1 = (int [2]) {10, 20}; 
```

Another thing you could do with a compound literal is pass it as an actual argument to a function with a matching formal parameter:

```c#
int sum(const int ar[], int n); 
int total3; 
total3 = sum((int []){4,4,4,5,5,5}, 6); 
```

You can extend the technique to two-dimensional arrays, and beyond. Here, for example, is how to create a two-dimensional array of ints and store the address: 

```c#
int (*pt2)[4]; // declare a pointer to an array of 4-int arrays 
pt2 = (int [2][4]) { {1,2,3,-9}, {4,5,6,-8} };
```





















## Character String and String Functions

### Representing Strings and String I/O 

The puts() function, like printf(), belongs to the the stdio.h family of input/output functions. It only displays strings, and, unlike printf(), it automatically appends a newline to the string it displays

#### Defining Strings Within a Program 

There are many ways to define a string. The principal ways are using string constants, using char arrays, and using char pointers. 

A string literal, also termed a string constant, is anything enclosed in double quotation marks. 



C concatenates string literals if they are separated by nothing or by whitespace. For example, 

```c#
char greeting[50] = "Hello, and"" how are" " you" " today!"; 
```

is equivalent to this: 

```c#
char greeting[50] = "Hello, and how are you today!"; 
```



"%s" to print string in printf()

Indeed, you can use pointer notation to set up a string. 

```c#
const char * pt1 = "Something is pointing at me."; 
```

This declaration is very nearly the same as this one: 

```c
const char ar1[] = "Something is pointing at me."; 
```

##### Array Versus Pointer 

The array form ( ar1[] ) causes an array of 29 elements. The quoted string is said to be in static memory. But the memory for the array is allocated only after the program begins running. At that time, the quoted string is copied into the array. Hereafter, the compiler will recognize the name ar1 as a synonym for the address of the first array element, &ar1[0]. One important point here is that in the array form, ar1 is an address constant. You can’t change ar1, because that would mean changing the location (address) where the array is stored. 

The pointer form ( *pt1) also causes 29 elements in static storage to be set aside for the string. In addition, once the program begins execution, it sets aside one more storage location for the pointer variable pt1 and stores the address of the string in the pointer variable. 

#### Arrays of Character Strings

char* arr[a] vs char arr[m\][n];

There are differences. The first is a five-element array. It takes up the space of the sum of all char in each pointer exactly. The second is an array of five pointers, taking up m*n bytes on our system. 

 

<img src="C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200614223554500.png" alt="image-20200614223554500" style="zoom:60%;" /><img src="C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200614223612798.png" alt="image-20200614223612798" style="zoom:60%;" />



Use %u or %lu instead of %p if your compiler doesn’t support %p . 



### String Input 

The C library supplies a trio of functions that can read strings: scanf(), gets(), and fgets(). 

#### gets() Function

When reading a string, scanf() and the %s specifier read just a single word.  

puts() reads an entire line up through the newline character, discards the newline character, stores the remaining characters, adding a null character to create a C string.

 The problem is that gets() doesn’t check to see if the input line actually fits into the array. If the input string is too long, you get buffer overflow, meaning the excess characters overflow the designated target. The extra characters might just go into unused memory and cause no immediate problems, or they may overwrite other data in your program, but those certainly aren’t the only possibilities. 



#### The Alternatives to gets() 

The traditional alternative to gets() is fgets()

##### The fgets() Function (and fputs() )

The fgets() function meets the possible overflow problem by taking a second argument that limits the number of characters to be read.

■ It takes a second argument indicating the maximum number of characters to read. If this argument has the value n, fgets() reads up to n-1 characters or through the newline character, whichever comes first. 

■ If fgets() reads the newline, it stores it in the string, unlike gets(), which discards it. 

■ It takes a third argument indicating which file to read. To read from the keyboard, use stdin (for standard input) as the argument; this identifier is defined in stdio.h . 

Because the fgets() function includes the newline as part of the string (assuming the input line fits), it’s often paired with fputs(), which works like puts(), except that it doesn’t automatically append a newline(put() will automatically put a new line). It takes a second argument to indicate which file to write to. For the computer monitor we can use stdout (for standard output) as an argument.

The first input, apple pie, is short enough that fgets() reads the whole input line and stores **apple pie\n\0** in the array. (include '\n')

Another example:

```c#
 /* fgets2.c -- using fgets() and fputs() */
 #include <stdio.h>
 #define STLEN 10
 int main(void)
 {
 	char words[STLEN];
 	puts("Enter strings (empty line to quit):");
 	while (fgets(words, STLEN, stdin) != NULL && words[0] != '\n')
 		fputs(words, stdout);
 	puts("Done.");
 	return 0;
 } 
```

Some output:

Here’s a sample run: Enter strings (empty line to quit): 

*By the way, the gets() function* 

By the way, the gets() function

Interesting—even though STLEN is 10, the program seems to have no problem processing input lines much longer than that. What’s happening is that, in this program, fgets() reads in input STLEN – 1 (i.e., 9) characters at a time. So it begins by reading “By the wa”, storing it as By the wa\0. Then fputs() displays this string and does not advance to the next output line. Next, fgets() resumes where it left off on the original input, that is, it reads “y, the ge” and stores it as y, the ge\0. Then fputs() displays it on the same line it used before. Then fgets() resumes reading the input, and so on, until all that’s left is “tion\n”.

The system uses buffered I/O. This means the input is stored in temporary memory (the buffer) until the Return key is pressed; this adds a newline character to the input and sends the whole line on to fgets(). On output, fputs() sends characters to another buffer, and when a newline is sent, the buffer contents are sent on to the display. 

You might not want the newline as part of the string you store. But the presence or absence of a newline character in the stored string can be used to tell whether the whole line was read. If it wasn’t, then you can decide what to do with the rest of the line. 

Get rid of the newline char:

```c
 while (words[i] != '\n') // assuming \n in words
 	i++;
 words[i] = '\0'; 
```

Skip all char in the same line but exceeding the strlen:

```c
 while (getchar() != '\n') // read but don't store
 	continue; // input including \n 
```



 The null character, or '\0', is the character used to mark the end of a C string. It’s the character whose code is zero.

The null pointer, or NULL, has a value that doesn’t correspond to a valid address of data. 



##### The gets_s() Function 

■ gets_s() just reads from the standard input, so it doesn’t need a third argument. 

■ If gets_s() does read a newline; it discards it rather than storing it. 

■ If gets_s() reads the maximum number of characters and fails to read a newline, it takes several steps. It sets the first character of the destination array to the null character. It reads and discards subsequent input until a newline or end-of-file is encountered. It returns the null pointer. It invokes an implementation-dependent “handler” function (or else one you’ve selected), which may cause the program to exit or abort.

if the input line doesn’t fit: if you don’t want the program to abort or otherwise exit, you’ll need to learn how to write and register special “handlers.” Also, if you manage to keep the program running, gets_s() disposes of the rest of the input line whether you want to or not. The fgets() function is the easiest to work with if the line doesn’t fit, and it leaves more choices up to you. 



##### The scanf() Function 

 scanf() is more of a “get word” than a “get string” function. If you use the %s format, the string runs up to (but not including) the next whitespace character (blank, tab, or newline). If you specify a field width, as in %10s, the scanf() collects up to 10 characters or up to the first whitespace character, whichever comes first





### String Output 

#### The puts() Function 

The puts() function is very easy to use. Just give it the address of a string for an argument. 

 It stops when it encounters the null character, so there had better be one. 

#### The fputs() Function 

 ■ The fputs() function takes a second argument indicating the file to which to write. You can use stdout (for standard output), which is defined in stdio.h, as an argument to output to your display. 

■ Unlike puts(), fputs() **does not** automatically append a newline to the output. 

#### The printf() Function 





### String Functions 

#### The strlen() Function 

Finds the length of a string.   Stop when encounter '\0'.

#### The strcat() Function 

The strcat() (for string concatenation) function takes two strings for arguments. A copy of the second string is tacked onto the end of the first, and this combined version becomes the new first string.

#### The strncat() Function 

The strcat() function does not check to see whether the second string will fit in the first array. If you fail to allocate enough space for the first array, you will run into problems as excess characters overflow into adjacent memory locations. You can use strncat(), which takes a second argument indicating the maximum number of characters to add. The first array need to be large enough to add the second array and '\0'.

#### The strcmp() Function 

Compare two strings' content(stop at '\0'). It returns 0 if its two string arguments are the same and nonzero otherwise.

##### The strcmp() Return Value 

The ANSI standard says that strcmp() returns a negative number if the first string comes before the second alphabetically, returns 0 if they are the same, and returns a positive number if the first string follows the second alphabetically. 

 In general, strcmp() moves along until it finds the first pair of disagreeing characters. It then returns the corresponding code. 

The strcmp() function is for comparing strings, not characters. So you can use arguments such as "apples" and "A", but you cannot use character arguments, such as 'A'. 

#### The strncmp() Variation 

 The strncmp() function compares the strings until they differ or until it has compared a number of characters specified by a third argument. 

####  The strcpy() and strncpy() Functions 

copy a string

strcpy() takes two string pointers as arguments. The second pointer, which points to the original string, can be a declared pointer, an array name, or a string constant. The first pointer, which points to the copy, should point to a data object, such as an array, roomy enough to hold the string.

##### Further strcpy() Properties The strcpy() 

It returns the value of its first argument—the address of a character. The first argument need not point to the beginning of an array; this lets you copy just part of an array.

##### strncpy()

The function call strncpy(target, source, n) copies up to n characters or up through the null character (whichever comes first) from source to target. 

The function never copies more than n characters, so if it reaches the limit before reaching the end of the source string, no null character is added. As a result, the final product may or may not have a null character. For this reason, the program sets n to one less than the size of the target array and then sets the final element in the array to the null character.

#### The sprintf() Function 

The sprintf() function is declared in stdio.h instead of string.h. It works like printf() , but it writes to a string instead of writing to a display. 

 The first argument to sprintf() is the address of the target string. The remaining arguments are the same as for printf()—a conversion specification string followed by a list of items to be written. 

#### Other String Functions 

#### 

### The ctype.h Character Functions and Strings 

 These functions can’t be applied to a string as a whole, but they can be applied to the individual characters in a string.





### Command-Line Arguments 

Then the command line to run it might look like this in Unix: 

$ fuss 

Or it might look like this in the Windows Command Prompt mode: 

C> fuss 

Command-line arguments are additional items on the same line. Here’s an example: 

$ fuss -r Ginger 

A C program can read those additional items for its own use

#### Command-Line Arguments in Integrated Environments 

Integrated Windows environments, such as Apple’s Xcode, Microsoft Visual C++, and Embarcadero C++ Builder, don’t use command lines to run programs. 



### String-to-Number Conversions 

If the number is an integer, you can use the atoi() function (for alphanumeric to integer). It takes a string as an argument and returns the corresponding integer value.

strtol() converts a string to a long, strtoul() converts a string to an unsigned long, and strtod() converts a string to double. 



Its prototype is as follows: 

long strtol(const char * restrict nptr, char ** restrict endptr, int base); 

Here, nptr is a pointer to the string you want to convert, endptr is the address of a pointer that gets set to the address of the character terminating the input number, and base is the number base the number is written in. 

e.g.

```c
#include <stdio.h>
#include <stdlib.h>
#define LIM 30
char *s_gets(char *st, int n);
int main()
{
    char number[LIM];
    char *end;
    long value;
    puts("Enter a number (empty line to quit):");
    while (s_gets(number, LIM) && number[0] != '\0')
    {
        value = strtol(number, &end, 10); /* base 10 */
        printf("base 10 input, base 10 output: %ld, stopped at %s (%d)\n",
               value, end, *end);
        value = strtol(number, &end, 16); /* base 16 */
        printf("base 16 input, base 10 output: %ld, stopped at %s (%d)\n",
               value, end, *end);
        puts("Next number:");
    }
    puts("Bye!\n");
    return 0;
}
char *s_gets(char *st, int n)
{
    char *ret_val;
    int i = 0;
    ret_val = fgets(st, n, stdin);
    if (ret_val)
    {
        while (st[i] != '\n' && st[i] != '\0')
            i++;
        if (st[i] == '\n')
            st[i] = '\0';
        else // must have words[i] == '\0'
            while (getchar() != '\n')
                continue;
    }
    return ret_val;
}
```

The output:

Enter a number (empty line to quit): 																															**10**             																																										base 10 input, base 10 output: 10, stopped at (0)                                                                                                    base 16 input, base 10 output: 16, stopped at (0)                                                                                                          Next number:                                                                                                                                                                   10atom                                                                                                                                                                                       base 10 input, base 10 output: 10, stopped at atom (97)                                                                                                            base 16 input, base 10 output: 266, stopped at tom (116)                                                                                                                                                                                                                 Next number:                                                                                                                                                                                                                                                                                                                                                                        

Bye! 



Many implementations have itoa() and ftoa() functions for converting integers and floating-point values to strings. However, they are not part of the standard C library; use sprintf(), instead, for greater compatibility. 





### Problem

#### scanf & getchar and fget

scanf() & getchar stop reading when you enter Enter. It will not read this '\n' and the '\n' will store in the buffer. Next, when you use fgets to read the next input, it will start with the '\n' you enter in the scanf. So 

```c
	char c;
    char string[10];
 	printf("Enter a char: ");
    c=getchar();// or scanf("%c",c);
    printf("Enter a string: ");
    fgets(string,10,stdin);
```

will not work as expected.

























## Storage Classes, Linkage, and Memory Management

### Storage Classes 

C provides several different models, or storage classes, for storing data in memory. 

 There is a hardware aspect to this—each stored value occupies physical memory. C literature uses the term object for such a chunk of memory. An object can hold one or more values. An object might not yet actually have a stored value, but it will be of the right size to hold an appropriate value. 

There also is a software aspect—the program needs a way to access the object. This can be accomplished, for instance, by declaring a variable: 

int entity = 3; 

This declaration creates an identifier called entity. An identifier is a name, in this case one that can be used to designate the contents of a particular object. 

A variable name isn’t the only way to designate an object. For instance, consider the following declarations: 

int * pt = &entity; 

int ranks[10]; 

In the first case, pt is an identifier. It designates an object that holds an address. Next, the expression *pt is not an identifier because it’s not a name. Next, the expression *pt is not an identifier because it’s not a name. However, it does designate an object, in this case the same object that entity designates.

You can describe an object in terms of its storage duration, which is how long it stays in memory. You can describe an identifier used to access the object by its scope and its linkage , which together indicate which parts of a program can use it. 



#### Scope

Scope describes the region or regions of a program that can access an identifier. 

**Function scope** applies just to labels used with goto statements. This means that even if a label first appears inside an inner block in a function, its scope extends to the whole function.  This means that even if a label first appears inside an inner block in a function, its scope extends to the whole function. It would be confusing if you could use the same label inside two separate blocks, and function scope for labels prevents this from happening. 

**Function prototype scope** applies to variable names used in function prototypes. Function prototype scope runs from the point the variable is defined to the end of the prototype declaration. What this means is that all the compiler cares about when handling a function prototype argument is the types; the names you use, if any, normally don’t matter, and they needn’t match the names you use in the function definition. One case in which the names matter a little is with variable-length array parameters: 

void use_a_VLA(int n, int m, ar[n][m\]); 

A variable with its definition placed outside of any function has **file scope**. 

##### Translation Units and Files(也称编译单元)

What you view as several files may appear to the compiler as a single file.

C preprocessing essentially replaces an #include directive with the contents of the header file. Thus the compiler sees a single file containing information from your source code file and all the header files. This single file is called a translation unit. When we describe a variable as having file scope, it’s actually visible to the whole translation unit. If your program consists of several source code files, then it will consist of several translation units, with each translation unit corresponding to a source code file and its included files. 



#### Linkage

A C variable has one of the following linkages: external linkage, internal linkage, or no linkage 

Variables with block scope, function scope, or function prototype scope have no linkage. That means they are private to the block, function, or prototype in which they are defined.

A variable with file scope can have either internal or external linkage. A variable with external linkage can be used anywhere in a multifile program. A variable with internal linkage can be used anywhere in a single translation unit. 

Some common short cuts are to use “file scope” for “file scope with internal linkage” and “global scope” or “program scope” for “file scope with external linkage.” 



The storage class specifier static is used in the external definition

```c
int giants = 5; // file scope, external linkage
static int dodgers = 3; // file scope, internal linkage
int main()
{
 ...
}
```

The variable giants can be used by other files that are part of the same program. The dodgers variable is private to this particular file, but can be used by any function in the file. 



#### Storage Duration 

A C object has one of the following four storage durations: static storage duration, thread storage duration, automatic storage duration, or allocated storage duration .

If an object has static storage duration, it exists throughout program execution. Variables with file scope have static storage duration. 

Thread storage duration comes into play in concurrent programming, in which program execution can be divided into multiple threads. An object with thread storage duration exists from when it’s declared until the thread terminates

Thread storage duration comes into play in concurrent programming, in which program execution can be divided into multiple threads. 

Variables with block scope normally have automatic storage duration. These variables have memory allocated for them when the program enters the block in which they are defined, and the memory is freed when the block is exited. 

Variable-length arrays provide a slight exception in that they exist from the point of declaration to the end of the block rather than from the beginning of the block to the end. 

It is possible, however, for a variable to have block scope but static storage duration. To create such a variable, declare it inside a block and add the keyword static to the declaration





C uses scope, linkage, and storage duration to define several storage schemes for variables. That leaves five storage classes: automatic, register, static with block scope, static with external linkage, and static with internal linkage. 

![image-20200616204723184](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200616204723184.png)





#### Automatic Variables 

A variable belonging to the automatic storage class has automatic storage duration, block scope, and no linkage. By default, any variable declared in a block or function header belongs to the automatic storage class. You can, however, make your intentions perfectly clear by explicitly using the keyword auto,

```c
auto int plox; 
```



#### Register Variables 

Variables are normally stored in computer memory. With luck, register variables are stored in the CPU registers or, more generally, in the fastest memory available, where they can be accessed and manipulated more rapidly than regular variables. Because a register variable may be in a register rather than in memory, you can’t take the address of a register variable. In most other respects, register variables are the same as automatic variables. 

 A variable is declared by using the storage class specifier register :  

```c
register int quick; 
```



#### Static Variables with Block Scope 

The computer remembers their values from one function call to the next—such variables are createdby declaring them in a block (which provides the block scope and lack of linkage) with the storage-class specifier static (which provides the static storage duration). 

For example:

```c
 /* loc_stat.c -- using a local static variable */
 #include <stdio.h>
 void trystat(void);
 int main(void)
 {
 	int count;
 	for (count = 1; count <= 3; count++)
 	{
 		printf("Here comes iteration %d: ", count);
 		trystat();
 	}
 	return 0;
 }
 void trystat(void)
 {
 	int fade = 1;
 	static int stay = 1;
 	printf("fade = %d and stay = %d\n", fade++, stay++);
 } 
```

The output is:

 Here comes iteration 1: fade = 1 and stay = 1 

Here comes iteration 2: fade = 1 and stay = 2 

Here comes iteration 3: fade = 1 and stay = 3 

The  change of the value of stay will remain.



#### Static Variables with External Linkage 

You create an external variable by placing a defining declaration outside of any function. As a matter of documentation, an external variable can additionally be declared inside a function that uses it by using the extern keyword.

 If a particular external variable is defined in one source code file and is used in a second source code file, declaring the variable in the second file with extern is mandatory.

##### Initializing External Variables 

Unlike automatic variables, external variables are initialized automatically to zero if you don’t initialize them. This rule applies to elements of an externally defined array, too. Unlike the case for automatic variables, you can use only constant expressions to initialize file scope variables: 



#### Static Variables with Internal Linkage 

 the static variable with internal linkage can be used only by functions in the same file. 





### A Random-Number Function and a Static Variable 

The ANSI C library provides the rand() function to generate random numbers. 



### Allocated Memory: malloc() and free() 

malloc() function takes one argument: the number of bytes of memory you want. Then malloc() finds a suitable block of free memory. The memory is anonymous; that is, malloc() allocates memory but it doesn’t assign a name to it. 

The malloc() function can be used to return pointers to arrays, structures, and so forth, so normally the return value is typecast to the proper value.  If malloc() fails to find the required space, it returns the null pointer. 

```c
double * ptd;
ptd = (double *) malloc(30 * sizeof(double)); 
```



#### The calloc() Function 

Another option for memory allotment is to use calloc().

The first argument is the number of memory cells you want. The second argument is the size of each cell in bytes. 

```c
 long * newmem;
 newmem = (long *)calloc(100, sizeof (long)); 
```

The statement using calloc() additionally sets each element to 0.

The free() function can also be used to free memory allocated by calloc() . 



#### Dynamic Memory Allocation and Variable-Length Arrays 

 You can create a two-dimensional array using malloc(), but the syntax is awkward. 

Some examples:

```c
 int n = 5;
 int m = 6;
 int ar2[n][m]; // n x m VLA
 int (* p2)[6]; // works pre-C99
 int (* p3)[m]; // requires VLA support
 p2 = (int (*)[6]) malloc(n * 6 * sizeof(int)); // n * 6 array
 p3 = (int (*)[m]) malloc(n * m * sizeof(int)); // n * m array
 ar2[1][2] = p2[1][2] = 12; 
```



#### Storage Classes and Dynamic Memory Allocation 

You can think of a program as dividing its available memory into three separate sections: one for static variables with external linkage, internal linkage, and no linkage; one for automatic variables; and one for dynamically allocated memory. 

The amount of memory needed for the static duration storage classes is known at compile time, and the data stored in this section is available as long as the program runs. Each variable of these classes comes into being when the program starts and expires when the program ends. 

An automatic variable, however, comes into existence when a program enters the block of code containing the variable’s definition and expires when its block of code is exited. 

Dynamically allocated memory comes into existence when malloc() or a related function is called, and it’s freed when free() is called. 

Memory persistence is controlled by the programmer, not by a set of rigid rules, so a memory block can be created in one function and disposed of in another function. Also, using dynamic memory tends to be a slower process than using stack memory.



### ANSI C Type Qualifiers 

You’ve seen that a variable is characterized by both its type and its storage class. C90 added two more properties: constancy and volatility. These properties are declared with the keywords const and volatile, which create qualified types. The C99 standard added a third qualifier, restrict, designed to facilitate compiler optimizations. And C11 adds a fourth, _Atomic. C11 provides an optional library, managed by stdatomic.h, to support concurrent programming, and _Atomic is part of that optional support. 

You can use the same qualifier more than once in a declaration, and the superfluous ones are ignored

```c
const const const int n = 6; // same as const int n = 6;

typedef const int zip;
const zip q = 8; //accepted
```



#### The const Type Qualifier 

must be initialized when the variable declared

##### Using const with Pointers and Parameter Declarations 

```c
const float * pf; /* pf points to a constant float value */ 
float const * pfc; // same as const float * pfc; 
float * const pt; /* pt is a const pointer */ 
```

One common use for this new keyword is declaring pointers that serve as formal function parameters. 

##### Using const with Global Data 

Recall that using global variables is considered a risky approach because it exposes data to being mistakenly altered by any part of a program.



#### The volatile Type Qualifier 

The volatile qualifier tells the compiler that a variable can have its value altered by agencies other than the program. 

 It is typically used for hardware addresses and for data shared with other programs or threads running simultaneously. For example, an address might hold the current clock time. The value at that address changes as time changes, regardless of what your program is doing. 

```c
volatile int loc1; /* loc1 is a volatile location */
volatile int * ploc; /* ploc points to a volatile location */ 
```





 It facilitates compiler optimization. e.g.

```CQL
 val1 = x;
 /* some code not using x */
 val2 = x;
```

A smart (optimizing) compiler might notice that you use x twice without changing its value. It would temporarily store the x value in a register. Then, when x is needed for val2, it can save time by reading the value from a register instead of from the original memory location. This procedure is called **caching**.

Ordinarily, caching is a good optimization, but not if x is changed between the two statements by some other agency. If there were no volatile keyword, a compiler would have no way of knowing whether this might happen. Therefore, to be safe, the compiler couldn’t cache. That was the pre-ANSI situation. Now, however, if the volatile keyword is not used in the declaration, the compiler can assume that a value hasn’t changed between uses, and it can then attempt to optimize the code. 

volatile tells the complier that the value might be changed during the proceeding so if the program needs to access the value of volatile variable, it directly accesses the value from its address, not the register.

 

#### The restrict Type Qualifier 

The restrict keyword enhances computational support by giving the compiler permission to **optimize** certain kinds of code. 

It can be applied only to pointers, and it indicates that a pointer is the sole initial means of accessing a data object.(唯一初始手段)

```c
int ar[10];
int * restrict restar = (int *) malloc(10 * sizeof(int));
int * par = ar; 
```

Here, the pointer restar is the sole initial means of access to the memory allocated by malloc(). Therefore, it can be qualified with the keyword restrict. The pointer par , however, is neither the initial nor the sole means of access to the data in the ar array, so it cannot be qualified as restrict . 

Without the restrict keyword, the compiler has to assume the worse case; namely, that some other identifier might have changed the data in between two uses of a pointer. With the restrict keyword used, the compiler is free to look for computational shortcuts. 



You can use the restrict keyword as a qualifier for function parameters that are pointers. This means that the compiler can assume that no other identifiers modify the pointed-to data within the body of the function and that the compiler can try optimizations it might not otherwise use.

The keyword restrict has two audiences. One is the compiler, and it tells the compiler it is free to make certain assumptions concerning optimization. The other audience is the user, and it tells the user to use only arguments that satisfy the restrict requirements. 



#### The _Atomic Type Qualifier (C11) 

Concurrent programming divides program execution into threads that may be executed in parallel. This creates several programming challenges, including how to manage different threads that access the same data. 

 C11 provides, as an option and not a requirement, management methods set up by the optional header files stdatomic.h and threads.h. While a thread performs an atomic operation on an object of atomic type, other threads won’t access that object

```c
 _Atomic int hogs; // hogs an atomic variable
 atomic_store(&hogs, 12); // macro from stdatomic.h 
```

Here, the storing of the value 12 in hogs is an atomic process during which other threads won’t access hogs. 



#### New Places for Old Keywords 

```c
void ofmouth(int * const a1, int * restrict a2, int n); // older style 
void ofmouth(int a1[const], int a2[restrict], int n); // allowed by C99 
```



Instead of indicating the scope or linkage of a static storage variable, the new use is to tell the compiler how a formal parameter will be used. 

```c
double stick(double ar[static 20]); 
```

This use of static indicates that the actual argument in a function call will be a pointer to the first element of an array having at least 20 elements. The purpose of this is to enable the compiler to use that information to optimize its coding of the function. 



























## File Input and Output

### Communicating with Files 

#### The Text Mode and the Binary Mode 

All file content is in binary form (zeros and ones). But if a file primarily uses the binary codes for characters (for instance, ASCII or Unicode) to represent text, much as a C string does, then it is a text file; it has text content. If, instead, the binary values in the file represent machinelanguage code or numeric data (using the same internal representation as, say, used for long or double values) or image or music encoding, the content is binary. 



#### Levels of I/O 

Low-level I/O uses the fundamental I/O services provided by the operating system. Standard high-level I/O uses a standard package of C library functions and stdio.h header file definitions. 



#### Standard File

C programs automatically open three files on your behalf. They are termed the standard input , the standard output, and the standard error output. The purpose of the standard error output file is to provide a logically distinct place to send error messages. 





### Standard I/O

 Input and output are buffered. This buffering greatly increases the data transfer rate. 



The exit() function causes the program to terminate, closing any open files. The argument to exit() is passed on to some operating systems, including Unix, Linux, Windows, and MS-DOS, where it can be used by other programs. 

#### The fopen() Function 

Next, the program uses fopen() to open the file. This function is declared in stdio.h. Its first argument is the name of the file to be opened; more exactly, it is the address of a string containing that name. The second argument is a string identifying the mode in which the file is to be opened. The C library provides for several possibilities

![image-20200618132740451](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200618132740451.png)

![image-20200618132757363](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200618132757363.png)



After your program successfully opens a file, fopen() returns a file pointer, which the other I/O functions can then use to specify the file. The file pointer ( fp in this example) is of type pointer-to- FILE; FILE is a derived type defined in stdio.h. The pointer fp doesn’t point to the actual file. The pointer fp doesn’t point to the actual file. Instead, it points to a data object containing information about the file, including information about the buffer used for the file’s I/O. Because the I/O functions in the standard library use a buffer, they need to know where the buffer is. They also need to know how full the buffer is and which file is being used. The data object pointed to by fp has all that information.

The fopen() function returns the null pointer (also defined in stdio.h) if it cannot open the file. This program exits if fp is NULL. The fopen() function can fail because the disk is full, because the file is not in the searched directory, because the name is illegal, because access is restricted, or because of a hardware problem……



#### The getc() and putc() Functions 

This statement means “get a character from the file identified by fp ”:

```c
ch = getc(fp); 
```

Similarly, this statement means “put the character ch into the file identified by the FILE pointer fpout ”: 

```c
putc(ch, fpout); 
```



#### End-of-File 

The getc() function returns the special value EOF if it tries to read a character and discovers it has reached the end of the file. So a C program discovers it has reached the end of a file only after it tries to read past the end of the file. 



#### The fclose() Function 

The **fclose(fp)** function closes the file identified by fp, flushing buffers as needed. The function fclose() returns a value of 0 if successful, and EOF if not: 

The fclose() function can fail if, for example, the disk is full, a removable storage device has been removed, or there has been an I/O error. 



#### Pointers to the Standard Files 

<img src="C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200618164908997.png" alt="image-20200618164908997" style="zoom:80%;" />







### File I/O: fprintf(), fscanf(), fgets(), and fputs() 

#### The fprintf() and fscanf() Functions 

The file I/O functions fprintf() and fscanf() work just like printf() and scanf(), except that they require an additional first argument to identify the proper file.



#### The fgets() and fputs() Functions 

Change the last argument to a certain file



### Adventures in Random Access: fseek() and ftell()

#### fseek()

The fseek() function enables you to treat a file like an array and move directly to any particular byte in a file opened by fopen(). 

The first of the three arguments to fseek() is a FILE pointer to the file being searched. The file should have been opened by using fopen() . 

The second argument to fseek() is called the offset. This argument tells how far to move from the starting point (see the following list of mode starting points). The argument must be a long value. It can be positive (move forward), negative (move backward), or zero (stay put). The third argument is the mode, and it identifies the starting point.

<img src="C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200618174439469.png" alt="image-20200618174439469" style="zoom:67%;" />

```c
 fseek(fp, 0L, SEEK_SET); // go to the beginning of the file
 fseek(fp, 10L, SEEK_SET); // go 10 bytes into the file
 fseek(fp, 2L, SEEK_CUR); // advance 2 bytes from the current position
 fseek(fp, 0L, SEEK_END); // go to the end of the file
 fseek(fp, -10L, SEEK_END); // back up 10 bytes from the end of the file 
```



#### The fgetpos() and fsetpos() Functions 

Instead of using a long value to represent a position, it uses a new type, called fpos_t (for file position type) for that purpose. 

 A variable or data object of fpos_t type can specify a location within a file, and it cannot be an array type, but its nature is not specified beyond that. 

ANSI C does define how fpos_t is used. The fgetpos() function has this prototype: 

```c
int fgetpos(FILE * restrict stream, fpos_t * restrict pos); 
```

When called, it places an fpos_t value in the location pointed to by pos; the value describes a location in the file. The function returns zero if successful and a nonzero value for failure. 





### Behind the Scenes with Standard I/O 

 The fopen() function not only opens a file but sets up a buffer (two buffers for read-write modes), and it sets up a data structure containing data about the file and about the buffer.  Also, fopen() returns a pointer to this structure so that other functions know where to find it. Assume that this value is assigned to a pointer variable named fp. The fopen() function is said to “open a stream.” If the file is opened in the text mode, you get a text stream, and if the file is opened in the binary mode, you get a binary stream. 

Calling any one of these functions causes a chunk of data to be copied from the file to the buffer. The buffer size is implementation dependent, but it typically is 512 bytes or some multiple thereof.  The initial function call sets values in the structure pointed to by fp. In particular, the current position in the stream and the number of bytes copied into the buffer are set. Usually the current position starts at byte 0. 

When an input function finds that it has read all the characters in the buffer, it requests that the next buffer-sized chunk of data be copied from the file into the buffer. 



### Other Standard I/O Functions 

#### The int ungetc(int c, FILE *fp) Function 

```c
int ungetc(int, FILE*)
```

The int ungetc() function pushes the character specified by c back onto the input stream.

<img src="C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200618210249592.png" alt="image-20200618210249592" style="zoom:67%;" />

#### The int fflush() Function 

```c
int fflush(FILE *fp); 
```

Calling the fflush() function causes any unwritten data in the output buffer to be sent to the output file identified by fp. 

#### The int setvbuf() Function 

```c
int setvbuf(FILE * restrict fp, char * restrict buf, int mode, size_t size); 
```

The setvbuf() function sets up an alternative buffer to be used by the standard I/O functions. It is called after the file has been opened and before any other operations have been performed on the stream. The pointer fp identifies the stream, and buf points to the storage to be used. If the value of buf is not NULL, you must create the buffer. For instance, you could declare an array of 1,024 chars and pass the address of that array. The size variable tells setvbuf() how big the array is. 

The mode is selected from the following choices: _IOFBF means fully buffered (buffer flushed when full), _IOLBF means line-buffered (buffer flushed when full or when a newline is written), and _IONBF means nonbuffered. The function returns zero if successful, nonzero otherwise. 

#### Binary I/O: fread() and fwrite() 

 In general, fprintf() converts numeric values to character data, possibly altering the value.

The most accurate and consistent way to store a number is to use the same pattern of bits that the computer does. Therefore, a double value should be stored in a size double unit. When data is stored in a file using the same representation that the program uses, we say that the data is stored in binary form. There is no conversion from numeric forms to character sequences.



##### The size_t fwrite() Function 

```c
size_t fwrite(const void * restrict ptr, size_t size, size_t nmemb, FILE * restrict fp); 
```

The fwrite() function writes binary data to a file. The size_t type is defined in terms of the standard C types. It is the type returned by the sizeof operator. Typically, it is unsigned int , but an implementation can choose another type. The pointer ptr is the address of the chunk of data to be written. Also, size represents the size, in bytes, of the chunks to be written, and nmemb represents the number of chunks to be written. As usual, fp identifies the file to be written to.

For example:

```c
char buffer[256];
fwrite(buffer, 256, 1, fp); 

double earnings[10];
fwrite(earnings, sizeof (double), 10, fp); 
```

 One problem with fwrite() is that its first argument is not a fixed type. Under ANSI C function prototyping, these actual arguments are converted to the pointer-to- void type, which acts as a sort of catchall type for pointers. 

The fwrite() function returns the number of items successfully written. Normally, this equals nmemb, but it can be less if there is a write error



##### The size_t fread() Function 

```c
size_t fread(void * restrict ptr, size_t size, size_t nmemb, FILE * restrict fp); 
```

 Use this function to read data that was written to a file using fwrite(). F



#### The int feof(FILE *fp) and int ferror(FILE *fp) Functions 

 The feof() function returns a nonzero value if the last input call detected the end-of-file, and it returns zero otherwise. The ferror() function returns a nonzero value if a read or write error has occurred, and it returns zero otherwise. 

















## Structures and Other Data Forms 

### Structure

```c
 struct book {
 	char title[MAXTITL];
 	char author[MAXAUTL];
 	float value;
 }; 
 
 struct book library; 


//short declaration
 struct book {
 	char title[MAXTITL];
 	char author[AXAUTL];
 	float value;
 } library; /* follow declaration with variable name */ 
```

<img src="C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200619112943703.png" alt="image-20200619112943703" style="zoom:80%;" />



#### Initializing a Structure 

e.g.

```c
//One way
struct book library = {
 	"The Pious Pirate and the Devious Damsel",
 	"Renee Vivotte",
 	1.95
 }; 


//Another way 
struct book gift = { .value = 25.99,
 					  .author = "James Broadfool",
                      .title = "Rue for the Toad"}; 


struct book gift= { .value = 18.90,
 					.author = "Philionna Pestle",
 					0.25}; 
/*
The value 0.25 is assigned to the value member because it is the one immediately listed after the author member in the structure declaration. The new value of 0.25 supersedes the value of 18.90 provided earlier
*/
```

If you are initializing a structure with static storage duration, the values in the initializer list must be constant expressions. If the storage duration is automatic, the values in the list need not be constants. 



##### Nested Structures 

structure in structure



#### Pointers to Structures 

**Member Access by Pointer** "->" and "*"

 If n_data and o_data are both structures of the same type, you can do the following: 

```c
o_data = n_data; // assigning one structure to another
```



#### Character Arrays or Character Pointers in a Structure 

```c
struct pnames {
 char * first;
 char * last;
}; 

struct pnames treas = {"Brad", "Fallingjaw"};
```

 For the struct pnames variable treas, however, the strings are stored wherever the compiler stores string constants. All the structure holds are the two addresses, which takes a total of 16 bytes on our system.  In particular, the struct pnames structure allocates no space to store strings. It can be used only with strings that have had space allocated for them elsewhere, such as string constants or strings in arrays. In short, the pointers in a pnames structure should be used only to manage strings that were created and allocated elsewhere in the program.



```c
struct names accountant;
struct pnames attorney;
puts("Enter the last name of your accountant:");
scanf("%s", accountant.last);
puts("Enter the last name of your attorney:");
scanf("%s", attorney.last); /* here lies the danger */
```

 For the attorney, scanf() is told to place the string at the address given by attorney.last. Because this is an uninitialized variable, the address could have any value, and the program could try to put the name anywhere. If you are lucky, the program might work, at least some of the time—or an attempt could bring your program to a crashing halt.



#### Structure, Pointers, and malloc() 

One instance in which it does make sense to use a pointer in a structure to handle a string is if you use malloc() to allocate memory and use a pointer to store the address. 



#### Compound Literals and Structures (C99) 

The syntax is to preface a brace-enclosed initializer list with the type name in parentheses. For example, the following is a compound literal of the struct book type: 

```c
(struct book) {"The Idiot", "Fyodor Dostoyevsky", 6.99};
```



#### Flexible Array Members (C99) 

```c
struct flex
{
 int count;
 double average;
 double scores[]; // flexible array member
}; 

struct flex * pf; // declare a pointer
// ask for space for a structure and an array
pf = malloc(sizeof(struct flex) + 5 * sizeof(double)); 
```

If you declare a variable of type struct flex, you can’t use scores for anything, because no memory space is set-aside for it. Instead, you are supposed to declare a pointer to the struct flex type and then use malloc() to allocate enough space for the ordinary contents of struct flex plus any extra space you want for the flexible array member. 



First, don’t use structure assignment for copying: 

```c
struct flex * pf1, *pf2; // *pf1 and *pf2 are structures ... 
*pf2 = *pf1; // don't do this 
```

This would just copy the nonflexible members of the structure. Instead, use the memcpy() function



#### Anonymous Structures (C11) 

With C11, you can define person using a nested unnamed member structure: 

```c
struct person
{
 int id;
 struct {char first[20]; char last[20];}; // anonymous structure
}; 
```

You could initialize this structure in the same fashion: 

```c
struct person ted = {8483, {"Ted", "Grass"}}; 
```



#### Functions Using an Array of Structures 



#### Saving the Structure Contents in a File 

s to use fread() and fwrite() to read and write structure-sized units. Recall that these functions read and write using the same binary representation that the program uses. For example, 

```c
fwrite(&primer, sizeof (struct book), 1, pbooks); 
```



First, the "a+b" mode is used for opening the file. The a+ part lets the program read the whole file and append data to the end of the file. The b is the ANSI way of signifying that the program will use the binary file format.





### Unions: A Quick Look 

A union is a type that enables you to store different data types in the same memory space (but not simultaneously). A typical use is a table designed to hold a mixture of types in some order that is neither regular nor known in advance.



Unions are set up in much the same way as structures. There is a union template and a union variable. They can be defined in one step or, by using a union tag, in two. 

```c
union hold {
 int digit;
 double bigfl;
 char letter;
}; 
```

This unioncan hold an int value **or** a double value **or** a char value. 

Here is an example of defining three union variables of the hold type: 

```c
union hold fit; // union variable of hold type 
union hold save[10]; // array of 10 union variables 
union hold * pu; // pointer to a variable of hold type 
```



You can initialize a union. e.g.

```c
union hold valA;
valA.letter = 'R';
union hold valB = valA; // initialize one union to another
union hold valC = {88}; // initialize digit member of union
union hold valD = {.bigfl = 118.2}; // designated initializer 
```



#### Using Union

```c
 fit.digit = 23; // 23 is stored in fit; 2 bytes used
 fit.bigfl = 2.0; // 23 cleared, 2.0 stored; 8 bytes used
 fit.letter = 'h'; // 2.0 cleared, h stored; 1 byte used 
```



You can use the -> operator with pointers to unions 

```c
pu = &fit; x = pu->digit; // same as x = fit.digit 
```



Another place you might use a union is in a structure for which the stored information depends on one of the members. 



#### Anonymous Unions (C11) 

e.g.

```c
 struct car_data {
 	char make[15];
 	int status; /* 0 = owned, 1 = leased */
 	union {
 		struct owner owncar;
 		struct leasecompany leasecar;
 	};
 	...
 }; 
```







### Enumerated Types 

```
enum spectrum {red, orange, yellow, green, blue, violet};
enum spectrum color; 
```

#### enum Constants 

```C
printf("red = %d, orange = %d\n", red, orange);
```

Here is the output:
*red = 0, orange = 1* 



#### enum default value and value assign



#### enum Usage 

The purpose of enumerated types is to enhance a program’s readability and make it easier to maintain. 



#### Shared Namespaces 

C uses the term namespace to identify parts of a program in which a name is recognized. Scope is part of the concept: Two variables having the same name but in different scopes don’t conflict; two variables having the same name in the same scope do conflict. 

There also is a category aspect to namespaces. Structure tags, union tags, and enumeration tags in a particular scope all share the same namespace, and that namespace is different from the one used by ordinary variables. 

You can use the same name for one variable and one tag in the same scope without causing an error, but you can’t declare two tags of the same name or two variables of the same name in the same scope. 







### typedef: A Quick Look 

■ Unlike #define, typedef is limited to giving symbolic names to types only and not to values. 

■ The typedef interpretation is performed by the compiler, not the preprocessor. 

■ Within its limits, typedef is more flexible than #define . 

For example:

```c
typedef unsigned char BYTE;
BYTE x, y[10], * z; 
```



Using typedef also helps increase portability. For example, we’ve mentioned the size_t type, which represents the type returned by the sizeof operator, and the time_t type, which represents the type of value returned by the time() function. The C standard says sizeof and time() return integer types but leaves it up to the implementation to determine which type. 



Some features of typedef can be duplicated with a #define. 

For example, 

```c
#define BYTE unsigned char
```

causes the preprocessor to replace BYTE with unsigned char.

Here is one that can’t be duplicated with a #define : 

```c
typedef char * STRING;
```

Without the keyword typedef, this example would identify STRING itself as a pointer-to- char. With the keyword, it makes STRING an identifier for pointers-to- char. Therefore, 

```c
STRING name, sign;
```

means 

```c
char * name, * sign; 
```

Suppose, instead, you did this: 

```c
#define STRING char *
```

Then

```c
STRING name, sign;
```

would translate to the following: 

```c
char * name, sign; 
```



You can define a structure

```c
typedef struct complex {
 	float real;
 	float imag;
} COMPLEX; 
```

You can then use the type COMPLEX instead of the struct called complex to represent complex numbers. 



#### Fancy Declarations 

C enables you to create elaborate data forms. 

<img src="C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200620002417723.png" alt="image-20200620002417723" style="zoom:80%;" />

```c
 int board[8][8]; // an array of arrays of int
 int ** ptr; // a pointer to a pointer to int
 int * risks[10]; // a 10-element array of pointers to int
 int (* rusks)[10]; // a pointer to an array of 10 ints
 int * oof[3][4]; // a 3 x 4 array of pointers to int
 int (* uuf)[3][4]; // a pointer to a 3 x 4 array of ints
 int (* uof[3])[4]; // a 3-element array of pointers to 4-element arrays of int 
```





### Functions and Pointers 

For example, consider this prototype: 

```c
void ToUpper(char *); // convert string to uppercase 
```

The type for the ToUpper() function is “function with char * parameter and return type void.” To declare a pointer called pf to this function type, do this: 

```c
void (*pf)(char *); // pf a pointer-to-function 
```

The first parentheses pair associates the * operator with pf , meaning that pf is a pointer to a function. This makes (*pf) a function, which makes (char *) the parameter list for the function and void the return type.

The first parentheses are needed because of operator precedence rules. Omitting them leads to something quite different: 

```c
void *pf(char *); // pf a function that returns a pointer 
```



After you have a function pointer, you can assign to it the addresses of functions of the proper type. 

```c
 void ToUpper(char *);
 void ToLower(char *);
 int round(double);
 void (*pf)(char *);
 pf = ToUpper; // valid, ToUpper is address of the function
 pf = ToLower; // valid, ToLower is address of the function
 pf = round; // invalid, round is the wrong type of function
 pf = ToLower(); // invalid, ToLower() is not an address 
```



e.g.

```c
 void ToUpper(char *);
 void ToLower(char *);
 void (*pf)(char *);
 char mis[] = "Nina Metier";
 pf = ToUpper;
 (*pf)(mis); // apply ToUpper to mis (syntax 1)
 pf = ToLower;
 pf(mis); // apply ToLower to mis (syntax 2)
```



Just as one of the most common uses of a data pointer is an argument to a function, one of the most common uses of a function pointer is an argument to a function. e.g.

```c
void show(void (* fp)(char *), char * str); 

show(ToLower, mis); /* show() uses ToLower() function: fp = ToLower */
show(pf, mis); /* show() uses function pointed to by pf: fp = pf */ 
```



You can use typedef in situations like these. For example, the program could have done this:

```c
 typedef void (*V_FP_CHARP)(char *); 
 void show (V_FP_CHARP fp, char *); 
 V_FP_CHARP pfun; 
```



























## Bit Fidding

### Binary Numbers, Bits, and Bytes 

#### Binary Floating Point 

 .101 represents 1/2 + 0/4 + 1/8 





### C’s Bitwise Operators 

#### Bitwise Logical Operators 

##### One’s Complement, or Bitwise Negation: ~

The unary operator ~ changes each 1 to a 0 and each 0 to a 1, as in the following example: 

~(10011010) // expression 

(01100101) // resulting value 

##### Bitwise AND: &

The binary operator & produces a new value by making a bit-by-bit comparison between two operands. For each bit position, the resulting bit is 1 only if both corresponding bits in the operands are 1. (In terms of true/false, the result is true only if each of the two bit operands is true.) Therefore, the expression 

(10010011) & (00111101) // expression 

(00010001) // resulting value 

C also has a combined bitwise AND-assignment operator: &=. 

##### Bitwise OR: |

The binary operator | produces a new value by making a bit-by-bit comparison between two operands. For each bit position, the resulting bit is 1 if either of the corresponding bits in the operands is 1. (In terms of true/false, the result is true if one or the other bit operands are true or if both are true.) Therefore, the expression 

(10010011) | (00111101) // expression 

(10111111) // resulting value 

C also has a combined bitwise OR-assignment operator: |=. 

##### Bitwise EXCLUSIVE OR: ^

The binary operator ^ makes a bit-by-bit comparison between two operands. For each bit position, the resulting bit is 1 if one or the other (but not both) of the corresponding bits in the operands is 1. (In terms of true/false, the result is true if one or the other bit operands—but not both— is true.) Therefore, the expression 

(10010011) ^ (00111101) // expression 

(10101110) // resulting value

C also has a combined bitwise OR-assignment operator: ^=.



#### Usage: Masks 

A mask is a bit pattern with some bits set to on (1) and some bits to off (0).

flags = flags & MASK; 

would cause all the bits of flags (except bit 1) to be set to 0 because any bit combined with 0 using the & operator yields 0. Bit number 1 will be left unchanged.



#### Usage: Bitwise Shift Operators 

<<  and  >>





convert an int into a binary string:

```c
 char * itobs(int n, char * ps)
 {
 	int i;
 	const static int size = CHAR_BIT * sizeof(int);
 	for (i = size - 1; i >= 0; i--, n >>= 1)//use & to check if each bit are 1.
 	ps[i] = (01 & n) + '0'; // assume ASCII or similar
 	ps[size] = '\0';
 	return ps;
 }
```





### Bit Fields 

The second method of manipulating bits is to use a bit field, which is just a set of neighboring bits within a signed int or an unsigned int.  A bit field is set up with a structure declaration that labels each field and determines its width. 

```c
 struct {
 	unsigned int autfd : 1;
 	unsigned int bldfc : 1;
 	unsigned int undln : 1;
	unsigned int itals : 1;
 } prnt;
```

This definition causes prnt to contain four 1-bit fields.



Sometimes there are more than two choices for a setting, so you need more than a single bit to
represent all the choices. That’s not a problem because fields aren’t limited to 1-bit sizes. You
can also do this:

```c
struct {
 unsigned int code1 : 2;
 unsigned int code2 : 2;
 unsigned int code3 : 8;
} prcode; 
```



What if the total number of bits you declare exceeds the size of an unsigned int? Then the next unsigned int storage location is used. A single field is not allowed to overlap the boundary between two unsigned ints. The compiler automatically shifts an overlapping field definition so that the field is aligned with the unsigned int boundary. When this occurs, it leaves an unnamed hole in the first unsigned int . 

You can “pad” a field structure with unnamed holes by using unnamed field widths. Using an unnamed field width of 0 forces the next field to align with the next integer: 

```c
struct {
 unsigned int field1 : 1;
 unsigned int : 2;
 unsigned int field2 : 1;
 unsigned int : 0;
 unsigned int field3 : 1;
} stuff; 
```





### Alignment Features (C11) (对齐特性)(看不懂)

Alignment, in this context, refers to how objects are positioned in memory. For example, for maximum efficiency, a system might require a type double value to be stored at a memory address divisible by four but allow a char to stored at any address. 

For most programmers most of the time, alignment isn’t a concern. But some situations may benefit from alignment control, for example, transferring data from one hardware location to another or invoking instructions that operate upon multiple data items simultaneously. 

The _Alignof operator yields the alignment requirement of a type. It’s used by following the keyword _Alignof with the parenthesized type: 

```c
size_t d_align = _Alignof(float); 
```

A value of, say, 4 for d_align means float objects have an alignment requirement of 4. 

You can use the _Alignas specifier to request a specific alignment for a variable or type. But you shouldn’t request an alignment weaker than the fundamental alignment for the type. 





















## The C Preprocessor and the C Library 

### First Steps in Translating a Program 

The compiler has to put a program through some translation phases before jumping into preprocessing.

Second, the compiler locates each instance of a backslash followed by a newline character and deletes them. That is, two physical lines such as 

printf("That's wond\ erful!\n"); 

are converted to a single logical line : 

printf("That's wonderful\n!"); 



Next, the compiler breaks the text into a sequence of preprocessing tokens and sequences of whitespace and comments. 

So something such as 

int/* this doesn't look like a space*/fox; 

becomes 

int fox; 





### Manifest Constants(明示常量): #define 

The #define preprocessor directive, like all preprocessor directives, begins with the # symbol at the beginning of a line. The ANSI and subsequent standards permit the # symbol to be preceded by spaces or tabs, and it allows for space between the # and the remainder of the directive.

We have used directives heavily to define symbolic, or manifest , constants in our programs, but they have more range than that, as we will show.

```c
#define TWO 2 /* you can use comments if you like */
#define OW "Consistency is the last refuge of the unimagina\
			tive. - Oscar Wilde" /* a backslash continues a definition */
 /* to the next line */
#define FOUR TWO*TWO
#define PX printf("X is %d.\n", x)
#define FMT　"X is %d.\n"
```

Each #define line (logical line, that is) has three parts. The first part is the #define directive itself. The second part is your chosen abbreviation, known as a macro. Some macros, like these examples, represent values; they are called object-like macros. (C also has function-like macros ) The third part (the remainder of the line) is termed the replacement list or body



The preprocessor does no calculation; it just makes the suggested substitutions very literally. So

```CQL
x=FOUR;
```

will become x=TWO*TWO and then x=2\*2





####  Tokens 

Technically, the body of a macro is considered to be a string of tokens rather than a string of characters. 

```c
#define EIGHT 4 * 8 
```

A preprocessor that interprets the body as a character string would replace EIGHT with 4 * 8 . That is, the extra spaces would be part of the replacement, but a preprocessor that interprets the body as tokens will replace EIGHT with three tokens separated by single spaces: 4 * 8. In other words, the character string interpretation views the spaces as part of the body, but the token interpretation views the spaces as separators between the tokens of the body. 

Incidentally, the C compiler takes a more complex view of tokens than the preprocessor does. The compiler understands the rules of C and doesn’t necessarily require spaces to separate tokens.



#### Redefining Constants 

Suppose you define LIMIT to be 20, and then later in the same file you define it again as 25. This process is called redefining a constant. Implementations differ on redefinition policy.  The ANSI standard allows redefinition only if the new definition duplicates the old. 

Having the same definition means the bodies must have the same tokens in the same order. ****

It has just one token, not three, so it doesn’t match. If you want to redefine a macro, use the #undef directive.



#### Using Arguments with #define 

Function-like macro definitions have one or more arguments in parentheses, and these arguments then appear in the replacement portion

![image-20200621114655842](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200621114655842.png)

It can be used in program like this:

```c#
#define SQUARE(X) X*X
z = SQUARE(2); 
z = SQUARE(x+2);//z=x+2*x+2,not (x+2)*(x+2)
z = 100/SQUARE(x);//z=100/x*x,not 100/(x*x)
```

So we need some paratheness to achieve that:

```c#
#define SQUARE(x) (x*x)
#define SQUARE(x) ((x)*(x)) 
```



#### Creating Strings from Macro Arguments: The # Operator 

Suppose you do want to include the macro argument in a string. C enables you to do that. Within the replacement part of a function-like macro, the # symbol becomes a preprocessing operator that converts tokens into strings.

```c#
#include <stdio.h>
#define PSQR(x) printf("The square of " #x " is %d.\n",((x)*(x)))
int main(void)
{
 int y = 5;
 PSQR(y);
 PSQR(2 + 4);
 return 0;
}
```

Here is the output:

The square of y is 25. 

The square of 2 + 4 is 36. 



#### Preprocessor Glue: The ## Operator 

Like the # operator, the ## operator can be used in the replacement section of a function-like macro. Additionally, it can be used in the replacement section of an object-like macro. The ## operator combines two tokens into a single token.

```c#
 #include <stdio.h>
 #define XNAME(n) x ## n
 #define PRINT_XN(n) printf("x" #n " = %d\n", x ## n);
 int main(void)
 {
 	int XNAME(1) = 14; // becomes int x1 = 14;
 	int XNAME(2) = 20; // becomes int x2 = 20;
 	int x3 = 30;
 	PRINT_XN(1); // becomes printf("x1 = %d\n", x1);
 	PRINT_XN(2); // becomes printf("x2 = %d\n", x2);
 	PRINT_XN(3); // becomes printf("x3 = %d\n", x3);
 	return 0;
 } 
```



#### Variadic Macros: ... and _ _VA_ARGS_ _ 

Some functions, such as printf(), accept a variable number of arguments. The stdvar.h header file provides tools for creating user-defined functions with a variable number of arguments.

The idea is that the final argument in an argument list for a macro definition can be ellipses (that is, three periods). If so, the predefined macro _ _VA_ARGS_ _ can be used in the substitution part to indicate what will be substituted for the ellipses.

```c#
 #define PR(...) printf(_ _VA_ARGS_ _)
 PR("Howdy");
 PR("weight = %d, shipping = $%.2f\n", wt, sp); 
```

```c#
#include <stdio.h>
#include <math.h>
#define PR(X, ...) printf("Message " #X ": " _ _VA_ARGS_ _)
int main(void)
{
 double x = 48;
 double y;
 y = sqrt(x);
 PR(1, "x = %g\n", x);
 PR(2, "x = %.2f, y = %.4f\n", x, y);
  return 0;
} 
```



#### Macro or Function? 

A macro produces inline code; that is, you get a statement in your program. If you use the macro 20 times, you get 20 lines of code inserted into your program. If you use a function 20 times, you have just one copy of the function statements in your program, so less space is used. On the other hand, program control must shift to where the function is and then return to the calling program, and this takes longer than inline code. 

 If you intend to use a macro instead of a function primarily to speed up a program, first try to determine whether it is likely to make a significant difference. A macro that is used once in a program probably won’t make any noticeable improvement in running time. A macro inside a nested loop is a much better candidate for speed improvements. Many systems offer program profilers to help you pin down where a program spends the most time. 





### File Inclusion: #include 

As with Unix, using double quotes means to search a local directory first, but the exact directory searched depends on the compiler.

Including a large header file doesn’t necessarily add much to the size of your program. The content of header files, for the most part, is information used by the compiler to generate the final code, not material to be added to the final code. 





### Other Directives 

#### The #undef Directive 

```c#
#define LIMIT 400
#undef LIMIT //remove the definition
```

Note that the scope of a #define macro extends from the point it is declared in a file until it is the subject of an #undef directive or until the end of the file

A few predefined macros, such as _ _DATE_ _ and _ _FILE_ _ (discussed later this chapter), are always considered defined and cannot be undefined. 



#### Conditional Compilation 

##### The #ifdef, #else, and #endif Directives 

The #ifdef directive says that if the following identifier ( MAVIS) has been defined by the preprocessor, follow all the directives and compile all the C code up to the next #else or #endif, whichever comes first. If there is an #else, everything from the #else to the #endif is done if the identifier isn’t defined.

##### The #ifndef Directive 

The #ifndef directive can be used with #else and #endif in the same way that #ifdef is.

Typically, this idiom is used to prevent multiple definitions of the same macro when you include several header files, each of which may contain a definition. 



```c#
 #ifndef THINGS_H_
 #define THINGS_H_
 /* rest of include file */
 #endif 
```

Suppose this file somehow got included several times. The first time the preprocessor encounters this include file, THINGS_H_ is undefined, so the program proceeds to define THINGS_H_ and to process the rest of the file. The next time the preprocessor encounters this file, THINGS_H_ is defined, so the preprocessor skips the rest of the file. 

Why would you include a file more than once? The most common reason is that many include files include other files, so you may include a file explicitly that another include file has already included.  Why is this a problem? Some items that appear in include files, such as declarations of structure types, can appear only once in a file. The standard C header files use the #ifndef technique to avoid multiple inclusions. 



##### The #if and #elif Directives 

The #if directive is more like the regular C if

It ends with #endif.



##### Predefined Macros 

<img src="C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200621180149876.png" alt="image-20200621180149876" style="zoom:80%;" />



#### \#line and #error 

The #line directive lets you reset the line numbering and the filename as reported by the _ _LINE_ _ and _ _FILE_ _ macros. You can use #line like this: 

```c#
#line 1000 // reset current line number to 1000 
#line 10 "cool.c" // reset line number to 10, file name to cool.c 
```



The #error directive causes the preprocessor to issue an error message that includes any text in the directive. If possible, the compilation process should halt. You could use the directive like this:

```c#
 #if _ _STDC_VERSION_ _ != 201112L
 #error Not C11
 #endif 
```

The output is like this:

$ gcc newish.c 

newish.c:14:2: error: #error Not C11 

$ gcc -std=c11 newish.c 

$ 



#### \#pragma(编译指示) 

The #pragma lets you place compiler instructions in the source code. For example, while C99 was being developed, it was referred to as C9X, and one compiler used the following pragma to turn on C9X support: 

```c#
#pragma c9x on 
```



C99 also provides the _Pragma preprocessor operator. It converts a string into a regular pragma. For example,

```c#
 _Pragma("nonstandardtreatmenttypeB on") 
 #pragma nonstandardtreatmenttypeB on //These two are equivalent
```



#### Generic Selection (C11) 

In programming, the term generic programming indicates code that is not specific to a particular type but which, once a type is specified, can be translated into code for that type.

The generic selection expression is not a preprocessor statement, but its usual use is a part of a #define macro definition that has some aspects of generic programming. 

```c#
 _Generic(x, int: 0, float: 1, double: 2, default: 3) 
```

The type of the first term is matched to one of the labels, and the value of the whole expression is the value following the matched label. For example, suppose x in the preceding expression is a type int variable. Then the type of x matches the int: label, making 0 the value of the whole expression. 



 an example combining a generic selection statement with a macro definition: 

```c#
#define MYTYPE(X) _Generic((X),\
 int: "int",\
 float : "float",\
 double: "double",\
 default: "other"\
)
```

The generic selection expression evaluates to a string. For example, the macro invocation MYTYPE(5) evaluates to the string "int" because the type for the value 5 matches the int: label.







### Inline Functions (C99) 

Normally, a function call has overhead. That means it takes execution time to set up the call, pass arguments, jump to the function code, and return.

What the C99 and C11 standards actually say is this: “Making a function an inline function suggests that calls to the function be as fast as possible. The extent to which such suggestions are effective is implementation-defined.” 

The standard says that a function with internal linkage can be made inline and that the definition for the inline function must be in the same file in which the function is used.  So a simple approach is to use the inline function specifier along with the static storage-class specifier. Usually, inline functions are defined before the first use in a file, so the definition also acts as a prototype.

```c#
#include <stdio.h>
inline static void eatline() // inline definition/prototype
{
 while (getchar() != '\n')
 continue;
}
int main()
{
 eatline(); // function call
} 
```

Because an inline function doesn’t have a separate block of code set aside for it, you can’t take its address. (Actually, you can take the address, but then the compiler will generate a non-inline function.) Also, an inline function may not show up in a debugger. 

If you have a multifile program, you need an inline definition in each file that calls the function. The simplest way to accomplish this is to put the inline function definition in a header file and then include the header file in those files that use the function. 





### _Noreturn Functions (C11) 

 C11 adds a second function specifier, _Noreturn, to indicate a function that, upon completion, does not return to the calling function. 





### C Library





### The Math Library 

![image-20200621201132473](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200621201132473.png)

![image-20200621201651774](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200621201651774.png)



#### Type Variants 

The basic floating-point math functions take type double arguments and return a type double value. You can pass them type float or type long double arguments, and the functions still work because the arguments are converted to type double. 

To deal with these potential problems, the C standard provides type float and type long double versions of the standard functions, using an f or an l (“ell”) suffix on the function name. So sqrtf() is a type float version of sqrt(), and sqrtl() is a type long double version.



#### The tgmath.h Library (C99) 

If a math.h function is defined for each of the three types float, double, and long double, the tgmath.h file creates a type-generic macro with the same name as the double version. For instance, it defines a sqrt() macro that expands to the sqrtf(), sqrt(), or sqrtl() function, depending on the type of argument provided.

If you want to, say, invoke the sqrt() function instead of the sqrt() macro even though tgmath.h is included, you can enclose the function name in parentheses: 

```c#
 #include <tgmath.h>
 ...
 float x = 44.0;
 double y;
 y = sqrt(x); // invoke macro, hence sqrtf(x)
 y = (sqrt)(x); // invoke function sqrt() 
```





### The General Utilities Library 

#### The exit() and atexit() Functions 

In addition, the exit() function is invoked automatically upon return from main(). 

The most important addition is that you can specify particular functions to be called when exit() executes. The atexit() function provides this feature by registering the functions to be called on exit; the atexit() function takes a function pointer as its argument.

##### atexit()

To use the atexit() function, simply pass it the address of the function you want called on exit. Because the name of a function acts as an address when used as a function argument, use sign_off or too_bad as the argument.atexit() registers that function in a list of functions to be executed when exit() is called. ANSI guarantees that you can place at least 32 functions on the list. Each function is added with a separate call to atexit(). When the exit() function is finally called, it executes these functions, with the last function added being executed first. 

##### exit()

It flushes all output streams, closes all open streams, and closes temporary files created by calls to the standard I/O function tmpfile(). Traditionally, Unix programs have used 0 to indicate successful termination and nonzero to report failure. Unix return codes don’t necessarily work with all systems, so ANSI C defined a macro called EXIT_FAILURE that can be used portably to indicate failure. Similarly, it defined EXIT_SUCCESS to indicate success, but exit() also accepts 0 for that purpose.



#### The qsort() Function 

The “quick sort” method is one of the most effective sorting algorithms, particularly for larger arrays.

```c#
 void qsort (void *base, size_t nmemb, size_t size, int (*compar)(const void *, const 				void *)); 
```

The first argument is a pointer to the beginning of the array to be sorted. The second argument is the number of items to be sorted. Because qsort() converts its first argument to a void pointer, qsort() loses track of how big each array element is. To compensate, you must tell qsort() explicitly the size of the data object. That’s what the third argument is for. For example, if you are sorting an array of type double, you would use sizeof(double) for this argument. Finally, qsort() requires a pointer to the function to be used to determine the sorting order. The comparison function should take two arguments: pointers to the two items being compared. It should return a positive integer if the first item should follow the second value, zero if the two items are the same, and a negative integer if the second item should follow the first.

Some example:

```c#
/* sort by increasing value */
int mycomp(const void * p1, const void * p2)
{
 /* need to use pointers to double to access values */
 const double * a1 = (const double *) p1;
 const double * a2 = (const double *) p2;
 if (*a1 < *a2)
 return -1;
 else if (*a1 == *a2)
 return 0;
 else
 return 1;
} 
```





### The Assert Library 

The assert library, supported by the assert.h header file, is a small one designed to help with debugging programs. 

#### Using assert 

If the expression evaluates as false (nonzero), the assert() macro writes an error message to the standard error stream ( stderr) and calls the abort() function, which terminates the program. 

```c#
assert(z >= 0);
```

If z<0, the function will exit.

#### _Static_assert (C11) 

 The assert() expression is a run-time check. C11 adds a feature, the _Static_assert declaration, that does a compile-time check. So, assert() can cause a running program to abort, while _Static_assert() can cause a program not to compile.

e.g.

```c#
 #include <stdio.h>
 #include <limits.h>
 _Static_assert(CHAR_BIT == 16, "16-bit char falsely assumed");
 int main(void)
 {
 	puts("char is 16 bits.");
 	return 0;
 } 
```

Sample output:

$ clang statasrt.c 

statasrt.c:4:1: error: static_assert failed "16-bit char falsely assumed" 

_Static_assert(CHAR_BIT == 16, "16-bit char falsely assumed"); 

^ ~~~~~~~~~~~~~~ 

1 error generated. 

$ 

In terms of syntax, _Static_assert is treated as a declaration statement. Thus, unlike most kinds of C statements, it can appear either in a function or, as in this case, external to a function. 

The requirement that the first argument to _Static_assert be an integer constant expression guarantees that it can be evaluated during compilation. (Recall that sizeof expressions count as integer constants.) So you can’t substitute _Static_assert for assert in Listing 16.18(example in the last session) , because that program used z > 0 for a test expression, and that’s a nonconstant expression that can be evaluated only while the program is running. 





### memcpy() and memmove() from the string.h Library 

```c#
 void *memcpy(void * restrict s1, const void * restrict s2, size_t n);
 void *memmove(void *s1, const void *s2, size_t n); 
```

To copy two arrays

This shows that memcpy() doesn’t know or care about data types; it just copies bytes from one location to another.





### Variable Arguments: stdarg.h 

The difference between the two, as indicated by the keyword restrict, is that memcpy() is free to assume that there is no overlap between the two memory ranges. The memmove() function doesn’t make that assumption, so copying takes place as if all the bytes are first copied to a temporary buffer before being copied to the final destination. 

```c#
 void f1(int n, ...); // valid
 int f2(const char * s, int k, ...); // valid
 char f3(char c1, ..., char c2); // invalid, ellipsis not last
 double f3(...); // invalid, no parameter


 //f1 could be used in these ways
 f1(2, 200, 400); // 2 additional arguments
 f1(4, 13, 117, 18, 23); // 4 additional arguments 
```

Next, the va_list type, which is declared in the stdargs.h header file, represents a data object used to hold the parameters corresponding to the ellipsis part of the parameter list.



The va_list type, which is declared in the stdargs.h header file, represents a data object used to hold the parameters corresponding to the ellipsis part of the parameter list. 

```c#
va_list ap; // declare object to hold arguments 
```

After this, the function will use the va_start() macro, also defined in stdargs.h, to copy the argument list to the va_list variable. The macro has two arguments: the va_list variable and the parmN parameter. Continuing with the previous example, the va_list variable is called ap and the parmN parameter is call lim, so the call would look like this: 

```c#
va_start(ap, lim); // initialize ap to argument list 
```

The next step is gaining access to the contents of the argument list. This involves using va_ arg(), another macro. It takes two arguments: a type va_list variable and a type name. The first time it’s called, it returns the first item in the list; the next time it’s called, it returns the next item, and so on. 

```c#
 double tic;
 int toc;
 ...
 tic = va_arg(ap, double); // retrieve first argument
 toc = va_arg(ap, int); // retrieve second argument 
```

The argument type really has to match the specification. If the first argument is 10.0, the previous code for tic works fine. But if the argument is 10, the code may not work; the automatic conversion of double to int that works for assignment doesn’t take place here. 

Finally, you should clean up by using the va_end() macro. It may, for example, free memory dynamically allocated to hold the arguments. 

```c#
 va_end(ap);
```



Some example:

```c#
double sum(int lim,...)
{
 va_list ap; // declare object to hold arguments
 double tot = 0;
 int i;
 va_start(ap, lim); // initialize ap to argument list
 for (i = 0; i < lim; i++)
 tot += va_arg(ap, double); // access each item in argument list
 va_end(ap); // clean up
 return tot;
}
```













## Advanced Data Representation 

### Abstract Data Types (ADTs) 

```c#
#define TSIZE 45 /* size of array to hold title */
struct film
{
 char title[TSIZE];
 int rating;
};
typedef struct film Item; 
```

Then you can use the Item type for the rest of the definitions. If you later want a list of some other form of data, you can redefine the Item type and leave the rest of the interface definition unchanged. 



Having defined Item, you now have to decide how to store items of that type. 

```c#
typedef struct node
{
 Item item;
 struct node * next;
} Node;
typedef Node * List;
```



#### Using the Interface 

Our claim is that you should be able to use this interface to write a program without knowing any further details