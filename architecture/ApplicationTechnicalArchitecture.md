---
layout: default
title: Application Technical Architecture
has_children: false
nav_order: 3
parent: The Architecture
# has_toc: false
---

# Application Technical Architecture


##	Strict Modularity


!["Strict Modularityle"](/assets/images/strict_modularity.png)


Strict Modularity (or componentization) means to build systems with the following features: 
* The system applications are structured as modules, following a de-facto standard like BIAN.
* Each Module encapsulates its business processes (intelligent workflows), business logic, data and AI logic, exposing a service and event interfaces to collaborate with other Modules in the system.
* No access is allowed to the Module functionality except through the formal Module Interface.
* The Interfaces are implemented following market standards, like BIAN, which can be extended with commercial standards like the IBM Banking Models (IFW), with a loosely coupling approach based on APIs (usually REST) and events.
* Transactional propagation among Modules is not allowed. 

This Modularity principle is represented in the next figure:

!["Modularity"](/assets/images/modularity.png)


In this picture the module encapsulates programmatic logic, for instance implemented with Java microservices style, but declarative logic as well, like process logic or rules logic running on engines that allow very fast response to the business requests. Additional logic like cognitive processing can be considered as part of the module to implement intelligent business logic (for instance, ML for predicting customer credit risk) or support intelligent workflows. The Module is the basic building block or construct used to create complex systems. 
The internal components are integrated but the interfaces between them cannot be accessed externally.
The module also owns and hides the data model (SQL or NoSQL) that contains its business data. This data can be only accessed through the formal Module interfaces, both online API Rest or event oriented, or by batch and data streaming interfaces for massive loading or off-loading. 
There’s a strict interface that expose the Module functionality for external collaboration, under different paradigms like synchronous API REST interfaces or asynchronous loosely coupled event interfaces. 


!["Module anatomy"](/assets/images/module_anatomy.png)
Figure 20. Module anatomy

The Modularity does have several dimensions that are crucial for an agile modular system:

* **Structural Modularization**. The system is composed of modules, each one with a clear responsibility and interface. The system is structured as a set of collaborating Modules in a loosely coupled way.  Each module knows no detail about the other module’s internal implementation style or deployment. This allows polyglot systems as each module is implemented with the architectural style, programing language and middleware that best fits its purpose. 

* **Development Modularity**. The strict encapsulation and interface allow very loosely coupled design and development lifecycles, extremely useful for agile development techniques. Different development teams only need to agree the public interfaces which allows independent development and deployment cycles. The intra-module architectural style can allow for much more granular development lifecycles, like in the microservices architecture. 

* **Operational Modularity**. Each module is operated independently of other modules (independent operational lifecycle), running on different and isolated runtime environments (depending on the implementation technology). This allows independent maintenance activities (only limited by interface dependencies, which can be in turn limited depending on the runtime style – as using some patterns like circuit-breakers in microservices) and avoids cascade systems fails, outages and ultimately system meltdown.

* **Governance Modularity**. The module is self-governed in alignment with the general IT Governance. Some development and runtime activities used to be concentrated on specific subsystems and organizations, like SOA and API Management on shared middleware managed by cross-organizational units, leading to organizational and operational bottlenecks (e.g. a unified services team centralizing services deployment). In some cases, the middleware can allow some level of governance delegation in the Modules’ teams as, for instance, with some commercial API managers that support multiple service catalogues.


A strict modular approach (Hyper-Modular) is key for making the solution agile, flexible, ready for the cloud and ready for the future. It will have the characteristics described in the follow image.

![Modularity Independence featuresle"](/assets/images/modularity_independence.png)

A strict modularized (Hyper-Modular) approach to systems design has the following advantages:
* Lower maintenance and evolution costs. Since the development of each module is very isolated and the inter-module interfaces are clearly defined, much less regression testing is needed. 
* Much faster response to the business needs. This is related to the previous point. A modular system with clear separation of responsibilities and with loosely coupled integration will result in much faster identification of needed functionality changes along with much quicker regression testing. 
* System robustness. Module fencing and isolation helps to prevent failure cascade propagation. 
* Polyglot systems. Each module can be developed with the architectural style and technology that best fits its business purpose. Each module can be developed in-house or supported on a commercial component, either on premise or in a SaaS model. 
* Future proof. Modules can be renewed or replaced by new technologies with low impact on the rest of the system. Technical obsolescence can be managed easily as a technological replacement only impacts the specific module.
* Modularity is a key condition in moving workloads to the cloud. The lack of modularity will prevent the cloud journey which in banking usually starts with on-premise private cloud, but which usually evolves to hybrid cloud models.  
* Strict modularization allows a hybrid sourcing model for the bank capabilities as the banking system can be built out of commercial or open sources components that can be bought or consumed as SaaS or built in house when a high differentiation deserve the effort and investment to create the module.


!["Hybrid sourcing model"](/assets/images/hybrid_source_model.png) 

* Hyper-modularity is a key element to support two other fundamental architectural principles in the Next Generation Architecture: Cloud and Ecosystem orientation. Both are essential elements for the design of the new banking systems. 

To determine the scope of a module and its deployment involves a number of factors as illustrated in the following diagram:
 
!["Determination of scope a deployment of a module"](/assets/images/scope_of_deployment.png)

There is a top-down decomposition of BIAN Service domains and other industry models – it is important that the chosen scope fits inside one domain so that it can be industry compliant. 

The process of Domain Driven Design identifies the business process, data entities and events that the module should support

There is then the consideration of data entities being clustered into coherent groupings so that they can be consistently managed by a single domain. In particular, as discussed in section 3.6.3Data Consistency, it is not possible to have ACID (atomic, consistent, isolated and durable) transactions that cross domain boundaries. It is sometimes necessary to provide a transaction that updates two things (such as a transfer of funds from one account to another) and it is required that:

* both the debit and credit must happen or, in an error condition, neither is committed
* that no transaction can “see” a state where only one of the updates has happened
* no intervening transaction can create an update that invalidates the transaction
* in the event of a failure either both of the debit and credit have been stored or the whole transaction was not carried out

In these circumstances the whole transaction must fall withing a single module’s transaction boundary

There may be considerations of legacy – particularly if there is co-existence of new developments and legacy they need common objects to interface

Non-Functional Requirements may affect the design. e.g.
* The need for very high performance may drive the combination of two logical domains to eliminate the overheads of loosely coupled integration 
* High performance may need distributed parallel processing e.g. to replace batch processing a number of transactions may be parallel pre-processed in real time, or performing analytics on large volumes of data 
* Commercially available software or service may provide part of a solution

The deployment of the sub-components onto infrastructure is determined by the NFRs and the technologies used – some can run in Kubernetes managed containers, some may not, such as Oracle RAC.


## The new system model

!["Technical architecture: component model"](/assets/images/technical_architecture_component_model.png)


The new technical model is built out of independent self-contained components with explicit and strict interfaces connected through an intelligent integration fabric (“motherboard”)

This technical architecture implements the main technical principles.
 

### Separation of Concerns


!["Separation of concerns"](/assets/images/separation_technical_concerns.png)

Systems and applications must be separated in different modules with specific responsibilities. That separation can be based in functional responsibilities, as the separation from production and distribution domains, or for technical responsibilities, as the separation between, business logic, data access, presentation logic, integration logic, etc.

This leads to structurimg the system into the following domains:

1.	SoR: Contains business logic and data access logic related to production and operations processes (like product processors or GL)
2.	SoE Distribution layer: Contains business logic and data access logic related to distribution processes (like product origination).
3.	SoE Channels & APIs: Provides user interaction, screen and user navigation, for all the business processes. Also provides public APIs to third parties. Only contain channel related data, as user personalization’s, etc…

## Ecosystem Centric

In the new digital economy an easy integration of partners is a key capability. Partners can be used to enrich the bank’s capabilities in any domain, from user interaction, customer facing added value services, or SoR new capabilities where the integration can be based in new Distributed Leger Technologies. The integration of partners requires very clearly designed interfaces, as APIs, or stream data publishing, with high levels of security and operational monitorization. The next generation banking architecture is a Platform-Native system, and not just ready to be part of platforms and ecosystems. It is conceptualized as having a “Platform DNA” as strictly modular and connected to the integration fabric / motherboard which allows easy capabilities extensions.  

!["Platform oriented architecture"](/assets/images/platform_oriented_architecture.png)


Banks are on a migration path towards a platform model, as illustrated in the following:

!["Evolution of banks business model"](/assets/images/evolution_business_models.png)


For most banks Open Banking regulation drove the first step away from a largely vertically integrated business model. They also are starting to integrate third party products into their offerings e.g. insurance
When they are fully a platform it will be possible for the bank and its partners to collaborate on the joint manufacture of offerings, customer experiences and distribution models

## AI by Design and Client Centric

Artificial intelligence, systems that learn automatically from experience, are going to have a critical role to optimize customer interactions, business processes, operations, etc. Any module should be prepared to integrate learning capabilities (“intelligence by design”) with two approaches: “data goes to intelligence” as a traditional model where data us extracted from the operational sources and analysed into lakes; “intelligence goes to data” where AI algorithms are embedded into operational processes to achieve real time intelligent processing.

AI is pervasive, in real time for data in motion and at rest. It is embedded on all the domains processes to create Intelligent Workflows
Data is massively processed by per-domain Data and Insight Fabrics
AI and data insight enables an advanced customer experience on a Client Centric design
 
!["AI by design and client oriented architecture"](/assets/images/ai_by_design.png)


## Cloud Oriented

The future banking architectures will be completely Hybrid models with components running on and off-prem; private, public or public dedicated; SaaS, PaaS or IaaS.
All the new developments should be cloud native, ready to be deployed in the cloud.
These applies specially for all the modules that belong to the Channel and Distribution domain, because the pressure to develop differentiating capabilities for the bank falls in these layers, so is where the agility provided by the cloud and DevOps is crucial. 
The functionality running into the deep layers of the banking system - product processors in the Production domain that, for technical and NFRs reasons, are deployed on traditional transactional monitors – will need to be re-architected to be capable of taking advantage of cloud. 
The cloud model is large numbers of small modules, running in parallel, distributed across infrastructure and horizontally scalable. Legacy core banking systems are monoliths, with shared databases, extensive batch processing and are vertically scalable. They therefore should be modularized, with distributed processing and minimal batch to have cloud-like capabilities. These technical changes are discussed in section 3.6 Integration Architecture.
 