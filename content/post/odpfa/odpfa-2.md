+++
categories = ['learning notes']
date = '2025-07-30 12:04:00+0000'
metaRobots = 'noindex, nofollow'
slug = 'oracle-data-platform-2025-foundations-associate-learning-notes-2'
tags = ['data', 'cloud', 'certification']
title = 'Oracle Data Platform 2025 Foundations Associate Learning Notes (2) - Convereged Database'
url = 'projects/odpfa/:slug'
+++

> 📌 **Disclaimer:**  
> This note is created for personal study purposes based the course videos by [Oracle University](https://mylearn.oracle.com/) for [Oracle Data Platform 2025 Foundations Associate](https://mylearn.oracle.com/ou/learning-path/become-an-oracle-data-platform-foundations-associate-2025/148510)
>  
> All content belongs to the original creator. This document summarizes and reflects my understanding and is not a transcript or official material.


## 1.0 - App Development: Then vs. Now

### Traditional Apps

Earlier, business applications were built using:
- A single development tool  
- A single platform  
- A single datastore  
This approach enabled rapid, simplified deployment.

### What Modern Business Apps Require

**Data Types Used:**
- JSON documents
- Full-text search
- Spatial info
- Blockchain
- Machine learning (fraud detection, real-time recommendation)
- Graph analytics (influencer mapping)
- IoT sensor streams

**Development Practices:**
- Microservices
- Distributed data
- SaaS
- API-driven
- CI/CD
- Low-code
- Security-first (Defense in Depth)

**Operational Demands:**
- Continuous delivery  
- 24/7 uptime

---
## Single-Purpose Database vs Converged Database?
### Single-Purpose Databases: Fragmented Approach
- Single-Purpose Database = Specialized system optimized for one task or data type:
    - Document  
    - Reporting  
    - ML  
    - Graph  
    - Spatial  
    - Blockchain  
    - Search

---

### Oracle’s Converged Database

![Converged Database|500](https://questoracle-staging.s3.amazonaws.com/wordpress/uploads/2023/08/23165105/Auto-DB-Photo-1.png)

- Converged Database = Unified platform handling multiple models and workloads

**Supports:**
- Relational, JSON, Graph, Spatial, Cube, Text, Blockchain
- OLTP, analytics, ML, IoT, streaming, multitenancy
- Modular architecture via Pluggable Databases (PDBs)

---

# 2.0 - Why Use JSON in Oracle?

**JSON (JavaScript Object Notation)** = lightweight, structured, and flexible text format used for storing and exchanging data between systems.

---
#### Key Benefits of JSON
- **Schema-flexible**  
  Applications can add new attributes without changing the database schema.
- **Application-friendly**  
  - Supports nested and hierarchical structures  
  - Maps well to application objects  
  - Enables fast read/write operations without SQL joins
- **Widely accepted format**  
  - Supported across major programming languages  
  - Human-readable  
  - Makes data sharing across applications and systems easier

#### How JSON Works in Oracle?
``` example of json...
{
    "name" : "Thomas Anderson",
    "job" : "Programmer",
    "addresses": [
       (
           "street" : "123 Main",
           "city" : "Santa Cruz",
           "zip" : 95041
       )
   ]
}
```

### [Oracle Autonomous JSON Database (AJD)](https://www.oracle.com/my/autonomous-database/autonomous-json-database/)
- Low-latency, scalable, JSON storage
- MongoDB APIs or SQL
- No database management
- Always-free service

#### [Autonomous Database Workloads Types](https://docs.oracle.com/en/cloud/paas/autonomous-database/serverless/adbsb/about-autonomous-database-workloads.html)

| Workload Type                               | Description                                                                                                                                      |
| ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Autonomous Transaction Processing (ATP)** | Optimized for mixed OLTP + JSON workloads using row format, caching, and indexing. Fully converged (relational + JSON) with MongoDB API support. |
| **Autonomous JSON Database (AJD)**          | Focused on JSON workloads. Feature parity with ATP but cost-optimized. Supports unlimited JSON collections and up to 20GB non-JSON data.         |
| **Autonomous Data Warehousing (ADW)**       | Designed for analytics. Uses columnar format and partitioning for large joins and fast queries. Supports JSON + other formats.                   |
|                                             |                                                                                                                                                  |

#### Understanding Oracle’s Relational Model
Oracle Database organizes data using the **relational model**, where:
- Tables Contains Rows
- Tables are Grouped Together in Schemas ![What is Schemas?|400](https://media.geeksforgeeks.org/wp-content/uploads/20250111100739447922/schema_3.jpg)
- SQL is used to access, filter, and join data across tables


#### Oracle Database API for MongoDB
Oracle offers an API compatible with MongoDB, allowing seamless migration and coexistence.

**What It Enables:**
- Data model: JSON collections, not tables
- Developers keep their skills and continue to use MongoDB's tool, drivers, and so on.
- Easy migrations of MongoDB workloads to Oracle
- Enables SQL:
    - More and faster analytical capabilities, machine learning
    - Query JSON alongside other data models: relational, XML, spatial, and so on
    - Expose relational data, reports, query results as MongoDB collections

#### How Oracle Handles Document Collections

Oracle mimics MongoDB behavior by translating document collection logic into SQL behind the scenes.

**Core Concepts:**
- **Document**: A flexible JSON object with `_id` and custom fields
- **Collection**: A logical container for documents
- **Database**: Contains multiple collections
- **SQL Usage**: Handled automatically, used only when needed


```MongoDB Collection API
use admin;

db. createCollection ("employee");

db. employee. insertOne (
{
    "_id" : 123,
    "name" : "Thomas Anderson" ,
    "job" : "Programmer"
});

db.employee.find (
    ("job" : "Programmer")
);
```

| **MongoDB Operation**                     | **Oracle Interpretation**                                     | **Background Work (SQL)**                                 |
| ----------------------------------------- | ------------------------------------------------------------- | --------------------------------------------------------- |
| `use admin`                               | Use database named `admin`, linked to schema `ADMIN`.         | Schema initialization (behind the scenes)                 |
| `db.createCollection("employee")`         | Create a **collection** (mapped to a table with JSON column). | `CREATE TABLE employee (ID VARCHAR2, DATA JSON)`          |
| `db.employee.insertOne({...})`            | Insert a **document** into the collection.                    | `INSERT INTO employee (data) VALUES (:1)`                 |
| `db.employee.find({ job: "Programmer" })` | Apply a **filter** to retrieve matching documents.            | `SELECT data FROM employee WHERE data.job = 'Programmer'` |

---
#### Oracle Autonomous JSON Database (AJD): Best of Both Worlds for Developers and Analysts

| App Developer                                                                                                                                                                                                                                                      | Analysts/Data Scientist                                                                                                                                                                                                                                                            |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1. Keep using the same MongoDB app dev toolkit:<br>-  Skills and knowledge <br>-  Favourite dev tools<br>-  Drivers, libraries, and frameworks<br><br><br>2. Develop new MongoDB compatible services that support more workload types, including SQL for analytics | 1. Keep using SQL and familiar Bl / data science tools:<br>-  Use SQL for analytical queries and reports over JSON data<br>-  Join JSON with other non-JSON data (relational. spatial, XML, Graph)<br>-  Keep using existing SQL-based tools and<br>dashboard, reporting pipelines |
| Solution:<br>- Oracle Database API for MongoDB<br>- Compass. Mongo Shell, mongoimport. and so on                                                                                                                                                                   | Solution:<br>- APEX, SQL Developer, and other third-party Bl tools<br>- OML Notebook, AutoML, Ul, and other third-party IDEs                                                                                                                                                       |

<br>

---
# 3.0 - How Graph Works in the Oracle Autonomous Database


#### [Property Graph](https://www.dataversity.net/what-is-a-property-graph/) Data Model
- It is a collection of Points (**Vertices**) and Lines between those points (**Edges**).
- Vertices & Edges can have **Properties**. 
- ![Property Graph|200](https://dv-website.s3.amazonaws.com/uploads/2020/01/01_whatispropertygraph_pic1.png)
- Common Use Cases for Graph Analytics:
    - **Anomaly Detection:**
      - Spot fraud rings or suspicious transaction patterns.
      - Identify cycles indicative of money laundering.
    - **Clustering & Community Detection:**
      - Analyze user churn and social behavior.
      - Recommend products based on shared interests.

#### How to Solve Business Problem with Graph Analytics

| Business Problem                                                                                                              | Graph Analytics Approach                                                                                                   |
| ----------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| Detect hidden fraud or suspicious finance behavior                                                                            | Is there a cycle in a graph representation of financial transactions?                                                      |
| What-if analysis in manufacturing, network management: What is the impact of changing one component?                          | What are the paths reachable from this vertex?                                                                             |
| Identify customer clusters based on activity and relationships                                                                | Are there tightly connected subgraphs in a graph of customer activities?                                                   |
| Find new insights and connections from current relationships                                                                  | - What vertices are reachable (path analysis)?<br>- Can we derive new information such as similarities in buying patterns? |
| Catalog management: How can I dynamically add new attributes to generate new assets without modifying the database structure? | How can I model a flexible schema in my database?                                                                          |

#### Oracle's Graph Analytics Capabilities
- Over **60 prebuilt in-memory parallel algorithms** ![Oracle's Prebuilt Graph Analytics Algorithms|400](https://files.speakerdeck.com/presentations/041cef945c0a4eb49a7366cc99a9da5d/slide_18.jpg)
- Enables powerful pattern-matching, ranking, community detection, and path analysis
- Support for **PGQL (Property Graph Query Language)** — SQL-like syntax for graph queries  
  - Enables declarative and intuitive querying of graph data

<br>

---

# 4.0 - Spatial Data Management in Oracle

#### What is Spatial Data?
Spatial data includes geographic and location-based information such as:
- GPS coordinates, addresses, and maps  
- Geometries: points, lines, polygons, circles, arcs  
- Satellite imagery, elevation data, and LiDAR models  
- Infrastructure networks (roads, utilities, telecom, energy)
### Oracle Spatial Studio

Oracle Spatial Studio is a **self-service mapping and analytics platform** designed to:
- Create interactive maps and visuals  
- Perform spatial queries on geospatial business data  
- Work seamlessly with Oracle databases (cloud or on-premises)

![Spatial Data Features in Oracle](https://livelabs.oracle.com/cdn/spatial-graph/spatial/workshops/intro-to-spatial/introduction/images/spatial-platform.png)

![Features on Oracle Spatial Studio](https://docs.oracle.com/en/database/oracle/spatial-studio/24.1/spstu/img/spatial_analysis_overview.png)

---

> **Read More From This Series:**
> - [My Review of the Oracle Data Platform 2025 Certification]({{< ref "post/odpfa/odpfa.md" >}})
> - [A Complete Directory of All My Learning Notes about Oracle Data Platform 2025 Foundations Associate]({{< ref "post/odpfa/odpfa-0.md" >}})
