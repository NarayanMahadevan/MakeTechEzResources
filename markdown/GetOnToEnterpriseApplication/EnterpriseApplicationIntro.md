# Enterprise Application

Enterprise is kind of application that has its own set of challanges and complexities. It could be because of lot of data or because its a realtime system or its a Business Process System with a complex workflow of how the work gets done or integration with multitude of systems from legacy mainframe to windows to unix to linux, etc Enterprise system usually involve 

* Persistent Data - Huge amount Data with tens of millions of records
* Access Data Concurrently - Web based systems with thousands of users accessing data concurrently
* Lots of User Interface Screens in Mobile, Web and Desktop for user access
* Integration with other enterprise application built on different technologies and requiring complete different Hardware servers.
* Integration with third party applications
* Differences in business models and processes w.r.t enterprise data. This is called business logic or rules which are unique to each systems and are tightly coupled.

Lets consider 3 sample Enterprise Application

**B2C eCommerce System -** Users browse, search for Products, add it to cart, buy, do payment and place orders. Such a system needs 

  a. To handle a very high volume of users 
  b. Highly Responsive
  c. Use system resources efficiently
  d. Be Scalable so that more load can be handled by adding more Hardware.
  e. Domain logic is pretty straight-forward, simple pricing, shipping and tax calculation
  f. Integration points with external systems are fairly well defined with Payment Systems or Shipping Handlers.
  g. Simple and elegant presentation layer and be able to allow access from multiple touch points like Web, Mobile, etc.
  h. Data Source includes database for holding users, products, orders, and perhaps the inventory systems
  i. The following picture shows a typical eCommerce System
#  
   ![eCommerce System](/Users/narayan/Documents/MakeTechEzResources/images/GK_EnterpriceApp/eCommSystem.png)
<!--
![eCommerce System](https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GK_EnterpriceApp/eCommSystem.png) 
-->   
#  

**Lease Management System -** Automates processing of lease agreements. Such a system need

  a. Simpler then B2C, manage fewer amx upto 100 users at any time
  b. Complicated Business Logic like calculating monthly bills on lease, handling    events such as early returns, late paymennts, etc, asset valuation, pricing, and validating data as lease are booked
  c. Dynamic Business Rules and adjust to competition
  d. Intricate User Interface and UI Navigation based on Business Logic. 
  e. Transaction support over a longer period of time as booking lease might take an hour or two over which time user is in a logic transaction.
  f. Complex Database schema with over 200 tables
  g. The following picture shows a typical Expense Tracking System          
#  
![Expense Tracking System](/Users/narayan/Documents/MakeTechEzResources/images/GK_EnterpriceApp/expenseTrackingSystem.png) 
<!--
![Expense Tracking System](https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GK_EnterpriceApp/expenseTrackingSystem.png) 
-->
#  

**Expense Tracking System -** Such a System needs

  a. To support fewer users and has to be made available across the company on the Internet.
  b. To be built quickly, such system has to accomodate new functionalities over a period of time like Calculate Reimbursement Checks, feed them into payroll system, understand tax implication, tie into airline reservation web service, etc
  c. Support Data Analytics and Reports to CFO as Expense is major area of control and cost cutting CFO would like to under take
  d. The following picture shows a typical Lease Management System 
#  
![Lease Management System](/Users/narayan/Documents/MakeTechEzResources/images/GK_EnterpriceApp/LeaseManagementSystem.png) 
<!--
![Lease Management System](https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GK_EnterpriceApp/LeaseManagementSystem.png) 
-->
#  

All the three systems are different but as you can see the architecture is more or less same. Hence broadly following parameters need to be considered for a available, scalable, secured and responsive system. Each of this items are discussed in detail in the blog, They are:

1. ***Application Architecture***
2. ***Application Design***
3. ***Application Security***
4. ***Application Performance***
 
**4 Legs of Enterprise Application** ![Enterprise Application][4]

[4]: /Users/narayan/Documents/MakeTechEzResources/images/GK_EnterpriceApp/EnterpriseApplication.png "4 Legs of Enterprise Application"  
<!--
4]: https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GK_EnterpriceApp/EnterpriseApplication.png "4 Legs of Enterprise Application"   
-->
#  

