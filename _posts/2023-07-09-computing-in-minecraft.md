---
title: Computing in Minecraft
# author: dxdydz
date: 2023-07-09 16:00:00 -0400
categories: [Computer Science]
tags: [computer architecture, machine code, digital logic]
math: True
pin: False
---

In July of 2010 I was introduced to Minecraft by a friend and he showed me a redstone mechanism he had constructed to operate a door. Although the device itself was quite simple, we were able to see the potential in redstone, although I don't think I realized how far one could go with it at the time. In September of that same year, theinternetftw uploaded a video about a [16-bit arithmetic logic unit](https://www.youtube.com/watch?v=LGkkyKZVzug) that he had constructed. This was the first push towards designing fully functional computer processors inside of Minecraft, an especially impressive feat in light of the fact that redstone was only added to the game two months before as part of the Alpha v1.0.1 update. His early work was inspiring and he also mentioned one of his resources, [The Elements of Computing Systems](https://mitpress.mit.edu/9780262640688/the-elements-of-computing-systems/), which looked like a promising place to start. I ended up getting a copy of this book and I read through the first sections on logic gates, and got the basic idea of the Harvard architecture, then I proceeded to experiment in Logisim and Minecraft until I got my first CPU working.

## Basic logic gates

The fundamental redstone components, other than basic building blocks, are redstone dust and the redstone torch. Dust is used to carry signals and the redstone torch has the ability to invert signals, the simplest device that demostrates this is the NOT gate,

<center><a href="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/NOT.gif"><img src="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/NOT.gif" alt="centered image" height="auto" width="400" title="source: github.com" /></a></center>

which is a logic gate that outputs $0$ when it receives a $1$, and outputs a $1$ when it receives a $0$. Wiring these simple gates together with multiple inputs forms the basis of the most common logic gate designs that could be found in Minecraft Alpha.

### AND gate

The AND gate only outputs a $1$ when both of its inputs are $1\text{s}$.

<center><a href="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/AND.gif"><img src="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/AND.gif" alt="centered image" height="auto" width="400" title="source: github.com" /></a></center>

### XOR gate

The XOR gate (short for exclusive or) will only output a $1$ if only one of its inputs is a $1$.

<center><a href="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/XOR.gif"><img src="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/XOR.gif" alt="centered image" height="auto" width="400" title="source: github.com" /></a></center>

These gates, and others, can be combined in ways that preform calculations and fascilitate the storage of data.

## My early experiments in computing

Unfortnately, not much of my early redstone circuitry has survived to today, only a few small snippets remain. I had more free time to build after the redstone repeater was added in the 1.3 Beta update and I was able to quickly get an ALU (arithmetic logic unit) thrown together.

### ALU 1

The first ALU I constructed was a 4 bit machine which could preform a variety of operations

* addition
* subtraction
* logical AND, OR, and XOR
* invert any output with NOT

<center><a href="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/ALU1.png"><img src="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/ALU1.png" alt="centered image" height="auto" width="400" title="source: github.com" /></a></center>

and had a simple interface that I intended to hook up to other fundamental computer components. This ALU was supposed to be the mathematical heart of my first computer design, but I never finished it as I had moved on to larger projects.

<center><a href="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/interface.png"><img src="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/interface.png" alt="centered image" height="auto" width="400" title="source: github.com" /></a></center>

### Memory and timing

Now that I had the ability to do basic calcualtions, I needed a way to store and retrieve results. The simplest way to do this is by use of an RS NOR latch

<center><a href="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/latch.png"><img src="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/latch.png" alt="centered image" height="auto" width="400" title="source: github.com" /></a></center>

 and I ended up testing the best ways to organize these and settled on a verticle design to make efficient use of rendered space. However, pistons were also released around this time and I ended up using those to store data instead.

 <center><a href="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/tower.png"><img src="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/tower.png" alt="centered image" height="auto" width="400" title="source: github.com" /></a></center>

 In front of the above memory tower is the first program counter I designed. The program counter is responsible for reading lines of the program stored in ROM, and managing the computation cycle. For me this was the most challenging part of a computer to design, as it needs to be efficient and accurate, it must be quick but not too quick, as data takes time to travel through the whole machine, so if it were too fast data would not make it to its destination.

## Second Minecraft computer design

My second design for a Minecraft computer was the first one that I finished assembling and got working. Its ALU had all the basic operations of the previous one, except it was 10-bit instead of 4-bit, and being a complete machine it had additional features,

* conditional jumping
* 10 memory addresses
* 32 lines of ROM to write code in.

 <center><a href="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/comp1.png"><img src="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/comp1.png" alt="centered image" height="auto" width="400" title="source: github.com" /></a></center>

 With a greater render distance on a better (real) computer, I no longer had to stack my memory vertically, which reduced the pain of wiring it up. The main drawback of this redstone computer is that it was extremely slow, I needed something faster.

## C3

My third and final* Minecraft computer is an 8-bit machine and a signifigant improvement on my previous designs in terms of speed, amount of RAM, amount of ROM, ALU functionality, and instruction size.

 <center><a href="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/above.gif"><img src="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/above.gif" alt="centered image" height="auto" width="400" title="source: github.com" /></a></center>

 The above image shows a complete computation cycle in a program that computes Fibonacci numbers (described further below); here is a [labeled image](https://i.imgur.com/lqbnTHk.png) of the machine to give a better idea of what is going on. Another huge upgrade this machine has is a pair of two digit hexadecimal displays instead of a binary readout (which is what my second computer has).

  <center><a href="https://imgur.com/a/aoFG8RC"><img src="https://i.imgur.com/Ot48f53.png" alt="centered image" height="auto" width="400" title="source: imgur.com" /></a></center>

\*I actually ended up making a 4-bit version of this on the XBox 360.

### RAM

The RAM consists of 16 memory addresses, each of which can store one 8-bit number. The memory works by storing information in piston states, which relies on [BUD switches](https://minecraft.fandom.com/wiki/Tutorials/Block_update_detector).

 <center><a href="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/RAM.gif"><img src="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/RAM.gif" alt="centered image" height="auto" width="400" title="source: github.com" /></a></center>

 This image shows writing the number $11101001$ to RAM address 3. This is the second instruction my machine executes in its Fibonacci program. Every time the machine adds two numbers together, it checks to see if the result is greater than or equal to this $11101001$, as this is the largest Fibonacci number the machine can hold before it overflows.

When a redstone block is down a $1$ is being stored, otherwise it is a $0$.

### ALU

The ALU has two memory registers and capable of

* bitwise OR, AND, XOR, and applying NOT to the outputs of these operations
* addition
* bitshifting to the left and to the right
* comparing values in the A and B registers (used in jumping)
* storing constants in a small read only databank

Here two numbers are being added togther. Some chaotic looking flashing can be seen on the right as the carries on the full adders propagate.

 <center><a href="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/ALU.gif"><img src="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/ALU.gif" alt="centered image" height="auto" width="400" title="source: github.com" /></a></center>

### Program counter

The program counter's job is to read through the ROM line by line, and execute jumps for branches in the program. These jumps rely on comparisons of values in the ALU's registers, as mentioned before.

 <center><a href="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/PC.gif"><img src="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/PC.gif" alt="centered image" height="auto" width="400" title="source: github.com" /></a></center>

 In the Fibonacci program, at the end of the computation cycle for ROM line $001111$, the machine checks if the most recent result from the addition step is greater than or equal to $11101001$ (the largest Fibonacci number that can be stored in 8 bits). Here the result was less than the aformentioned number, so it jumps back to line $000011$ and continues its loop.

### ROM

There are 64 lines of program memory available to code in.

<center><a href="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/ROM.gif"><img src="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/ROM.gif" alt="centered image" height="auto" width="400" title="source: imgur.com" /></a></center>

The program is stored as rows of torches in a large grid. Here we see the program advance forward one line of code. The red region is the 'read from' address.
White is the 'write to' address.
And the grey way down at the end are three control bits, responsible for branching and turning the machine off.

### Programs

Here are some examples of what machine code looks like for the C3. More information on how this code operates and how data moves through the computer can be found in the `C3_Documentation` file in the download below.

#### Shutdown the computer on line 2

```
0: 000000 000000 000  do nothing
1: 000000 000000 000  do nothing
2: 000000 000000 111  shutdown
```

#### Sum user input

```
0: 010011 000001 000  in1 to RAM1
1: 010100 000010 000  in2 to RAM2
2: 000001 010001 000  RAM1 to RegA
3: 000010 010010 000  RAM2 to RegB
4: 011000 000011 000  A+B to RAM3
5: 000011 010011 000  RAM3 to display1
6: 000000 000000 111  shutdown
```

#### Comparison program

```
0: 010011 000001 000  in1 to RAM1
1: 010100 000010 000  in2 to RAM2
2: 000001 010001 000  RAM1 to RegA
3: 000010 010010 000  RAM2 to RegB
4: 000111 000101 110  go to ROM#5 if B<=A is true, and if it's false go to ROM#7.
5: 000001 010011 000  RAM1 to display1
6: 000000 000000 111  shutdown
7: 000010 010011 000  RAM2 to display1
8: 000000 000000 111  shutdown
```

#### Fibonacci sequence

```
0:  011110 001111 000  C1 to RAM15
1:  011111 001110 000  C2 to RAM14
2:  001111 010001 000  RAM15 to RegA
3:  010000 010010 000  RAM16 to RegB
4:  011000 010000 000  A+B to RAM16
5:  010000 010100 000  RAM16 to display2
6:  010000 010010 000  RAM16 to RegB
7:  001110 010001 000  RAM14 to RegA
8:  001001 010000 010  A=B? If true go to ROM#16, if false go to ROM#9.
9:  001111 010001 000  RAM15 to RegA
10: 010000 010010 000  RAM16 to RegB
11: 011000 001111 000  A+B to RAM15
12: 001111 010100 000  RAM15 to display2
13: 001111 010001 000  RAM15 to RegA
14: 001110 010010 000  RAM14 to RegB
15: 000011 010000 010  A=B? If true go to ROM#16, if false go to ROM#3.
16: 000000 000000 111  shutdown
```

In order to operate, `constant1` needs to equal $1$ and `constant2` needs to equal $233$.

## C3 download and setup

[download link](https://github.com/VolumeElement/C3-Microprocessor)

The world file is `New World-` and should be run in any Minecraft java version between 1.11.2 and 1.15.2, inclusive. In theory, it can be run on 1.11.2, but the earliest version I could get working was 1.13.2. The computer can't be used in [Minecraft 1.16](https://minecraft.fandom.com/wiki/Java_Edition_1.16#Changes) or any version after that due to the toggleable redstone dust that was implemented. When the world is first loaded, the computer will already be set up to run the Fibonacci program.