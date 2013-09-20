# Application Performance

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

![Application Performance][1]

[1]: /Users/narayan/Documents/MakeTechEzResources/images/GK_EnterpriceApp/ApplicationPerformance.png "4 Pillers for Application Performance"  
<!--
1]: https://raw.github.com/NarayanMahadevan/MakeTechEzResources/master/images/GK_EnterpriceApp/ApplicationPerformance.png "4 Pillers for Application Performance"   
-->
#  
