---
marp: true
theme: gaia
color: black
---

![bg opacity:70%](background.jpeg)

# Design and architecture of the system

---

## Data

- Data is stored as items in document
- Each item has a key and a value, and is identified by a unique Document ID
- Keys and values are stored as JSON documents
- CREATE, RETRIEVE, UPDATE AND DELETE (CRUD) operations can be performed on document

---

## Storage

- Items are stored in buckets, which are named data containers
- Most deployments have two or three buckets and generally no more than five

---

## Data management

- Couchbase Server provides multiple ways of accessing data via _Services_
  Key services:
- _Data service_ is used to store and retrieve data-items by key
- _Index service_ is used to create indices
- _Query service_ is used to retrieve data-items via queries, and uses the Data and Index services

---

## Cluster management

- A cluster is one or more nodes which are each running a Couchbase Server
- Additional nodes can be initialised and join a cluster
- Couchbase data is
- The cluster manager is written in Erlang, a virtual machine based language

---

## Failover and rebalance

_Failover_

- _Failover_ is when a node is removed from a cluster with speed.
- When a data service node is removed manually it is known as a _graceful failover_
- _Graceful failover_ of a data-service node that needs to be operated on triggers replica vBuckets on the remaining nodes to become active, and ensures continued data availability to the application
- When a node fails it is known as a _hard failover_
- _Automatic failover_ is hard failover initiated by the server

_Rebalance_

- _Rebalance_ is when data is redistributed between the available nodes in the cluster
- _Rebalance_ should occur when nodes are added or removed

---

# Use cases of the database

![bg opacity:70%](background.jpeg)

---

#### Popular companies that use Couchbase

Media and communications:

- BT
- Sky
- Verizon
- Vodafone

E-commerce:

- Tesco
- Staples

---

## Gaming

Gaming considerations:

- Large numbers of concurrent users (often global)
- Responsiveness
- Availability 24/7
- Frequent updates
- Semi and unstructured data?

In gaming, databases are used to store data such as character data, saved games, scores and much more

---

## Use case: Jam City

_Jam City_ is a Facebook game which began to use Couchbase due to anticipated increased scalability requirement

![bg right width:650px height:400px](jam-city.jpeg)

---

## Failover and rebalance

The failover and rebalance means that live traffic is not functionally affected when nodes are manually updated or maintained:

- Graceful failover of the target node performed (replica vBuckets activated)
- Maintenance operations performed on the target node
- Target node added back to cluster and rebalance occurs
- Cluster is at original state with updated target node

---

### Iterative game design

- Game design is based on continuous iteration
- The JSON data model allows the game to iterate without having to request and wait for schema changes (altering of database structure)
- The JSON data model of Couchbase benefits Jam City by providing database schema flexibility and increased application speed
<!-- - Iterative game design includes planning, design, coding, testing, release and evaluation -->

---

## Media

Broadcasting/media considerations:

- Sign-up and sign-in platform
- Fluctuating user numbers - i.e. tea-time peak and peak during the Coronation
- Frequent content updates
- Potentially millions of users (depending on the company)

---

## Use case: Sky

_Sky_ is the largest TV broadcaster and media company in Europe, and has over 22 million users

_"There are many key factors that made us choose Couchbase: scalability, high availability, XDCR, flexible schema, and advanced monitoring, to name a few."
Krishnan Venkatasubramanian
Head of IT Architecture, Sky_

---

## Identity platform

- _Sky_ moved its identity platform - user sign-up and sign in - from Oracle RDBMS to Couchbase
- 50% reduction in sign-in response time
- XDCR

---

## Traffic load

Couchbase performs better at a large scale which is important during viewing peaks

---

## Content updates

---

![bg opacity:70%](background.jpeg)

# Demo
