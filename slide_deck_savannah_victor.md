---
marp: true
theme: gaia
color: black
---

\
\
\
\
![bg opacity:70%](img/background.jpeg)

# Overview

---

![bg right height:50% 55%](img/couchbase-1-logo-png-transparent.png)

### Overview

- Source-available
- Distributed
- Shared-nothing architecture
- NoSQL
- Multi-model
- SQL++ for querying

---

![bg opacity:70%](img/background.jpeg)

# Design and architecture of the system

---

### Data

![bg right height:90%](img/documentstore.png)

- Couchbase is both a key-value and a document database
- Storage in binary format or JSON documents
- CRUD operations can be performed on document

---

### Storage

- Items are stored in buckets
- Most deployments have two or three buckets and generally no more than five
- Replica buckets
  ![bg right height:80% 105%](img/storage.png)

---

### Data management

- Access data via _Services_
  Key services:
- _Data service_
- _Index service_
- _Query service_

---

### Cluster management

- Clusters and nodes
- Additional nodes can be initialised and join a cluster
- Cluster management via REST API or Couchbase UI
- The cluster manager is written in Erlang
  ![bg right height:90% 105%](img/couchbase-node.png)

---

### Failover

- _Graceful failover_
  Replica vBuckets ensure continued data availability to the application

- _Hard failover_
- _Automatic failover_
- _Rebalance_ should occur when nodes are added to or removed from a cluster

---

### Cross Data Center Replication

- Cross Data Center Replication (XDCR) replicates data from a bucket on the source cluster, and the data is received by a bucket on the target cluster
- The source and target cluster can be different
- Replicates data across multiple data centers in different geographical locations

---

\
\
\
\
![bg opacity:70%](img/background.jpeg)

# How does this apply to CAP?

---

![bg width:auto height:100%](img/cap.png)

---

\
\
\
\
![bg opacity:70%](img/background.jpeg)

# Use cases of the database

---

## Popular companies that use Couchbase

![bg width:100% height:15%](img/vodafone-logo.png)
![bg width:90%](img/sky-logo.jpeg)
![bg width:90% height:15%](img/tesco-logo.png)
![bg width:90%](img/bt-logo.jpeg)

---

## Gaming

Gaming considerations:

- Large numbers of concurrent users (often global)
- Responsiveness
- Availability 24/7
- Frequent updates

---

## Use case: Jam City

_Jam City_ is a Facebook game which began to use Couchbase due to anticipated increased scalability requirement

![bg right width:650px height:400px](img/jam-city.jpeg)

---

## Failover and rebalance

Live traffic is not functionally affected when nodes are manually updated or maintained:

- Graceful failover of the target node performed (replica vBuckets activated)
- Maintenance operations performed on the target node
- Target node added back to cluster and rebalance occurs
- Cluster is at original state with updated target node

---

### Iterative game design

- JSON data model facilites game design
- No need to request and wait for schema changes
- Database schema flexibility and increased application speed

---

## Media

Broadcasting/media considerations:

- Sign-up and sign-in platform
- Fluctuating user numbers
- Frequent content updates
- Potentially millions of users

---

## Use case: Sky

Sky is the largest TV broadcaster and media company in Europe, and has over 22 million users

Couchbase offered Sky increased scalability and performance in comparison with Oracle RDBMS

---

### Identity platform

- _Sky_ moved its identity platform - which enables user sign-up and sign in - from Oracle RDBMS to Couchbase
- XDCR ensures there is always a backup of data if there are issues with one data centers
- XDCR tends to operate at the speed of network and/or memory with low latency
- 50% reduction in sign-in response time due to XDCR

---

### Disaster recovery

- Setup - Unidirectional XDCR from the primary cluster to a disaster recovery cluster
- The Disaster Recovery cluster is promoted to be the Primary cluster, and the old Primary cluster is demoted the new Disaster Recovery cluster
- Reduced recovery time from hours to minutes

---

\
\
\
\
![bg opacity:70%](img/background.jpeg)

# Pros / Cons

---

![bg right width:105% height:70%](img/nosql-survey.png)
_"There are many key factors that made us choose Couchbase: scalability, high availability, XDCR, flexible schema, and advanced monitoring, to name a few."_

_Krishnan Venkatasubramanian
Head of IT Architecture, Sky_

---

\
\
\
\
![bg opacity:70%](img/background.jpeg)

# Demo

---

### Reading

https://couchbase.live/ (online sandbox)

glossary
https://docs.couchbase.com/server/current/learn/glossary.html

intra-cluster-replication
https://docs.couchbase.com/server/current/learn/clusters-and-availability/intra-cluster-replication.html

intro / marketing video:
https://www.youtube.com/watch?v=7OKSgtDt1lo
