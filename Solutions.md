---
layout: default
title: IBM Solutions in Financial Services
has_children: false
nav_order: 97
parent: The Architecture
# has_toc: false
---


# IBM Solutions in Financial Services

## Hybrid cloud and Cloud Paks
To enable Hybrid Cloud to be managed as one system, IBM will always use Red Hat OpenShift Container Platform, and Cloud Paks as shown in the following diagrams:
 

!["Hybrid Cloud"](/assets/images/hybrid_cloud.png)


Red Hat Kubevirt allows legacy applications that cannot be containerised to nevertheless be orchestrated together with Cloud Native applications. The infrastructure platform is hybrid cloud, managed by Red Hat with the technical services supported by Cloud Paks:
 
!["Infrastructure platform"](/assets/images/infrastructure_platform.png)


* OpenShift and  CLOUDFORMS manage the Hybrid Cloud
* Ansible provides automation of provisioning, configuration and deployment
* FS Workbench provides low code/no code microservice development with many pre-created patterns and integrations

Cloud Pak for Data includes:
* IBM Cloud Pak for Data control plane
* Watson Machine Learning
* Watson OpenScale
* Waston Studio (Local)
* Analytics Engine for Apache Spark
* IBM Streams
* Cognos Dashboard Embedded
* Watson Knowledge Catalog
* Data Refinery
* Information Governance Catalog
* Information Analyzer
* Data Virtualization
* IBM Db2 Event Store
* IBM Db2 Warehouse
* IBM Performance Server
* Master Data Connect
* DB2 Big SQL
* Guardium (Integration component  only)
* Watson Machine Learning Accelerator

Add-ons to Cloud Pak for data include:

* Watson Assistant
    * Watson Assistant for Voice Interaction 
* Watson Discovery
* Watson API Kit
    * Watson Knowledge Studio
    * Watson Natural Language Understanding
    * Watson Speech to text
    * Watson Text to speech
* Watson Studio (Premium)
    * Decision Optimization
    * Execution Engine for Apache Hadoop
    * SPSS® Modeler
* Watson Financial Crimes Insights
* Financial Services Workbench
* Anaconda Repository with IBM
* CockroachDB
* Datameer
* Informix
* Cognos Analytics
* IBM Db2 Advanced Edition
* DataStage Edition
* Information Server
* Planning Analytics
* Master Data Management

Cloud Pak for integration includes:

* IBM Cloud Pak for Integration Platform
* IBM App Connect Enterprise
* IBM API Connect
* IBM MQ Advanced
* IBM Event Streams
* IBM Aspera
* IBM Datapower Gateway
* IBM Storage Suite for Cloud Paks
* Confluent Platform

Cloud Pak for automation includes:

* Business Automation Content Analyzer 
* Business Automation Insights
* Business Automation Application Designer & Studio
* Business Automation Navigator
* Automation Digital Worker 
* Automation Workstream Services
* FileNet Content Manager
* Operational Decision Manager
* Business Automation Workflow
* Datacap
* Enterprise Records
* Content Collector for Email, File Servers, SharePoint and SAP

Cloud Pak for Security includes:

* IBM Cloud Pak for Security Core Platform
* Guardium Insights
* Data Security Hub
* Data Explorer
* Cases
* Threat Intelligence Data Insights
* Security Advisor Adapter
* Connectors
* SOAR Capability - Security Orchestration Automation and Response (Resilient)
* QRadar Security Intelligence Platform

##	IBM Financial Services Workbench

 
!["Financial Services Workbenchitle"](/assets/images/fsw.png)

Financial Services Workbench is a low-code tool for building and deploying applications. It has industry templates that can be used in the Solution Designer to create Domain Designs, these can then be run through the Solution Hub which has pre-integrated development tooling and then deployed and run using Solution Envoy.

There is a library of industry standard templates (based on BIAN or IBM IFW) as shown the following diagram:
 
!["Industry standard models to create solution templates"](/assets/images/fsw_templates.png)

The Solution Designer then uses these standard templates, customises then and generates microservices code. 
The Solution Hub manages asset repositories, and builds, packages, tests and deploys microservices and their associated Docker images, Helm Charts etc.
Solution Envoy provisions the services the new application needs, and provides runtime and monitoring services
Financial Services Workbench is an add-on to Cloud Pak for Data running on RH OCP, and uses that as its platform.


## Information Framework (IFW)

IFW is part of IBM Industry Models for Financial Services. It provides a comprehensive set of data models that contain data warehouse design models, business terminology model and analysis templates to accelerate the implementation. IFW also provide best practice business process models with supportive service definitions


##	IBM Financial Services Public Cloud

IBM has developed the necessary policies and controls to allow deployment of Banking systems on Public Cloud:
 
!["Financial Services-Ready Public Cloud"](/assets/images/fss_cloud.png)


This solution maintains acceptable level of controls by:
•	Isolation
•	Visibility & Audibility
•	Data Location
•	Customer key management

It ensures security of transactions by:
•	Encryption and Keys
•	Detection, prevention and remediation of unauthorized access
•	Notification

For each regulatory regime IBM’s regulatory consultancy Promontory will provide documented compliance:
•	Understanding the regulations
•	Provide policies to comply with the regulations
•	Adapt to regulatory changes

A number of ISVs have joined/are joining the eco-system on Financial Services Cloud:
 
!["ISVs on FS Cloud"](/assets/images/isv_fss_cloud.png)



##	Input Management

IBM Input Management is a secure, IBM Cloud based solution to digitize and analyze incoming data like mail, letters or ongoing messaging data and existing archives of old documents. It was developed for the Insurance industry, but would be equally applicable in banking:
 
!["Input Management System"](/assets/images/input_management.png)

Image Processing
* Image preprocessing
* Image correction / refinement

PROSAR
* OCR based on neural networks
* OCR for machine printing and forms-based handwriting

PROSAR-AIDA
* Artificial Intelligence for Document Analysis
* Trained classification
* Data extraction
* Creates structured data
* Supervised feedback

PROKEY
* Professional Keying from Image
* Smart validation
* User interface (GUI)

Data Enrichment
* Filtering
* Conversion into different result formats

Free-form document processing, regardless of layout or “partner-specific” design features
* Classification of document type
* document type detection as a basis for initiating business processes
* automatic document separation (i.e. detecting start page and subsequent pages)

* Detection of header and footer data / index data
    * e.g.: account number, final billing amount, supplier number
    * data relevant to processing and meta-data for archiving
* Detection of line items
    * e.g.: billing items
    * basis for auditing, payments and data mining
    * Data currently manually partially not extracted because of cost associated with manual data entry

IBMs cognitive technologies provide capabilities which cover all use cases of Input Management:

 
!["AI enabled document processing"](/assets/images/ia_enabled_document_processing.png)
 

## Safer Payments

IBM Safer Payments is a market leading omni-channel fraud detection platform that uses AI to create new models that detect fraud in real time with minimal false positives.
 
!["Safer Payments"](/assets/images/safer_payments.png)


## Trusteer

Through cloud-based intelligence, backed by AI and patented machine learning, Trusteer provides a holistic approach to identifying new and existing customers, without negatively impacting user experience. 

Over 500 leading organizations rely on Trusteer to help enable and secure their customers’ digital journey and support business growth. In doing so, Trusteer runs over 40 billion application accesses monthly and over 1 billion monthly user sessions.

 !["IBM Trusteer"](/assets/images/trusteer.png)
 

## Financial Crime Insights

IBM has an AI solution for financial crime like money laundering. It is a few years old and is no longer market leading – SMEs recommend third party solutions NICE Actimize or ComplyAdvantage.

##	Data Protection and Data Monetisation
There is enormous value in the huge volumes of financial transaction data, for example Mastercard makes more profit by selling marketing insights to Merchants than it does by processing payment transactions.

However, there are strict regulatory constraints on the use of data, particularly Personally Identifiable Information. Data protection legislation such as GDPR has strict rules and crippling penalties for non-compliance. 

Data protection also applies to the use of production data for testing. IBM practice is to use tools like Optim to mask identifiers. This is not sufficient protection for all circumstances, data may still be identifiable to an individual.

To explain, supposing there is a dataset of 1000 people, with the identifiers masked. Suppose that attribute A has ten possible values. Then, assuming relatively even distribution, there will be an average of 100 people with each value (being 1000 people divided by 10 equivalence classes), so no individual is likely to be identifiable from their value of A. Now supposing there are three such attributes A, B and C – then there are 10x10x10 equivalence classes so there is near certainty that an individual could be identified by their value of the (A,B,C) tuple.

This gross over-simplification indicates the problem – for data to be rich enough to be of value, its richness destroys anonymity and exposes regulatory risk. It not just personal data – BMW found that with all the optional extras, people could be identified by their car even without the vehicle identifiers.

IBM Research has expertise and tooling for anonymising data while retaining value. Contacts:

| Name                | Email                     |
|:--------------------|:--------------------------|
|Tamas Visegrady      | tvi@zurich.ibm.com        |
|Axel Tanner          | axs@zurich.ibm.com        | 
|Stefano Germin       | stefano.germin@ch.ibm.com |
|Marco Brenner        | marco.brenner@ch.ibm.com  |
|Michael Osborne      | osb@zurich.ibm.com        |

