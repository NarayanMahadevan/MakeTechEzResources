# Step 5: &nbsp;C/C++ Pointers
</br>

This chapter discusses one of the most powerful features of the C/C++ programming language, the **pointer**. Pointers are considered as the most difficult capability to master. In the previous step we saw references to the memory location were passed  as **call-by-reference** function parameters. Call-by-reference parameters share the common memory chuck and nothing is copied. Pointers enable call-by-reference and to create and manipulate dynamic data structures that can grow and shrink, such as linked lists, queues, stacks and trees. 

The Objective of this step is to explain the basic pointer concepts - pointer declaration, initialization, pointer expressions and pointer arthmatics. Further this step explans calling function by reference, function pointers and relationship among Arrays and Pointers. The concepts introduced in this step are:

1. [**Pointer Variable Declaration and Initialization**](#ptr_var)

2. [**Pointer Operators**](#ptr_oper)

3. [**Calling Function by Reference**](#call_by_ref)

4. [**Using Const Qualifier with Pointers**](#const_ptr)

5. [**Relationship between Pointers and Arrays**](#ptr_and_array)

6. [**Arrays of Pointers**](#array_ptrs)

7. [**Function Pointers**](#func_ptrs)


</br>
<a name="ptr_var"/></a>
## Pointer Variable Declaration and Initialization
</br>

Pointer variables contain memory addresses as their values. Normally, a variable directly contains a specific value. A pointer contains the memory address of a variable that, in turn, contains a specific value. In this sense, a variable name directly references a value, and a pointer indirectly references a value as can be seen in the figure below. Referencing a value through a pointer is called indirection. 

Pointers, like any other variables, must be declared before they can be used. For example, for the pointer in the figure below, the declaration is as follows

	int *yPtr; // declare pointer variable yPtr
	*yPtr = 5; // dereferencing a pointer using * for variable assignment

Lets represent `yptr` with a diagram. Diagrams typically represent a pointer as an arrow from the variable that contains an address to the variable located at that address in memory.

**Graphical Representattion of a Pointer pointing to a Interger in the memory**

![Pointer pointing to an Integer][1]

[1]: /Users/narayan/Documents/MakeTechEzResources/images/GetOnToC++/S5_PointerRef.png "Pointer pointing to an Integer"

<!--
[1]: https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToC++/S5_PointerRef.png "Pointer pointing to an Integer" 
-->

The above figure shows schematic representation of memory after the assignment `*yPtr = 5;`. The “pointing relationship” is indicated by drawing an arrow from the box that represents the pointer yPtr in memory to the box that represents the Integer value in memory.

**Graphical Representation of Integer Value and yPtr in memory**

![Memory Location of Integer Value and yPtr][2]

[2]: /Users/narayan/Documents/MakeTechEzResources/images/GetOnToC++/S5_PointerLocation.png "Memory Location of Integer Value and yPtr"

<!--
[2]: https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToC++/S5_PointerLocation.png "Memory Location of Integer Value and yPtr"
-->

The Figure above shows another pointer representation in memory with integer value 5 stored at memory location 600000 and pointer variable yPtr stored at memory location 500000. As can be seen in the figure the contents of yPtr is the memory address holding the Integer Value 5.

#### Pointer Initialization

Pointers should be initialized to 0, NULL or an address of the corresponding type either when they’re declared or in an assignment. A pointer with the value 0 or NULL “points to nothing” and is known as a null pointer. Symbolic constant NULL is defined in several stan- dard library headers to represent the value 0. Initializing a pointer to NULL is equivalent to initializing a pointer to 0, but in C++, 0 is used by convention. When 0 is assigned, it’s converted to a pointer of the appropriate type. The value 0 is the only integer value that can be assigned directly to a pointer variable without first casting the integer to a pointer type. 

##### SIDE PROGRAM # &nbsp;1

Write a program that demonstrates pointer declaration and assignment.

    //
    //  Program Name - S5_SP_PointerDemo.cpp
    //  Series: GetOnToC++ Step: 5 Side Program
    //
    //  Purpose: This program demonstrates pointer declaration and assignment.
    //
    //  Compile: g++ S5_SP_PointerDemo.cpp -o S5_SP_PointerDemo
    //  Execute: ./S5_SP_PointerDemo
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>    using namespace std;
    int main() 
    {
        // Declare pointer variable yPtr which is a pointer to an integer.
        // If not initialized to null, then the yPtr by default is assigned a 
        // memory location having the value 0. While initializing the pointer 
        // to null will ensure no memory is allocated during declaration.
        
        // Note that If initialized to null then the assignment statement of 
        // *yPtr = 5 will lead to segmentation fault as no memory is allocated
        // to the Pointer 
        int *yPtr; 

        // Printing yPtr before assignment.
        cout << "As no initialization is done yPtr is pointing to default memory: " 
             << yPtr << " having default value: " << *yPtr << endl;
        
        // dereferencing a pointer using * for variable assignment
        *yPtr = 5; 

        cout << "\nThe value of yPtr is a memory address: " << yPtr << endl;
        cout << "The value stored in the memory address can be accessed using " 
             << "*yPtr: " << *yPtr << endl;

        cout << "\nThe sizeof memory stored by Pointer: " << sizeof(yPtr)
             << "\nAnd the sizeof memory stored by content of the pointer is: "
             << sizeof(*yPtr) << " bytes and is same as memory size of int" 
             << endl;

    } // end main


RESULT:

    $ ./S5_SP_PointerDemo
    As no initialization is done yPtr is pointing to default memory: 0x7fff5a147b18 	having default value: 0
    
    The value of yPtr is a memory address holding a Integer Value: 0x7fff5a147b18
    The value stored in the memory address can be accessed using *yPtr: 5
    
    The sizeof memory stored by Pointer: 8
    And the sizeof memory stored by content of the pointer is: 4 bytes and is same 	as memory size of int

</br>
<a name="ptr_oper"/></a>
## Pointer Operators
</br>

The Pointer Operators are the 

- **&, or address operator -** This is a unary operator that returns the address of its operand; So in the below code sample `countPtr = &count;`, assigns the memory address of variable count to pointer variable countPtr. Variable countPtr is said to point to count.

		int count = 7; // count is an integer
		int *countPtr; // countPtr is a pointer pointing to an integer
		countPtr = &count; // countPtr is set to the address of count

![Pointer Referencing a Variable][3]

[3]: /Users/narayan/Documents/MakeTechEzResources/images/GetOnToC++/S5_PointerRefVariable.png "Pointer Referencing a Variable"

<!--
[3]: https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToC++/S5_PointerRefVariable.png "Pointer Referencing a Variable" 
-->

- **\*, or indirection operator or dereferencing operator -** This is a unary operator that when used in conjunction with a pointer variable can either be used for retrieval of value the pointer is pointing to or assigning the value to the variable the pointer is pointing to.

		// Prints the value stored in the memory where the countPtr pointer is 
		// pointing
		cout << *countPtr << endl; 
		// Similary to statement below
		cout << count << endl;
		
		// Assignment Statement to assign value by dereferencing the pointer
		*countPtr = 9;
		
		// Dereferencing the pointer may also be used to receive input value
		cin >> *countPtr;

####Operator precedence and associativity

</br>
![Operator precedence and associativity][4]

[4]: /Users/narayan/Documents/MakeTechEzResources/images/GetOnToC++/S5OperatorAssociativity.png "Operator precedence and associativity"

<!--
[4]: https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToC++/S5OperatorAssociativity.png "Operator precedence and associativity"
-->
</br>

##### SIDE PROGRAM # &nbsp;2

Write a program that demonstrates & (address) and *(dereferencing) pointer operators.

    //
    //  Program Name - S5_SP_PointerOperatorDemo.cpp
    //  Series: GetOnToC++ Step: 5 Side Program
    //
    //  Purpose: This program demonstrates & and * pointer operators.
    //
    //  Compile: g++ S5_SP_PointerOperatorDemo.cpp -o S5_SP_PointerOperatorDemo
    //  Execute: ./S5_SP_PointerOperatorDemo
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>    using namespace std;
    int main() 
    {
        // Local Variable

        int y = 5; // y is an integer 

        // Declare pointer variable yPtr which is a pointer to an integer.
        // Here yPtr is initialized to null, equivalent to initializing to 0 
        // i.e. int *yPtr = 0; Initializing the pointer to null will ensure no 
        // memory is allocated during declaration
        // Note that If initialized to null then the assignment statement of 
        // *yPtr = 5 will lead to segmentation fault till some memory is assigned
        // to the Pointer 
        int *yPtr = NULL; 

        // Printing yPtr before assignment.
        // Note that printing the content of yPtr i.e. *yPtr will result in
        // Segmentation Fault as the yPtr memory is not yet allocated or assigned
        cout << "As yPtr is initialized to null, hence value of yPtr is: " 
             << yPtr << endl;
             
        // yPtr is set the address of y in other words yPtr is pointing to y
        yPtr = &y; 

        cout << "\nThe address of y is " << &y             << "\nThe value of yPtr is " << yPtr << endl;        cout << "\nThe value of y is " << y             << "\nThe value of *yPtr is " << *yPtr << endl;
        
        // If the value is updated and since yPtr is pointing to the same memory, 
        // hence the value of yPtr will be 9
        y = 9;

        cout << "\nThe updated value of y after y = 9 is " << y             << "\nThe updated value of *yPtr is " << *yPtr << endl;

        // Similar case as above, since the variable y and yPtr are pointing to 
        // the same memory, updating one will update the other
        *yPtr = 11;

        cout << "\nThe Updated value of y after *yPtr = 11 is " << y             << "\nThe updated value of *yPtr is " << *yPtr << endl;


        // As you can see the output the memory address of the content of the 
        // yPtr is same as the content in the address of the yPtr        cout << "\nShowing that * and & are inverses of each other." 
             << " \n&*yPtr = " << &*yPtr             << "\n*&aPtr = " << *&yPtr << endl;

    } // end main

**RESULT:**

    $ ./S5_SP_PointerOperatorDemo
    As yPtr is initialized to null, hence value of yPtr is: 0

    The address of y is 0x7fff5a5efaf4
    The value of yPtr is 0x7fff5a5efaf4

    The value of y is 5
    The value of *yPtr is 5

    The updated value of y after y = 9 is 9
    The updated value of *yPtr is 9

    The Updated value of y after *yPtr = 11 is 11
    The updated value of *yPtr is 11

    Showing that * and & are inverses of each other. 
    &*yPtr = 0x7fff5a5efaf4
    *&aPtr = 0x7fff5a5efaf4


</br>
<a name="call_by_ref"/></a>
## Calling Function by Reference
</br>

There are two ways in C++ to pass arguments to a function pass-by-value and pass-by-reference also referred as call-by-value and call-by-reference. When function arguments are passed by reference, either the memory address of the variable can be passed or the pointer can be directly passed. Such arguments enable the called function to modify the original values of the arguments in the caller. Reference arguments also enable programs to pass large data objects to a function and avoid the overhead of passing the objects by value.

When calling a function with an argument that should be modified, the address of the argument is passed. This is normally accomplished by applying the address operator (&) to the name of the variable whose value will be modified. In such a scenario the indirection operator (*) is used in the function definition and the body to form a synonym for the name of the variable. This pointer variable in turn can be used to modify the variable’s value at that location in the caller’s memory. Call by Value and Call by  reference is illustrated in the Side Program # 3.

As seen in Step 4, arrays are not passed using operator &, because the name of the array is the pointing to the starting memory location of the array (i.e., an array name is already a pointer). The name of the array i.e. arrayName is equivalent to `&arrayName[0]`. 

##### SIDE PROGRAM # &nbsp;3

Write a program that demonstrates passing arguments to a function using pass-by-value and pass-by-reference

    //
    //  Program Name - S5_SP_PassByRefDemo.cpp
    //  Series: GetOnToC++ Step: 5 Side Program
    //
    //  Purpose: This program demonstrates passing arguments to a function using
    //           pass-by-value and pass-by-reference
    //
    //  Compile: g++ S5_SP_PassByRefDemo.cpp -o S5_SP_PassByRefDemo
    //  Execute: ./S5_SP_PassByRefDemo
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //


    #include <iostream>    using namespace std;
    // Function  Prototype

    // This function demonstrates passing variable by value
    int cubeByValue( int ); 

    // This function demonstrates passing variable by reference
    void cubeByReference( int * );

    // This function demonstrates important rule of passing variable by reference
    void passByReferenceTest( int * );
    int main()    {
        int number = 5;        cout << "The original value of number is " << number 
             << "\nAnd Memory Address: " << &number << endl;

        // Pass number by value to cubeByValue        number = cubeByValue( number );         cout << "\nThe new value of number is " << number 
             << "\nAnd Memory Address: " << &number << endl;

        // Resetting the number back to 5
        number = 5;

        // Pass number address to cubeByReference        
        cubeByReference( &number );         cout << "\nThe new value of number is " << number
             << "\nAnd Memory Address: " << &number << endl;

        // Passing By Reference Test
        cout << "\nPassing By Reference Test" 
             << "\n-------------------------" << endl;

        int y = 10, *yPtr = &y;
        cout << "\nThe updated value of y is: " << y 
             << " And Memory Address is: " << &y
             << "\nThe value of yPtr is: " << *yPtr 
             << " And Memory Address is: " << yPtr << endl;

        passByReferenceTest(yPtr);

        cout << "\nThe value of y is: " << y 
             << " And Memory Address is: " << &y
             << "\nThe value of yPtr is: " << *yPtr 
             << " And Memory Address is: " << yPtr << endl;
    } //end main

    // This function demonstrates passing variable by value.
    // This function calculates and return cube of integer argument    int cubeByValue( int n )    {
        cout << "\nIn cubeByValue( int n ) function:"
             << "\n----------------------------------" 
             << "\nThe value of n passed by value is " 
             << n << "\nAnd Memory Address: " << &n << endl;
        return n * n * n; // cube local variable n and return result    } // end function cubeByValue

    // This function demonstrates passing variable by reference
    // calculate cube of *nPtr; modifies variable number in main    void cubeByReference( int *nPtr )    {        cout << "\nIn cubeByReference( int *nPtr ) function: "
             << "\n-------------------------------------------" 
             << "\nThe value of nPtr passed by reference is " << *nPtr 
             << "\nAnd Memory Address: " << nPtr << endl;
        *nPtr = *nPtr * *nPtr * *nPtr; // cube *nPtr    } // end function cubeByReference

    // This function demonstrates important rule of passing variable by reference
    //
    // Notice 1: Since it is pass by reference xPtr can modify the value and the 
    //           same value will be reflected by variable y and the yPtr   
    //
    // Notice 2: xPtr points to the same memory location as yPtr. xPtr can 
    //           legally point to new Memory address but will not affect the yPtr
    //
    void passByReferenceTest( int *xPtr ) 
    {
        cout << "\nIn Function passByReferenceTest(): "
             << "\n----------------------------------" 
             << "\nThe value of xPtr is " << *xPtr 
             << " And Memory Address is: " << xPtr << endl;

        // The value is modified to 50 through the dereferenced pointer
        *xPtr = 50;         cout << "The updated value of xPtr is " << *xPtr 
             << " And Memory Address is: " << xPtr << endl;

        // xPtr is modified to point to variable b
        int b = 100;
        xPtr = &b; 
        cout << "The value of updated xPtr is " << *xPtr 
             << " And Memory Address is: " << xPtr << endl;
    } // end function passByReferenceTest


**RESULT:**

    ./S5_SP_PassByRefDemo
    The original value of number is 5
    And Memory Address: 0x7fff5e599b04

    In cubeByValue( int n ) function:
    ----------------------------------
    The value of n passed by value is 5
    And Memory Address: 0x7fff5e599a7c

    The new value of number is 125
    And Memory Address: 0x7fff5e599b04

    In cubeByReference( int *nPtr ) function: 
    -------------------------------------------
    The value of nPtr passed by reference is 5
    And Memory Address: 0x7fff5e599b04

    The new value of number is 125
    And Memory Address: 0x7fff5e599b04

    Passing By Reference Test
    -------------------------

    The updated value of y is: 10 And Memory Address is: 0x7fff5e599b00
    The value of yPtr is: 10 And Memory Address is: 0x7fff5e599b00

    In Function passByReferenceTest(): 
    ----------------------------------
    The value of xPtr is 10 And Memory Address is: 0x7fff5e599b00
    The updated value of xPtr is 50 And Memory Address is: 0x7fff5e599b00
    The value of updated xPtr is 100 And Memory Address is: 0x7fff5e599a74

    The value of y is: 50 And Memory Address is: 0x7fff5e599b00
    The value of yPtr is: 50 And Memory Address is: 0x7fff5e599b00


***
**Note:** We can see the following in the Side Program above

1. Memory Address of variable `int number` defined in main is: 0x7fff5e781b04
2. Memory Address of variable `int n` defined in cubeByValue is: 0x7fff5e781aac
3. Memory Address of variable `int *nPtr` defined in cubeByReference is: 0x7fff5e781b04
4. **Notice # 1:** The memory address of variable n in cubeByValue is different from the memory address of variable number defined in main. This means a new memory is created for variable n and the value is copied. This is pass-by-value 
5. **Notice # 2:** The memory address of variable nPtr in cubeByReference is same as the memory address of variable number defined in main. This means the memory is shared or the same for variable nPtr and number. This is pass-by-reference
6. **Notice # 3:** As you can see in `passByReferenceTest()` function, xPtr points to the same memory location as yPtr. xPtr can legally point to new Memory address but will not affect the yPtr
***

</br>
<a name="const_ptr"/></a>
## Using Const Qualifier with Pointers
</br>

As already seen const inform the compiler that the value of a particular variable should not be modified. This section discusses how to combine const with pointer declarations. Many possibilities exist for using (or not using) const with function parameters or pointer declarations. Each combination provides a different level of access privilege. There are four ways to pass a pointer to a function: 

1. A Nonconstant Pointer to Nonconstant Data, 
2. A Nonconstant Pointer to Constant Data, 
3. A Constant Pointer to Nonconstant Data and 
4. A Constant Pointer to Constant Data. 

#### A Nonconstant Pointer to Nonconstant Data

The highest access is granted by a nonconstant pointer to nonconstant data — the data can be modified through the dereferenced pointer, and the pointer can be modified to point to other data. Such a pointer’s declaration does not include const.

	int *countPtr;

***
**IMPORTANT NOTE:** The declaration `int *countPtr;` is read from right to left as *“countPtr is a pointer to an integer”*.
***

##### SIDE PROGRAM # &nbsp;3

Write a program that demonstrates Nonconstant Pointer to Nonconstant Data

    //
    //  Program Name - S5_SP_NonConstPointers.cpp
    //  Series: GetOnToC++ Step: 5 Side Program
    //
    //  Purpose: This program demonstrates Nonconstant Pointer to Nonconstant Data
    //
    //  Compile: g++ S5_SP_NonConstPointers.cpp -o S5_SP_NonConstPointers
    //  Execute: ./S5_SP_NonConstPointers
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>    using namespace std;
    // Function Prototype

    // This function demonstrates Nonconstant Pointer to Nonconstant Data
    void f1( int * ); 

    int main()
    {
        int x = 25, y = 10, *yPtr = &y;        cout << "The original value of y is: " << y 
             << " And Memory Address is: " << &y
             << "\nThe value of yPtr is: " << *yPtr 
             << " And Memory Address is: " << yPtr << endl;

        // Passing Nonconstant Pointer to a function that takes Nonconstant Data 
        cout << "\nDemonstrating Nonconstant Pointer to Nonconstant Data";
        cout << "\n------------------------------------------------------";

        f1( yPtr );

        cout << "\nThe value of y is " << y << " And Memory Address: " << &y
             << "\nThe value of yPtr is " << *yPtr 
             << " And Memory Address: " << yPtr << endl;

    } // end main


    // This function demonstrates Nonconstant Pointer to Nonconstant Data
    //
    // Notice 1: Since it is pass by reference xPtr can modify the value and the 
    //           same value will be reflected by variable y and the yPtr   
    // Notice 2: xPtr points to the same memory location as yPtr. xPtr can 
    //           legally point to new Memory address but will not affect the yPtr
    // Notice 3: Such Pointer declarion does not include const and the highest 
    //           access is granted 
    //
    void f1( int *xPtr ) 
    {
        cout << "\nIn Function f1(): "
             << "\n-----------------" 
             << "\nThe value of xPtr is " << *xPtr 
             << " And Memory Address is: " << xPtr << endl;

        // The value is modified to 200 hrough the dereferenced pointer
        *xPtr = 50; 
        cout << "The UPDATED value of xPtr is " << *xPtr 
             << " And Memory Address is: " << xPtr << endl;

        // xPtr is modified to point to variable b
        int b = 100;
        xPtr = &b; 
        cout << "The value of xPtr is " << *xPtr 
             << " And UPDATED Memory Address is: " << xPtr << endl;
    } // end function f1

**RESULT:**

    $ ./S5_SP_NonConstPointers
    The original value of y is: 10 And Memory Address is: 0x7fff5f43db00
    The value of yPtr is: 10 And Memory Address is: 0x7fff5f43db00

    Demonstrating Nonconstant Pointer to Nonconstant Data
    ------------------------------------------------------
    In Function f1(): 
    -----------------
    The value of xPtr is 10 And Memory Address is: 0x7fff5f43db00
    The UPDATED value of xPtr is 50 And Memory Address is: 0x7fff5f43db00
    The value of xPtr is 100 And UPDATED Memory Address is: 0x7fff5f43da44

    The value of y is 50 And Memory Address: 0x7fff5f43db00
    The value of yPtr is 50 And Memory Address: 0x7fff5f43db00

***
**NOTE # 1:** In the above side program both the data as well as the pointer pointing to a new data in function f1 is possible. 

**Note # 2:** In pass-by-reference only the data value change can be reflected in the main function and not the pointer reference change. Hence as you will see in the **Result** when xptr changed the data value to 50, y and yptr in main function have the new value. But when xptr points new memory address no change is reflected on either y or yptr.
***


#### A Nonconstant Pointer to Constant Data, 

A nonconstant pointer to constant data is a pointer that can be modified to point to any data item of the appropriate type, but the data to which it points cannot be modified through that pointer. Such a pointer might be used to receive an array argument to a function that will process each array element, but should not be allowed to modify the data. Any attempt to modify the data in the function results in a compilation error. The declaration for such a pointer places const to the left of the pointer’s type, as in

	const int *countPtr;

***
**IMPORTANT NOTE:** The declaration `const int *countPtr;` is read from right to left as *“countPtr is a pointer to an integer constant”*.

**Programming Tip # 1:** If it is not needed to be modified by the called function, pass large objects using pointers to constant data or references to constant data, to obtain the performance benefits of pass-by-reference.

**Programming Tip # 2:** Pass large objects using pointers to constant data, or references to constant data, to obtain the security of pass-by-value.
***

##### SIDE PROGRAM # &nbsp;4

Write a program that demonstrates Nonconstant Pointer to Constant Data

    //
    //  Program Name - S5_SP_NonConstPtrConstData.cpp
    //  Series: GetOnToC++ Step: 5 Side Program
    //
    //  Purpose: This program demonstrates const pointers
    //
    //  Compile: g++ S5_SP_NonConstPtrConstData.cpp -o S5_SP_NonConstPtrConstData
    //  Execute: ./S5_SP_NonConstPtrConstData
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>    using namespace std;
    // Function Prototype

    // This function demonstrates Nonconstant Pointer to Constant Data
    void testNonConstPtrConstData( const int * ); 

    int main()
    {
        int x = 25, y = 10, *yPtr = &y;        cout << "The original value of y is: " << y 
             << " And Memory Address is: " << &y
             << "\nThe value of yPtr is: " << *yPtr 
             << " And Memory Address is: " << yPtr << endl;

        // Passing Nonconstant Pointer to a function that takes Constant Data 
        cout << "\nDemonstrating Nonconstant Pointer to Constant Data";
        cout << "\n------------------------------------------------------";
        testNonConstPtrConstData( yPtr );

        cout << "\nThe value of y is: " << y << " And Memory Address is: " << &y 
             << "\nThe value of yPtr is: " << *yPtr 
             << " And Memory Address is: " << yPtr << endl;

    } // end main

    //
    // This function demonstrates Nonconstant Pointer to Constant Data
    // Notice 1: xPtr cannot modify the value of constant variable to which 
    //           it points
    // Notice 2: xPtr is passed by reference and points to the same memory 
    //           location as yPtr. xPtr can legally point to new Memory address
    //           or any data item of the appropriate type. But this will not 
    //           affect the yPtr. 
    // Notice 3: Pointer reference can be chaged because as per the declaration
    //           const int * the data is Constant but the pointer is Nonconstant 
    //
    void testNonConstPtrConstData( const int *xPtr ) 
    {
        int b = 100;
        cout << "\nIn Function testNonConstPtrConstData():"
             << "\n---------------------------------------" 
             << "\nThe value of xPtr is " << *xPtr 
             << " And Memory Address is: " << xPtr << endl;

        // *xPtr = 100; // error: cannot modify a const object        xPtr = &b; 

        cout << "The value of xPtr is " << *xPtr 
             << " And UPDATED Memory Address is: " << xPtr << endl;
    } // end function testNonConstPtrConstData


**RESULT:**

    $ ./S5_SP_NonConstPtrConstData
    The original value of y is: 10 And Memory Address is: 0x7fff5f43db00
    The value of yPtr is: 10 And Memory Address is: 0x7fff5f43db00

    Demonstrating Nonconstant Pointer to Constant Data
    ------------------------------------------------------
    In Function testNonConstPtrConstData():
    ---------------------------------------
    The value of xPtr is 50 And Memory Address is: 0x7fff5f43db00
    The value of xPtr is 100 And UPDATED Memory Address is: 0x7fff5f43da44

    The value of y is: 50 And Memory Address is: 0x7fff5f43db00
    The value of yPtr is: 50 And Memory Address is: 0x7fff5f43db00

***
**Note:** The declaration of Nonconstant Pointer to Constant Data is `const int *`.  Please notice in the side program the data cannot be modified but the Pointer reference can be chaged.
***

#### A Constant Pointer to Nonconstant Data

A constant pointer to nonconstant data is a pointer that always points to the same memory location; the data at that location can be modified through the pointer. An example of such a pointer is an array name, which is a constant pointer to the beginning of the array. All data in the array can be accessed and changed by using the array name and array subscripting. The declaration for such a pointer places const to the right of the pointer, as in

	int * const countPtr;

***
**IMPORTANT NOTE:** The declaration `int * const countPtr;` is read from right to left as *“countPtr is a constant pointer to a nonconstant integer”*.

**Programming Tip # 1:** Not initializing a pointer that’s declared const is a compilation error.
***

##### SIDE PROGRAM # &nbsp;5

Write a program that demonstrates Constant Pointer to Nonconstant Data

    //
    //  Program Name - S5_SP_ConstPtrNonConstData.cpp
    //  Series: GetOnToC++ Step: 5 Side Program
    //
    //  Purpose: This program demonstrates Constant Pointer to Nonconstant Data
    //
    //  Compile: g++ S5_SP_ConstPtrNonConstData.cpp -o S5_SP_ConstPtrNonConstData
    //  Execute: ./S5_SP_ConstPtrNonConstData
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>    using namespace std;

    int main()
    {
        int x = 25, y = 10;
        
        // ptr is a constant pointer to an integer that can be modified through        // ptr, but ptr always points to the same memory location.        int * const ptr = &y; // const pointer must be initialized
        cout << "\nThe original value of y is: " << y 
        	 << " And Memory Address is: " << &y 
             << "\nThe value of ptr is: " << *ptr 
             << " And Memory Address is: " << ptr << endl;

        // Attempting to modify a constant pointer to nonconstant data.
        cout << "\nDemonstrating Constant Pointer to Nonconstant Data";
        cout << "\n------------------------------------------------------";

        // Attempting to modify a constant pointer to constant data.
        *ptr = 100; // allowed: *ptr is not const and data can be changed
        cout << "\nThe value of y is: " << y << " And Memory Address is: " << &y 
             << "\nThe UPDATED value of ptr is: " << *ptr 
             << " And Memory Address is: " << ptr << endl;
        // ptr = &x; // error: ptr is const; cannot assign to it a new address        
	} // end main

**RESULT:**

    $ ./S5_SP_ConstPtrNonConstData

    The original value of y is: 10 And Memory Address is: 0x7fff5f43db00
    The value of ptr is: 10 And Memory Address is: 0x7fff5f43db00

    Demonstrating Constant Pointer to Nonconstant Data
    ------------------------------------------------------
    The value of y is: 100 And Memory Address is: 0x7fff5f43db00
    The UPDATED value of ptr is: 100 And Memory Address is: 0x7fff5f43db00

***
**Note:** The declaration of Constant Pointer to Nonconstant Data is `int * const`.  Please notice in the side program the data can be modified but the Pointer reference cannot be chaged.
***

#### A Constant Pointer to Constant Data 

The minimum access privilege is granted by a constant pointer to constant data. Such a pointer always points to the same memory location, and the data at that location cannot be modified via the pointer. This is how an array should be passed to a function that only reads the array, using array subscript notation, and does not modify the array. The declaration for such a pointer places const to the right of the pointer as well as a const to the left of the pointer’s type, as in

	const int * const countPtr;

***
**IMPORTANT NOTE:** The declaration `const int * const countPtr;` is read from right to left as *“countPtr is a constant pointer to a integer constant”*.
***

##### SIDE PROGRAM # &nbsp;6

Write a program that demonstrates Constant Pointer to Constant Data

    //
    //  Program Name - S5_SP_ConstPointerAndData.cpp
    //  Series: GetOnToC++ Step: 5 Side Program
    //
    //  Purpose: This program demonstrates Constant Pointer to Constant Data
    //
    //  Compile: g++ S5_SP_ConstPointerAndData.cpp -o S5_SP_ConstPointerAndData
    //  Execute: ./S5_SP_ConstPointerAndData
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>    using namespace std;

    int main()
    {
        // ptr is a constant pointer to a constant integer.        cout << "\nDemonstrating Constant Pointer to Constant Data";
        cout << "\n-------------------------------------------------";
        
        int x = 25;
        // xptr always points to the same location; the integer        // at that location cannot be modified.
        const int *const xptr = &x;
        cout << "\nThe value of x is: " << x << " And Memory Address is: " << &x 
             << "\nThe value of xptr is: " << *xptr 
             << " And Memory Address is: " << xptr << endl;
		cout << "The value of const pointer and const data xptr can only be " 
			 << "printed but no updates are possible"
    	￼￼￼￼// *xptr = 7; // error: *xptr is const; cannot assign new value    	￼￼￼￼// xptr = &y; // error: xptr is const; cannot assign new address
        
	} // end main

**RESULT:**

    $ ./S5_SP_ConstPointerAndData
    
    Demonstrating Constant Pointer to Constant Data
    -------------------------------------------------
    The value of x is: 25 And Memory Address is: 0x7fff5f43db04
    The value of xptr is: 25 And Memory Address is: 0x7fff5f43db04
	The value of const pointer and const data xptr can only be printed but no 	updates are possible

***
**Note:** The declaration of Constant Pointer to Constant Data is `const int * const`.  Please notice in the side program the data can neither be modified nor the Pointer reference can be chaged.
***


</br>
<a name="ptr_and_array"/></a>
## Relationship between Pointer and Array
</br>

This section covers Pointer Expressions and Pointer Arthmatics for Array traversal using Pointer

</br>
<a name="array_ptrs"/></a>
## Arrays of Pointers
</br>


</br>
<a name="func_ptrs"/></a>
## Function Pointers
</br>


