# Get To Know BPM

This is the third part of the six part series. The essesnse of this Get To Know BPM series is to get overall understanding of Business Process Management in a quick and an easy manner. This series of articles is meant for both Technical as welll as Business folks. Here are the abstract of all the articles covered in the BPM series. 

1. [**What is BPM**](http://wp.me/p2Yph5-5w) - This article is the quick introduction of Business Process Management.
2. [**BPM Lifecycle and Implementation Plan**](http://wp.me/p2Yph5-5y) - This articles takes you through BPM Lifecycle and typical implementation of BPM project.
3. [**BPM Software Components**](#bpm_software_compsA) - This article covers major software components that make-up the BPM Platform.
4. [**BPM Process Design, Business Rules and Event Management**](http://wp.me/p2Yph5-5C) - This article goes deeper into understanding in more detail the most important software components of BPM Platform. 
5. [**BPM Software Vendors**](http://wp.me/p2Yph5-5E) - This article gives a overview of different Software Vendors who specialize in developing BPM Platform.
6. [**BPM for various Industries**](http://wp.me/p2Yph5-5G) - This article briefly covers BPM Projects that are implemented in various Industry Segments.

<a name="bpm_software_comps"/></a>
# BPM Software Components

The first article introduced the basic concept while the second part was more BPM Lifecycle and Implementation Plan for BPM Project. This article is more about the Software Components that make up the BPM Platform.

<a name="bpm_platform"/></a>
# Major Components in BPM Software

The figure below shows high-level overview of BPM Platform. 

#  
![BPM Software Components][1]

[1]: /Users/narayan/Documents/MakeTechEzResources/images/GK_EnterpriseArchPlan/BPMSystem.png "BPM Software Components"  
<!--
[1]: https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GK_EnterpriseArchPlan/BPMSystem.png "BPM Software Components"     
-->

As can be seen in the figure the folllwoing are some of the major software components that make up BPM Platform. 
1. **End User Components** include 
   a. **Web UI -** Workspace Component for process monitoring, management dashboards, and task inboxes. 

   b. **Enterprise Mobility -** Mobile interface enabling the right employees, access to key business processes, tasks, data, and reports realtime on-the-go.

   c. **Collaboration Tools —** Effective communication both intra- and inter departmental through discussion forums, dynamic workspaces, and message boards
2. An **Execution Environment Components** which includes 

   a. **Workflow Processor** is the execution of Process Model where in the Business Process Engine executes individual process and Business Rule Engine execute the logicflow between the processes. 

   b. **Business Process Engine** responsibility is to execute individual processes with-in the Business Process Model. Each Business Process has a defined implementation that may be a human task, an automated step, a business rule, a business systems across the enterprise, or external business system

   c. **Business Rules Engine** to execute Business Rules and automate the decision making process. More details in Business Rule Management.

   d. **Business Event Processor** to send, receive and process message events for asynchronous process communication. Business Event Processor enables an organization to set Rules and Timers to detect and send events taking place during the execution of the Business Process Model as well as receive and process messages to trigger relevant business processes. More details in Business Event Processing.

   e. **Analytics Engine** This helps in **Predictive Analytics** to create prediction models for future process activities, real-time analysis and reporting for up to tens of millions of active process instances, and **Postmortem Analytics** of process models to view inefficiencies and bottlenecks measured against key performance indicators (KPIs). <p></p>

3. **Designer Toolbox** that enables process modeling, business rule definition, event specifications, definition of  key performance indicators (KPI’s), process development, and design of user interfaces

4. **Metadata Repository** that contains process repository, rules and events repositiory. For appropriate management of repository, its importatnt that BPM platform supports version control, hierarchical categorization, search, and role-based security for controlled access.

5. <a name="bpm_prcs_simulation"/></a>**Process Simulation -** This component allows to test your processes before going live with them. Its also usesful to run the processes through what-if scenarios for adjustments and fine-tuning of the model. Process simulation is one of the iterative steps in the development of an effective BPM system. Typically the importance is discovered by analyzing the results of the simulation, making necessary changes, and rerunning the simulation — possibly several times.
6. **Document Management** component provides a system for storing and securing electronic documents, images, and other files. Full text search and quick content filters ensure one can quickly find key documents to share in processes and tasks. Version Control, Sharing, Document Genaration, Mobile Access, etc are other key features of Document Management System.
7. **Integration Component** that integrates easily using SOA, Web Services, Messaging Systems, etc to enterprise systems as well as external systems. This is important to protect the investments done by enterprise on Technology Assets and leverage them to create an Integrated BPM Solution.   

<a name="next_step"/></a>
# Next Article

The next article [**BPM Process Design, Business Rules and Event Management**](http://wp.me/p2Yph5-5C) article goes deeper into understanding in more detail the most important software components of BPM Platform. 


