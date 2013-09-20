# Application Architecture

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


