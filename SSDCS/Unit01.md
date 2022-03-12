![Logo](Images/Logo.png)
[1](/MyPortfolio/SSDCS/Unit01.html) | [2](/MyPortfolio/SSDCS/Unit02.html) | [3](/MyPortfolio/SSDCS/Unit03.html) | [4](/MyPortfolio/SSDCS/Unit04.html) | [5](/MyPortfolio/SSDCS/Unit05.html) | [6](/MyPortfolio/SSDCS/Unit06.html) | [7](/MyPortfolio/SSDCS/Unit07.html) | [8](/MyPortfolio/SSDCS/Unit08.html) | [9](/MyPortfolio/SSDCS/Unit09.html) | [10](/MyPortfolio/SSDCS/Unit10.html) | [11](/MyPortfolio/SSDCS/Unit11.html) | [12](/MyPortfolio/SSDCS/Unit12.html)

![Logo](Images/Diary.png)
### Week One [una sabbatorum]

**Forum Post**

Buffer Overflow Attack

Before starting this module, I had some experience of buffer overflows both as a developer writing code that uses fixed buffers for variables (C  , C++ & ASM) but also as part of a team that has to patch commercial and internally developed software to mitigate against these flaws. In this post will look at the security flaw of buffer overflows.

Overview

What is a buffer overflow? When A program is run on an operating system the executable of that program and data structures will be held in memory in a very precise and known way The operating system (Windows, Linux, OSX) will call the main method of the code as a function, which then starts the flow for the rest of the program.

A Buffer overflow attack happens when more data than the size of the memory allocated for a variable or data structure is written allowing inputted data to overrun the bounds of the space allocated to store the data and therefore corrupt the heap or stack an attacker can use this flaw by crafting a custom input in the form of Shell Code in order to force the execution of arbitrary code this works by overwriting the values of the EIP (Instruction Pointer) , EBP (Base Pointer)  

![BUFFER1](Images/BUFFER1.png)

**Weekly Skills Matrix New Knowledge Gained**

- [x] 
- [x] 

**Happiness Level**
