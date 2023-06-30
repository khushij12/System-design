# System-design

## What is CAP theorem?
CAP(Consistency-Availability-Partition Tolerance) theorem says that a distributed system cannot guarantee C, A and P simultaneously. It can at max provide any 2 of the 3 guarantees. Let us understand this with the help of a distributed database system. 

**Consistency**: This states that the data has to remain consistent after the execution of an operation in the database. For example, post database updation, all queries should retrieve the same result.
**Availability**: The databases cannot have downtime and should be available and responsive always.
**Partition Tolerance**: The database system should be functioning despite the communication becoming unstable.

![](https://d3n0h9tb65y8q.cloudfront.net/public_assets/assets/000/002/781/original/CAP_theorem.png?1644591573)

## How is Horizontal scaling different from Vertical scaling?
**Horizontal scaling** refers to the addition of more computing machines to the network that shares the processing and memory workload across a distributed network of devices. In simple words, more instances of servers are added to the existing pool and the traffic load is distributed across these devices in an efficient manner.
**Vertical scaling** refers to the concept of upgrading the resource capacity such as increasing RAM, adding efficient processors etc of a single machine or switching to a new machine with more capacity. The capability of the server can be enhanced without the need for code manipulation.

**Horizontal Scaling / Vertical Scaling**
1. Requires load balancing for distributing request traffic across multiple machine / Since there is just one single machine, the load balancer is not required.
2. More resistant to application failure because if one server fails, traffic is routed to other servers. / This is more prone to failure as there is only one machine and failure of this results in failure of the entire application.
3. Since there are multiple machines being involved, it is very much necessary to have network communication / Vertical scaling makes use of inter-process communication within the machine which makes it quite fast.
4. There exist possibilities of data inconsistencies here because there are different machines for handling different requests which might result in data being out of sync. / As there is only one machine, there is no issue of data inconsistency.

Since this scaling requires multiple servers, there might be concerns on budget and space but the scaling of the application can be done as much as needed based on the business needs.	/ Vertical scaling has a limit on the capacity of the resources that are achievable. If the resources are scaled up above this limit, then the application might crash and result in downtime.

##  What do you understand by load balancing? Why is it important in system design?
Modern-day websites are designed to serve millions of requests from clients and return the responses in a fast and reliable manner. In order to serve these requests, the addition of more servers is required. In such a scenario, it is essential to distribute request traffic efficiently across each server so that they do not face undue loads. 
1. Load balancer acts as a traffic police cop facing the requests and routes them across the available servers in a way that not a single server is overwhelmed which could possibly degrade the application performance.
2. They help to prevent requests from going to unhealthy or unavailable servers.
3. Requests sent to the servers are encrypted and the responses are decrypted. It aids in SSL termination and removes the need to install X.509 certificates on every server.
4. Load balancing impacts system security and allows continuous software updates for accomodating changes in the system.

## What do you understand by Latency, throughput, and availability of a system?
Performance is an important factor in system design as it helps in making our services fast and reliable. Following are the three key metrics for measuring the performance:

**Latency**: This is the time taken in milliseconds for delivering a single message.
**Throughput**: This is the amount of data successfully transmitted through a system in a given amount of time. It is measured in bits per second.
**Availability**: This determines the amount of time a system is available to respond to requests. It is calculated: System Uptime / (System Uptime+Downtime).

## What is Sharding?
Sharding is a process of splitting the large logical dataset into multiple databases. It also refers to horizontal partitioning of data as it will be stored on multiple machines. By doing so, a sharded database becomes capable of handling more requests than a single large machine.

Sharding helps to scale databases by helping to handle the increased load by providing increased throughput, storage capacity and ensuring high availability.

## How is NoSQL database different from SQL databases?
Follows relational model / Follows the non-relational model.

Deals with structured data / Deals with semi-structured data.

SQL follows a strict schema / NoSQL deals with dynamic schema and is very flexible.

Follows ACID (Atomicity, Consistency, Isolation, Durability) properties / Follows BASE (Basic Availability, Soft-state (The state of the data could change without application interactions due to eventual consistency.), Eventual consistency) properties.


## How is sharding different from partitioning?
**Database Sharding** - Sharding is a technique for dividing a single dataset among many databases, allowing it to be stored across multiple workstations.

**Database Partitioning** - Partitioning is the process of separating stored database objects (tables, indexes, and views) into distinct portions. Large database items are partitioned to improve controllability, performance, and availability.

## How is performance and scalability related to each other?
A system is said to be scalable if there is increased performance is proportional to the resources added. This can also mean being able to handle larger work units when datasets grow. 

## What is Caching? What are the various cache update strategies available in caching?
The cache can only store a limited amount of data. Due to this, it is important to determine cache update strategies that are best suited for the business requirements. Following are the various caching strategies available:

1. **Cache-aside**: In this strategy, our application is responsible to write and read data from the storage. Cache interaction with the storage is not direct. Here, the application looks for an entry in the cache, if the result is not found, then the entry is fetched from the database and is added to the cache for further use. Memcached is an example of using this update strategy. Cache-aside strategy is also known as lazy loading because only the requested entry will be cached thereby avoiding unnecessary caching of the data.

Some of the disadvantages of this strategy are:
1. In cases of a cache miss, there would be a noticeable delay
2. The chances of data being stale are more if it is updated in the database. This can be reduced by defining the time-to-live parameter which forces an update of the cache entry.

2. **Write-through**: 


## Design Tic-Tac-Toe game.
Tic-tac-toe game involves two players where one player chooses 0 and the other player chooses X for marking the cells. The player who fills a row/column/diagonal with their selected character wins.

**What are some of the Required Features?**
1. Support 2 player game where one player can be a computer.
2. Design algorithm to calculate the win and loss results.
**What are some of the common problems encountered?**
1. What happens if both players play optimally?
2. How to decide the winning strategy?
**Possible tips for consideration:**
If one player is a computer, then make use of the rand() method for ensuring moves are completely random.


## Design a traffic control system.
Generally, in a traffic control system, we see that the lights transition from RED To GREEN, GREEN to ORANGE and then to RED.

**What are some of the Required Features?**
1. Transition traffic lights based on the conventions.
**What are some of the common problems encountered?**
1. Determine the time interval for which the state of the traffic lights has to change.
2. What happens in worst-case scenarios where the state is wrongly shown?
**Possible tips for consideration:**
1. Make use of state design patterns and scheduling algorithms for the transition of the state from one colour to another.

## Design Web Crawler.
The Web crawler is a search engine-related service like Google, DuckDuckGo and is used for indexing website contents over the Internet for making them available for every result.

**What are some of the Required Features?**
1. Design and develop a Scalable service for collecting information from the entire web and fetching millions of web documents.
2. Fresh data has to be fetched for every search query.
**What are some of the common problems encountered?**
1. How to handle the updates when users are typing very fast?
2. How to prioritize dynamically changing web pages?
**Possible tips for consideration:**
1. Look into URL Frontier Architecture for implementing this system.
2. Know how crawling is different from scraping.
   
## Design ATM system.
ATMs are used for depositing and withdrawing money from customers. It is also useful for checking the account balance.

**What are some of the required features?**
1. Each user should have at least one bank account that is linked to the card for performing transactions.
2. ATM to authenticate the user based on 4 digit PIN associated with the card.
3. User to perform only one transaction at a given time.
**What are some of the common problems encountered?**
1. What happens during transaction timeout?
2. What happens if the money is deducted from the bank account but the user hasn't received it from the machine?
**Possible tips for consideration:**
1. Divide the problem into different entities like Card, Card Reader etc and establish a relationship between each of the entities.


## Design Uber, Ola or Lyft type of systems.
These platforms help user request rides and the driver picks them up from the location and drop them at the destination selected by the user.
### What are some of the required features?
1. Real-time service for booking rides
2. Should have the capability of assigning rides that lets the user reach the destination fast.
3. Show the ETA (Estimated Time of Arrival) of the driver after booking the ride and once the ride has been started, show the ETA of the vehicle arriving at the destination.

### What are some of the common problems encountered?
1. How to store geographical locations for drivers always on move?
2. How to assign drivers to the customers efficiently?
3. How do you calculate the ETA of the driver arrival or the destination arrival?

### Possible tips for consideration:
1. Make use of the microservices concept with fast databases for booking rides faster.
2. Evaluate Dispatch System for assigning drivers to the users.

