---
layout: default
title: Analysis & Design Guidelines
has_children: true
nav_order: 2
parent: NGA Method
has_toc: true
---

# Analysis & Design Guidelines (Practice)


Before going into proper design of the domains, create guidelines for analysis and business architectures of the different domains to follow common rules and apply best practices. Actual designs should later be reviewed for compliance to such guidelines by the design authority or architecture board in charge of architecture compliance. 


| Task | Description |
|:--------------|:-------------------|
| **Define Service Domain Specification Metamodel**. | Develop a common metamodel to document the designs of the domains, so that every team or squad create designs following the same metamodel, and any external stakeholder can understand the designs done by the different squads. If using BIAN and DDD, elements in the metamodel can be Service Domain, Service Area, Control Record, Aggregate, Command, API, Business Event, etc. |
| **Define Service Domain Stereotypes.** | To scale in the delivery, improving the development and design efficiency, and the learning curve of the teams, create [Stereotypes](../guidance/service_domain_stereotypes.md) for the Service Doamins. Typical Stereotypes are: <br /> - Registry or Repository <br /> - Assessment <br /> - Log <br /> - Fulfillment <br /> <br /> Two service domains with the same stereotype will have similar structures. Solution Templates can be developed for each sterotype to accelerate and standardize the designs.|
| **Define Integration Patterns** | Complex banking systems developed for Hybrid Cloud are built on hyper-modular components with high operational modularity. This requires to limit the run-time synchronnous integrations between services and favour asyncronous, event driven integration. As part of the design process, dependencies between services are identified and integrations patterns are selected according to the NFR for the service domains.|
| **Define Coexistence Patterns and Usage Guidance** | | 
| **Define Guidelines for Security Policies Specifications** |  | 
| **Define Guidelines for Event Driven Architecture** |  | 
| **Define API specification guidelines** |  | 
| **Define Guidelines for Aggregates Specification** |  |
| **Define Guidelines for Business Process Management / Case Management Specification** |  |
| **Define Guidelines for use of Business Rules Specification** |  |
| **Define guidelines for specification of Multi-language requirements** |  |
| **Define guidelines for specification of Multi-entity requirements** |  | 
| **Define guidelines for reference data usage and specification** <br /> | | 

**Guidance**

* [Guidance: Service Domains Specification Metamodel for Domain Driven Design](../guidance/model_metamodel.md)
* [Guidance: Specification of Stereotypes for Service Domains](../guidance/service_domain_stereotypes.md)
* [Guidance: BPM, BAM, CM and BRMS Guidance for Hybrid Cloud Solutions](assets/documents/bpm_guidance.doc)
* [Guidance: API Specification Guidance](assets/documents/api_guidance.doc)
* [Guidance: Mainframe Integration Guidance](assets/documents/mainframe_integration_guidance.doc)
* [Guidance: Event Driven Architecture Guidance](assets/documents/event_driven_architecture_guidance.doc)
* Guidance: Multi-language Specification Guidance **(PENDING)**
* Guidance: Multi-entity Specification Guidance **(PENDING)**
* Guidance: Reference Data Management Guidance **(PENDING)**
* [Guidance: Integration Patterns and Specification Guidance](guidance/integration_patterns.md)

* Security Policy Management and Specification Guidance **(PENDING)**
* [Tool Mentor: Design Service Domains in Archimate](assets/documents/domain_models_specification_with_archimate_tool_guidance.docx)

