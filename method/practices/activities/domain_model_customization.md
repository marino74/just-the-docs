---
layout: default
title: Domain Model Customization (activity)
nav_order: 2
parent: Service Landscape Design
grand_parent: Method
has_children: false
has_toc: false
---

# Domain Model Customization


| Task | Description |
|:--------------|:-------------------|
| **Customize BIAN Service Domain Model** | Customization of the reference model to the Financial Entity to reflect the different Business Models, Organizations, Products & Services, etc.  <br />  The customization involves the identification of new service domains not existing in the reference model, specialization of service domains (split the domain in several ones according to different capabilities supported), identification of domains with no relation with any existing application, regrouping of service domains into business domains which will describe the recommended changes in the IT organization. <br />  <br /> Sub-tasks:  <br /> * **Identify New Service Domains Identification.** Identify new service domains that do not exist in BIAN, rename service domains to the business language used in the Financial Entities. It is important to use always the business language of the entity and not to force new terms which will not be understood by the Financial Institution stakeholders. <br /> * **Split service domains to reflect specializations.** This is done when there are important functional differences or when there are different responsibilities within a Service Domain. The principle is not to have domains with more than one "owner", neither in IT nor in Business. Service domains are split to avoid such situations.
For example, "Position Management" specializations for "Refinancing Management" or "Management of Structured Loan Positions”. <br /> * **Identify service domains for which no application has been related.** These situations are carefully analyzed because it can be caused by an incorrect analysis (most banks will have capabilities in most of the BIAN domains) but also can lead to business opportunities. For example, “product matching” or “product training” are usually capabilities not provided by legacy systems. Developing such capabilities will be very valuable to the Financial Institution. The Gap Analysis help to identify potential business opportunities. The next diagram is an example of a gap analysis. Service Domains in green could not be mapped to any existing legacy application. Many of them were later identified as business opportunities. <br /> * **Re-grouping of Service Domains into Business Domains.** BIAN structures the service domains into Business Area and Business Domains. The first one represents the different steps in a value chain, and the second a grouping by responsibility. The grouping into functional domains must be changed to adapt the domain model to the responsibilities and organizational model within the Bank. This is very important. Otherwise, the business domain will not provide value further than from a communication or presentation purpose.  Our PoV is to use Business Domain to group together service domains that will share business language, Domain Experts and IT Teams responsible for the development, maintenance and evolution of the applications in the domain. This is a key driver for an institution to adopt Domain Driven Design practices. This outcome is one of the most valued by the customer we have worked with. The final result will provide recommendations on changes in the organizational model, and should be carried out maximizing the knowledge and experience of the different teams of the entity (grouping service domains around teams with the most appropriate skills and experiences for them) |


![Example of Service Domain split to reflect specialization of responsibilities](/assets/images/split_domains_example.png) 

![Example of Gap Analysis](/assets/images/gap_analysis_example.png) 