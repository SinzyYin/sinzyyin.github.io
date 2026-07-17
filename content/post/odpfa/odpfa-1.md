+++
categories = ['learning notes']
date = '2025-07-30 12:03:00+0000'
metaRobots = 'noindex, nofollow'
slug = 'oracle-data-platform-2025-foundations-associate-learning-notes-1'
tags = ['data', 'cloud', 'certification']
title = 'Oracle Data Platform 2025 Foundations Associate Learning Notes (1) - Introduction to Data Management'
url = 'projects/odpfa/:slug'
+++

> 📌 **Disclaimer:**  
> This note is created for personal study purposes based on the course videos by [Oracle University](https://mylearn.oracle.com/) for [Oracle Data Platform 2025 Foundations Associate](https://mylearn.oracle.com/ou/learning-path/become-an-oracle-data-platform-foundations-associate-2025/148510)
>  
> All content belongs to the original creator. This document summarizes and reflects my understanding and is not a transcript or official material.

## 1.0 What Does Oracle Offer?  --- Oracle Autonomous Database  

The Oracle Autonomous Database is a next-generation cloud database that automates performance, security, and scalability. It includes built-in tools that simplify development, especially for data-driven applications.

---
### Oracle Application Express (APEX)

Oracle APEX = low-code development platform integrated into the Autonomous Database. It allows users to build secure, scalable web apps—fast.

**Key Benefits:**
- Rapid development of enterprise-grade applications (often in hours)
- Start building from a spreadsheet or an existing database table
- Built-in support for:
  - Interactive reports  
  - Faceted search  
  - Data grids  
- Iterative app design to match changing business needs

**Why It’s Powerful:**
- Deeply integrated with the database
- Eliminates the need for:
  - Middle-tier setup  
  - Connection and state management  
  - Manual mapping of database types to application types

---


## What Is Multi-Cloud?

**Multi-Cloud** = Strategy that involves using multiple cloud service providers to avoid dependency on any single platform.

**Advantages:**
- Avoid vendor lock-in by spreading workloads across platforms
- Access best-of-breed innovation from different providers
- Achieve cost savings by eliminating physical infrastructure
- Speed up deployment and delivery cycles
- Reduce latency by choosing local data centers
- Improve resilience with redundancy across clouds
- Enhance DevOps, microservices, compliance, and governance
- Support migration and disaster recovery across platforms

#### Megaport Cloud Router (MCR)  = Virtual Routing Service

[Megaport MCR](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/megaport1582290752989.megaport_mcr?tab=overview) helps bridge cloud environments—public, private, hybrid, and multi-cloud setups—without physical routers.

![Megaport Cloud Router (MCR)|450](https://docs.megaport.com/cloud/mcr/img/ovhcloud/ovh-mcr-redundant.png)

**Features:**
- Cloud-to-cloud communication
- No need for physical hardware
- Enables flexible hybrid architecture

---
### Oracle’s Hybrid & Multi-Cloud Support Models

| Support Model                    | Description                                                                 |
|----------------------------------|-----------------------------------------------------------------------------|
| Oracle Public Regions            | 30+ global hyperscale cloud regions                                        |
| Dedicated Regions                | Full OCI stack deployed in customer’s data center                          |
| Oracle Cloud VMware Solution     | Native VMware support in public or dedicated Oracle Cloud regions          |
| Exadata Cloud@Customer           | Autonomous databases running on-premises                                   |
| Roving Edge Infrastructure       | Portable compute/storage solutions for disconnected or remote environments |
| Microsoft Azure Interconnect     | Low-latency integration between Azure and OCI regions                      |

---

### Database Management Levels (From Traditional to Autonomous)

1. **On-Premises Database**  
   - Hosted and managed on local infrastructure
1. **Database Cloud Service**  
   - Basic cloud-hosted database with manual management
1. **Exadata Cloud Service**  
   - High-performance database appliance offered as a service
1. **Autonomous Database Service**  
   - Fully managed, self-driving database that handles tuning, security, and scaling


---

> **Read More From This Series:**
> - [My Review of the Oracle Data Platform 2025 Certification]({{< ref "post/odpfa/odpfa.md" >}})
> - [A Complete Directory of All My Learning Notes about Oracle Data Platform 2025 Foundations Associate]({{< ref "post/odpfa/odpfa-0.md" >}})


