---
layout: default
title: Business Architecture
has_children: false
nav_order: 2
# has_toc: false
parent: The Architecture
---

# Functional Architectural

Banks can play multiple roles in the ecosystem.  They can, for example, have one vertically integrated brand, and process transactions on behalf of another distributor. For example HSBC UK does this for Marks and Spencer Bank. To achieve this with a single system stack needs separation of concerns between distribution and production.
The next picture describes European Banking Association & Innopay´s view of different business models that Financial Institutions may adopt, including traditional models where the institution processes, sales and serve their own banking products to new business models, such as Distributor, where they only play a role in the value chain, for example distributing external products (processed by other financial institutions), or Producer Model, when a bank specialized in processing the products, that are sold and served from other financial and, even non-financial institution
 
!["Business Models for Banking"](/assets/images/BusinessModels.png)


To implement these new business models, the banking architectures should move out from product-oriented applications and break the value chain into separate business platforms supporting different business areas, such as distribution, production, risk & finance management, etc.

!["Breaking the product silos"](/assets/images/Break_Product_Silo.png)


Applications are, in consequence, structured in strongly separated business area with different business imperatives

!["Conceptual Business Responsibility Model"](/assets/images/Separaton_Concerns.png)


* **Distribution**: Sales processes and activities regarding the management of customers (to whom the bank sells), products (what the bank sells) and contracts or arrangements (the formalization of a customer buying a product), thru the bank channels, open banking, partners and marketplaces.
* **Production**: Processes for managing the products that the bank can offer to the market. This is the equivalent of the manufacturing capabilities in other industries. The difference in banking is that banks don’t create a physical product, but rather a financial product that must accept operations and must be administered.
* **Operations**: Includes decentralized processes in the back office to support the distribution channels and ensure the daily functioning of the overall organization.
* **Business Development**: Includes marketing functions, market analysis, etc. to identify, on-board and retain customers.
* **Financial & Risk Management**: Functions such as risk management, business units planning and result tracking.
* **Business Infrastructure**: Support functions necessary for the bank but not specific to the banking sector, such as legal departments, document management, IT, knowledge management and HR.

Separate business platforms with separate teams will allow each business each area to focus of what really matters. For example, the distribution area will focus on providing superior customer experience, efficient commercial processes, market insights, etc; the production, or product processing, area will focus on providing agile support to new products and features; the operations area will aim for efficiency and product wide coverage of supporting functions such as payments, collections, clearing and settlement, etc.

!["Imperatives by Business Areas"](/assets/images/Imperatives_area.png)


This model implies a very strong independence between areas such as distribution, production and operations capabilities, so the bank can include in its product offer the products and services provided by their partners. This is achieved with distribution and operation capabilities that can easily deal with new products and services, allowing the deployment of new business models, like bank as a factory, distribution banking or banking platforms.

!["New Business Models"](/assets/images/new_business_model_transform.png)


By separating the Distribution layer from the Production and Operations layers, it is possible to reduce the time necessary to offer new products and services. In this way, a bank operating at two different speeds is achieved by isolating the sales and service capabilities, which require a high level of agility to maintain competitiveness and the expectations of customers, from the mission critical systems of the banking core.

Applications in the next generation banking architecture are designed, built and managed by business domains and not anymore by technical environments. This is significant change from current organizations, where currently teams are specialized in mainframe back-ends, java back-ends, BPM platform, API, DWH, data-lakes, etc. This type organization spread the business logic of business domains across different teams making the operation and maintenance of the business applications very complicated. Incidence resolution becomes a fight across team to identify and allocate the cause-roots and any new development requires the collaboration of several teams, create dependencies that will dramatically impact the agility and efficiency, and rendering useless the efforts to apply Agile and DevOps practices.

In the next generation of banking architectures, the applications are developed and managed by domain teams, with domain SME, and variety of skills to build the application using the combination of technologies that better suit for each use case. This enables e2e accountability for the software quality, improves the incidence investigation and resolution and improves the maintainability of the applications. In this scenario the business logic is centrally managed by a domain team who is fully accountable for incidence resolution.

The Applications in the next generation banking architecture will follow BIAN Standard in a collaborative pursuit of achieving a greater level of standardization in the Banking Architecture. Standardization with BIAN will improve the reusability of solution across financial institutions, improving the interoperability of commercial solutions, SaaS and custom developments, decreasing the implementation, integration and ownership costs.

BIAN provides a comprehensive model of business capabilities structured in building blocks named “Service Domains”.

Each Service Domain has a unique business purpose, are elemental (not composed of other Service Domains), and collectively comprehensive (any business activity can be model using Service Domains). 
Services Domains that implement business capabilities under the principle of single business responsibility. They expose the business capabilities using APIS or public business events. Interactions and collaborations are implemented between service domains, while business domains remains an organization and governance element.
Service Domains are implemented, integrated, deployed and/or consumed as Self-Contain Systems. They provide business capabilities exclusively through standard API and Business Events. A service domain can be implemented using any kind or combination of technical solution, from application servers, BPMaaS, IA solutions, etc. Service Domains do not share data nor transactional contexts with other domains
 
!["Service Domains in BIAN 9.0 Service Landscape"](/assets/images/BIAN9.png)


Services Domains are grouped into Business Domains, which are allocated to the business areas. Business domains are the key context element to design the IT organization that will manage the applications. The service domains within a business domain share business language, domain SMEs and even application teams.

!["Example of Business Domain"](/assets/images/business_domain.png)


