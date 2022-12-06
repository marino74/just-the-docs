---
layout: default
title: Transformational Roadmap
has_children: false
nav_order: 80
# has_toc: false
---


# The Transformational Roadmap (HOW)

This document focusses on the specific issues in transforming incumbent banks. IBM has a number of tools and methods for transformation, these are discussed in another document as illustrated in the following diagram:


!["IBM Digital Core Systems Modernization Methodology v2.0"](/assets/images/transformation_method.png)


These methods and tools will of course be used in the transformation described here. 

A systems evolution for an incumbent bank has to be a gradual process that takes advantage of and leverages the current system capabilities and assets. Modernised and legacy systems will co-exist for a very long time. The transformation has to keep providing business outcomes to justify the investments.

Transformation is not just about the technical innovation adoption and evolution but also about the evolution of the whole Target Operating Model, which includes in addition to technology and architecture, organization and people, processes, partnership strategies or culture, and the capacity of the bank to absorb the change and manage the risk. 

## Planning the transformation
This transformation should be gradual, driven by business strategy and the cost/benefit case.

### Strategy definition

It is seldom possible to just build the target architecture and migrate data onto it. For an incumbent bank this would take years and only yield benefits after the migration. Banks usually have no appetite for business cases that only break even years down the line.

IBM can help a bit with financial engineering, but not enough to support a big bang approach. 
Banks usually want to save existing costs. They will not buy just on future cost-avoidance or revenue and customer experience uplifts – although they will want those too.

IT cost savings will not be sufficient, so business operational savings are needed too.

It is therefore necessary to create an incremental approach, prioritizing areas that can give savings in both business and IT, but converging on the target architecture, not just tactical initiatives. Areas with typically the most scope for delivering benefit from transformation will be prioritised – these will mainly target FTE reduction so will focus on areas with manual processes that can be automated. Banks typically have 3000-4000 FTE per $1bn revenue, labour costs distributed roughly as shown below:


!["Prioritising business benefits"](/assets/images/prioritization.png)
Source: APQC (American Productivity & Quality Center) Consumer banking benchmarking study December 14th 2015 



For a major transformation, the same type of data should be gathered from the bank. Then for each business area, an investigation can determine and agree the potential benefits that might be achieved by strategic initiatives. The following are illustrative examples:

1. **Customer Interaction**

The Customer Interaction area is people and business process heavy so can show substantial cost savings  through automation and changing the channel mix towards low cost digital channels.
 
!["Customer interaction savingst"](/assets/images/customer_interaction.png)



2. **Production**

The Production area is business process heavy so can show substantial cost savings through automation:
 
!["Production savings"](/assets/images/production_savings.png)


As well as Intelligent Workflows, Trade Finance would be a possible use case for Blockchain. The antiquated business processes of Letters Of Credit, Bills of Exchange, Bankers Acceptances, Time Drafts, Forfaiting etc. are all about brokering a trusted relationship between parties – which is Blockchain’s USP.

3. **Operations**

The Operations area is also business process heavy so can show substantial cost savings through automation:
 
!["Operations savings"](/assets/images/operations_savings.png)


4. **Business Development**

The Business Development area has relatively little saving potential except in campaign execution:
 
!["Business Development savings"](/assets/images/business_dev_savings.png)


5. **Accounting Risk and Control**

The Accounting, Control and Risk  area has relatively low staff costs but there are other significant benefits:

!["Accounting Control and Risk savings"](/assets/images/accounting_savings.png)


6. **Enterprise Services**

Back office services can benefit from process automation. IT can be totally transformed by the Next Generation Architecture DevOps and Hybrid Cloud:

!["Enterprise Services savings"](/assets/images/enterprise_services_savings.png)


###	Capabilities assessment

For each business area an assessment is carried out of the current maturity of IT support v business strategy and best practices as described in this Next Generation Architecture. The capability gaps are used to assess how much of the potential benefits identified could be realized by the strategic initiatives.  

Typically this uses Component Business Modelling to map out the areas and highlight the capability gaps and potential improvements.

In addition, the legacy systems catalogue is analysed to identify fit to business requirements, operational and technical risk as illustrated by this heatmap:

!["IT capabilities assessment"](/assets/images/it_capabilities_assessment.png)


IBM has a standard set of tooling for analysing legacy systems and assessing their cloud-readiness:
 
!["Analysis tooling"](/assets/images/analysis_tooling.png)


Based on this a preliminary disposition is identified for each – Retain, Retire, Re-Host, Replace, Refactor (This is preliminary as when the new development part of the Transformation is planned it may change the dispositions e.g. a system planned for Replace may be need to be Refactored as it will be required for some time before eventual Replace)


### Target operating model alignment

This step defines the changes required to the business operating model to support the desired business outcomes. 
The business model may change e.g.:

* A closed, vertically integrated bank to a partnership model
* Product silo organisations may be eliminated and replaced by customer segment centric. 
* Brand/ geography specific systems and organisations may be replaced by shared services.

Manual tasks may be eliminated by Intelligent Workflows e.g. Loan collateral documentation may be ingested and analysed by AI, with underwriters only seeing a precis. 

The delivery model of IT may be profoundly changed from in-house development and maintained systems running in a data centre to services consumed from an eco-system of cloud service providers.


###	IT architecture alignment

Based on the strategic initiatives, Target Operating Model and the capabilities assessment, a business and IT architecture and a first draft of the Transformation Programmes are created.

It should be noted that this architecture is not the ideal Target Architecture that would never be delivered – it is what can be realistically achieved with the timescale and business case that would be supported by the identified cost savings.  

It should be built to comply with the architecture principles laid out in this document, is very likely to have a scope that means that, in some areas of the business, existing systems will be retained in co-existence architecture.


### Cloud Migration Roadmap 

The existing application catalogue with preliminary dispositions can now be re-visited as there is now a top-down view of what has to happen to the systems as well as the bottom-up view:
 

!["Cloud Migration Roadmap planning"](/assets/images/cloud_migration_roadmap_planning.png)


Based on the prioritised business initiatives, a number of legacy systems will be replaced at a time, and a number of other legacy systems retained and integrated to the new in an interim architecture. Where possible, these will be migrated to hybrid cloud so they can fall under the same management as the new applications.

If they are containerisable (either as cloud native or containerized virtual machines they will be re-platformed). They may be refactored if they are expected to continue to exist for a time

As a last resort, if it is uneconomic to move them to cloud, they may be left on premises and integrated. It would be preferred that this is restricted to applications have little impact on the business transformation.

The projects to migrate to hybrid cloud are added to the list of business initiatives as input to transformation roadmap planning

### Transformation Roadmap 

The business initiatives will have business and technical dependencies which means if they were executed as single projects they wouldn’t deliver until too late, so they need to be subdivided into a number of short projects that deliver capabilities. 

Then milestones can be created to align these projects, as illustrated in the following example taken from a previous transformation plan:
 

!["Transformation planning dependencies"](/assets/images/transformation_dependencies.png)


In this case there were 16 business initiatives but dependencies necessitated the definition of 70 project milestones and bi-annual interim architectures. 

##	Transformation Approach

### As-Is situation before Transformation

Typically an incumbent bank will have a number of legacy systems of record that are monoliths i.e.:

1.	they do the core functions of a banking system – account maintenance, transaction processing, interest calculations, statements etc.
2.	they usually do more – user interaction, customer onboarding and servicing (as well as account), card management, product management, business processes, reporting
Generally they do a good job of 1 and a poor, inflexible job of 2. Because of this, and the opening of digital channels, the bank IT department will have created an integration layer and built systems of engagement to front-end the core(s). Unfortunately, in any bank that we are likely to be asked to transform, this will have not been done in a fashion that provides the flexibility needed e.g.:

* Integration will not have the appropriate level of abstraction
* The core will still be mastering data for customers, accounts and products and its data model restricting what can be done.

The objective of the transformation is to:
* Put in place the architectural construct described above, with modularity, separation of concerns etc.
* Move data and functionality where it belongs, so the core becomes only product processors and ledgers and the distribution layer manages customer interactions, product catalogue, customer data etc.

However this is a massive task and, as described above, has to be done incrementally and must generate business outcomes incrementally to support the investments as it proceeds. 

### The first phase of Transformation

The first phase needs to be a business-led initiative that both delivers some business benefit and establishes some of the architectural framework for subsequent phases. 

A typical interim architecture is illustrated below:

![" Interim architecture"](/assets/images/interim_architecture.png)

For example:
* It is decided that transforming loan origination will generate business Opex savings by automation and AI.
* At this stage legacy Core banking remains the master for account and payment processing, interest calculation, customer and account details 
* Channels will need to be able to access both the new loan origination and legacy account processing
* A new, more flexible product catalogue will support the selling and origination process
* Loan origination will be an “Intelligent Workflow” with AI based eligibility, document scanning, data ingestion, credit, fraud, anti-money laundering, credit checks, offers, collateral analysis 
* Loan origination will need to create accounts in Core banking
* Loan origination will need customer and account data from Core Banking
* Loan systems of record will manage collateral, commissions, documents etc.

The new systems, being built in accordance with the event-based architecture described in this document, would have no problem with having service and event interfaces to get the data they need and send the results to legacy. 

The mechanism for integrating with legacy will vary from one case to another – depending on the legacy technology, existing integrations, whether a non-intrusive approach is mandated by risk considerations etc. Techniques include CICS business event publishing, Change Data Capture, Enterprise Service Bus, zOS Connect, Data Integration Hub.

The solution will be built, not as stand-alone, but as “slices” of the target platform architecture as illustrated in the following diagram:

!["Example of initial partial deployment of the architecture"](/assets/images/interim_architecture_example.png)


### Subsequent phases

Each subsequent initiative will extend the footprint of the target architecture.

In the early phases the new Distribution and Production systems will replicate data from legacy systems of record, which remain the master. 

At some point, this can be reversed e.g. when a new CRM system is implemented it can become the master of customer data, much richer than the data before, with a subset replicated to the systems of record.

The legacy core can be incrementally reduced, moving to the distribution layer the data, functionality and processes that should be there (like everything related to Customer Management, Sales and Origination, Servicing etc.)

Once the core has been reduced to its proper size and perimeter the bank can decide if there is a business case to transform it, and if so, regardless the technical option, should evolve following the principle of extreme modularization.
