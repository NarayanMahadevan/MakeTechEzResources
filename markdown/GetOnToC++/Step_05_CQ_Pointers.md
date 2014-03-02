# Step 5: &nbsp;C/C++ Pointers Concept Questions
</br>

1. [**Pointer Variable Declaration and Initialization**](#ptr_var)

2. [**Pointer Operators**](#ptr_oper)

3. [**Calling Function by Reference**](#call_by_ref)

4. [**Using Const Qualifier with Pointers**](#const_ptr)

5. [**Relationship between Pointers and Arrays**](#ptr_and_array)

6. [**sizeOf Operator with Pointer and Array**](#ptr_and_array)

7. [**Pointer to a Pointer(Multiple Indirection)**](#ptr_to_ptr)

8. [**Arrays of Pointers**](#array_ptrs)

9. [**Function Pointers**](#func_ptrs)

</br>
<a name="ptr_var"/></a>
## Concept 1: Pointer Variable Declaration and Initialization

###### [Try Program Modifications Online](http://ideone.com/1EsbCY) 
- **Mod 1:** Modify the program to check if yPtr is null. If yPtr is not null print the value and address of yPtr. If null print the address of the yPtr. 
- **Mod 2:** Modify the program to initialize the yPtr to null. Check if any memory is allocated to yPtr.
- **Mod 3:** Modify the program to show the size of Memory yPtr holds is same as the size of memory of variable y which is same as size of int data type. 
- **IMP Mod 4:** Modify the program to initialize yPtr to point to y. Show the content and address of yPtr and y variable are the same. 

###### Programatic Questions

1. Write code to initialize a pointer to null 
2. Write code to initialize a pointer to point to a variable
3. Check if pointer is a null pointer or not
4. What happens if you assign value to a pointer using `*xptr = 5;` if xptr is a null pointer
5. In the following code `int * xptr = 0; double * yptr = 0;` What is the memory of `sizeof(xptr); sizeof(yptr);`. If xptr and yptr are initialized to point to a corresponding int and double data. Then what will be the memory `sizeof(*xptr); sizeof(*yptr);`


<a name="ptr_oper"/></a>
## Concept 2: Pointer Operators

###### [Try Program Modifications Online](http://ideone.com/KWiJfe) 
- **Mod 1:** Modify the program to assign new value to y, show that the yPtr also has the same value. 
- **Mod 2:** Modify the program to assign new value to yPtr, show that y also has the same value. 
- **IMP Mod 3:** Modify the above program to show the  &*yPtr is same as *&yptr which is same as yPtr as well as same as &y 

###### Programatic Questions

1. In the following code `int x = 33; int * xptr;`, write code to initialize xptr to point to x;
2. Write code to check variables xptr and x are pointing to the same memory location
3. Write code to check the data value of xptr pointer variable and the value of x variable is the same
4. Write code to modify the value of xptr and show xptr and x have the same value


<a name="call_by_ref"/></a>
## Concept 3: Calling Function by Reference

###### [Try Program Modifications Online](http://ideone.com/C3vEU8) 
- **IMP Mod 1:** Modify the program to show the memory address of variable n in cubeByValue function is different from the variable number defined in main. 
- **IMP Mod 2:** Modify the program to show the memory address of variable cubeVal in cubeByReference is same as the memory address of variable cubeRefVal defined in main. 
- **IMP Mod 3:** Modify the Program to pass cubeValue as a parameter in cubeByReference function instead of cubeRefVal
- **IMP Mod 4:** Modify the function passByReferenceTest to show in pass-by-reference the value if modified for xPtr, the same value is reflected for yPtr and y datatype
- **IMP Mod 5:** Modify the function passByReferenceTest to show  xPtr can legally point to new Memory address but will not affect the yPtr


###### Programatic Questions

1. If `int x = 5;` write function f1 to take parameter x by value and by reference
2. If `int x = 5; int * xPtr = &x;` write function f1 to take parameter xPtr by value and by reference

<a name="const_ptr"/></a>
## Concept 4: Using Const Qualifier with Pointers

#### A Nonconstant Pointer to Nonconstant Data

###### [Try Program Modifications Online](http://ideone.com/qYMEE3) 
- **IMP Mod 1:** Modify the program by updating the data of yPtr using de-referenced pointer and show programatically the same value is reflected for y 
- **IMP Mod 2:** Modify the program by updating the yPtr to point to x and show yPtr can legally point to new Memory address but will not affect y

###### Programatic Questions

1. Declare a non-constant pointer dblPtr to a non-constant data of datatype double. How would you read such a declaration.
2. If `double dbl1 = 100.00, dbl2 = 50.0;`, write code to show dblPtr pointing to dbl1.
3. Assign dblPtr to have the value of dbl2. Is the address and the value of dbl1 same as the  dblPtr.
4. Assign dblPtr to have the address of dbl2. Is the address and the value of dbl1 same as the  dblPtr

#### A Nonconstant Pointer to Constant Data

###### [Try Program Modifications Online](http://ideone.com/qYMEE3) 
- **Mod 1:** Modify the program to define xPtr variable which is Pointer to constant Data of int data type
- **Mod 2:** Modify the program to assign xPtr to point to yPtr. Show programatically xPtr, yPtr and y point to the same locaton
- **Mod 3:** Modify the program to assign xPtr to point to x. Show programatically xPtr and yPtr are pointing to different locaton
- **Mod 4:** Modify the program to assign new value to xPtr. Is it possible what is the error you get. What is the benifit of using a pointer to a constant data???

###### Programatic Questions

1. Declare a  pointer dblPtr to a constant data of datatype double. How would you read such a declaration.
2. Define function prototype modifyPtr2ConstData which takes pointer to a constant data as a argument
3. Define function header for the function prototype modifyPtr2ConstData. Name the variable as xPtr
4: In the function body modify xPtr to point to new memory address 
5: Can you change the value of the xPtr. If not why?


#### A Constant Pointer to Nonconstant Data

###### [Try Program Modifications Online](http://ideone.com/qYMEE3) 

- **Mod 1:** Modify Program to specify a constPtr variable which is a Constant Pointer to an Integer.
- **Mod 2:** Modify Program to assign value of x to constPtr. This is possible as data can be changed. If constPtr was initialized to point to yPtr, show programatically if the value of constPtr and yPtr are the same.
- **Mod 3:** Modify Program to update constPtr to point to variable x. Is this possible?? If not what is the error???

###### Programatic Questions

1. Declare a constant pointer dblPtr to a data of datatype double. How would you read such a declaration.
2. Initialize the dblPtr. Is it compulsary to initialize the dblPtr? If so why??
3. Can you change the value of the dblPtr. If so why?
4. Can you assign dblPtr to point to a new memory. If not why?

#### A Constant Pointer to Constant Data 

###### [Try Program Modifications Online](http://ideone.com/qYMEE3) 

- **Mod 1:** Modify Program to specify a variable xPtr which is a Constant Pointer to an Integer Constant.
- **Mod 2:** Modify Program to assign xPtr to point to variable y. Is this possible?? If not what is the error???
- **Mod 3:** Modify Program to update xPtr to have value of y. Is this possible?? If not what is the error???

###### Programatic Questions

1. Declare a constant pointer flPtr to a float constant. How would you read such a declaration.
2. Initialize the flPtr. Is it compulsary to initialize the flPtr? If so why??
3. Can you change the value of the flPtr. If not why?
4. Can you assign flPtr to point to a new memory. If not why?


<a name="ptr_and_array"/></a>
## Concept 5: Relationship between Pointer and Array

#### Array, Pointers and Pointer Comparisons

###### [Try Program Modifications Online](http://ideone.com/qYMEE3) 

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

#### Pointer Expressions and Pointer Arithmetic


