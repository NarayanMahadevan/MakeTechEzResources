# Step 2: Get On To C++ Classes and Objects

The main purpose of C++ programming is to add object orientation to the C programming language and classes are the central feature of C++ that supports object-oriented programming and are often called user-defined types. In this step C++ Classes and Objects are introduced by writing a executable program for the Problem Statement defined below. The Concepts introduced in this step are:

1. [**Declaration of Classes**](#declare_class)
2. [**Declaration of Member Variables**](#member_vars) 
3. [**Declaration of Member Functions**](#member_functions)
4. [**Create Object and set Values to Member Variable**](#create_objects)
5. [**Call Member Function on the Object**](#call_function)

Finally the end of the Section 

a. [**Displays the result**](#result) of the [**Program**](#problem) defined below and
b. Gives [**Practice Problems**](#practice) for Development

<a name="problem"/></a>
# Problem Statement
  
In this step lets write same Program as in Step 1 but creates Box Car and Tank Car Object. Write member function to compute the volume of a Box Car and Tank Car and Outputs the result onto the Console.

Here Box Car is a Rectangular Car having length, breadth and height while the tank car is cylindrical having radius and length.

<a name="main_code"/></a>
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

    // Section 1B - Tank Car Class Defined Here

    main ( ) { 
        
        // Declaration of Local Variables 

        // Variabes for Box Car
        double length = 0.0, width = 0.0, height = 0.0;
        
        // Vairables for Tank Car which is a Cylinder
        double radius = 0.0, lengthOfTankCar = 0.0;

        // Section 4A - Create BoxCar Object and Assign values to its member 
        // variable
        
        // Section 5A - Calling Member Function volume to calculate the Volume of 
        // BoxCar Object
        
        // Section 4B - Create TankCar Object and Assign values to its member 
        // variable
        
        // Section 5B - Calling Member Function volume to calculate the Volume of 
        // TankCar Object

    }

<a name="declare_vars"/></a>
# Section 1: Declaration of Classes
  
As discussed earlier C++ **built-in data types** are char, short, int, long, float, double, etc. Further C++ encourges building your own data type and data type heirarchies to describe effectively the real-world problems. **These user defined data types are called Classes**. A class is described by its attributes which are called [**Member Vairables**](member_vars) and behaviours which are called [**Member Functions**](member_functions). 

A class definition starts with the keyword class followed by the class name; and the class body, enclosed by a pair of curly braces. A class definition must be followed either by a semicolon or a list of declarations. For example we defined the Circle data type using the keyword class as follows:

	class Circle {
		public:
			int mRadius;   	// Member Variable Radius of the Circle
			Circle(); 		// Default Constructor
			double area(); 	// Member Function computes the Area of the Circle
	}

The Circle class is implemented in [**Side Step: 4**](#side_step_4). Here is the diagram representation of class definition:
</br>  
![Class Definition](/Users/narayan/Documents/MakeTechEzResources/images/GetOnToC++/ClassDefinition.png "Class Definition") 
<!--
![Class Definition](https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToC++/ClassDefinition.png "Class Definition") 
-->
</br>  

***
**Note:** The keyword public determines the access attributes of the members of the class that follow it. A public member can be accessed from outside the class anywhere within the scope of the class object. You can also specify the members of a class as private or protected which we will discuss in later steps.
***

**A Class is typically identified by the *Noun* in the Problem Statement. **

<a name="side_step_1"/></a>
**SIDE STEP :1 Define Simple Class** 

**Problem:** Demonstrated Class Definition using a Counter Class to maintain the count value

**Solution:** Here the noun is the Counter. The attribute or member variables of Counter is count. More details on Member Vairables will be covered in next section

    //
    //  Program Name - S2_Counter.cpp
    //  Series: GetOnToC++ Step: 2
    //
    //  Purpose: This program Demonstrated Class Definition using a Counter 
    //           Class to maintain the count
    //
    //  Compile: g++ S2_Counter.cpp -o S2_Counter
    //  Execute: ./S2_Counter
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    using namespace std;

    class Counter {
        public:
            // Member Variable count to store the counter value. 
            // The starting char m indicates member vairable
            int mCount;

    } aCounter; // Note that the class definition ends with semicolon. 
                // Here a global variable aCounter is difined of type Counter

    // Main Function as the execution starts at the main function
    main ( ) { 
        // Section 1 - Declaration of Variables 
        int count = 10;

        // Assigning value to aCounter member variable.
        // Notice that the member variable mCounter is accessed using access 
        // operator (.) 
        aCounter.mCount = count;

        // Printing the counter value using mCounter Objects member vairable 
        cout << "Assigned value = " << count <<
                " And Objects mCount Value = " << aCounter.mCount << endl;

        // Calculating the size of Counter class and Counter Object. Both are same. 
        // Note since the Counter class holds one integer vairable radius and 
        cout << "Size of Counter Class = " << sizeof(Counter) << endl 
             << "Same as sizeof(int), which is = " << sizeof(int) << endl  
             << "Same as Size of Counter Object = " << sizeof(aCounter) << endl;
        
    }

***
**NOTE:** The following can be learnt from the above example: 

1. The example defines the class Counter with member variable mCount
2. The Class Definition ends with semicolon
3. The examples defines a global vairable aCounter of type Counter
4. aCounter is a Object and has a memory size of 4 bytes. 
5. The memory size of class or an object is the addition of size of all its member variables. Since Counter has an Integer and hence the size if 4 bytes.
***

<a name="class_code"/></a>
**Main Program**

Looking at the [**Problem Statement**](#problem), we can see the nouns are Box Car and Tank Car. The following code defines the BoxCar and TankCar class. Please insert the code in appropriate sections of the [**Main Code**](#main_code) 

    // Section 1A - Box Car Class Defined Here
    class BoxCar {

        // public accessor Specifies member variables and functions can be accessed 
        // outside the class anywhere within the scope of the class object.
        public:
        
            // Section 2A - Box Car Class Member Variables Defined Here

            // Section 3A - Box Car Class Member Functions Defined Here

    };

    // Section 1B - Tank Car Class Defined Here
    class TankCar {
        
        // public accessor Specifies member variables and functions can be accessed 
        // outside the class anywhere within the scope of the class object.
        public:
        
            // Section 2B - Tank Car Class Member Variables Defined Here

            // Section 3B - Tank Car Class Member Functions Defined Here

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
# Section 2: Declaration of Member Variables
  

Member Variables are attributes that describe the class. Like radius is the attribute of a circle or length is the attribute of the square. Member Vairables appear inside the class definition. The memory size of the class or the object is determined by the memory size of the member variables. This member variables are also called **Instance Variable**. As the memory for the member vairable is allocated when an Instance of a Class i.e. is the Object is created. 

<a name="side_step_2"/></a>
**SIDE STEP :2 Define Class and Member Vairable** 

**Problem Statment:** Determine the Volume of the 2 Boxes, one is 4.0, 6.0, 8.0 feet while the other is 10.0, 12.0 and 14.0 feet 

This program demonstrates declaration of Member Variables of Box class, creation of Box Object and calculating volume of the Box.

    //
    //  Program Name - S2_Box.cpp
    //  Series: GetOnToC++ Step: 2
    //
    //  Purpose: This program demonstrates declaration of Member Variables of Box 
    //           class, creation of Box Object and calculating volume of the Box.
    //
    //  Compile: g++ S2_Box.cpp -o S2_Box
    //  Execute: ./S2_Box
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>

    using namespace std;

    class Box
    {
       public:
          double mLength;   // Length of a box
          double mWidth;    // Width of a box
          double mHeight;   // Height of a box
    };

    /*
     * This function calculates the Volume of the Box 
     * Input Param: box Object of user defined data type Box
     * return: volume of the Box
     * Note: Here the scope of box Parameters is local to this function 
     * and hence it is call-by-value and the box object will have its own
     * memory
     */    
    double volumeOfBox(Box box) {
        double boxCarVol = 0.0;
        
        // Box Car Volume Computation using Arithmatic Operations
        boxCarVol = box.mHeight * box.mWidth * box.mLength;
        
        // Returns the Box Car Volume
        return boxCarVol;
    }

    int main( )
    {
        // Creating box1 and box2 as Object of Box Class
        Box box1;        // Declare instance box1 of type Box
        Box box2;        // Declare instance box2 of type Box
       
        // Since memory is allocated, box1 and box2 will have definite 
        // memory size. 

        // Calculating the size of box1 Object
        cout << "Size of box1 Object = " << sizeof(box1) << endl;

        // Calculating the size of box2 Object
        cout << "Size of box2 Object = " << sizeof(box2) << endl;
        
        double volume = 0.0;     // Store the volume of a box here
     
        // box 1 specification. Assigning value to member variables
        box1.mHeight = 4.0; 
        box1.mLength = 6.0; 
        box1.mWidth = 8.0;

        // box 2 specification
        box2.mHeight = 10.0;
        box2.mLength = 12.0;
        box2.mWidth = 14.0;
       
        // volume of box 1
        volume = volumeOfBox(box1);
        cout << "Volume of Box1 : " << volume <<endl;

        // volume of box 2
        volume = volumeOfBox(box2);
        cout << "Volume of Box2 : " << volume <<endl;
        return 0;
    }

***
**Note No 1: ** volumeOfBox function takes Box Data Type as a function parameter. The Box Object that is passed to the function is passed as Call-by-Value. This means the function parameter box Object as its own memory and the values of its member veriable is copied from the object that is passed. In this case box1 and box2 for volume computation

**Note No 2: **

sizeOf(box1) = sizeOf(box1.length) +  sizeOf(box1.height) + 
               sizeOf(box1.width);

sizeOf(box2) = sizeOf(box2.length) +  sizeOf(box2.height) + 
               sizeOf(box2.width);

You will notice Memory sizeOf(box1) = Memory sizeOf(box2) = 8 + 8 + 8 = 24 bytes
***
 
**Main Program**

Looking at the [**Problem Statement**](#problem), we can see the attributes of Box Car are length, width and height and that of Tank Car are the radius and the length of the Tank Car Cylinder. The following code defines the attributes of BoxCar and TankCar class. Please insert the code in appropriate sections of the [**Class Code**](#class_code) 

            // Section 2A - Box Car Class Member Variables Defined Here
            // Attributes of Box Car are length, width and height
            double mLength, mWidth, mHeight; 
            
            // Section 2B - Tank Car Class Member Variables Defined Here
            // Attributes of Tank Car are radius and length
            double  mRadius, mLength; 
            

<a name="member_functions"/></a>
# Section 3: Declaration of Member Functions  

Member functions are part of a class and are basically behaviours or actions defined in the class. Member functions use the member variables to describe the behaviour or to compute results or to take actions. 

Member functions are similar to ordinary functions, small but important changes in syntax distinguish the member function from ordinary function. It is in the way the member functions are invoked on the class object using the class-member operator.

Member-function definitions differ from ordinary function definitions in the following respects:

a. Member functions have no parameter corresponding to the class-object argument. Instead class-object is joined by class-member operator, a period, to the name of the member function, in a manner reminiscent of member variable references.
b. In member functions, there are no parameters or variables connected to member variables via the class-member operator; instead, all member variables are taken to belong to the class-object argument. Thus, you define volume as a member function as follows:

		class FlatCar { 
  			public: 
  			double width, length; 
        	double volume ( ) { 
          		// Member Function volume can directly access the member vairables 
          		return 1 * width * length; 
        	} 
		} myFlatCar; 

Hence to call the volume function on FlatCar, its written as `myFlatCar.volume ()`. Here myFlatCar is the class object joined by class-operator "." invoking the member function volume.

<a name="side_step_3"/></a>
**SIDE STEP :3 Define Class, Member Vairable and Member Functions** 

**Problem Statment:** Find the area of the Circle whose radius is 10cm. 

**Solution:** Here the noun is the Circle. The attribute or member variables of Cicle is radius. The member functions here is area as it uses the attribute to compute the value. More details on Member Vairables and Member functions will be covered in next section

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

        // This method is a Member Function as it computes the area using 
        // attribute of the circle.
        // Member Functions are covered in the Section 4 of Step 2
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

        // Assigning value to aCircle Objects member variable.
        // Notice that the member variable mRadius is accessed using access 
        // operator (.) 
        aCircle.mRadius = rad;

        // Notice that the area() function takes Circle Data type as Parameter
        cout << "Area of the Circle = " << aCircle.area() << endl;

        // Calculating the size of Circle class
        // Note since the Circle class holds one integer vairable radius and 
        // hence size of user defined data type Circle is 4 bytes.
        cout << "Size of Circle Class = " << sizeof(Circle) << endl;
        
        // Calculating the size of Circle Object aCircle
        cout << "Size of Circle Object = " << sizeof(aCircle) << endl;
    }

**Main Program**

Looking at the [**Problem Statement**](#problem), we can define volume member function to compute volume of the box car and tank car. Please copy appropriately paste in section 3A and 3B in the [**Program**](#class_code) defined above.
             
            // Section 3A - Box Car Class Member Functions Defined Here

            /*
             * This member function calculates the Volume of the Box Car
             * return: volume of the Box Car
             * Note: volume is the class member function and can directly access 
             *       the member variables 
             */    
            double volume() {
                /*
                 * The scope of the boxCarVol variable is local to this function.
                 * This means the memory is not available outside the function.
                 * The local variable boxCarVol stores the volume of the Box Car
                 */        
                double boxCarVol = 0.0;
                
                // Box Car Volume Computation using Arithmatic Operations
                boxCarVol = mHeight*mWidth*mLength;
                
                // Returns the Box Car Volume
                return boxCarVol;
            }
            
            
            // Section 3B - Tank Car Class Member Functions Defined Here

            /*
             * This function calculates the Volume of the Tank Car
             * return: volume of the Tank Car
             * Note: volume is the class member function and can directly access 
             *       the member variables 
             */    
            double volume() {
                /*
                 * The scope of the tankCarVol variable is local to this function.
                 * This means the memory is not available outside the function.
                 * The local variable tankCarVol stores the volume of the Tank Car
                 */        
                double tankCarVol = 0.0;
                
                // Tank Car Volume Computation using Arithmatic Operations
                // M_PI is a macro defined in Math.h and its value is 3.14159            
                tankCarVol = M_PI * mRadius * mRadius * mLength;
                
                // Returns the Tank Car Volume
                return tankCarVol;
            }
            

<a name="create_objects"/></a>
# Section 4: Create Object and set Values to Member Variable
  

Once the BoxCar and TankCar class is defined, the variable for the user defined data type can be introduced as `BoxCar myBoxCar;` for BoxCar class and `TankCar myTankCar;` for TankCar class. Here Object and hence the memory for the member variables is created for BoxCar and TankCar class and can be accessed using the Objects myBoxCar and myTankCar.

The member vairables of BoxCar and TankCar class can be accessed using the Object followd by **class-member operator i.e. "."**. Thus myBoxCar.mHeight accessess the height member variable of BoxCar Object. This can be used to assign value and subsequently retrieve value from the Object's member vairable. 

**Main Program**

The following codes creates BoxCar and TankCar Object and correspondingly sets the value for its member variables. Please copy appropriately paste in section 4A and 4B in the [**Program**](#main_code) defined above.

        // Section 4A - Create BoxCar Object and Assign values to its member 
        // variable

        // Read in the Variables of Box Car and Tank Car
        cout << "Please Enter the Length, Width and Height of the Box Car." 
        	     << endl;
        cin >> length >> width >> height;  

        // Creating myBoxCar object for user defined class BoxCar. Once BoxCar
        // Object is created, corresponding memory for the member variable is 
        // created and can be accessed using the myBoxCar object.         
        BoxCar myBoxCar;

        // Assigning values to the Objects Member Variable
        myBoxCar.mLength = length; 
        myBoxCar.mHeight = height; 
        myBoxCar.mWidth = width; 
        
        // Section 4B - Create TankCar Object and Assign values to its member 
        // variable
        
        cout << "Please Enter the Radius and Length of the Tank Car." << endl;
        cin >> radius >> lengthOfTankCar;  
        
        // Creating myTankCar object for user defined class TankCar. Once TankCar
        // Object is created, corresponding memory for the member variable is 
        // created and can be accessed using the myTankCar object.         
        TankCar myTankCar;

        // Assigning values to the Objects Member Variable
        myTankCar.mLength = lengthOfTankCar; 
        myTankCar.mRadius = radius; 


<a name="call_function"/></a>
# Section 5: Call Member Function on the Object  

The member functions of BoxCar and TankCar class can be accessed using the Object followd by **class-member operator i.e. "."**. Hence to call the volume function on BoxCar Object, its written as `myBoxCar.volume ()`. Here myBoxCar is the class object joined by class-operator "." invoking the member function volume.

**Main Program**

The following codes calls the volume member function of BoxCar and TankCar Object. Please copy appropriately paste in section 5A and 5B in the [**Program**](#main_code) defined above.

        // Section 5A - Calling Member Function volume to calculate the Volume of 
        // BoxCar Object
        cout << "The Volume of the Box Car Object of lth: " << myBoxCar.mLength 
             << " Wt: " << myBoxCar.mWidth << " and Ht: " << myBoxCar.mHeight
             << " is " << myBoxCar.volume() << endl;

        // Section 5B - Calling Member Function volume to calculate the Volume of 
        // TankCar Object
        cout << "The Volume of the Tan Car Object of lth: " << myTankCar.mLength 
             << " And Rad: " << myTankCar.mRadius << " is " << myTankCar.volume()
             << endl;
    
        // Memory Size of Box Car and Tank Car Class is same as their Objects
        cout << "Memory of BoxCar Class = " << sizeof(BoxCar) << endl;
        cout << "Memory of TankCar Class = " << sizeof(TankCar) << endl;        
  
<a name="result"/></a>
# Display Program Result  

The following displays the Compilation, Execution, Inputs and Outputs of the [**Main Program**](#main_code) developed in this step

***

Enter the Following in Command Prompt for first Compilation and then Executiom

`$ g++ S2_CreateClassesAndObjects.cpp -o S2_CreateClassesAndObjects`

`$ ./S2_CreateClassesAndObjects `

Please Enter the Length, Width and Height of the Box Car.

10 10 10

The Volume of the Box Car Object of lth: 10 Wt: 10 and Ht: 10 is 1000

Please Enter the Radius and Length of the Tank Car.

10 10

The Volume of the Tan Car Object of lth: 10 And Rad: 10 is 3141.59

Memory of BoxCar Class = 24

Memory of TankCar Class = 16

***

<a name="practice"/></a>
# Practice Problem for Development  

1. Device a FlatCar class for Flat Cars and device a volume function if the flat cars are loaded to a maximum height of 8.25 feet 

2. Calculate the age of BoxCar and TankCar. For this do the following 
   a. Define member variable `int mYearBuilt; // Year Built` for Box Car and Tank Car 
   b. Take user input to specify the value for the mYearBuilt member variable
   c. Define `int age()`  member function that returns the current age of the Box Car and Tank Car. 