---
layout: default
title: Business Process Architecture
has_children: false
nav_order: 4
# has_toc: false
parent: The Architecture
---

# Business Process Architecture

Business benefits must be realised in large enough quantity and quickly enough to justify the investment in transformation The IT savings from having more agile and easily maintained systems come later. The early paybacks can only come from business operational cost savings by automating manually intensive business processes.  The aim is to create Intelligent Workflows i.e. AI supported at each stage, with very little human intervention.


## Example Intelligent Workflow

An illustrative example of such a workflow is mapped out in the following diagram:

!["Intelligent Workflow"](/assets/images/iw_example.png)

This process imagines a personal customer application for a residential mortgage:

1. The customer will provide the usual documents to support an application e.g. passport or driving licence, proofs of residence like utility bills, payslips, bank statements etc. This may be done online by the customer scanning the documents, or via a broker or branch.
2. The document images are processed by Optical Character Recognition technology. 
3. Various checks are carried out – Id, residence, KYC, AML, credit
4. An offer is created.
5. Offers can be digitally accepted. In the UK at least, witnessed “wet signatures” are required on title deeds 
6. Documents such as title deeds and lease agreements are submitted in support of the application
7. Accounts are set up, settlements made and collateral perfected to register a lien 

Much of these processes can be AI supported to reduce manual work as illustrated here:

!["AI support for business process"](/assets/images/ia_support_business_process.png)


1. If the customer is self-servicing online to submit the application, then AI support can coach the customer by checking that the required information is in good order, capturing external data to supplement and cross check. The aim would be to increase the take up of low-cost digital channels by providing a well guided experience and to reduce the number of applications that need correction and further input.
2. The document images are processed by Optical Character Recognition technology. State of the art AI enabled input management is capable of ingesting text from semi-structured documents in typeface or handwriting. The system has to have the intelligence to understand the structure of the document – what is a name, what is an address, what is a date of birth, what is the date of a transaction, which collection of attributes make up a transaction. AI is capable of facial recognition to determine whether the applicant’s documents match other sources – see Hooyu.com for an example of  KYC
3. AI can also carry out the other types of checks such as AML and Fraud using both the data provided on the application and other publically available data. It can determine what products are eligible and suitable. In straightforward cases this would not need human intervention. The system can determine whether there are issues.
4. AI can analyse documents e.g. title deeds and lease agreements and identify any red flags, for example, issues that require indemnity insurance
5. The collateral management process can be automated, both the original valuation and scheduled reviews.
6. Overall risk and credit management can be AI supported


##	Technical implementation

In the Hyper-Modular architecture recommended there is no overarching Business Process engine spanning across modules and managing state as this would re-create the coupling we are trying to avoid. 
Instead of this each module includes its own business process, and the scope of a module is to manage the interaction until some logical end. 


!["Business processes in self-contained domains"](/assets/images/bp_in_selfcontained_domains.png)

In the illustrative example above, one module could handle the capture of a loan application through to the creation of an offer. Another second could manage the onboarding of the customer and a third module could manage underwriting. In this case the reasons for deciding to make it multiple modules might be:

* The modules align to BIAN service domains
* The modules may be implemented differently in practice – they may use commercially available solutions – or in an interim architecture part of the process would be new development and part supported by existing systems
* The customer might be an existing customer not requiring onboarding

In a microservices architecture a long running business process like this that includes multiple updating processes is a SAGA.  

Each independent process does its own updates but must then generate a response – either a success or a failure – so that other processes can take appropriate action.
There are two alternative patterns:

* Choreography – which is a chain where each process in turn acts and informs its successors via events
* Orchestration – where a master process triggers and receives responses and decides what to do next

Which pattern to use in any circumstance depends on the nature of the system in question, the types of exception conditions and remedial actions. Orchestration smacks of “the monolith fights back” but exception handling logic can get very complex in Choreography if there are multiple issues, or in an intermediate architecture the modules may be called by an existing system like CRM.

In general, the preferred approach is a Choreography of independent modules that run a long running process in the Distribution areas and send update commands to Production systems as illustrated:
 
!["Long running business process"](/assets/images/long_running_bp.png)



 

