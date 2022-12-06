---
layout: default
title: Create Disposition Rules
has_children: false
nav_order: 10
has_toc: false
nav_exclude: true
parent: Guidance
grand_parent: Method
---

# Guidance: Create Disposition Rules

Disposition rules provides recommendations on what disposition pattern to follow for each of the legacy applications. 

Different set of disposition patterns within IBM can be found depending on the source. It is important to differentiate technical programs with business transformation programs. The first ones are IT driven and has a strong focus on reducing TCO by moving workloads out of Mainframe. The business transformation are business driven and aims to provide business value, generally decreasing operation cost, reducing time to market of new products and increasing revenue though better customer experience and better sales and service digital capabilities.

We are barely interested in the technical initiatives as they are well addressed by other offerings in IBM. Also, most of them rarely get budget because miss the business value and the business organizations are not happy to take risks for no value only to decrease their IT Cost.

Business Trasnformations, however, would provide significant business cases and will address business pain points; this will justify the investements.

When looking at Trasnformation to Cloud initiatives to typical dispositions patterns are:


| Disposition Pattern	| Description | Modernization Patterns |
|:--------------------|:---------------------------|:---------------------------|
| Retain | No major changes to existing applications have to be done. But in some cases due to the refactor of other SPI Groups, it could be necessary to include some changes.	| |
| Refactor | Improve the technical or functional characteristic without a technology change. The application is decomponentized to a higher degree and some components may even be replaced or rewriten in different technical platforms but most of the application remanins un touched and there won´t be mayor data migrations | API Enable <br /> Componentize <br /> Cloud Native |
| Re-Architecture (Modernize) |Re-design the existing applications to cloud, including business process re-invention | Cloud Native  <br /> COTS / SaaS |
| Rationalize (Consolidate) | Migrate the functionality to another solution in the bank to create enterprise or business unit wide capabilities <br /> Requires a consolidation decision: which is the target solution? Does the target solution require transformation? | |
| Retire | Application is decommissioned due to lack of use or purpose | |
| Re-platform | Moving applications to the cloud without major changes, but taking advantage of benefits of the cloud environment. | |
| Replace | Replace with and ISV or SaaS | |



## Dimensions for decisions

* **Key Imperative for the Domain** Describes the primary (albeit non unique) objectives of the domain and what should be the used of the allocated budget. For example, customer services would focus on providing the best customer experience while payment processing would aim to maximum efficiency

    | Values | Description |
    |:--------------------|:---------------------------|
    | Customer | The primary objectives of applications supporting the domain would be to provide the best customer or user experience |
    | User Experience | The primary objectives of applications supporting the domain would be the cost efficiency |
    | Efficiency | The primary objectives of applications supporting the domain would be the cost efficiency |
    | Compliance | The primary objectives of applications supporting the domain would be assurance of compliance regulations |
    | Business Agility | The primary objectives of applications supporting the domain would be the time to market for new products and services or new product/services features |

* **Total Cost of Ownership (TCO)** Cost of application management: infrastructure cost + application management cost. Dimension Values:

    | Values | Description |
    |:--------------------|:---------------------------|
	| Low |  The TCO is below average in the Portfolio of applications |
    | Medium | The TCO is around average in the Portfolio of applications |
    | High |  The TCO is about average in the Portfolio of applications |
    
	
* **Business Value** Classification of the Business Application in terms of their importance in the Strategic objectives and achieving of the strategy and imperatives of the bank or bank unit. Dimension Values:

    | Values | Description |
    |:--------------------|:---------------------------|
	| Strategic Capability | They are applications providing differentating capabilities, for example a product matching application |
    | Utility |	Application not providing actual busines capabilities but only technical of fucntional services to other applications, for example a loging or a referenca data application |
	| Commodity	| Applications providing business capabililities which are not differentiating for the Bank, for example a payment order application |

* **Transformation Value** Classification of the application in terms on the impact in the Business Transformation Startegy. This dimension only applies in Business Transformation Scenarios and not in simple cost reduction scenarios. It measures whether an application is important to fulfill the business strategy and how far it is to support them. For example, an application supporting business processes in branches will be probably far from been able to support digital processes and, in consequence, may require to be completely changed rather than modernized. Dimension Values:

    | Values | Description |
    |:--------------------|:---------------------------|
	| N/A |  The application is not relevant in the transformation |
    | Low Gap | The application is relevant and require minor changes (below 20% of functions impacted) |
    | Medium Gap | The application is relevant and require minor changes (20%-50% of functions impacted) |
    | Large Gap | The application is relevant and require mayor changes (above 50% of functions impacted) |

* **Capability Scope** Classification of the application according to the reusability of their business capabilities. For example, a "Customer Profile" application would provide enterprise-wide capabilites supporting any kind of product or service, while a "Card Authorization" will provide capabilities with much narrower scope, such as Card Products. Dimension Values:

    | Values | Description |
    |:--------------------|:---------------------------|
	| Enterprise Wide |  The application provide capabilities that can be shared accross all products and services, for example, a customer profiling, a product catalogue, a product potfolio analysis... |
    | Business Domain Wide | The application provide capabilities that can be shared accross all products and services of an specific domains (i.e. Credits), for example: risk anaysis, credit underwriting... but not to other products or services on other Business Domains |
    | Product Wide | The application provide capabilities only related to a specific product, for example: Card Authorization, Investment Account, Tax Payment... but not to other products or services |

The Disposition rules are based in classifications of the application based in business and technical dimensions. Following are the recommended one to use:

* **Size** Size of the application or component. Size is usually meassured in LOC (Lines of Code), which can be adjusted when dealing with applications in different technologies or lenguages. In each situation is important to have a "sizing" approach that allows to compare of applications independently of the their technology.
  
    | Values | Description |
    |:--------------------|:---------------------------|
	| Small |  The size is below 30% of the average size in the portfolio of applications |
    | Medium | The size is between 30%-70% of the average size in the portfolio of applications |
    | Large |  The size is above 70% of the average size in the portfolio of applications |
    

* **Internal Coupling** An estimation of the level of dependencies among components in the same application. 

    | Values | Description |
    |:--------------------|:---------------------------|
	| Small |  The number of internal interfaces is below 10% of total software elements of the application(programs, classess, .... depending on the technology) |
    | Medium | The number of internal interfaces is between 10%-30% of total software elements of the application |
    | Large |   The number of internal interfaces is above 30% of total software elements of the application |
    

* **External Coupling** An estimation of the level of dependencies with other applications. 

    | Values | Description |
    |:--------------------|:---------------------------|
	| Small |  The number of external interfaces is below 5% of total software elements of the application(programs, classess, .... depending on the technology) |
    | Medium | The number of external interfaces is between 5%-15% of total software elements of the application |
    | Large |   The number of external interfaces is above 15% of total software elements of the application |
    

* **Allignment Open Standards** The application follows open standard or deviate from them. For example applications developed in Cobol, or java, versus application developed on proprietary lenguages. Also, usage or dependencies with proprietary middleware, libraries... is considered deviation from open standard.

    | Values | Description |
    |:--------------------|:---------------------------|
	| Small |  More than 20% of software elements are not considered to follow open standards |
    | Medium | 5% -20% of software elements are not considered to follow open standards |
    | Large |  Less than 5% of software element are not considered to follow open standards |

   
* **Complexity** It meassures how easy or difficult is to understand and reproduce the code. This is usually provided by the code analysis tools using standard metrics.


## Technical versus Business Disposition recommendations.

Disposition recommendations can be provided from a pure technical perspective or from business perspective. The experience says that they rarely match. The technical disposition will usually advise the most efficient way to drive TCO down, but they do noot necessary help to achieve the business objectives.

For example, applications loosely coupled and not complex are nice candidates, from a technical point of view to be migrated to cloud. However, these applications may not provide strategic capabilities to business or they may not have a high TCO and, in consequence, from a business point of view, should be retained and not rearchitecture (as suggested by technical analysis).

In the other side, complex applications supporting the core processes are usually also strongly coupled. Moving them to cloud require costly and very risky projects for limited TCO benefits, and are usually recommended to be retained in the current platform, when only technical dimensions are considered. However, doing so may not address the business objectives to provide digitalization, better time to market or reduction of operational cost by reducing the FTE required to work in the business processes. From a business point of view, they should be reinvented, with means rearchitectured.

In this guidence we are providing recommendations for business driven transformation and not technical ones, which are already covered in other transformation to cloud method.

## Disposition Rules (Business driven)

The disposition rules should be adjusted for each customer, but the following guidelines are recommended:

Basic Rules:

| TCO | Strategic Value | Capability Scope | Recommendation |
|:--------------------|:-------|:-------|:-------|
| Low  | Low  |  |  Retain | 
| Medium <br/> High   | Low  |  |  Refactor  <br/> Re-architect <br/> Replace (1) | 
|  | Medium <br/> High  | Product-wide  |  Refactor  <br/> Re-architect <br/> Replace (1) | 
|  | Medium <br/> High  | Enterprise-wide <br/> Domain-wide | Rationalize | 

(1) additional rules:

| Business Value | Imperative | Recommendation |
|:------------|:--------|:------- |
| Strategic Value | Customer / User Experience <br/> (systems of engagement) | Re-Architect |
| Strategic Value | Others | Refactor |
| Commodity <br/> Utility |  | Replace |



The Dispositions Patterns can include not only "what to do", but also, "how to do". For example, there are different approaches to "Refactor" from simply enabling some APIs or solving some technical debt, to a full decomposition with some components completely refurbished to cloud, when the capability they provide are extensive on business logic, or whether the technical dimensions determine that it is cheaper to develop this new on cloud. 

Large applications should be decomposed into smaller applicaton components and dipositions decided to a component level. For example, a loan application may support "loan origination" process and also "loan agreement administration" in a single monolith. This application should be handled as separated components (origination and administration) and each component would probably have different dispositions (re-archietcture vs. refactor/replace in most of the cases).

This fine grain rules should be refined for each project.
