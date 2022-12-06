---
layout: default
title: Technology Architecture
has_children: false
nav_order: 8
# has_toc: false
parent: The Architecture
---

# Technology Architecture

## Open Source

The technologies used will be largely Open Source as illustrated in the following diagram:
 


!["Technology architecture"](/assets/images/technology_architecture.png)



It should be noted that the technology choices of individual components are not as critical as the architectural principles and frameworks described in this document. Bank IT departments are typically passionate about these choices – it shouldn’t become a deal breaker. The key considerations are:

* Redhat Openshift Container Platform and IBM Cloud Paks are mandatory. The argument for Cloud Paks being that if the client wants a random selection of software, the work that IBM had to do to integrate, containerise and certify the Cloud Paks has to be repeated as an overhead for the programme.
* IBM does have solutions, as described in the Part 2 document, which can add value but are not essential


## Alternative Run Times

There are a range of run times with varying degrees of prepackaging and automation

 
!["Alternative Run times"](/assets/images/runtimes.png)



