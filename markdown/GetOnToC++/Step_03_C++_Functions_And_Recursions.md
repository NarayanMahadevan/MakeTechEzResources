# Step 3: C++ Functions and Recursions
</br>

The Objective of this step is to introduce all about functions including function definition, function prototypes, in-line functions, function overload and recursive functions. In the initial part we look into built-in functions provided by C++ Standard Library and Math Lib functions. The concept introduced in this step are as follows:

1. [**C++ Standard Library Headers**](#c++_std_lib)
2. [**Math Lib Functions**](#math_lib)
3. [**Function Definition**](#func_def)
4. [**Function Prototype and Body**](#func_prototype)
5. [**Function Scope Rules**](#func_scope_rules)
6. [**Recursive Functions**](#recursive_func)
7. [**Inline Functions**](#inline_func)
8. [**Function Oveloading**](#func_overload)

Finally the end of the section specifies a [**Programming Problem**](#prog_problem) that will try to use all the concepts covered in this step 

<a name="c++_std_lib"/></a>
## C++ Standard Library Headers
</br>

The C++ Standard Library is divided into many portions, each with its own header. The headers contain the function prototypes for the related functions that form each portion of the library. The headers also contain definitions of various class types and functions, as well as constants needed by those functions. The table below discusses the various C++ Library Headers with a brief explanation

Standard Library | Explanation
------------     | ------------- | 
**iostream**     | Contains function prototypes for the C++ standard input and output functions   
**iomanip**     | Contains function prototypes for stream manipulators that format streams of data.
**cmath**     | Contains function prototypes for math library functions 
**cstdlib**     | Contains function prototypes for conversions of numbers to text, text to numbers, memory allocation, random numbers and various other utility functions. 
**ctime**     | Contains function prototypes and types for manipulating the time and date. 
**vector, list, deque, queue, stack, map, set, bitset**     | Standard Template Libraries STL) contain classes that implement the C++ Standard Library containers. Containers store data during a program’s execution. 
**cctype**     | Contains function prototypes for functions that test characters for certain properties as well as functions that can be used to convert lowercase letters to uppercase letters and vice versa.
**cstring**     | Contains function prototypes for C-style string-processing functions. 
**exception, stdexcept**     | These headers contain classes that are used for exception handling
**fstream**     | Contains function prototypes for functions that perform input from and output to files on disk 
**string**     | Contains the definition of class string from the C++ Standard Library
**cfloat**     | Contains the floating-point size limits of the system
**locale**     | Contains classes and functions normally used by stream processing to process data in the natural form for different languages 

##### SIDE PROGRAM # &nbsp;1

Write a Program to demonstrate simulation of six-sided dice rolled 20 times using random number generator

    //
    //  Program Name - S3_SP_RandomDiceRoll.cpp
    //  Series: GetOnToC++ Step: 1 Side Program
    //
    //  Purpose: To demonstrate rand, simulate 20 rolls of a six-sided die 
    //           and displays the value of each roll. The function prototype 
    //           for the rand function is in <cstdlib>. To produce integers 
    //           in the range 0 to 5, we use the modulus operator (%) with 
    //           rand as follows: rand() % 6
    //
    //  Compile: g++ S3_SP_RandomDiceRoll.cpp -o S3_SP_RandomDiceRoll
    //  Execute: ./S3_SP_RandomDiceRoll
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>    #include <iomanip>
    #include <cstdlib> // contains function prototype for rand

    using namespace std;

    int main()
    {
        // loop 20 times
        for ( int counter = 1; counter <= 20; ++counter ) {
            // pick random number from 1 to 6 and output it            cout << setw( 10 ) << ( 1 + rand() % 6 );
            // if counter is divisible by 5, start a new line of output            if ( counter % 5 == 0 ) cout << endl;        } // end for
    }

 
<a name="math_lib"/></a>
## Math Lib Functions
</br>

Math Lib Functions are defined in cmath standard library. The **cmath** header provides a collection of functions that enable you to perform common mathematical calculations. For example, you can calculate the square root of 900.0 with the function call `sqrt( 900.0 )` which evaluates to 30.0. Function sqrt takes an argument of type dou- ble and returns a double result. 

Some math library functions are summarized in Figure below as Part 1 and Part 2. In the figure, the variables x and y are of type double.

**Math Library Function Part 1**

![Math Library Function Part 1][1]

[1]: /Users/narayan/Documents/MakeTechEzResources/images/GetOnToC++/MathLibFuncPart1.png "Math Library Function Part 1"

<!--
[1]: https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToC++/MathLibFuncPart1.png "Math Library Function Part 1" 
-->

**Math Library Function Part 2**

![Math Library Function Part 2][2]

[2]: /Users/narayan/Documents/MakeTechEzResources/images/GetOnToC++/MathLibFuncPart2.png "Math Library Function Part 2"

<!--
[1]: https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToC++/MathLibFuncPart2.png "Math Library Function Part 2" 
-->

##### SIDE PROGRAM # &nbsp;2

Calculate Compound interest based on Principal Amount, Rate of Interest and Duration using the formulae 

	a = p ( 1 + r )^n where	p is the original amount invested (i.e., the principal), 	r is the annual interest rate, 	n is the number of years and 	a is the amount on deposit at the end of the nth year.

The Program is written below

    //
    //  Program Name - S3_SP_CalcCompoundInterest.cpp
    //  Series: GetOnToC++ Step: 3 Side Program
    //
    //  Purpose: Calculate Compound interest based on Principal Amount, Rate of 
    //		     Interest and Duration
    //
    //  Compile: g++ S3_SP_CalcCompoundInterest.cpp -o S3_SP_CalcCompoundInterest
    //  Execute: ./S3_SP_CalcCompoundInterest
    //
    //  Created by Narayan Mahadevan on 10/11/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    using namespace std;

    // standard C++ math library
    #include <cmath>
    
    // standard C++ library to format the output
    #include <iomanip>
    
    int main ( ) { 

        // Setting the deposit amount, starting principal and the interest rate
        double amount = 0.0, principal = 1000.0, rate = .05; 
        // The Width for output Amount on deposit is set to 21
        cout << "Year" << setw( 21 )             << "Amount on deposit" << endl;

        for(int year = 1; year <= 10; year++ ) { 
            // Calculating the amount including the principal and interest based
            // on the year value
            amount = principal * pow( 1.0 + rate, year );

            // Prints the value of the variable year and amount based on the 
            // format specified by the parameterized stream manipulator setw, 
            // setiosflags and setprecision

            // The setw(4) specifies the year will be printed with atleast 
            // 4 char position. If the value is less then 4 chars then the 
            // year will be printed right justified by default

            // The call to setiosflags(ios::fixed | ios::showpoint) is used 
            // to print the amount as fixed point value with a decimal point. 

            // The setprecision is used to set the output to 2 digit precision

            cout << setw(4) << year 
                 << setiosflags( ios::fixed | ios::showpoint ) 
                 << setw( 21 ) << setprecision( 2 )                 << amount << endl ;
        }
        return 0;
    }**RESULT:**

	$ ./S2_SP_CalcCompoundInterest
	Year    Amount on deposit
   	   1              1050.00
   	   2              1102.50
   	   3              1157.63
   	   4              1215.51
   	   5              1276.28
   	   6              1340.10
   	   7              1407.10
   	   8              1477.46
   	   9              1551.33
  	  10              1628.89


<a name="func_def"/></a>
## Function Definition
</br>

A function is a group of statements that together perform a task. Every C++ program has at least one function which is main(). 

Lets consider an example to compute the volume of the Box Car and the Tank Car. Since the volume will be computed for varying length, breadth and height as well as for varying cylindrical length and radius, its best this computation is done in a volume computing function. The function definition is as follows: 

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

<a name="call_functions"/></a>
### Function Call
#  

The function is invoked by a function call. The function is called by the name along with the parameters as specified in the function definition. 

##### SIDE PROGRAM # &nbsp;3

Write a Program that computes the Volume of the Box Car and the Tank Car

	//
    //  Program Name - S3_SP_ComputeVolume.cpp
    //  Series: GetOnToC++ Step: 3 Side Program
    //
    //  Purpose: This program computes the Volume of the Box Car and the Tank Car  
    //
    //  Compile: g++ S3_SP_ComputeVolume.cpp -o S3_SP_ComputeVolume
    //  Execute: ./S3_SP_ComputeVolume
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    using namespace std;

    // Use the mathematics library, which contains a declaration for M_PI: 
    #include <math.h>
        
    // Function Definition - The Function Prototype and Body are defined together
    // Before the main

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
        
        // Box Car Volume Computation using Arithmatic Operations
        boxCarVol = ht * wt * lt;
        
        // Returns the Box Car Volume
        return boxCarVol;
    }

    /*
     * This function calculates the Volume of the Tank Car
     * Input Param are: rad => radius, and l = length of the cylinder
     * return: volume of the Tank Car
     * Note: Here the scope of Function Parameters are local to this 
     * function and is called call-by-value  
     */    
    double calcTankCarVolume(double rad, double l) {
        /*
         * The scope of the tankCarVol variable is local to this function.
         * This means the memory is not available outside the function.
         * The local variable tankCarVol stores the volume of the Tank Car
         */        
        double tankCarVol = 0.0;
        
        // Tank Car Volume Computation using Arithmatic Operations
        tankCarVol = M_PI * rad * rad * l;
        
        // Returns the Tank Car Volume
        return tankCarVol;
    }


    main ( ) { 
        
        // Declaration of Variables 

        /* 
         1. The Vairbles defined below are Local Variables and are local to this 
            main function. 
         2. All Variables are of data type double(holds 8 bytes or 64 bits memory) 
            and intialized to 0.0
        */
        // Variabes for Box Car
        double length = 0.0, width = 0.0, height = 0.0;
        
        // Vairables for Tank Car which is a Cylinder
        double radius = 0.0, lengthOfTankCar = 0.0;

        // Output & Input Operators

        // Reading the User inputs and setting the values of length, width and
        // height of the Box Car
        cout << "Please Enter the Length, Width and Height of the Box Car - ";
        cin >> length >> width >> height;  
        
        // Reading the User inputs and setting the values of radius and length
        // of the Tank Car
        cout << "Please Enter the Radius and Length of the Tank Car - ";
        cin >> radius >> lengthOfTankCar;  

        // Function Call

        // Calling Function calcBoxCarVolume to calculate the Volume of Box Car
        double boxCarVol = calcBoxCarVolume(height, width, length);
        cout << "The volume of the Box Car is " << boxCarVol << endl; 

        // Calling Function calcTankCarVolume to calculate the Volume of Tank Car
        double tankCarVol = calcTankCarVolume(radius, lengthOfTankCar);
        cout << "The volume of the Tank Car is " << tankCarVol << endl; 
    }

**RESULT:**

	$ ./S3_SP_ComputeVolume
	Please Enter the Length, Width and Height of the Box Car - 10 10 10
	Please Enter the Radius and Length of the Tank Car - 10 10
	The volume of the Box Car is 1000
	The volume of the Tank Car is 3141.59

<a name="func_prototype"/></a>
## Function Prototype and Body
</br>

**Function Prototypes** is also referred as **Function Declaration**. Its one of the very useful feature of C++. It improves readability of the program. It tells the compiler the name of the function, the type of data returned by the function and the order and number of parameters the function should except. The compiler uses this to validate the function call.

**Function Body** is the place where the code for actual computation or the logic is written. Once the place holder in the function prototype is defined for compiler to validate the program, the function body can be written after the main. Or else the function body has to written before the function call otherwise there would be compilation error.

##### SIDE PROGRAM # &nbsp;4

This program demonstrates writing a function prototype and function body to calculate maximum of 3 numbers

    //
    //  Program Name - S3_SP_FunctionDemo.cpp
    //  Series: GetOnToC++ Step: 1
    //
    //  Purpose: This program demonstrates writing a function prototype and 
    //           function body to calculate maximum of 3 numbers
    //
    //  Compile: g++ S3_SP_FunctionDemo.cpp -o S3_SP_FunctionDemo
    //  Execute: ./S3_SP_FunctionDemo
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

**RESULT:**

	$ ./S3_SP_FunctionDemo
	Enter three integers: 23 12 45
	Maximum is: 45

##### SIDE PROGRAM # &nbsp;5

This is another Side Program that demonstrates taking no function parameters. Up until now all the function were parameterized functions. This program demonstrates random dice Rolling a six-sided dice 6,000,000 times and check the frequency of 1 to 6 faces appearing

    //
    //  Program Name - S3_SP_RandomDiceRollDemo.cpp
    //  Series: GetOnToC++ Step: 3 Side Program
    //
    //  Purpose: To demonstrate random dice Rolling a six-sided dice 6,000,000 
    //           times and check the frequency of 1 to 6 faces appearing
    //
    //  Compile: g++ S3_SP_RandomDiceRollDemo.cpp -o S3_SP_RandomDiceRollDemo
    //  Execute: ./S3_SP_RandomDiceRollDemo
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>    #include <iomanip>    #include <cstdlib> // contains function prototype for rand    using namespace std;
    // Global Variable
    int frequency1 = 0; // count of 1s rolled    int frequency2 = 0; // count of 2s rolled    int frequency3 = 0; // count of 3s rolled    int frequency4 = 0; // count of 4s rolled    int frequency5 = 0; // count of 5s rolled    int frequency6 = 0; // count of 6s rolled

    // Function Prototype
    void summarize(void);

    int main() {

        summarize();

        cout << "Face" << setw( 13 ) << "Frequency" << endl; // output headers
        cout << "   1" << setw( 13 ) << frequency1
             << "\n   2" << setw( 13 ) << frequency2
             << "\n   3" << setw( 13 ) << frequency3
             << "\n   4" << setw( 13 ) << frequency4
             << "\n   5" << setw( 13 ) << frequency5
             << "\n   6" << setw( 13 ) << frequency6 << endl;
    }//endmain

    void summarize(void) 
    {
        int face; // stores most recently rolled value

        // summarize results of 6,000,000 rolls of a die        for ( int roll = 1; roll <= 6000000; ++roll )        {
            face = 1 + rand()%6; //randomnumberfrom1to6            // determine roll value 1-6 and increment appropriate counter            switch ( face ) {            case 1:               ++frequency1; // increment the 1s counter 
               break;            case 2:                ++frequency2; // increment the 2s counter 
                break;            case 3:                ++frequency3; // increment the 3s counter 
                break;            case 4:                ++frequency4; // increment the 4s counter 
                break;            case 5:                ++frequency5; // increment the 5s counter 
                break;            case 6:                ++frequency6; // increment the 6s counter 
                break;            default: // invalid value                cout << "Program should never get here!";            } // end switch        } // end for    }

**RESULT:**

	$ ./S3_SP_RandomDiceRollDemo
	Face    Frequency
   	   1      1001548
       2       998795
       3       999665
       4      1000202
       5       999052
       6      1000738

</br>
<a name="func_scope_rules"/></a>
## Function Scope Rules
</br>

Up until now we have seen Local Variables and Global Variables. Local Variables retain their scope within the function or the block it is defined. While Global Variables are defined outside the function and retain their values throughout execution of the program. Global variables and global functions can be referenced by any function that follows their decla- rations or definitions in the source file.

Now lets see static local variable. Local variables declared static are still known only in the function in which they’re declared, but, unlike local variables, static local variables retain their values when the function returns to its caller. The next time the function is called, the static local vari- ables contain the values they had when the function last completed execution. The following statement declares local variable count to be static and to be initialized to 1:`static int count = 1;`

It’s possible to declare local and global variables of the same name. C++ provides the **unary scope resolution operator (::)** to access a global variable when a local variable of the same name is in scope. The unary scope resolution operator cannot be used to access a local variable of the same name in an outer block. A global variable can be accessed directly without the unary scope resolution operator if the name of the global variable is not the same as that of a local variable in scope.


##### SIDE PROGRAM # &nbsp;6

This program demonstrates scoping of variables with global variables, local variables and static local variables. Further the global variable is accessed using **unary scope resolution operator (::)** 

    //
    //  Program Name - S3_SP_FunctionScope.cpp
    //  Series: GetOnToC++ Step: 3 Side Program
    //
    //  Purpose: This program demonstrates scoping of variables with global 
    //           variables, local variables and static local variables.
    //
    //  Compile: g++ S3_SP_FunctionScope.cpp -o S3_SP_FunctionScope
    //  Execute: ./S3_SP_FunctionScope
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>    using namespace std;

    // Function Prototypes
    void useLocal();     void useStaticLocal();     void useGlobal(); 

    // Global Variable
    int x = 1;

    int main() 
    {
        cout << "global x in main is " << x << endl;

        int x = 5; // local variable to main

        cout << "local x in main's outer scope is " << x << endl;
        
		// Inner Block
		
        { // start new scope            int x = 7; // hides both x in outer scope and global x            cout << "local x in main's inner scope is " << x << endl;        } // end new scope

        cout << "local x in main's outer scope is " << x << endl;

        useLocal(); // useLocal has local x        useStaticLocal(); // useStaticLocal has static local x        useGlobal(); // useGlobal uses global x        useLocal(); // useLocal reinitializes its local x        useStaticLocal(); // static local x retains its prior value        useGlobal(); // global x also retains its prior value

        cout << "\nlocal x in main is " << x << endl;

    } // end main

    // useLocal reinitializes local variable x during each call    void useLocal()    {
        int x = 25; // initialized each time useLocal is called        cout << "\nlocal x is " << x << " on entering useLocal" << endl; 
        ++x;        cout << "local x is " << x << " on exiting useLocal" << endl;
        // Note that the global value of x is accessed using unary scope 
        // resolution operator ::
        cout << "Global int value of x = " << ::x << endl;
                    } // end function useLocal  

    // useStaticLocal initializes static local variable x only the 
    // first time the function is called; value of x is saved    // between calls to this function    void useStaticLocal()
    {
        static int x = 50; // initialized first time useStaticLocal is called        cout << "\nlocal static x is " << x << " on entering useStaticLocal" 
             << endl;        ++x;        cout << "local static x is " << x << " on exiting useStaticLocal"
             << endl;    } // end function useStaticLocal    
    // useGlobal modifies global variable x during each call    void useGlobal() 
    {        cout << "\nglobal x is " << x << " on entering useGlobal" << endl; 
        x *= 10;        cout << "global x is " << x << " on exiting useGlobal" << endl;    } // end function useGlobal

**RESULT:**

    $ ./S3_SP_FunctionScope
    global x in main is 1
    local x in main's outer scope is 5
    local x in main's inner scope is 7
    local x in main's outer scope is 5

    local x is 25 on entering useLocal
    local x is 26 on exiting useLocal
	Global int value of x = 1

    local static x is 50 on entering useStaticLocal
    local static x is 51 on exiting useStaticLocal

    global x is 1 on entering useGlobal
    global x is 10 on exiting useGlobal

    local x is 25 on entering useLocal
    local x is 26 on exiting useLocal
    Global int value of x = 10

    local static x is 51 on entering useStaticLocal
    local static x is 52 on exiting useStaticLocal

    global x is 10 on entering useGlobal
    global x is 100 on exiting useGlobal

    local x in main is 5


</br>
<a name="recursive_func"/></a>
## Recursive Functions
</br>

For some problems, it’s useful to have functions call themselves. A recursive function is a function that calls itself, either directly, or indirectly through another functions. This is called recursion step where it calls itself. The recursion step executes while the original call to the function is still “open,” i.e., it has not yet finished executing. The recursion step can result in many more such recursive calls till some condition is met. First the inner-most recursive call is terminated then subsequently all the outer calls terminates up-until the original call.

##### SIDE PROGRAM # &nbsp;7

This program uses recursion to calculate and print the factorials of the integers 0–10.

    //
    //  Program Name - S3_SP_Factorial.cpp
    //  Series: GetOnToC++ Step: 3 Side Program
    //
    //  Purpose: This program uses recursion to calculate and print the 
    //           factorials of the integers 0–10.
    //
    //  Compile: g++ S3_SP_Factorial.cpp -o S3_SP_Factorial
    //  Execute: ./S3_SP_Factorial
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>    #include <iomanip>    using namespace std;    

    unsigned long factorial( unsigned long ); // function prototype

    int main() {        // calculate the factorials of 0 through 10        for ( int counter = 0; counter <= 10; ++counter )            cout << setw( 2 ) << counter << "! = " << factorial( counter )                 << endl; 
    } //end main

    // recursive definition of function factorial    unsigned long factorial( unsigned long number )    {        if ( number <= 1 ) // test for base case            return 1; // base cases: 0! = 1 and 1! = 1        else // recursion step            return number * factorial( number - 1 );    } // end function factorial

**RESULT:**

	$ ./S3_SP_Factorial
 	0! = 1
	1! = 1
 	2! = 2
 	3! = 6
 	4! = 24
 	5! = 120
 	6! = 720
 	7! = 5040
 	8! = 40320
 	9! = 362880
	10! = 3628800

##### SIDE PROGRAM # &nbsp;8

The Fibonacci series `0, 1, 1, 2, 3, 5, 8, 13, 21, …` begins with 0 and 1 and has the property that each subsequent Fibonacci number is the sum of the previous two Fibonacci numbers. The ratio of successive Fibonacci numbers converges on a constant value of 1.618.... This number, too, frequently occurs in nature and has been called the golden ratio or the golden mean.

The Fibonacci series can be defined recursively as follows:

	￼fibonacci(0) = 0	fibonacci(1) = 1	fibonacci(n) = fibonacci(n – 1) + fibonacci(n - 2)

Write a program to calculate the nth Fibonacci number recursively by using func- tion fibonacci.

    //
    //  Program Name - S3_SP_Fibonacci.cpp
    //  Series: GetOnToC++ Step: 3 Side Program
    //
    //  Purpose: Write a program to calculate the nth Fibonacci number 
    //           recursively by using func- tion fibonacci
    //
    //  Compile: g++ S3_SP_Fibonacci.cpp -o S3_SP_Fibonacci
    //  Execute: ./S3_SP_Fibonacci
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>    using namespace std;

    unsigned long fibonacci( unsigned long ); // function prototype

    int main()    {        // calculate the fibonacci values of 0 through 10        for ( int counter = 0; counter <= 10; ++counter )            cout << "fibonacci( " << counter << " ) = "                 << fibonacci( counter ) << endl;

        // display higher fibonacci values        cout << "fibonacci( 20 ) = " << fibonacci( 20 ) << endl;
        cout << "fibonacci( 30 ) = " << fibonacci( 30 ) << endl;
        cout << "fibonacci( 35 ) = " << fibonacci( 35 ) << endl;

    } // end of main

    // recursive function fibonacci    unsigned long fibonacci( unsigned long number )    {        if ( ( number == 0 ) || ( number == 1 ) ) // base cases            return number;        else // recursion step            return fibonacci( number - 1 ) + fibonacci( number - 2 );    } // end function fibonacci

**RESULT:**

	$ ./S3_SP_Fibonacci
    fibonacci( 0 ) = 0
    fibonacci( 1 ) = 1
    fibonacci( 2 ) = 1
    fibonacci( 3 ) = 2
    fibonacci( 4 ) = 3
    fibonacci( 5 ) = 5
    fibonacci( 6 ) = 8
    fibonacci( 7 ) = 13
    fibonacci( 8 ) = 21
    fibonacci( 9 ) = 34
    fibonacci( 10 ) = 55
    fibonacci( 20 ) = 6765
    fibonacci( 30 ) = 832040
    fibonacci( 35 ) = 9227465

</br>
<a name="inline_func"/></a>
## Inline Functions
</br>

Implementing a program as a set of functions is good from a software engineering stand- point, but function calls involve execution-time overhead. C++ provides inline functions to help reduce function call overhead — especially for small functions. Placing the qualifier inline before a function’s return type in the function definition “advises” the compiler to generate a copy of the function’s body code in place (when appropriate) to avoid a function call. The trade-off is that multiple copies of the function code are inserted in the program (often making the program larger) rather than there being a single copy of the function to which control is passed each time the function is called. 

##### SIDE PROGRAM # &nbsp;9

Use an inline function to calculate the volume of a cube.

    //
    //  Program Name - S3_SP_InlineFunctionTest.cpp
    //  Series: GetOnToC++ Step: 3 Side Program
    //
    //  Purpose: This program uses an inline function to calculate the volume 
    //			 of a cube.
    //
    //  Compile: g++ S3_SP_InlineFunctionTest.cpp -o S3_SP_InlineFunctionTest
    //  Execute: ./S3_SP_InlineFunctionTest
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>    using namespace std;

    // Definition of inline function cube. Definition of function appears    // before function is called, so a function prototype is not required.    // First line of function definition acts as the prototype.
    inline double cube( const double side )    {        return side * side * side; // calculate cube    } // end function cube

    int main() 
    {
        double sideValue; // stores value entered by user        cout << "Enter the side length of your cube: ";        cin >> sideValue; // read value from user
        // calculate cube of sideValue and display result        cout << "Volume of cube with side "             << sideValue << " is " << cube( sideValue ) << endl;
    } // end main

**RESULT:**

	$ ./S3_SP_InlineFunctionTest
	Enter the side length of your cube: 10
	Volume of cube with side 10 is 1000

</br>
<a name="func_overload"/></a>
## Function Overloading
</br>

C++ enables several functions of the same name to be defined, as long as they have different signatures. This is called **Function Overloading**. The C++ compiler selects the proper function to call by examining the number, types and order of the arguments in the call.

##### SIDE PROGRAM # &nbsp;10

Use overloaded square functions to calculate the square of an int and the square of a double 

    //
    //  Program Name - S3_SP_FuncOverloadTest.cpp
    //  Series: GetOnToC++ Step: 3 Side Program
    //
    //  Purpose: Use overloaded square functions to calculate the square of an int 
    //			 and the square of a double 
    //
    //  Compile: g++ S3_SP_FuncOverloadTest.cpp -o S3_SP_FuncOverloadTest
    //  Execute: ./S3_SP_FuncOverloadTest
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>    using namespace std;

    // Function Prototype to calculate square of int and double value    int square( int x );
    double square( double y );

    int main() 
    {
        cout << square( 7 ); // calls int version
        cout << endl;
        cout << square( 7.5 ); // calls double version
        cout << endl;
    } // end main

    // function square for int values    int square( int x )    {        cout << "square of integer " << x << " is ";        return x * x;    } // end function square with int argument

    // function square for double values    double square( double y )    {        cout << "square of double " << y << " is ";        return y * y;    } // end function square with double argument

**RESULT:**

	$ ./S3_SP_FuncOverloadTest
	square of integer 7 is 49
	square of double 7.5 is 56.25

</br>  
<a name="prog_problem"/></a>
## Programming Problem
</br>  

One of the most popular games of chance is a dice game known as “craps,” which is played in casinos and back alleys worldwide. Write a program that will simulate the Craps Game

**Rules:** A player rolls two dice. Each die has six faces. These faces contain 1, 2, 3, 4, 5 and 6 spots. After the dice have come to rest, the sum of the spots on the two upward faces is calculated. If the sum is 7 or 11 on the first roll, the player wins. If the sum is 2, 3 or 12 on the first roll (called “craps”), the player loses (i.e., the “house” wins). If the sum is 4, 5, 6, 8, 9 or 10 on the first roll, then that sum becomes the player’s “point.” To win, you must continue rolling the dice until you “make your point.” The player loses by rolling a 7 before making the point.

    //
    //  Program Name - S3_MP_CrapsDiceGame.cpp
    //  Series: GetOnToC++ Step: 3 Main Program
    //
    //  Purpose: One of the most popular games of chance is a dice game known 
    //           as “craps,” which is played in casinos and back alleys 
    //           worldwide. This program will simulate the Craps Game
    //
    //  RULES: A player rolls two dice. Each die has six faces. These faces 
    //         contain 1, 2, 3, 4, 5 and 6 spots. After the dice have come 
    //         to rest, the sum of the spots on the two upward faces is 
    //         calculated. If the sum is 7 or 11 on the first roll, the player 
    //         wins. If the sum is 2, 3 or 12 on the first roll (called “craps”), 
    //         the player loses (i.e., the “house” wins). If the sum is 4, 5, 6, 
    //         8, 9 or 10 on the first roll, then that sum becomes the player’s 
    //         “point.” To win, you must continue rolling the dice until you 
    //         “make your point.” The player loses by rolling a 7 before making 
    //         the point.
    //
    //  Compile: g++ S3_MP_CrapsDiceGame.cpp -o S3_MP_CrapsDiceGame
    //  Execute: ./S3_MP_CrapsDiceGame
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>    #include <cstdlib> // contains prototypes for functions srand and rand    #include <ctime> // contains prototype for function time    using namespace std;
    // Function Prototype rollsdice, calculates and displays sum 
    int rollDice(); 

    int main() {
        // enumeration with constants that represent the game status        enum Status { CONTINUE, WON, LOST }; // all caps in constants

        int myPoint; // point if no win or loss on first roll 
        Status gameStatus; // can contain CONTINUE, WON or LOST

        // randomize random number generator using current time        srand( time( 0 ) );

        int sumOfDice = rollDice(); // first roll of the dice

        // determine game status and point (if needed) based on first roll        switch ( sumOfDice ) {            case 7: // win with 7 on first roll            case 11: // win with 11 on first roll
                gameStatus = WON; 
                cout << "Player Rolled: " << sumOfDice << " Hence Wins." << endl;
                break;            case 2: // lose with 2 on first roll            case 3: // lose with 3 on first roll            case 12: // lose with 12 on first roll                gameStatus = LOST;                cout << "Player Rolled: " << sumOfDice << " Hence Lost." << endl;
                break;            default: // did not win or lose, so remember point                gameStatus = CONTINUE; // game is not over 
                myPoint = sumOfDice; // remember the point 
                cout << "Player Rolled: " << sumOfDice << " Hence Continue." 
                     << endl;
                cout << "Point To Reproduce to Win is: " << myPoint << endl; 
                break; // optional at end of switch        } // end switch

        // while game is not complete not won not lost        while ( gameStatus == CONTINUE ) {            sumOfDice = rollDice(); // roll dice again

            // determine game status
            
            // win by making point             if ( sumOfDice == myPoint ) {
                gameStatus = WON;
                cout << "Point Reproduced again. Hence Won" << endl;
                break; // breaking the loop            } 

            // lose by rolling 7 before point
            if ( sumOfDice == 7 ) {                gameStatus = LOST;
                cout << "Lost by Rolling 7" << endl;
                break; // breaking the loop
            } 
        }//end while

        // display won or lost message
        if( gameStatus == WON )
            cout << "Player wins" << endl;
        else cout << "Player Losses" << endl;
    
    } // end main

    /*
     * Function Body - rollDice
     * This function calculate sum and display results
     * Input Param are: -NA-
     * return: the sum of 2 dice
     */    
    int rollDice() {        // pick random die values        int die1 = 1 + rand() % 6; // first die roll 
        int die2 = 1 + rand() % 6; // second die roll    

        int sum = die1 + die2; // compute sum of die values

        // display results of this roll        cout << "Player rolled " << die1 << "+" << die2 << "=" << sum <<endl;        return sum; // end function rollDice 
    } // end function rollDice


**RESULT:**

    $ ./S3_MP_CrapsDiceGame
    Player rolled 3+3=6
    Player Rolled: 6 Hence Continue.
    Point To Reproduce to Win is: 6
    Player rolled 4+1=5
    Player rolled 3+6=9
    Player rolled 6+6=12
    Player rolled 1+1=2
    Player rolled 5+4=9
    Player rolled 5+5=10
    Player rolled 2+1=3
    Player rolled 1+4=5
    Player rolled 1+5=6
    Point Reproduced again. Hence Won
    Player wins

    $ ./S3_MP_CrapsDiceGame
    Player rolled 5+2=7
    Player Rolled: 7 Hence Wins.
    Player wins

    $ ./S3_MP_CrapsDiceGame
    Player rolled 4+1=5
    Player Rolled: 5 Hence Continue.
    Point To Reproduce to Win is: 5
    Player rolled 2+4=6
    Player rolled 5+2=7
    Lost by Rolling 7
    Player Losses

***
**Note:** The enum keyword is used to create an enumerated type, which is a collection of related constants. In the above example to indicate Game Status of Won, Lost or Continue. Enum is covered in more detail in the next step
***