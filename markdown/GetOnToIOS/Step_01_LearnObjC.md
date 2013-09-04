# Step 1: Learn Objective C

<a name="intro"/></a>
## Introduction
#  
Objective-C is the primary programming language for writing software in OS X and iOS. It’s a superset of the C programming language and provides object-oriented capabilities and a dynamic runtime. Objective-C inherits the syntax, primitive types, and flow control statements of C and adds syntax for defining classes and methods. Its assumed that you have basic understanding of C and Object Oriented Programming. 

Objective-C is the first step before programming in iOS. This step will help you understand all you have to know about Objective-C by implementing a [**Simple Project**](#simple_project) as defined below. The Concepts introduced in this step are:

1. [**Create Objective-C Project**](#create_project)
2. [**Definition of new classes**](#create_class)  
3. [**Declaration of Properties**](#declare_props)
4. [**Defining Class and instance methods**](#create_methods)
5. [**Class Implementation**](#class_implementation)
6. [**Object Creation and Method invocation**](#call_methods)
7. [**Static and dynamic typing**](#typing_var)
8. [**Memory Management**](#manage_memory)
9. [**Blocks**](#set_blocks) — encapsulated segments of code that can be executed at any time
10. [**Working with protocols and categories**](#explain_protocols)

<a name="simple_project"/></a>
## Simple Project
#  
This is a simple project, the goal being end of this step you are comfortable with basics of Objective-C Programming. In this step, you will learn to create new Project, Define a new Class, specify class attributes and properties, define class and instance methods, etc as listed in item 2 - 10. Every section would introduce a new concept with the sample code. All the sample codes when copied one-by-one into your xcode environment will finally build up into an executable project.

The project is about Dog Class which is essentially an Animal. We will describe the Dog's attributes by its Color, Breed, Name, etc as well as Dogs behaviour by Barking, Wagging, Eating, etc. The execuatble project will let you create a Dog with its name, breed and color and check-out its behaviour. 

<a name="create_class"/></a>
## Create Objective-C Project
#  
Please refer the following figure for steps to create a new Command Line Project. 

* **Step 1:** Create a new Xcode project, located directly below the Welcome to Xcode title or you can create a new project by going to the File menu and selecting New > Project….
* **Step 2:** In the column on the left hand side, find the OS X section, click on Application and select Command Line Tool as shown in the figure above.
* **Step 3:** On clicking Next, fill in the fields as indicated in the screen: 
  * Product Name: My Dog Project
  * Organization Name: This field can be left blank. Here we have entered MakeTechEz
  * Company Identifier: Enter com.maketechez
  * Type: Foundation. This indicates Foundation Framework
  * Use Automatic Reference Counting: Check this box
* **Step 4:** Click Next to choose a location to store the project files
* **Step 5:** Click Create and Xcode will set up your new project and open it up in the editor.
 

<a name="create_class"/></a>
## Definition of new classes
#  
As in most Object Oriented Languages, Objective-C supports creating your own Data Type by creating a **Class Interface** and ecapsulation of data by creating **Properties** and defining the actions that operate on that data by creating **Methods**. Creating Objects as run-time instance of class having its own in-memory copy of the instance variables declared by its class and pointers to the methods of the class.

A Class in Objective-C consists of 

* **Header file** - The header file is essentially a class definition with properties which are attributes of the class and methods that describe the behavior.
* **Implementation file** - The Implementation file is the source file containing the programmong logic by implementing the methods defined in the Header file.

The table below indicates the file name extensions for Header Files and Implementation Files

Extension | Source Type 
:----     | :----------  
.h        | Header files. Header files contain class, type, function, and constant declarations.        
.m        | Implementation files. A file with this extension can contain both Objective-C and C code. It is sometimes called a source file.
.mm       | Implementation files. An implementation file with this extension can contain C++ code in addition to Objective-C and C code. Use this extension only if you actually refer to C++ classes or features from your Objective-C code.       


**Example** - This Step will help you build a simple Objective-C Project. will show sample code to define a header file and implementation file of Dog Class which is essentially an Animal. We can describe the Dog's attributes by its Color, Breed, Name, etc as well as Dogs behaviour by Barking, Wagging, Eating, etc. 

#####Comments

The following code sample shows the Comments in Objective-C

	//
	//  Dog.h
	//  LearnObjective-C
	//
	//  Created by MakeTechEz on 18/08/13.
	//  Copyright (c) 2013 MakeTechEz. All rights reserved.
	//

#####Import Foundation Framework

The following code sample uses **#import** directive. This is similar to C’s #include directive, except that it makes sure that the same file is never included more than once. 

Here Foundation Framework is imported. Generally framework is imported to import most or all of the header files contained within the framework. This is done by  importing the framework’s umbrella header file, which has the same name as the framework.

The Foundation framework provides many primitive object classes and data types, making it fundamental to any Objective-C development. It defines classes to manage Strings (NSString), manage numbers NSNumber, manage Collections NSArray and NSDictionary, etc. The core classes of Foundation framework is covered in step 2.

	#import <Foundation/Foundation.h>

#####Class Declaration

The class declaration begins with the **@interface** compiler directive and ends with the **@end** directive. The instance variables, properties, and methods appear between these two statements. The class interface is usually stored in the .h file. The following diagram typically shows class declaration  

#  
![Class Definition](https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToIOS/ObjC_ClassDef.png) 
#  

The following sample shows class declaration. The class interface defined is Dog and hence the header file name is Dog.h and the implemntation file is Dog.m. Following the class name (and separated from it by a colon) is the name of the parent class NSObject. In Objective-C, a class can have only one parent.

	@interface Dog : NSObject
	{
		// Section 1: Instance Variables declared here
	}
	// Section 2: Accessor Methods i.e. getter and setter methods are declared here
	// Section 3: Properties are declared here
	// Section 4: Class Methods and Instance Methods declared here
	@end


you can see in the sample code above, Dog class has 4 sections. Each of the Sections are discussed with code samples.

* Section 1: [**Instance Variables**](@create_variables) 
* Section 2: [**Accessor Methods**](#accessor_methods)
* Section 3: [**Properties**](#declare_props)
* Section 4: [**Class and Instance Methods**](#create_methods)

***
**Note:** Instance Variables and Methods can be called using an Object which is a run-time instance of class having its own in-memory copy. While Class Variables and Methods can be called directly using the Class.
***

 
<a name="create_variables"/></a>
####Instance Variables

Instance Variables are defined within the curly brackets immediately after the class declaration as shown in the sample below. This are essentially read-only variables and setter and getter methods (accessor methods) have to be manually defined to access these variables. [Properties](#declare_props) as discussed later are far superior to Instance Variable. Use Properties instead of Instance Variables.

    // Section 1: Instance Variables declared here.
    NSString* name; // Name of the Dog
    NSString* breed; // Breed of the Dog
    NSString* color; // Color of the Dog


<a name="accessor_methods"/></a>
####Accessor Methods

This section shows how to add getter and setter accessor methods to get and set values to the Instance Vairables. 

***
**Note:** If [**Properties**](#declare_props) were used instead of Instance Variables, [**@synthesize**](#synthesize) feature of Objective-C can be used to auto-generate accessor methods.  
***

The getter and setter methods are instance method and indicated by single dash (-) before the method name. Class methods can be called without creating an instance and is indicated by plus (+) sign before the method name.  

The following code sample shows the accessor methods for the instance variables. The getter methods are specified with the same name as the instance variable, while the setter methods are specified by adding "set" word in front of the vairable as shown below

	// Section 2: Accessor Methods i.e. getter and setter methods are declared here

	// getter methods
	- (NSString*) name;
	- (NSString*) breed;
	- (NSString*) volor;

	// setter methods
	- (void) setName: (NSString*) name;
	- (void) setBreed: (NSString*) breed;
	- (void) setColor: (NSString*) color;

***
**Note: ** The way setter method is defined is exactly the same way the methods are defined in Objective-C. See more in [**Class and Instance Methods**](#create_methods)
***

<a name="declare_props"/></a>
## Declaration of Properties
#  

A property in the general sense is some data encapsulated or stored by an object. It is either an attribute—such as a name or a color or a relationship to one or more other objects.  

Properties in Objective-C provide a well-defined interface for other classes to manipulate attributes of a class. It is extension of Instance Variable described above. As such it is better to use Properties then Instance Variable. 

The code below declares property of the Instance Variable describe above plus adds age property for the Dog.

	// Section 3: Properties are declared here
	// This properties are defined for instance veriable mName, mBreed and mColor
	// Note here the properties are defined with attributes nonatomic and strong
	@property (nonatomic, strong) NSString* name;
	@property (nonatomic, strong) NSString* breed;
	@property (nonatomic, strong) NSString* color;
	
	// This is the new property defining age of the dog 
	@property (nonatomic, strong) NSNumber* age;

Property essentially is a feature in Objective-C that allow automatic generation of  accessors through the use of [synthesize](#synthesize) directive. The properties are defined with attributes comma seperated as shown in the declaration below:
***
@property (attributes) property Name;
***
**Attributes** fall into following categories:

- **Writability**
  - **readwrite** (Default Setting) - the property may be written and read. 
  - **readonly** - the property only may be read. 
- **Memory Settings**
  - **strong** (Default Setting) - Same as **retain** used in iOS 4.0. The memory cannont be released till the reference is nullified.
  - **weak** - Does not protect the object from Garbage Collection. As soon as the stron reference to the object is released the weak refrence is automatically released.
  - **assign** - the incoming value will be assigned to the property. Use this for plain datatypes (e.g. int, double).
  - **retain** - the incoming value will be retained. If the value is an Objective-C object this is the most common.
  - **copy** - the incoming value will be copied. This is used if there is a chance that the incoming object may change (e.g. NSMutableString).
- **Atomocity**
  - **atomic** (Default Setting) - Only one thread executes at a time on the property
  - **nonatomic** - Multiple thread can access and set the property. Is not thread sefe but gives better performance

<a name="create_methods"/></a>
## Defining Class and instance methods
#  


<a name="class_implementation"/></a>
## Class Implementation
#  


<a name="synthesize"/></a>
#### @synthesize Directive
#  

@synthesize Directive is used for Property for the compiler to automatically generate the most common forms of getters and setter. This is done in the implementation file as show in the sample below

	//
	//  Dog.m
	//  LearnObjective-C
	//
	//  Created by Narayan Mahadevan on 18/08/13.
	//  Copyright (c) 2013 MakeTechEz. All rights reserved.
	//

	#import "Dog.h"

	@implementation Dog
	
	// Use synthesize dirivative to auto-generate setter and getters methods for  
	// the property.
	// Here the property name, breed, color, and age is referred by instance name
	// mName, mBreed, mColor and mAge.
	@synthesize name = mName;
	@synthesize breed = mBreed;
	@synthesize color = mColor;
	@synthesize age = mAge;

The general form of the synthesize directive is:

@synthesize property_name;

OR

@synthesize property_name = instance_name;

Here instance_name is optional. It helps to refer the instance variable by instance name. So dogs instance veriable can be accessed as self.name or mName in the implementation file. Our recomendation is to have an instance name as mName, mBreed, etc for readability of code so there is clear seperation between local veriable and class veriable. 

<a name="call_methods"/></a>
## Object Creation and Method invocation
#  

<a name="typing_var"/></a>
## Static and dynamic typing
#  

<a name="manage_memory"/></a>
## Memory Management
#  

<a name="set_blocks"/></a>
## Blocks
#  

<a name="explain_protocols"/></a>
## Working with protocols and categories
#  

