# Get To Know BPM

This is the third part of the six part series. The essesnse of this Get To Know BPM series is to get overall understanding of Business Process Management in a quick and an easy manner. This series of articles is meant for both Technical as welll as Business folks. Here are the abstract of all the articles covered in the BPM series. 

1. [**What is BPM**](http://wp.me/p2Yph5-5w) - This article is the quick introduction of Business Process Management.
2. [**BPM Lifecycle and Implementation Plan**](http://wp.me/p2Yph5-5y) - This articles takes you through BPM Lifecycle and typical implementation of BPM project.
3. [**BPM Software Components**](http://wp.me/p2Yph5-5A) - This article covers major software components that make-up the BPM Platform.
4. [**BPM Process Design, Business Rules and Event Management**](http://wp.me/p2Yph5-5C) - This article goes deeper into understanding in more detail the most important software components of BPM Platform. 
5. [**BPM Software Vendors**](http://wp.me/p2Yph5-5E) - This article gives a overview of different Software Vendors who specialize in developing BPM Platform.
6. [**BPM for various Industries**](http://wp.me/p2Yph5-5G) - This article briefly covers BPM Projects that are implemented in various Industry Segments.

<a name="bpm_software_comps"/></a>
# BPM Process Design Busines Rules and Event Management

This article is an extension to the previous articles which introduced in general the Software Components that make up the BPM Platform. This article goes deeper into understanding in more detail the most important software components of BPM Platform. They are:

a. [**BPM Process Design**](bpm_process_design)
b. [**BPM Business Rule Management**](bpm_buss_rule)
c. [**BPM Business Event Management**](#bpm_evnt_mgmt)

<a name="bpm_process_design"/></a>
# Process Design

In the BPM environment, process design and definition occurs within a graphical environment. Most BPM development tools are a standard modeling notation — essentially, a simplified programming language — to define the process model. Typically, either Business Process Modeling Notation (BPMN) or XML Process Definition Language (XPDL) is used. Essentially, a process design looks very much like a flowchart wherein the **Business Processes** are the boxes in the flowchart, and the **Business Rules** define the logic flow through the flowchart.  

1. Each **Business Process** has a defined implementation that may be a human task, an automated step, a business rule, a business systems across the enterprise, or external business system. 

2. **Business rules** are at the heart of a BPM project. These rules are the policies and procedures that automate the business process. Essentially Business rules govern workflow routing within a BPM process.

<a name="bpm_buss_rule"/></a>
# Business Rule Management

The basic operational value proposition of BPM is the ability to process more for less effort with higher predictatbility and consistency. To achieve this automation of high value Operational Decision is the must. This Decisions are based on Business Rules that are based on policies and procedures as well as derived from current Business Analytics and future Predictive Analytics.  

Business Rules are essentially conditional statements and are used for a variety purposes with-in Business Process Management. They are:

1. Process Initialization and Prioritizations
2. Routing Decisions
3. Setting alerts and triggers
4. Determine Business Outcome

Using Software for Business Rules Management, allows clear seperation of Business Rules from Application Code. This essentially means Business Owners can define and manage the decision logic, reducing the amount of time and effort required to update that logic in production systems. Thus enhancing the organization’s ability to respond to changes in the business environment. Essential **Components** of Business Rule Management Software are:

1. **Rules Repository -** Rules are stored in Hierarchical Manner with version control and ability to role back. 

2. **Rules Designer -** To create rules that support complex decisions, data transformations, global constants, and data queries. 

3. **Rules Validator -** Validate rules before publishing using Process Simulation.

4. **Rules Executer -** To execute Business Rules Engine to execute Rules real-time during Process Execution.  The outcome of Rules Exceution could be Process Initialization, Process Routing, Alerts and Triggers, or Business Outcome.

<a name="bpm_evnt_mgmt"/></a>
# Business Event Management

Business Events are events that are triggered during the execution Business Processes or are messages that are processed comming from external sources or systems. Business Events occour real time to facilitate situational awareness and response. 

Types of Event Supported are 

1. **Timer Events -** Timer Events are based on Events that are triggered on Set Date and Time or the Events that are triggered after particular delay. Timer Events can be also be rule based. Timer Events trigger processes, notifications or other events, etc in a Business Process Management System.

2. **Rule Based Events -** These events are triggered based on the execution of Business Rule. As any other events Rule Based Events also triggers Asynchronous Process Communication.

3. **Message Events -** Message Events are events that are detected, received or intercepted by Event Processor and processed based on rules enabling automated decision making. Message events can be unstructured data such as client letters and communications, emails, policies, media attachments, event feeds, social networking feeds, and a range of real-time collaboration tools.

