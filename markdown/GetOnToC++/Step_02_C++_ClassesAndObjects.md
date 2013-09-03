# Step 2: Get On To C++ Classes and Objects

The main purpose of C++ programming is to add object orientation to the C programming language and classes are the central feature of C++ that supports object-oriented programming and are often called user-defined types. In this step C++ Classes and Objects are introduced by writing a executable program for the Problem Statement defined below. The Concepts introduced in this step are:

1. [**Declaration of Classes**](#declare_class)
2. [**Declaration of Member Variables**](#member_vars) 
3. [**Declaration of Constructor Functions**](#constructor)
4. [**Declaration of Member Functions**](#member_functions)
5. [**Create Object and set Values to Member Variable**](#create_objects)
6. [**Call Member Function on the Object**](#call_function)

<a name="problem"/></a>
## Problem Statement
#  
In this step lets write same Program as in Step 1 but creates Box Car and Tank Car Object. Write member function to compute the volume of a Box Car and Tank Car and Outputs the result onto the Console.

Here Box Car is a Rectangular Car having length, breadth and height while the tank car is cylindrical having radius and length.

**Main Program**

Lets create a S1_ComputeVolume.cpp file and declare the main function and the place holders for Variables, Input & Output Operators, Functions, and Global Variables.

	//
    //  Program Name - S2_CreateClassesAndObjects.cpp
    //  Series: GetOnToC++ Step: 2
    //
    //  Purpose: This program defines Box Car and Tank Car class. Creates
    //           corresponding objects of Box Car and Tank Car and calls member 
    //			 function to computes the Volume of the Box Car and Tank Car.
    //
    //  Compile: g++ S2_CreateClassesAndObjects.cpp -o S2_CreateClassesAndObjects
    //  Execute: ./S2_CreateClassesAndObjects
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    using namespace std;

    // Global Variables 

    // CurrentYear is a Global Vairable and indicates the current year     
    int gCurrentYear = 2013;

    /*
     * PI is a Global Variable and is also a Mathematical Constant as indicated
     * by const directive. This means PI value cannot be re-assigned.
     */
    const double PI = 3.14159;

    // Section 1A - Box Car Class Defined Here

    // Section 2A - Box Car Class Member Variables Defined Here

    // Section 3A - Box Car Class Constructor Defined Here

    // Section 4A - Box Car Class Member Functions Defined Here

    // Section 1B - Tank Car Class Defined Here

    // Section 2B - Tank Car Class Member Variables Defined Here

    // Section 3B - Tank Car Class Constructor Defined Here

    // Section 4B - Tank Car Class Member Functions Defined Here

    main ( ) { 
        
        // Declaration of Local Variables 

        // Variabes for Box Car
        double length = 0.0, width = 0.0, height = 0.0;
        
        // Vairables for Tank Car which is a Cylinder
        double radius = 0.0, lengthOfTankCar = 0.0;

        // Section 5A - Create BoxCar Object and Assign values to its member 
        // variable
        
        // Section 6A - Calling Member Function volume to calculate the Volume of 
        // BoxCar Object
        
        // Section 5B - Create TankCar Object and Assign values to its member 
        // variable
        
        // Section 6B - Calling Member Function volume to calculate the Volume of 
        // TankCar Object

        // Display the Result
    }

<a name="declare_vars"/></a>
## Section 1: Declaration of Classes
#  
As discussed earlier C++ **built-in data types** are char, short, int, long, float, double, etc. Further C++ encourges building your own data type and data type heirarchies to describe effectively the real-world problems. **These user defined data types are called Classes**. A class is described by its attributes which are called [**Member Vairables**](member_vars) and behaviours which are called [**Member Functions**](member_functions). 

A class definition starts with the keyword class followed by the class name; and the class body, enclosed by a pair of curly braces. A class definition must be followed either by a semicolon or a list of declarations. For example we defined the Circle data type using the keyword class as follows:

	class Circle {
		public:
			int mRadius; // Member Variable Radius of the Circle
		
			double area(); // Member Function computes the Area of the Circle
	}

Here is the diagram representation of class definition:

***
**Note:** The keyword public determines the access attributes of the members of the class that follow it. A public member can be accessed from outside the class anywhere within the scope of the class object. You can also specify the members of a class as private or protected which we will discuss in later steps.
***

A Class is typically identified by the **Noun** in the Problem Statement. 

**SIDE STEP**

**Problem:** Find the area of the Circle whose radius is 10cm.  

**Solution:** Here the noun is the Circle. The attribute or member variables of Cicle is radius. The member functions here is area as it uses the attribute to compute the value. 

    //
    //  Program Name - S2_Circle.cpp
    //  Series: GetOnToC++ Step: 2
    //
    //  Purpose: This program defines Circle and Square Shape and computes its area
    //
    //  Compile: g++ S2_Circle.cpp -o S2_Circle
    //  Execute: ./S2_Circle
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    using namespace std;

    // Use the mathematics library, which contains a declaration for M_PI: 
    #include <math.h>

    class Circle {
        public:
            // Member Variable mRadius. m indicates member vairable
            int mRadius;

            // Member Function
            double area() { 
                // M_PI is a macro defined in Math.h and its value is 3.14159            
                return M_PI*mRadius*mRadius;
            }
    } aCircle; // Note that the class definition ends with semicolon. 
               // Here a global variable aCircle is difined of type Circle

    // Main Function as the execution starts at the main function
    main ( ) { 
        // Section 1 - Declaration of Variables 
        int rad = 10;

        // Assigning value to aCircle Objects member variable
        aCircle.mRadius = rad;

        // Calling the member function on the Object aCircle
        cout << "Area of the Circle = " << aCircle.area() << endl;

        // Calculating the size of Circle class
        // Note since the Circle class holds one integer vairable radius and 
        // hence size of user defined data type Circle is 4 bytes.
        cout << "Size of Circle Class = " << sizeof(Circle) << endl;
        
        // Calculating the size of Circle Object aCircle
        cout << "Size of Circle Object = " << sizeof(aCircle) << endl;
    }

***
**NOTE:** The following can be learnt from the above example: 

1. The example defines the class Circle with member variable mRadius and member function area()
2. The Class Definition ends with semicolon
3. The examples defines a global vairable aCircle of type Circle
4. aCircle is a Object and has a memory size of 4 bytes. 
5. The memory size of class or an object is the addition of size of all its member variables. Since Circle has Integer and hence the size if 4 bytes.
***

**Main Program**

Looking at the [**Problem Statement**](#problem), we can see the nouns are Box Car and Tank Car. The following code defines the BoxCar and TankCar class

    // Section 1A - Box Car Class Defined Here
    class BoxCar {

        // Section 2A - Box Car Class Member Variables Defined Here

        // Section 3A - Box Car Class Constructor Defined Here

        // Section 4A - Box Car Class Member Functions Defined Here

    };

    // Section 1B - Tank Car Class Defined Here
    class TankCar {
        
        // Section 2B - Tank Car Class Member Variables Defined Here

        // Section 3B - Tank Car Class Constructor Defined Here

        // Section 4B - Tank Car Class Member Functions Defined Here

    };

Inside the main function immediately after " main() { " lets write the following statement

        // Size of Box Car and Tank Car Class
        cout << "Size of BoxCar Class = " << sizeof(BoxCar) << " byte" << endl;
        cout << "Size of TankCar Class = " << sizeof(TankCar) << " byte" << endl;

***
**NOTE:** You will notice the following output

Size of BoxCar Class = 1 byte

Size of TankCar Class = 1 byte

Since no Vairable is assigned to BoxCar and TankCar class hence the minimum memory size of 1 byte is assigned to the class
  
***

<a name="member_vars"/></a>
## Section 2: Declaration of Member Variables
#  

Member Variables are 
When you define a class, you tell C++ about the variables that describe the objects 
that belong to that class. Note that you also can define functions that work with those objects. You might, for example, define a volume function that knows how to find values for any box-car object's height, width, and length variables, and that knows how to use those values to compute the box-car object's volume.

<a name="constructor"/></a>
## Section 3: Declaration of Constructor Functions
#  

<a name="member_functions"/></a>
## Section 4: Declaration of Member Functions
#  

<a name="create_objects"/></a>
## Section 5: Create Object and set Values to Member Variable
#  

<a name="call_function"/></a>
## Section 6: Call Member Function on the Object
#  


