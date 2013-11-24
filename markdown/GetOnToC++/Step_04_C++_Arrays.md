# Step 4: &nbsp;C/C++ Arrays
</br>

The objective of this step is to introduce all about Arrays write from Array Declaration, Passing Array to Functions, Search and Sorting Arrays to Multi-Dimensional Arrays. Before we dive into Arrays we will have brief look into enum declaration and usage. The concepts introduced in this step are:

1. [**Enums**](#enums)
2. [**Arrays and Declaration**](#arrays)
3. [**Global, Local and Static Local Arrays**](#array_types)
4. [**Passing Arrays to Functions**](#passing_arrays)
5. [**Sorting Arrays**](#sorting_arrays)
6. [**Searching Arrays**](#searching_arrays)
7. [**Multi-dimensional Arrays**](#multi_dim_arrays)

Finally the end of the section specifies a [**Programming Problem**](#prog_problem) that will try to use all the concepts covered in this step 

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

The following figure shows an integer array called c that contains 12 elements. You refer to any one of these elements by giving the array name followed by the particular element’s position number in square brackets ([]). 

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
    
##### SIDE PROGRAM # &nbsp;3

Write a Program that demonstrates the course mark obtained by student graphically in a bar of astricks to visualize the grade distribution. Suppose the grades were 87, 68, 94, 100, 83, 78, 85, 91, 76 and 87. Show the grade distribution in 0-9, 10 - 19, etc. So the mark 87 fall in the rage of 80 - 89

    //
    //  Program Name - S4_SP_GradeDistribution.cpp
    //  Series: GetOnToC++ Step: 4 Side Program
    //
    //  Purpose: This Program Demonstrates the course mark obtained by student
    //           in a bar of astricks to visualize the grade distribution. 
    //           Suppose the grades were 87, 68, 94, 100, 83, 78, 85, 91, 76 
    //           and 87. Show the grade distribution in 0-9, 10 - 19, etc. So
    //           the mark 87 fall in the rage of 80 - 89
    //
    //  Compile: g++ S4_SP_GradeDistribution.cpp -o S4_SP_GradeDistribution
    //  Execute: ./S4_SP_GradeDistribution
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>    #include <iomanip>    using namespace std;
    int main() 
    {        const int marksDistrSize = 11, numStudents = 10;

        // Initializing the array with Marks obtained by students        int marks[numStudents] = { 87, 68, 94, 100, 83, 78, 85, 91, 76, 87 }; 

        // Initializing Marks Distributions array elements with 0
        int marksDistribution[marksDistrSize] = {};

        cout << "Grade distribution:" << endl; 

        // for loop to find the mark distribution
        for(int i = 0; i < numStudents; ++i)        {
            ++marksDistribution[marks[i]/10];
        }
        // for each element of array n, output a bar of the chart        for(int i = 0; i < marksDistrSize; ++i)        {
            // output bar labels ("0-9:", ..., "90-99:", "100:" )            if ( i == 0 )                cout << " 0-9: ";            else if ( i == 10 )                cout << "  100: ";            else                cout << i * 10 << "-" << ( i * 10 ) + 9 << ": ";
            // print bar of asterisks            for ( int stars = 0; stars < marksDistribution[ i ]; ++stars )                cout << '*';
            cout << endl; // start a new line of output        }  // end outer for
    }

**RESULT:**

    $ ./S4_SP_GradeDistribution
    Grade distribution:
      0-9: 
    10-19: 
    20-29: 
    30-39: 
    40-49: 
    50-59: 
    60-69: *
    70-79: **
    80-89: ****
    90-99: **
      100: *

<a name="array_types"/></a>
## Global, Local and Static Local Arrays
</br>

The Global, local and Static Local Arrays are similar to what was discussed in last step. Local Variables retain their scope within the function or the block it is defined. While Global Variables are defined outside the function and retain their values throughout execution of the program. Global variables and global functions can be referenced by any function that follows their declarations or definitions in the source file. Static local variable in a function definition exists for the program’s duration but is visible only in the function’s body. 

##### SIDE PROGRAM # &nbsp;4

Write a program that demonstrates Array Scope, Global Scope, Local to the function and static local variable in a function definition exists for the program’s duration but is visible only in the function’s body

    //
    //  Program Name - S4_SP_ArrayVarScope.cpp
    //  Series: GetOnToC++ Step: 4 Side Program
    //
    //  Purpose: This program demonstrates Array Scope, Global Scope, Local to
    //           the function and static local variable in a function definition 
    //           exists for the program’s duration but is visible only in the 
    //           function’s body
    //
    //  Compile: g++ S4_SP_ArrayVarScope.cpp -o S4_SP_ArrayVarScope
    //  Execute: ./S4_SP_ArrayVarScope
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>    using namespace std;

    // function prototype
    void globalArrayInit( void );    void staticArrayInit( void );    void localArrayInit( void ); 
    const int arraySize = 3;

    // Global Array Variable initialized to 0
    int array1[ arraySize ] = {};

    int main()    {        cout << "First call to each function:\n";
        globalArrayInit();        staticArrayInit();        localArrayInit();
        cout << "\n\nSecond call to each function:\n";        globalArrayInit();        staticArrayInit();        localArrayInit();        cout << endl;    } //end main


    // function to demonstrate usage of global array    void globalArrayInit( void )    {        cout << "\nValues on entering globalArrayInit: \n";
        // output contents of array1        for ( int i = 0; i < arraySize; ++i )            cout << "array1[" << i << "] = " << array1[i] << " ";
  
        cout << "\nValues on exiting globalArrayInit: \n";         
        // modify and output contents of array1        for ( int j = 0; j < arraySize; ++j )            cout << "array1[" << j << "] = " << (array1[j] += 10) << " ";
        cout << endl;
    } // end function globalArrayInit

    // function to demonstrate an automatic local array    void localArrayInit( void )    {
        // initializes elements each time function is called        int array1[ arraySize ] = { 1, 2, 3 }; // automatic local array

        cout << "\n\nValues on entering localArrayInit:\n"; 
        // output contents of array1        for ( int i = 0; i < arraySize; ++i )            cout << "array1[" << i << "] = " << array1[i] << " ";
        cout << "\nValues on exiting localArrayInit:\n"; 
        // modify and output contents of array1
        for ( int j = 0; j < arraySize; ++j )            cout << "array1[" << j << "] = " << (array1[j]+=5) << " ";
        cout << "\nGlobal Values on exiting localArrayInit:\n"; 
        // output contents of global array1        for ( int i = 0; i < arraySize; ++i )            cout << "array1[" << i << "] = " << ::array1[i] << " ";
        cout << endl;
    } // end function localArrayInit

    // function to demonstrate a static local array    void staticArrayInit( void )    {        // initializes elements to 0 first time function is called        static int array1[ arraySize ]; // static local array

        cout << "\nValues on entering staticArrayInit: \n"; 
        // output contents of array1        for ( int i = 0; i < arraySize; ++i )            cout << "array1[" << i << "] = " << array1[i] << " ";

        cout << "\nValues on exiting staticArrayInit:\n";
        // modify and output contents of array1        for ( int j = 0; j < arraySize; ++j )            cout << "array1[" << j << "] = " << (array1[j] += 5) << " ";
        cout << endl;
    } // end function staticArrayInit


**RESULT:**


    $ ./S4_SP_ArrayVarScope
    First call to each function:

    Values on entering globalArrayInit: 
    array1[0] = 0 array1[1] = 0 array1[2] = 0 
    Values on exiting globalArrayInit: 
    array1[0] = 10 array1[1] = 10 array1[2] = 10 

    Values on entering staticArrayInit: 
    array1[0] = 0 array1[1] = 0 array1[2] = 0 
    Values on exiting staticArrayInit:
    array1[0] = 5 array1[1] = 5 array1[2] = 5 


    Values on entering localArrayInit:
    array1[0] = 1 array1[1] = 2 array1[2] = 3 
    Values on exiting localArrayInit:
    array1[0] = 6 array1[1] = 7 array1[2] = 8 
    Global Values on exiting localArrayInit:
    array1[0] = 10 array1[1] = 10 array1[2] = 10 


    Second call to each function:

    Values on entering globalArrayInit: 
    array1[0] = 10 array1[1] = 10 array1[2] = 10 
    Values on exiting globalArrayInit: 
    array1[0] = 20 array1[1] = 20 array1[2] = 20 

    Values on entering staticArrayInit: 
    array1[0] = 5 array1[1] = 5 array1[2] = 5 
    Values on exiting staticArrayInit:
    array1[0] = 10 array1[1] = 10 array1[2] = 10 


    Values on entering localArrayInit:
    array1[0] = 1 array1[1] = 2 array1[2] = 3 
    Values on exiting localArrayInit:
    array1[0] = 6 array1[1] = 7 array1[2] = 8 
    Global Values on exiting localArrayInit:
    array1[0] = 20 array1[1] = 20 array1[2] = 20 

***
**PERFORMANCE TIP:** We can apply static to a local array declaration so that it is not created and initialized each time the program calls the function and is not destroyed each time the function terminates. This can improve performance, especially when using large arrays.
***

<a name="passing_arrays"/></a>
## Passing Arrays to Functions
</br>

To pass an array argument to a function, specify the name of the array without any brackets. For example, if array hourlyTemperatures has been declared as
	int hourlyTemperatures[ 24 ]; 
the function call
	modifyHourlyTemp( hourlyTemperatures, 24 );

When passing an array to a function, the array size is normally passed as well, so the function can process the specific number of elements in the array. Otherwise, we would need to build this knowledge into the called function itself or, worse yet, place the array size in a global variable. 

When const qualifier applied to an array parameter, the array cannot be modified. Any attempt by the function to modify such array will result in a compilation error. The following Side Program # 5 will illustrate the const qualifier in a function call. 

***
**NOTE #1:** &nbsp;C++ passes arrays to functions by reference. This means the functions can modify the element values in the callers’ original arrays. The value of the name of the array is the address in the computer’s memory of the first element of the array. 

**NOTE #2:** &nbsp;Because the starting address of the array is passed, the called function knows precisely where the array is stored in memory. Therefore, when the called function modifies array elements in its function body, it’s modifying the actual elements of the array in their original memory locations. 

**NOTE #3:** &nbsp; **Pass By Reference and Pass By Value** will be covered in detail in next step.

**PERFORMANCE TIP:** &nbsp; Passing by reference makes sense for performance reasons. Passing by value would require copying each element.  
***

##### SIDE PROGRAM # &nbsp;5

Write a program to demonstrate passing array to function. Firstly Array is passed as reference, then an array element is passed by value and finally a const array is passed to function.

    //
    //  Program Name - S4_SP_PassingArray.cpp
    //  Series: GetOnToC++ Step: 4 Side Program
    //
    //  Purpose: This program demonstrates passing array to function. Firstly
    //           Array is passed as reference, then an array element is passed
    //           by value and finally a const array is passed to function. You
    //           will notice when const array is passed no modification to the 
    //           array element is possible
    //
    //  Compile: g++ S4_SP_PassingArray.cpp -o S4_SP_PassingArray
    //  Execute: ./S4_SP_PassingArray
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    #include <iomanip>    using namespace std;

    // function prototype
    void modifyArray( int [], int ); // array and its size for modification    void modifyElement( int ); // receive array element value
    void printArray( const int [], int ); // Const array for print

    int main()    {
        const int arraySize = 5; // size of array a        int a[ arraySize ] = { 0, 1, 2, 3, 4 }; // initialize array a
        cout << "Effects of passing entire array by reference:"             << "\nThe values of the original array are:\n";
        // output original array elements.        // Here array a is passed by reference and as a const array and hence 
        // cannot be modified
        printArray(a, arraySize);

        // Here array a is passed by reference to modifyArray function
        modifyArray(a, arraySize);

        cout << "The values of the modified array are:\n";         // output modified array elements        printArray(a, arraySize);

        cout << "\nEffects of passing array element by value:"             << "\na[3] before modifyElement: " << a[ 3 ] << endl;
        modifyElement( a[ 3 ] ); // pass array element a[ 3 ] by value        cout << "a[3] after modifyElement: " << a[ 3 ] << endl;
    } // end main

    // In function modifyArray, "b" points to the original array "a" in memory
    void modifyArray( int b[], int sizeOfArray )
    {
        // multiply each array element by 2        for ( int k = 0; k < sizeOfArray; ++k )            b[ k ] *= 2;    } // end function modifyArray

    // In function modifyElement, "e" is a local copy of    // array element a[ 3 ] passed from main    void modifyElement( int e )    {        // multiply parameter by 2        cout << "Value of element in modifyElement: " << ( e *= 2 ) << endl;    } // end function modifyElement

    // In function printArray, "b" cannot be used to modify the original 
    // array "a" in main.    void printArray( const int b[], int sizeOfArray )    {        // b[ 0 ] /= 2; Any Modification will result in compilation error
        // output modified array elements        for(int j=0; j < sizeOfArray; ++j)            cout << setw( 3 ) << b[ j ];        cout << endl;
    } // end function printArray


**RESULT:**

    $ ./S4_SP_PassingArray
    Effects of passing entire array by reference:
    The values of the original array are:
      0  1  2  3  4
    The values of the modified array are:
      0  2  4  6  8

    Effects of passing array element by value:
    a[3] before modifyElement: 6
    Value of element in modifyElement: 12
    a[3] after modifyElement: 6


<a name="sorting_arrays"/></a>
## Sorting Arrays
</br>

Sorting data means placing the data into some particular order such as ascending or descending order. It is one of the most important computing applications as it is required in many day to day real world problems for e.g. phone directories are sorted by last name and, within that, by first name to make it easy to find phone numbers. Here we will look at 2 sorting techniques. They are:

1. **Insertion Sort**
2. **Bubble Sort**

#### Insertion Sort

Insertion sort is a simple, but inefficient, sorting algorithm. The first iteration of this algorithm takes the second element and, if it’s less than the first element, swaps it with the first element (i.e., the program inserts the second element in front of the first element). The second iteration looks at the third element and inserts it into the correct position with respect to the first two elements, so all three elements are in order. At the ith iteration of this algorithm, the first i elements in the original array will be sorted.

##### SIDE PROGRAM # &nbsp;6

Write a program that sorts the 10-element array data with values 34 56 4 10 77 51 93 30 5 52 into ascending order using Insertion Sort Algorithm. 

    //
    //  Program Name - S4_SP_InsertionSort.cpp
    //  Series: GetOnToC++ Step: 4 Side Program
    //
    //  Purpose: This program sorts the 10-element array data with values 
    //           34 56 4 10 77 51 93 30 5 52 into ascending order using 
    //           Insertion Sort Algorithm.
    //
    //  Compile: g++ S4_SP_InsertionSort.cpp -o S4_SP_InsertionSort
    //  Execute: ./S4_SP_InsertionSort
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    #include <iomanip>    using namespace std;

    // function prototype
    void doInsertionSort( int [], int ); // Sort Array using Insertion Sort
    void printArray( const int [], int ); // Const array for print

    int main()    {        const int arraySize = 10; // size of array a        int data[ arraySize ] = { 34, 56, 4, 10, 77, 51, 93, 30, 5, 52 };

        cout << "Unsorted array:\n";
        printArray(data, arraySize); // output original array

        // Sorting Array using insertion Sort
        doInsertionSort(data, arraySize);

        cout << "\nSorted array:\n";
        printArray(data, arraySize); // output sorted array

    } // end main

    // Sort Array using insertion Sort
    // Note here the array data is the local variable pointing to the same 
    // memory location as the array data in the main function. This is because 
    // the original data array in the main function is passed by reference
    void doInsertionSort( int data[], int arraySize)
    {
        int insert; // temporary variable to hold element to insert
        int iter = 0; // This tracks the number of iteration needed for Sorting

        // loop over the elements of the array        for ( int next = 1; next < arraySize; ++next )        {            insert = data[ next ]; // store the value in the current element            int moveItem = next; // initialize location to place element
            iter++; // Incrementing the Iteration
            // Search for the location in which to put the current element
            // In the while loop re-sorting is done upto the current iteration            while ( ( moveItem > 0 ) && ( data[ moveItem - 1 ] > insert ) )            {
                iter++; // Incrementing the Iteration
                // shift element one slot to the right                data[ moveItem ] = data[ moveItem - 1 ];                moveItem--;            } // end while

            // place inserted element into the array at the appropriate location
            // identified by moveItem array position            data[ moveItem ] = insert;         } // end for    
        cout << "\nNumber of Iteration needed for Sorting is: " << iter << endl;
    }

    // In function printArray, "b" cannot be used to modify the original 
    // array "a" in main.    void printArray( const int b[], int sizeOfArray )    {        // b[ 0 ] /= 2; Any Modification will result in compilation error
        // output modified array elements        for(int j=0; j < sizeOfArray; ++j)            cout << setw( 4 ) << b[ j ];        cout << endl;
    } // end function printArray


**RESULT:**

    $ ./S4_SP_InsertionSort
    Unsorted array:
      34  56   4  10  77  51  93  30   5  52

    Number of Iteration needed for Sorting is: 30

    Sorted array:
       4   5  10  30  34  51  52  56  77  93

#### Bubble Sort

Bubble Sort Algorithm is also called Sinking Algorithm. Its called Bubble Sort because the smaller values gradually "bubble" their way upward to the top of the array like air bubbles rising in water, while the larger value sink to the bottom of the array. 

The technique is to make several pass through the array. On each pass successive pairs of element are compared till the last element of the array. If the pair is in increasing order than the value is left as is or else he values are swapped in the array.

##### SIDE PROGRAM # &nbsp;7

Modify the side program number 6 to sorts the 10-element array data with values 34 56 4 10 77 51 93 30 5 52 into ascending order using Bubble Sort Algorithm. 

    //
    //  Program Name - S4_SP_BubbleSort.cpp
    //  Series: GetOnToC++ Step: 4 Side Program
    //
    //  Purpose: This program sorts the 10-element array data with values 
    //           34 56 4 10 77 51 93 30 5 52 into ascending order using 
    //           Bubble Sort Algorithm.
    //
    //  Compile: g++ S4_SP_BubbleSort.cpp -o S4_SP_BubbleSort
    //  Execute: ./S4_SP_BubbleSort
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    #include <iomanip>    using namespace std;

    // function prototype
    void doBubbleSort( int [], int ); // Sort Array using Bubble Sort
    void printArray( const int [], int ); // Const array for print

    int main()    {        const int arraySize = 10; // size of array a        int data[ arraySize ] = { 34, 56, 4, 10, 77, 51, 93, 30, 5, 52 };

        cout << "Unsorted array:\n";
        printArray(data, arraySize); // output original array

        // Sorting Array using Bubble Sort
        doBubbleSort(data, arraySize);
        cout << "\nSorted array after Bubble Sort:\n";
        printArray(data, arraySize); // output sorted array
    } // end main

    // Sort Array using Bubble Sort
    // Note here the array a is the local variable pointing to the same 
    // memory location as the array data in the main function. This is because 
    // the original data array in the main function is passed by reference
    void doBubbleSort( int a[], int size) 
    {
        int hold;

        // Variable to track the number of iteration needed 
        // for Sorting
        int iter = 0; 

        // Boolean to Check if the Sorting is complete
        bool isSortComplete = true; 

        // loop over the elements of the array        for ( int pass = 1; pass < size; pass++ )        {
            isSortComplete = true;            iter++; // Incrementing the Iteration
            for ( int j = 0; j < size - 1; j++ )            {
                iter++; // Incrementing the Iteration
                if ( a[j] > a [j+1] ) {
                    isSortComplete = false;
                    hold = a[j];
                    a[j] = a [j+1];
                    a [j+1] = hold;
                }            } // end inner for loop

            // Breaking out of for loop if sorting is complete
            if (isSortComplete) break;
        } // end for loop

        cout << "\nNumber of Iteration needed for Sorting is: " << iter << endl;
    } // end of function doBubbleSort

    // In function printArray, "b" cannot be used to modify the original 
    // array "a" in main.    void printArray( const int b[], int sizeOfArray )    {        // b[ 0 ] /= 2; Any Modification will result in compilation error
        // output modified array elements        for(int j=0; j < sizeOfArray; ++j)            cout << setw( 4 ) << b[ j ];        cout << endl;
    } // end function printArray


**RESULT:**

    ./S4_SP_BubbleSort
    Unsorted array:
      34  56   4  10  77  51  93  30   5  52

    Number of Iteration needed for Sorting is: 10

    Sorted array after Bubble Sort:
       4   5  10  30  34  51  52  56  77  93

***
**NOTE:** As you can see from Side Program 6 and 7, the number of Iteration required for Bubble Sort is 10 while for the same array the number of Iteration required for Insertion Sort is 30. 
***

<a name="searching_arrays"/></a>
## Searching Arrays
</br>

Often it may be necessary to determine whether an array contains a value that matches a certain key value. The process of finding a particular element of an array is called searching. This section will discuss 2 Searching Techniques. They are:

1. **Linear Search**

2. **Binary Search**

</br>
#### Linear Search Technique

The linear search compares each element of an array with a search key. Because the array is not in any particular order, it’s just as likely that the value will be found in the first element as the last. On average, therefore, the program must compare the search key with half the elements of the array to find the value. And  to determine that a value is not in the array, the program must compare the search key to every element of the array.

The linear searching method works well for small arrays or for unsorted arrays (i.e., arrays whose elements are in no particular order). However, for large arrays, linear searching is inefficient. If the array is sorted (e.g., its elements are in ascending order), the high-speed binary search technique is more efficient.

##### SIDE PROGRAM # &nbsp;7

Write a program to determine whether an array contains a value that matches a certain key using a Linear Search Technique

    //
    //  Program Name - S4_SP_LinearSearch.cpp
    //  Series: GetOnToC++ Step: 4 Side Program
    //
    //  Purpose: This program demonstrated whether an array contains a value 
    //           that matches a certain key using a Linear Search Technique
    //
    //  Compile: g++ S4_SP_LinearSearch.cpp -o S4_SP_LinearSearch
    //  Execute: ./S4_SP_LinearSearch
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    using namespace std;

    // function prototype for linear search
    int linearSearch( const int [], int, int ); 

    int main()    {        const int arraySize = 15; // size of array a        int a[ arraySize ]; // create array a        int searchKey; // value to locate in array a
        // Constructing an array of even numbers from 0 to 30        
        for ( int i = 0; i < arraySize; ++i )            a[ i ] = 2 * i; // create some data


        cout << "Enter integer search key: ";        cin >> searchKey;

        // attempt to locate searchKey in array a        int element = linearSearch( a, searchKey, arraySize );

        // display results        if (element != -1)            cout << '\n' << searchKey << " Found in array element " 
                 << element << endl;        else            cout << '\n' << searchKey << " not found" << endl;    } //end main

    // compare key to every element of array until location is    // found or until end of array is reached; return index of    // element if key is found or -1 if key not found    int linearSearch( const int array[], int key, int sizeOfArray )    {
        int index = -1; // By Default, key is not found
        int iter = 0; // Number of Iteration        for ( int j = 0; j < sizeOfArray; ++j ) {
            iter++;            if ( array[ j ] == key )  { // if found,                index = j; // assigns index the location of key
                break;
            }
        }

        cout << "Number of iteration for linear search: " << iter << endl;        return index; // returning the index if value found or -1
    } // end function linearSearch


**RESULT:**

    ./S4_SP_LinearSearch
    Enter integer search key between 0 and 28: 10
    Number of iteration for linear search: 6
    10 Found in array element 5

    $ ./S4_SP_LinearSearch
    Enter integer search key between 0 and 28: 29
    Number of iteration for linear search: 15
    29 not found


</br>
#### Binary Search Technique

The Binary Search algorithm is more efficient then the Linear Search Algorithm but it requires the array to be first sorted in ascending order before applying the Binary Search Algorithm. This algorithm eliminates one half of the elements in the array being searched after each comparison. 

The algorithm locates the middle element of the array and compares it to the search key. If they are equal, the search key is found and the corresponding index of the array element is returned. Otherwise, the problem is reduced to searching one half the array. If the search key is less then the middle element of the array, then the first half of the array is searched, otherwise the second half is searched. Again if the search key is not in the middle element of the specified sub array (piece of the original array), the algorithm is repeated on one quarter of the original array. The search continues until the search key is equal to the middle element of the subarray or until the subarray consists of one element that is not equal to the search key (i.e. in case the search key is not found)  

In Worst case scenario, the searching array of 1024 elements will take only 10 comparisons using the binary search. Repeatedly dividing 1024 by 2 yields the value 512, 256, 128, 64, 32, 16, 8, 4, 2, 1 as dividing by 2 is quivalent to one comparison in binary search algorithm. Therefore number 1024 is $$$2^{10}$$$, hence is divided by 2 only 10 times to get the value 1. Similarly 1048576 is $$$2^{20}$$$, hence is divided by 2 only 20 times to get the value 1.

##### SIDE PROGRAM # &nbsp;7

Write a program to determine whether an array contains a value that matches a certain key using a Binary Search Technique

    //
    //  Program Name - S4_SP_BinarySearch.cpp
    //  Series: GetOnToC++ Step: 4 Side Program
    //
    //  Purpose: This program demonstrated whether an array contains a value 
    //           that matches a certain key using a Linear Search Technique
    //
    //  Compile: g++ S4_SP_BinarySearch.cpp -o S4_SP_BinarySearch
    //  Execute: ./S4_SP_BinarySearch
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    #include <iomanip>    using namespace std;

    // Function Prototype 

    // Search Element using binary search
    int binarySearch( const int [], int, int, int, int ); 

    // Print a Header for the output
    void printHeader( const int ); 

    // Print one row of output showing the sub array being processed
    void printRow( const int [], int, int, int, int ); 

    int main()    {        const int arraySize = 15; // size of array a        int a[ arraySize ]; // create array a        int searchKey; // value to locate in array a
        // Constructing an array of even numbers from 0 to 30        
        for ( int i = 0; i < arraySize; ++i )            a[ i ] = 2 * i; // create some data

        cout << "Enter integer search key between 0 and 28: ";        cin >> searchKey;

        printHeader(arraySize);

        // attempt to locate searchKey in array a using Linear Search        element = binarySearch( a, searchKey, 0, arraySize-1, arraySize );

        // display results        if (element != -1)            cout << '\n' << searchKey << " Found in array element " 
                 << element << endl;        else            cout << '\n' << searchKey << " not found" << endl;    } //end main

    // Search Element using binary search
    // The algorithm locates the middle element of the array and compares it 
    // to the search key. If equal Search is complete or else if less the first
    // half is selected or else the second half. The process is repeated till 
    // the middle element of the sub array is equal to the search key or else 
    // until one element remains
    int binarySearch( const int b[], int searchKey, int low, int high, int size)
    {
        int middle;
        int index = -1; // By Default, key is not found
        int iter = 0; // Number of Iteration
        while (low <= high)
        {
            iter++;
            middle = (low + high)/2;

            // Printing the Row under Consideration
            printRow( b, low, middle, high, size);

            if (searchKey == b[middle]) {
                index = middle; // match found on the middle row
                break;
            } else if ( searchKey < b[middle] )
                high = middle - 1; // Search low end of the array
            else 
                low = middle + 1; // Search high end of the array

        } // end while loop

        cout << "Number of iteration for binary search: " << iter << endl;        return index; // returning the index if value found or -1
    } // end of binarySearch

    // Print a Header for the output
    void printHeader( const int size)
    {
        cout << "\nSubscripts:\n";
        for (int i = 0; i < size; i++)
            cout << setw(3) << i << ' ';
        cout << '\n';
        for (int i = 1; i <= 4*size; i++)
            cout << '-';
        cout << endl;    
    } 

    // Print one row of output showing the sub array being processed
    void printRow( const int b[], int low, int middle, int high, int size)
    {
        for (int i = 0; i < size; i++)
        {
            if ( i < low || i > high)
                cout << "    ";
            else if ( i == middle )
                cout << setw(3) << b[i] << '*';
            else
                cout << setw(3) << b[i] << ' ';
        } // end for loop

        cout << endl;
    } 


**RESULT:**

    $ ./S4_SP_BinarySearch
    Enter integer search key between 0 and 28: 10

    Subscripts:
      0   1   2   3   4   5   6   7   8   9  10  11  12  13  14 
    ------------------------------------------------------------
      0   2   4   6   8  10  12  14* 16  18  20  22  24  26  28 
      0   2   4   6*  8  10  12                                 
                      8  10* 12                                 
    Number of iteration for binary search: 3

    10 Found in array element 5

    $ ./S4_SP_BinarySearch
    Enter integer search key between 0 and 28: 29

    Subscripts:
      0   1   2   3   4   5   6   7   8   9  10  11  12  13  14 
    ------------------------------------------------------------
      0   2   4   6   8  10  12  14* 16  18  20  22  24  26  28 
                                     16  18  20  22* 24  26  28 
                                                     24  26* 28 
                                                             28*
    Number of iteration for binary search: 4

    29 not found

****
**NOTE:** From the above Side Programs, for the same array and the same search key Binary Search Technique takes maximum of 4 iterations while the Linear Search Technique takes maximum of 15 iterations.
****

</br>
<a name="multi_dim_arrays"/></a>
## Multi-dimensional Arrays
</br>

Arrays with two dimensions (i.e., subscripts) often represent tables of values consisting of information arranged in rows and columns. To identify a particular table element, we must specify two subscripts. By convention, the first identifies the element’s row and the second identifies the element’s column. Arrays that require two subscripts to identify a particular element are called two-dimensional arrays or 2-D arrays. Arrays with two or more dimensions are known as multidimensional arrays and can have more than two dimensions.

Its **important to understand** all array elements are stored consecutively in memory, regardless of the number of dimensions. In a two-dimensional array, row 0 is stored in memory followed by row 1. 

The following figure illustrates a two-dimensional array, a. The array contains three rows and four columns, so it’s said to be a 3-by-4 array. In general, an array with m rows and n columns is called an m-by-n array.

![2D Array][2]

[2]: /Users/narayan/Documents/MakeTechEzResources/images/GetOnToC++/2DArray.png "2D Array"

<!--
[1]: https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToC++/2DArray.png "2D Array"
-->

Every element in array a is identified in the above Figure by an element name of the form a[ i ][ j ], where a is the name of the array, and i and j are the subscripts that uniquely identify each element in a

***
**Note** that we can also read 2-D array `int a[2][3];` as a is a pointer pointing  to the first row a[ 0 ] of the 3 rows of 2-D Array. While a[ 0 ] is the pointer pointing to the single dimensional array of columns. The Array and Pointers will be elaborated more in the next step.
***

##### SIDE PROGRAM # &nbsp;8

Write a program that demonstrates different ways of initializing 2D Array during Declaration.

    //
    //  Program Name - S4_SP_2DArrayDemo.cpp
    //  Series: GetOnToC++ Step: 4 Side Program
    //
    //  Purpose: This program demonstrates different ways of initializing 
    //           2D Array during Declaration.
    //
    //  Compile: g++ S4_SP_2DArrayDemo.cpp -o S4_SP_2DArrayDemo
    //  Execute: ./S4_SP_2DArrayDemo
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>    #include <iomanip>    using namespace std;

    // Function Prototype to print Array
    // The printArray function is used to output each array’s elements.
    void printArray( const int [][ 3 ] ); 
    const int rows = 2;    const int columns = 3;

    int main()    {
        // Local Array Variable initialisation

        // The declaration of array1 provides six initializers in two sublists.
        // The first sublist initializes row 0 of the array to 1, 2 and 3; while 
        // the second sublist initializes row 1 of the array to 4, 5, and 6
        // Note: array1 can also be initialized as { 1, 2, 3, 4, 5, 6 };
        int array1[ rows ][ columns ] = { { 1, 2, 3 }, { 4, 5, 6 } };

        // The declaration of array2 provides only five initializers. Firstly 
        // the row 0 is initialized with the first 3 elements 1, 2 and 3 then 
        // row 1 is initialized with 4, 5 and 0. 
        // Note: Any elements that do not have an explicit initializer are 
        // initialized to zero, so array2[1][2] is initialized to zero.        int array2[ rows ][ columns ] = { 1, 2, 3, 4, 5 };

        // The declaration of array3 provides three initializers in two sublists. 
        // The sublist for row 0 explicitly initializes the first two elements of 
        // row 0 to 1 and 2; the third element is implicitly initialized to zero. 
        // The sublist for row 1 explicitly initializes the first element to 4 and 
        // implicitly initializes the last two elements to zero.        int array3[ rows ][ columns ] = { { 1, 2 }, { 4 } };

        cout << "Values in array1 by row are:" << endl;        printArray( array1 );
        cout << "\nValues in array2 by row are:" << endl;        printArray( array2 );
        cout << "\nValues in array3 by row are:" << endl;        printArray( array3 );    } // end main

    // The printArray function is used to output each array’s elements.
    // Note that the function prototype and definition specify the parameter 
    // const int a[][columns]. When a function receives a one-dimensional array 
    // as an argument, the array brackets are empty in the function’s parameter 
    // list. The size of a two-dimensional array’s first dimension i.e. the 
    // number of rows is not required either, but all subsequent dimension sizes 
    // are required. The compiler uses these sizes to determine the locations in 
    // memory of elements in multidimensional arrays. 
    void printArray( const int a[][ columns ] )    {        // loop through array's rows        for ( int i = 0; i < rows; ++i )        {            cout << "Row # " << i+1 << ": ";            // loop through columns of current row            for ( int j = 0; j < columns; ++j )                cout << a[ i ][ j ] << ' ';            cout << endl; // start new line of output        } // end outer for    } // end function printArray


**RESULT:**

    $ ./S4_SP_2DArrayDemo
    Values in array1 by row are:
    Row # 1: 1 2 3 
    Row # 2: 4 5 6 

    Values in array2 by row are:
    Row # 1: 1 2 3 
    Row # 2: 4 5 0 

    Values in array3 by row are:
    Row # 1: 1 2 0 
    Row # 2: 4 0 0 

***
**Note No 1: Array Initialization during Declaration**

As you can see the program above, Array can be initialized using Sublists as in 

`int array1[ 2 ][ 3 ] = { { 1, 2, 3 }, { 4, 5, 6 } };` 

or directly without any sublist 

`int array2[ 2 ][ 3 ] = { 1, 2, 3, 4, 5 };`

Also Note that during initialization any elements that do not have an explicit initializer are initialized to zero

**Note No 2:** While passing multi-dimensional array to a function, the function definition must specify the size of all the dimension except the first one as seen in the function definition of printArray

`void printArray( const int a[][ 3 ] )`

This is because the compiler uses these sizes to determine the locations in memory of elements in multidimensional arrays. 

***


</br>  
<a name="prog_problem"/></a>
## Programming Problem
</br>  

Write a program that stores the students and their grade in 2D Array. Using the 2D Array, finds the lowest grade, highest grade, and the mean i.e. the average grade. First sort the array using bubble sort and then find the lowest, highest and the average grade. Further for the overall class show the grade distribution.

    //
    //  Program Name - S4_MP_StudentGrades.cpp
    //  Series: GetOnToC++ Step: 4 Main Program
    //
    //  Purpose: This program stores the students and their grade in 2D Array. 
    //           Using the 2D Array, this program finds the lowest grade, highest
    //           grade, and the mean i.e. the average grade. First sort the array 
    //           using bubble sort and then find the lowest, highest and the 
    //           average grade. Further for the overall class show the grade 
    //           distribution.
    //
    //  Compile: g++ S4_MP_StudentGrades.cpp -o S4_SP_StudentGrades
    //  Execute: ./S4_SP_StudentGrades
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>    #include <iomanip>
    #include <string.h> // This header file is included to use function memcpy    using namespace std;

    // Constants
    const int students = 10; // number of students
    const int tests = 3; // number of tests

    // Function Prototype

    void sortStudentGrades( int [][tests] ); // Sorting each Students Grades
    void doBubbleSort( int [], int ); // Sort Array using Bubble Sort
    float averageGrade( const int [], int ); // Find the average Grade for each Student
    void printGrades( const int [][tests] ); // Printing Student Grades

    // Printing Grade Analytics
    void printGradeAnalytics( const int [][tests], int  [][tests] ); 

    int main()
    {
        // two-dimensional array of student grades        int studentGrades[ students ][ tests ] =
            {   { 87, 96, 70 },                { 68, 87, 90 },                { 94, 100, 90 }, 
                { 100, 81, 82 }, 
                { 83, 65, 85 },                { 78, 87, 65 },                { 85, 75, 83 },                { 91, 94, 100 }, 
                { 76, 72, 84 },                { 87, 93, 73 }  };

        // Printing the grades
        cout << "\nThe grades for the student is:\n\n";
        printGrades( studentGrades );
         // This local variable array is used to store sorted student grades. 
        // Note - Its better to initialize the array to 0 else the array will 
        //        have junk values.
        int sortedStudentGrades[ students ][ tests ] = {};

        // Using function memcpy to copy into sortedStudentGrades array from 
        // studentGrades array. Its better to use memcpy function then using 
        // a nested loop to copy every element. 
        // Note - In many platforms, memcpy() is written in highly-optimized 
        //        assembly code. Therefore, the performance gain of using 
        //        memcpy() instead of nested loops can be significant.

        memcpy(sortedStudentGrades, studentGrades, sizeof(sortedStudentGrades)); 

        // Sorting the Student Grades
        sortStudentGrades( sortedStudentGrades );

        // Printing the grades
        cout << "\nThe grades for the student after Sorting is:\n\n";
        printGrades( sortedStudentGrades );
         // Printing the grades
        printGradeAnalytics( studentGrades, sortedStudentGrades );

    } // end main

    // Sorting each Students grades using Bubble Sort Algorithm
    void sortStudentGrades( int grades[][tests] )
    {
        // create rows/columns of text representing array grades        for ( int student = 0; student < students; ++student )
        {
            doBubbleSort(grades[student], tests);
        } // end of for loop
    } // end sortStudentGrades function

    // Sort Array using Bubble Sort
    void doBubbleSort( int a[], int size) 
    {
        int hold;

        // Variable to track the number of iteration needed 
        // for Sorting
        int iter = 0; 

        // Boolean to Check if the Sorting is complete
        bool isSortComplete = true; 

        // loop over the elements of the array        for ( int pass = 1; pass < size; pass++ )        {
            isSortComplete = true;            iter++; // Incrementing the Iteration
            for ( int j = 0; j < size - 1; j++ )            {
                iter++; // Incrementing the Iteration
                if ( a[j] > a [j+1] ) {
                    isSortComplete = false;
                    hold = a[j];
                    a[j] = a [j+1];
                    a [j+1] = hold;
                }            } // end inner for loop

            // Breaking out of for loop if soring is complete
            if (isSortComplete) break;
        } // end for loop

        //cout << "\nNumber of Iteration needed for Sorting is: " << iter << endl;
    } // end of function doBubbleSort

    // Average Grade for Each Student
    float averageGrade( const int setOfGrades[], int tests) 
    {
        int total = 0; // initialize total        // sum grades in array        for ( int grade = 0; grade < tests; ++grade ) 
            total += setOfGrades[ grade ];        // return average of grades        return static_cast< double >( total ) / tests;
    }

    void printGrades( const int grades[][tests] )
    {
        // create rows/columns of text representing array grades        for ( int student = 0; student < students; ++student )
        {
            cout << "Student " << setw( 4 ) << student + 1;
            // output student's grades            for ( int test = 0; test < tests; ++test )                cout << setw( 9 ) << grades[ student ][ test ];
            cout << endl;
        } // end of outer for loop
    } // end printGrades

    void printGradeAnalytics( const int grades[][tests], 
    						   int sortedGrades[][tests] )
    {
        // Lowest, Highest and Average Grade of the Students and the corresponding 
        // Student
        int lowestGrade = 100, highestGrade = 0;
        int lowestGrade4Student = 0, highestGrade4Student = 0;

        // stores frequency of grades in each range of 10 grades        const int frequencySize = 11;        int frequency[ frequencySize ] = {}; // initialize elements to 0

        cout << "\nThe Grade Analytics on the Students Grades are:\n\n";
        cout << "\t\t"; // allign the column heads

        // create a column heading for each of the tests
        for ( int test = 0; test < tests; ++test )
            cout << " Test " << test+1 << " ";

		// student average column heading
        cout << " Lowest " << " Highest " << " Average" << endl;  
                // create rows/columns of text representing array grades        for ( int student = 0; student < students; ++student )
        {
            cout << "Student " << setw( 4 ) << student + 1;
            // output student's grades            for ( int test = 0; test < tests; ++test ) {                cout << setw( 9 ) << grades[ student ][ test ];
                ++frequency[ grades[ student ][ test ] / 10 ];
            }

            // Printing the lowest and highest grade for each student
            cout << setw( 8 ) << fixed << sortedGrades[ student ][0];
            cout << setw( 8 ) << fixed << sortedGrades[ student ][tests-1];

            // call member function getAverage to calculate student's average;            // pass row of grades and the value of tests as the the arguments
            double average = averageGrade( grades[ student ], tests );
            cout << setw( 9 ) << setprecision( 2 ) << fixed << average;

            // Initializing the lowest and highest grade
            if (student == 0) {
                lowestGrade4Student = student+1;
                lowestGrade = sortedGrades[ student ][0]; 
                highestGrade4Student = student+1;
                highestGrade = sortedGrades[ student ][tests-1]; 
            }

            // Finding the Student with Lowest and Highest Grade

            if (sortedGrades[ student ][0] < lowestGrade) {
                lowestGrade4Student = student+1;
                lowestGrade = sortedGrades[ student ][0]; 
            }

            if (sortedGrades[ student ][tests-1] > highestGrade) {
                highestGrade4Student = student+1;
                highestGrade = sortedGrades[ student ][tests-1]; 
            }
            cout << endl;
        } // end of outer for loop

        // Printing the Lowest and Highest Grade
        cout << "\nThe Lowest Grade is: " << lowestGrade 
             << " Obtained by Student Num: " << lowestGrade4Student << endl;
        cout << "The Highest Grade is: " << highestGrade 
             << " Obtained by Student Num: " << highestGrade4Student << endl;

        // Printing the Grade Distribution Chart
        // for each element of array n, output a bar of the chart
        cout << "\nOverall grade distribution:" << endl;        for(int i = 0; i < frequencySize; ++i)        {
            // output bar labels ("0-9:", ..., "90-99:", "100:" )            if ( i == 0 )                cout << " 0-9: ";            else if ( i == 10 )                cout << "  100: ";            else                cout << i * 10 << "-" << ( i * 10 ) + 9 << ": ";
            // print bar of asterisks            for ( int stars = 0; stars < frequency[ i ]; ++stars )                cout << '*';
            cout << endl; // start a new line of output        }  // end outer for

    } // end printGrades


**RESULT:**

    $ ./S4_SP_StudentGrades

    The grades for the student is:

    Student    1       87       96       70
    Student    2       68       87       90
    Student    3       94      100       90
    Student    4      100       81       82
    Student    5       83       65       85
    Student    6       78       87       65
    Student    7       85       75       83
    Student    8       91       94      100
    Student    9       76       72       84
    Student   10       87       93       73

    The grades for the student after Sorting is:

    Student    1       70       87       96
    Student    2       68       87       90
    Student    3       90       94      100
    Student    4       81       82      100
    Student    5       65       83       85
    Student    6       65       78       87
    Student    7       75       83       85
    Student    8       91       94      100
    Student    9       72       76       84
    Student   10       73       87       93

    The Grade Analytics on the Students Grades are:

		     Test 1  Test 2  Test 3  Lowest  Highest  Average
    Student    1       87       96       70      70      96    84.33
    Student    2       68       87       90      68      90    81.67
    Student    3       94      100       90      90     100    94.67
    Student    4      100       81       82      81     100    87.67
    Student    5       83       65       85      65      85    77.67
    Student    6       78       87       65      65      87    76.67
    Student    7       85       75       83      75      85    81.00
    Student    8       91       94      100      91     100    95.00
    Student    9       76       72       84      72      84    77.33
    Student   10       87       93       73      73      93    84.33

    The Lowest Grade is: 65 Obtained by Student Num: 5
    The Highest Grade is: 100 Obtained by Student Num: 3

    Overall grade distribution:
     0-9: 
    10-19: 
    20-29: 
    30-39: 
    40-49: 
    50-59: 
    60-69: ***
    70-79: ******
    80-89: ***********
    90-99: *******
      100: ***

***
**NOTE:** The above program uses function memcpy defined in string.h header file to copy into destination array from the source array. Its better to use memcpy function then using a nested loop to copy every element. This is because in many platforms, memcpy() is written in highly-optimized assembly code. Therefore, the performance gain of using memcpy(). The function memcpy is covered in Step 6.
***