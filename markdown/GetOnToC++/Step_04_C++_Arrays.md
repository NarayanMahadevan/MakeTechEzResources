# Step 4: &nbsp;C++ Arrays
</br>

The objective of this step is to introduce all about Arrays write from Array Declaration, Passing Arry to Functions, Search and Sorting Arrays to Multi-Dimensional Arrays. Before we dive into Arrays we will have brief look into enum declaration and usage. The concepts introduced in this step are:

1. [**Enums**](#enums)
2. [**Arrays and Declaration**](#arrays)
3. [**Passing Arrays to Functions**](#passing_arrays)
4. [**Searching Arrays**](#searching_arrays)
5. [**Sorting Arrays**](#sorting_arrays)
6. [**Multi-dimensional Arrays**](#multi_dim_arrays)


<a name="enums"/></a>
## Enums
</br>

The enum keyword is used to create an enumerated type, which is a collection of related constants. For e.g. enumeration of months

	￼enum Months { JAN = 1, FEB, MAR, APR, MAY, JUN, JUL, AUG, SEP, OCT, NOV, DEC };
	Months month; // The variable month can only take values defined in Month enum

##### SIDE PROGRAM # &nbsp;1

This program demonstrates enum to show the car models

    //
    //  Program Name - S4_SP_CarModel.cpp
    //  Series: GetOnToC++ Step: 4 Side Program
    //
    //  Purpose: This program uses enum to show the car Model
    //
    //  Compile: g++ S4_SP_CarModel.cpp -o S4_SP_CarModel
    //  Execute: ./S4_SP_CarModel
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    using namespace std;

    // Defining enum of car models
    typedef enum {
        FORD,
        HONDA,
        NISSAN,
        PORSCHE
    } CarModel;

    main ( ) { 
        
        CarModel myCar = NISSAN;
        switch (myCar) {
            case FORD:
            case PORSCHE:
                cout << "You like Western cars?" << endl;
                break;
            case HONDA:
            case NISSAN:
                cout << "You like Japanese cars?" << endl;
                break;
            default:
                break;
        }
    }

**RESULT:**

	$ ./S4_SP_CarModel
	You like Japanese cars?

<a name="arrays"/></a>
## Arrays and Declaration
</br>

An array is a consecutive group of memory locations that all have the same type. To refer to a particular location or element in the array, we specify the name of the array and the position number of the particular element in the array.

The following figure shows an integer array called c that contains 12 elements. You refer to any one of these elements by giving the array name followed by the particular element’s posi- tion number in square brackets ([]). 

**Array of 12 Elements**

![Array of 12 Elements][1]

[1]: /Users/narayan/Documents/MakeTechEzResources/images/GetOnToC++/ArrayOf12Elems.png "Array of 12 Elements"

<!--
[1]: https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToC++/ArrayOf12Elems.png "Array of 12 Elements" 
-->

Arrays occupy space in memory. To specify the type of the elements and the number of elements required by an array use a declaration of the form 

	type arrayName[ arraySize ];

The compiler reserves the appropriate amount of memory. The arraySize must be an integer constant greater than zero. For example, to tell the compiler to reserve 12 elements for integer array c, use the declaration

	int c[ 12 ]; // c is an array of 12 integers
		
##### SIDE PROGRAM # &nbsp;2

Write a Program to Set the array to the even integers from 2 to 20 and Compute the sum of the elements of the array.

    //
    //  Program Name - S4_SP_ArrayDemo.cpp
    //  Series: GetOnToC++ Step: 4 Side Program
    //
    //  Purpose: Set the array to the even integers from 2 to 20 and Compute 
    //           the sum of the elements of the array.
    //
    //  Compile: g++ S4_SP_ArrayDemo.cpp -o S4_SP_ArrayDemo
    //  Execute: ./S4_SP_ArrayDemo
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>    #include <iomanip>    using namespace std;
    int main() 
    {        // constant variable can be used to specify array size        const int arraySize = 10;
        int total = 0;
        int s[ arraySize ]; // array s has 10 elements

        for ( int i = 0; i < arraySize; ++i ) // set the values            s[ i ] = 2 + 2 * i;

        cout << "Element" << setw( 13 ) << "Value" << endl;

        // output contents of array s in tabular format        for ( int j = 0; j < arraySize; ++j ) {            cout << setw( 7 ) << j << setw( 13 ) << s[ j ] << endl;
            total += s[ j ];
        }

        cout << "Total of array elements: " << total << endl;    } // end main

**RESULT:**

	$ ./S4_SP_ArrayDemo
    Element        Value
          0            2
          1            4
          2            6
          3            8
          4           10
          5           12
          6           14
          7           16
          8           18
          9           20
    

<a name="passing_arrays"/></a>
## Passing Arrays to Functions
</br>

<a name="searching_arrays"/></a>
## Searching Arrays
</br>

<a name="sorting_arrays"/></a>
## Sorting Arrays
</br>

<a name="multi_dim_arrays"/></a>
## Multi-dimensional Arrays
</br>

