# Step 1: Get On To C/C++ Intro
</br>

This objective of this step is to introduce typical C++ development enviromnet, to be able to write simple programs in C++, to understand variable declaration and scope, look into input and output operators as wells as arthmatic operators. Note that all the concepts are introduced using **Side Program** to explain the concept. The Concepts introduced in this step are:

1. [**C++ Development Environment**](#c++_dev_env)
2. [**Setup C++ Environment**](#c++_setup) 
3. [**Overview of C++**](#c++_overview)
4. [**Helloworld C++ Program**](#c++_helloworld)
5. [**Compile and Run Helloworld Program**](#c++_execute)
6. [**Decalration of Variables**](#declare_vars)
7. [**Type and Scope of Variables**](#var_scope)
8. [**Output & Input Operators**](#output_input_oper)
9. [**Arithmatic Operators**](#arth_oper) 
10. [**Operators Precedence**](#oper_precdence)

Finally the end of the section specifies a [**Programming Problem**](#prog_problem) that will try to use all the concepts covered in this step 

<a name="c++_dev_env"/></a>
## C++ Development Environment and Setup
</br>

C++ program goes through typically go through six phases to be executed as shown in figure below. They are **edit, preprocess, compile, link, load and execute**

![C++ Development Environment][1]

[1]: /Users/narayan/Documents/MakeTechEzResources/images/GetOnToC++/C++DevEnv1.png "C++ Development Environment"

<!--
[1]: https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToC++/C++DevEnv1.png "C++ Development Environment" 
-->

![C++ Development Environment][2]

[2]: /Users/narayan/Documents/MakeTechEzResources/images/GetOnToC++/C++DevEnv2.png "C++ Development Environment"

<!--
[2]: https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToC++/C++DevEnv2.png "C++ Development Environment" 
-->

<a name="c++_setup"/></a>
## Setup C++ Environment
</br>
Before you start programming in C++, it is important you have the environment to 

1. Type the C++ program i.e. Text Editor and 
2. The compiler to compile and run the C++ Program 

<a name="editor"/></a>
###Text Editor
</br>
This will be used to type your program. Examples of few editors include Windows Notepad, OS Edit command, Brief, Epsilon, EMACS, and vim or vi. 

Our recomendation is [**gedit**](https://projects.gnome.org/gedit/) from GNOME. Its a free software. Linux fans will already be familiar with the world of GNOME but gedit has brought it to a wider audience by providing the default GNOME editor on Windows and Mac. This can be **downloaded** from <http://gedit.en.softonic.com>. The advantages are:

* One Editor for multiple OS Environment
* Wide range of languages supported by Gnome include C, C++, Java, HTML, XML, Python and Perl. 

###C++ Compiler
</br>
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

<a name="c++_overview"/></a>
## Overview of C++
</br>
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

<a name="c++_helloworld"/></a>
## Helloworld C++ Program
</br>
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
</br>
![C++ Compile and Run][3]

[3]: /Users/narayan/Documents/MakeTechEzResources/images/GetOnToC++/C++CompileAndRunFlow.png "C++ Compile and Run" 

<!--
[3]: https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToC++/C++CompileAndRunFlow.png "C++ Compile and Run" 
-->

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
<a name="declare_vars"/></a>
## Declaration of Variables
#  
As the first step lets learn how to declare variables. Variables are containers that can store different values. In C, variables are statically typed, which means that you must explicitly state what kind of value they will hold.  

The format for Veriable Definition is as shown below

</br>  
![Declare Variables](/Users/narayan/Documents/MakeTechEzResources/images/GetOnToC++/DeclareVariables.png "Declare Variables") 
<!--
![Declare Variables](https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToC++/DeclareVariables.png "Declare Variables") 
-->

**Data Type** can be C++ built-in data types are char, short, int, long, float, double, etc or User Defined Data Types.

A **Variable** with name length refers to chunk of computer memory. The variable's data type determines the size of the memory. Here variable belongs to the double data type, the chunk of memory involved is likely to contain 64 bits (1 byte = 8 bits).

The **Assignment Operator (=)** assigns value to the variable length,

The double **Value** of 20.5 is stored in the variable length.

##### SIDE PROGRAM # &nbsp;1

If you are curious about how much memory your C++ implementation allocates for the various data types, you can compile and execute the following program, which uses the sizeof operator to determine data-type size:

	//
    //  Program Name - S1_SP_SizeOfVar.cpp
    //  Series: GetOnToC++ Step: 1 Side Program
    //
    //  Purpose: This program outputs the size of C++ in built data types using  
    //           sizeof operator 
    //
    //  Compile: g++ S1_SizeOfVar.cpp -o S1_SizeOfVar
    //  Execute: ./S1_SizeOfVar
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //
    
    #include <iostream>
    using namespace std;

    main ( ) { 
  		cout << "Data Type    Bytes" << endl 
       		 << "char         " << sizeof(char) << endl 
       		 << "short        " << sizeof(short) << endl 
             << "int          " << sizeof(int) << endl 
             << "long         " << sizeof(long) << endl 
             << "float        " << sizeof(float) << endl 
             << "double       " << sizeof(double) << endl 
             << "long double  " << sizeof(long double) << endl; 
    }
    
***
**NOTE:** You can include comments in C++ programs in two ways. 

1. // short comments that appear in single line
2. /\* Long Comments that appear in multiple lines \*/ 
***

<a name="var_types"/></a>
# Section 2: Variable Types
  
This section discusses different variable types. This includes 

1. **Local Variable** 
2. **Global Vairable**
3. **Constants**
4. **Macros**
5. **Typedef**
 
#### Local Vairable  

1. A variable declared inside a function definition is said to be a **local variable**.
2. The memory allocated for Function Parameters and Local Variables are **reallocated** as soon as the corresponding function has finished executing, so parameters and local variables are said to have **dynamic extent**.
3. Function Parameters and local variables can be evaluated and assigned only in the function in which they are declared. Accordingly, parameters and local variables are said to have **local scope**.

#### Global Vairable 

1. A variable defined outside of any function definition is said to be a **global variable**.
2. The memory set aside for a global variable is never reallocated, so global variables are said to have **static extent**.
3. Global variables can be evaluated and assigned at any point in a program after they are defined, so global variables are said to have **universal scope**. 

#### Constants
</br>
The const variable modifier can be used to tell the compiler that a variable is never allowed to change. For example, defining a constant called pi and then trying to alter it will result in a compiler error:

`double const pi = 3.14159;`</br>
`pi = 42001.0;  // Result in Compiler error`

This is often used in function parameters to inform the caller that they can safely assume whatever value they pass will not be altered by the function.

#### Macros
</br>

Macros are a low-level way to define symbolic constants and space-saving abbreviations. The #define directive maps a macro name to an expansion, which is an arbitrary sequence of characters. Before the compiler tries to parse the code, the preprocessor replaces all occurrences of the macro name with its expansion. In other words, it’s a straightforward search-and-replace:

##### SIDE PROGRAM # &nbsp;2

Define a Macro to convert Radians to Degree

    //
    //  Program Name - S1_SP_RadToDeg.cpp
    //  Series: GetOnToC++ Step: 1 Side Program
    //
    //  Purpose: Write a Program to convert Radians to Degrees using a Macro.
    //           The formulae is deg = rad * (180/pi)
    //
    //  Compile: g++ S1_SP_RadToDeg.cpp -o S1_SP_RadToDeg
    //  Execute: ./S1_SP_RadToDeg
    //
    //  Created by Narayan Mahadevan on 10/11/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    using namespace std;

    // Defining a Macro to specify the value of pi. 
    #define PI 3.14159

    // Defining a Macro to convert Radians to Degrees
    #define RAD_TO_DEG(radians) (radians * (180.0 / PI))

    main ( ) { 
        double angle = PI / 2; 
        cout << "Radians to Degree is: " << RAD_TO_DEG(angle) << endl;
    }
    
**RESULT:**

	Radians to Degree is: 90 

#### Typedef
</br>

The typedef keyword lets you create new data types or redefine existing ones. After typedef’ing an unsigned int in the following example, we can use ColorComponent just like we would use char, int, double, or any other built-in type

##### SIDE PROGRAM # &nbsp;3

Write a Program where unsigned int is assigned as ColorComponent and ColorComponent is used as any other datatype

    //
    //  Program Name - S1_SP_TypedefEg.cpp
    //  Series: GetOnToC++ Step: 1 Side Program
    //
    //  Purpose: Write a Program where unsigned int is assigned as ColorComponent 	//			  and ColorComponent is used as any other datatype
    //
    //  Compile: g++ S1_SP_TypedefEg.cpp -o S1_SP_TypedefEg
    //  Execute: ./S1_SP_TypedefEg
    //
    //  Created by Narayan Mahadevan on 10/11/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    using namespace std;

    // Creating a new Data Type ColorComponent of unsigned char
    typedef unsigned int ColorComponent;

    main ( ) { 
        // Setting the RGB color value        
        ColorComponent red = 255;
        ColorComponent green = 160;
        ColorComponent blue = 0;    

        cout << "Paint job has R value: " << red << " G value: " << green 
             << " and B value: " << blue << endl;
    }
    
**RESULT:**

	Paint job has R value: 255 G value: 160 and B value: 0    
	
<a name="output_input_oper"/></a>
## Output & Input Operators
#  

#### Output Operator

Lets see how C++ handles output statements essentially cout and the output operator (<<). 

a. **cout** - cout is actually a variable, and like all variables, it is the name of a chunk of memory
b. **Output Operator "<<"** - The chunk of memory held by cout vairable is only useful to output operator to display on the console.

***

For e.g.

`cout << "The volume of the box car is " << 10 * 9 * 40 << endl; `

Output Operator is evaluated from Left to Right. So cout first stores the String "The volume of the box car is " then after display it replaces the String with the value of the expression  10 * 9 * 40 and then endl i.e. new line.  

Also Note that the **Output Operator has precendence lower than the Arithmetic Operator** and hence the volume 10 * 9 * 40 is computed first before assigning to cout variable.
***

#### Format the Output

C++ uses the escape character "\" to format the output. The figure below shows some of the common escape sequence

![C++ Format Output][4]

[4]: /Users/narayan/Documents/MakeTechEzResources/images/GetOnToC++/C++EscapeSeq.png "C++ Format Output" 

<!--
[4]: https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToC++/C++EscapeSeq.png "C++ Format Output" 
-->

#### SIDE PROGRAM: &nbsp;4

This simple program demonstrates Printing a Hollow Box

	//
    //  Program Name - S1_SP_PrintBox.cpp
    //  Series: GetOnToC++ Step: 1 Side Program
    //
    //  Purpose: This program demonstrates printing a hollow box
    //
    //  Compile: g++ S1_SP_PrintBox.cpp -o S1_SP_PrintBox
    //  Execute: ./S1_SP_PrintBox
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    using namespace std;

    main ( ) { 
        cout << "Display a Hollow Box" << endl;        
        cout << "*********\n";
        cout << "*\t*\n";
        cout << "*\t*\n";
        cout << "*\t*\n";
        cout << "*********\n";
    }

**RESULT:**

	$ ./S1_SP_PrintBox
	Display a Hollow Box
	*********
	*	    *
	*	    *
	*	    *
	*********

#### Input Operator

The input operator, >>, also known as the extraction operator, is the complement of the output operator. 

When output operator used with the **cout** output-place specification, the output operator displays the value of an expression on your screen. Similarly when input operator used with the **cin** input-place specification, the input operator picks up a value for a variable by watching whats typed on the keyboard. 

#### SIDE PROGRAM: &nbsp;5

This program demonstrated Input and Output Operators

	//
    //  Program Name - S1_SP_UserInputs.cpp
    //  Series: GetOnToC++ Step: 1 Side Program
    //
    //  Purpose: This program picks up an integer from the console and assigns  
    //           that integer to a variable to compute volume
    //
    //  Compile: g++ S1_UserInputs.cpp -o S1_UserInputs
    //  Execute: ./S1_UserInputs
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    using namespace std;

    main ( ) { 
          int height, width, length;
          cout << "Please type three integers." << endl;
          cin >> height;  
          cin >> width;   
          cin >> length;  
          cout << "The volume of a " 
               << " box car is " << height * width * length << endl; 
    }

    /*
      On executing the program, the following lines are displayed on screen
      Please type three integers.                     <-- Your program types 
      10 9 40                                         <-- You type 
      The volume of a box car is 3600.                <-- Your program types 
    */

***
**NOTE:** In Unix, MAC or Linux OS, the characters typed accumulate temporarily in an input buffer before delivery to the program. Delivery occurs only when a carriage return entered.  
***

<a name="arth_oper"/></a>
## Arithmetic Operators
#  
Arithmetic Operators are either

* **Binary Operator** - Most operators are binary operators; that is, they have two operands. **Binary Operators are +, -, *, / and %** operators for addition, subtraction, multiplication, division, and modulus operator. For e.g. 
  * 6 / 3 => In this case "/" is a division operator and 6 and 3 are Operands
  * 5 % 3 => The Modulus Operator produces the reminder i.e. 2
  * 5 / 3 => Divide, evaluating to 1, rather than 2 or 1.66667
  * 5.0 / 3.0 => Divide, evaluating to 1.66667

* **Unary Operators** - Unary operators, such as the negation operator, -, and unary plus, +, have just one operand, found on the immediate right of the operator.  For e.g. 6 - (-3) => The result is 9. "(-3)" is the unary operator. Unary Operator evaluates from right to left and the precedence of the unary operator is higher than that of Binary Operators +, -, *, or /. More in [**Operator Precedence**](#precedence_operator)

C++ Expressions are evaluated first on Precedence and than if operators have same Precedence then on Associativity i.e. either the expression is evaluated left to right or right to left. 

* **Precedence** - Unary Operators have highest precedense followed by "*, /, %" operators and than by "+ or -" operators. 
* **Associativity** - Unary Operators are evaluated from Right to Left and the remaining Arithmetic Operators Left to Right.

#### SIDE PROGRAM: &nbsp;6

This program shows how C++ handles precedence and associativity.

    //
    //  Program Name - S1_SP_ArthmaticExpression.cpp
    //  Series: GetOnToC++ 	Step: 1 Side Program    
    //
    //  Purpose: This program shows the way C++ handles operator precedence and 
    //           associativity
    //
    //  Compile: g++ S1_ArthmaticExpression.cpp -o S1_ArthmaticExpression
    //  Execute: ./S1_ArthmaticExpression
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //
    
    #include <iostream>
    using namespace std;

    main ( ) { 

        // Equivalent to 6 + (3 * 2) = 12 And not (6 + 3) * 2 = 18
        cout << "Expression = 6 + 3 * 2, with Higher Precedense: " 
             << 6 + 3 * 2 << endl; 

        // Equivalent to 6 - (-3) = 9 
        cout << "Expression = 6 - -3, with Unary Opetrator -3: " 
             << 6 - -3 << endl; 

        // Equivalet to: (6 / 3) / 2 = 1
        cout << "Expression = 6 / 3 / 2, with Same Precedense (L to R): " 
             << 6 / 3 / 2 << endl;       
           
        // Equivalent to (6 / 3) * 2 = 4 And not 6 / (3 * 2) = 1     
        cout << "Expression = 6 / 3 * 2, with Same Precedense (L to R): " 
             << 6 / 3 * 2  << endl;

        // Equivalent to (6 * 3) / 2 = 9 And not 6 * (3 / 2) = 6    
        cout << "Expression = 6 * 3 / 2, with Same Precedense (L to R): " 
             << 6 * 3 / 2  << endl;
    }

</br>    
<a name="oper_precdence"/></a>
## Operator Precedence
</br>    
The precedences and associativity of the operators are arranged from highest precedence to lowest in the following table. If Precedence of the Operator are same then Associativity Rule is applied

Sr.No | Operators   		| Associativity | Explanation  
:---- | :--------- 			| :------------ | :------------
1     | - (Unary) +(Unary) | Right to Left | Highest Precedence
2     | *, /, % 			| Left to Right | e.g. 6 / 3 / 2 = (6 / 3) / 2 = 1
3     | -, +   				| Left to Right | e.g. 6 + 3 * 2 = 6 + (3 * 2) = 12
4     | << (Output)        | Left to Right | e.g. cout << "res = " << 6 * 6 * 10; res = 360
5     | = (Assignment) 		| Right to Left | Lowest Precedence


</br>  
<a name="prog_problem"/></a>
## Programming Problem
</br>  

Determine the value of global variable a using expression `a = 2/3*b + c*c - c%c + 50% of b/c`. Where b and c are input values taken from the user

    //
    //  Program Name - S1_MP_NumberArthmatic.cpp
    //  Series: GetOnToC++ Step: 1 Main Program
    //
    //  Purpose: Determine the value of global variable a using expression 
    //           a = 2/3*b + c*c - c%c + 50% of b/c. Where b and c are input 
    //           values taken from the user
    //
    //  Compile: g++ S1_MP_NumberArthmatic.cpp -o S1_MP_NumberArthmatic
    //  Execute: ./S1_MP_NumberArthmatic
    //
    //  Created by Narayan Mahadevan on 10/11/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    using namespace std;

    // Macro to calculate percentage
    #define PERC_VAL(b, c) (0.5 * (b/c))

    // Global Variable to hold value a
    double a = 0;

    main ( ) { 

        // Local Variables to hold value b and c
        int b = 0, c = 0;

        // Input Operator to take User Input for course marks
        cout << "Enter any two values: \a";
        cin >> b >> c;

        // Use Arthmatic Expression to find value of a
        // Checkout the Operator Precedence and associativity to understand how
        // compiler resolves arthmatic expression.
        a = 2/3*b + c*c - c % c + PERC_VAL(b, c);

        // Output the Result
        cout << "The Value of a = " << a << endl;

    }

**RESULT:**

	$ ./S1_MP_NumberArthmatic
	Enter any two values: 45 55
	The Value of a = 3025
