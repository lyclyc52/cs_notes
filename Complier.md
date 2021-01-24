# Engineering a Complier



## Overview

### structure

A compiler must both understand the source program that it takes as input and map its functionality to the target machine. The distinct nature of these two tasks suggests a division of labor and leads to a design that decomposes compilation into two major pieces: a front end and a back end.

**intermediate representation (IR)**  A compiler uses some set of data structures to represent the code that it processes. That form is called an intermediate representation, or IR.

At each point in compilation, the compiler will have a definitive representation. It may, in fact, use several different irs as compilation progresses, but at each point, one representation will be the definitive ir.



**Optimizer**  The middle section of a compiler, called an optimizer, analyzes and transforms the IR to improve it.

The optimizer can make one or more passes over the ir, analyze the ir, and rewrite the ir. The optimizer may rewrite the ir in a way that is likely to produce a faster target program from the back end or a smaller target program from the back end



#### The Front End

The front end determines if the input code is well formed, interms of both syntax and semantics. If it finds that the code is valid, it creates a representation of the code in the compiler’s intermediate representation; if not, it reports back to the user with diagnostic error messages to identify the problems with the code.

**Scanner**  the compiler pass that converts a string of characters into a stream of words

**Parser**  the compiler pass that determines if the input stream is a sentence in the source language



#### The Optimizer

The analysis determines where the compiler can safely and profitably apply the technique.

Transformations have been invented to improve the time or space requirements of executable code.



#### The Back End

##### **Instruction Selection**  

rewrites the IR operations into target machine operations, a process called instruction selection. During instruction selection, the compiler deliberately ignored the fact that the target machine has a limited set of registers. Instead, it used virtual registers and assumed that “enough” registers existed.

##### **Register Allocation**  

The register allocator decides, at each point in the code, which values should reside in the target-machine registers.

##### Instruction Scheduling

The instruction scheduler reorders the operations in the code. It attempts to minimize the number of cycles wasted waiting for operands. Of course, the scheduler must ensure that the new sequence produces the same result as the original.







## Scanner

### Introduction

It aggregates characters to form words and applies a set of rules to determine whether or not each word is legal in the source language. If the word is valid, the scanner assigns it a syntactic category, or part of speech.

A compiler’s scanner reads an input stream that consists of characters and produces an output stream that contains words, each labelled with its Syntactic category syntactic category—equivalent to a word’s part of speech in English. To a classification of words according to their grammatical usage accomplish this aggregation and classification, the scanner applies a set of rules that describe the lexical structure of the input programming language, Microsyntax sometimes called its microsyntax. The microsyntax of a programming lanthe lexical structure of a language guage specifies how to group characters into words and, conversely, how to separate words that run together.





### RECOGNIZING WORDS

The simplest explanation of an algorithm to recognize words is often a character-by-character formulation.



#### A Formalism for Recognizers

##### Finite automaton  

a formalism for recognizers that has a finite set of
states, an alphabet, a transition function, a start
state, and one or more accepting states

Formally, a finiteautomaton (FA) is a five-tuple 
$$
S, \sum, \delta, s_0, S_A
$$
where

S is the finite set of states in the recognizer, along with an error state s_e.

\sum is the finite alphabet used by the recognizer. Typically, \sum is the unionof the edge labels in the transition diagram.

\delta(s,c) is the recognizer’s transition function. It maps each state s \in S and each character c \in \sum into some next state. In state si with input character c, the FA takes the transition s_i \leftarrow \delta(s_i,c)

s_0 \in S is the designated start state.

S_A is the set of accepting states, S_A \subset S. Each state in S_A appears as a double circle in the transition diagram.

![image-20201005231603784](D:\computer science\notes\Complier.assets\image-20201005231603784.png)

Here s_e is a error state.



For more  complex words, we can use one state to represent many cases. For example,

![image-20201005232834532](D:\computer science\notes\Complier.assets\image-20201005232834532.png)



We can simplify the fa significantly if we allow the transition diagram to
have cycles. We can replace the entire chain of states beginning at s2 with a single transition from s2 back to itself.



### REGULAR EXPRESSIONS

The language consisting of the two words new or while can be written
as new or while. To avoid possible misinterpretation of or, we write
this using the symbol j to mean or. Thus, we write the re as
new | while.

The language consisting of new or not can be written as new j not.
Other res are possible, such as n(ew | ot). Both res specify the same
pair of words. The re n(ew| ot) suggests the structure of the fa that we drew earlier for these two words.



**zero or more occurrences: ***

We call the * operator *Kleene closure*, or *closure* for short.
Using the closure operator, we can write an re for this fa:

0 |(1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9) (0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9)*.

#### Formalizing the Notation
For a given RE, r, we denote the language that it specifies as L(r). An RE is built up from three basic operations:
1. Alternation The alternation, or union, of two sets of strings, R and S, denoted ***R|S*** 
$$
  \{ x|x \in R \; or\; x \in S \}
$$

2. Concatenation The concatenation of two sets R and S, denoted ***RS***, contains all strings formed by prepending an element of R onto one from S, or 
  $$
\{ xy|x \in R\; or \; x \in S\}
  $$
  
3. Closure The Kleene closure of a set R, denoted ***R****, is
  $$
  \bigcup^{\infty}_{i=0}R^i
  $$
  This is just the union of the concatenations of R with itself, zero or more times.

For example:
$$
R^3=(R|RR|RRR)
$$
