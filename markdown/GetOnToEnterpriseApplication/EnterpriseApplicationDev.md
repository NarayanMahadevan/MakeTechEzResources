# Enterprise Application Development

Enterprise is kind of application that has its own set of challenges and complexities. It could be because of lot of data or because its a realtime system or its a Business Process System with a complex workflow of how the work gets done or integration with multitude of systems from legacy mainframe to windows to unix to linux, etc. Enterprise system usually involve 

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
![eCommerce System][1]
[1]:https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GK_EnterpriceApp/eCommSystem.png "eCommerce System"
<!--   
[1]:/Users/narayan/Documents/MakeTechEzResources/images/GK_EnterpriceApp/eCommSystem.png "eCommerce System"
-->

#  

**Lease Management System -** Automates processing of lease agreements. Such a system need

  a. Simpler then B2C, manage fewer - max up-to 100 users at any time
  b. Complicated Business Logic like calculating monthly bills on lease, handling    events such as early returns, late payments, etc, asset valuation, pricing, and validating data as lease are booked
  c. Dynamic Business Rules and adjust to competition
  d. Intricate User Interface and UI Navigation based on Business Logic. 
  e. Transaction support over a longer period of time as booking lease might take an hour or two over which time user is in a logic transaction.
  f. Complex Database schema with over 200 tables
  g. The following picture shows a typical Expense Tracking System          
#  
![Lease Management System][2]

[2]:https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GK_EnterpriceApp/LeaseManagementSystem.png "Lease Management System"


<!--
[2]:/Users/narayan/Documents/MakeTechEzResources/images/GK_EnterpriceApp/LeaseManagementSystem.png "Lease Management System"
-->
#  

**Expense Tracking System -** Such a System needs

  a. To support fewer users and has to be made available across the company on the Internet.
  b. To be built quickly, such system has to accommodate new functionalities over a period of time like Calculate Reimbursement Checks, feed them into payroll system, understand tax implication, tie into airline reservation web service, etc
  c. Support Data Analytics and Reports to CFO as Expense is major area of control and cost cutting CFO would like to under take
  d. The following picture shows a typical Lease Management System 
#  
![Expense Tracking System][3]

[3]:https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GK_EnterpriceApp/expenseTrackingSystem.png "Expense Tracking System" 

<!--
[3]:/Users/narayan/Documents/MakeTechEzResources/images/GK_EnterpriceApp/expenseTrackingSystem.png "Expense Tracking System" 
-->
#  

## Enterprise Architecture

All the three systems described above are different but as you can see the architecture shown here is more of a Layered Architecture. In real world there are different Architectural Patters that determine the Enterprise Applications. Hence broadly following parameters need to be considered for a available, scalable, secured and responsive system. Each of this items are discussed in detail in separate blogs as seen in the figure below. They are:

![Enterprise Application][4]

[4]: https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GK_EnterpriceApp/EnterpriseApplication.png "4 Legs of Enterprise Application"   

<!--
[4]: /Users/narayan/Documents/MakeTechEzResources/images/GK_EnterpriceApp/EnterpriseApplication.png "4 Legs of Enterprise Application"  
-->

1. ***Architecture :-*** Architecture involves breaking enterprise software into tiers where in each tier is independent of the other. The tiers represent logical divisions of an application's services, and not necessarily physical divisions between hardware or software components. Yet it is important to consider both the Software and the Server(or Hardware) Architecture when designing Enterprise Applications. So Architecture is a combination of 

	a. [**Software Application Architecture**](#app_arch) 

	b. [**Server Architecture**](#server_arch) 

2. ***Design :-*** As seen earlier Architecture breaks the Enterprise Application in various tiers. In design, each tier is looked upon in further detail with respect to the User Experience (UX) as well as the Software Design. 

	a. [**User Experience (UX) Design**](#ux_design) 

	b. [**Software Application Design**](#app_design) 

3. ***Security :-*** The characteristics of an application should be considered when deciding the layer and type of security to be provided for applications. There are different types of security or protection layer that can be used for application. This includes Application Level Security, Transport Level Security and Message Level Security. They can be used individually or in combination. Further this section also covers Secure Communication, SSL Communication and different Security Terminology. 

	a. [**Application Level Security**](#app_sec) 

	b. [**Transport Level Security**](#transport_sec) 

	c. [**Message Level Security**](#mesg_sec)

	d. [**Secure Communication**](#secure_comm)

	e. [**SSL Communication**](#ssl_comm)
	
	f. [**Security Terminology**](#sec_term)

4. [***Performance***](#performance) 

 
<a name="app_arch"/></a>
### 1a :- Software Application Architecture

Application architecture is the organizational design of an entire software application, from user interactions to interactions with all the sub components to interaction with internal and external systems and finally to a data storage. 

Thus Application Architecture describes the structure and behaviour of applications used in a business, focused on how they interact with each other,  with users and with external systems. It is focused on the data consumed and produced by applications rather than their internal structure.  

There are several design patterns that are used to define the type of architecture, and these patterns help to communicate how an application will complete the necessary business processes as defined in the system requirements. Thus applications can be classified in various types depending on the applications architecture pattern they follow.	Here are some of the frequently used Architecture Patterns. Each one of them will be described in detail in a separate blog.

a. **Layered Architecture :-** Layered Architecture is Layering of Enterprise Application in the form of Layered Cakes, where in each layer rests on the lower layer. This essentially means Top Layer uses various services of Bottom Layer and the Bottom Layer is independent or unaware of the top layer. Further each layer hides the lower layer from the layer above. 

b. **MVC Architecture :-** MVC architecture is a Model-View-Controller architecture used in simple GUI applications. The architecture is event-driven, which means that all activity starts by some event and is propagated by some other events. The architecture usually contains a large number of components comprising of 

	**The Model** is the Data Model of the component. It can be as simple as an integer or a string, and as complex as an interface to an external database. 

	**The View** is the visual representation of the component. It is User Interface component through which the User Interacts with the system. 

	**The Controller** takes care of all the action or the execution of Business Logic. It knows how to change the model in response to these events and it also knows how to change the component's state in the view. 

c. **SOA Architecture :-** A service-oriented architecture is essentially a collection of services. Each Service is well-defined, self-contained, and does not depend on the context or state of other services. These services communicate with each other as well as with internal and external systems. The communication can involve either simple data passing or it could involve two or more services coordinating some activity. The services are connected typically using web services defined using SOAP, REST or JSON. The services can also be connected using distributed technologies like DCOM, CORBA, or J2EE Technologies.

d. **Hub-and-Spoke Architecture :-** This is one of the most powerful architecture for Enterprise Application Integration (EAI). It comes from the realization that for a completely connected graph of n nodes would need n/2 * (n-1) integration connectors. Here node represents an Application, Data Source, Legacy Systems, 3rd Party Systems, etc. For example, while 4 nodes require only 6 connections but 8 nodes require 28 connections.  

	The general idea is that the combinatorial explosion of the number of connections can be avoided if this "web" of connection is replaced with something that resembles a wheel with a central hub and spokes going out to all the nodes. In such a topology, the number of nodes is equal to the number of connections, which means it grows linearly. 

	The airlines as well as FedEx have been implementing this idea 
for quite some time. It is much too expensive to fly airplanes directly from everywhere from anywhere. Instead, each carrier maintains a small number of central hubs and tries to route as many flights as possible through these hubs. 
	
e. **Pipe And Filter Architecture :-** This is a very simple, yet powerful and robust architecture. It consists of any number of components (filters) that transform or filter data, before passing it on via connectors (pipes) to other components. The typical Components of Pipe And Filter Architecture are

	**The Pump ** or Producer is the data source. It can be a static text file, or a keyboard input, or systems that is continuously creating new data.
	 
	**The Pipe** is the connector that passes data from one filter to the next. It is a directional stream of data, that is usually implemented by a data buffer to store all data, until the next filter has time to process it.
	
	**The Filter** Which transforms or filters the data it receives via the pipes with which it is connected. A filter can have any number of input pipes and any number of output pipes.
	
	**The Sink** or consumer is the data target. It can be a another file, a database, or a computer screen.
	
f. **Ports And Adapters :-**  This was earlier called as **Hexagonal Architecture**. The main aim of this architecture is to decouple the application's core logic from the services it uses. This allows different services to be "plugged in", and it allows the application to be run without these services. 

	So the aim of this architecture is to make The Domain independent from low level concerns such as databases, network services, GUIs and other things “external” to the core of the application. To achieve this all the external services interact with **The Domain** (The core business logic) through **Port and Adapter** and also The Domain interacts with the external services through Port and Adapter. The Domain is essentially the core logic or the business purpose it is trying to serve.	
	
g. **Blackboard Architecture :-** This Architecture is typically used as a way to handle complex, ill-defined problems, where the solution is the sum of its parts. Blackboard Architecture typically consists of a Blackboard, a Knowledge Source and Schedular. The blackboard is iteratively updated through the schedular by a specialist knowledge sources, starting with a problem specification and ending with a solution. As stated Each knowledge source updates the blackboard with a partial solution when its internal constraints match the blackboard state.

<a name="server_arch"/></a>
### 1b :- Server Architecture 

This essentially means running the enterprise application on different servers or machines. Logically all layers can be run on one server or each layer of the application can be run on different servers. Server Architecture involves Firewall, DMZ, Load Balancer, HTTP Proxy Server, and Clusters of Web and Application Server. Here is the brief about all the components of the Server Architecture.

a. **De-Militized Zone (DMZ) :-** DMZ is the logical collection of Hardware and Services that are made available to outside untrusted sources. Bunch of web servers reside in DMZ to allows access to HTML content.

b. **Load Balancer :-** Load Balancer describes any technology that distributes  Client Connection Request to one or more distinct IP Addresses. A simple Web application may use the **DNS Round-robin Algorithm** as a load balancer. Larger applications generally use hardware-based load balancing solutions which may also provide firewall-like security capabilities. 

	Load Balancing Strategies include **Connection Based Algorithm** of associating a particular client connection request to a particular server in the cluster or **Weight Based Algorithm** based on monitoring the utilization of individual machine.

c. **HTTP Proxy Server :-** HTTP Proxy Server is in the DMZ zone and typically host http static contents. This server has a proxy plugin to the Web Services hosted in the Cluster of Web Servers outside the DMZ zone. The proxy plug-in contains the load balancing logic for accessing the web server clusters.

d. **Server Clusters :-** Clusters consists of multiple server instances of Web and Applications Servers running simultaneously to provide increase Scalability and Availability. Clusters support Application Fail-overs and Load Balancing capabilities.

<a name="ux_design"/></a>
### 2a :- User Experience (UX) Design

This is a 4 Step process from White Boarding to Wire Frames to Visual Designs to Mock-ups. The focus of User Experience starts with how to treat people and finally as we go through this process the focus is more on creating an impact using Visual Designs.


1. **White Boarding :-** Here on a piece of paper following three questions are answered 

	a: Who are the users

	b: What they see

	c: What can they do    

2. **Wire frames :-** The User Interactions essentially the user flow is captured in Wire frames. The information from White Boarding what users see and whet users can do is captured as flow in the Wire Frames. It all begins with the layout of landing page or the dash board which identifies all the visual elements and the corresponding flow based on interactions with the visual elements.

3. **Visual Designs :-** The Visual Elements of the wireframe are UI Controls, Images, Icons, Colour Schemes are elaborated to form Visual Designs. During Visual Designs the principles of Contrast, Emphasis, Variety, Balance, Proportion, Repetition, Texture, etc are considered to create an impact to the users. 

4. **UI Mockups :-** The Visual Designs are converted to UI Mockups either HTML, Desktop or Mobile based on delivery platform and Technology.

<a name="app_design"/></a>
### 2b :- Software Application Design

To design a sound application, its essential to analyze the business domain, capture system requirements, capture expected user and system interactions, analyze and capture information about the application domain, and then produce a detailed design. Application Design begins with identifying the users, the goals that the user wants to achieve, or a particular problem that the user wants to solve, and then discovering the functionality and environment of the system that can achieve these goals or solve the problem. The second step is to build on the first step to create a high-level structures that describes how the system will be logically constructed. Finally the structure is analyzed to incorporate the best practices and proven solution by employing appropriate Design Patterns to specific problems. A design pattern is not a framework. It provides common language for certain problem and captures good practices. Design patterns can be classified in three categories: Creational, Structural and behavioural patterns..

1. **Creational Patterns :-** These design patterns provides way to create objects while hiding the creation logic, rather than instantiating objects directly using new operator. This gives program more flexibility in deciding which objects need to be created for a given use case.

2. **Structural Patterns :-** These design patterns concern class and object composition. Concept of inheritance is used to compose interfaces and define ways to compose objects to obtain new functionalities.

3. **Behavioural Patterns :-** These design patterns are specifically concerned with communication between objects.

<a name="app_sec"/></a>
### 3a :- Application Level Security

Application Level Security is the Security uniquely suited to the needs of the Application. Applications consist of components that can contain both protected and unprotected resources. Protected Resources are accessed by Authorsized users. The Security at the Application layer include 

**Authentication :-** This is a process that verifies the identity of a user, device, or other entity in a computer system, usually as a prerequisite to allowing access to resources in a system.

**Authorization, or Access Control :-** This is a process that enables recognition of an entity which are collections of users or programs in the system for the purpose of performing operations or accessing data.

**Non-repudiation :-** The means used to prove that a user who performed some action cannot reasonably deny having done so. This ensures that transactions can be proved to have happened.

**Auditing :-** This means the system maintains a record of transactions and security information.

<a name="transport_sec"/></a>
### 3b :- Transport Level Security

Transport-layer security is provided by the transport mechanisms used to transmit information over the wire between clients and providers; thus, transport-layer security relies on secure HTTP transport (HTTPS) using Secure Sockets Layer (SSL). Transport security is a point-to-point security mechanism that can be used for authentication, message integrity, and confidentiality. When running over an SSL-protected session, Transport-layer security is performed in a series of phases, as follows 

1. The client and server agree on an appropriate encryption algorithm
2. The server and client authenticate each other using Digital Certificates 
3. A cryptographic key is exchanged using public-key encryption. Usually three keys are used to set up the SSL connection: the public, private, and session keys. Anything encrypted with the public key can only be decrypted with the private key, and vice versa.
4. A symmetric session key is used during the information exchange. This is because encrypting and decrypting with private and public key takes a lot of processing power. Hence they are used in the initial client server authentication to create a symmetric session key.


<a name="mesg_sec"/></a>
### 3c :- Message Level Security

In Message Level Security, security information is contained within the SOAP message and/or SOAP message attachment, which allows security information to travel along with the message or attachment. For example, a portion of the message may be signed by a sender and encrypted for a particular receiver. When sent from the initial sender, the message may pass through intermediate nodes before reaching its intended receiver. In this scenario, the encrypted portions continue to be opaque to any intermediate nodes and can be decrypted only by the intended receiver. 

<a name="ssl_comm"/></a>
### 3d :- SSL Communication

Here are the steps for SSL Certificate to create Secure Communication.
 
1. Browser connects to a web server (website) secured with SSL (https).
2. Browser requests that the server identify itself.
3. Server sends a copy of its SSL Certificate, including the server’s public key.
4. Browser checks the certificate root against a list of trusted CAs(Certificate Authorities) and that the certificate is unexpired, unrevoked, and that its common name is valid for the website that it is connecting to. If the browser trusts the certificate, it creates, encrypts, and sends back a symmetric session key using the server’s public key.
5. Server decrypts the symmetric session key using its private key and sends back an acknowledgement encrypted with the session key to start the encrypted session.
6. Server and Browser now encrypt all transmitted data with the session key.


<a name="sec_term"/></a>
### 3e :- Security Terminology

**SSL(Secure Sockets Layer) :-** SSL is a standard security technology for establishing an encrypted link between a server and a client—typically a web server (website) and a browser; or a mail server and a mail client (e.g., Outlook). SSL allows sensitive information such as credit card numbers, social security numbers, and login credentials to be transmitted securely. 

**Encryption :-** Encryption scrambles or modifies a message or document so it cannot be read and understood, except by the intended recipient. A key is necessary to reverse the scrambling or modification, to make the message readable.

**Symmetric Cryptosystem :-** If the same key is used to encrypt the message, as is used to decrypt the message; such a scheme is called a symmetric cryptosystem. 

**Asymmetric Cryptosystem :-** This is a second kind of cryptosystem, which uses one key to encrypt, and a different key to decrypt. It has the advantage that many people can use the encryption key to encrypt messages for a recipient, but only the recipient who has the decryption key can read and understand them.

**Public Key Cryptosystem :-** When the encryption key is published for anyone to use, then this is called a public key cryptosystem

**Digital Certificates :-** This are used to verify that a message or document was authored by a certain person, and that it was not altered or modified by anyone else. They are issued by Trusted Certificate Authorities (CA).

**SSL Certificates :-** They have a key pair a public and a private key. These keys work together to establish an encrypted connection. This are also Digital Certificates that contains what is called the “subject,” which is the identity of the certificate/website owner.

**SSL Handshake :-** This is a process by which the Browser establishes a Secured Connection with the Web Server by creating and encrypting symmetric session key using the server’s public key and sending it to the server for acknowledgement to start the encrypted session.

<a name="performance"/></a>
### 4 :- Performance

Generally the approach is to get the system up and running and then use disciplined optimization process based on measurement. However some architectural decisions affects performance that are difficult to fix. Its difficult to talk about performance because every system is very unique. But broadly its important to consider the different performance parameter while architecting a system. This include Response Time, Responsiveness of the System, Latency in Calls, Throughput in number of calls per second, Load to measure stress in the system, Capacity to measure maximum acceptable throughput, and finally the most important parameter Scalability both Hardware and Server Scalability. Performance is discussed in detail in the separate blog article called [**Application Performance**](http://wp.me/p2Yph5-5f).

