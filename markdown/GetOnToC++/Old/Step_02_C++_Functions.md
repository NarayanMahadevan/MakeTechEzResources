# Step 1: Get On To C/C++ Basics

In this step C++ Basics is introduced by writing a executable program for the Problem Statement defined below. The Concepts introduced in this step are:

1. [**Declaration of Variables**](#declare_vars)
2. [**Local and Global Variables**](#local_global_vars) 
3. [**Arithmetic Operators, Output & Input Operators and Assignment Operators**](#operators)
4. [**Functions**](#write_functions)
5. [**Function Call**](#call_functions)

Finally the end of the Section 

a. [**Displays the result**](#result) of the [**Program**](#problem) defined below and
b. Gives [**Practice Problems**](#practice) for Development

<a name="problem"/></a>
## Problem Statement
</br>  
In this step lets write a Program that reads User Defined Inputs to compute the volume of a Box Car and Tank Car and Outputs the result onto the Console.

Here Box Car is a Rectangular Car having length, breadth and height while the tank car is cylindrical having radius and length.

<a name="main_code"/></a>
**Main Program**

Lets create a S1_ComputeVolume.cpp file and declare the main function and the place holders for Variables, Input & Output Operators, Functions, and Global Variables.

    //
    //  Program Name - S1_ComputeVolume.cpp
    //  Series: GetOnToC++ Step: 1
    //
    //  Purpose: This program computes the Volume of the Box Car and the Tank Car  
    //
    //  Compile: g++ S1_ComputeVolume.cpp -o S1_ComputeVolume
    //  Execute: ./S1_ComputeVolume
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //
    
    #include <iostream>
    using namespace std;
        
    // Section 2 - Global Variables 

    // Section 4A - Function Prototypes
    
    main ( ) { 
        // Section 1 - Declaration of Variables 
    
        // Section 3 - Output & Input Operators 

        // Section 5 - Function Call
    }
 
    // Section 4B - Function Body
    
***
**NOTE:** The Functions are defined below the Global Variables and Above the Main Function. Every Section 1, 2, 3 and 4 has code for the Main Program. As you go through the section copy the code and place it appropriately under the section identified above.
***

<a name="declare_vars"/></a>
## Section 1: Declaration of Variables
#  
As the first step lets learn how to declare variables. As mentioned above the parameters to compute volume of Rectangular Car are Length, Breadth and Height while the parameters that compute the volume of Tank Car are Radius and the Length. These parameters are nothing but Variables in C/C++

The format for Veriable Definition is as shown below

![Declare Variables](https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToC++/DeclareVariables.png) 

**Data Type** can be C++ built-in data types are char, short, int, long, float, double, etc or User Defined Data Types.

A **Variable** with name length refers to chunk of computer memory. The variable's data type determines the size of the memory. Here variable belongs to the double data type, the chunk of memory involved is likely to contain 64 bits (1 byte = 8 bits).

The **Assignment Operator (=)** assigns value to the variable length,

The double **Value** of 20.5 is stored in the variable length.

**SIDE STEP**

If you are curious about how much memory your C++ implementation allocates for the various data types, you can compile and execute the following program, which uses the sizeof operator to determine data-type size:

	//
    //  Program Name - S1_SizeOfVar.cpp
    //  Series: GetOnToC++ Step: 1
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

**Main Program**

Lets declare the variables for the Problem Statement

        // Section 1 - Declaration of Variables 
        
        /* 
         1. The Vairbles defined below are Local Variables and are local to this 
            main function. 
         2. All Variables are of data type double(holds 8 bytes or 64 bits memory) 
            and intialized to 0.0
        */
        
        // Variabes for Box Car
        double length = 0.0, breadth = 0.0, height = 0.0;
        
        // Vairables for Tank Car which is a Cylinder
        double radius = 0.0, cylLength = 0.0;


<a name="local_global_vars"/></a>
## Section 2: Local and Global Variables
#  
**Local Vairable -** 

1. A variable declared inside a function definition is said to be a **local variable**.
2. The memory allocated for Function Parameters and Local Variables are **reallocated** as soon as the corresponding function has finished executing, so parameters and local variables are said to have **dynamic extent**.
3. Function Parameters and local variables can be evaluated and assigned only in the function in which they are declared. Accordingly, parameters and local variables are said to have **local scope**.

**Global Vairable -** 

1. A variable defined outside of any function definition is said to be a **global variable**.
2. The memory set aside for a global variable is never reallocated, so global variables are said to have **static extent**.
3. Global variables can be evaluated and assigned at any point in a program after they are defined, so global variables are said to have **universal scope**. 

**Main Program**

Lets declare the Global Vairables to indicate the current year and the mathamatical constant Pi

    // Section 2 - Global Variables 
    
    // CurrentYear is a Global Vairable and indicates the current year     
    int gCurrentYear = 2013;

    /*
     * PI is a Global Variable and is also a Mathematical Constant as indicated
     * by const directive. This means PI value cannot be re-assigned.
     */
    double PI = 3.14159;

***
**NOTE:** To differentiate between local and global variables, global variable begin with g. The Constant Global Variable are all caps.  
***

<a name="operators"/></a>
## Section 3: Arithmetic Operators, Output & Input Operators and Assignment Operators
#  
This section defines the following:

a. [**Arithmetic Operator**](#Arithmetic_operator)
b. [**Output Operator**](#output_operator)
c. [**Assignment Operator**](#assignment_operator)  
d. [**Input Operator**](#input_operator)  
e. [**Operator Precedence and Associativity Table**](#precedence_operator)

<a name="Arithmetic_operator"/></a>
### Arithmetic Operators
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

**SIDE STEP**

This program shows how C++ handles precedence and associativity.

    //
    //  Program Name - S1_ArthmaticExpression.cpp
    //  Series: GetOnToC++ 	Step: 1 	
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
    
<a name="output_operator"/></a>
### Output Operator
#  

Lets see how C++ handles output statements essentially cout and the output operator (<<). 

a. **cout** - cout is actually a variable, and like all variables, it is the name of a chunk of memory
b. **Output Operator "<<"** - The chunk of memory held by cout vairable is only useful to output operator to display on the console.

***

For e.g.

cout << "The volume of the box car is " << 10 * 9 * 40 << endl; 

Output Operator is evaluated from Left to Right. So cout first stores the String "The volume of the box car is " then after display it replaces the String with the value of the expression  10 * 9 * 40 and then endl i.e. new line.  

Also Note that the **Output Operator has precendence lower than the Arithmetic Operator** and hence the volume 10 * 9 * 40 is computed first before assigning to cout variable.
***

<a name="assignment_operator"/></a>
### Assignment Operator
#  

The assignment operator, =, like all operators in C++, produces a value. The assignment operator has the lowest precedence and the associativity is from right to left. Thus for e.g.

int volume = 10 * 9 * 40;

First the value 10 * 9 * 40 is computed because of higher precedence and the value 3600 is assigned to the variable volume bacause of right to left associativity.

<a name="input_operator"/></a>
### Input Operator
#  
The input operator, >>, also known as the extraction operator, is the complement of the output operator. 

When output operator used with the **cout** output-place specification, the output operator displays the value of an expression on your screen. Similarly when input operator used with the **cin** input-place specification, the input operator picks up a value for a variable by watching whats typed on the keyboard. 

**SIDE STEP**

This program demonstrated Input and Output Operators

	//
    //  Program Name - S1_UserInputs.cpp
    //  Series: GetOnToC++ Step: 1
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

<a name="precedence_operator"/></a>
### Operator Precedence and Associativity Table
#  
The precedences and associativity of the operators are arranged from highest precedence to lowest in the following table. If Precedence of the Operator are same then Associativity Rule is applied

Sr.No | Operators   		| Associativity | Explanation  
:---- | :--------- 			| :------------ | :------------
1     | - (Unary) +(Unary) | Right to Left | Highest Precedence
2     | *, /, % 			| Left to Right | e.g. 6 / 3 / 2 = (6 / 3) / 2 = 1
3     | -, +   				| Left to Right | e.g. 6 + 3 * 2 = 6 + (3 * 2) = 12
4     | << (Output)        | Left to Right | e.g. cout << "res = " << 6 * 6 * 10; res = 360
5     | = (Assignment) 		| Right to Left | Lowest Precedence

**Main Program**

The following code uses the input operator to read user inputs to populate the variables needed to calculate volume of the Box Car and the Tank Car.  Please copy and appropriately paste in section 3 in the [**Program**](#main_code) defined above.

        // Section 3 - Output & Input Operators

        // Reading the User inputs and setting the values of length, width and
        // height of the Box Car
        cout << "Please Enter the Length, Width and Height of the Box Car." 
             << endl;
        cin >> length >> width >> height;  
        
        // Reading the User inputs and setting the values of radius and length
        // of the Tank Car
        cout << "Please Enter the Radius and Length of the Tank Car." << endl;
        cin >> radius >> lengthOfTankCar;  

<a name="write_functions"/></a>
## Section 4: Functions
</br>

A function is a group of statements that together perform a task. Every C++ program has at least one function which is main(). Looking into the problem statement, we can see we have to compute the volume of the Box Car and the Tank Car. Since the volume will be computed for varying length, breadth and height as well as for varying cylindrical length and radius, its best this computation is done in a volume computing function. The function definition is as follows: 

![Function Declaration](/Users/narayan/Documents/MakeTechEzResources/images/GetOnToC++/DeclareFunctions.png "Function Declaration") 

<!--!
[Function Declaration](https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToC++/DeclareFunctions.png "Function Declaration") 
-->
**Procedure Abstraction** is achieved when computational detail are moved into a function. The benifits are: 

1. Easy to reuse your programs
2. Makes programs easier to read and enables to concentrate on high-level steps
3. Easy to debug program
4. Easy to change and improve code

Function Definition consists of Function Prototypes and Function Body. It is required by the compiler that function be defined before the function is called. So either the Function is to be defined in full or function prototypes needs to be  defined.

**SIDE STEP**

This program demonstrates writing a function prototype and function body to calculate maximum of 3 numbers

    //
    //  Program Name - S1_FunctionDemo.cpp
    //  Series: GetOnToC++ Step: 1
    //
    //  Purpose: This program demonstrates writing a function prototype and 
    //           function body to calculate maximum of 3 numbers
    //
    //  Compile: g++ S1_FunctionDemo.cpp -o S1_FunctionDemo
    //  Execute: ./S1_FunctionDemo
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    using namespace std;

    int maximum( int, int, int ); // function prototype 

    int main ( ) 
    { 
        int a, b, c; // variables to store user inputs
        
        cout << "Enter three integers: "; 
        cin >> a >> b >> c; 

        // a, b and c below are arguments to the maximum function call
        cout << "Maximum is: " << maximum( a, b, c ) << endl;

        return 0;
    }

    // Function maximum definition x, y and z below are parameters to the 
    // maximum function definition

    int maximum( int x, int y, int z )
    {
        int max = x; // setting the maximum value to x
        
        // Using the if condition statement to check y and z are greater then max
        if (y > max) max = y;
        if (z > max) max = z;

        return max; // Returning the max value
    }

***
**S1_FunctionDemo.cpp program execution and results**

	$ g++ S1_FunctionDemo.cpp -o S1_FunctionDemo
	$ ./S1_FunctionDemo 
	Enter three integers: 23 12 45
	Maximum is: 45

***

#### Function Prototypes 

Function Prototypes is also referred as **Function Declaration**. Its one of the very useful feature of C++. It improves readability of the program. It tells the compiler the name of the function, the type of data returned by the function and the order and number of parameters the function should except. The compiler uses this to validate the function call.

**Main Program**

The following code defines the function prototype to calculate volume of the Box Car and the Tank Car.  Please copy and appropriately paste in section 4A in the [**Program**](#main_code) defined above.

    // Section 4A - Function Prototype

    // The function prototype or declaration to calculate the Volume of the Box Car
    double calcBoxCarVolume(double, double, double);

    // The function prototype to calculate the Volume of the Tank Car
    double calcTankCarVolume(double, double);

#### Function Body 

Function Body is the place where the code for actual computation or the logic is written. Once the place holder in the function prototype is defined for compiler to validate the program, the function body can be written after the main. Or else the function body has to written before the function call otherwise there would be compilation error.

**Main Program**

The following code declares the function body to calculate volume of the Box Car and the Tank Car.  Please copy and appropriately paste in section 4B in the [**Program**](#main_code) defined above.

    // Section 4B - Function Body

    /*
     * This function calculates the Volume of the Box Car
     * Input Param are: ht => height, wt => width, and lt = length
     * return: volume of the Box Car
     * Note: Here the scope of Function Parameters are local to this 
     * function and is called call-by-value  
     */    
    double calcBoxCarVolume(double ht, double wt, double lt) {
        /*
         * The scope of the boxCarVol variable is local to this function.
         * This means the memory is not available outside the function.
         * The local variable boxCarVol stores the volume of the Box Car
         */        
        double boxCarVol = 0.0;
        
        // Box Car Volume Computation using Arithmetic Operations
        boxCarVol = ht * wt * lt;
       
        // Returns the Box Car Volume
        return boxCarVol;
    }

    /*
     * This function calculates the Volume of the Tank Car
     * Input Param are: rad => radius, and lt = length of the cylinder
     * return: volume of the Tank Car
     * Note: Here the scope of Function Parameters are local to this 
     * function and is called call-by-value  
     */    
    double calcTankCarVolume(double ht, double wt, double lt) {
        /*
         * The scope of the tankCarVol variable is local to this function.
         * This means the memory is not available outside the function.
         * The local variable tankCarVol stores the volume of the Tank Car
         */        
        double tankCarVol = 0.0;
        
        // Tank Car Volume Computation using Arithmetic Operations
        tankCarVol = PI * rad * rad * l;
        
        // Returns the Tank Car Volume
        return tankCarVol;
    }

***
**NOTE:** When the scope of function parameters are local to the function and not available outside the function, such parameters are called **call-by-value**. The scope and extent to which Memory is available for Function Parameters are similar to Local Variable.  
***

<a name="call_functions"/></a>
## Function Call
#  

The function is invoked by a function call. The function is called by the name along with the parameters as specified in the function prototype. Finally the code in the Main Program below demonstrates function calling.
 
**Main Program**

Lets complete the program by taking user inputs and correspondingly calling the functions calcBoxCarVolume and calcTankCarVolume to get the volume of the Box Car and the Tank Car

        // Section 5 - Function Call
        
        // Calling Function calcBoxCarVolume to calculate the Volume of Box Car
        double boxCarVol = calcBoxCarVolume(height, width, length);
        cout << "The volume of the Box Car is " << boxCarVol << endl; 
 
        // Calling Function calcTankCarVolume to calculate the Volume of Tank Car
        double tankCarVol = calcTankCarVolume(radius, lengthOfTankCar);
        cout << "The volume of the Tank Car is " << tankCarVol << endl; 

<a name="result"/></a>
# Display Program Result  

The following displays the Compilation, Execution, Inputs and Outputs of the [**Main Program**](#main_code) developed in this step

***
	$ g++ S1_ComputeVolume.cpp -o S1_ComputeVolume
	$ ./S1_ComputeVolume 
	Please Enter the Length, Width and Height of the Box Car.
	10 10 10
	The volume of the Box Car is 1000
	Please Enter the Radius and Length of the Tank Car.
	10 10
	The volume of the Tank Car is 3141.59

***

<a name="practice"/></a>
# Practice Problem for Development  

1. Write a function `int calcFlatCarVolume(int length);` to calculate volume of the the flat cars if they are loaded to a maximum length of 8.25 feet. Note that the flat car height and width are exactly 1 feet.

2. Write a fuction `float c_to_f(float);` to calculate fahrenheit given the celcius. The formulae is **°C x 9/5 + 32 = °F **
`
3. Write a function `float f_to_c(float);` to calculate celcius given the fahrenheit 

4. Write a function `double energyOfMovingMass(float, float);` to calculate energy of the moving mass given its weight and speed. The energy of a moving mass is given by the formula **E =  ½mv²** 

