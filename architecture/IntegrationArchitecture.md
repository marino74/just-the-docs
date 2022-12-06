---
layout: default
title: Integration Architecture
has_children: false
nav_order: 6
# has_toc: false
parent: The Architecture
---

# Integration Architecture

##	Types of integration

The following diagram illustrates the types of integration:


!["Integration architecture"](/assets/images/integration_architecture.png)


The integration methods are:
* Event and data streaming with publish and subscribe – where modules are “unaware” of each other
* Rest services – where modules only “know” of the existence of services they can call
* Co-existence services that integrate to legacy by whatever technologies legacy can support

To protect modules from unauthorised access there are a number of possible means:
 
!["Isolation of modules"](/assets/images/isolation_of_modules.png)


###	Event Driven Architecture 

An event driven architecture enables the independence of modules. Modules are not aware of each other, they respond to events and create events as illustrated in the following diagram:
 

!["Event Driven Architecture"](/assets/images/event_driven_architecture.png)

1.	An event source – e.g. an API call creates an event
2.	The event joins a queue and is consumed by the appropriate function
3.	The function is carried out and creates a response event
4.	The events are processed by cognitive streaming analytics
5.	Events are persisted in an event store
6.	Cloud native applications respond to and create events
7.	Machine learning analyses events, trains models which support cognitive analytics

Event streams are a key data source for Machine Learning. Data at rest classifies entities, events give patterns of behaviour:

!["Machine Learning from Event Streams"](/assets/images/matching_learning_event_streaming.png)


To support long running processes and provide auditability and recovery from failure without data loss an immutable, ordered queue of events is created. Example: an event is created, like a loan application, it goes through a number of actions like KYC, credit check and comes to a point of commitment:

 
!["Long running transactions in Event Driven Architecture"](/assets/images/long_running_transaction_event_architecture.png)


If the action from the commitment failed, e.g. by a Pod going down, when a new Pod is automatically created it can replay from the checkpoint. When a long running transaction involves multiple updating processes a coordinating pattern is needed with exception processing. 


### Data Consistency

To preserve the independence of hyper-modularity there is no transactional propagation between modules. In the architecture data updating is asynchronous and distributed which means that ACID transactions can only take place within a module, not across multiple modules as only two of these three conditions can be true at the same time (CAP Theorem):

* **Consistency**: all database clients will read the same value for the same query, even given concurrent updates

* **Availability**: All database clients will always be able to read and write data.

* **Partition tolerance**: The database can be split into multiple machines and it can continue functioning in the face of network segmentation breaks.

In addition to this constraint, there is the issue that microservices can use different database technologies suited to their use case e.g. NoSQL – many of which do not support the traditional two phase commit approach to updates.

Therefore in a hyper-modular system, where the components are self-contained (with different technologies), low-coupled and run normally distributed in a cloud native environment, strict distributed transactionality (Two Phase Commit) is not recommended and even not possible for clusterised platforms like Kubernetes and should be replaced by other mechanisms that provide eventual consistency, like the SAGA patterns, when a semantic transaction (business events that should comprise a unit of work) is required. 

Consistency can be managed with different approaches: 


**1. Technical Transactionality**

!["Technical transactionality"](/assets/images/technical_transactionality.png)

Technical transactionality is an attempt to extend the transaction boundary to include more than one microservice.  This is anti-pattern and should not be used.

Traditionally there was a trend to overuse technical transactions even not strictly required as was a “cheap” resource omnipresent in the transactional monitors. 

New systems should be designed taking into account that distributed transactions are not possible in most cases in cloud deployments. With Domain Driven Design, by correctly modularising, it is possible to reduce the need for transactions to span multiple modules.

Integration that is required should be supported, whenever possible, using asynchronous mechanisms that ensure the messages delivery and with processes for error recovery. If a business unit of work is needed then one of the following mechanisms should be selected. 


**2. SAGA/TCC**

!["SAGA pattern"](/assets/images/saga_pattern.png)

In a SAGA pattern each microservice manages only its own database and communicates only by events or services. This is a recommended approach.

SAGA design patterns are well documented and used on microservices developments, based on choreography or orchestration to ensure that the unit of work is eventually consistent across the involved microservices and data.

In a choreography pattern the microservices are unaware of each other, they just respond to their standard event and services interfaces. This is the ideal pattern for preserving the independence of modules, but error condition processing can be complex.

Using SAGAs does have an impact on business logic development as most of the engines requires to participants to be idempotent and compensable, which requires an extra effort in application development. 

Additionally, the SAGAs do not cover the Isolation of the “ACID” models i.e. they cannot guarantee that there will be no other updates before the unit of work is complete.

To achieve isolation an additional algorithm, like TCC (Try-Confirm-Cancel) is required. 

Another consideration with SAGAs is that the consistency mechanisms (the dialogue between the participants, the manager and the “transactional log”) creates some overhead in the business service execution that can lead to latencies that may not be acceptable for very high workloads. 

SAGA can be implemented in-house, but that is not recommended as very complex algorithms may be needed to handle complex error situations in any part of the system (participants, communications, manager, log implementation, etc).  Therefore it is highly recommended to use an opensource or commercial framework, like Narayana as part of Camel (that in turn can be used as RedHat Fuse distribution), Apache Service Comb Pak, Axon, etc. 


**3. Common Ledger**
 
!["Common Ledger pattern"](/assets/images/common_ledger_pattern.png)


In a common ledger pattern the modules are designed so that financial transactions are sent to a microservice that handles the “double entry” book-keeping, thus making the transaction Atomic (i.e. it all happened or it all didn’t happen). 

This pattern is a recommended one for this type of transfer of funds. 

In the example above, of a loan settlement or disbursement, the loan microservice processes the contract conditions and calculates the funds that need to be transferred, calls a service on the current account microservice to ensure all is well, then sends both a debit and credit to the position keeping service, which updates both the loan account and current account balances.

The disadvantage is that the common ledger couples the two domains to some extent, but this position keeping is an accepted concept in BIAN.

This pattern has the major advantage of immediate consistency – which resolves the eventual consistence issue of a “snap-shot” transaction finding that money has left one account and not arrived anywhere (yet) – which would otherwise need an additional mechanism to see the “in-flight” transfer.

Also, in an intermediate architecture, where both new developments and legacy co-exist, it is quite likely that the book-keeping is all in one system.


**4. Transactional Islands**
 
!["Transactional Islands"](/assets/images/transactional_island_pattern.png)

In this approach we assume that we will use, for the more transactional parts of the system, traditional transactional monitors, like Java EE, where the components, even with a good level of modularization, run in a monolith or in different processes but under a traditional two phase commit protocol like, for instance, Java Transaction API implemented with EJBs in Java EE. 
This approach provides strict transactional support managed by the monitor but is not appropriate for modular distributed systems with a cloud native architectural style.
It may occur as a temporary solution while new microservice developments co-exist with legacy, but it is anti-pattern.


**5. Adaptive**

!["Adaptive pattern"](/assets/images/adaptive_pattern.png)

The adaptive pattern is designed for extreme performance situations. 

Microservices are developed independently as usual and can be deployed independently as usual if Non-functional requirements allow.

However, as stated above, the SAGA pattern algorithms create an overhead as result of the integration protocol that can lead to higher latencies that are unacceptable for very high throughput scenarios. In such a case the deployment process groups the functionality in just one deployment unit running under the same process.

 In cases of core systems with a massive number of customers and very high throughput requirements the DB is can be partitioned using sharding techniques. 


### Command Query Responsibility Separation

 
!["Command Query Responsibility Separation"](/assets/images/cprs.png)

Each module has its own data store with the data relevant to its own function. If the module needs to update some data it does not own it issues a command event. The module responsible for that data will subscribe to that event and carry out the transaction. 

If a module needs data that it does not own, it can issue a query. This may be an API call, which exposes the appropriate service from a module or legacy. 

A module can also subscribe to events that notify it of changes in data that it does not own but is of impact to it.

In co-existence, when there are both new modules and legacy systems of record, the commands that need to update legacy will integrate with legacy by whatever technology its interface supports. For queries, both master data and transaction data may be replicated from legacy and a module handles the queries on behalf of legacy for performance.


### Real Time Processing

Legacy banking systems traditionally have heavy batch processing. These processes are typically scheduled overnight to avoid conflict with online transactions. Batch processing typically is only vertically scalable and therefore creates a peak of system resource load e.g. MIPs on a mainframe (which tends to be a sore point with banks IT budgets). Batch does not take advantage well of the elastic horizontal scalability of Cloud.
The alternative to these processes would be reactive, near real time architectures where information is processed as it happens and the end of day/ end of month processing are avoided or reduced. 
There are also business requirements driving the move to real time:

* Payment transactions and their fraud monitoring are already real time, in funds transfer Real Time Gross Settlement has been taking over from overnight net settlement for some years. Where banks are going next is RTGS for equities and bonds, non-securities like Foreign Exchange and Over the Counter trading. This improves the efficiency of intra-day liquidity management etc.

* Real time analytics enable insights and intelligent workflows
We have identified different batch processing patterns and we propose some solutions that making use of event streaming mechanisms would minimize overnight processes.
 

!["Application to application real time "](/assets/images/a2a_realtime_pattern.png)


Batch Processes are used to exchange data between applications. Customer information, accounts and financial transactions are, at the end of the day, downloaded and stored in master files, and made available to other applications. These processes can be substituted by each of the sources publishing events when new operations occur or relevant information changes, and application services that subscribe to those events, assembles and stores these inputs, and produces the required output when needed. 
 

!["Real time "month end" processing"](/assets/images/rt_endmonth_process.png)


Batch processing is also typically used in bulk processes handling huge amount of data such as day-end, month-end and year-end processes. These processes can be redesigned to take advantages of micro-batching to parallelize execution and event streaming to process individually and produce the information near real time. Using event streaming the execution does not need to happen overnight, but during the day when there is low system resources load.  
 

!["Real time feed for analytics"](/assets/images/real_time_feed_pattern.png)


The other heavy batch workload is transferring data from operational to informational systems. Again, using event driven mechanisms has the advantage of allowing Near Real Time streaming analytics.
Moving from batch processing to event-based processing allows taking advantage of Hybrid cloud. Rather than a single big workload absorbing the main resources e.g. The core banking system, the processing is done by many parallel microservices distributed across the cloud infrastructure with the workload deployed to not conflict with transaction processing.
Near real time processing has clear advantages for the business. Not only customers benefit from immediate information but all bank statements: marketing and commercial departments, treasury, risk and fraud, etc. Near real time processing improve agility of front and back office processes and facilitate the bank's decision-making. 
