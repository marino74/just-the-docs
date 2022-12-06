---
layout: default
title: Architectural Principles
has_children: false
nav_order: 1
# has_toc: false
parent: The Architecture
---

# Architectural Principles
The Architectural Principles are guidelines and rules that drive the systems design, development and management for realizing the business. 

The next figure shows the key principles guiding the Next Generation Architecture: 
 

!["NGA Core Principles"](/assets/images/Principles.png)


## Modularity 

Usually, the legacy information systems in banks are monoliths, or set of monoliths, without a clear differentiation of the modules that support the business functions. The applications are very poorly structured and componentized, overlapping or having functional gaps not covered by any of them. 

!["Hyper-integrated legacy"](/assets/images/Spaghetti_2.png)


This lack of modularity causes an uncontrolled integration among the banking applications without clear interfaces at any of the main application layers: data logic, business logic and presentation logic, which has produced extremely complex systems that are very difficult to maintain, run and evolve.

Uncontrolled functionality integration means a “Services mess” – it is very difficult to, for example, create Application Programme Interfaces.

Uncontrolled data integration creates a “Data Monolith” – with shared databases components have interdependencies, there is a performance bottleneck and there can be conflicting versions of the “truth”
Uncontrolled transaction propagation creates “Massive Glue” – again complex dependencies, performance issues and complex error handling.

Hyper-integration is also a root cause of unstable runtime systems: as everything is connected with everything (and interfaces are neither formalized nor identified) runtime problems can produce cascade effects in the whole system leading to full outages or even systems melt down. Even planned maintenances are much riskier on systems that lack modularity like many of the banking systems.

In this scenario, it is extremely difficult to understand the system and modify the code. Even minor changes often need complex and large regression tests to understand the side effects in the whole system. No one in the bank knows exactly the interfaces of a specific module with the rest of the system.

The next generation banking systems need to be built on a key design principle: Modularity, being also an underlying principle for other design principles like Cloud Ready.

This is a paradigm shift: **from Hyper-Connectivity to Hyper-Modularity**. 

!["From hyper-connectivity to hyper-modularity"](/assets/images/Spaghetty_To_Modular.png)

 

##	Separation of concerns

Applications are structured in 6 independent business capabilities with strict separation of concerns.  This provides business flexibility in playing different roles, supporting multiple brands/geographies etc. It also provides flexibility in transformation from legacy to modernized. Changes in one area have little or no impact on other areas. This simplifies development and test – improving time to market, IT productivity and risk reduction. However the integration layers between areas can impose a performance overhead compared to, for example, a front end system calling a back end database directly. Architectural techniques such as caching, eventual consistence may be needed.
 
!["Separation of Concerns"](/assets/images/Separaton_Concerns.png)


* Channels interact with customers, staff, brokers, financial advisors, fintechs and other partners. 
* Distribution provides the functions to sell and service products
* Production manages the products and accounts 
* Business development manages marketing, partnerships, product development
* Finance and Risk management controls accounting, risk and compliance
* Business Infrastructure provides support functions – HR, IT, facilities etc.


##	Vendor Agnostic

Vendor agnostic prevents the lock in that monolithic systems have created in the past and allows the best available solutions on the market to be used. However there is a danger that mixed solutions will not work well together or it may take a lot of time and effort to integrate them. This is mitigated by the use of pre-bundled open source software in IBM Cloud Paks and the hybrid cloud management capability of Red Hat OCP.

Applications can be developed as microservice components, can be consumed as Software as a Service, or can include ISV components as long as they comply with the modularity requirement i.e. they must do only one function, work independently and interact only via API.

System software will typically be open source e.g. databases, middleware, development tools. They will need to be certified and cloud native – and many are provided in this form as IBM Cloud Paks.

Infrastructure as a Service can be hybrid, from multiple cloud suppliers and virtualised legacy systems. To manage from a single control plane, the architecture will include Red Hat Openshift Container Platform


##	AI By Design

AI is necessary to provide automation with Intelligent workflows which can have productivity improvements of the order of 80% when automating an entire business function. 

Up until recently in banking use of AI has been mainly limited to virtual call centre agents, agent assistance etc. There are much more fruitful areas which include:

* **Document digitalization and analysis** – it is possible to train AI to understand the structure of scanned documents and extract structured data from them. For example, analysing a bank statement requires understanding that the columns are dates, descriptions, credits, debits and a running balance, and that the rows represent transactions. AI can be trained to process unstructured and semi-structured documents and identify salient facts – so for example it could analyse title deeds and leases and identify adverse clauses such as Chancel Repair Liability.

* **Recommendations and offers** – can be targeted by individual profiling

* **Controls** – such as KYC, Anti-Money Laundering, Anti-Bribery and Corruption, FATCA, PEP etc. These can be more complex than simple checks, e.g. investigating the Ultimate Beneficial Owner of a company in a complex structure.

**Credit checking, underwriting, application fraud monitoring, post transaction fraud monitoring** – all can use AI solutions.

However, AI is only as good as the data, so data governance and data quality management must prioritized to get reliable results. Also transparency must be provided to ensure trust in AI based decisions.


##	Customer Centric

Banks are traditionally product and account centric in product silos, but they don’t make their money from liability products – they need to be able to cross-sell. Customer Centric is necessary to provide good customer service, bundle products to increase revenue, reduce churn and to make relevant recommendations.

**Systems of engagement** need to have access to all relevant information about a customer even though they may have different accounts and products in different systems

**Controls** must have access to all relevant information about a customer for KYC, Anti-Money Laundering, Anti-Bribery and Corruption, FATCA, PEP etc.

**Credit check, Underwriting, Fraud Monitoring etc.** need access to all relevant information about a customer.

Providing 360o view of customer will improve Net Promoter Score, reduce churn, reduce financial crime and increase revenue generating products per customer. However, the data from various systems may be inconsistent. Master data management will be required with sophisticated techniques for matching and de-duplication.

Consent management and access controls will be required to comply with Data Protection legislation 


##	Reduced cost and time for change

With DevOps Continuous Integration/ Continuous Deployment modules can be tested and deployed in hours/days – improving time to market, IT productivity and risk reduction.

* Centered around secure coding practices, our DevSecOps Garage Method will create write once deploy many code
* Using the standard Garage Method, applications will be designed, developed, built, tested and deployed using fully automated processes
* Continuous improvements are built into the method, with post implementation monitoring and alerting allowing a full and repeatable application lifecycle

##	Hybrid Cloud oriented

Banks want to take advantage of hybrid cloud to:

* avoid capital investment in infrastructure and data centre facilities
* avoid technical debt and obsolescence 
* have elastic capacity on demand
* will provide flexibility to deploy in the most appropriate environments – based on policy (such as data sensitivity), performance (such as latency) and lastly price (the most economic platform that satisfies the policy and performance criteria.
* Hybrid cloud will also allow access to a wider range of services from different cloud providers

However, they face obstacles in migration to cloud:

* Traditional legacy systems in incumbent banks are often monoliths with internal uncontrolled integration that are not possible to deploy in any form of cloud delivery model (private on-prem, public, hybrid). To take full advantage of the cloud benefits the monolithic systems have to be deconstructed and refactored into the business (Distribution, Production) and technical domains (engagement, record, insight) that are described in the following chapters. Without following this process monolithic legacy systems cannot be moved to a cloud delivery model. 
* Non- monolithic legacy systems may not be containerisable as they are not abstracted from the technology 
Interim architectures may combine new cloud native developments and existing systems which may not be able to be containerised. The use of Red Hat Kubevirt will allow virtual machines to participate in containerized workflows. New developments will be created as Cloud Native.

## Secure and regulatory compliant

Banks have relatively few production workloads on public cloud because of the need for regulatory approval and data protection. Security is a much more complex element in the new hyper modular hybrid systems than in the legacy monoliths where the banking systems are protected with a clear border as there is no integrations with other platforms but the bank on-oprem one. Now the system is built out of components that can be deployed on-prem and off-prem, built in house, based on commercial and open-source applications or even consumed as SaaS. This creates new challenges and needs of protection in: 

* Identification and authentication. The new banking systems are the result of the bank, partners and ecosystems capabilities integration. The ecosystems in turn can be composed of thousands of participants interacting among them and the bank. This requires reinforcing the identification and authentication mechanism in the bank systems and the platforms it owns. 
* Communications and networking. Moving from monoliths to highly distributed modular systems means many more systems components and an exponential growth in integrations among those components. Protecting the information at motion that is interchanged as services, events or data streams among remote components is a new dimension of the systems’ security. 
* Data. Data is no longer hosted only on the on-prem bank systems; it is actually distributed along the bank hybrid platforms requiring therefore high data protection mechanisms like data encryption and clear mechanisms to protect the data ownership when is shared with others into platforms. 
* Homomorphic Encryption allows one to perform operations on encrypted data without decrypting it first. The result of the computation is in an encrypted form, when decrypted the output is the same as if the operations had been performed on the unencrypted data. This allows a Data Processor to host and manage data on behalf of a Data Controller (i.e. the Bank) without having any access to the content.
* Platform security. The banking systems sits now on top of a much complex stack like including clusters and virtualization that makes more complex to protect the systems. New security elements to the virtualization, containers and clusters levels are required in addition.

## Eco-system enabled

Being Eco-system enabled allows the bank to operate in different business models, to offer services to third parties and consume services from third parties.

A key trend in banking (as in most of the industries) is the transformation of the traditional integrated business models to business platforms on its various flavours (factories, distributors, marketplaces, etc) which are closely linked to the Cloud delivery model. To create any kind of platform it is essential to create a clear separation between Distribution and Production (refers to Functional Architecture), which is required not only by the market forces but also by new regulations (PSD2 and Open Banking in Europe), and secondly at the application structure level with a clear modular approach.

### The bank as a publisher of services:

Banks have little choice as Open Banking legislation spreads, so must try and turn this to their advantage by finding different business models for accessing a more open, less captive audience .

### The bank as a consumer:

Banks will increasing rely on external data sources and externally provided IT services. The richness of data available greatly enhances the effectiveness of AI, Insights and standard processes such as Anti-Money Laundering.

There is no reason why generic banking functions should be in-house developed when they are available as a Service

### The bank as a business platform:

Banks should not be just participants in ecosystems (either as a publisher or consumer) but they should also create platforms (financial or cross-industry) that they can manage and control. 

The winners in the platform business models are those that create and manage the platform. In the case of banks they can include financial products and services into third party ecosystems. 

The platform owner can also manage and participate in the interactions happening in the platform among participants and monetize the huge amount of data that flows through and is created in the platform. Monetising data in a regulatory and data protection environment requires controls e.g. consent management, anonymization – an IBM solution is discussed in Part 2 

Some financial institutions are creating industry specific platforms, like in the agricultural sector, to support the full value chain and serving all its participants, not just the farmers with the traditional financial products (e.g. loans) but also farm equipment vendors, seeds and fertilizers producers, crop health services etc. 

To attract participants to the ecosystem the platform offers freemium services like weather prediction, markets information, analytical and predictive services, etc. This is the case of Baroda Bank in India (Baroda Kisan) and BCC in Spain (Plataforma Tierra, https://www.plataformatierra.es/)


## Future Proof

The system can’t become the next obsolete legacy system to handicap the bank in a few years, particularly as it will have cost a great deal and taken a lot of time to build. That means it must comply with the principles above:

* Be built from independent modules allows components to be replaced without impacting the rest
* Be vendor agnostic allowing replacement when what was “best of breed’ is no longer the best solution available
* Use hybrid cloud to give flexibility to deploy wherever satisfies policy, performance and price requirements
* Be eco-system enabled to allow external services to be consumed and applications composed rather than coded. It must be able to accommodate future business models
