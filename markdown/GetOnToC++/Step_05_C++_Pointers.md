# Step 5: &nbsp;C/C++ Pointers
</br>

This chapter discusses one of the most powerful features of the C/C++ programming language, the **pointer**. Pointers are considered as the most difficult capability to master. In the previous step we saw references to the memory location were passed  as **call-by-reference** function parameters. Call-by-reference parameters share the common memory chuck and nothing is copied. Pointers enable call-by-reference and to create and manipulate dynamic data structures that can grow and shrink, such as linked lists, queues, stacks and trees. 

The Objective of this step is to explain the basic pointer concepts - pointer declaration, initialization, pointer expressions and pointer arthmatics. Further this step explans calling function by reference, function pointers and relationship among Arrays and Pointers. The concepts introduced in this step are:

1. [**Pointer Variable Declaration and Initialization**](#ptr_var)

2. [**Pointer Operators**](#ptr_oper)

3. [**Calling Function by Reference**](#call_by_ref)

4. [**Using Const Qualifier with Pointers**](#const_ptr)

5. [**Relationship between Pointer and Array**](#ptr_and_array)

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
    //  Series: GetOnToC++ Step: 4 Side Program
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

##### SIDE PROGRAM # &nbsp;2

Write a program that demonstrates & (address) and *(dereferencing) pointer operators.

    //
    //  Program Name - S5_SP_PointerOperatorDemo.cpp
    //  Series: GetOnToC++ Step: 4 Side Program
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


</br>
<a name="const_ptr"/></a>
## Using Const Qualifier with Pointers
</br>



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


