# Step 2: Loop and Conditional Expressions
</br>

The Objective of this step is to introduce to C++ Predicates, Conditional Statements, and loops. The concept introduced in this section are:

1. [**Boolean Expression**](#c++_bool_expr)
2. [**One and Two way Conditional Statements**](#if_else_loop)
3. [**The while Repitition Loop**](#while_loop)
4. [**do...while Repetition Statement**](#do_while_loop)
5. [**The for Repitition Loop**](#for_loop)
6. [**Multi-way Conditional Statement**](#switch_loop)
7. [**Logical Operators**](#logical_oper)

Finally the end of the section specifies a [**Programming Problem**](#prog_problem) that will try to use all the concepts covered in this step 

<a name="c++_bool_expr"/></a>
## Boolean Expression
</br>

Boolean expression is an expression that produces a true or false result. In C++, a Boolean expression is an expression that produces either 0, meaning false, or any other integer, meaning true. C++ offers several expressions that test the relationship between pairs of numbers. They are categorized as Relational Operators and Equality Operators. The relational operators all have the same level of precedence and associate left to right. The equality operators both have the same level of pre- cedence, which is lower than that of the relational operators, and associate left to right.

![Equality and Relational Operator][1]

[1]: /Users/narayan/Documents/MakeTechEzResources/images/GetOnToC++/EqualityRelnOper.png "Equality and Relational Operator"

<!--
[1]: https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToC++/EqualityRelnOper.png "Equality and Relational Operator" 
-->

##### SIDE PROGRAM # &nbsp;1

Write a Program that tests the Equality and Relational operator between two numbers

    //
    //  Program Name - S2_SP_TestNumPredicate.cpp
    //  Series: GetOnToC++ Step: 2 Side Program
    //
    //  Purpose: Write a Program that tests the Equality and Relational operator
    //           between an Int and a double value
    //
    //  Compile: g++ S2_SP_TestNumPredicate.cpp -o S2_SP_TestNumPredicate
    //  Execute: ./S2_SP_TestNumPredicate
    //
    //  Created by Narayan Mahadevan on 10/11/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    using namespace std;


    main ( ) { 
        int i = 50; 
        double d = 50.0; 

        // Note that either the int is caseted as double or viceversa to apply 
        // equal and relational operator between the two numbers

        cout << "i == (int) d    yields " << (i == (int) d)    << endl; 
        cout << "(double) i != d yields " << ((double) i != d) << endl; 
        cout << "i > (int) d     yields " << (i > (int) d)     << endl; 
        cout << "(double) i < d  yields " << ((double) i < d)  << endl; 
        cout << "i >= (int) d    yields " << (i >= (int) d)    << endl; 
        cout << "(double) i <= d yields " << ((double) i <= d) << endl; 
    }

**RESULT:**

	$ ./S2_SP_TestNumPredicate
	i == (int) d    yields 1
	(double) i != d yields 0
	i > (int) d     yields 0
	(double) i < d  yields 0
	i >= (int) d    yields 1
	(double) i <= d yields 1

<a name="if_else_loop"/></a>
## One and Two way Conditional Statements
</br>

An if Statement are one way conditional statements in c++ while the if/else statement are the two way conditional statements. An if statement contains a Boolean expression, in parentheses, followed by an embedded statement:

	if (Boolean expression) 
  		if true statement 
  	else 
  		if false statement

When the Boolean expression of an if statement evaluates to any integer other than 0, C++ considers the expression to be true and executes the embedded statement; otherwise, if the Boolean expression evaluates to 0, C++ considers the expression to be false and executes the else statement

##### SIDE PROGRAM # &nbsp;1

Write a Program that reads the mark as input and outputs grades as well as pass or fail.

    //
    //  Program Name - S2_SP_CalcGrade.cpp
    //  Series: GetOnToC++ Step: 2 Side Program
    //
    //  Purpose: Write a Program that reads the mark as input and outputs grades as 
    //			 well as pass or fail.
    //
    //  Compile: g++ S2_SP_CalcGrade.cpp -o S2_SP_CalcGrade
    //  Execute: ./S2_SP_CalcGrade
    //
    //  Created by Narayan Mahadevan on 10/11/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    using namespace std;

    // Defining a Macro determine pass or fail
    // Note that this alternate way of writing if/else loop
    // The Format: (Boolean Expression ? IF TRUE : IF FALSE)
    #define PASS_FAIL(grade) (grade >= 60 ? "PASSED" : "FAILED")

    main ( ) { 
        // Read the mark from user input        
        int mark = 0;
        cout << "Enter the mark = ";
        cin >> mark;
        
        // check the if loop to determine the grade
        char grade;
        if (mark >= 90 ) grade = 'A';
        else if (mark >= 80) grade = 'B';
        else if (mark >= 70) grade = 'C';
        else grade = 'D';

        // Printing the result and the grade
        cout << "The result is: " << PASS_FAIL(grade) << " And Grade is: " 
        	 << grade << endl;

    } 
    
**RESULT:**

	$ ./S2_SP_CalcGrade
	Enter the mark = 92
	The result is: PASSED And Grade is: A
    

<a name="while_loop"/></a>
## The while Repitition Loop
</br>

C++'s iteration statements enable functions to do computations over and over until a test has been satisfied. C++'s while statement, for example, consists of a Boolean expression, in parentheses, followed by an embedded statement:

	while (Boolean expression) 
  		embedded statement 
  
The Boolean expression is evaluated, and if the Boolean expression evaluates to any integer other than 0, the embedded statement is evaluated as well; otherwise, C++ skips the embedded statement. In contrast to an if statement, however, the evaluate-Boolean-expression–evaluate-embedded-statement cycle continues as long as the Boolean expression evaluates to some integer other than 0.

##### SIDE PROGRAM # &nbsp;2

Write a Program that reads a number and its corresponding power as inputs to calculate power of a number. For e.g. 2 power of 5 = 2 x 2 x 2 x 2 x 2 = 32. 

    //
    //  Program Name - S2_SP_PowerOfCalc.cpp
    //  Series: GetOnToC++ Step: 2 Side Program
    //
    //  Purpose: Write a Program that reads a number and its corresponding power as 
    // 			 inputs to calculate power of a number. 
    //			 For e.g. 2 power of 5 = 2 x 2 x 2 x 2 x 2 = 32
    //
    //  Compile: g++ S2_SP_PowerOfCalc.cpp -o S2_SP_PowerOfCalc
    //  Execute: ./S2_SP_PowerOfCalc
    //
    //  Created by Narayan Mahadevan on 10/11/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    using namespace std;

    main ( ) { 
    
        // Read the Base Number and the Power of number
        int baseNum = 0, powerOf = 0;

        cout << "Enter Base Number: "; cin >> baseNum;
        cout << "Enter the powerOf number: "; cin >> powerOf;
        
        // result is achieved by multiplying base number n times, 
        // where n is the powerOf number.
        int n = powerOf; int result = 1;
        while (n != 0) {
            result = result * baseNum;
            n = n - 1;
        }
        
        // Printing the result
        cout << baseNum << " to power of " << powerOf << " is: " << result << endl;

    }

**RESULT:**

	$ ./S2_SP_PowerOfCalc
	Enter Base Number: 2
	Enter the powerOf number: 6
	2 to power of 6 is: 64

<a name="do_while_loop"/></a>
## do...while Repitition Loop
</br>

The do...while repetition statement is similar to the while statement. In the while state- ment, the loop-continuation condition test occurs at the beginning of the loop before the body of the loop executes. The do...while statement tests the loop-continuation con- dition after the loop body executes; therefore, the loop body always executes at least once.

##### SIDE PROGRAM # &nbsp;3

Write a Program that prints the 1 through 10 using do…while loop

    //
    //  Program Name - S2_SP_DoWhileLoopTest.cpp
    //  Series: GetOnToC++ Step: 2 Side Program
    //
    //  Purpose: Write a Program that prints the 1 through 10 using do…while loop
    //
    //  Compile: g++ S2_SP_DoWhileLoopTest.cpp -o S2_SP_DoWhileLoopTest
    //  Execute: ./S2_SP_DoWhileLoopTest
    //
    //  Created by Narayan Mahadevan on 10/11/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>    using namespace std;
    int main() {
        int counter = 1; // initialize counter        do        {               cout << counter << " "; // display counter            ++counter; // increment counter        } while ( counter <= 10 ); // end do...while
        cout << endl;
    } // end main

**RESULT:**

	$ ./S2_SP_DoWhileLoopTest
	1 2 3 4 5 6 7 8 9 10


<a name="for_loop"/></a>
## The for Repitition Loop
</br>

As you would see in while loops, the details that govern the looping appear in three places: the place where the counting variable is initialized, the place where it is tested, and the place where it is reassigned. Such distribution makes the looping difficult to understand. In case of for loop, there is an entry expression, followed by Boolean Expression, followed by continuation expression. 

	for (entry expression; Boolean expression; continuation expression) 
		embedded statement 

The entry expression is evaluated only once, when the for statement is entered. Once the entry expression is evaluated, the Boolean expression is evaluated, and if the result is not 0, the embedded statement is evaluated, followed by the continuation expression. Then, the Boolean-expression–embedded-statement–continuation-expression evaluation cycle continues until the Boolean expression eventually evaluates to 0.

##### SIDE PROGRAM # &nbsp;4

Write a program to take a number from the user and find the sum of add and even numbers

    //
    //  Program Name - S2_SP_ForLoopTest.cpp
    //  Series: GetOnToC++ Step: 2 Side Program
    //
    //  Purpose: Write a Program to Sum the Odd and Even Integers
    //
    //  Compile: g++ S2_SP_ForLoopTest.cpp -o S2_SP_ForLoopTest
    //  Execute: ./S2_SP_ForLoopTest
    //
    //  Created by Narayan Mahadevan on 10/11/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>    using namespace std;
    int main() {
        // Local Variable for the user defined number and variable to
        // maintain the sum of odd and even numbers        int num = 0, sumOdd = 0, sumEven = 0;
        // Read the Number from the user        cout << "Enter a number: "; cin >> num; 
        for ( int i = 0; i <= num; i++ ) // iterate from 0 to num        {
            if (i%2 == 0) sumEven += i; // Adding Even Numbers
            else sumOdd += i; // Adding Odd Numbers        } // end for

        // Printing the Result
        cout << "Sum of Even Numbers: " << sumEven
             << "\nSum of Odd Numbers: " << sumOdd << endl;    } // end main
**RESULT:**

	$ ./S2_SP_ForLoopTest
	Enter a number: 4
	Sum of Even Numbers: 6 // 2 + 4 = 6
	Sum of Odd Numbers: 4 // 1 + 3 = 4

<a name="switch_loop"/></a>
## Multi-way Conditional Statement
</br>

The purpose of a switch statement is to execute a particular sequence of statements according to the value of an expression that produces an integer or a character or a constant value. In most switch statements, each anticipated value of the integer-producing expression and the corresponding sequence of statements is sandwiched between a case symbol on one end and a break statement on the other, with a colon separating the anticipated value and the statement sequence:

	switch (integer-producing expression) { 
  		case integer constant 1: statements for integer 1 break; 
  		case integer constant 2: statements for integer 2 break; 
  		... 
  		default: default statements 
	} 

When such a switch statement is encountered, the expression is evaluated, producing an integer or a char. That value is compared with the integer or char constants found following the case symbols. As soon as there is a match, evaluation of the following statements begins; it continues up to the first break statement encountered. 

##### SIDE PROGRAM # &nbsp;5

Write a Program that reads the grade as input and outputs the marks scored

    //
    //  Program Name - S2_SP_SwitchLoopTest.cpp
    //  Series: GetOnToC++ Step: 2 Side Program
    //
    //  Purpose: Write a Program that reads the grade as input and outputs the 
    //			 marks scored
    //
    //  Compile: g++ S2_SP_SwitchLoopTest.cpp -o S2_SP_SwitchLoopTest
    //  Execute: ./S2_SP_SwitchLoopTest
    //
    //  Created by Narayan Mahadevan on 10/11/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    using namespace std;

    int main ( ) { 

        // Read the grade from user input        
        char grade;
        cout << "Enter the Grade A, B, C, or D = ";
        cin >> grade;
        
        switch (grade) {
            case 'A' : case 'a' :
                cout << "Marks Scored is more then 90" << endl;
                break;
            case 'B' : case 'b' : 
                cout << "Marks Scored is more then 80" << endl;
                break;
            case 'C' : case 'c' :
                cout << "Marks Scored is more then 70" << endl;
                break;
            case 'D' : case 'd' :
                cout << "Marks Scored is more then 50" << endl;
                break;
            default :
                cout << "Got Failed Marks" << endl;
        }

        return 0;
    }

**RESULT:**

	$ ./S2_SP_SwitchLoopTest
	Enter the Grade A, B, C, or D = A
	Marks Scored is more then 90
	
<a name="logical_oper"/></a>
## Logical Operators
</br>

So far simple boolean expressions have been used. These expressions were expressed using relational operators >, <, >= and <=, and the equality operators == and !=. Each decision tested precisely one condition. To test multiple conditions while making a decision, nested if or if...else statements.

C++ provides logical operators that are used to form more complex conditions by combining simple conditions. The logical operators are 

1. Logical AND (&&) Operator 
2. Logical OR (||) Operator and 
3. Logical Negation (!) Operator

### Logical AND (&&) Operator

Logical AND (&&) Operator is used to ensure that the two conditions are both true. For e.g. Student Grade is A if Semister Mark and Final Mark are greater then 90

	￼if ( ( semesterMark >= 90 ) && ( finalMark >= 90 ) ) 
		cout << "Student grade is A" << endl;
		
### Logical OR (||) Operator

Logical OR (||) Operator is used to ensure atleast one of the two conditions are true. For e.g. Student Grade is A if atleast the Semister Mark or Final Mark is 90 or more

	￼if ( ( semesterMark >= 90 ) || ( finalMark >= 90 ) ) 
		cout << "Student grade is A" << endl;

### Logical Negation (!) Operator
C++ provides the ! (logical NOT, also called logical negation) operator to “reverse” a condition’s meaning. The unary logical negation operator has only a single condition as an operand.	
##### SIDE PROGRAM # &nbsp;6

Write a Program to test Logical Operators

    //
    //  Program Name - S2_SP_LogicalOperator.cpp
    //  Series: GetOnToC++ Step: 2 Side Program
    //
    //  Purpose: Write a Program to test Logical Operators
    //
    //  Compile: g++ S2_SP_LogicalOperator.cpp -o S2_SP_LogicalOperator
    //  Execute: ./S2_SP_LogicalOperator
    //
    //  Created by Narayan Mahadevan on 10/11/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    using namespace std;

    int main ( ) { 

        // Create truth table for && (logical AND) operator        cout << "Logical AND (&&)" 
             << "\nfalse && false: " << (false && false) 
             << "\nfalse && true: " << (false && true)              << "\ntrue && false: " << (true && false)              << "\ntrue && true: " << (true && true) << endl;
        // Create truth table for || (logical OR) operator
        cout << "Logical OR (||)" 
             << "\nfalse || false: " << (false || false)             << "\nfalse || true: " << (false || true)             << "\ntrue || false: " << (true || false)             << "\ntrue || true: " << (true || true) << endl;
        // create truth table for ! (logical negation) operator        cout << "Logical NOT (!)"             << "\n!false: " << (!false)              << "\n!true: " << (!true) << endl;

        return 0;
    }

**RESULT:**

	$ ./S2_SP_LogicalOperator
	Logical AND (&&)
	false && false: 0
	false && true: 0
	true && false: 0
	true && true: 1
	
	Logical OR (||)
	false || false: 0
	false || true: 1
	true || false: 1
	true || true: 1

	Logical NOT (!)
	!false: 1
	!true: 0

</br>  
<a name="prog_problem"/></a>
## Programming Problem
</br>  

Write a program that takes student marks as user inputs. Checks if it is pass, fail, A, B, C or D Grade and outputs number of students passed, failed and have got A, B, C and D grade.

    //
    //  Program Name - S2_MP_CourseGrade.cpp
    //  Series: GetOnToC++ Step: 1
    //
    //  Purpose: This program takes user input for course marks & total marks 
    //           and computes the number of students passed, failed and have 
    //           got A, B, C and D grade. 
    //
    //  Compile: g++ S2_MP_CourseGrade.cpp -o S2_MP_CourseGrade
    //  Execute: ./S2_MP_CourseGrade
    //
    //  Created by Narayan Mahadevan on 18/08/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #include <iostream>
    using namespace std;

    // Constants for A, B, C and D Grade
    const int  A_GRADE = 90, B_GRADE = 80, C_GRADE = 70, D_GRADE = 60;

    // Macros to calculate percentage
    #define PERC_MARK(mark, totalMark) (((double)mark/(double)totalMark)*100)


    main ( ) { 
        // Variables to capture Course Mark, Total Mark, Percentage and Grade
        int mark = 0, totalMark = 0;
        double percMark = 0.0;
        char grade;

        // Variabes to hold number of students with A, B, C, and D grade and also 
        // number of students passed and failed 
        int numAGrade = 0, numBGrade = 0, numCGrade = 0, numDGrade = 0;
        int numPassed = 0, numFailed = 0;

        // Reading from user input total mark
        cout << "Enter Total Marks: "; cin >> totalMark;

        // Processing Phase
        cout << "Enter Mark and -1 to end: "; cin >> mark;

        // While loop to take in multiple User Inputs
        while ( mark != -1 ) {

            // Calculating the percentage
            percMark = PERC_MARK(mark, totalMark);  
            cout << "Total Mark: " << totalMark 
                 << " Student Mark: " << mark
                 << " Perc Mark = " << percMark << endl;       

            // Two Way Conditional loop to determine A, B, C and D Grade
            if (percMark >= A_GRADE) grade = 'A';
            else if (percMark >= B_GRADE) grade = 'B';
            else if (percMark >= C_GRADE) grade = 'C';
            else if (percMark >= D_GRADE) grade = 'D';
            else grade = 'F'; 


            // Multiway Conditional loop to calc num of A, B, C and D Grade
            switch (grade) {
                case 'A' : case 'a' :
                    // Using Increment Operator to increment the number
                    numAGrade++; numPassed++;
                    break;
                case 'B' : case 'b' : 
                    numBGrade++; numPassed++;
                    break;
                case 'C' : case 'c' :
                    numCGrade++; numPassed++;
                    break;
                case 'D' : case 'd' :
                    numDGrade++; numPassed++;
                    break;
                default :
                    numFailed++;
            }

            // Entering Another Mark
            cout << "Enter Mark and -1 to end: "; cin >> mark;
        }

        // Print Results

        cout << "Number of Students: " << numPassed+numFailed
             << " Number Passed: " << numPassed 
             << " And Number Failed: " << numFailed << endl;

        cout << "Number of AGrade Students: " << numAGrade 
             << "\nNumber of BGrade Students: " << numBGrade 
             << "\nNumber of CGrade Students: " << numCGrade
             << "\nAnd Number of DGrade Students: " << numDGrade << endl;

    }

**RESULT:**

	$ ./S2_MP_CourseGrade
	Enter Total Marks: 150
	Enter Mark and -1 to end: 95
	Total Mark: 150 Student Mark: 95 Perc Mark = 63.3333
	Enter Mark and -1 to end: 125
	Total Mark: 150 Student Mark: 125 Perc Mark = 83.3333
	Enter Mark and -1 to end: 139
	Total Mark: 150 Student Mark: 139 Perc Mark = 92.6667
	Enter Mark and -1 to end: 135
	Total Mark: 150 Student Mark: 135 Perc Mark = 90
	Enter Mark and -1 to end: -1
	Number of Students: 4 Number Passed: 4 And Number Failed: 0
	Number of AGrade Students: 2
	Number of BGrade Students: 1
	Number of CGrade Students: 0
	And Number of DGrade Students: 1
