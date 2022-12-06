---
layout: default
title: Platform  Architecture
has_children: false
nav_order: 7
# has_toc: false
parent: The Architecture
---

# Platform Architecture

## Platform overview

The overall platform is illustrated in the following diagram:


!["Platform architecture"](/assets/images/platform_architecture.png)


The cross-industry capabilities provided by the underlying technical platform needs to be complemented with specific banking capabilities: Banking Services Platform to support the banking industry specific requirements and hyper-modular approach.


## Banking Applications and Services

Support the banking business capabilities for Channels and Distribution, Production with a hyper-modular approach using in-house or commercial components or reuse of legacy banking applications. There will be a number of different channels to support – customers, bank staff, agents, eco-system partners, using multiple technologies.

Services to support the banking hyper-modular application development, that extends the pure technical platform services.

Transaction and consistency mechanisms (SAGA like) for an industry where consistency is crucial. Strict and eventual consistency. 

Engines to support the banking workloads on online traditional or FaaS and batch processing. Replacing batch with real time mechanisms based on Event Driven Architecture, data streaming and in memory DBS. 

Business application monitoring through all the layers. Security applied to financial services threats and regulations. 

Advance resiliency for the banking industry with HA/DR mechanism for a multi cloud hybrid environment.

Legacy coexistence services that manage data replications and services coexistence for master/slave models using the Legacy Integration Services

To support an eco-system there will be a number of applications:

* Publishing bank data and services to Open Banking, Fintechs etc.
* Consuming data and services from publicly available sources and partners
* Selling banking and other services via. Market place services

System development lifecycle has low code/no code facilities as well as a DevOps toolchain and AppOps, and will be designed to “hide” the platform complexity from the developer.

There are data and insight services:

* Data and analytics applied to the banking industry, built based on the foundational data & Ai capabilities provided by the underlying technical platform. 
* Analytics for risk management, compliance and regulation, fraud and security control. 
* Data privacy and confidentiality services. Consent management for third party and ecosystems integrations
* Banking customer customer behaviour analysis for prediction, next best actions and Intelligent Workflows. 
* AI applied to machine financial advisory for budget and investment management
* Tools for data engineering and data science – Ingestion, conforming, cataloguing, governance, data science and machine learning 

Integration is critical for a hyper-modular approach where the application modules are fully distributed. In addition to generic technical integration services there are banking specific services based on industry standards like BIAN provides BIAN oriented services and events on top of the technical integration services (APIs, EDA, Streams)

* API integration services – serving both internal and external interfaces 
* Event integration services – providing event queues, publish and subscriber mechanisms
* Data integration services exposing data as services or events
* Service mesh to further abstract the independent modules when they need to access services
* Transaction and consistency frameworks
* Co-existence integration to allow business applications to access legacy. Support for specific integration mechanisms with legacy systems (legacy communication and message protocols)
* Governance of this complex integration mechanisms thru API and events management tools. Making banking services consumable for the Banks and third parties
* Boundary services to support the hyper-modular principle. Physical barriers to prevent hyper connection (service mesh, network policies, K8s controls ,micro-gateways, etc)

The infrastructure platform is a managed Hybrid Cloud environment.


## Technical services

The platform has independent application modules, in accordance with the Hyper-Modularity principle, and shared technical services. As noted above it is not a violation of the hyper-modularity principle to re-use technical utility services – only business-related logic and data must be strictly separated. The technical services are mostly Open Source.


!["gateway technical services"](/assets/images/gateway_technical_services.png)


There is layer of technical services between the Channels and the Distribution systems. This provides:

* Identity and access management
* Backend for Frontend and API Gateways for the digital channels so that the self -contained business domain applications can be channel independent and omni-channel.
* Developer tooling to allow ecosystem partners such as Fintechs to create and test applications
* Document and file ingestion e.g. to take in loan applications from brokers
* A messaging gateway to receive and send SMS, email etc.
* Virtual AI agents supporting call centre and digital channels
* A co-existence gateway routing transactions to modernised applications or legacy



