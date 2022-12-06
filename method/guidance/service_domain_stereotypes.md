---
layout: default
title: Service Domain Stereotypes
has_children: false
nav_order: 10
has_toc: true
nav_exclude: false
parent: Guidance
grand_parent: Method
---

# Guidance - BIAN Functional Patterns and use of Service Domain Stereotypes

BIAN service landscape contains 400+ service domains (SD), but all them are classified in 24 functional patterns. This is very useful because it provides a clear understanding on the type of capability providad by the SD and also the opportunity to create repeteable design patterns and solution templates to accelerate and standardize the design effort, providing uniformity in the designs so that learning curves for new members of the design teams is much quicker as they will be familiar with the patterns used.

For example, a SD may have a "Process" functional patterns with means that the SD responsibility is to manage the execution of a process (i.e Account Receivable SD), while another SD with "analysis" functional pattern will have a very different type of responsility, such as analyzing the performance or behavior of some on-going activity or entity (for examples: Financial Market Analysis SD). 

The functional patterns in BIAN (v9) are:

| Create | Initiate | Register | Evaluate | Provide |
|:--------------------|:---------------------------|:------|:------|:------|
| Direct  <br/> manage <br/> Administer <br/> Operate <br/> Process  |  Design <br/> Develop <br/> Assess <br/> Maintain | Track <br/> Monitor <br/> Analyze | Agree Terms <br/> Enroll <br/> Allocate <br/> Catalog | Advise <br/> Transact <br/> Fullfil |

Descriptions of the patterns can be found [here](https://bian.org/servicelandscape-9-0/views/view_164141.html)


We find the functional pattern for the BIAN service domain in the SD Overview Diagram. The following picture is an example:

![example of SD overview diagram in BIAN](assets/images/example_sd_overview_diagram.png)


With every SD with the same functional pattern having a similar type of responsibility, we can create design templates for the functional patterns and the designers will only have to extend and customize the template. This can be done for designs, but also for implementation, testing, etc. We call **Service Domains Sterotypes** to such templates.

To simplify, instead of creating one sterdotype per functional pattern we use 4 stereotypes as a basis, but aditional ones can be created for the project.

A service domain should have only one Functional Pattern and an Stereotype. If describing an SD requires more than one, then spliting the SD in different smaller SD should be considered. Typical Stereotypes are:

- Registry or Repository
- Assessment
- Process
- Accounting Unit
- Tracking

The following table advises on which stereotype to use for each BIAN Functional Pattern. The structure of the cells in the table is **Functional Pattern: Recommended Stereotype**

| Create | Initiate | Register | Evaluate | Provide |
|:--------------------|:---------------------------|:------|:------|:------|
| **Direct**: Process |  **Design**: Process | **Track**: Tracking | **Agree Terms**: Process | **Advise** (not used in BIAN) |
| **Manage** : Process |  **Develop**: Process | **Monitor**: Tracking | **Enroll**: Process | **Transact**: Process |
| **Administer**: Process | **Assess**: Assessment | **Analyze**: Assessment | **Allocate**: Ledger | **Fullfil**: Process |
| **Operate**: Process |  **Maintain**: Process |  | **Catalog**: Registry | |
| **Process**: Process |   | |  | |


To understand the stereotypes, you first need to get some knowledge on the standard used to document them, which is described in the [Metamodel](model_metamodel.md)


## [Registry or Directory](stereotypes/directory_stereotype.md)

This type of services store inventories of business objects. Business Objects are classified and grouped, although the logic for the classification and grouping can be external to the SD. The registry is maintained through API and subcriptions to events published by other services.

The registry is exposed through API to external consumers. It is a principle that an enquire to the registy will never require the registry to access other services to complement the response. For example, a product registry will provide the product information where enquired without accessing any other service domains. 

Examples are: Party Directory, Product Directory, Customer Profile, Customer Credit Rating, Customer Products and Services, Fixed Assets Registry...

## [Assessment](stereotypes/assessment_stereotype.md)

The assessment stereotype evaluates or calculate assessments. Assessment services receives a request, gather additional data required for the assessment algorithms, apply the algorithms and calculate the results. 

Assessment can be automatically calculated, human performed or a combination of both. Assessment are great candidates to be evolved to use AI, and it is a good practice to record the entire assessment (request, data, results) so that machine learning algorithms can be created and fed.

Assessments are calculated by applying policies (or business rules). Such policies/ ules have to be created and administered. This can be done as part of the service or in a separate service. Policy evaluation can be a human task or an automated tasks implemented on different technologies from programmed logic, rules engines, up to AI services.

## [Process](stereotypes/process_stereotype.md)

Process-type services orchestrates from business process. Process can be complex or simple, and can be long-term (different activities by different roles and at different moment of time) or short-term.

## [Accounting Unit (incl. Product Ledger)](stereotypes/accouting_unit_stereotype.md)

The Accounting Unit type of service is used to keep track and monitor both monetary and non-monetary standings. 

## [Tracking](stereotypes/tracking_stereotype.md)

Tracking-type services monitor and define the status/rating of some entity, or maintain a log of transactions or activity, typically a financial account/journal or a log of activity to support behavioral analysis. 
