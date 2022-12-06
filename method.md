---
layout: default
title: NGA Method
has_children: true
nav_order: 40
has_toc: true
---

# NGA Methodology

The NGA Methodology is presented as a Delivery Capability Model, each delivery capabilty described through a Practice.

This is a work in progress to be completed through future collaborations:



| | Strategy & Roadmap | Design | Implementation | Deploy and Operate |
|:--------------|:-------------------|:-------|:---------------|:-------------------|
|Business       |  **[Service Landscape Design](method/practices/service_landscape_design.md)**   | **[Service Domain Design](method/practices/service_domains_design.md)** | | |
|Application    |  **[Analysis & Design Guidelines](method/practices/analysis_and_design_guidelines.md)**   | **[Service Domain Design](method/practices/service_domains_design.md)** | | |
|Data           |     | | ||
|Infrastructure |     | | ||
|Management     |     | | ||



* **[Service Landscape Design](method/practices/service_landscape_design.md)**. Design of the Target Domain Model (functional view of the target application architecture). Combination of top-down approach (analysis of business strategy) and botton-up (analysis of current applications and business processes). The target Domain Models will be based on the banking industry standard [BIAN](http://www.bian.org). This practice is usually included in Solution Outlines phases of delivery projects.

* **[Service Domain Design](method/practices/service_domains_design.md)**. This practice describes the activities, guidances, workproduct... to design service domains following Domain Driven Design and BIAN standard. This practice transforms business requirements into a technology-agnostic domain design that can later be implemenented using different technologies, but with the right caracteristics of modularity and integration patterns to be deployed in a hybrid multi-cloud. This practice is usually applied in Macro Design stages of Delivery phase.

* **Practice: Service Domain Detailed Design**. This practice transforms the service domain designs, which are technology-agnostic, into detailed designs for specific technologies that can be implemented and deployed. **This practice is PLANNED for future, not available yet**

* **[Analysis & Design Guidelines](method/practices/analysis_and_design_guidelines.md)**. This practice how tocreate guidelines for analysis and business architectures of the different domains to follow common rules and apply best practices. Actual designs should later be reviewed for compliance to such guidelines by the design authority or architecture board in charge of architecture compliance.


