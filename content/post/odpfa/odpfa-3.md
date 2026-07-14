+++
categories = ['learning notes']
date = '2025-07-30 12:05:00+0000'
metaRobots = 'noindex, nofollow'
slug = 'oracle-data-platform-2025-foundations-associate-learning-notes-3'
tags = ['data', 'cloud', 'certification']
title = 'Oracle Data Platform 2025 Foundations Associate Learning Notes (3) - Exadata & Base Database Service'
url = 'projects/odpfa/:slug'
+++

> 📌 **Disclaimer:**  
> This note is created for personal study purposes based the course videos by [Oracle University](https://mylearn.oracle.com/) for [Oracle Data Platform 2025 Foundations Associate](https://mylearn.oracle.com/ou/learning-path/become-an-oracle-data-platform-foundations-associate-2025/148510)
>  
> All content belongs to the original creator. This document summarizes and reflects my understanding and is not a transcript or official material.

## 1.0 Oracle Base Database Service

Oracle Base Database Service offers **full-featured cloud-hosted instances of Oracle Database**, designed for flexibility, security, and enterprise-grade performance. It supports a broad range of workloads and is available globally via Oracle Cloud Infrastructure (OCI).

- Key Capabilities of Oracle Base Database:
    - **Deployment Options:**
      - Available in multiple OCI regions worldwide
      - Supports both Standard Edition 2 and Enterprise Edition license models
      - Multilevel security model with **always-on encryption**
      - Flexible licensing: _License Included_ or _Bring Your Own License (BYOL)_
    - **Database Versions Supported:**
      - Oracle Database 12c, 19c, 21c, and 23ai
    - **Virtual Machine (VM) Configurations:**
      - Choose between:
        - Single-instance databases
        - 2-node RAC (Real Application Cluster) virtual machines
      - RAC improves availability and scalability
      - VMs offer secure, isolated environments and faster time to production
    - **Storage Architecture Options:**
      - **Logical Volume Manager (LVM)**
      - **Automatic Storage Management (ASM)** (Default)
        - Uses separate **DATA** and **RECO** disk groups
        - Required for 2-node RAC deployments
    - **Cloud Automation:**
      - Customer-controlled provisioning, patching, backup, and disaster recovery workflows

---
---

## Understanding Fault Domains, Availability Domains, and Regions

![OCI Architecture](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcS1YqhMpeVAtLDb7kNljQa9-vXQ5CuvSlHo4g&s)

- **Region**  
  A geographic area where Oracle operates OCI infrastructure. Regions are independent and geographically isolated from each other.  
  - Supports **inter-region Data Guard** for disaster recovery.

- **Availability Domain (AD)**  
  A set of data centers within a region, interconnected with low-latency networks.  
  - Multiple ADs in a region provide high availability and fault tolerance.  
  - **Intra-region Data Guard** ensures redundancy across ADs.

- **Fault Domain**  
  A group of physical hardware within an availability domain.  
  - Each AD includes 3 fault domains.  
  - Helps isolate failures by spreading instances across separate physical infrastructure.  
  - **RAC across fault domains** provides added fault isolation for database instances.

---
# 2.0 Oracle Exadata Database Service

Oracle Exadata Database Service delivers **high-performance database capabilities** using the industry-leading Exadata infrastructure—perfect for mission-critical OLTP and analytical workloads.

- Key Features of Oracle Exadata Database Service:
    - **Platform: Oracle Exadata Machine**
      - Fastest and most reliable Oracle Database platform
      - Designed for optimal cloud performance
      - Offered as a **monthly subscription** (no upfront capex)
    - **Cloud Benefits:**
      - Fully managed infrastructure by Oracle
      - Simple web-based provisioning
      - Dedicated and isolated compute environments
      - Fully compatible with on-premises Oracle workloads

---

#### Choice of Database Management Models in Oracle

| Exadata Database                                                                                                                                                                                                                                                                                                                              | Automated Database                                                                                                                                                                                                                                                                               |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Most flexible with full administrative control<br>- Co-Managed Oracle Database Cloud Service<br>- Infrastructure managed by Oracle<br>- Root access to Database VM to customize environment<br>- Supports third-party management agents<br>- Customer controlled automation to simplify admin tasks<br>- Full Control of Database VM Patching | Easiest to deploy and manage<br>- Fully-Managed Oracle Database Cloud Service<br>- Simplest data management<br>- Self-provisioning, self-securing, self-repairing, self-tuning<br>- Eliminates database & infrastructure management<br>- Frees DBAS and Developers focus on value and innovation |
| Pay only for allocated compute resources<br>- Customer initiated scaling for variable workloads                                                                                                                                                                                                                                               | Pay only for used compute resources<br>- Autoscaling for variable workloads                                                                                                                                                                                                                      |
| Easy lift and shift from on-premises<br>- Migrate any supported Oracle Database Enterprise Edition<br>version                                                                                                                                                                                                                                 | Automatic workload optimizations<br>- Data Warehouse, Transaction Processing, JSON                                                                                                                                                                                                               |

#### Oracle's Choice of Deployment
![Oracle Choice of Deployment](https://k21academy.com/wp-content/uploads/2019/10/1-2.png)


#### Management Responsibilities in Exadata Database Service

![Management Responsibilities in Exadata Database Service|400](https://docs.oracle.com/en/engineered-systems/exadata-cloud-service/ecscm/img/responsibilities.png)


---
### Exadata Licensing Options
- License Models:
  1. **License Included**  
     - Licensing is bundled with service
  2. **BYOL (Bring Your Own License)**  
     - Use existing Oracle licenses with the service
- Pricing Based on:
  - **OCPU scaling** (Oracle CPUs allocated per workload)

---

### Security: Operator Access Control (OpCtl)
Oracle’s **OpCtl system** gives customers tight control over Oracle-managed infrastructure:
- **Access Control Features:**
  - Grant and revoke operator access  
  - Limit commands and visibility  
  - Monitor and record Oracle staff sessions  
  - Terminate sessions or processes at any time


---

> **Read More From This Series:**
> - [My Review of the Oracle Data Platform 2025 Certification]({{< ref "post/odpfa/odpfa.md" >}})
> - [A Complete Directory of All My Learning Notes about Oracle Data Platform 2025 Foundations Associate]({{< ref "post/odpfa/odpfa-0.md" >}})