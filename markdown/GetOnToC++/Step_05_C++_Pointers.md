# Step 5: &nbsp;C/C++ Pointers
</br>

This chapter discusses one of the most powerful features of the C/C++ programming language, the **pointer**. Pointers are considered as the most difficult capability to master. In the previous step we saw references to the memory location were passed  as **call-by-reference** function parameters. Call-by-reference parameters share the common memory chuck and nothing is copied. Pointers enable call-by-reference and to create and manipulate dynamic data structures that can grow and shrink, such as linked lists, queues, stacks and trees. 

The Objective of this step is to explain the basic pointer concepts - pointer declaration, initialization, pointer expressions and pointer arthmatics. Further this step explans calling function by reference, function pointers and relationship among Arrays and Pointers. The concepts introduced in this step are:

1. [**Pointer Variable Declaration and Initialization**](#ptr_var)

2. [**Pointer Operators**](#ptr_oper)

3. [**Calling Function by Reference**](#call_by_ref)

4. [**Using Const Qualifier with Pointers**](#const_ptr)

5. [**Relationship between Pointers and Arrays**](#ptr_and_array)

6. [**Pointer to a Pointer(Multiple Indirection)**](#ptr_to_ptr)

7. [**Arrays of Pointers**](#array_ptrs)

8. [**Array of Pointers Based Strings**](#array_strings)

9. [**Function Pointers**](#func_ptrs)

10. [**Void Pointers**](#void_ptrs)


Finally the end of the section specifies a [**Programming Problem**](#prog_problem) that will try to use all the concepts covered in this step 


</br>
<a name="ptr_var"/></a>
## Concept 1: Pointer Variable Declaration and Initialization
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
exe/
#### Pointer Initialization

Pointers should be initialized to 0, NULL or an address of the corresponding type either when they’re declared or in an assignment. A pointer with the value 0 or NULL “points to nothing” and is known as a **Null Pointer**. Symbolic constant NULL is defined in several standard library headers to represent the value 0. Initializing a pointer to NULL is equivalent to initializing a pointer to 0, but in C++, 0 is used by convention. When 0 is assigned, it’s converted to a pointer of the appropriate type. The value 0 is the only integer value that can be assigned directly to a pointer variable without first casting the integer to a pointer type. 

##### SIDE PROGRAM # &nbsp;1

Write a program that demonstrates pointer declaration and assignment.

    //
    //  Program Name - S5_SP_PointerDemo.cpp
    //  Series: GetOnToC++ Step: 5 Side Program
    //
    //  Purpose: This program demonstrates pointer declaration and assignment.
    //
    //  Compile: g++ S5_SP_PointerDemo.cpp -o exe/S5_SP_PointerDemo
    //  Execute: exe/S5_SP_PointerDemo
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>    using namespace std;
    int main() 
    {
        // Declare pointer variable yPtr which is a pointer to an integer.
        int y = 5, *yPtr; 

        // Printing yPtr before assignment.
        cout << "\nThe address of yPtr is " << yPtr << endl;

        cout << "\nThe sizeof yPtr: " << sizeof(yPtr)
             << endl;

    } // end main


RESULT:

    $ exe/S5_SP_PointerDemo

	The address of yPtr is 0x7fff5ebbcb20

	The sizeof memory yPtr: 8

***

**Note # 1:** yPtr can be initialized to null using the `int *yPtr = 0;` or `int *yPtr = NULL;`  

**Note # 2:** Initializing the pointer to null will ensure no memory is allocated during declaration. Also if initialized to null then the assignment statement of *yPtr = 5 will lead to segmentation fault as no memory is allocated to the Pointer 

**Note # 3:** To check for a null pointer you can use an if statement as follows:

	// succeeds if yPtr is not null
	if(yPtr || yPtr != NULL) { }   
	
	// succeeds if yPtr is null
	if(!yPtr || yPtr == NULL) {}
	

***

###### [Try Program Modifications Online](http://ideone.com/1EsbCY) 
- **Mod 1:** Modify the program to check if yPtr is null. If yPtr is not null print the value and address of yPtr. If null then print yPtr to check its address. 
- **Mod 2:** Modify the program to initialize the yPtr to null. Check if any memory is allocated to yPtr.
- **Mod 3:** Modify the above program to show the size of Memory yPtr holds is same as the size of memory of variable y which is same as size of int data type. 

###### Programatic Questions

1. Decalre a pointer dblPtr that points to an object of type double. Initialize the dblPtr to point to null 
2. Decalre a pointer dblPtr that points to an object of type double. Initialize a pointer to point to a variable dbl of type double with value 25.0
3. Check if pointer is a null pointer or not
4. What happens if you assign value to a pointer using `*xptr = 5;` if xptr is a null pointer
5. In the following code `int * xptr = 0; double * yptr = 0;` What is the memory of `sizeof(xptr); sizeof(yptr);`. If xptr and yptr are initialized to point to a corresponding int and double data. Then what will be the memory `sizeof(*xptr); sizeof(*yptr);`

</br>
<a name="ptr_oper"/></a>
## Concept 2: Pointer Operators
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

[4]: /Users/narayan/Documents/MakeTechEzResources/images/GetOnToC++/S5_OperatorAssociativity.png "Operator precedence and associativity"

<!--
[4]: https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToC++/S5_OperatorAssociativity.png "Operator precedence and associativity"
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
    //  Compile: g++ S5_SP_PointerOperatorDemo.cpp -o exe/S5_SP_PointerOperatorDemo
    //  Execute: exe/S5_SP_PointerOperatorDemo
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
        int *yPtr; 

        // Printing yPtr before assignment.
        cout << "yPtr is: " << yPtr << endl;

        // yPtr is set the address of y in other words yPtr is pointing to y
        yPtr = &y; 

        cout << "\nThe address of y is " << &y
             << "\nThe value of yPtr is " << yPtr << endl;
        cout << "\nThe value of y is " << y
             << "\nThe value of *yPtr is " << *yPtr << endl;
        
    } // end main

**RESULT:**

    $ exe/S5_SP_PointerOperatorDemo
    yPtr is: 0

    The address of y is 0x7fff5a5efaf4
    The value of yPtr is 0x7fff5a5efaf4

    The value of y is 5
    The value of *yPtr is 5

###### [Try Program Modifications Online](http://ideone.com/KWiJfe) 
- **Mod 1:** Modify the above program to initialize yPtr to point to y. Write code to show the content and address of yPtr and y variable are the same. 
- **Mod 2:** Modify the program to assign new value to y, show that the yPtr also has the same value. 
- **Mod 3:** Modify the program to assign new value to yPtr, show that y also has the same value. 
- **IMP Mod 4:** Modify the above program to show the  &*yPtr is same as *&yptr which is same as yPtr as well as same as &y 

###### Programatic Questions

1. In the following code `int x = 33; int * xptr;`, write code to initialize xptr to point to x;
2. Write code to check variables xptr and x are pointing to the same memory location
3. Write code to check the data value of xptr pointer variable and the value of x variable is the same
4. Write code to modify the value of xptr and show xptr and x have the same value

</br>
<a name="call_by_ref"/></a>
## Concept 3: Calling Function by Reference
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
    //  Compile: g++ S5_SP_PassByRefDemo.cpp -o exe/S5_SP_PassByRefDemo
    //  Execute: exe/S5_SP_PassByRefDemo
    //
    //
    //  Online Execution: http://ideone.com/C3vEU8
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //


    #include <iostream>
    using namespace std;

    // Function  Prototype

    // This function demonstrates passing variable by value
    int cubeByValue( int ); 

    // This function demonstrates passing variable by reference
    int * cubeByReference( int *, int );

    int main()
    {
        int number = 5;
        cout << "The original value of number is " << number 
             << "\nAnd Memory Address: " << &number << endl;

        // Pass number by value to cubeByValue
        int cubeValue = cubeByValue( number ); 
        cout << "\nThe cube value is " << cubeVal << endl;

        // Pass number address to cubeByReference 
        int * cubeRefVal = &cubeValue;
        cubeByReference( cubeRefVal, number ); 
        cout << "\nThe cube value of number is " << *cubeRefVal
             << "\nAnd Memory Address: " << cubeRefVal << endl;

    	int y = 10, *yPtr = &y;
    	cout << "\nThe value of y is: " << y 
          	 << " And Memory Address is: " << &y
         	 << "\nThe value of yPtr is: " << *yPtr 
         	 << " And Memory Address is: " << yPtr << endl;

    	passByReferenceTest(yPtr);

    	cout << "\nThe updated value of y is: " << y 
         	 << " And Memory Address is: " << &y
         	 << "\nThe updated value of yPtr is: " << *yPtr 
         	 << " And Memory Address is: " << yPtr << endl;
        
    } //end main

    // This function demonstrates passing variable by value.
    // This function calculates and return cube of integer argument
    int cubeByValue( int n )
    {
        cout << "\nIn cubeByValue( int n ) function:"
             << "\n----------------------------------" 
             << "\nThe value of n passed by value is " 
             << n << "\nAnd Memory Address: " << &n << endl;
        int * cubeVal = &n;
        *cubeVal = n * n * n;
        return *cubeVal; // cube local variable n and return result
    } // end function cubeByValue

    // This function demonstrates passing variable by reference
    // to calculate cube; 
    int * cubeByReference( int *cubeVal, int val )
    {
        cout << "\nIn cubeByReference( int *cubeVal, int val ) function: "
             << "\n-------------------------------------------" 
             << "\nThe value is " << val 
             << "\nAnd Memory Address: " << cubeVal << endl;
        *cubeVal = val * val * val; // cube val
        return cubeVal;
    } // end function cubeByReference

	// This function demonstrates important rule of passing variable by reference
	//
	// Notice 1: Since it is pass by reference xPtr can modify the value and the 
	//           same value will be reflected by variable y and the yPtr   
	//
	// Notice 2: xPtr points to the same memory location as yPtr. xPtr can 
	//           legally point to new Memory address but will not affect the yPtr
	//
	int * passByReferenceTest( int *xPtr ) 
	{
	    cout << "\nIn Function passByReferenceTest(): "
	         << "\n----------------------------------" 
	         << "\nThe value of xPtr is " << *xPtr 
	         << " And Memory Address is: " << xPtr << endl;
	
		return xPtr;
	} // end function passByReferenceTest


    RESULT:

    exe/S5_SP_PassByRefDemo
    The original value of number is 5
    And Memory Address: 0x7fff50ff8af4

    In cubeByValue( int n ) function:
    ----------------------------------
    The value of n passed by value is 5
    And Memory Address: 0x7fff50ff8a6c

    The cube value is 125

    In cubeByReference( int *cubeVal, int val ) function: 
    -------------------------------------------
    The value is 5
    And Memory Address: 0x7fff50ff8af0

    The cube value of number is 125
    And Memory Address: 0x7fff50ff8af0

	The value of y is: 10 And Memory Address is: 0xbf9c189c
	The value of yPtr is: 10 And Memory Address is: 0xbf9c189c

	In Function passByReferenceTest(): 
	----------------------------------
	The value of xPtr is 10 And Memory Address is: 0xbf9c189c

	The updated value of y is: 10 And Memory Address is: 0xbf9c189c
	The updated value of yPtr is: 10 And Memory Address is: 0xbf9c189c

***
**Note:** We can see the following in the Side Program above

1. **Notice # 1:** The memory address of variable n in cubeByValue is different from the memory address of variable number defined in main. This means a new memory is created for variable n and the value is copied. This is pass-by-value 
2. **Notice # 2:** The memory address of variable cubeVal in cubeByReference is same as the memory address of variable cubeRefVal defined in main. This means the memory is shared or the same for variable cubeVal and cubeRefVal. This is pass-by-reference
3. Notice # 3: Since it is pass by reference xPtr can modify the value and the same value will be reflected by variable y and the yPtr   
4. Notice # 4: xPtr points to the same memory location as yPtr. xPtr can legally point to new Memory address but will not affect the yPtr
***

###### [Try Program Modifications Online](http://ideone.com/C3vEU8) 
- **IMP Mod 1:** Modify the program to show the memory address of variable n in cubeByValue function is different from the variable number defined in main. 
- **IMP Mod 2:** Modify the program to show the memory address of variable cubeVal in cubeByReference is same as the memory address of variable cubeRefVal defined in main. 
- **IMP Mod 3:** Modify the Program to pass cubeValue as a parameter in cubeByReference function instead of cubeRefVal
- **IMP Mod 4:** Modify the function passByReferenceTest to show in pass-by-reference the value if modified for xPtr, the same value is reflected for yPtr and y datatype
- **IMP Mod 5:** Modify the function passByReferenceTest to show  xPtr can legally point to new Memory address but will not affect the yPtr


###### Programatic Questions

1. If `int x = 5;` write function f1 to take parameter x by value and by reference
2. If `int x = 5; int * xPtr = &x;` write function f1 to take parameter xPtr by value and by reference

</br>
<a name="const_ptr"/></a>
## Concept 4: Using Const Qualifier with Pointers
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
    //  Compile: g++ S5_SP_NonConstPointers.cpp -o exe/S5_SP_NonConstPointers
    //  Execute: exe/S5_SP_NonConstPointers
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>    using namespace std;

    int main()
    {
        int x = 25, y = 10, *yPtr = &y;        cout << "The original value of y is: " << y 
             << " And Memory Address is: " << &y
             << "\nThe value of x is: " << x 
             << " And Memory Address is: " << &x 
             << "\nThe value of yPtr is: " << *yPtr 
             << " And Memory Address is: " << yPtr << endl;

        // Passing Nonconstant Pointer to a function that takes Nonconstant Data 
        cout << "\nDemonstrating Nonconstant Pointer to Nonconstant Data";
        cout << "\n------------------------------------------------------";

		// Modify the data of yPtr using de-referenced pointer

        cout << "\nThe value of y is " << y << " And Memory Address: " << &y
             << "\nThe value of yPtr is " << *yPtr 
             << " And Memory Address: " << yPtr << endl;
        
        // Modify the yPtr to point to x 

        cout << "\nThe value of y is " << y << " And Memory Address: " << &y
             << "\nThe value of yPtr is " << *yPtr 
             << " And Memory Address: " << yPtr << endl;

    } // end main


**RESULT:**

    $ exe/S5_SP_NonConstPointers
    The original value of y is: 10 And Memory Address is: 0x7fff54e46af0
    The value of x is: 25 And Memory Address is: 0x7fff54e46af4
    The value of yPtr is: 10 And Memory Address is: 0x7fff54e46af0

    Demonstrating Nonconstant Pointer to Nonconstant Data
    ------------------------------------------------------
    The value of y is 10 And Memory Address: 0x7fff54e46af0
    The value of yPtr is 10 And Memory Address: 0x7fff54e46af0

    The value of y is 10 And Memory Address: 0x7fff54e46af0
    The value of yPtr is 10 And Memory Address: 0x7fff54e46af0

***
**NOTE # 1:** In the above side program both the data as well as the pointer pointing to a new data in function f1 is possible. 

**Note # 2:** In pass-by-reference only the data value change can be reflected in the main function and not the pointer reference change. Hence as you will see in the **Result** when xptr changed the data value to 50, y and yptr in main function have the new value. But when xptr points new memory address no change is reflected on either y or yptr.
***

###### [Try Program Modifications Online](http://ideone.com/qYMEE3) 
- **IMP Mod 1:** Modify the program by updating the data of yPtr using de-referenced pointer and show programatically the same value is reflected for y 
- **IMP Mod 2:** Modify the program by updating the yPtr to point to x and show yPtr can legally point to new Memory address but will not affect y

###### Programatic Questions

1. Declare a non-constant pointer dblPtr to a non-constant data of datatype double. How would you read such a declaration.
2. If `double dbl1 = 100.00, dbl2 = 50.0;`, write code to show dblPtr pointing to dbl1.
3. Assign dblPtr to have the value of dbl2. Is the address and the value of dbl1 same as the  dblPtr.
4. Assign dblPtr to have the address of dbl2. Is the address and the value of dbl1 same as the  dblPtr

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
    //  Program Name - S5_SP_PtrToConstData.cpp
    //  Series: GetOnToC++ Step: 5 Side Program
    //
    //  Purpose: This program demonstrates const pointers
    //
    //  Compile: g++ S5_SP_PtrToConstData.cpp -o exe/S5_SP_PtrToConstData
    //  Execute: exe/S5_SP_PtrToConstData
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>    using namespace std;
    
    // Function Prototype

    int main()
    {
        int x = 25, y = 10, *yPtr = &y;        cout << "The original value of y is: " << y 
             << " And Memory Address is: " << &y
             << "\nThe value of yPtr is: " << *yPtr 
             << " And Memory Address is: " << yPtr << endl;

        // Passing Nonconstant Pointer to a function that takes Constant Data 
        cout << "\nDemonstrating Nonconstant Pointer to Constant Data";
        cout << "\n------------------------------------------------------";

    	// Notice 1: xPtr cannot modify the value of constant variable to which 
    	//           it points
    	// Notice 2: xPtr is passed by reference and points to the same memory 
    	//           location as yPtr. xPtr can legally point to new Memory address
    	//           or any data item of the appropriate type. But this will not 
    	//           affect the yPtr. 
    
        // Define xPtr variable which is Pointer to constant Data
        // Modification Code # 1
        
        // Assign xPtr to point to yPtr
        // Modification Code # 2

        cout << " \nAfter assignment of xPtr to point to yPtr ---------------" 
             << "\nThe value of y is: " << y << " And Memory Address is: " << &y 
             << "\nThe value of yPtr is: " << *yPtr 
             << " And Memory Address is: " << yPtr; 
             
        // cout << "\nThe value of xPtr is: " << *xPtr 
        //      << " And Memory Address is: " << xPtr << endl;
             
        // Assign xPtr to point to x
        // Modification Code # 3

        cout << " \nAfter assignment of xPtr to point to y ------------------" 
             << "\nThe value of y is: " << y 
             << " And Memory Address is: " << &y 
             << "\nThe value of yPtr is: " << *yPtr 
             << " And Memory Address is: " << yPtr; 
             
        // cout << "\nThe value of xPtr is: " << *xPtr 
        //      << " And Memory Address is: " << xPtr << endl;

		// Try Modifying the value of xPtr. You will get an error cannot modify
        // Modification Code # 4

    } // end main

**RESULT:**

    $ exe/S5_SP_PtrToConstData
    The original value of y is: 10 And Memory Address is: 0xbfebbb4c
    The value of yPtr is: 10 And Memory Address is: 0xbfebbb4c

    Demonstrating Nonconstant Pointer to Constant Data
    ------------------------------------------------------ 
    After assignment of xPtr to point to yPtr ---------------
    The value of y is: 10 And Memory Address is: 0xbfebbb4c
    The value of yPtr is: 10 And Memory Address is: 0xbfebbb4c 
    After assignment of xPtr to point to y ------------------
    The value of y is: 10 And Memory Address is: 0xbfebbb4c
    The value of yPtr is: 10 And Memory Address is: 0xbfebbb4c
    
***
**Note Num 1:** The declaration of Nonconstant Pointer to Constant Data is `const int *`.  Please notice in the side program the data cannot be modified but the Pointer reference can be chaged.
**Note Num 1:** The benifit of using a pointer to a constant data is performance benefits of pass-by-reference as same memory is used and security benifits of pass-by-value as the values cannot be modified.
***

###### [Try Program Modifications Online](http://ideone.com/fPVJkI) 
- **Mod 1:** Modify the program to define xPtr variable which is Pointer to constant Data of int data type
- **Mod 2:** Modify the program to assign xPtr to point to yPtr. Show programatically xPtr, yPtr and y point to the same locaton
- **Mod 3:** Modify the program to assign xPtr to point to x. Show programatically xPtr and yPtr are pointing to different locaton
- **Mod 4:** Modify the program to assign new value to xPtr. Is it possible what is the error you get. What is the benifit of using a pointer to a constant data???

###### Programatic Questions

1. Declare a  pointer dblPtr to a constant data of datatype double. How would you read such a declaration.
2. Define function prototype modifyPtr2ConstData which takes pointer to a constant data as a argument
3. Define function header for the function prototype modifyPtr2ConstData. Name the variable as xPtr
4. In the function body modify xPtr to point to new memory address 
5. Can you change the value of the xPtr. If not why?


#### A Constant Pointer to Nonconstant Data

A constant pointer to nonconstant data is a pointer that always points to the same memory location; the data at that location can be modified through the pointer. An example of such a pointer is an array name, which is a constant pointer to the beginning of the array. All data in the array can be accessed and changed by using the array name and array subscripting. The declaration for such a pointer places const to the right of the pointer, as in

	int * const countPtr;

***
**IMPORTANT NOTE:** The declaration `int * const countPtr;` is read from right to left as *“countPtr is a constant pointer to an integer”*.

**Programming Tip # 1:** Not initializing a pointer that’s declared const is a compilation error.
***

##### SIDE PROGRAM # &nbsp;5

Write a program that demonstrates Constant Pointer to Nonconstant Data

    //
    //  Program Name - S5_SP_ConstPtrVarData.cpp
    //  Series: GetOnToC++ Step: 5 Side Program
    //
    //  Purpose: This program demonstrates Constant Pointer to Nonconstant Data
    //
    //  Compile: g++ S5_SP_ConstPtrVarData.cpp -o exe/S5_SP_ConstPtrVarData
    //  Execute: exe/S5_SP_ConstPtrVarData
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>    using namespace std;

    int main()
    {
        int x = 25, y = 10, *yPtr = &y;
        
        cout << "\nDemonstrating Constant Pointer to Nonconstant Data";
        cout << "\n------------------------------------------------------";

        // Note in case of Constant Pointer to an integer, the integer value can 
        // be modified bur the Pointer's memory location cannot be changed

        // Specify a constPtr variable which is a Constant Pointer to an Integer
        // Initialize to point to yPtr. Note constPtr must be initialized
        // Modification Code # 1
        
        cout << " \nAfter Initialization of constPtr ---------------" 
             << "\nThe value of yPtr is: " << *yPtr 
             << " And Memory Address is: " << yPtr; 
             
        // cout << "\nThe value of constPtr is: " << *constPtr 
        //      << " And Memory Address is: " << constPtr << endl;

        // Assign value of x to constPtr. This is possible as data can be changed 
        // Modification Code # 2

        cout << " \nAfter assignment of x to constPtr ---------------" 
             << "\nThe value of yPtr is: " << *yPtr 
             << " And Memory Address is: " << yPtr; 
             
        // cout << "\nThe value of constPtr is: " << *constPtr 
        //      << " And Memory Address is: " << constPtr << endl;

		// Modify constPtr to point to variable x. This will cause error as cannot 
		// be assigned to new address
        // Modification Code # 3
        
	} // end main

**RESULT:**

    $ exe/S5_SP_ConstPtrVarData

    Demonstrating Constant Pointer to Nonconstant Data
    ------------------------------------------------------ 
    After Initialization of constPtr ---------------
    The value of yPtr is: 10 And Memory Address is: 0xbfb122ec 
    After assignment of x to constPtr ---------------
    The value of yPtr is: 10 And Memory Address is: 0xbfb122ec
    
***
**Note:** The declaration of Constant Pointer to Nonconstant Data is `int * const`.  Please notice in the side program the data can be modified but the Pointer reference cannot be chaged.
***

###### [Try Program Modifications Online](http://ideone.com/IXP382) 

- **Mod 1:** Modify Program to specify a constPtr variable which is a Constant Pointer to an Integer.
- **Mod 2:** Modify Program to assign value of x to constPtr. This is possible as data can be changed. If constPtr was initialized to point to yPtr, show programatically if the value of constPtr and yPtr are the same.
- **Mod 3:** Modify Program to update constPtr to point to variable x. Is this possible... If not what is the error...

###### Programatic Questions

1. Declare a constant pointer dblPtr to a data of datatype double. How would you read such a declaration.
2. Initialize the dblPtr. Is it compulsary to initialize the dblPtr? If so why??
3. Can you change the value of the dblPtr. If so why?
4. Can you assign dblPtr to point to a new memory. If not why?

#### A Constant Pointer to Constant Data 

The minimum access privilege is granted by a constant pointer to constant data. Such a pointer always points to the same memory location, and the data at that location cannot be modified via the pointer. This is how an array should be passed to a function that only reads the array, using array subscript notation, and does not modify the array. The declaration for such a pointer places const to the right of the pointer as well as a const to the left of the pointer’s type, as in

	const int * const countPtr;

***
**IMPORTANT NOTE:** The declaration `const int * const countPtr;` is read from right to left as *“countPtr is a constant pointer to a integer constant”*.

**Programming Tip:** Not initializing a pointer that’s declared const is a compilation error.
***

##### SIDE PROGRAM # &nbsp;6

Write a program that demonstrates Constant Pointer to Constant Data

    //
    //  Program Name - S5_SP_ConstPointerAndData.cpp
    //  Series: GetOnToC++ Step: 5 Side Program
    //
    //  Purpose: This program demonstrates Constant Pointer to Constant Data
    //
    //  Compile: g++ S5_SP_ConstPointerAndData.cpp -o exe/S5_SP_ConstPointerAndData
    //  Execute: exe/S5_SP_ConstPointerAndData
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>    using namespace std;

    int main()
    {
        // ptr is a constant pointer to a constant integer.        cout << "\nDemonstrating Constant Pointer to Constant Data";
        cout << "\n-------------------------------------------------";
        
        int x = 25, y = 15;
        
        // Constant pointer to a constant integer always points to the same 
        // location; the integer at that location cannot be modified.
        
        // Specify variable xPtr which is a Constant Pointer to an Integer 
        // Constant. Initialize the pointer to point to memory location of x 
        // Modification Code # 1
        const int *const xptr = &x;
        
        cout << "\nThe value of x is: " << x << " And Memory Address is: " << &x;
        
        // cout << "\nThe value of xptr is: " << *xptr 
        //   << " And Memory Address is: " << xptr << endl;

		// Modify xPtr to point to variable y. This will cause error as cannot 
		// be assigned to new address
        // Modification Code # 2
    			// Modify xPtr to have value of y. This will also cause an error as xPtr 		// cannot be assigned to a new value
        // Modification Code # 3
        
	} // end main

**RESULT:**

    $ exe/S5_SP_ConstPointerAndData
    
	Demonstrating Constant Pointer to Constant Data
    -------------------------------------------------
    The value of x is: 25 And Memory Address is: 0xbfa1322c
    
***
**Note:** The declaration of Constant Pointer to Constant Data is `const int * const`.  Please notice in the side program the data can neither be modified nor the Pointer reference can be chaged.
***

###### [Try Program Modifications Online](http://ideone.com/iKRfPp) 

- **Mod 1:** Modify Program to specify a variable xPtr which is a Constant Pointer to an Integer Constant.
- **Mod 2:** Modify Program to assign xPtr to point to variable y. Is this possible... If not what is the error...
- **Mod 3:** Modify Program to update xPtr to have value of y. Is this possible... If not what is the error...

###### Programatic Questions

1. Declare a constant pointer flPtr to a float constant. How would you read such a declaration.
2. Initialize the flPtr. Is it compulsary to initialize the flPtr? If so why??
3. Can you change the value of the flPtr. If not why?
4. Can you assign flPtr to point to a new memory. If not why?


</br>
<a name="ptr_and_array"/></a>
## Concept 5: Relationship between Pointer and Array
</br>

Arrays and pointers are intimately related in C++ and may be used almost interchangeably. An array name can be thought of as a constant pointer pointing to first element of the array. Pointers can be used to do any operation involving array subscripting including array traversals on single or multi-dimensional array. Assume the following declarations:

	int v[ 5 ]; // create 5-element int array v
	int *vPtr;  // create a vPtr pointer pointing to an integer 

Because the array name (without a subscript) is a (constant) pointer to the first element of the array, we can set vPtr to the address of the first element in array v with the statement

	vPtr = v; // assign address of array v to vPtr

This is equivalent to assigning the address of the first element of the array as follows:

	vPtr = &v[ 0 ]; // also assigns address of array v to vPtr

Assuming the first element is at memory location 3000. Since pointer vPtr is pointing to v[0], hence the value of vPtr is 3000. The following figure shows the memory location of array v and pointer vPtr for a machine with four-byte integers.

</br>
![Pointer Referencing a Array][5]

[5]: /Users/narayan/Documents/MakeTechEzResources/images/GetOnToC++/S5_ArrayPointerMemory.png "Pointer Referencing a Array"

<!--
[5]: https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToC++/S5_ArrayPointerMemory.png "Pointer Referencing a Array"
-->
<p></p>
***
**Note:** Many computers have two-byte or four-byte integers. Some of them use eight-byte integers. Because the results of pointer arithmetic depend on the size of the objects a pointer points to, pointer arithmetic is machine dependent. You can find the size the int datatype occupies using sizeOf operator
***

Array element v\[3] can be alternatively be referenced with the pointer expression

	*( vPtr + 3 ); // This is equivalent to *( v + 3 ) which is same as v[3]

The 3 in the preceding expression is the offset to the pointer. When the pointer points to the beginning of an array, the offset indicates which array element should be referenced, and the offset value is identical to the subscript. This notation is referred to as **pointer/offset notation**. 

***
**NOTE:** The parentheses for the code `*( bPtr + 3 );` is necessary, because the precedence of * is higher than that of +. Without the parentheses, the preceding expression would add 3 to a copy *bPtr’s value (i.e., 3 would be added to b[0], assuming that bPtr points to the beginning of the array). 
***

Just as the array element can be referenced with a pointer expression, the address`&b[ 3 ]` can be written with the pointer expression `bPtr + 3`

***
**Note No 1:** In general, all subscripted array expressions can be written with a pointer and an offset. Either using the name of the array as a pointer (i.e. v) or by using the pointer pointing to the array element (i.e. vPtr)

**Note No 2:** In the expression `v + 3`, there is no modification to array v, it still points to the first element of the array. 
***

**Important Note**

Remember that an array name is a constant pointer; it always points to the beginning of the array. Thus, the expression `v += 3` will cause a compilation error, because it attempts to modify the value of the array name (a constant) with pointer arithmetic.

**Pointer Comparisons**

Pointers may be compared by using relational operators, such as ==, <, and >. If p1 and p2 point to variables that are related to each other, such as elements of the same array, then p1 and p2 can be meaningfully compared as seen in the following code snippet. 

	int  p[3] = {5, 15, 10};
    int  *p1 = NULL, *p2 = 0; // assigning ptr to null
    p1 = p; // p1 points to the first element of array p
    p2 = p + 2; // p2 points to the second element of array p
    
In such a case pointer comparisons of p1 and p2 can be done. 

1. `if (p1 == p2)` => This checks both pointers p1 and p2 are pointing to same element of the array
2. `if (p2 > p1)` => This checks the pointer p1 is closer to the first element of array compared to pointer p2
3. `if (p2 <= p+2)` => This checks the pointer p2 is always equal to or less then max length of the array p
    
The following side program uses pointer comparisons for navigating through while loop...

##### SIDE PROGRAM # &nbsp;7

Write a program that demonstrates pointer and array relationship. Use pointer expression and pointer comparisons to traverse through the array

    //
    //  Program Name - S5_SP_PointerArrayDemo.cpp
    //  Series: GetOnToC++ Step: 5 Side Program
    //
    //  Purpose: This program demonstrates pointer and array relationship using
    //           pointer expression and pointer comparisons.
    //
    //  Compile: g++ S5_SP_PointerArrayDemo.cpp -o exe/S5_SP_PointerArrayDemo
    //  Execute: exe/S5_SP_PointerArrayDemo
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    using namespace std;

    const int MAX = 3;

    int main ()
    {
       int  v[MAX] = {10, 100, 200};
       
       // Declare vPtr1 and vPtr2 as a Pointer to an Integer and 
       // Initialize it to null
       int  *vPtr1 = NULL; // assigning ptr to null
       // Modification Code # 1

       // Assign vPtr1 to point to the first element of the array v and 
       // vPtr2 to last elment of array v
       // Modification Code # 2
       
       // Perform Pointer comparisons to show vPtr1 and vPtr2 are pointing to the 
       // same element
       // Modification Code # 3

       // Perform Pointer comparisons to show vPtr1 or vPtr2 is closer to the 
       // first element
       // Modification Code # 4
       
       // Perform Pointer comparisons to show vPtr1 or vPtr2 is closer to the last 
       // element
       // Modification Code # 5
              
       // Perform Pointer comparisons to show vPtr1 is pointing to the first 
       // element of the array
       // Modification Code # 6
       
       // Perform Pointer comparisons to show vPtr2 is pointing to the last
       // element of the array
       // Modification Code # 7
       
       int i = 0;
       cout << "Address of vPtr1 is: " << vPtr1 << endl;
       
       // Traversing the array v
       while ( vPtr1 && vPtr1 <= &v[MAX - 1] ) 
       {
          cout << "Address of v[" << i << "] = ";
          cout << vPtr1 << endl;

          cout << "Value of v[" << i << "] = ";
          cout << *vPtr1 << endl;

          // Using Pointer expression to re-reference vPtr1
          i++;
          vPtr1 = v + i;
       }
       return 0;
    }

###### [Try Program Modifications Online](http://ideone.com/9GTUjF) 

- **Mod 1:** Modify the program to declare vPtr2 as a Pointer to an Integer and Initialize it to null
- **Mod 2:** Modify the program to Assign vPtr1 to point to the first element of the array v and vPtr2 to the last element of array v
- **Mod 3:** Modify the program to Perform Pointer comparisons to show if vPtr1 and vPtr2 are pointing to the same element
- **Mod 4:** Modify the program to Perform Pointer comparisons to show if vPtr1 or vPtr2 is closer to the first element
- **Mod 5:** Modify the program to Perform Pointer comparisons to show if vPtr1 or vPtr2 is closer to the last element
- **Mod 6:** Modify the program to Perform Pointer comparisons to show if vPtr1 is pointing to the first element of the array
- **Mod 7:** Modify the program to Perform Pointer comparisons to show vPtr2 is pointing to the last element of the array
- **Mod 8:** Modify the above program to show the vPtr points to some memory and junk value if the value of int i is >= MAX. In such a case make vPtr point to null

###### Programatic Questions

1. In the code `int v[ 5 ];`. What is the array name and how will you describe the array name. Is it a pointer to a integer or constant pointer to an integer or pointer to a constant integer or constant pointer to a constant integer.
2. Prove why the array name is not a pointer to a constant data.
3. Which element of the array the array name point to.
4. Considering `int v[ 5 ];`, is `v += 3` a correct statment. If not why???
5. Considering `int v[ 5 ]; int * vPtr = 0;`, write 2 alternate ways to assign vPtr to point to first element of the array.
6. Considering vPtr (which is pointer to an integer) point to first element of the array v, write code to show 3 alternate ways to retrieve the 3rd element of the array

Lets look into Pointer Expressions and Pointer Arthmatics for Array traversal using Pointer in more detail.

#### Pointer Expressions and Pointer Arithmetic

This section describes the operators that can have pointers as operands and how these operators are used with pointers. C++ enables pointer arithmetic that can be performed on the pointers. A pointer may be incremented (++) or decremented (--), an integer may be added to a pointer (+ or +=), an integer may be subtracted from a pointer (- or -=), or one pointer may be subtracted from another of the same type.

In conventional arithmetic, the addition 3000 + 2 yields the value 3002. This is normally not the case with pointer arithmetic. When an integer is added to, or subtracted from, a pointer, the pointer is not simply incremented or decremented by that integer, but by that integer times the size of the object to which the pointer refers. The number of bytes depends on the object’s data type. For example, the statement

	vPtr += 2;

would produce 3008 (from the calculation 3000 + 2 * 4), assuming that an int is stored in four bytes of memory. In the array v, vPtr would now point to v\[2] as shown in the figure below. 

<br>
![Pointer Arithmetic][6]

[6]: /Users/narayan/Documents/MakeTechEzResources/images/GetOnToC++/S5_PointerArthmatic.png "Pointer Arithmetic on Array"
<!--
[6]: https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToC++/S5_PointerArthmatic.png "Pointer Arithmetic on Array"
-->
<p></p>

***
**Note:** If an integer is stored in two bytes of memory, then the preceding calculation would result in memory location 3004 (3000 + 2 * 2). If the array elements were of a different data type, the preceding statement would increment the pointer by twice the number of bytes it takes to store an object of that data type.
***

If a pointer is being incremented or decremented by one, the increment (++) and decrement (--) operators can be used. Each of the statements increments the pointer to point to the next element of the array. 

	++vPtr;	vPtr++;

Each of the statements decrements the pointer to point to the previous element of the array.

	--vPtr;	vPtr--;

Pointer variables pointing to the same array may be subtracted from one another. For example, if vPtr contains the address 3000 and v2Ptr contains the address 3008, the statement	

	x = v2Ptr - vPtr;
	
would assign to x the number of array elements from vPtr to v2Ptr—in this case, 2. 

**Important Note**

Pointer arithmetic is meaningless unless performed on a pointer that points to an array. We cannot assume that two variables of the same type are stored continiously in memory unless they’re adjacent elements of an array. Infact Subtracting or comparing two pointers that do not refer to elements of the same array is a logic error.

**Program Modification:** Modifying the Program # 7 to use pointer arithmatic instead of vPtr1 = v + i;

##### SIDE PROGRAM # &nbsp;8

Write a program that demonstrates pointer and array relationship. Use pointer arithmatic to traverse through the array. This is similar to last program except pointer arithmatic is used for navigation through the array

    //
    //  Program Name - S5_SP_PointerArithmetic.cpp
    //  Series: GetOnToC++ Step: 5 Side Program
    //
    //  Purpose: This program demonstrates pointer and array relationship using
    //           pointer arithmetic.
    //
    //  Compile: g++ S5_SP_PointerArithmetic.cpp -o exe/S5_SP_PointerArithmetic
    //  Execute: exe/S5_SP_PointerArithmetic
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    using namespace std;

    // Function Prototype
    void incrementArrayElements (int *, int *);
    void printArray (const int* , const int* );

    int main ()
    {
        int numbers [] = {10, 20, 30};
    
        // Increment the value Array Elements by 1
        cout << "Incrementing Array Elements" << endl;
        
        // Print the Initial Array Elements
        cout << "Printing Initial Array Elements: ";
        printArray(numbers,numbers+3);
        
        cout << "Incrementing Array Elements" << endl;
        
        // Invoke incrementArrayElements function and pass the first and last 
        // element of number array as parameter
        // Modification Code # 1

        cout << "Printing Incremented Array Elements: ";
        // Invoke printArray function and pass the first and last element of number
        // array as parameter
        // Modification Code # 2
        
        return 0;
    }

	/**
	 * Increment the value of all the array elements by 1. 
	 * Param 1: start :- first element of the array
	 * Param 2: stop :- last element of the array
	 */
    void incrementArrayElements(int* start, int* stop)
    {
    	// Declare current pointer pointing to start of the element
        // Modification Code # 3
        
        // Loop the current pointer from start to stop
        // Inside the loop
        // 1: Increment the value
        // 2: Increment the pointer
        
        // Modification Code # 4
    }

	/**
	 * Print all the array elements. 
	 * Param 1: start :- first element of the array
	 * Param 2: stop :- last element of the array
	 */
    void printArray(const int* start, const int* stop)
    {
    	// Declare current pointer to a constant Interger. 
    	// Initialize current pointer to point to start of the element
        const int * current = start;
        
        // Loop the current pointer from start to stop
        // Inside the loop
        // 1: Print the value
        // 2: Increment the pointer
        while (current != stop) {
            // Print the value
            cout << *current << ' ';
            // Increment the pointer
            ++current;   
        }
        cout << endl;
    }

###### [Try Program Modifications Online](http://ideone.com/f3fIoZ) 

- **Mod 1:** Modify the program to Invoke incrementArrayElements function and pass the first and last element of number array as parameter
- **Mod 2:** Modify the program to Invoke printArray function and pass the first and last element of number array as parameter
- **Mod 3:** Modify the program to Declare current pointer pointing to start of the element
- **Mod 4:** Modify the program to Loop the current pointer from first element to last element of the array. Inside the loop - Increment the value and Increment the pointer
- **IMP Mod 5:** Modify the function incrementArrayElements to take function parameters as constant pointer to an Integer for start and stop instead of pointer to an integer.
- **IMP Mod 6:** Modify the function printArray to take function parameters as constant pointer to a constant Integer for start and stop instead of pointer to a constant integer.
- **IMP Mod 7:** Modify the program to create a new function incrementArrayElements which takes an additional parameter value. This function would increment array element by this constant value

###### Programatic Questions

1. Is it possible to re-define function incrementArrayElements as follows. If not explain why????

	`void incrementArrayElements(const int* const start, const int * stop)`
	
2. 	In the code snippet 

		int v[] = {10, 20, 30}; 
		int * const vPtr1 = v; 
		const int * vPtr2 = v + 1;

	a. Is it possible to increment vPtr1 pointer `vPtr1++;` . If not why?
	b. Is it possible to increment vPtr2 pointer `vPtr2++;` . If yes why?
	c. Is it possible to increment the integer content of vPtr2 pointer as `(*vPtr2)++`. If not why?
	d. Is following code valid `vPtr1 = vPtr2;`. If not why??? 

</br>
<a name="ptr_to_ptr"/></a>
## Concept 6: Pointer to a Pointer
</br>

A pointer to a pointer is a form of multiple indirection or a chain of pointers. Normally, a pointer contains the address of a variable. When we define a pointer to a pointer, the first pointer contains the address of the second pointer, which points to the location that contains the actual value as shown in figure below.

<br>
![Pointer to a Pointer][7]

[7]: /Users/narayan/Documents/MakeTechEzResources/images/GetOnToC++/S5_pointer_to_pointer.jpg "Pointer to a Pointer"
<!--
[7]: https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToC++/S5_pointer_to_pointer.jpg "Pointer to a Pointer"
-->
<p></p>

A variable that is a pointer to a pointer must be declared as

	int **dblPtr;
	
***
**IMPORTANT NOTE 1:** The declaration `int **dblPtr;` is read from right to left as *“dblPtr is a pointer to a pointer to an Integer”*.

***

##### SIDE PROGRAM # &nbsp;9

Write a program that demonstrates pointer to a pointer. 

    //
    //  Program Name - S5_SP_Pointer2Pointer.cpp
    //  Series: GetOnToC++ Step: 5 Side Program
    //
    //  Purpose: This program demonstrates pointer to a pointer 
    //
    //  Compile: g++ S5_SP_Pointer2Pointer.cpp -o exe/S5_SP_Pointer2Pointer
    //  Execute: exe/S5_SP_Pointer2Pointer
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    using namespace std;

    int main() 
    {
        // Declaring Integer Variable and a Pointer to an Integer
        int var = 3000, *ptr = 0;
        
        // Declare a Pointer to a Pointer to an Integer
        // Modification Code # 1

        // Assign the address of the var Variable to the Pointer ptr
        // Modification Code # 2

        // Assign the address of the Pointer ptr to the Pointer to a Pointer pptr
        // Modification Code # 3

        // Outputing the variables
        cout << "Value of var :" << var << endl;
        
        if (ptr)
        	cout << "Address of ptr is: " << ptr << " And Value is:" << *ptr 
        		 << endl;
       	if (pptr) {
        	cout << "Address of pptr is: " << pptr << " Value of *pptr:" << *pptr 
        	 	 << endl;
        	cout << "Value available at **pptr :" << **pptr << endl;
        }

		// Prove that variables var, ptr, and pptr have the same integer value
        // Modification Code # 4
		
		
		// Prove that variables var, ptr and pptr are pointing to the same Integer 
		// Memory
        // Modification Code # 5
		
        return 0;
    }

###### [Try Program Modifications Online](http://ideone.com/eRNPTP) 

- **Mod 1:** Modify the program to Declare a Pointer to a Pointer to an Integer
- **Mod 2:** Modify the program to Assign the address of the var Variable to the Pointer ptr
- **Mod 3:** Modify the program to Assign the address of the Pointer ptr to the Pointer to a Pointer pptr
- **Mod 4:** Modify the program to Prove that variables var, ptr, and pptr have the same integer value
- **Mod 5:** Modify the program to Prove that variables var, ptr and pptr are pointing to the same Integer Memory

###### Programatic Questions

1. Declare a Pointer to a Pointer to a Double
2. Declare a Pointer to a Pointer to a Double Constant 
3. Declare a Pointer to a Constant Pointer to a Double Constant 
4. Declare a Constant Pointer to a Constant Pointer to a Double Constant 
5. Declare a Constant Pointer to a Pointer to a Double Constant 

</br>
<a name="array_ptrs"/></a>
## Concept 7: Arrays of Pointers
</br>

Arrays contain pointers. The double pointer which is a pointer to a pointer are predominantly used in multi-dimensional arrays as array of pointers. 
The following code snippet declares Identity Matrix 

	int rows = 3, cols = 3;
    // Declaring an Identity Matrix 
    int matrix[ rows ][ cols ] = { { 1, 0, 0 }, { 0, 1, 0 }, { 0, 0, 1 } };
	
As known arrays are stored in a set of contiguous memory cells and name of the array is associated with a pointer cell to this block of memory. Similarly in the code snippet shown above, `matrix` is the pointer pointing to single dimensional array of rows, where in each element of the row is pointer pointing to the corresponding column element as shown in figure below

**Graphical Representation of 2D Array and access using Array Name Pointer**

![2D Array and access using array name pointer][8]

[8]: /Users/narayan/Documents/MakeTechEzResources/images/GetOnToC++/S5_Matrix2D.jpg "2D Array and access using array name pointer"

<!--
[1]: https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToC++/S5_PointerRef.png "2D Array and access using array name pointer" 
-->

Here by default `matrix` points to zeroth row i.e. `matrix[0]` and `(matrix + 1)` points to `matrix[1]`. So *matrix of mth row* will be `(matrix + m)` pointing to `matrix[m]`. In 2 Dimensional Matrix each row points to corresponding column, so to `*(matrix)` is a pointer to pointer to zeroth row and zeroth column and `*(matrix) + 1` is the pointer pointing to zeroth row and first column. So *matrix of nth columns* can be accessed using `*(matrix) + (n-1)` which is a pointer to zeroth row and nth column, Hence the mth row and nth column can be accessed using

	*(matrix + m) + n;

The following code snippet shows traversing the matrix array using matrix pointer

    for ( int m = 0; m < rows; m++ )
    {
        for ( int n = 0; n < columns; n++ ) {
            // Printing the value stored in mth row and nth column
            cout << *((*(matrix + m)) + n) << " ";
        }
        cout << endl; // start new line of output
    } // end outer for

The identity matrix can also be traversed using Double Pointer i.e. a Pointer to a Pointer. For this declare a double pointer and allocate memory to create Array of Pointers and then make each element of the array point to the corresponding column of the identity matrix. Please refer the following code snippet.

	// Declaring Double Pointer to an Integer and allocating memory to create array 
	// of pointers. 
	int** matPtr = new int*[rows]; // matPtr is a array of pointers
	
	// Assigning each element of the matPtr to point to the corresponding column of 
	// the matrix 
    for (int i = 0; i < rows; i++) *(matPtr + i) = *(matrix + i);
    
The following code snippet shows traversing the identity matrix using matPtr double pointer defined above

	int **rowPtr = matPtr; // Defing rowPtr and initializing it to point to matPtr	int *colPtr = 0; // Defining colPtr and initializing to null
	// Loop through rows till the rowPtr reaches the end of the row.
    while(rowPtr != matPtr + rows) {
		colPtr = *rowPtr; // Making colPtr point to the first element of the row
		// Loop through columns till the colPtr reaches the end of the column.
		while(colPtr != colPtr + columns) {
			cout << *colPtr << " "; // Printing the value in the column
			colPtr++; // Increment the colPtr
		} // end of column
		rowPtr++; // Increment ithe rowPtr	
	} // end of row
    
**IMPORTANT NOTE 1:** The following code is invalid `int **matPtr = matrix; // Invalid Code`. Even though as shown in note 1, matrix can be accessed using pointer to a pointer. This is because the datatype of matrix is a `int [3][3]` and not `int **`; 

**IMPORTANT NOTE 2:** Hence as you can see the code snippet `int** matPtr = new int*[row];`, matPtr is allocated memory such that it becomes Array of Pointers. Then each element of matPtr is made to point to the corresponding column of the matrix as you can see the code snippet `for (int i = 0; i < row; i++) matPtr[i] = *(matrix + i);`

##### SIDE PROGRAM # &nbsp;10

Write a program that demonstrates traversing 2D array using pointer to a pointer. The code snippet above is converted tp Program below.


    //
    //  Program Name - S5_SP_2DPointers.cpp
    //  Series: GetOnToC++ Step: 5 Side Program
    //
    //  Purpose: This program demonstrates traversing 2D array using pointer 
    //           to a pointer.
    //
    //  Compile: g++ S5_SP_2DPointers.cpp -o exe/S5_SP_2DPointers
    //  Execute: exe/S5_SP_2DPointers
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    #include <iomanip>
    using namespace std;

    // Function Prototype to print Array
    void printMatrix( int** ); 

    const int rows = 3;
    const int columns = 3;

    int main()
    {
        // Declaring an Identity Matrix 
        int matrix[ rows ][ columns ] = { { 1, 0, 0 }, { 0, 1, 0 }, { 0, 0, 1 } };

        cout << "Printing the identity matrix using matrix variable:" << endl;
        
        // Loop through the rows and columns to Print the value stored in the 
        // identity matrix using matrix pointer
        // Modification Code # 1


        cout << "Printing the identity matrix using double pointer:" << endl;
        
		// Declaring Double Pointer to an Integer and allocating memory to create 
		// array of pointers. 
        // Modification Code # 2
        
		// Assigning each element of the matPtr to point to the corresponding 
		// column of the matrix 
        // Modification Code # 3
    	
    	// Call printMatrix function and pass matPtr
        // Modification Code # 4

        return 0;
    } // end main

    void printMatrix( int** matPtr )
    {
        int row = 0, col = 0;

        // Define rowPtr as pointer to a pointer to a integer and assign 
        // it to matPtr
        int** rowPtr = matPtr; 

        // Define colPtr as pointer to an integer and initialize it to NULL
        int* colPtr = 0;
        
        // Write while loop to loop thorugh rows and columns to print the values 
        // stored in matPtr
        // Modification Code # 5

		// Step 1 : Outer while loop for rows
        // Loop through rows using while loop using rowPtr till the rowPtr is 
        // equal to the pointer pointing to (matPtr + rows). That is till the 
        // rowPtr reaches the eand of the row. Use Pointer Arithmatic and 
        // Pointer Expression to derive value.
        
		// Step 2 - Inside the OUTER while loop for rows            
		// Set colPtr to Point to same location as rowPtr i.e. to the first
		// column of the corresponding row. 
		
		// Step 3 - Inner while Loop for columns
		// Loop through the columns using while loop till colPtr points to 
		// the same element as (*rowPtrs + columns) i.e. till the colPtr 
		// reaches the end of the column for that row
        	
		// Step 4 - Inside the INNER while loop for columns
		// Output the value stored in the colPtr and increment the colPtr
                
		// Step 5 - In the OUTER while loop for rows
		// Increment the rowPtr and Output the new line for the new row

    } // end function printMatrix

###### [Try Program Modifications Online](http://ideone.com/s2rj5E) 

- **Mod 1:** Modify the program to Loop through the rows and columns to Print the value stored in the identity matrix using matrix pointer
- **Mod 2:** Modify the program to Declare Double Pointer to an Integer and allocating memory to create array of pointers.
- **Mod 3:** Modify the program to assign each element of the matPtr to point to the corresponding column of the matrix 
- **Mod 4:** Modify the program to Call printMatrix function and pass matPtr
- **Mod 5:** Modify the program to Write while loop to loop thorugh rows and columns to output the values stored in matPtr
- **IMP Mod 6:** Modify the program in main function to show that the `matrix` which is a two dimenional array is stored continiousely in the memory as a single dimensional array. For this

	- Declare a variable matrixPtr which is a pointer to a integer and initial it to point to the first element of the matrix i.e. `matrix[0]`
	- Declare a while loop till matrixPtr Pointer reaches end the row and column element i.e. `matrix[0] + (rows * columns)`
	- Inside the while looop Output the value stored in matrixPtr and increment the matrixPtr

###### Programatic Questions

1. Can you re-define printMatrix function to take in matPtr as a constant pointer to constant pointer to a constant integer. If yes then

	a. Write the function prototype
	b. Write the function header
	c. In the function body redefine the datatype of rowPtr
	b. Redefine the datatype of colPtr
	e. Why doing this is benificial 

2. In the above program matPtr is a array of pointers where in each element of the array is pointing to corresponding column of the matrix variable. Does the memory arrangement of matPtr and matrix are the same. If not why???

3. Is the following code invalid `int **matPtr = matrix;`. If so why????

<a name="array_strings"/></a>
## Concept 8: Array of Pointers Based Strings
<br>
Another common use of Array of Pointers data structures is to form an array of pointer-based strings, referred to simply as a string array. 

Consider the declaration of string array suit that might be useful in representing a deck of cards:

	const char * const suit[ 4 ] = { "Hearts", "Diamonds", "Clubs", "Spades" };

The suit[4] portion of the declaration indicates an array of four elements. Each entry in the array is a string, but in C++ a string is essentially a pointer to its first character, so each entry in an array of strings is simply a pointer to the first character of a string. The const char * portion of the declaration indicates that each element of array suit is of type “pointer to char constant data.” So the declaration `const char * const suit[ 4 ] = {};` is read as ***suit array is Constant pointer to Character Constant***

The four values to be placed in the array are "Hearts", "Diamonds", "Clubs" and "Spades". Each is stored in memory as a null-terminated character string that is one character longer than the number of characters between quotes as shown in the figure below:

<br>
![Graphical Representation of Array][9]

[9]: /Users/narayan/Documents/MakeTechEzResources/images/GetOnToC++/S5_ArrayOfPointers.png "Graphical Representation of Array"
<!--
[9]: https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToC++/S5_ArrayOfPointers.png "Graphical Representation of Array"
-->
<p></p>

Although it appears as though these strings are being placed in the suit array, only pointers are actually stored in the array. Each pointer points to the first character of its corresponding string. Thus, even though the suit array is fixed in size, it provides access to character strings of any length. 

***
**IMPORTANT NOTE:** The suit strings could also be placed into a two-dimensional array, in which each row represents one suit and each column represents one of the letters of a suit name. Such a data structure must have a fixed number of columns per row, and that number must be as large as the largest string. In such a case , considerable memory is wasted as most are shorter than the longest string. 
***

##### SIDE PROGRAM # &nbsp;11

Write a program that demonstrates array of pointers using string array suit having hearts, diamonds, clubs and spades to represent the deck of cards. Traverse through the first dimensional array of rows and show the characters in each element of second dimensional array of columns. Also show that even in 2D array all the elements of the array are co-located in memory

    //
    //  Program Name - S5_SP_ArrayOfPointers.cpp
    //  Series: GetOnToC++ Step: 5 Side Program
    //
    //  Purpose: This program demonstrates array of pointers using string array 
    //           suit having hearts, diamonds, clubs and spades to represend 
    //           the deck of cards. Traverse through the first dimensional array 
    //           of rows and show the characters in each element of second 
    //           dimensional array of columns. Also show that even in 2D array 
    //           all the elements of the array are co-located in memory
    //
    //  Compile: g++ S5_SP_ArrayOfPointers.cpp -o exe/S5_SP_ArrayOfPointers
    //  Execute: exe/S5_SP_ArrayOfPointers
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    #include <string>
     
    using namespace std;
    const int MAX = 4;
     
    int main ()
    {
    	// Declare Integer Variable cntr and suitLength
        int cntr = 0, suitLength = 0;
        
    	// Declare variable suit array which is constant pointer to a character 
    	// constant. Initialize the array with values Hearts, Diamond, Club and 
    	// Spades
        const char * const suit[ MAX ] = { "Hearts", "Diamonds", 
                                           "Clubs", "Spades" };
                                           
		// Declare Variable suitPtr which is a pointer to a character constant and 
		// initialize it to point to suit[0]
        const char * suitPtr = suit[0]; 

		// Loop through the suit array to calculate the lenght of each suit and 
		// print each element of the suit array
        for (int i = 0; i < MAX; i++)
        {
        	// Calculating the total length of each suit
            suitLength += strlen(suit[i]);
            
            // Printing the suit array element
            cout << "Value of suit[" << i << "] = " << suit[i] << endl;
            
            cntr = 0; // Reset the cntr variable
            
            // Assign the suitPtr to element of the suit array corresponding to 
            // vairable  i
            suitPtr = suit[i]; 
            
            // Traverses the individual element of the array using while loop 
            // till the empty character is found in suitPtr. 
            // Print the character value stored in suitPtr and then Increment 
            // the suitPtr. This would print every character for a particular suit
            // of card.
            while (*suitPtr) 
            {
                cout << "Value of suit[ " << i << " ][ "<< cntr << "] = ";
                cout << *(suitPtr) << endl;
                cntr++; suitPtr++;
            }
            cout << endl;
        }

        cout << "Total characters in suit array is: " <<  suitLength << endl;    
        
        cntr = 0; // Resetting the cntr variable
        
        // Resetting the suitPtr to point to the first element of the suit Array
        suitPtr = suit[0];   
        
        // Traverses the whole array using while loop till the empty character 
        // is found in suitPtr
        while (*suitPtr ) 
        {
            if (cntr >= suitLength) break;
            cout << *(suitPtr) << " ";
            cntr++; suitPtr++;
            if (!(*suitPtr)) { 
                cout << *(suitPtr) << " "; 
                suitPtr++;
            }                    
        }

        cout << endl;
        return 0;
    }


**RESULT:**

    $ exe/S5_SP_ArrayOfPointers
    Value of suit[0] = Hearts
    Value of suit[ 0 ][ 0] = H
    Value of suit[ 0 ][ 1] = e
    Value of suit[ 0 ][ 2] = a
    Value of suit[ 0 ][ 3] = r
    Value of suit[ 0 ][ 4] = t
    Value of suit[ 0 ][ 5] = s

    Value of suit[1] = Diamonds
    Value of suit[ 1 ][ 0] = D
    Value of suit[ 1 ][ 1] = i
    Value of suit[ 1 ][ 2] = a
    Value of suit[ 1 ][ 3] = m
    Value of suit[ 1 ][ 4] = o
    Value of suit[ 1 ][ 5] = n
    Value of suit[ 1 ][ 6] = d
    Value of suit[ 1 ][ 7] = s

    Value of suit[2] = Clubs
    Value of suit[ 2 ][ 0] = C
    Value of suit[ 2 ][ 1] = l
    Value of suit[ 2 ][ 2] = u
    Value of suit[ 2 ][ 3] = b
    Value of suit[ 2 ][ 4] = s

    Value of suit[3] = Spades
    Value of suit[ 3 ][ 0] = S
    Value of suit[ 3 ][ 1] = p
    Value of suit[ 3 ][ 2] = a
    Value of suit[ 3 ][ 3] = d
    Value of suit[ 3 ][ 4] = e
    Value of suit[ 3 ][ 5] = s

    Total characters in suit array is: 25
    H e a r t s  D i a m o n d s  C l u b s  S p a d e s  


</br>
<a name="func_ptrs"/></a>
## Concept 9: Function Pointers
</br>

A **pointer to a function** contains the function’s address in memory. We know that an array’s name is actually the address in memory of the first element. Similarly, a function’s name is actually the address in memory of the code that performs the function’s task. Consider a function prototype f1 as shown in the code snippet below

	// Declaring fptr as a pointer to a function of type void (*) (int)
	// fptr can be read as pointer to a function taking int as a parameter and
	// returning void 
   	typedef void (*fptr)(int);
   	
	// Function Prototype for Function f1
	void f1 (int);

***

**NOTE :-** The following code snippet `typedef void (*fptr)(int);` can be read as 
***fptr is a pointer to a function taking int as a parameter and returning void*** 

***	

Pointers to functions can be used in following ways 

1. **Passed to functions :-** The following code snippet shows function pointer being passed in function f2

		// Function Prototype for Function f2
		void f2 ( int, fptr);
	
		// Passing Function f1 
		f2 (1, f1(0));

2. **Returned from functions :-** The following code snippet shows function pointer  is being returned from function f3 


		// Function Prototype for Function f3
    	fptr f3( int );
	
		// Function f3 returning pointer to function f1
	    fptr fptr1 = f3(2);
	    
	    // Calling function f1 using the function pointer fptr
	    fptr1(2)


3. **Stored in arrays :-** The following code snippet shows storing pointers to a function in an array

		// Declaring an array of function pointers
    	fptr f[1] = { f1 }; 
    	
    	// Calling the function f1 using the array
    	f[0](0);


4. **Assigned to other function pointers :-** The following code snippet shows function pointer can be assigned to other function pointer which takes in the same parameter type and return type

		// Function Prototype for Function f0. This is similar to f1 which takes 
		// int as input parameter and void as return parameter
		void f1 (int);
		
		// Assigning fptr function pointer to first point to f0 and then f1
		fptr fptr1 = &f0;
		fptr1(0);
		
		fptr1 = &f1;
		fptr1(1);
		

5. **Used to call the underlying function :-** The code snippet above shows function pointer fptr calling the function f0 and function f1. The code snippet below iterates the same

		// Assigning fptr function pointer to first point to f1 
		fptr fptr1 = &f1;
		
		// Use fptr1 to call the underlying function f1 and passing value 0
		fptr1(0);
		

##### SIDE PROGRAM # &nbsp;11

Write a Program that demonstrates different ways in which pointers to a function can be used

    //
    //  Program Name - S5_SP_FunctionPtrDemo.cpp
    //  Series: GetOnToC++ Step: 5 Side Program
    //
    //  Purpose: Demonstrating different ways in which pointers to a function 
    //           can be used
    //
    //  Compile: g++ S5_SP_FunctionPtrDemo.cpp -o exe/S5_SP_FunctionPtrDemo
    //  Execute: exe/S5_SP_FunctionPtrDemo
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    #include <iomanip>
    using namespace std;
    
	// Declare fptr as a pointer to a function of type void (*) (int)
	// fptr can be read as pointer to a function taking int as a parameter and
	// returning void 
    typedef void (*fptr)(int);
    
    // Function Prototype
    void f0( int );
    void f1( int );
    
    // Declare function prototype f2 to take int and function pointer fptr as a 
    // parameter and returning void
    void f2( int, fptr );
    
    
    // Declare function prototype f3 to take int as a parameter and returning 
    // function pointer fptr
    fptr f3( int );
    
    int main() 
    {
    	// Declare fPtrArr as an array of function pointers of type fptr and having 
    	// Function f1 as its element
        // Modification Code # 1
    	
        int choice;

        cout << "Enter a number between 0 and 2, 3 to end: "; cin >> choice;
        	
        while( choice >= 0 && choice<3 )
        {
            if (choice == 0) {
            	// Calling the function f1 using the array of function pointer 
            	// fPtrArr
		        // Modification Code # 2
            } 
            else if (choice == 1) {
            	// Calling function f2 passing choice and function f1 as a 
            	// parameter
		        // Modification Code # 3
		    }
            else if (choice == 2) {
				// Calling function f3 returning function pointer
		        // Modification Code # 4
            	
		    	// Calling function f1 using the function pointer fptr1
		        // Modification Code # 5
            	
				// Assigning fptr function pointer to point to f0
		        // Modification Code # 6
		    	
		    	// Calling function f0 using function pointer fptr1
		        // Modification Code # 7
            }
            
        	cout << "Enter a number between 0 and 2, 3 to end: "; cin >> choice;
        }
        cout << "Program execution completed." << endl;
        return 0;
    }

    void f0( int choice )
    {
    	cout << "Inside Function f0\n";
    }
    
    void f1( int choice )
    {
    	if (choice == 0)
       		cout << "You entered " << choice << " so function f1 was called\n";
        else if (choice == 1) 
        	cout << "Function f1 is being called from function f2" << endl;
        else if (choice == 2) 
        	cout << "Function f1 is being called from returned function f3" 
        		 << endl;
    }

    void f2( int choice, fptr fptr1  )
    {
       	cout << "You entered " << choice << " so function f2 was called\n";
       	
		// Using function pointer fptr1 to call the underlying function f1 
		// and passing choice variable
		// Modification Code # 8
    }

    fptr f3( int choice )
    {
       cout << "You entered " << choice << " so function f3 was called\n";
       return f1;
    }


###### [Try Program Modifications Online](http://ideone.com/BFuXSa) 

- **Mod 1:** Modify the program to Declare fPtrArr as an array of function pointers of type fptr and having Function f1 as its element
- **Mod 2:** Modify the program to Call the function f1 using the array of function pointer fPtrArr
- **Mod 3:** Modify the program to Call function f2 passing choice and function f1 as a parameter
- **Mod 4:** Modify the program to Call function f3 returning function pointer
- **Mod 5:** Modify the program to Call function f1 using the function pointer fptr1
- **Mod 6:** Modify the program to Call function f1 using the function pointer fptr1
- **Mod 7:** Modify the program to Assign fptr function pointer to point to f0
- **Mod 8:** Modify the program to Call function f0 using function pointer fptr1

###### Programatic Questions

1. Use typedef to Declare fPtr as a pointer to a function of type int (*) (int, int)
2. How the function pointer fPtr is read
3. How the function pointer fPtr Passed to a function f have int as another parameter and returning void
4. How to Declare an array of function pointers fPtrArr of type fPtr and having 
some Function f1 as its element
5. How would you declare a variable fPtr1 of type Function Pointer fPtr and assign it to Function f1
6. How would you call the underlying Function f1 using variable fPtr1


</br>
<a name="void_ptrs"/></a>
## Concept 10: Void Pointers
</br>

The void type of pointer is a special type of pointer. In C++, void represents the absence of type. Therefore, void pointers are pointers that point to a value that has no type (and thus also an undetermined length and undetermined dereferencing properties).

This gives void pointers a great flexibility, by being able to point to any data type, from an integer value or a float to a string of characters. In exchange, they have a great limitation: the data pointed by them cannot be directly dereferenced (which is logical, since we have no type to dereference to), and for that reason, any address in a void pointer needs to be transformed into some other pointer type that points to a concrete data type before being dereferenced.

One of its possible uses may be to pass generic parameters to a function. For example: 