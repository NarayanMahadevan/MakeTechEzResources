# Step 1: Learn Objective C

<a name="intro"/></a>
# Introduction

Objective-C is the primary programming language for writing software in OS X and iOS. It’s a superset of the C programming language and provides object-oriented capabilities and a dynamic runtime. Objective-C inherits the syntax, primitive types, and flow control statements of C and adds syntax for defining classes and methods. Its assumed that you have basic understanding of C and Object Oriented Programming. Objective-C, unlike C++, doesn’t allow operator overloading, templates, or multiple inheritance. 

Objective-C is the first step before programming in iOS. This step will help you understand all you have to know about Objective-C by implementing a [**Simple Project**](#step_project) as defined below. The Concepts introduced in this step are:

1. [**Create Objective-C Project**](#create_project)
2. [**Definition of new classes**](#create_class)  
3. [**Declaration of Properties**](#declare_props)
4. [**Defining Class and instance methods**](#create_methods)
5. [**Class Implementation**](#class_implementation)
6. [**Object Creation and Method invocation**](#call_methods)

Finally the end of the Section 

a. [**Displays the result**](#result) of the [**Simple MyDog Project**](#step_project) defined below and
b. Gives [**Practice Projects**](#practice) for Development

<a name="step_project"/></a>
# Simple MyDog Project

This is a simple project, the goal being end of this step you are comfortable with basics of Objective-C Programming. In this step, you will learn to create new Project, Define a new Class, specify class attributes and properties, define class and instance methods, etc as listed in [Introduction](#intro). 

***
**NOTE:** *Every section would introduce a new concept with the code for the sample project under the heading **Main Program**. All the codes when copied one-by-one into your xcode environment will finally build up into an executable project.*
***

The project is about Dog Class which is essentially an Animal. We will describe the Dog's attributes by its Color, Breed, Name, etc as well as Dogs behaviour such as temperament, aggression, intelligence etc. The execuatble project will let you create a Dog with its name, breed and color and check-out its behaviour. 

<a name="create_project"/></a>
# Create Objective-C Project
  
Please refer the following figure for steps to create a new Command Line Project for the MyDog Project . 
  
![Class Definition](/Users/narayan/Documents/MakeTechEzResources/images/GetOnToIOS/ObjCCreateProject.jpg) 
<!--
![Class Definition](https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToIOS/ObjCCreateProject.jpg "Class Definition") 
-->
#  

* **Step 1:** Create a new Xcode project, located directly below the Welcome to Xcode title or you can create a new project by going to the File menu and selecting New > Project….
* **Step 2:** In the column on the left hand side, find the OS X section, click on Application and select Command Line Tool as shown in the figure above.
* **Step 3:** On clicking Next, fill in the fields as indicated in the screen: 
  * Product Name: My Dog Project
  * Organization Name: This field can be left blank. Here we have entered MakeTechEz
  * Company Identifier: Enter com.maketechez
  * Type: Foundation. This indicates Foundation Framework
  * Use Automatic Reference Counting: Check this box
* **Step 4:** Click Next to choose a location to store the project files and Click Create
* **Step 5:** On Create, Xcode will set up your new project and open it up in the editor as shown in the Figure below. 
<a name="main_source_file"/></a>
#  
![New XCode Project](/Users/narayan/Documents/MakeTechEzResources/images/GetOnToIOS/NewProjectCreated.png "New XCode Project") 
<!--
![New XCode Project](https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToIOS/NewProjectCreated.png "New XCode Project") 
-->
#  
 
As you can see the figure, the left pane of Xcode displays a list of files that are part of the project. The files you see were automatically created by the project template you used. For detail explanation please see [**Class Implementation**](#class_implementation)

***
**Note: ** *You should be able to Compile and Run the My Dog project without writing single line of code and see the Hello World output. This log statement is in main.m Source code which is the starting point for any execution.*
#  
![Run and View Output](/Users/narayan/Documents/MakeTechEzResources/images/GetOnToIOS/RunAndViewOutput.jpg "Run and View Output") 
<!--
![Run and View Output](https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToIOS/RunAndViewOutput.jpg "Run and View Output") 
-->
#  
***

<a name="create_class"/></a>
# Definition of new classes
  
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

The Following Figure shows process to create Objective-C file for Dog. This in turn will create Dog.h Header file and Dog.m Implementation File
#  
![Dog Source File](/Users/narayan/Documents/MakeTechEzResources/images/GetOnToIOS/DogFile.jpg "Source File") 
<!--
![Dog Source File](https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToIOS/RunAndViewOutput.jpg "Source File") 
-->
#  

####Comments

The following code will be auto-generated on the top of Dog.h File. This are comments in  Objective-C to give information of Dog file

	//
	//  Dog.h
	//  LearnObjective-C
	//
	//  Created by MakeTechEz on 18/08/13.
	//  Copyright (c) 2013 MakeTechEz. All rights reserved.
	//

####Import Foundation Framework

The following code sample uses **#import** directive. This is similar to C’s #include directive, except that it makes sure that the same file is never included more than once. 

Here Foundation Framework is imported. Generally framework is imported to import most or all of the header files contained within the framework. This is done by  importing the framework’s umbrella header file, which has the same name as the framework.

The Foundation framework provides many primitive object classes and data types, making it fundamental to any Objective-C development. It defines classes to manage Strings (NSString), manage numbers NSNumber, manage Collections NSArray and NSDictionary, etc. The core classes of Foundation framework is covered in step 2. 

The following code is auto generated in Dgg.h file to import the Foundation Framework.

	#import <Foundation/Foundation.h>

####Class Declaration

The class declaration begins with the **@interface** compiler directive and ends with the **@end** directive. The instance variables, properties, and methods appear between these two statements. The class interface is usually stored in the .h file. The following diagram typically shows class declaration  

#  
![Class Definition](/Users/narayan/Documents/MakeTechEzResources/images/GetOnToIOS/ObjC_ClassDef.png "Class Definition") 
<!--
![Class Definition](https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToIOS/ObjC_ClassDef.png "Class Definition") 
-->
#  

<a name="header_code"/></a>
**Main Program - Class Declaration**

The following code shows class declaration of Dog.h header file. The class interface defined is Dog and hence the header file name is Dog.h and the implemntation file is Dog.m. Following the class name (and separated from it by a colon) is the name of the parent class NSObject. In Objective-C, a class can have only one parent. Please copy the following code into Dog.h file. Please insert code from different sections to build MyDog Project.

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

**Main Program - Instance Variable Declaration**

Please copy the code below and paste it into Section 1 of Dog.h file as shown in the [Class Declaration](#header_code).

    // Section 1: Instance Variables declared here.
    NSString* name; // Name of the Dog
    NSString* breed; // Breed of the Dog


<a name="accessor_methods"/></a>
####Accessor Methods

This section shows how to add getter and setter accessor methods to get and set values to the Instance Vairables. 

***
**Note:** If [**Properties**](#declare_props) were used instead of Instance Variables, [**@synthesize**](#synthesize) feature of Objective-C can be used to auto-generate accessor methods.  
***

The getter and setter methods are instance method and indicated by single dash (-) before the method name. Class methods can be called without creating an instance and is indicated by plus (+) sign before the method name.  

**Main Program - Accessor Methods**

The following code shows the accessor methods for the instance variables. The getter methods are specified with the same name as the instance variable, while the setter methods are specified by adding "set" word in front of the vairable as shown below. Please copy the code below and paste it into Section 2 of Dog.h file as shown in the [Class Declaration](#header_code).

	// Section 2: Accessor Methods i.e. getter and setter methods are declared here

	// getter methods
	- (NSString*) name;
	- (NSString*) breed;

	// setter methods
	- (void) setName: (NSString*) name;
	- (void) setBreed: (NSString*) breed;

***
**Note: ** The way setter method is defined is exactly the same way the methods are defined in Objective-C. See more in [**Class and Instance Methods**](#create_methods)
***

<a name="declare_props"/></a>
# Declaration of Properties  

A property in the general sense is some data encapsulated or stored by an object. It is either an attribute—such as a name or a color or a relationship to one or more other objects.  

Properties in Objective-C provide a well-defined interface for other classes to manipulate attributes of a class. It is extension of Instance Variable described above. As such it is better to use Properties then Instance Variable. 

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

**Main Program - Declaration of Properties**

The code below declares property of the Instance Variable describe above plus adds color, age, and isPoliceDog property for the Dog. Please copy the code below and paste it into Section 3 of Dog.h file as shown in the [Class Declaration](#header_code).

	// Section 3: Properties are declared here
	// This properties are defined for instance veriable mName, mBreed and mColor
	// Note here the properties are defined with attributes nonatomic and strong
	@property (nonatomic, strong) NSString* name;
	@property (nonatomic, strong) NSString* breed;
	@property (nonatomic, strong) NSString* color;
	
	// This is the new property defining age of the dog 
	@property (nonatomic, strong) NSNumber* age;

	// This property defines if the dog is a Police Dog and defines a new 
	// setter method 
	@property (nonatomic, assign, setter=isPoliceDog:) BOOL isPoliceDog;

***
Note: The setter method is defined for the Property isPoliceDog. Also assign attribute is used as it is basic data type
***

<a name="create_methods"/></a>
# Defining Class and instance methods  

Methods are basically behaviours or actions defined in the class. So taking the example of Dog, the behaviours are temperament, aggression, intelligence etc. Methods use the properties to describe the behaviour or to compute results or to take actions. 

Methods are also used where-in large network of objects can interact with each other by sending messages. In Objective-C terms, one object sends a message to another object by calling a method on that object. 

There are two kinds of methods in Objective-C: instance methods and class methods.

1. **Instance Method** - An instance method is a method whose execution is scoped to a particular instance of the class. In other words, before you call an instance method, you must first create an instance or an object of the class. 

2. **Class Method** - A class method is a method whose execution is scoped to the method’s class. Class method gets called on the Class itself and does not require an instance of a class to be created by the programmer.

Here’s the declaration of a method in ObjC.

#  
![Class Definition](/Users/narayan/Documents/MakeTechEzResources/images/GetOnToIOS/method_decl_objc.png "Class Definition") 
<!--
![Class Definition](https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToIOS/ObjC_ClassDef.png "Class Definition") 
-->
#  

The declaration of a method consists of  

1. **Method Type Identifier ( - or + )** to indicate Instance or Class Method 
2. **Return type** enclosed within paranthesis to indicate the data type object of the return value. In case of no return it is (void). 
3. One or more **Signature Keywords** to indicate method name
4. Each method name or signature keyword is specified by colon (:) followed by
   a. **Parameter Type** enclosed within paranthesis to indicate the data type and
   b. **Parameter Name** i.e. the name of the parameter 

<a name="method_code"/></a>
**Main Program - Class and instance methods**

The following code adds the class and instance methods for Dog class. Please copy the code below and paste it into Section 4 of Dog.h file as shown in the [Class Declaration](#header_code).

	// Section 4: Class Methods and Instance Methods declared here

    // Class Method to initialize Dog Object
    +(id)alocAndInitName:(NSString*)aName Breed:(NSString*)aBreed 
                   Color:(NSString*)aColor AndAge:(NSNumber*)aAge;

    // Instance Methods to Set Dog Object Properties
    -(id)initName:(NSString*)aName Breed:(NSString*)aBreed 
            Color:(NSString*)aColor AndAge:(NSNumber*)aAge;

    // Instance Methods to describe Dogs Behaviour such as temperament, 
    // aggression, intelligence etc
    
    -(void) temperament;

    -(void) aggression;

    -(void) intelligence;

***
**Note Num 1:** The name of the following method is **initName:Breed:Color:AndAge:**

	-(id)initName:(NSString*)aName Breed:(NSString*)aBreed 
            Color:(NSString*)aColor AndAge:(NSNumber*)aAge;
            
**Note Num 2:** The Instance Method returns id Object. This is Dynamic Typing as in Objective-C uses pointers to keep track of Objects in Memory, so it doesn’t matter what specific class type you use for that pointer. Hence Objective-C defines **id type** for a generic object pointer. Refer [**Static and dynamic typing**](#typing_var) for more details.
***

<a name="class_implementation"/></a>
# Class Implementation  

The Class Implementation begins with importing the corresponding header file. Then begins with the **@implementation** compiler directive and ends with the **@end** directive, just like the interface. All methods must appear between these two statements. 

The following code is auto generated in Dog.m implementation file when Dog Objective-C file is created. 

	//
	//  Dog.m
	//  LearnObjective-C
	//
	//  Created by Narayan Mahadevan on 18/08/13.
	//  Copyright (c) 2013 MakeTechEz. All rights reserved.
	//

	#import "Dog.h"
	
<a name="impl_code"/></a>
**Main Program - Class Implementation Code**

To the auto-generated code add following sections to synthesize properties, implement [class and instance methods](#method_code) declared in the header file, etc. 	

    // Optional Section A1: Implementation Variable - Local to the 
    // implementation file is defined here
	
	@implementation Dog {
    	// Optional Section A2: Implementation Variable - Instance Variable 
    	// available only to this implementation file is defined here
	}
	
	// Section B: @synthesize directive
	// Section C: Accessor Methods are implemented here
	// Section D: Class Method to Initialize (init) is implemented here
	// Section E: Instance Method to Initialize (init) is implemented here
	// Section F: Instance Method to describe Dogs Behaviour is implemented here

	@end

As you can see in the implementation code above, Dog implementation class has 5 sections. Each of the Sections are discussed with code samples.

* Section A: [**Implementation Variable**](#impl_var)
* Section B: [**@synthesize directive**](@synthesize) 
* Section C: [**Accessor Methods Implementation**](#accessor_methods_impl)
* Section D: [**Class Init Method Implementation**](#class_method_impl)
* Section E: [**Instance Init Method Implementation**](#init_method_impl)
* Section F: [**Instance Method Implementation**](#instance__method_impl)

<a name="impl_var"/></a>
### Section A :- Implementation Variable
  
Implementation Variable can be a local variable or instance variable. In both the cases the variable scope is local to the implementation file. Both are optional. 

**Main Program - Instance Variable in Implementation**

As seen in the code below, NSDictionary Objects (Discussed more in Next Step Number 2) for Dogs Behaviour is defined. NSDictionary Objects essentially maintains a key value pair and is part of Foundation Framework. Please copy the code below and paste it into Section A1 and A2 of Dog.m file as shown in the [Class Implementation](#impl_code).


	// Optional Section A1: Implementation Variable - Local to the implementation
	// file is defined here

	// The vairables are declared static only one instance object needs
	// to be created across all Dog Objects
    static NSDictionary *_DogTemperament;
    static NSDictionary *_DogAggression;
    static NSDictionary *_DogIntelligence;
    static Bool _IsStaticVarInit = false;

    // Optional Section A2: Implementation Variable - Instance Variable available 
    // only to this implementation file is defined here
    
    // This variable maintains Dog Objects temperament, aggression and intelligence
    NSString *mTemperament;
    NSString *mAggression;
    NSString *mIntelligence;
    
***
**Note:** The static keyword in the above code indicates that these Objects like _DogTemperament, _DogAggression, etc are initialized only ones and is used by all Dog Objects.
***

<a name="synthesize"/></a>
### Section B :- @synthesize Directive  

@synthesize Directive is used for Property for the compiler to automatically generate the most common forms of getters and setter. 

The general form of the synthesize directive is:

@synthesize property_name;

OR

@synthesize property_name = instance_name;

Here instance_name is optional. It helps to refer the instance variable by instance name. So dogs instance veriable can be accessed as self.name or mName in the implementation file. Our recomendation is to have property name begining with smaller case like name, breed, etc and instance name as mName, mBreed, etc for readability of code so there is clear seperation between local veriables and class variables. 

**Main Program - @synthesize Directive**

Please copy the code below and paste it into Section A of Dog.m file as shown in the [Class Implementation](#impl_code).

The following code shows @synthesize Directive for the properties define in Dog Header file. Please copy the code below and paste it into Section B of Dog.m file as shown in the [Class Implementation](#impl_code).

	// Section B: @synthesize directive
	
	// Use synthesize dirivative to auto-generate setter and getters methods for  
	// the property.
	// Here the property name, breed, color, age is referred by instance name
	// mName, mBreed, mColor, mAge, etc.
	
	@synthesize name = mName;
	@synthesize breed = mBreed;
	@synthesize color = mColor;
	@synthesize age = mAge;
	@synthesize isPoliceDog = mIsPoliceDog;

<a name="accessor_methods_impl"/></a>
### Section C :- Accessor Methods Implementation
  
The accessor methods i.e. the setter and getter methods are defined in the header file and implemented in .m file as shown below. 

**Main Program**

The code below shows the implementation of [Setter and Getter Methods](#accessor_methods) described in Dog.h file. Please copy the code below and paste it into Section C of Dog.m file as shown in the [Class Implementation](#impl_code).


    // Section C: Accessor Methods are implemented here

    // getter methods
    - (NSString*) name {
        return mName;
    }

    - (NSString*) breed {
        return mBreed;
    }

    // setter methods
    - (void) setName: (NSString*) aName {
        mName = aName;
    }

    - (void) setBreed: (NSString*) aBreed {
        mBreed = aBreed;
    }

***
**Note Num 1: ** Since the @synthesize directive is used, the accessor methods definition and implementation is not needed. Here it is just shown for completeness.

**Note Num 2: ** If there is no Garbage Collection Environment then the following code becomes relevant as the old memory has to be released before new assignment. For e.g. setName setter method will be written as

    - (void) setName: (NSString*) aName {
    	// Since no Auto Garbage Collection is used hence need to release the 
    	// old object, and retain the new one. 
    	[mName autorelease];
        mName = [aName retain];
    }

In Manual Reference Counting Environment, firstly the reference to the existing object has to be released, and then the new input object has to be retained. In a Manual Reference Counting Environment(ARC), we could just set the new value directly as shown in the setter method. **Memory Management** is covered in next step.
***

<a name="class_method_impl"/></a>
### Section D :- Class Init Method Implementation
  
The class init methods typically allocate memory and set the values for the property. 
 
**Main Program**

The code below shows the implementation of class method to allocate new memory for Dog Object and initialize with the input parameters. Please copy the code below and paste it into Section D of Dog.m file as shown in the [Class Implementation](#impl_code).

    // Section D: Class Method to Initialize (init) is implemented here

    +(id)alocAndInitName:(NSString*)aName Breed:(NSString*)aBreed 
    			   Color:(NSString*)aColor AndAge:(NSNumber*)aAge
    {
        Dog* myDog = [[Dog alloc] init];
        // Calls the Instance Method to initialize the Class Properties
        return [myDog initName:aName Breed:aBreed Color:aColor AndAge:aAge];
    }
    
    // This C method is local to the implementation file and its purpose is to
    // allocate memory and initialize the static variables
    void initStaticVars() {
        
        // Checks if the static variables are already initialized. If not then 
        // the memory is allocated and initialized.
        if (_IsStaticVarInit) return;
        
        // Set the values for the local static variable
        _DogTemperament = [[NSDictionary alloc] initWithObjectsAndKeys:
                           @"Fearless, and willing to defend",
                           @"Doberman",
                           @"Active and willingness to learn",
                           @"German Shepherd",
                           nil];
        
        _DogAggression = [[NSDictionary alloc] initWithObjectsAndKeys:
                          @"Extremely high on stranger-directed aggression",
                          @"Doberman",
                          @"Being very safe",
                          @"German Shepherd",
                          nil];
        
        _DogIntelligence = [[NSDictionary alloc] initWithObjectsAndKeys:
                            @"Ranked 5th most intelligent dog",
                            @"Doberman",
                            @"Ranked 3rd most intelligent dog",
                            @"German Shepherd",
                            nil];
        _IsStaticVarInit = true;
        
    }
    

***
**Note:** The code above instantiates the Object and calls the Instance Methods. More Explanation is provided in [**Object Creation and Method invocation**](#call_methods)
***

<a name="init_method_impl"/></a>
### Section E :- Instance Init Method Implementation  

The init methods typically used to set the values for the property. The default init method is declared in NSObject class and will be called by default during allocation.

**Main Program**

The code below shows the implementation of instance method to initialize the properties with the input parameters. The init method is over-written to initialize the static variable defined in the implementation file. Please copy the code below and paste it into Section E of Dog.m file as shown in the [Class Implementation](#impl_code).

    // Section E: Instance Method to Initialize (init) is implemented here

    // This method is over written from the super class.
    // Since all the properties are using @synthesize directive, this 
    // init method is called during memory allocation

    -(id)init {
        self = [super init];
    	// By default all dogs are not Police Dog
 	   	mIsPoliceDog = false;
    	if (self) {
            // Initializes and Sets the values for the local instance variable
        	initStaticVars();
        }
        return self;
    }


    -(id)initName:(NSString*)aName Breed:(NSString*)aBreed 
            Color:(NSString*)aColor AndAge:(NSNumber*)aAge
    {
    	initStaticVars();
        mName = aName;
        mBreed = aBreed;
        mColor = aColor;
        mAge = aAge;
        return self;
    }

<a name="instance__method_impl"/></a>
### Section F :- Instance Method Implementation
  
The Behaviour of the class is implemented as instance method. The Behaviors are defined in the .h file and are implemented in the .m file

**Main Program**

The code below shows the implementation of instance methods to implement Dogs Behaviour such as temperament, aggression, intelligence etc. Note that pre-defined Dictionary Object to specify the Dogs Behaviour. Please copy the code below and paste it into Section F of Dog.m file as shown in the [Class Implementation](#impl_code).


    // Section F: Instance Method to describe Dogs Behaviour is implemented here

    -(void) temperament {
    	if (mTemperament == NULL)
        	mTemperament = [_DogTemperament objectForKey:mBreed];
	    NSLog(@"Temperament of my %@ the %@ Dog is %@", mName, mBreed,
	     	  mTemperament);
    }

    -(void) aggression {
    	if (mAggression == NULL)
        	mAggression = [_DogAggression objectForKey:mBreed];
	    NSLog(@"Aggression of my %@ the %@ Dog is %@", mName, mBreed,
          	  mAggression);
    }

    -(void) intelligence {
    	if (mIntelligence == NULL)
        	mIntelligence = [_DogIntelligence objectForKey:mBreed];
	    NSLog(@"Intelligence of my %@ the %@ Dog is %@", mName, mBreed,
              mIntelligence);
    }

	// This method is over-written from NSObject and Returns a string that
	// represents the contents of the receiving class.
	- (NSString *)description {
    	return [NSString stringWithFormat:
                @"My Dogs name is %@, Breed is %@, and Color is %@",
	            mName, mBreed, mColor];
	}
	
***
**Note:** Logging messages to the console in Objective-C is very simple. Use NSLog() function to Log. For Logging Objects use %@ token as shown above in the instance methods as well as below to show the current date. The Constant String in Objective-C is defined as @"string". More in Step 2. 

	NSLog ( @"The current date and time is: %@", [NSDate date] );
***

<a name="call_methods"/></a>
# Object Creation and Method invocation 
 
Object Creation of Dog Class and Invocation of its method will be done in this MyDog project in the main.m file. As with plain old C programs, the main() function serves as the root of an Objective-C application. Most of the built-in Xcode templates create a file called main.m that defines a default main() function. 

<a name="main_code"/></a>
**Main Program: main.m file**

To this we add sections to create Dog Object and Invoke Methods. Please copy the following code to main.m file

    //
    //  main.m
    //  MyDog
    //
    //  Created by Narayan Mahadevan on 06/09/13.
    //  Copyright (c) 2013 MakeTechEz. All rights reserved.
    //

    #import <Foundation/Foundation.h>

    // Section A: Import file.

    // This line declares a function called main. All of the code in your
    // app that provides some type of processing or logic is encapsulated
    // into functions; the main function is what kicks off the whole app.

    // The int part of int main means the return value of main returns an
    // integer such as 10 or -2. The (int argc, const char * argv[]) bits
    // in parentheses are the arguments, or inputs, to the function.
    int main(int argc, const char * argv[])
    {

        // Autorelease pools are used to manage memory. Automatic Memory
        // Management is done for all the objects in between the curly braces
        @autoreleasepool {
            
            // Section B: Object Creation
            
            // Section C: Method Invocation or Messaging 
            
            // Section D: Set Properties 
            
            // Section E: Invoke Behaviour
            
        }
        return 0;
    }
***
**Note Num 1:** As discussed earlier code execution begins in main function. It takes in argc and argv input parameters and returns the result. Here it is defaulted to 0.

**Note Num 2:** **@autoreleasepool** is a tool that automates the task of releasing memory. The other tool is Automatic Reference Counting (ARC). More in [**Memory Management**](#manage_memory) Section.

**Note Num 3:** As you can see the code above, the following auto generated code is replaced

	// insert code here...
    NSLog(@"Hello, World!");

***

As you can see the code above consists of 3 sections. They are:

1. Section A: [**Import file**](#import_file)
2. Section B: [**Object Creation**](#object_creation)
3. Section C: [**Method Invocation or Messaging**](#method_invocation)
4. Section D: [**Set Properties**](#set_props)
5. Section E: [**Invoke Behaviour**](#invoke_behaviour)

<a name="import_file"/></a>
### Section A: Import Files  

**Main Program**

Here files created for My Dog Project is imported. Please copy the code below and paste it into Section A of main.m file as shown in the [Main Code](#main_code). 

    // Section A: Import file pertaining to MyDog Project.
    // This tells the compiler where to look when Dog Object is create and
    // methods are invoked

    #import "Dog.h"

<a name="import_file"/></a>
### Section B: Object Creation
  
Objects inherited from NSObject must be prepared for use in 2 steps:

1. **Allocation**: Unlike C++ where Objects can be accessed without pointers, in Objective-C the Objects are always accessed using pointers. So the first step is allocation of memory to the pointer. This is done using **alloc** method which is implemented in NSObject. This method creates memory for all the instance variables and initializes the Instance Vairables to zero. After this initialization of variables are done.

2. **Initialization**: Here the **init** method is invoked. The init method's default implementation is in NSObject class. The sub class can overwrite this init method to set appropriate default values to the vairables and performing other task such as instatiating other internal objects.

**Main Program**

As you can see the code below we create 2 Dog Objects, one for German Shepard and other for Dobberman. Please copy the code below and paste it into Section B of main.m file as shown in the [Main Code](#main_code).

        // Section B: Object Creation
        
        // Creating Dog Objects for Doberman and German Shepherd
        Dog *myDoberman = [[Dog alloc] init];
        Dog *myGermanShepherd = [[Dog alloc] init];
        
<a name="method_invocation"/></a>
### Section C: Method Invocation or Messaging
  
As discussed earlier method invocation can be done on a class for class methods or on an instance of the class for instance methods. The class itself in Objective-C is an Object of type **Class** created by the runtime. This class object is a singleton object reated at runtime. 

A Method is called by sending a message to the object that implements the method. Messaging is done to perform some action, return some object or value, or do both things. The Messaging is done on a Object called **reciver** and the method name with parameters is called the **message**. The message expression is on the right side of the assignment, enclosed by the square brackets and as shown in the figure below. 

#  
Messaging Format => `[receiver message]`
![Method Call](/Users/narayan/Documents/MakeTechEzResources/images/GetOnToIOS/method_call_new.png "Method Call") 
<!--
![Method Call](https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToIOS/method_call_new.png "Method Call") 
-->
#  

Lets take the allocation and initialization of myDoberman object

        Dog *myDoberman = [[Dog alloc] init];

The above code sample is a nested method call consisiting of 2 parts. 

1. The first is the alloc method called on Dog `Class Dog* myDoberman = [Dog alloc];` Here Dog class Object is the receiver and alloc is the message that is called on the receiver. This is a relatively low-level call which reserves memory and instantiates the Dog object.
  
2.  The second partxp is a call to initialize the new Dog object `myDoberman = [myDoberman init];` The init implementation usually does basic setup, such as creating instance variables. The init method can be over-written for initialization  of properties and local vairables.

***
**Note:** As discussed above even though its possible to first allocate and then init in two different method calls, its best practise that both allocation and initialization are one nested call. This is because its very much possible for init to return different object then in that case you’ll be left with a pointer to the object that was originally allocated but never initialized.
***

**Nested Messaging** is done to avoid declaring numerous local variables to store temporary results. The return value from each nested expression is used as a parameter, or as the receiving object, of another message. 

**Main Program**

The code below shows the nested method to allocate and initialize the properties of Dog Object. Please copy the code below and paste it into Section C of main.m file as shown in the [Main Code](#main_code). 

        // Section C: Method Invocation or Messaging 
        
        // The following method Dog Object is initialized without calling
        // Objects Setter Property
        // Here dog is directly initialized after allocation by calling the
        // initName:Breed:Color:AndAge method
        Dog* myDog = [[Dog alloc] initName:@"Stormy" Breed:@"Doberman"
                                     Color:@"Black"
                                     AndAge:[NSNumber numberWithInt:10]];

        // Here allocation and initialization of dog object is done by calling
        // the Dog's Class Method
        Dog* myDog1 = [Dog alocAndInitName:@"Topsy" Breed:@"German Shepherd"
                                     Color:@"Black"
                                     AndAge:[NSNumber numberWithInt:10]];
        
        
As you would see the instantiation of myDog object, it first allocates and then calls the instance method initName:Breed:Color:AndAge to set the properties of Dog Class. Similarly myDog1 object calls the class method alocAndInitName:Breed:Color:AndAge to allocate and initialize the properties of Dog class. The following diagram identifies the receiver object and message for Allocation and Intiallization of mDog Object  
#  
![Method Call](/Users/narayan/Documents/MakeTechEzResources/images/GetOnToIOS/method_multi_call.png "Multi Level Method Call") 
<!--
![Method Call](https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GetOnToIOS/method_multi_call.png "Multi Level Method Call")  
-->
#  
As you can see the figure above alloc class method is invoked on receiver 1 i.e. Dog Class Object. The result is Dog Object which is receiver 2. The instance method initName:Breed:Color:AndAge is invoked on receiver 2. The combination of keyword and its value which is essentially the method parameter is the message. As you can see in the figure the value4 is derived by calling numberWithInt method on NSNumber class object.

***
**Note:** The combination of keyword and value for each methof parameters improves the readability of the code. It is of the form `keyword: value`
***

<a name="set_props"/></a>
### Section D: Set Properties
  
As you know the properties of Dog are Name, Breed, Color, Age, and isPoliceDog. Since they were declared as Property using `@synthesize` their getter and setter(i.e. accessor) methods can be called as if they were declared and implemented. You would see that for Name and Breed Property the  accessor methods are over written. But for isPoliceDog the name of the setter method is changed to isPoliceDog. For Age and Color Property the accessor methods will be called as if they were implemented. 

Properties accessed via dot-notation get translated to the accessor methods behind the scenes, so the following `myDoberman.color = @"Black";` code actually calls `[myDoberman setColor:@"Black"];` So as you can see the direct benifits of declaring Property are 

1. The accessor methods can be called as if they were declared and implemented.
2. The accessor method name can be changed while declaration and again the same need not be declared nor implemented.
3. Properties can be accessed via dot-notation and behind the scene the accessor methods will be called.

**Main Program**

The following code sets the value for Dogs Property. Please copy the code below and paste it into Section D of main.m file as shown in the [Main Code](#main_code).

        // Section D: Set Properties
        // Note that the compiler internally convert the following code to
        // setter method during compile-time. So value can be assigned to
        // name property directly instead of [myDoberman setName:@"Stacy"];
        
        // Here setter method is called on each property while in section C
        // the init method is set on all the properties of Dog class
        
        // Setting myDoberman properties
        myDoberman.name = @"Buddy";
        myDoberman.breed = @"Doberman";
        myDoberman.color = @"Black";
        myDoberman.age = [NSNumber numberWithInt:10];
        
        // myGermanShepherd myDoberman properties
        myGermanShepherd.name = @"Rombo";
        myGermanShepherd.breed = @"German Shepherd";
        myGermanShepherd.color = @"Black";
        myGermanShepherd.age = [NSNumber numberWithInt:5];
        
        // Note: The both lines of the following code call the setter method
        //       isPoliceDog. The second line calls explicitly. Also note
        //       the setter method name was changed during Property Settings
        //       to isPoliceDog
        myGermanShepherd.isPoliceDog = true;
        [myGermanShepherd isPoliceDog:true];
        
<a name="invoke_behaviour"/></a>
### Section E: Invoke Behaviour
  
As discussed in the [Method Invocation](#method_invocation), a method is invoked by placing the object and the desired method in square brackets, separated by a space. Arguments are separated from the method name using a colon(:).

**Main Program**

The following code invokes the instance methods on Dog Object to know the behaviour. Please copy the code below and paste it into Section E of main.m file as shown in the [Main Code](#main_code).

        // Section E: Invoke Behaviour
        
        // Invoke Methods to understand the Behaviour of Doberman
        [myDoberman temperament];
        [myDoberman aggression];
        [myDoberman intelligence];
        
        // Invoke Methods to understand the Behaviour of German Shepherd
        [myGermanShepherd temperament];
        [myGermanShepherd aggression];
        [myGermanShepherd intelligence];

        // Dog Description
        NSLog(@"myDog Object Desc = %@", [myDog description]);
        NSLog(@"myDog1 Object Desc = %@", [myDog1 description]);

<a name="result"/></a>
# Display Simple Dog Project Results

The following displays the Outputs of the [**Simple Dog Project**](#step_project) developed in this step

***
2013-09-23 10:07:24.319 MyDog[8849:303] In Dog Project

2013-09-23 10:07:24.322 MyDog[8849:303] Temperament of my Buddy the Doberman Dog is Fearless, and willing to defend

2013-09-23 10:07:24.322 MyDog[8849:303] Aggression of my Buddy the Doberman Dog is Extremely high on stranger-directed aggression

2013-09-23 10:07:24.323 MyDog[8849:303] Intelligence of my Buddy the Doberman Dog is Ranked 5th most intelligent dog

2013-09-23 10:07:24.324 MyDog[8849:303] Temperament of my Rombo the German Shepherd Dog is Active and willingness to learn

2013-09-23 10:07:24.324 MyDog[8849:303] Aggression of my Rombo the German Shepherd Dog is Being very safe

2013-09-23 10:07:24.326 MyDog[8849:303] Intelligence of my Rombo the German Shepherd Dog is Ranked 3rd most intelligent dog

2013-09-23 10:07:24.327 MyDog[8849:303] myDog Object Desc = My Dogs name is Stormy, Breed is Doberman, and Color is Black

2013-09-23 10:07:24.327 MyDog[8849:303] myDog1 Object Desc = My Dogs name is Topsy, Breed is German Shepherd, and Color is Black
***

<a name="practice"/></a>
# Practice Project 

Try developing following Practice Projects:

1. Create a Project to find the area of the Circle whose radius is 10 cm.

2. Create a Project to find the speed of the Car which has travelled 200 kms in 4 hours.
