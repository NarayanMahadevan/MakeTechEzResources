# Get On To C++

## Purpose
#  
The purpose of this **Get On To C++** tutorials is to help you learn the essentials 
of C++ programming. Mainly by writing and compiling lot of C++ programs than reading lot of theory. Its learning C++ by practice. This tutorial is different from other tutorials because of the following

1. Learning and being a **Confident C++ programmer** is a simple **18 Step Process** which can be completed in flat **2 - 4 weeks** time.

2. Every Step introduces concepts and demonstrates the concept with a **sample code**. This sample code when put together develops into a deliverable live project.

3. We encourage you to cut and paste this sample code into youe editor. All the sample code combines into one **C++ Program** which you can run and execute.

2. Each step results into one realistic C++ program that you have built, compiled and executed.

3. The emphasis of Get On Series is on **Programming** and learning the language rather than reading a lot of theories.

4. Finally as you go through the step this will lead to a **C++ Project** that reads information from a file describing a railroad train, computes the load-bearing volume of each box car and tank car using formulas drawn from descriptions of boxes and cylinders, and displays a car-by-car report.   

5. Whats most **Important** is in the end you will be a **Confident Developer of C++ Language having written some 20+ complex real-world C++ programs.**

## Certification Program
#  
Certification Program (comming soon) is a paid program and serves multiple purposes

- Certfies you as a **Developer of C++** 
- The certification program will ensure that for every step you have written the sample program and the practice program and that the C++ program is executed and working correctly.
- For every step once the program is written successfully, you will be required to answer questions before you can proceed to the next step.
- You will follow the same process for each of the 18 steps to finally build up a Certified C++ Project. The Scores from the Questionnaire on each step will be combined to give you a final score
- Once you are Certified Developer of C++, based on your score, you can select 5 companies of your choice who are in lookout for C++ Developers and **Apply for Job**. 
- This is a recognized **Certification Program** by the industry and your certification will give the company confidence on your programming skills.

## Inroduction
#  
Before we Get On to C++ and start writing code, following sections are important for you to go through quickly so that you have the necessary understanding and development environment to get started. 

1. [**Setup C++ Environment**](#setup) 
2. [**Overview of C++**](#overview)
3. [**Overview of Get On To C++**](#steps_overview)
4. [**Helloworld C++ Program**](#helloworld)
5. [**Compile and Run Helloworld Program**](#execute)

<a name="setup"/></a>
## Setup C++ Environment
#  
Before you start programming in C++, it is important you have the environment to 

1. Type the C++ program i.e. Text Editor and 
2. The compiler to compile and run the C++ Program 

<a name="editor"/></a>
###Text Editor
#  
This will be used to type your program. Examples of few editors include Windows Notepad, OS Edit command, Brief, Epsilon, EMACS, and vim or vi. 

Our recomendation is [**gedit**](https://projects.gnome.org/gedit/) from GNOME. Its a free software. Linux fans will already be familiar with the world of GNOME but gedit has brought it to a wider audience by providing the default GNOME editor on Windows and Mac. This can be **downloaded** from <http://gedit.en.softonic.com>. The advantages are:

* One Editor for multiple OS Environment
* Wide range of languages supported by Gnome include C, C++, Java, HTML, XML, Python and Perl. 

###C++ Compiler
#  
This is actual C++ compiler which will be used to compile source code into final executable program.

Most C++ compilers don't care what extension is given to the C++ program and many will use .cpp by default

Most frequently used and free available compiler is [**GNU C/C++ compiler**](http://gcc.gnu.org). 

####Installing GNU C++ Compiler
  
#####Unix/Linux Installation

For Linux or Unix to check if GCC is installed, enter the following command from the command line:

	$ g++ -v

If GCC is installed proper message with version number will be displayed. Else command not found will be displayed. If GCC is not installed, then install it from <http://gcc.gnu.org/install/>

#####Mac OSX Installation

The easiest way to obtain GCC is to download the Xcode development environment from Apple's web site and follow the simple installation instructions.

Xcode is currently available at <http://developer.apple.com/technologies/tools/>.

The article [How To Install Gcc Compiler On Mac OS X](http://www.mkyong.com/mac/how-to-install-gcc-compiler-on-mac-os-x/) provides a good walkthrough to install GCC on Mac 

#####Windows Installation

To install GCC for Windows install [**MinGW**](http://www.mingw.org), and follow the link to the MinGW download page. Download the latest version of the MinGW installation program.

While installing MinWG, at a minimum, install gcc-core, gcc-g++, binutils, and the MinGW runtime. Then add the bin subdirectory of MinGW installation to PATH environment variable so that gcc, g++, etc compiler can be run from the Windows command line.

<a name="overview"/></a>
## Overview of C++
#  
The C++ programming language is built on C as indicated by increment operator ++. C++ is an Object Oriented Programming Language. Just like C, C++ built-in data types are char, short, int, long, float, double, etc. Further C++ encourges building your own data type and data type heirarchies to describe effectively the real-world problems.  

So C++ encourages you to think in terms of Objects which is associated with the user defined data type stored in a chunck of memory. So essentially C++ is made up of

1. **Class** - This is essentially a User Defined Data Type. e.g. We can define a class called Dog which is essentially an Animal. We can describe Dog by its Color, Breed, Name, etc as well as Dogs behaviour by Barking, Wagging, Eating, etc.
2. **Object** - This is an instance of a Class having a chunck of memory. So taking the same e.g. of Dog Class - Dog with Name - Slash, Breed - Labrador, Color - White is an Object with proper value for all the attributes describing the Dog.
3. **Methods** - This are basically behaviours or actions defined in the class. So taking the example of Dog, the behaviours are Barking, Wagging, Eating, etc.
4. **Variables** - Variables describes the attributes of class. So for Dog, the attributes are Color, Breed, Name, etc. 

So C++ as an Object Oriented Language supports

1. **Abstraction** - This can be Data Abstraction or Method Abstraction which are hiding and showing the necessary attributes and behaviours of the class.
2. **Encapsulation** - Encapsulation is placing the data and the functions that work on that data in the same place. As you can see the example of Dog - the attributes and behaviours of the Dog are defined in the Class
3. **Inheritance** - Helps in code re-usability. As the name suggests Inheritance is the process of forming a new class from an existing class. So we could have Animal as the Base Class or Parent Class and Dog inheriting from the Animal.
4. **Polymorphism** - Poly means many so C++ allows users to define the same behavior many time with different method parameters. So for e.g. in Dog class, as we know Dog barks differently at different times based on Hunger, excitement, On seeing Strangers, etc. Thus we could define same method Barking for different scenarios. 
5. **Overloading** - This is similar to Polymorphism where in Operator or Function is overloaded.

<a name="steps_overview"/></a>
## Overview of Get On To C++
#  
Get On To C++ is divided into parts essentially 18 steps. Each step introduces a concept with a sample program to understand the concept. Get On To C++ focusses on understanding concepts through programming compared then lot of theory.

1.  **Step 1**   -> Get On To C++ **C++ Basics**
2.  **Step 2**   -> Get On To C++ **Classes and Member Functions**
3.  **Step 3**   -> Get On To C++ **Member Veriables & Assignments**
4.  **Step 4**   -> Get On To C++ **Inheritance and Class Heirarchies**
5.  **Step 5**   -> Get On To C++ **Loops and Conditional Expressions**
6.  **Step 6**   -> Get On To C++ **Function Blocks and Recursive Functions**
7.  **Step 7**   -> Get On To C++ **Arrays**
8.  **Step 8**   -> Get On To C++ **Input & Output File Streams** 
9.  **Step 9**   -> Get On To C++ **Objects and Pointers**
10. **Step 10**  -> Get On To C++ **Interfaces and Polymorphism**
11. **Step 11**  -> Get On To C++ **Data Abstraction and Encapsulation**  
12. **Step 12**  -> Get On To C++ **Call By Reference**  
13. **Step 13**  -> Get On To C++ **Overloading**  
14. **Step 14**  -> Get On To C++ **Strings**  
15. **Step 15**  -> Get On To C++ **Copy Constructors and Destructors**  
16. **Step 16**  -> Get On To C++ **Multi-File Programs**  
17. **Step 17**  -> Get On To C++ **Linked List**  
18. **Step 18**  -> Get On To C++ **Templates**  

Through all this steps the program is building a simple but realistic live project of a Railroad Train. The program reads information from a file describing a railroad train, computes the load-bearing volume of each box car and tank car using formulas drawn from descriptions of boxes and cylinders, and displays a car-by-car report. 

<a name="helloworld"/></a>
## Helloworld C++ Program
#  
Let us look at a simple code that would print the words Hello World on the console.

	//
	//  hello.cpp
	//
	//  Created by MakeTechEz on 18/08/13.
	//  Copyright (c) 2013 MakeTechEz. All rights reserved.
	//
	
	// Uses the header iostream to read and write to the command line
	#include <iostream>
	
	// Tells the Compiler to use std namespace
	using namespace std;

	// main() is where program execution begins.
	int main()
	{
		// prints Hello World
   		cout << "Hello World"; 
   		
   		//Terminates main() function
   		return 0;
	}

1. The C++ language defines several headers, which contain information that is either necessary or useful to your program. For this program, the header <iostream> is needed.
2. The line using namespace std; tells the compiler to use the std namespace. 
3. The line int main() is the main function where program execution begins.
4. The next line cout << "Hello World."; causes the message "Hello World" to be displayed on the Console.
5. The next line return 0; terminates main( )function and causes it to return the value 0 to the calling process.

<a name="execute"/></a>
## Compile and Run Helloworld Program
#  

![C++ Compile and Run Flow Chart](https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToC++/C++CompileAndRunFlow.png) 

**Step 1:** Write the program hello.cpp using any [Text Editor](@editor) 

**Step 2:** Compile the program, translating it into machine instructions. In its 
original form, the program is text or source code. Once translated, the source code becomes Object Code. If there are any Compilation error, fix the code and again compile the program. There are 2 Methods to compile.  

**Method 1:**

	$ g++ hello.cpp -o hello

This command compiles hello.cpp directly into an executable program named "hello" that can be run by typing 'hello' at the command line.

**Method 2:**

	$ g++ -c hello.cpp

The command transaltes the source code hello.cpp to hello.o object code file.  This is the advantage of the Method 2, in that only the changed files can be compiled to its corresponsing object code file. 

**Step 3:** Its applicable to Method 2 where in all the Object Code file can be linked to produce executable code. Here hello.o is linked to produce hello executable program. For more information refer [Compiling C++ * Program link](http://pages.cs.wisc.edu/~beechung/ref/gcc-intro.html).
  
```
$ g++ hello.o -o hello
```
**Step 4:** Finally, run the executable code

```
$ ./hello
Hello World
```

