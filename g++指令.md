# g++指令



g++编译器是GCC的一部分，GCC编译工作一般分为四个步骤：

1. 预处理，生成.i文件[预处理器cpp]

   ```
   g++ -E Test.cpp > Test.i 
   ```

   这一步主要做了这些事情：宏的替换，还有注释的消除，还有找到相关的库文件

2. 将预处理后的文件不转换成汇编语言,生成文件.s[编译器egcs]

   ```
   命令:g++ -S Test.cpp
   ```

3. 有汇编变为目标代码(机器代码)生成.o的文件[汇编器as]

   ```
   g++ -c Test.cpp 
   ```

4. 链接（Linking）。由链接器ld，将.o文件连接生成可执行程序[连接器Id]

   ```
   g++ Test.o -L F:\vs2008\VC\include\iostream
   ```

   -L 表示链接，这里我后面写的是绝对路径

在上面各个步骤中你可以用-o命令输出你自己想要的各种名字。比如最后一个命令，用下面的输出Test.exe

```
g++ Test.o -o Test.exe -L F:\vs2008\VC\include\iostream
```



## 参数详解

#### -c

只激活预处理,编译,和汇编,也就是他只把程序做成obj文件

```
gcc -c hello.c
```

他将生成.o的obj文件



#### -S

只激活预处理和编译，就是指把文件编译成为汇编代码。

```
gcc -S hello.c
```

他将生成.s的汇编代码，你可以用文本编辑器察看



#### -E

只激活预处理,这个不生成文件,你需要把它重定向到一个输出文件里面.

```
gcc -E hello.c > pianoapan.txt
```



#### -o

改名字

```
gcc -o hello.exe hello.c 
gcc -o hello.asm -S hello.c
```



#### -pipe

使用管道代替编译中临时文件

