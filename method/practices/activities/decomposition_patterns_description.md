---
layout: default
title: Decomposition patterns description (activity)
nav_order: 3
parent: Service Landscape Design
grand_parent: Method
has_children: false
has_toc: false
---

# Decomposition patterns description

| Task | Description |
|:--------------|:-------------------|
| **Identify and Describe Decomposition Patterns** | This task identifies and describes patterns of decomposition that are repeated for many applications.
The objective is that these patterns can be applied in future transformation projects, even with applications that have not entered in the scope of the domain model design. <br /> For example, product applications almost always break down into: <br /> * Product management. <br /> * Sales Process (Account opening, Loan origination, etc.). <br /> * Agreement management. <br /> * Account processing and management (operations that affect the product ledgers). <br /> * Classifications, aggregation and accounting treatments (taxes, withholdings, ...). <br /> * Calculation and settlement of fees and service expenses. To these service domains others are added depending on the characteristics of the product (guarantees, management of participants in products involving groups of parties, management of third parties in services in which the bank acts as a "broker", etc.). <br /> <br /> Some typical patterns that usually emerge in the analysis are: <br /> * Pattern for decomposition of vertical product applications (Loan, Deposit…). <br /> * Product Origination. <br /> * Downstream application integration. <br /> * Fraud / behavior detections pattern. <br /> * Separation of business and technical capabilities.|


![Example of decomposition pattern: Product Silo Decomposition](/assets/images/product_decomposition_pattern.png)
Figure: Example of decomposition pattern: Product Silo Decomposition

Next picture provides an example on how this pattern applies to a siloed product application

![Example of Product Silo Decomposition](/assets/images/application_descomposition_example.png)

* **[Guidance: Decomposition Patterns](guidance/decomposition_patterns_reference.md)** 
