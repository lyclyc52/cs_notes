

[toc]









## History

SIMD (single-instruction, multiple-data-stream):单指令多数据结构，一个step分成小部分，不同processor同时执行不同小部分

Ethernet 以太网

Workstations or personal computers networked together became known as LANs (local area networks).

ARPANET, where today Internet is descended from.

Like ARPANET and LANs, the Internet uses packet switching, a way for messages to share lines. The Internet, however, is made up of many different networks across the world that communicate by using a common protocol, TCP/IP (transmission-control protocol/internet protocol).

If the Internet of the 1990s became the Information Superhighway, then Ethernet became the equally important network of local roads to feed it.

time sharing—many different users, each at a terminal, communicating (inputting and outputting) with a single computer all at the same time

In the third generation, these utility programs were refined and put under the direction of the operating system. This group of utility programs, the operating system, and the language translators (assemblers and compilers) became known as systems software.

 

Blaise Pascal, a French mathematician, built and sold gear-driven mechanical machines, which performed whole-number addition and subtraction.

 

in the seventeenth century, a German mathematician, Gottfried Wilhelm von Leibniz, built the first mechanical device designed to do all four whole-number operations: addition, subtraction, multiplication, and division.

 

Charles Babbage designed what he called his analytical engine. His design was too complex for him to build with the technology of his day, so it was never implemented.

 

Ada Lovelace: the first programmer  poet Byron’s daughter

She worked with Charles Babbage, helping to document his designs, translating writings about his work, and developing programs for his machines.

 

Hollerith developed the first electro-mechanical tabulator, which read information from a punched card. His device revolutionized the census taken every ten years in the United States. Dr. Hollerith later formed a company that is known today as IBM.

 

 

The reason is that each storage location within a computer either contains a low-voltage signal or a high-voltage signal. Because each location can have one of two states, it is logical to equate those states to 0 and 1. A low-voltage signal is equated with a 0, and a high-voltage signal is equated with a 1.

 

Modern computers are often 32-bit machines (such as Intel’s Pentium III processor) or 64-bit machines (such as Compaq’s Alpha processors and Intel’s Itanium processor). However, some microprocessors that are used in applications such as pagers are 8-bit machines. The computing machine you are using, whatever it is, is ultimately supported by the binary number system.

 

Word: A group of one or more bytes; the number of bits in a word is the word length of the computer.

half words (2 bytes or 16 bits), full words (4 bytes), and double words (8 bytes).

 

 

 

## **Data representation**

### Data and computers

#### Analog and Digital Information:

The former one is continuous, while the latter is digitized, which means we break it into pieces.

electronic signals are far easier to maintain if they transfer only binary data. An analog signal continually fluctuates in voltage up and down. But a digital signal has only a high or low state, corresponding to the two binary digits.

Digital signals, on the other hand, jump sharply between two extremes. This is referred to as pulse-code modulation (PCM). A digital signal can degrade quite a bit before any information is lost, because any voltage value above a certain threshold is considered a high value, and any value below that threshold is considered a low value. Periodically, a digital signal is reclocked to regain its original shape. As long as it is reclocked before too much degradation occurs, no information is lost. ( Reclock: The act of reasserting an original digital signal before too much degradation occurs)

 

#### Bandwidth: 

The number of bits or bytes that can be transmitted from one place to another in a fixed amount of time

 

#### Lossless compression:

 A technique in which there is no loss of information

 

#### Lossy compression:

 A technique in which there is loss of information

 



### Representing Numeric Data

#### Sign-magnitude representation:

Number representation in which the sign represents the ordering of the number (negative and positive) and the value represents the magnitude

 

#### Number Overflow:

Overflow occurs when the value that we compute cannot fit into the number of bits we have allocated for the result. For example, if each value is stored using eight bits, adding 127 to 3 would overflow:.

01111111 + 00000011 = 10000010

100000010 in our scheme represents 126, not +130. If, however, we were not representing negative numbers, the result would be correct. Overflow is a classic example of the type of problems we encounter by mapping an infinite world onto a finite machine. No matter how many bits we allocate for a number, there is always the potential need to represent a number that doesn’t fit. How overflow problems are handled varies by computer hardware and by the differences in programming languages.

 

#### Radix point: 

The dot that separates the whole part from the fractional part in a real number in any base

 

#### Floating point: 

A representation of a real number that keeps track of the sign, mantissa(小数点后的数), and exponent

a binary floating-point value is defined by the following formula: sign * mantissa * 2exp

 

#### Character set：

A list of the characters and the codes used to represent each one

 

#### The ASCII character set：

originally used seven bits to represent each character, allowing for 128 unique characters.

 

#### Unicode character set

the Unicode character set uses 16 bits per character. Therefore, the Unicode character set can represent 216, or over 65 thousand, characters.

 

### Text compression:

#### Keyword encoding

frequently used words are replaced with a single character.

An extension of keyword encoding is to replace specific patterns of text with special characters. The encoded patterns are generally not complete words, but rather parts of words such as common prefixes and suffixes— “ex”, “ing”, and “tion,” for instance.



#### Run-length encoding (recurrence coding)

a single character may be repeated over and over again in a long sequence. This type of repetition doesn’t generally take place in English text, but often occurs in large data streams, such as DNA sequences.

a sequence of repeated characters is replaced by a flag character, followed by the repeated character

e.g. AAAAAAA is replaced by *A7(“*” is our flag)

 

#### Huffman encoding

using a variable-length binary string to represent a character so that frequently used characters have short codes

The idea behind this approach is that if we use only a few bits to represent characters that appear often and reserve longer bit strings for characters that don’t appear often, the overall size of the document being represented is small.

 

### Representing Audio Information

To represent a sound, we must somehow represent the appropriate sound wave.

To represent audio information on a computer, we must digitize the sound wave, somehow breaking it into discrete, manageable pieces. One way to accomplish this is to actually digitize the analog representation of the sound. That is, take the electric signal that represents the sound wave and represent it as a series of discrete numeric values.

An analog signal varies in voltage continuously. To digitize the signal we periodically measure the voltage of the signal and record the appropriate numeric value. This process is called sampling. Instead of a continuous signal, we end up with a series of numbers representing distinct voltage levels.

To reproduce the sound, the stored voltage values are used to create a new continuous electronic signal. The assumption is that the voltage levels in the original signal changed evenly between one stored voltage value and the next. If enough samples are taken in a short period of time, that assumption is reasonable. But the process of sampling can lose information.

In general, a sampling rate of around 40,000 times per second is enough to create a reasonable sound reproduction.

A vinyl record album(黑胶唱片) is an analog representation of the sound wave. The needle of a record player (turntable) rides up and down in the spiral groove of the album. The rise and fall of the needle is analogous to the voltage changes of the signal that represents the sound.

A compact disc (CD), on the other hand, stores audio information digitally. On the surface of the CD are microscopic pits that represent binary digits. A low intensity laser is pointed at the disc. The laser light reflects strongly if the surface is smooth and reflects poorly if the surface is pitted. A receptor(受体) analyzes the reflection and produces the appropriate string of binary data, which represents the numeric voltage values that were stored when the signal was digitized.

 

#### Audio Formats

There have been several popular formats for audio information, including WAV, AU, AIFF, VQF, and MP3. All of these are based on the storage of voltage values sampled from analog signals, but all format the details of the information in different ways and all use various compression techniques to one extent or another.

For now MP3 is the general favorite.

MP3 is short for MPEG–2, audio layer 3 file. MPEG is an acronym(首字母缩写) for the Moving Picture Experts Group, which is an international committee that develops standards for digital audio and video compression.

MP3 employs both lossy and lossless compression. First it analyzes the frequency spread and compares it to mathematical models of human psychoacoustics (the study of the interrelation between the ear and the brain), then it discards information that can’t be heard by humans. Then the bit stream is compressed using a form of Huffman encoding to achieve additional compression.

 

 

### Representing Images and Graphics

#### Representing colors

Color is often expressed in a computer as an RGB (red-green-blue) value, which is actually three numbers that indicate the relative contribution of each of these three primary colors. If each number in the triple is given on a scale of 0 to 255, then 0 means no contribution of that color, and 255 means full contribution of that color. For example, an RGB value of (255, 255, 0) maximizes the contribution of red and green, and minimizes the contribution of blue, which results in a bright yellow.

The amount of data that is used to represent a color is called the color depth. It is usually expressed in terms of the number of bits that are used to represent its color. HiColor is a term that indicates a 16-bit color depth. Five bits are used for each number in an RGB value and the extra bit is sometimes used to represent transparency. TrueColor indicates a 24-bit color depth. Therefore, each number in an RGB value gets eight bits, which gives the range of 0 to 255 for each. This results in the ability to represent over 16.7 million unique colors.

Keep in mind that 24-bit TrueColor provides more colors than the human eye can distinguish. To reduce file sizes, a technique called indexed color is often used. That is, a particular application such as a browser may support only a certain number of specific colors, creating a palette from which to choose. The palette color closest to the actual color is displayed by the browser.

 

#### Digitized Images and Graphics

Pixels(像素): Individual dots used to represent a picture; stands for picture elements 

Resolution(分辨率): The number of pixels used to represent a picture

Raster-graphics format (光栅图形格式): Storing image information pixel by pixel.here are several popular raster file formats in use, including bitmap (BMP), GIF, and JPEG.

Bitmap File: one of the most straightforward graphic representations. A bitmap file contains the pixel color values of the image from left to right and top to bottom. A bitmap file supports 24-bit TrueColor, though usually the color depth can be specified to reduce the file size. A bitmap file may be compressed using run-length encoding as described earlier in this chapter.

GIF Format (Graphics Interchange Format): developed by CompuServe in 1987, uses indexed color exclusively to reduce file size, which limits the number of available colors to 256. If even fewer colors are required, the color depth can usually be specified to fewer bits. GIF files are best used for graphics and images with few colors, and are therefore considered optimal for line art.

The JPEG Format: designed to exploit the nature of our eyes. Humans are more sensitive to gradual changes of brightness and color over distance than we are to rapid changes. Therefore, the data that the JPEG format stores averages out the color hues over short distances. The JPEG format is considered superior for photographic color images. A fairly complicated compression scheme significantly reduced file sizes.

Bob Bemer: Bemer is best known for his work on the ASCII computer code, which is the standard internal code for 8-bit PCs today.Perhaps Bemer’s most important contribution is the concept of an escape character(转义字符 e.g. \n,\t). The escape character alerts the system processing the characters that the character(s) following the escape character change the standard meaning of the characters to follow.

 

#### Vector Representation of Graphics

A vector graphic is a series of commands that describe a line’s direction, thickness, and color. The file sizes for these formats tend to be small because every pixel does not have to be accounted for. The complexity of the image, such as the number of items in the picture, determines the file size. 

A raster graphic such as a GIF must be encoded multiple times for different sizes and proportions. Vector graphics can be resized mathematically, and these changes can be calculated dynamically as needed. 

However, vector graphics is not good for representing real-world images. JPEG images are far superior in that regard, but vector graphics is good for line art and cartoon-style drawings.

The most popular vector format used on the Web today is called Flash. Flash images are stored in a binary format and require a special editor to create. A new vector format, called Scalable Vector Graphics (SVG), is under development. SVG is expressed in plain text. When the SVG format is finalized, it is likely to make vector graphics a popular approach for web-based imaging.

 

 

### Representing Video

#### Video Codecs 

Video codec:  methods used to shrink the size of a movie

Temporal compression: Movie compression technique based on differences between consecutive frames

A keyframe is chosen as the basis to compare the differences, and its entire image is stored. For consecutive images, only the changes (called delta frames) are stored. Temporal compression is effective in video that changes little from frame to frame, such as a scene that contains little movement.

Spatial compression: it removes redundant information within a frame. This problem is essentially the same as that faced when compressing still images. Spatial video compression often groups pixels into blocks (rectangular areas) that have the same color, such as a portion of a clear blue sky. Instead of storing each pixel, the color and the coordinates of the area are stored instead. This idea is similar to run-length encoding described earlier in this chapter.

 

 

#### Napster:

Nineteen-year-old Shawn had only recently dropped out of his first year at Northeastern University to pursue a solution to the difficulty of downloading and exchanging music over the Net. Shawn wrote source code that wove together a search engine, file sharing, and Internet Relay Chat, making it possible for anyone to easily access and trade music files. Napster was born, and with it a fresh controversy over intellectual property rights and privileges. Napster worked through the direct exchange of files from one computer to another. This peer-to-peer sharing allows users to bypass a central server, access music files from computers located all over the world, and download those files.

 

 

 

## **Gates and Circuits**

### Computers and Electricity

#### Gate 

A device that performs a basic operation on electrical signals, accepting one or more input signals and producing a single output signal. The gates in a computer are sometimes referred to as logic gates because they each perform one logical function.

 

#### Circuit 

A combination of interacting gates designed to accomplish a specific logical function

 

#### George Boole

Boolean algebra is named for its inventor, English mathematician George Boole

 

#### Boolean algebra 

A mathematical notation for expressing two valued logical functions

 

#### Logic diagram 

A graphical representation of a circuit; each type of gate has its own symbol

 

#### Truth table 

A table showing all possible input values and the associated output values

![image-20200413211510302](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200413211510302.png)

A NOT gate inverts its single input value. 

An AND gate produces 1 if both input values are 1. 

An OR gate produces 1 if one or the other or both input values are 1. 

An XOR gate produces 1 if one or the other (but not both) input values are 1. 

A NAND gate produces the opposite results of an AND gate. 

A NOR gate produces the opposite results of an OR gate.

 

 

 

### Constructing Gates

#### Transistor （三极管）

A device that acts either as a wire or a resistor, depending on the voltage level of an input signal. A transistor has three terminals: a source, a base, and an emitter. The emitter is typically connected to a ground wire. An output line is usually connected to the source line. The transistor is either on, producing a high output signal, or off, producing a low output signal. This is determined by the base electrical signal. If the base signal is high (close to a +5 voltage), the source signal is grounded, which turns the transistor off. If the base signal is low (close to a 0 voltage), the source signal stays high, and the transistor is on.

 

 

基极输入高电平，三极管导通，集电极接地，输出是低电平。
基极输入低电平，三极管关断，集电极电压为电源电压，输出是高电平。

 

#### Semiconductor 

Material such as silicon that is neither a good conductor nor insulator

 ![image-20200413211530539](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200413211530539.png)

 

 

### Circuits

#### Combinational 

circuit A circuit whose output is solely determined by its input values 

 

#### Sequential circuit 

A circuit whose output is a function of input values and the current state of the circuit

 

#### Circuit equivalence

The same output for each corresponding input-value combination for two circuits

 

#### DeMorgan’s law

┐(A or B) = ┐A and ┐B

┐(A and B) = ┐A or ┐B

 

#### Adder 

An electronic circuit that performs an addition operation on binary values. Like addition in any base, the result of adding two binary digits could produce a carry value. Recall that 1 + 1 = 10 in base two. 

 

#### Half adder (半加器)

A circuit that computes the sum of two bits and produces the appropriate carry bit

半加器电路是指对两个输入数据位相加，输出一个结果位和进位

carry = AB

sum = A ⊕ B

 

#### Full adder 

A circuit that computes the sum of two bits, taking an input carry bit into account.

the input to the sum must be the carry-in and the sum from adding the two input values.

 ![image-20200413212144824](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200413212144824.png)

 

 

 

#### Multiplexer (often referred to as a mux)（数据选择器）

A circuit that uses a few input control signals to determine which of several input data lines is routed to its output.

e.g. 

 ![image-20200413212201393](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200413212201393.png)

A block diagram of a mux is shown in Figure 4.11. The control lines S0, S1, and S2 determine which of eight other input lines (D0 through D7) are routed to the output (F). The values of the three control lines, taken together, are interpreted as a binary number, which determines which input line to route to the output. Recall from Chapter 2 that three binary digits can represent eight different values: 000, 001, 010, 011, 100, 101, 110, and 111. Note that these values simply count in binary from 0 to 7, which correspond to our output values D0 through D7. So if S0, S1, and S2 are all 0, the input line D0 would be the output from the mux. If S0 is 1, S1 is 0, and S2 is 1, then D5 would be output from the mux. 

 

#### Demultiplexer 

it takes a single input and routes it to one of 2n outputs, depending on the values of the n control lines.

 

 

 

### Circuits as Memory

#### S-R latch

An S-R latch stores a single binary digit (1 or 0). There are several ways an S-R latch circuit could be designed using various kinds of gates. One such circuit, using NAND gates, is pictured in Figure 4.12. The design of this circuit guarantees that the two outputs X and Y are always complements of each other. That is, when X is 0, Y is 1, and vice versa. The value of X at any point in time is considered to be the current state of the circuit. Therefore, if X is 1, the circuit is storing a 1; if X is 0, the circuit is storing a 0. Recall that a NAND gate produces an output of 1 unless both of its input values are 1. Each gate in this circuit has one external input (S or R) and one input coming from the output of the other gate. Suppose the current state of the circuit is storing a 1 (that is, X is 1). And suppose both S and R are 1. Then Y remains 0 and X remains 1. Now suppose that the circuit is currently storing a 0 (X is 0), and that R and S are again 1. Then Y remains 1 and X remains 0. Therefore, no matter which value is currently being stored, if both input values S and R are 1, the circuit keeps its existing state.

 ![image-20200413212415545](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200413212415545.png)

 

### Integrated Circuits

#### Integrated circuit (also chip) 

A piece of silicon on which multiple gates have been embedded different type

 ![image-20200413212443694](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200413212443694.png)

 







## **Computing Components**

###  Stored-Program Concept

#### von Neumann(冯诺依曼) Architecture

the units that process information are separate from the units that store information.

It includes five parts.

1. The memory unit that holds both <u>data and instructions</u>.
2. The arithmetic/logic unit that is capable of performing arithmetic and logic operations on data
3. The input unit that moves data from the outside world into the computer
4. The output unit that moves results from inside the computer to the outside world
5. The control unit that acts as the stage manager to ensure that all the other components act in concert

##### Memory

Memory is a collection of cells, each with a unique physical address. We use the generic word cell here rather than byte or word, because the number of bits in each addressable location, called the memory's addressability, varies from one machine to another.

The ad in the previous section describes a memory of 128,000,000 bytes. This means that each of the 128M bytes is uniquely addressable. Therefore, the addressability of the machine is 8 bits.

The Pentium IV processor mentioned in the ad is a 32-bit machine. This means that the processor can distinguish 2^32 different memory addresses.

We could not know what the content of one address represents. We must apply an interpretation on any bit pattern(位模式，二进制比特“0”与“1”的组合格式) to determine the information it represents.

##### Arithmetic/Logic Unit(ALU)

The arithmetic/logic unit (ALU) is capable of performing basic arithmetic
operations such as adding, subtracting, multiplying, and dividing two
numbers. This unit is also capable of performing logical operations such as
AND, OR, and NOT.

Most modern ALUs have a small amount of special storage units called
registers. These registers contain one word and are used to store information
that is needed again immediately.

##### Input/Output Units

An input unit is a device through which data and programs from the
outside world are entered into the computer. 

An output unit is a device through which results stored in the computer
memory are made available to the outside world.

###### Herman Hollerith:

He designed a method of counting based on cards with holes punched in them and built a tabulating Machine. 

霍列瑞斯首先把穿孔纸带改造成穿孔卡片，以适应人口数据采集的需要。由于每个人的调查数据有若干不同的项目，如性别、籍贯、年龄等等。霍列瑞斯把每个人所有的调查项目依次排列于一张卡片，然后根据调查结果在相应项目的位置上打孔。例如，穿孔卡片“性别”栏目下，有“男”和“女”两个选项；“年龄”栏目下有从“0岁”到“70岁以上”等系列选项，如此等等。统计员可以根据每个调查对象的具体情况，分别在穿孔卡片各栏目相应位置打出小孔。每张卡片都代表着一位公民的个人档案他在机器上安装了一组盛满水银的小杯，穿好孔的卡片就放置在这些水银杯上。卡片上方有几排精心调好的探针，探针连接在电路的一端，水银杯则连接于电路的另一端。与杰卡德提花机穿孔纸带的原理类似：只要某根探针撞到卡片上有孔的位置，便会自动跌落下去，与水银接触接通电流，启动计数装置前进一个刻度。

This method was used for tabulating the census and the cards becameknown as Hollerith cards. Hollerith's electrical tabulating system led to the founding of the company known today as IBM.

##### Control Unit

The control unit is the organizing force in the computer, for it is in charge of the fetch-execute cycle(执行周期).There are two registers in the control unit. The **instruction register (IR)** contains the instruction that is being executed, and the **program counter (PC)** contains the address of the next instruction to be executed.

Because the ALU and the control unit work so closely together, they are often thought of as one unit called the Central Processing Unit, or CPU.

The parts are connected to one another by a collection of wires called a **bus** through which data travels within the computer.

In a personal computer, the components in a von Neumann machine reside physically in a printed circuit board called the motherboard. The motherboard also has connections for attaching other devices to the bus, such as a mouse, a keyboard, or additional storage devices.

#### The Fetch-Execute Cycle

Recall the principal of the von Neumann machine: Data and instructions are stored in memory and treated alike. This means that instructions and data are both addressable. Instructions are stored in contiguous
memory locations; data to be manipulated are stored together in a different part of memory. To start the fetch-execute cycle, the address of the first instruction is loaded into the program counter.

The steps in the processing cycle are:
 1.Fetch the next instruction.

The program counter (PC) contains the address of the next instruction to be executed, so the control unit goes to the address in memory specified in the PC, makes a copy of the contents, and places the copy in the instruction register. At this point the instruction register contains the instruction to be executed. Before going on to the next step in the cycle, the program counter must be updated to hold the address of the next instruction to be executed when the current instruction has been completed. Because the
instructions are stored contiguously in memory, adding 1 to the program counter should put the address of the next instruction into the PC. So the control unit increments the program counter. It is possible that the PC may be changed later by the instruction being executed.



 2.Decode the instruction.

the instruction is decoded into control signals. That is, the logic of the circuitry in the CPU determines which operation is to be executed. This step shows why a computer can only execute instructions that are expressed in its own machine language. The instructions themselves are literally built into the circuits.



 3.Get data if needed.

 4.Execute the instruction.

Execution involves sending signals to the arithmetic/logic unit to carry out the processing.



When the execution is complete, the cycle begins again. If the last instruction was to add a value to the contents of a register, the next instruction probably says to store the results into a place in memory. However, the next instruction might be a control instruction: an instruction that asks a question about the result of the last instruction and perhaps changes the contents of the program counter.



#### RAM and ROM

RAM: Random Access Memory

ROM: Read Only Memory

RAM is memory in which each cell (usually byte) can be directly accessed.Inherent in the idea of being able to access each location is the ability to change the contents of each location.

The contents in locations in ROM cannot be changed. Their contents are permanent and cannot be changed by a stored operation. Placing the bit pattern in ROM is called burning.The bit pattern is burned either at the time the ROM is manufactured or at the time the computer parts are assembled.

RAM does not retain its bit configuration when the power is turned off, but ROM does. Because ROM is stable and cannot be changed, it is used to store the instructions that the computer needs to start itself.

 Main memory usually contains some ROM along with the general purpose RAM. Note that ROM is also random access. It has been suggested that RAM be called RWM for read/write memory, because all main memory is random access, but the term is already in common use.

#### Secondary Storage Devices

Because most of main memory is volatile and limited, it is essential that there be other types of storage devices where programs and data can be stored when they are no longer being processed or the machine is not turned on.

#####  Magnetic Tape

A magnetic tape drive is like a tape recorder and is most often used to back up (make a copy of) the data on a disk in case the disk is ever damaged.

##### Magnetic Disks

![image-20200418170559366](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200418170559366.png)

A read/write head (similar to the record/playback head in a tape recorder) travels across a spinning magnetic disk, retrieving or recording data. Like a compact disk, the heads travel directly to the information desired, and like a tape, the information is stored magnetically.

Disks come in several varieties, but they all use a thin disk made out of magnetic material. The surface of each disk is logically organized into tracks and sectors. Tracks are concentric circles around the surface of the disk. Each track is divided into sectors. Each sector holds a block of information as a continuous sequence of bits.Although the tracks nearer the center look smaller, each track has the same number of
sectors, and each sector has the same number of bits.

The read/write head in a disk drive is positioned on an arm that moves from one track to another. An input/output instruction specifies the track and sector. When the read/write head is over the proper track, it waits until the appropriate sector is beneath the head and the block of information in the sector is then accessed.

Hard disks, the disks on the hard drive that comes with the computer, consist of several disks. Let's call the
individual disks platters. Hard disks consist of several platters attached to a spindle that rotates. Each platter has its own read/write head. All of the tracks that line up under one another are called a cylinder. An address in a hard drive is the cylinder number, the surface number, and the sector. Hard drives rotate at a much higher speed than floppy drives, and the read/write heads donÕt actually touch the surface of the platters but, rather, float above them.

##### Compact Disks(CD)

A CD drive uses a laser to read information stored optically on a plastic disk. Rather than having concentric tracks, there is one track that spirals from the inside out.

CD-DA stands for Compact Disk-Digital Audio. Certain fields in the format are used for timing information. A sector in a CD-DA contains 1/75 of a second of music.

DVD is a newer technology that can store up to 10 GB. DVD, which stands for Digital Versatile Disk, can store multi-media presentations that combine audio and video. As you probably know, movies are now available on DVDs.



#### Non-von Neumann Architectures

##### synchronous(同步的) processing

In this approach, processors often execute the same instructions at the same time; that is, a common program is run at each processor.

![image-20200418180713938](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200418180713938.png)

##### Pipelining(流水线) processing

Multiple processors arranged in tandem, where each contributes one part of an overall computation

 ![image-20200418180733855](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200418180733855.png)

##### Shared memory

Multiple processors share a global memory

![image-20200418181028373](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200418181028373.png)

#### Interpreting Ads

Increased processor speed does not necessarily mean better performance in tasks such as web surfing, e-mail, and word processing as long as the machine has sufficient memory. That is, the more memory you have, the less powerful the processor needs to be. Be aware, however, that the total memory that comes with a computer may not be available to the user. In lower-priced machines, memory
may be siphoned off to power the video processor. For example, in a 64MB shared-memory machine, only 54 to 60MB may be available for programs.

#### Facial Recognition/Privacy

To obtain a faceprint, cameras scan the peaks and valleys of features, called nodal points. The face contains over 80 nodal points, but only 14 to 22 stable nodal points are needed for a successful match.





## **Problem Solving and Algorithm Design**

### Problem Solving

#### Algorithm 

Unambiguous instructions for solving a problem or subproblem in a finite amount of time using a finite amount of data

There are two methodologies that are currently used: top-down design also called functional decomposition) and object-oriented design (OOD). We introduce top-down design first because it mirrors how we solve problems in general.

### Top-Down Design

The top-down design process starts by breaking the problem into a set of subproblems. Then, each subproblem is divided into subproblems. This process continues until each subproblem is defined at a level basic enough so that further decomposition is not necessary.

The process we have used is a top-down testing. We assume that lower modules are correct and verify the main module. Then we take each firstlevel module and repeat the process. Then we take each second-level module and repeat the process. Alternately, we can take one first-level module and verify it and all its submodules before going to the second first-level module. This continues until all the modules have been verified. An alternative approach is bottom-up testing. Bottom-up testing starts by verifying the lowest-level modules first, and working toward the top of the design tree.

This process that we used to verify this design is called desk checking. We sit at a desk with a pencil and paper and work through the design. It is useful to take actual data values and trace what happens to them as we reason about the design. For example, we can take a few names, some with all the information and some with only partial values, and follow the design by hand.
Teams of programmers develop most professional computer programs. A verification method analogous to desk checking that is used by teams is a walk-through. A walk-through is a manual simulation of the design by the team members. They take sample data values and simulate the design using the sample data. Another team-oriented technique is an inspection. In this technique, the design is handed out in advance, and one person (not the designer) reads the design line by line while the others point out errors. These activities are carried out in as nonthreatening a manner as possible. The goal is not to criticize the design or the designer, but to remove defects in the product. Sometimes it is difficult to remove the natural human emotion of pride from this process, but the best teams adopt a policy of egoless(无私的) programming.

### Object-Oriented Design

Object-oriented design is a problem-solving methodology that produces a solution to a problem in
terms of self-contained entities called objects, which are composed of both data and operations that manipulate the data.

#### Object Orientation

An object is a thing or entity(实体) that makes sense within the context of the problem.

A group of similar objects is described by an object class, or class for short.

#### Relationships between Classes

Object classes can relate to one another in three ways. 

The first relationship is that a class can contain an instance of another class as a field. This
relationship is called containment. This is a "part-of" or "contains" relationship.

A second relationship is that a class can inherit from another class. Inheritance is a property of object-oriented design in which classes can inherit data and behavior from other classes. This relationship is an "is-a" relationship. A super class is a class being inherited from; a derived class is a class doing the inheriting.

##### Object-Oriented Design Methodology

There are four stages to the decomposition process that we present.

Brainstorming is the stage in which we make a first pass at determining the classes in the problem. Filtering is the stage in which we go back over the proposed classes determined in the brainstorming stage to see if any can be combined or if any are missing. Each class that survives the filtering stage is recorded on a 5-by-8 card with appropriate headings, called a CRC card. Scenarios is the stage in which the behavior of each class is determined. Because each class is responsible for its own behavior, we call the behaviors responsibilities. In this stage, "what if" questions are explored to be sure that all situations are examined. When all of the responsibilities of each class have been determined, they are recorded on the class's CRC card, along with the names of any other classes with which it must collaborate (interact) to complete its responsibility. Responsibility algorithms, the last stage, is where the algorithms are written for each of the responsibilities outlined on the CRC cards. Now you can see where the term CRC comes from: Class, Responsibility, and Collaboration.

#### Important Threads(线程)

##### Information Hiding

The practice of hiding the details of a module with the goal of controlling access to the details of the module Abstraction

Shouldn't the designer know everything? No. If the designer knows the low-level details of a module, he/she is more likely to base the moduleÕs algorithm on these details. And it is these low-level details that are more likely to change. If they do, then the entire module has to be rewritten.

##### Abstraction

A model of a complex system that includes only the details essential to the viewer

###### Data abstraction 

The separation of the logical view of data from its implementation

###### Procedural abstraction

The separation of the logical view of an action from its implementation

###### Control abstraction

The separation of the logical view of a control structure from its implementation

###### Control structure 

A statement used to alter the normally sequential flow of control

##### Naming Things

When we get to the stage where we translate an algorithm into a program in a language that a computer can execute, we may have to modify the identifiers. Each language has its own rules about forming identifiers. So there is a two-stage process: Data and actions are given names in the algorithm, then these names are translated into identifiers that meet the rules of the computer language. Notice that giving identifiers to information and actions is a form of abstraction.

##### Programming Languages

###### Programming language

A set of rules, symbols, and special words used to construct a program---that is, to express a sequence of instructions for a computer

###### Program 

A sequence of instructions written to perform a specified task

###### Syntax

The formal rules governing the construction of validinstructions

###### Semantics 

The set of rules that gives the meaning of instructions in a language

##### Testing

#### Plagiarism(剽窃)



## **Low-Level Programming Languages**

### Computer Operations

The operational words are programmable, store, retrieve, and process.

The instructions that manipulate data are stored within the machine along with the data. To change what the computer does to the data, we change the instructions.

The instructions that the control unit executes can store data into the memory of the machine, retrieve data from the memory of the machine, and process the data in some way in the arithmetic/logic unit.
The word "process" is very general. At the machine level, the processing involves performing arithmetic and logical operations on data values.

### Levels of Abstraction

### Machine Language

The language made up of binary-coded instructions that is used directly by the computer

The relationship between the processor and the instructions it can carry out is completely integrated. The electronics of the CPU inherently recognize the binary representations of the specific commands. So there is no actual list of commands the computer must consult. The CPU embodies the list in its design.

#### Pep/7: A Virtual Computer

Each type of CPU has its own machine language that it understands.

To solve it, we use virtual computer. It is a hypothetical machine designed to illustrate important features of a real machine.

Pep/7, designed by Stanley Warford, is the virtual machine that we use here. Pep/7 has 32 machine-language instructions. This means that a program for Pep/7 must be a sequence made of up of a combination of these 32 instructions.

Pep/7 has seven registers, four of which we focus on at this point:
1. The program counter (PC), which contains the address of the next
instruction to be executed
2. The instruction register (IR), which contains a copy of the instruction
being executed
3. The index register (X register)
4. The accumulator (A register

The index register and the accumulator are used to hold data and the results of operations.

##### Instruction Format

There are two parts to an instruction: the 8-bit instruction specifier and (optionally) the 16-bit operand(运算对象) specifier. 

The instruction specifier (the first byte of the instruction) indicates what operation is to be carried out, such as "Add a number" to a value already stored in a register, and how to interpret just where the operand is. The operand specifier (the second and third bytes of the instruction) holds either the operand itself or the address of where the operand is. Some instructions do not use the operand specifier.

The instruction specifier is made up of several sections: the operation code, the register specifier, and the addressing-mode specifier.

Instructions that do not have an operand (data to be manipulated) are called unary instructions, and do not have an operand specifier.

##### Pep/7 Simulator

We have a program that behaves just like the Pep/7 virtual machine behaves.



### Assembly Language

A low-level programming language in which a mnemonic(记忆) represents each of the machinelanguage instructions for a particular computer

Program called an assembler reads each of the instructions in mnemonic form and translates it into the machine-language equivalent.

#### Pseudo-Operations

In a machine language program, every instruction is stored in memory and then executed. Beginning with assembly languages, most programming languages have two kinds of instructions: instructions to be translated and instructions to the translating program.

Assembly language allows us to add a comment beside the instruction.



### Other Important Threads

We talked about threads that are important in computing: information hiding, abstraction, naming things, programming languages, and testing.

At the machine-language level, there is very little information hiding going on.





## **High-Level Programming Languages**

### Translation Process

#### Compilers

A program that translates a highlevel language program into machine code

#### Interpreters

 A translating program that translates and executes the statements in sequence. 

 Interpreters can be viewed as simulators(模拟器) for the language in which a program is written. 

##### Java 

was introduced in 1996 and swept the computing community by storm. 

 Java is compiled into a standard machine language called Bytecode.

 A software interpreter called the JVM (Java Virtual Machine) takes the Bytecode program and executes it. 



### Programming Language Paradigms(范例)

That is, the program describes the processing necessary to solve the problem. The imperative(命令的) paradigm is thus characterized by sequential execution of instructions, the use of variables that represent memory locations, and the use of assignment statements that change the values of these variables.

Another model of computation is the functional model, which is based on the mathematical concept of the function. Computation is expressed in terms of the evaluation of functions. The solution to a problem is expressed in terms of function calls. The basic mechanism is the evaluation of functions; there are no variables and no assignment statements. For example, the addition of two values would be expressed this way:(+ 30 40)

Logic programming is a third programming paradigm. Logic programming is based on the principles of symbolic logic. The model is of a set of facts about objects and a set of rules about the relationships among the objects. A program then consists of asking questions about the objects and their relationships, which can be deduced from the facts and the rules.

The fourth paradigm is the object-oriented paradigm. The objectoriented view is one of a world of interacting objects. Each object has responsibility for its own actions. In the imperative paradigm, data objects are considered passive and are acted upon by the program. In the objectoriented paradigm, objects are active. Objects and the code that manipulates them are bundled together, thus making each object responsible for its own manipulation. 



### Functionality of Imperative Languages

#### Strong Typing

 The requirement that only a value of the proper type can be stored into a variable is called strong typing

##### Declarations 

A declaration is a statement that associates an identifier with a variable, an action, or some other entity within the language that can be given a name so that the programmer can refer to that item by name.

 An assignment statement is an action statement (not a declaration) that says to evaluate the expression on the right-hand side of the symbol and store that value into the place named on the left-hand side.

##### Control Structures

A control structure is an instruction that determines the order in which other instructions in a program are executed.

##### Subprogram Statements

We can give a section of code a name and use that name as a statement in another part of the program. The place where the name of the code appears is called the calling unit. 

##### Asynchronous(异步的) Processing

When you use a mouse clicking on the screen, the mouse can be clicked at any time; it is not synchronized with any other instructions. 

### Functionality of Object-Oriented Languages

There are three essential ingredients in an object-oriented language: encapsulation, inheritance, and polymorphism. 

#### Encapsulation

Encapsulation is a language feature that enforces information hiding. 

 It is a feature that hides a module’s implementation in a separate block with a formally specified interface. 

The construct used to provide encapsulation is called a class. Just as the concept of the class dominates object-oriented design, the class concept is the major feature of Java and other object-oriented languages.

In the design (problem-solving) phase, an object is a thing or entity that makes sense within the context of the problem. In the implementation phase, a class is a language construct that is a pattern for an object and provides a mechanism for encapsulating the properties and actions of the object class. To get an object that fits the pattern, we instantiate the class, by using an operator that takes the class name and returns an instance of the class.

#### Inheritance 

#### Polymorphism 

The ability of a language to have duplicate method names in an inheritance hierarchy and to apply the method that is appropriate for the object to which the method is applied

### Hacking





## **Abstract Data Types and Algorithms**

### Abstract Data Types

A data type whose properties (data and operations) are specified independently of any particular implementation

 This view sees the properties represented as specific data fields and behaviors represented as methods implemented in code. This level is concerned with data structures, the implementation of a composite data fields in an abstract data type. 

### Implementation

#### Array-Based Implementations

 An implementation of a container in which the items are stored in an array

If there is no ordering on the item in the container, we call the container unsorted. If there is an ordering, we call the container sorted. 

#### Linked Implementation

An implementation of a container where the items are stored together with information on where the next item can be found



### Lists

#### Basic List Operations

A generic data type (or class) is one in which the operations are specified but the type or class of the objects being manipulated is not. 

 1.create itself  2.insert an item  3.delete an item 4.print itself  5.know the number of items it contains

#### Additional List Operations



### Sorting

#### Selection Sort

1. Find the name that comes first in the alphabet, and write it on a second sheet of paper. 
2. Cross out the name on the original list. 
3. Continue this cycle until all the names on the original list have been crossed out and written onto the second list, at which point the second list is sorted.

#### Bubble Sort

The bubble sort is a selection sort that uses a different scheme for finding the minimum value. Starting with the last list element, we compare successive pairs of elements, swapping whenever the bottom element of the pair is smaller than the one above it.

start with the last one    compare with the one above it -> smaller, swap

​																								   -> larger, start with the one above

#### Quicksort

The Quicksort algorithm, developed by C. A. R. Hoare, is based on the idea that it is faster and easier to sort two small lists than one larger one. 

Divide the list into two parts (compared with a certain thing) until each item becomes the smallest. This strategy is based on recursion—on each attempt to sort the stack of tests, the stack is divided, and then the same approach is used to sort each of the smaller stacks (a smaller case). 

#### Binary Search

##### Sequential search 

Looking for an item from the beginning of the list

##### Binary search 

Looking for an item in an already sorted list by eliminating large portions of the data on each comparison



### Stacks and Queues

#### Stacks

A stack is an abstract data type in which accesses are made at only one end. You can insert an item as the first one and you can remove the first one. 

The insert is called Push and the delete is called Pop. 

#### Queues 

Queues are an abstract data type in which items are entered at one end and removed from the other end. Accountants call this FIFO, for First In First Out.

#### Implementation 

Stacks and queues are often visualized as linked structures. The stack has only one external pointer and it points to the top of the stack. The queue needs two external pointers, one to the front of the queue and one to the rear. See Figure 9.15. Stacks and queues may also be implemented in array-based fashion.

![image-20200510203836352](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200510203836352.png)



### Trees

#### Binary Trees

A container object with a unique starting node called the root , in which each node is capable of having two child nodes, and in which a unique path exists from the root to every other node 

#### Graphs 

A graph is made up of a set of nodes called vertices and a set of lines called edges (or arcs) that connect the nodes. 



### Programming Libraries

Most modern programming languages provide a collection of library classes and coded algorithms available for the programmer to use. 





## **Operating Systems**

####  Roles of an Operating System

A computer generally has one operating system that becomes active and takes control when the system is turned on.  Computer hardware is wired to initially load a small set of system instructions stored in permanent memory (ROM). These instructions load a larger portion of system software from secondary memory, usually a magnetic disk. Eventually all key elements of the operating system software are loaded, start-up programs are executed, the user interface is provided, and the system is ready for use. This activity is often called booting the computer. The term boot comes from the idea of “pulling yourself up by your own bootstraps,” which is essentially what a computer does when it is turned on. 

A computer could have two or more operating systems from which the user chooses when the computer is turned on. This configuration is often called a dual-boot or multi-boot system.

##### Memory, Process, and CPU Management

Multiprogramming is the technique of keeping multiple programs in main memory at the same time, competing for the CPU

An operating system must therefore perform memory management to keep track of what programs are in memory and where in memory they reside. 

 A process is the dynamic entity that represents the program while it is being executed.

 A process might get interrupted during execution, so the operating system performs process management to carefully track the progress of a process and all of its intermediate states. 

Related to the ideas of memory management and process management is the need for CPU scheduling, which determines which process in memory is executed by the CPU at any given point. 



#### Batch Processing 

The operator would organize various jobs from multiple users into batches. A batch would contain a set of jobs that needed the same or similar resources. Therefore, the operator wouldn’t have to reload and prepare the same resources over and over. 



#### Timesharing 

 A system in which CPU time is shared among multiple interactive users at the same time 

##### Virtual machine 

The illusion created by a timesharing system that each user has a dedicated machine

##### Mainframe 

A large, multi-user computer often associated with early timesharing systems 

##### Dumb terminal

A monitor and keyboard that allow the user to access the mainframe computer in early timesharing systems



#### Other OS Factors

Mainframe computers gave rise to minicomputers, which no longer needed dedicated rooms in which to store them. Minicomputers became the basic hardware platform for timesharing systems. Microcomputers, which for the first time relied on a single integrated chip as the CPU, truly fit on an individual’s desk. This gave rise to the idea of a personal computer (PC). 

One final aspect of operating systems is the need to support real-time systems. A real-time system is one that must provide a guaranteed minimum response time to the user.





### Memory Management

A logical address (sometimes called a virtual or relative address) is a value that specifies a generic location, relative to the program but not to the reality of main memory. A physical address is an actual address in the main memory device

When a program is compiled, a reference to an identifier (such as a variable name) is changed to a logical address. When the program is eventually loaded into memory, each logical address finally corresponds to a specific physical address. The mapping of a logical address to a physical address is called address binding. 

#### Single Contiguous Memory Management

Let’s initially keep things simple by assuming that there are only two programs in memory: the operating system and the application program we want to execute.

 We divide main memory up into two sections, one for each. The operating system gets what space it needs, and the program is allocated the rest. 

In this memory management scheme, a logical address is simply an integer value relative to the starting point of the program. That is, logical addresses are created as if the program is loaded at location 0 of main memory. Therefore, to produce a physical address, we add a logical address to the starting address of the program in physical main memory. 

Suppose the program is loaded into memory beginning at address 555555. When a program uses relative address 222222, we know that that actually refers to address 777777 in physical main memory. 

#### Partition Memory Management

There are two strategies that can be used to partition memory: fixed partitions and dynamic partitions. 

When using fixed partitions, main memory is divided into a particular number of partitions. The partitions do not have to be the same size, but their size is fixed when the operating system initially boots. 

When using dynamic partitions, the partitions are created to fit the need of the programs. Main memory is initially viewed as one large empty partition.

When a program becomes active on the CPU, the OS stores the address of the beginning of that program’s partition into the base register. Similarly, the length of the partition is stored in the bounds register. 

When a logical address is referenced, it is first compared to the value in the bounds register to make sure the reference is in that program’s allocated memory space. If it is, the value of the logical address is added to the value in the base register to produce the physical address.

Which partition should we allocate to a new program? There are three general approaches to partition selection:

   1. First fit, in which the program is allocated to the first partition big enough to hold it   

2. Best fit, in which the program is allocated to the smallest partition big enough to hold it  

3. Worst fit, in which the program is allocated to the largest partition big enough to hold it

Worst fit doesn’t make sense to use in fixed partitions because it would waste the larger partitions. First fit or best fit work for fixed partitions. But in dynamic partitions, worst fit often works best because it leaves the largest possible empty partition, which may accommodate another program later on.



#### Paged Memory Management

Main memory is divided into small fixed-size blocks of storage called frames. A process is divided into pages that (for the sake of our discussion) we assume are the same size as a frame. 

When a program is to be executed, the pages of the process are loaded into various unused frames distributed through memory.

To keep track of all this, the operating system maintains a separate page-map table (PMT) for each process in memory; it maps each page to the frame in which it is loaded. 

![image-20200511215259744](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200511215259744.png)

A logical address in a paged memory management system consists of two values, a page and an offset. A logical address is often written as <page, offset>, such as <2, 518>, which means the reference is to 518 bytes into page 2 of the process. 

If process 1 is active, a logical address of <1, 222> would be processed as follows: Page 1 of process 1 is in frame 12; therefore, the corresponding physical address is 12*1024 + 222 or 12510.

An important extension to the idea of paged memory management is the idea of **demand paging**, which takes advantage of the fact that not all parts of a program actually have to be in memory at the same time. 

In demand paging, the pages are brought into memory on demand. That is, when a page is referenced, we first see whether it is in memory already and, if so, complete the access. If not, the page is brought in from secondary memory into an available frame, and then the access is completed. The act of bringing in a page from secondary memory, which often causes another page to be written back to secondary memory, is called a **page swap**.

The demand paging approach gives rise to the idea of virtual memory, the illusion that there are no restrictions on the size of a program (because the entire program is not necessarily in memory at the same time anyway). In all earlier memory management techniques we examined, the entire process had to be brought into memory as a continuous whole. We therefore always had an upper bound on process size. Demand paging removes that restriction.

However, virtual memory comes with lots of overhead during the execution of a program. With the virtual memory approach, we constantly have to swap pages between main and secondary memory. This overhead is acceptable—while one program is waiting for a page to be swapped, another process can take control of the CPU and make progress. Too much page swapping, however, is called thrashing and can seriously degrade system performance.



### Process Management

Another important resource that an operating system must manage is the use of the CPU by individual processes.

#### The Process States 

 The process states are depicted in Figure 10.8.

![image-20200511221942875](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200511221942875.png)

In the new state a process is being created. It may, for instance, be a login process created by a user logging onto a timeshare system, an application process created when a user submits a program for execution, or a system process created by the operating system to accomplish a specific system task. 

A process that has no barriers to its execution is in the ready state. That is, a process in the ready state is not waiting for an event to occur, or for data to be brought in from secondary memory. It’s waiting only for its chance to use the CPU.

 A process in the running state is currently being executed by the CPU. Its instructions are being processed in the fetch-execute cycle. 

A process in the waiting state is currently waiting for resources (other than the CPU). For example, a process in the waiting state may be waiting for a page of its memory to be brought in from secondary memory or for another process to send it a signal that it may continue. 

A process in the terminated state has completed its execution and is no longer an active process. At this point the operating system no longer needs to maintain the information regarding the process.



#### The Process Control Block (PCB,进程控制块)

 The data structure used by the operating system to manage information about a process

When a process moves from one state to another, its corresponding PCB is moved from one state list to another in the operating system.

The PCB stores a variety of information about the process, including the current value of the program counter, which indicates which instruction in the process is to be executed next. 

##### Context switch 

The exchange of register information that occurs when one process is removed from the CPU and another takes its place

The PCB also maintains information about CPU scheduling, such as the priority that a process is given by the operating system. 

Finally, the PCB also includes accounting information, such as account numbers, time limits, and the amount of CPU time used so far.





### CPU Scheduling

CPU scheduling is the act of determining which process in the ready state should be moved to the running state. 

##### Nonpreemptive scheduling 

CPU scheduling that occurs when the currently executing process gives up the CPU voluntarily

##### Preemptive scheduling (剥夺调度)

CPU scheduling that occurs when the operating system decides to favor another process, preempting the currently executing process

##### Turnaround time 

The CPU scheduling metric(衡量标准) that measures the elapsed(消逝的) time between a process’s arrival in the ready state and its ultimate completion



#### First-Come, First-Served

In first-come, first-served (FCFS) scheduling approach, processes are moved to the CPU in the order in which they arrive in the running state.

#### Shortest Job Next

The shortest-job-next (SJN) CPU scheduling algorithm looks at all processes in the ready state and dispatches the one with the smallest service time. 

A **Gantt chart** is a horizontal bar chart developed as a production control tool 

#### Round Robin

Round-robin CPU scheduling distributes the processing time equitably among all ready processes. 

The algorithm establishes a particular time slice (or time quantum), which is the amount of time each process receives before being preempted and returned to the ready state to allow another process its turn.

![image-20200513195327593](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200513195327593.png)











### Seymour Cray

Cray went to work for Engineering Research Associates (ERA), a year-old digital circuit company housed in an old glider factory. He spent time researching computers, listening to lecturers from scholars such as von Neumann, and participating in a design group for the development of two computers. Remington Rand bought ERA, changing the focus from scientific computers to commercial computers, and so Cray joined Control Data Corporation (CDC) as the first technical employee in 1957.He left to form his own company, Cray Research, with the intention of building the world’s highest performance supercomputer. And he did—the CRAY-1. The CRAY-2 and CRAY-3 followed. He also designed, but never built, the CRAY-4. 









##  **File Systems and Directories**

### File Systems

The most prevalent secondary storage device is the magnetic disk drive. This includes both hard drives in the computer’s main box and floppy disks(软磁碟) that are portable and can be moved easily between computers. 

We store information on a disk in files, a mechanism for organizing data on an electronic medium. A **file** is a named collection of related data. A **file system** is the logical view that an operating system provides so that users can manage information as a collection of files. A file system is often organized by grouping files into **directories**.

#### Text and Binary Files

**Text file**   A file that contains characters 

**Binary file**   A file that contains data in a specific format, requiring a special interpretation of its bits

Though text files contain nothing but characters, those characters can represent a variety of information. For example, an operating system may store much of its data as text files, such as information about user accounts. A program written in a high-level language is stored as a text file, which is sometimes referred to as a source file. Any text editor can be used to create, view, and change the contents of a text file, no matter what specific type of information it contains. 

For other information types it is more logical and efficient to represent data by defining a specific binary format and interpretation. Only programs set up to interpret that type of data can be used to view or modify it. For example, there are many types of files that store image information: bitmap, GIF, JPEG, and TIFF, to name a few. 

#### File Types

File names are often separated, usually by a period, into two parts: the main name and the file extension. 

When you see a file in a folder, it is shown with the appropriate icon. 

**File type**    The specific kind of information contained in a file, such as a Java program or a Microsoft Word document 

**File extension**    Part of a file name that indicates the file type

#### File Operations

Most operating systems require that a file be opened before read and write operations are performed on it.

Create a file.
 Delete a file.
Open a file.
Close a file.
Read data from a file.
Write data to a file.
Reposition the current file pointer in a file.
Append data to the end of a file.
Truncate a file (delete its contents).
Rename a file.
Copy a file.

At any point in time, an open file has a current file pointer (an address) indicating the place where the next read or write operation should occur. 

An operating system also provides an operation to change the name of a file, which is called renaming the file. It also provides the ability to create a complete copy of the contents of a file, giving the copy a new name.

#### File Access

The type of access available for a given file is established when the file is created.

**Sequential file access**  The technique in which data in a file is accessed in a linear fashion 

**Direct file access**  The technique in which data in a file is accessed directly, by specifying logical record numbers

#### File Protection

a file protection mechanism determines who can use a file and for what general purpose. 

For example, a file’s protection settings in the Unix operating system is divided into three categories: Owner, Group, and World. Each file is “owned” by a particular user, often the creator of the file. The Owner usually has the strongest permissions regarding the file. A file may have a group name associated with it. A group is simply a list of users. The Group permissions apply to all users in the associated group. You may do this, for instance, for all users who are working on a particular project. Finally, World permissions apply to anyone who has access to the system. Because these permissions give access to the largest number of users, they are usually the most restricted. 





### Directories

A directory, in most operating systems, is represented as a file. The directory file contains data about the other files in the directory. For any given file, the directory contains the file name, the file type, the address on disk where the file is stored, and the current size of the file.

#### Directory Trees

 A structure showing the nested directory organization of the file system.

The directory containing another is usually called the parent directory, and the one inside is called a subdirectory. 

The directory at the highest level is called the root directory.

![image-20200518085126112](C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200518085126112.png)

At any point in time, you can be thought of as working in a particular location (that is, a particular subdirectory) of the file system. This subdirectory is referred to as the current working directory.

#### Path Names 

**Path**  A text designation of the location of a file or subdirectory in a file system 

**Absolute path**  A path that begins at the root and includes all successive subdirectories 

**Relative path**  A path that begins at the current working directory



### Disk Scheduling

The act of deciding which outstanding requests for disk I/O to satisfy first

The most important hardware device used as secondary memory is the magnetic disk drive. File systems stored on these drives must be accessed in an efficient manner. It turns out that transferring data to and from secondary memory is the worst bottleneck in a general computer system.

Because secondary I/O is the slowest aspect of a general computer system, the techniques for accessing information on a disk drive are of crucial importance to our discussion of file systems.

A magnetic disk drive is organized as a stack of platters, where each platter is divided into tracks, and each track into sectors.

The seek time is the time it takes for the heads to reach the appropriate cylinder. The latency is the additional time it takes the platter to rotate into the proper position so that the information can be read or written. Seek time is the more restrictive of these two, and therefore is the primary issue dealt with by the disk-scheduling algorithms.

 A disk may have thousands of cylinders. To keep things simple, let’s also assume a range of 100 cylinders. Suppose at a particular time the following cylinder requests have been made, in this order:
	49, 91, 22, 61, 7, 62, 33, 35
Suppose also, that the read/write heads are currently at cylinder 26. The question is now: To which cylinder should the disk heads move next? Different algorithms produce different answers to that question.

#### First-Come, First-Served Disk Scheduling 

(easy)

#### Shortest-Seek-Time-First Disk Scheduling

The shortest-seek-time-first (SSTF) disk-scheduling algorithm moves the heads the minimum amount it can to satisfy any pending request. This approach could potentially result in the heads changing directions after each request is satisfied.

But it may suffer from starvation. In the SSTF algorithm, it is possible for some requests never to be serviced because requests closer to the read/write heads keep being issued.

#### SCAN Disk Scheduling

A classic example of algorithm analysis in computing comes from the way an elevator is designed to visit floors that have people waiting. An elevator is designed to visit floors that have people waiting. In general, an elevator moves from one extreme to the other (say, the top of the building to the bottom), servicing requests as appropriate. Then it travels from the bottom to the top, servicing those requests.

As the read/write heads move from cylinder 26 toward cylinder 1, they satisfy the requests at cylinders 22 and 7 (in that order). After reaching cylinder 1, the heads reverse direction and move all the way out to the other extreme. Along the way, they satisfy the following requests, in order: 33, 35, 49, 61, 62, and 91. 



### FORTRAN

Formula Translation 它是为科学、工程问题或企事业管理中的那些能够用数学公式表达的问题而设计的，其数值计算的功能较强。

### ALGOL

ALGOrithmic Language 是在计算机发展史上首批清晰定义的高级语言









##  **Information Systems**

### Managing Information

**Information system**  Software that helps the user organize and analyze data

Two of the most popular general application information systems are electronic spreadsheets and database management systems. . A spreadsheet is a convenient tool for basic data analysis based on extensible formulas that define relationships among the data. Database management systems are geared toward large amounts of data that are often searched and organized into appropriate subsections.



### Spreadsheets(电子制表程序)

A spreadsheet is a software application that allows the user to organize and analyze data using a grid of labeled cells.  A cell can contain data or a formula that is used to calculate a value. Data stored in a cell can be text, numbers, or “special” data such as dates. 

#### Spreadsheet Formulas

Formulas can make use of basic arithmetic operations using the standard symbols (+, -, *, and /). They can also make use of spreadsheet functions that are built into the software(e.g. sum). 

Because functions often operate on a set of contiguous cells, spreadsheets provide a convenient way to specify a range of cells. Syntactically, a range is specified with two dots (periods) between the two cell endpoints. 

Others allow the user to set up logical relationships among cells. 

Another dynamic aspect of spreadsheets is the ability to copy values or formulas across a row or down a column. When formulas are copied, the relationships among cells are maintained. Therefore, it becomes easy to set up a whole set of similar calculations. 

##### Daniel Bricklin

Bricklin enrolled in the MBA program at the Harvard Business School, in 1977. While there, he began to envision a program that could manipulate numbers like word processors manipulate text. Such a program would have an immense impact on the business world. He teamed up with his old MIT buddy Bob Franksten and turned the dream into a reality. With Bricklin doing the design and Franksten doing the programming, VisiCalc, the first spreadsheet program, was written. 

#### Circular References

**Circular reference**  A set of formulas that ultimately, and erroneously, rely on each other to compute their results

For instance, if cell B15 contains the formula=D22+D23 and cell D22 contains the formula=B15+B16
there is a circular reference. Cell B15 uses the value in cell D22 for its result, but cell D22 relies on B15 for its result.

#### Spreadsheet Analysis

One reason spreadsheets are so useful is their versatility. 

Another reason spreadsheets are so useful is their dynamic nature. We’ve seen how, if we set up the spreadsheet formulas correctly, changes, additions, and deletions to the data are automatically taken into account by the appropriate calculations. 

The dynamic nature of spreadsheets also provides the powerful ability to do **what-if analysis**( Modifying spreadsheet values that represent assumptions to see how changes in those assumptions affect related data). 



### Database Management Systems

A **database** can simply be defined as a structured set of data. 

A **database management system (DBMS)** is a combination of software and data made up of the:

1. physical database
2. database engine
3. database schema

The database engine software interacts with specialized database languages that allow the user to specify the structure of data; add, modify, and delete data; and **query**( A request for information submitted to a database ) the database to retrieve specific stored data.

The database **schema**( A specification of the logical structure of data in a database) provides the logical view of the data in the database, independent of how it is physically stored. 

#### The Relational Model 

**Relational model**  A database model in which data and the relationships among them are organized into tables

**Table**  A collection of database records

**Record (or object, or entity)**  A collection of related fields that make up a single database entry  

**Field (or attribute)**  A single value in a database record

**Key**  One or more fields of a database record that uniquely identifies it among all other records in the table

<img src="C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200523165824046.png" alt="img src=“url” style=“zoom:50” /" style="zoom:67%;" />

Each row in the table corresponds to a record. Each record in the table is made up of the same fields in which particular values are stored. 

The values stored in key field(s) for each record in a table must be unique. 

#### Relationships

We can create a record to represent a relationship between objects and include attributes about the relationship in the record. Therefore, we can use a table to represent a collection of relationships between objects. 

##### Universal Product Codes

<img src="C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200523180403240.png" alt="image-20200523180403240" style="zoom:50%;" /> 

A UPC symbol is made up of the machine-readable bar code and the corresponding human-readable 12digit UPC number. The first six digits of the UPC number are the manufacturer identification number. The first six digits of the UPC number are the manufacturer identification number . For example, General Mills has a manufacturer ID number of 016000. The next five digits are the item number . Each type of product, and each different packaging of the same product, is assigned a unique item number. The last digit of the UPC code is called a check digit , which allows the scanner determine whether it scanned the number correctly. 

For some products, particularly small ones, a technique has been developed to create UPC numbers that can be shortened by eliminating certain digits (all zeros). In this way, the entire UPC symbol can be reduced in size.

Note that a product’s price is not stored in the UPC number. When a product is scanned at a cash register (more formally called a Point of Sale, or POS), the manufacturer and item numbers are used to look up that item in a database. The database might contain a great deal of product information, including its price. Keeping only basic information in the UPC number makes it easy to change other information such as the price without having to relabel the products. 

#### Structured Query Language 

**Structured Query Language (SQL)** A comprehensive relational database language for data management and queries

 It includes statements that specify database schemas as well as statements that add, modify, and delete database content. It also includes, as its name implies, the ability to query the database to retrieve specific data. 

The original version of SQL was Sequal, developed by IBM in the early ’70s. In 1986, the American National Standards Institute (ANSI) published the SQL standard, the basis for commercial database languages for accessing relational databases.

NOTES: Capital words represent the SQL terminolgies. Italic words are what you need to specify.

##### Queries(查询)

SELECT  *列名称*  FROM *表名称*

SELECT * FROM *表名称* (select all columns)

##### Modifying Database Content

The insert, update, and delete statements in SQL allow the data in a table to be changed.

insert: INSERT INTO *表名称* VALUES (*值1*, *值2*,....)

​            INSERT INTO *table_name* (*列1*, *列2*,...) VALUES (*值1*, *值2*,....)

#### Database Design

A database must be carefully designed from the outset if it is going to fulfill its role. 

One popular technique for designing relational databases is called **entity-relationship (ER) modeling**. Chief among the tools used for ER modeling is the **ER diagram**. An ER diagram captures the important record types, attributes, and relationships in a graphical form. From an ER diagram, a database manager can define the necessary schema and create the appropriate tables to support the database specified by the diagram. e.g.

<img src="C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200524223541233.png" alt="image-20200524223541233" style="zoom:80%;" />

Also note that the relationship connectors are labeled, one side with a 1 and the other side with an M. These designations show the **cardinality constraint** of the relationship. A cardinality constraint puts restrictions on the number of relationships that may exist at one time. There are three general cardinality relationships:

1. one-to-one 2. one-to-many 3. many-to-many







## **Artificial Intelligence**

### Thinking Machines

#### The Turing Test

**Turing test**  A behavioral approach to determining if a computer system is intelligent

A computer that passes the Turing test would demonstrate weak equivalence, meaning that the two systems (human and computer) are equivalent in results (output), but they do not arrive at those results in the same way. Strong equivalence indicates that two systems use the same internal processes to produce results.

New York philanthropist Hugh Loebner organized the first formal instantiation of the Turing test. The competition has been run annually since 1991. 

#### Aspects of AI

1. Knowledge representation—the techniques used to represent knowledge so that a computer system can apply it to intelligent problem solving 

2. Expert systems—computer systems that embody the knowledge of human experts 

3. Neural networks—computer systems that mimic the processing of the human brain 

4. Natural language processing—the challenge of processing languages that humans use to communicate 

5. Robotics—the study of robots



### Knowledge Representation

We want to create a logical view of the data, independent of its actual underlying implementation, so that the data can be processed in specific ways.

#### Semantic Networks 

**Semantic network**  A knowledge representation technique that represents the relationships among objects

e.g.

<img src="C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200527230725586.png" alt="image-20200527230725586" style="zoom:67%;" />

There are essentially no restrictions on the types of relationships that can be modeled in a semantic network. 

#### Search Trees

**Search tree**  A structure that represents alternatives in adversarial situations, such as game playing

You can create a game program that maximizes its chances to win. In some cases it may even be able to guarantee a win. We could use a tree to show all possible solution.

Programmers came up with ways to “prune” the search trees, eliminating paths that no human player would consider reasonable. And still the trees are too large to completely analyze for each move. 

So the question becomes, do we choose a depth-first approach, analyzing selective paths all the way down the tree that hopefully result in successful moves? Or do we choose a breadth-first approach, analyzing all possible paths but only for a short distance down the tree? This issue has been debated among AI programmers for many years, though a breadth-first approach tends to yield the best results. 

In 1997, the computer chess program Deep Blue, developed by IBM using an expert system, defeated world champion Garry Kasparov in a sixgame match. This marked the first time a computer had defeated a human champion at master-level play.



### Expert Systems

**Knowledge-based system**  Software that uses a specific set of information 

**Expert system**  A software system based on the knowledge of human experts

A user consults an expert system when confronted with a particular problem, and the system uses its expertise to advise the user how to proceed.

An expert system uses a set of rules to guide its processing, and therefore is called a **rule-based system**(A software system based on a set of if-then rules). The inference engine is the part of the software that determines how the rules are followed and therefore what conclusions can be drawn.

Real expert systems may have thousands of rules to help analyze a situation. The set of rules presented here do not cover all situations.



### Neural Networks

**Artificial neural network**  A computer representation of knowledge that attempts to mimic the neural networks of the human body

#### Biological Neural Networks

A neuron is a single cell that conducts a chemically-based electronic signal. 

A biological neuron has multiple input tentacles called dendrites and one primary output tentacle called an axon.

Neurons fire, or pulsate(悸动), up to 1,000 times per second, so the pathways along the neural nets are in a constant state of flux. The activity of our brain causes some pathways to strengthen and others to weaken. As we learn new things, new strong neural pathways in our brain are formed.

#### Artificial Neural Networks

Each processing element in an artificial neural net is analogous to a biological neuron.  An element accepts a certain number of input values and produces a single output value of either 0 or 1. These input values come from the output of other elements in the network, so each input value is either 0 or 1. The effective weight of the element is defined to be the sum of the weights multiplied by their respective input values. 

Suppose an artificial neuron accepts three input values: v1, v2, and v3. Associated with each input value is a weight: w1, w2, and w3. The effective weight is therefore:
v1 * w1 + v2 * w2 + v3 * w3

Each element has a numeric threshold value. The element compares the effective weight to the threshold value. If the effective weight exceeds the threshold, the unit produces an output value of 1. If it does not exceed the threshold, it produces an output value of 0. 

This processing closely mirrors the activity of a biological neuron. The input values correspond to the signals passed in by the dendrites. The weight values correspond to the controlling effect of the synapse for each input signal. The computation and use of the threshold value correspond to the neuron producing a strong signal if “enough” of the weighted input signals are strong. 

The output of each element is truly a function of all pieces. If an input signal is 0, its weight is irrelevant. If the input signal is 1, the magnitude of the weight, and whether it is positive or negative, greatly affects the effective weight. 

The pathways established in an artificial neural net are a function of its individual processing elements. And the output of each processing element changes on the basis of the input signals, the weights, and/or the threshold values. But the input signals are really just output signals from other elements. Therefore, we affect the processing of a neural net by changing the weights and threshold value in individual processing elements. 

The process of adjusting the weights and threshold values in a neural net is called training. Often, initially, a neural net is set up with random weights, threshold values, and initial inputs. The results are compared to the desired results and changes are made. This process continues until the desired results are achieved. 

Consider the problem we posed at the beginning of this chapter: Find a cat in a photograph. Suppose a neural net is used to address this problem, using one output value per pixel. Our goal is to produce an output value of 1 for every pixel that contributes to the image of the cat, and to produce a 0 if it does not. The input values for the network could come from some representation of the color of the pixels. We then train the network using multiple pictures containing cats, reinforcing weights and thresholds that lead to the desired (correct) output. 



### Natural Language Processing

 we must first realize that there are three basic types of processing going on during human/computer voice interaction.

1. voice recognition—recognizing human words 
2. natural language comprehension—interpreting human communication 
3. voice synthesis—recreating human speech

#### Voice Synthesis(语音合成)

There are two basic approaches to the solution: dynamic voice generation and recorded speech. 

Human speech has been categorized into specific sound units called **phonemes**(The set of fundamental sounds made in any given natural language). After selecting the appropriate phonemes, the computer may modify the pitch of the phoneme based on the context in which it is used. Finally, the phonemes are combined to form individual words. The sounds themselves are produced electronically, designed to mimic the way a human vocal track produces the sounds. 

The challenges to this approach include the fact that the way we pronounce words varies greatly among humans, and the rules governing how letters contribute to the sound of a word are not consistent. Dynamic voice-generation systems often sound mechanical and stilted(不自然的), though usually the words are recognizable. 

The other approach to voice synthesis is to play digital recordings of a human voice saying specific words. Sentences are constructed by playing the appropriate words in the appropriate order. Sometimes common phrases or groups of words that are always used together are recorded as one entity.

Note that each word or phrase needed must be recorded separately. Furthermore, since words are pronounced differently in different contexts, some words may have to be recorded multiple times. For example, a word at the end of a question rises in pitch compared to its use in the middle of a sentence. As the need for flexibility increases, recorded solutions become problematic. 

#### Voice Recognition 

First, the sounds that each person makes when speaking are unique. 



### LISP 

LISP ( LIS t P rocessor) is generally regarded as the programming language for AI. LISP’s essential data structure is an ordered sequence of elements called a list. The elements may be indivisible entities called “atoms” (functions, names, or numbers) or they may be other lists. 

LISP programs rely on recursion rather than looping. Scheme, a LISP dialect, is used as an introductory programming language at some universities. LISP and its dialects belong to the functional paradigm of languages.



### Herbert A. Simon

In 1955, Dr. Simon, Allen Newell, and J. C. Shaw (their programmer) created Logic Theorist, a program that could discover geometric theorem proofs. At about the same time, Simon was working with E. A. Feigenbaum on EPAM, a program that modeled their theory of human perception and memory. These **programs and the subsequent series of papers on the simulation of human thinking, problem solving, and verbal learning marked the beginning of the field of Artificial Intelligence. In 1988, Simon and Newell received the Turing Award of the Association for Computing Machinery for their work in human problem solving.** 









## **Networks**

### Networking

A **computer network** is a collection of computing devices that are connected in various ways in order to communicate and share resources. 

**Node(or Host)** Any addressable device attached to a network 

**Data transfer rate (also bandwidth)** The speed with which data is moved from one place to another on a network

**Protocol** A set of rules that defines how data is formatted and processed on a network

**Client/server model** A distributed approach in which a client makes requests of a server and the server responds 

#### Types of Networks

**Local-area network (LAN)** A network connecting a small number of nodes in a close geographic area

 A **ring topology** connects all nodes in a closed loop on which messages travel in one direction. The nodes of a ring network pass along messages until they reach their destination. A **star topology** centers around one node to which all others are connected and through which all messages are sent. A star network puts a huge burden on the central node; if it is not working, communication on the network is not possible. In a **bus topology**, all nodes are connected to a single communication line that carries messages in both directions. The nodes on the bus check any message sent on the bus, but ignore any that are not addressed to them. A bus technology called **Ethernet** has become the industry standard for local-area networks. 

A **wide-area network (WAN)** connects two or more local-area networks over a potentially large geographic distance. Often one particular node on a LAN is set up to serve as a gateway to handle all communication going between that LAN and other networks. 

Recently, the term **metropolitan-area network (MAN)** has been adopted to refer to the communication infrastructures that have been developed in and around large cities. 

#### Internet Connections

**Internet backbone** A set of high-speed networks carrying Internet traffic
**Internet service provider (ISP)** A company providing access to the Internet

 The three most popular techniques for home connections are a phone modem, a digital subscriber line (DSL), or a cable modem. 

A **phone modem** converts computer data into an analog audio signal for transfer over a telephone line, and then a modem at the destination converts it back again into data. To use a phone modem, you must first establish a telephone connection between your home computer and one that is permanently connected to the Internet.

 A **digital subscriber line** (DSL) uses regular copper phone lines to transfer digital data to and from the phone company’s central office. You must be within a certain distance of special equipment or else the signal degrades.

A third option for home connections is a **cable modem**. In this approach, the data is transferred on the same line that your cable TV signals come in on. The signal deteriorates(恶化) if too many people in the neighborhood have the service.

Both DSL connections and cable modems fall under the category of **broadband** connections, which generally mean speeds faster than 128 bits per second. 

For both DSL and cable modems, the speed for downloads (getting data from the Internet to your home computer) may not be the same as uploads (sending data from your home computer to the Internet). 

#### Packet Switching

To improve the efficiency of transferring information over a shared communication line, messages are divided into fixed-sized, numbered **packets**.  The packets are sent over the network individually to their destination, where they are collected and reassembled into the original message. This approach is referred to as **packet switching**. 

The packets of a message may take different routes on their way to the final destination. 

A packet may make several intermediate hops between computers on various networks before it reaches its final destination. Network devices called **routers** are used to direct packets between networks. 

If a communication line spans a long distance, such as across an ocean, a device called a **repeater** is installed periodically along the line to strengthen and propagate(传播) the signal. 







### Open Systems and Protocols

#### Open Systems

 We needed a way for computing systems made by different vendors to communicate. 

**Open system** A system that is based on a common model of network architecture and an accompanying suite of protocols

The International Organization for Standardization (ISO) established the **Open Systems Interconnection (OSI) Reference Model** to facilitate the development of network technologies. It defines a series of layers of network interaction

<img src="C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200601005606664.png" alt="image-20200601005606664" style="zoom:50%;" />Each layer deals with a particular aspect of network communication. 

#### Network Protocols 

Following the general concepts of the OSI Reference Model, network protocols are layered such that each one relies on the protocols that underlie it.This layering is sometimes referred to as a **protocol stack**. The layered approach allows new protocols to be developed without abandoning fundamental aspects of lower levels.

<img src="C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200601010151962.png" alt="image-20200601010151962" style="zoom:80%;" />

#### TCP/IP 

TCP stands for Transmission Control Protocol and IP stands for Internet Protocol.

IP software deals with the routing of packets through the maze of interconnected networks to their final destination. TCP software breaks messages into packets, hands them off to the IP software for delivery, and then orders and reassembles the packets at their destination.  TCP software also deals with any errors that occur, such as if a packet never arrives at the destination. 

**UDP** stands for **User Datagram Protocol**. It is an alternative to TCP. That is, UDP software basically plays the same role as TCP software. The main difference is that TCP is highly reliable, at the cost of decreased performance, while UDP is less reliable, but generally faster. 

An IP program called **ping** can be used to test the reachability of network designations. Ping officially stands for Packet InterNet Groper.

Another TCP/IP utility program called **traceroute** shows the route that a packet takes to arrive at a particular destination node. 

#### High-Level Protocols

Other protocols build on the foundation established by the TCP/IP protocol suite.

-  Simple Mail Transfer Protocol (SMTP)—A protocol used to specify the transfer of electronic mail 

- File Transfer Protocol (FTP)—A protocol that allows a user on one computer to transfer files to and from another computer 

-  Telnet—A protocol used to log into a computer system from a remote computer. If you have an account on a particular computerthat allows telnet connections, you can run a program that uses the telnet protocol to connect and log in to that computer as if you were seated in front of it.

- Hyper Text Transfer Protocol (HTTP)—A protocol defining the exchange of World Wide Web documents, which are typically written using the Hyper Text Markup Language (HTML). HTML is discussed in more detail in the next chapter.

These protocols all build on TCP. Some high-level protocols have also been defined that build on top of UDP in order to capitalize on the speed it provides. But because UDP does not provide the reliability that TCP does, UDP protocols are less popular.

Several high-level protocols have been assigned a particular port number. A **port** is a numeric designation that corresponds to a particular high-level protocol

#### MIME Types

Related to the idea of network protocols and standardization is the concept of a file’s **MIME type**. MIME stands for Multipurpose Internet Mail Extension.

Although MIME types do not define a network protocol, they define a standard for attaching or including multimedia or otherwise specially formatted data with other documents, such as e-mail. 

Based on a document’s MIME type, an application program can decide how to deal with the data it is given. 

#### Firewalls

A **firewall** is a machine and its software that serve as a special gateway to a network, protecting it from inappropriate access. 

A firewall enforces an **organization’s access control policy** (A set of rules established by an organization that specify what types of network communication are permitted and denied). 

The system administrators of an organization set up a firewall for their LAN that permits “acceptable” types of communication and denies other types.



### Network Addresses

**Hostname** A name made up of words separated by dots that uniquely identifies a computer on the Internet; each hostname corresponds to a particular IP address 

**IP address** An address made up of four numeric values separated by dots that uniquely identifies a computer on the Internet

An IP address can be split into a **network address**, which specifies a specific network, and a **host number**, which specifies a particular machine in that network. How the IP address is split up depends on what network “class” it represents. The classes of networks (A, B, and C) provide for networks of various sizes. 

The entire Internet protocol is based on a 32-bit IP address. If the use of Internet-ready devices continues to grow, we will eventually run out of reasonable address space to use.

#### Domain Name System

A hostname consists of the computer name followed by the **domain name**.

A domain name is separated into two or more sections that specify the organization, and possibly a subset of an organization, of which the computer is a part.

The very last section of the domain is called its **top-level domain (TLD) name**. 

<img src="C:\Users\jack\AppData\Roaming\Typora\typora-user-images\image-20200602165650792.png" alt="image-20200602165650792" style="zoom:67%;" />

Initially, anyone or any organization could register a domain name for their own use as long as that name hadn’t already been taken. 

The **domain name system** (DNS) is chiefly used to translate hostnames into numeric IP addresses. 

**Domain name** server A computer that attempts to translate a hostname into an IP address

When you specify a hostname in a browser window or e-mail address, the browser or e-mail software sends a request to a nearby domain name server. If that server can resolve the hostname, it does so. If not, that server asks another domain name server. If that second server can’t resolve it, the request continues to propagate. Ultimately, the request finally reaches a server that can resolve the name, or the request expires because it took too much time to resolve.









##  **The World Wide Web**

### Spinning the Web

Compared to the Internet, the World Wide Web (or simply the Web) is a relatively new idea.

A Web address is the core part of a **Uniform Resource Locator**, or URL, which uniquely identifies the page you want out of all of the pages stored anywhere in the world. 



### HTML

Web pages are created (or built) using a language called the **Hypertext Markup Language**, or **HTML**. 

The term **markup language** comes from the fact that the primary elements of the language take the form of **tags** that we insert into a document to annotate the information stored there. 



### Interactive Web Pages

#### Java Applets

A Java applet is a program that is designed to be embedded into an HTML document and transferred over the Web to someone who wants to run the program.

When a Web user references the page containing this tag, the applet program is sent along with any text, images, and other data that the page contains. In the case of an applet, the browser has a built-in interpreter that executes the applet, allowing the user to interact with it. Thousands of Java applets are out on the Web, and most browsers are set up to execute them.

The Java language has a carefully constructed security model. An applet, for instance, cannot access any local files or change any system settings. 

#### Java Server Pages

A Java Server Page, or JSP, is a Web page that has **JSP scriptlets** embedded in them.  A scriptlet is a small piece of executable code intertwined among regular HTML content. 

Note that JSPs are executed on the server side where the Web page resides. They help dynamically define the content of a Web page before it is shipped to the user. By the time it arrives at your computer, all active processing has taken place, producing a static (though dynamically created) Web page.

JSPs are particularly good for coordinating the interaction between a Web page and an underlying database. 



### XML

The Extensible Markup Language, or XML, allows the creator of a document to describe its contents by defining his or her own set of tags. 

XML is a metalanguage. Metalanguage is the word language with the prefix meta, which means “beyond” or “more comprehensive.” A metalanguage is a language that goes beyond a normal language by allowing us to speak precisely about that language.  It is a language for talking about, or defining, other languages. 

A metalanguage called the Standard Generalized Markup Language, or SGML, was used by Tim Berners-Lee to define HTML.  XML is a simplified version of SGML and is used to define other markup languages. XML has taken the Web in a new direction. It does not replace HTML; it enriches it.

The first line of the document indicates the version of XML that is used. The second line indicates the file that contains the Document Type Definition (DTD) for the document. The DTD is a specification of the organization of the document. 

XML represents a standard format for organizing data without tying it to any particular type of output. A related technology called the Extensible Stylesheet Language (or XSL) can be used to transform an XML document into another format suitable for a particular user. 

 For example, an XSL document can be defined that specifies the transformation of an XML document into an HTML document so that it can be viewed on the Web. Another XSL document can be defined to transform the same XML document into a Microsoft Word document, or into a format suitable for a Personal Data Assistant such as a Palm Pilot, or even into a format that can be used by a voice synthesizer. 









## Limitations of Computing

### hardware

#### Limits on Arithmetic

##### Integer Numbers

The hardware of a particular machine determines the limits of the numbers, both real and integer, that can be represented. There are software solutions, however, that allow programs to overcome these limitations. 

##### Real Number

**Representational (round-off) error**  An arithmetic error caused by the fact that the precision of the result of an arithmetic operation is greater than the precision of our machine

**Underflow** The condition that occurs when the results of a calculation are too small to represent in a given machine 

**Overflow** The condition that occurs when the results of a calculation are too large to represent in a given machine

**Cancellation error** A loss of accuracy during addition or subtraction of numbers of widely differing sizes, due to limits of precision

##### Limits on Components

Hardware failures do occur: The best solution is preventive maintenance. In computing this means periodic tests to detect problems and replacement of worn parts. 

Preventive maintenance also means that the physical environment in which a computer is housed is appropriate. Large mainframe computers often require air conditioned, dust-free rooms. PCs should not be set up under leakprone(容易泄露) plumbing. 

#### Limits on Communications 

##### Parity Bits (校验位)

A parity bit is an extra bit that is associated with each byte in the hardware that uses the scheme. This bit is used to ensure that the number of 1 bits in a 9-bit value (byte plus parity bit) is odd (or even) across all bytes. 

Odd parity requires the number of 1s in a byte plus parity bit to be odd. For example, if a byte contains the pattern 11001100, the parity bit would be 1, thus giving an odd number of 1s. If the pattern were 11110001, the parity bit would be 0, giving an odd number of 1s. 

##### Check Digits

A software variation of the same scheme is to sum the individual digits of a number, and then store the unit’s digit of that sum with the number. For example, given the number 34376, the sum of the digits is 23, so the number would be stored as 34376–3.

##### Error-Correcting Codes

If enough information about a byte or number is kept, it is possible to deduce what an incorrect bit or digit must be. The ultimate redundancy would be to keep two separate copies of every value that is stored.



### Software

#### Complexity of Software

#### Current Approaches to Software Quality

Software requirements are broad, but precise, statements outlining what is to be provided by the software product. Software specifications are a detailed description of the function, inputs, processing, outputs, and special features of a software product. The specifications tell what the program does, but not how it does it. 

Teams of programmers produce large software products. Two verification techniques effectively used by programming teams are design or code walk-throughs and inspections. 

In a walk-through, the team performs a manual simulation of the design or program with sample test inputs, keeping track of the program’s data by hand on paper or a blackboard.

At an inspection, a reader (never the program’s author) goes through the requirements, design, or code line by line.

##### Formal Verification

The verification of program correctness, independent of data testing, is an important area of theoretical computer science research. The goal of this research is to establish a method for proving programs that is analogous to the method for proving theorems in geometry. A major focus of verification research is the attempt to build automated program provers—verifiable programs that verify other programs. 

##### Open Source Movement

With the advent of the Internet, programmers from all over the world can collaborate at almost no cost. A simple version of a software product can be made available on the Internet.  A “benevolent dictator” who keeps track of what is going on governs most open-source projects. If a change or improvement passes the peer review of fellow developers and gets incorporated in the next version, it is a great coup.

#### Notorious Software Errors

##### 

### Problems

#### Comparing Algorithms

##### Comparing Algorithms

(learned in comp3711H)

##### Halting Problem(停机问题)

**Halting problem** The unsolvable problem of determining whether any program will eventually stop given particular input