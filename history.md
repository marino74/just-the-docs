---
layout: default
title: NGA History
# has_children: true
nav_order: 60
---
# History of Next Generation Banking Architecture

## What's new on v3

- More structured architectural (business and technical) content following the IBM Method (new artifacts included):  
  * Overview and Scope: Business Challenge, System Context
  * Requirements: NFRs, Use case (example)
  * Architectural Principles
  * Architectural Overview: Service, Enterprise (BIAN oriented) & IT Views, Usage Scenarios
  * Architectural Decisions
  * Component Model: Static View (Ref. Arch), Sequence and Collaboration Views (examples)
  * Operating Model: Logical Operating Model
  * RAID: Risks, Assumptions, Issues, Dependencies

- Decomposition Model (BIAN+DDD) method: Formalized thru an IBM AoT Study. Helps on decoupling the monolith identifying the new components starting with BIAN as a reference and canonical model

- NGA Japanese version

## What's new on v2

This document is an evolution of the Next Generation Banking Architecture (NGA) document produced some years ago by the GBS Banking & Financial Markets CoC. 
NGA 1.0 concentrated on two main points:
1.	A modular architecture – with the business logic, business process and data for each functional domain encapsulated in an independent module communicating only services and events
2.	BIAN alignment – so that the domain modules and the services they expose and consume follow strict industry standards, enabling the use of compliant third-party services and components

This architecture has been used successfully for some years, and the two principles mentioned above are still hold true as they provide great flexibility and agility. 

However, some considerations have arisen with experience and much more detail has been understood since. These are addressed in this document – the main topics being as follows:

###	Hybrid Cloud
With the acquisition of Red Hat in 2019, Hybrid Cloud has become the strategic focus of IBM. 
NGA 1.0 said little beyond being cloud oriented but didn’t address some of the issues this raises.  In particular the fact that cloud is a poor platform for heavily batch oriented Core Banking systems because their shared databases and vertically scaled batch processing does not match the horizontally scaled distributed processing cloud model.  The solution of modularising core also requires parallel near real time transaction processing rather than overnight batch runs.

###	Business cases and incremental development
A complete transformation of an incumbent bank to this architecture is a multi-year programme requiring a substantial investment. A purely technical approach would generate IT savings towards the end of the programme which would not support the investment case. It will therefore be necessary to have an approach that transforms business domains, prioritised to deliver business operational savings so the programme can pay for itself, but in a manner that builds compliant to the architecture not creating more complexity. 
This also implies co-existence of modernised systems and legacy for a period of years, and therefore there may be cloud migration of legacy as well as deployment of new cloud-native developments.

### Intelligent workflows
Automation will be needed to generate the business operational savings. This means AI driven low touch/no touch end to end processes.  Within a functional domain, the business process can be encapsulated as part of a module and orchestrated by middleware. However, some long running processes will span multiple domains, and it is anti-pattern to have a overall orchestration as this breaks the independence of the domains. There will therefore be an Event Driven Architecture so that domains remain un-coupled. There has been experience of what patterns are recommended and how these should be implemented. 
### Transactionality and consistency
The cloud-based distributed data and processing model poses technical challenges with data consistency. The usual microservices approach of eventual consistency works for some areas in banking such as business process automation, but not where, for example, funds are transferred as a transaction could “see” funds leaving one account but not arriving in the destination (yet).
### Platform architecture
The Domain-Driven independent business modules need to reside in a platform that provides all of the technical services they require so that they are abstracted from the underlying technologies.

