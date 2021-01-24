#### 空格

LATEX 将空格和制表符等空白字符视为相同的空白距离（space）。多个连续的空白字符等同为一个空白字符。在LATEX 文件中，每行开始的空白字符将被忽略，而单个的回车符被视为一空格。



#### 注释

当LATEX 在处理源文件时，如果遇到一个百分号字符%，那么LATEX将忽略% 后的该行文本，分行符以及下一行开始的空白字符



#### 结构

```latex
\documentclass{...}  %以如下命令开始，指定文档类别
\usepackage{...}  %引入宏
\begin{document}  %开始文档

\end{document}  %结束文档
```



#### 文档布局

##### 文档类型

```latex
\documentclass[11pt,twoside,a4paper]{article}
```

这条命令指定LATEX 使用论文版式，11 磅大小的字体来排班此文档，并且得到适合打印在A4 纸上的输出结果。



#### 编译出的各类文件

.tex LATEX 或TEX 源文件。可以用latex 处理。

.sty LATEX 宏包文件。可使用命令\usepackage 将其加载到你的LATEX 文
件中。

.dtx 文档化TEX 文件。这也是LATEX 宏包发布的主要格式。通过处理一个
.dtx 文件就可以得到该LATEX 宏包中所包括的宏代码文档。

.ins 为相应的.dtx 文件的安装文件。如果你在网络上下载了一LATEX 宏
包，你通常会发现会有一个.dtx 和一个.ins 文件。使用LATEX 对.ins
文件进行处理，可以从.dtx 文件中提取出宏包。

当你运行LATEX 处理你的源文件时，会得到下列文件：
.dvi 与设备无关文件。这是LATEX 编译运行的主要结果。你可以使用DVI
预览器浏览其内容，或者使用像dvips 这样的应用程序输出到打印
机。

.log 记录了上次编译运行时的详细信息。

toc 存储了所有章节标题。该文件将在下次编译运行时被读入并生成目
录。

.lof 类似.toc 文件，可生成图形目录。

.lot 类似.toc 文件，可生成表格目录。

.aux 另一个用来向下次编译运行传递信息的辅助文件。除了其它信息
外，.aux 文件通常包含交叉引用信息。

.idx 如果你的文件中包含有索引，LATEX 使用此文件存储所有的索引词
条。此文件需要使用makeindex 处理。



#### 页面样式

```latex
\pagestyle{style}  
\thispagestyle{style}  %改变当前页面样式
```



#### 快速检索

使用syntonly 宏包可以让LATEX 快速的检查你的文档：LATEX 浏览你的
文档，仅仅检查语法和所使用的命令是否正确，不会产生DVI 输出。在这
种模式下，LATEX 运行的非常快，可以节省可观的时间。使用方法非常简
单：

```latex
\usepackage{syntonly}
\syntaxonly
```



#### 段行和分页

##### 段落

```latex
\\  %另起一行
\\*  %断行，并且禁止分页
\newpage  %另起一页
```

##### 断字

```latex
\hyphenation{FORTRAN Hy-phen-a-tion}%允许对“hyphenation” 和“Hyphenation” 进行断字，却根本不允许“FORTRAN”, “Fortran” 和“fortran” 进行断字。

\mbox{text}  %保证把几个单词排在同一行上。在任何情况下，这个命令把它的参量排在一起（同一行上）。
```

命令 \\-  在单词中插入一个自主的断字点。它也就成为这个单词中允许
出现的唯一断字点。



#### 特殊符号

```latex
''  %双引号

daughter-in-law, X-rated\\  %连字号
pages 13--67\\  %短破折号
yes---or no? \\  %长破折号
$0$, $1$ and $-1$  %减号

\sim  %波浪号


$30\,^{\circ}$  %30°，\,代表一个小空格


shelf\mbox{}ful  %防止两个ff出现部分重叠


H\^otel, na\"\i ve, \'el\`eve,\\
sm\o rrebr\o d, !`Se\~norita!,\\
Sch\"onbrunner Schlo\ss{}
Stra\ss e %实现对斜线后面的字符的注音
```





#### 使用其他语言

```latex
\usepackage[language]{babel}  %插入语言宏包

```





#### 单词间隔

为了使输出的右边界对齐，LATEX 在单词间插入不等的间隔。在句子的
末尾插入的空间稍多一些，因为这使得文本更具可读性。LATEX 假定句子以
句号、问号或惊叹号结尾。如果句号紧跟一个大写字母，它就不视为句子
的结尾。因为一般在有缩写地方，才出现句号紧跟大写字母的情况。

```latex
~  %也产生一个不能伸长的空格，并且禁止断行
\frenchspacing %能禁止在句号后插入额外的空间，它告诉LATEX 在句号后不要插入比正常字母更多的空间
```





#### 标题，章和节

对于article：

```latex
\section{...}
\subsection{...}
\subsubsection{...}
\paragraph{...}
\subparagraph{...}
```

对于report和book类还有：

```latex
\part{...} 
\chapter{...}
```

LATEX 在文档编译的最后一个循环中，提取节的标题和页码以生成目
录。

```latex
\tableofcontents
```

在其出现的位置插入目录。为了得到正确的目录内容，一个新文档必须编
译两次。有时还要编译三次。届时LATEX 会通知你。



```latex
\maketitle  %出现文档标题（）标题出现在指令之前

%设置标题作者的指令
\title{...} 
\author{...}  %可以输入几个用\and 命令分开的名字。
\date{...}%optional

\footnote{...}  %设置脚注（右上角）
```



#### 字体

```latex
\underline{text}  %下划线

\emph{text}  %强调文本
```



#### 环境

```latex
\begin{aaa}... %可以嵌套环境
	\begin{bbb}...
	\end{bbb}...
\end{aaa}
```

##### Itemize, Enumerate, and Description

itemize 环境用于简单的列表，enumerate 环境用于带序号的列表，description环境用于带描述的列表。

```latex
\flushleft
\begin{enumerate}
\item You can mix the list
environments to your taste:
	\begin{itemize}
	\item But it might start to %（实心黑点） But it might start to look silly.
	look silly.
	\item[-] With a dash. %- With a dash.
	\end{itemize}
\item Therefore remember:
	\begin{description}
	\item[Stupid] things will not%[]内单词被突出
	become smart because they are
	in a list.
	\item[Smart] things, though, can be
	presented beautifully in a list.
	\end{description}
\end{enumerate}
```



##### Flushleft, Flushright, and Center

flushleft 和flushright 环境分别产生靠左排列和靠右排列的段落。center 环境产生居中的文本。如果你不输入命令\\ 指定断行点，LATEX将自行决定。



##### Quote, Quotation, and Verse

quote 环境对重要断语和例子的引用很重要。quotation 环境用于
超过几段的较长引用，因为它对段落进行缩进。verse 环境用于诗歌，在诗歌中断行很重要。在一行的末尾用\\ 断行，在每一段后留一空行。



##### 表格

tabular 环境能用来排印带有水平和铅直表线的漂亮表格。LATEX 自动
确定每一列的宽度。

用一个l 产生左对齐的列，用一个r产生右对齐的列，用一个c 产生居中的列；用p{宽度值width} 产生相应宽度、包含自动断行文本的列；| 产生铅直表线。

在tabular 环境中，用& 跳入下一列，用\\ 开始新的一行，用\hline
插入水平表线。用\cline{j-i} 可添加部分表线，其中j 和i 分别表示表线
的起始列和终止列的序号。

```latex
\begin{tabular}{|r|l|}
\hline
7C0 & hexadecimal \\
3700 & octal \\ \cline{2-2}
11111000000 & binary \\
\hline \hline
1984 & decimal \\
\hline
\end{tabular}
```

![image-20200913194536533](D:\computer science\notes\latex\image-20200913194536533.png)





### 数学公式

#### 在数学模式中输入文本

```latex
\textrm{...} %来输入这些文本。
```



#### 实数

```latex
\mathbf{R}
\mathbb{R}
```

![image-20200913202711842](D:\computer science\notes\LaTex指令.assets\image-20200913202711842.png)

![image-20200913202743091](D:\computer science\notes\LaTex指令.assets\image-20200913202743091.png)



#### 空格

```latex
\quad %一个空格
\qquad %两个空格
```



#### 求导符号

字符' 将生成（prime）



#### 点

```latex
\cdot
```



#### 分数

```latex
\frac{...}{...}
```



#### 文本中插入公式(行内公式)

```latex
$x=a$
```



#### 文本外插入公式(行间公式)

```latex
\[ x=a \]
```



#### 公式内空格

```latex
\quad
```



#### 长公式，对齐

```latex
\[\begin{aligned}
x ={}& a+b+c+{} \\
&d+e+f+g
\end{aligned}\]
```



#### 连等变形，对齐

```latex
\begin{align*}
a &= b+c+d \\
  &= y+z
\end{align*}
```



#### 分段函数

```latex
\[ y= \begin{cases}
-x,\quad x\leq 0 \\
x,\quad x>0
\end{cases} \]
```



#### 排列组合符号

排版二项系数或类似的结构可以使用命令{... \choose ...} 或
{... \atop ...}。第二个命令与第一个命令的输出相同，只是没有括
号。



#### 数学字体大小

这时可以使用\mathrm 来确保字体大小交换机制起作用。但是需要注意的是，\mathrm 只对于较短的项才起作用。

在数学模式中，字体大小用四个命令来设定： \displaystyle (123), \textstyle (123), \scriptstyle (123) and \scriptscriptstyle (123).



#### 粗体

```latex
\boldsymbol{\mu}, \boldsymbol{M}
```





### 定制LATEX

#### 建立新的命令

```latex
\newcommand{name}[num]{definition}

%EX:
\newcommand{\tnss}{The not so Short Introduction to \LaTeXe}
%\tnss命令表示definition的那句话


\newcommand\loves[2]{#1 喜欢 #2}
\newcommand\hatedby[2]{#2 不受 #1 喜欢}

\loves{小猫}{鱼}
\hatedby{小猫}{萝卜干}
%output
%小猫喜欢鱼
%萝卜干不受小猫喜欢
```

第三个参数num 是可选的，用于指定命令所需的参数数目（命令最多可以有9个参数）。如果不给出这个参数，那么新建的命令将不接受任何参数。

LATEX 不允许你用\newcommand 新建一个与原有命令重名的命令。有
一个特殊的命令专门用于处理这种情况：\renewcommand。它使用与命令\newcommand 相同的语法。



#### 建立新的环境

```latex
\newenvironment{name}[num]{before}{after}
```

在参数before 中提供的内容将在被命令包含的文本之前处
理，而在参数after 中提供的内容将恰好在\end{name} 的前面处理。



#### 建立你自己的宏包

```latex
\ProvidesPackage{package name}
```



#### 字体和尺寸

```latex
\textbf{} %加粗
\textit{} %斜体

\large %变大
\small %变小

%以上内容只作用于符号后一个单词或大括号内的内容

%避免大括号
\begin{Large}
This is not true.
But then again, what is these
days \ldots
\end{Large}
```

其他看书



#### 数学字体

```latex
\mathbb{...} %数学加粗
\mathcal{...} %数学花体
```



#### 水平距离

```latex
\hspace{length} %产生一个1.5cm的空白
\hspace{\stretch{n}} %产生一个长度为n的的空白长度
```



#### 垂直距离

```latex
\vspace{length} %在两段之间增加额外距离
```



#### 页面布局