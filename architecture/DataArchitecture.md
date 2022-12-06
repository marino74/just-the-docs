---
layout: default
title: Data Architecture
has_children: false
nav_order: 5
# has_toc: false
parent: The Architecture
---

# Data Architecture

Traditionally, data architecture defines Enterprise-Wide canonical models and implements using shared databases and transform processes to move data between systems. Shared databases etc. are an underlying cause of hyper-integrated monoliths.

In a Hyper-Modular architecture there is no shared databases at all – each domain has its own private set of data.  IBM’s reference architecture for data and analytics provides for analysis of data in motion as well as data at rest and is oriented towards analytics and production of insights, it does not imply shared databases:


!["IBM Reference Data Architecture"](/assets/images/data_reference_architecture.png)

This reference architecture contains both different types of data stores and technical utilities. It should not be read as implying that there is only one instance of each – it is not a violation of the hyper-modularity principle to re-use technical utility services – only business-related logic and data must be strictly separated.

In practice, unless building an entire Hyper-Modular “Green Field” system, some compromises need to be made to allow co-existence 

There are several approaches to implement modular systems based on at what extent the modularity principle is applied not just to the code (microservices), but also to processes, business rules and data. On data we can see the following approaches:

 
!["Data in a modular architecture"](/assets/images/data_modular_architecture.png)

Pure Modular. This is preferred. The systems are modular also to the data level. This allows maximum modularity and new data models (unrestricted by the legacy). The ability to have new data models removes legacy constraints that may prevent new commercial offerings like bundling and cross-product discounting. However, co-existence can be complex as communication between legacy and new has different data models

Pseudo Modular. Modularity at the business logic level but monolithic at the data level. Usually reusing a legacy database. Does not allow a deep transformation (as the data model is still a monolith), the components are highly coupled to the data level but the coexistence with the legacy systems is much simpler. This is frequently the way tactical projects are implemented in-house (also known as the “lipstick on a pig” approach) – but is not a route to a Next Generation Architecture

Pseudo Modular with Data Replication. This is a tactical approach usually oriented to reduce resource consumption in the legacy backends (like MIPS in MF). Simple replication but frequently complex data replication problems.  This can be a route to Next Generation Architecture as the Distributed Backend replica can be decomposed and transformed over time.

Finally, a variant of Pseudo Modular is the one that use DB sharding for supporting massive data volumes (Pseudo Modular with Sharding):

 
!["Data sharding for massive volumes"](/assets/images/data_sharding.png)

The Pure Modular approach should be implemented for both Operational Data and Analytic Data: following the hyper-modular principle the domains are self-contained, including for all type of data. 

Operational Data can be supported by traditional SQL and NoSQL databases using different instances per module. 

The infrastructure for analytic data and its processing is based on at rest and in motion analytic and AI techniques and specialized data repositories, with zones for ingestion, landing, processing and consumption, following architectural models like the IBM reference architecture for data and analytics.



 

