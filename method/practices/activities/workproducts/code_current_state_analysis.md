---
layout: default
title: WP - Current State Analysis for Application Disposition
has_children: false
nav_order: 1
has_toc: true
nav_exclude: true
---

# Current State Analysis for Application Disposition - workproduct - 

The Current State Analysis for Application Disposition workproduct provide the relevant information about the existing applications that will be used in the disposition decisions for the applications. For example, the current state analysis can provide a technical metric of the number and complexity of the technical dependencies of the applications with the sourounding systems and the complexity of the code, and these inputs are used to decide whether the application should be refactored or completelly re-designed.

The most important technical metrics to be provided in the workproducts will depend on the use that the WP will received in further stages of a project. When the WP is going to be used as input to decide application disposition strategies, the target application architecture and a transformation roadmap, all in a context of a core to cloud transformation, the metrics we are looking for are:


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
    

* **Allignment Open Standards** The application follows open standard or deviate from them. For example applications developed in Cobol, or java, versus application developed on proprietary lenguages. Also usage or dependencies with proprietary middleware, libraries... is considered deviation from open standard 

    | Values | Description |
    |:--------------------|:---------------------------|
	| Small |  More than 20% of software elements are not considered to follow open standards |
    | Medium | 5% -20% of software elements are not considered to follow open standards |
    | Large |  Less than 5% of software element are not considered to follow open standards |

   
* **Complexity** It meassures how easy or difficult is to understand and reproduce the code. This is usually provided by the code analysis tools using standard metrics.





