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

All the three systems are different but as you can see the architecture is more or less same. Hence broadly following parameters need to be considered for a available, scalable, secured and responsive system. They are:

1. [**Application Architecture**](#appln_architecture) 
2. [**Application Design**](#appln_flexibility)
3. [**Application Security**](#appln_security)
4. [**Application Performance**](#appln_performance)
 
**4 Legs of Enterprise Application** ![Enterprise Application][4]

[4]: /Users/narayan/Documents/MakeTechEzResources/images/GK_EnterpriceApp/EnterpriseApplication.png "4 Legs of Enterprise Application"  
<!--
4]: https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GK_EnterpriceApp/EnterpriseApplication.png "4 Legs of Enterprise Application"   
-->
#  


<a name="appln_architecture"/></a>
## Application Architecture
#  
Enterprise Architecture is essentially a combination of Application Architecture and System Architecture. 

1. **Application Architecture:** This essentially means breaking enterprise software into different software layeres, each layer indipendent of the other. Hence this can also be referred as Layered Architecture. More details in the following section.

2. **System Architecture:** This esentially means running the enterprise application on different servers or machines. Logically all layers can be run on one server or each layer of the application can be run on different servers. System Architecture also involves Firewall for Secured Access, Server Clustering for Load Balancing, etc. 

####Layered Architecture

As discusssed earlier Layered Architecture is Layering of Enterprise Application in the form of Layered Cakes, where in each layer rests on the lower layer. This essentially means Top Layer uses various services of Bottom Layer and the Bottom Layer is independent or unaware of the top layer. Further each layer hides the lower layer from the layer above. 

**Benefits** of Layered Architecture are:

1. Since each Layer is independent of the other, hence each layer can be understood and developed seperately.
2. Each Layer can have alternative implementation of the same basic service without impacting the other layers.
3. Layers are good places for standardization as they expose standard well defined interface for interaction.
4. Once a layer is built many higher level services can be built on top of it. Typically there are many different Client Interfaces like Web, Desktop, and Mobile built on top of single standard middleware

Eventhough Layering is important, one should be aware of the potential **Downsides** to work around the same in the overall Application Architecture. They are:

1. Layers sometimes fail to encapsulate all the things and hence have cascading and time consuming impact. The classic example is to show a new field in the UI. This field is in the database and need to be introduced in each layer in between the UI Layer and the DB layer to accomodate the change.
2. Each Layer adds latency which impacts performance and hence in a real-time system of request and response, avoid traversing through many layers. 
  
Typically Enterprise Application can be devided into 3 Principal Layer as shown in the table below

Layer        | Description  | 
:----------- | :----------- | 
Presentation | <p></p> 1. This Layer handles interaction between the Users and the Software. <p></p> <p> 2. Presentation Layer can be Simple Command Line or Rich Client UI or Mobile App or Internet App.</p> 3. The Primary Responsibility of this layer is to display information to the user and to interpret command from the user into action on the Domain Layer and then to the Data Source.<p></p>
Domain       | <p></p> 1. This Layer interprets the action from the Presentation Layer and translates into Business Logic that needs to be executed. <p></p> 2.The Primary Responsibility of this Layer includes some calculation based on user input, store data, validate data, or more importantly the Data Source to be used based on commands received from presentation layer.<p></p>      
Data Source  | <p></p> 1. This layer handles communication with the Database, Messaging System to retrieve data from Legacy System, Transaction Monitors or other Applications <p></p> 2. The Primary Responsibility of this layer is to perform action on the Data Model i.e. to get, set or update the data model. <p></p>      


<a name="appln_performance"/></a>
## Application Performance
#  
Generally the approach is to get the system up and running and then use disciplined optimization process based on measurement. However some architectural decisions affects performance that are difficult to fix. Its difficult to talk about performance because every system is very unique. But broadly the following parameters should be understood when architecting a system. They are:

a. [**Response Time and Responsiveness**](#system_response)
b. [**Latency**](#system_latency)
c. [**Throughput**](#system_throughput) 
c. [**Load and Load Sensistivity**](#system_load)
d. [**Efficiency and Capacity**](#system_efficiency)
e. [**Scalability**](#system_scalability)
f. [**General Thumb Rule**](#system_thumb_rule)

<a name="system_response"/></a>
#### Response Time and Responsiveness
#  
**Response Time** is the time taken by the system to precoess a individual request. This might be UI Request or Server API Calls. Response Time can be improved by better caching but this also results in reduction of performance as load increases.

**Responsiveness** is how quickly system acknowledges a request as opposed to 
processing it. This is important because user may become frustrated if system has low responsiveness even if the response time is good. 

If the system waits during the whole request then the responsiveness and response time are the same. On the other hand if the system indicates it has received request before even it completes then the responsiveness is better. **For e.g.**  providing progress bar during file transfer improves responsiveness of the system.

<a name="system_latency"/></a>
#### Latency
#  
Latency is the minimum time required to get any form of response, even if the work to be done is non-existent. If it is a local calll then the response if instentanious but there is some latency when it is a remote call. Letency is the reason why remote calls should be reduced. 
	
<a name="system_throughput"/></a>
#### Throughput
# 
Throughput is the work done in a given time. In Enterprise System it is typically transactions per second(tps). This are common sets of transactions that are frequently done by the system. In an Internet System its number of http calls handled by the system in a given time. While in a Web Service environment, its number of api calls handled in a given time. Sometimes improving throughput can effect the response time. So its best to improve responsiveness at the cost of response time to increase throughput and increase performance.
	
<a name="system_load"/></a>
#### Load and Load Sensistivity
#  
**Load** is how much stress system is under and is typically measured by number of concurrent users, concurrent connections, concurrent threads, etc. Load is used in context of response time like some request takes 0.5 secs/request to respond for 10 users while takes 2 secs/request for 20 users. As you can see the response time per request is impacted as number of users increases.

**Load Sensistivity** is measured based on how response times varies with the load. So for example System A has a response time of 0.5 secs for 10 through 20 users and System B has response time of 0.2 secs for 10 users and 2 secs for 20 users. The System A has lower load sensitivity compared to System B. In other words System B degrades in performance more the System B. 
	
<a name="system_efficiency"/></a>
#### Efficiency and Capacity
#  
**Efficiency** is thoughput divided by resources. A system that gets 30 tps on 2 CPUs is better then the system that give 40 tps with 4 CPUs.

The **Capacity** of a system is an indication of maximum effective throughput or load. This is absolute maximum or a point after which the performance dips below an acceptable threshold.	

<a name="system_scalability"/></a>
#### Scalability
#  
**Scalability** is a measure of how adding resources(usually hardware) affects performance. A scalable system is one that allows to add hardware and get commensurate performance improvement. Such as doubling the server gave double the throughput. 

**Vertical Scalability** or **Scalling Up** means adding more power to single server where as **Horizontal Scalability** or **Scalling Out** means adding more server.	
<a name="system_thumb_rule"/></a>
#### General Thumb Rule
#  
Here are some basic thumb rules that can be used while architecting a system
	
1. Build **Highly Responsive System**. Do not sacrifice performance to achieve higher response time.

2. Improve Latency by **Minimizing Remote Calling** and locating servers closer to the user to reduce number of hops for the request and response to make their way across the wire.

3. Balance between Response Time and Throughput needs to be achieved as increasing one will impact the other.

4. Building Enterprise Application, it makes sense to build for **Hardware Scalability** rather than capacity or efficiency.  

Thus the 4 Pillar's for a highly available and responsive systems are Scalability, Responsiveness, Throughput and Response Time. Latency has to be improved where ever possible and balace between Throughput and Response Time has to be achieved.