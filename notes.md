# Background

- distributed
  - subject to the CAP theorem
  - how to distribute data between nodes?

Q) What is NoSQL?

- NoSQL databases are schema-less or have flexible schemas,
- Typically they are easier to scale horizontally
- Can be optimized for different datatypes
- They are particularly suited for handling large volumes of unstructured or semi-structured data.

Q) What is a Schema-less application?

- _FORMAT_ of the data is not owned by the database (compare with Relational databases which will ensure the data is tabular and in "normal form")
- Couchbase is _schemaless_ because it will store any valid JSON or XML file
- Usually document stores are schemaless, whereas relational databases have a schema

# Couchbase is a document store

- NoSQL database, Document-oriented
- Use: scalable web applications, mobile applications, real-time analytics
- Characteristics: JSON document storage, key-value storage, distributed architecture, easy scalability, N1QL for querying

# History

# AP, CA, or CP?

Partition-tolerant by default.

Can be configured to be both AP ('eventual' consistency/low latency) or CP ('strong' consistency/high latency).

# Data Model

NoSQL document-oriented data model
Data stored as JSON documents

# Questions to answer

# Sources

https://docs.couchbase.com/server/current/learn/clusters-and-availability/xdcr-overview.html
https://www.couchbase.com/
https://en.wikipedia.org/wiki/Couchbase_Server
https://developer.couchbase.com/tutorial-quickstart-nodejs
https://couchbase.live/examples/basic-java-query-rows
https://terrydhariwal.github.io/2016/03/22/part-2-couchbase-architecture-in-a-nutshell

# Tasks

Some background to the database system - Victor
Overview of the design and architecture of the system - Savannah
Where does it fall in the CAP model, Why? - Victor
Describe some use cases of the database - Savannah
Pros and Cons of the database - Victor
Consider a demo if that's possible - Savannah

# Savannah notes

### Data

- Data is stored as items in a document
- Each item has a key and a value, and is identified by a unique Document ID
- Keys and values are stored as JSON documents
- CREATE, RETRIEVE, UPDATE AND DELETE (CRUD) operations can be performed on document
- Document is comparable to a row

### Storage

- Items are stored in buckets, which are named data containers
- Most deployments have two or three buckets and generally no more than five
- At bucket creation, replica buckets are configured via intra-cluster replication
- A cluster is one or more nodes, each node is running an instance of Couchbase Server

### Data management

- Couchbase Server provides multiple ways of accessing data via _Services_
  Key services:
- _Data service_ is used to store and retrieve data-items by key
- _Index service_ is used to create indexes
- Each index makes a predefined subset of data available for search in the query service
- _Query service_ is used to retrieve data-items via queries, and uses the Data and Index services. Uses SQL like query

### Cluster management

- Additional nodes can be initialised and join a cluster
- Users can manage clusters via REST API or Couchbase UI
- The cluster manager is written in Erlang, a virtual machine based language

### Failover

_Failover_ is when a node is removed from a cluster with speed.

- When a data service node is removed manually it is known as a _graceful failover_.
- It occurs on a data-service node that needs to be operated on and triggers replica vBuckets on the remaining nodes to become active.
- This ensures continued data availability to the application

- When a node fails it is known as a _hard failover_. _Automatic failover_ is hard failover initiated by the server

### Rebalance

- _Rebalance_ is when data is redistributed between the available nodes in the cluster
- It should occur when nodes are added to or removed from a cluster

### Cross Data Center Replication

- Cross Data Center Replication (XDCR) replicates data from a bucket on the source cluster, and the data is received by a bucket on the target cluster

- The source and target cluster can be different, unlike in intra-cluster replication
- XDCR replicates data across multiple data centers in different geographical locations so data is close to users

# Use cases of the database

## Gaming

Gaming considerations:

- Large numbers of concurrent users (often global)
- Responsiveness
- Availability 24/7
- Frequent updates
- Semi and unstructured data?

In gaming, databases are used to store data such as character data, saved games, scores and much more

## Use case: Jam City

_Jam City_ is a Facebook game which began to use Couchbase due to anticipated increased scalability requirement

## Failover and rebalance

The failover and rebalance means that live traffic is not functionally affected when nodes are manually updated or maintained:

- Graceful failover of the target node performed (replica vBuckets activated)
- Maintenance operations performed on the target node
- Target node added back to cluster and rebalance occurs
- Cluster is at original state with updated target node

### Iterative game design

- Iterative game design includes planning, design, coding, testing, release and evaluation
- Game design is based on continuous iteration
- The JSON data model allows the game to iterate without having to request and wait for schema changes (altering of database structure)
- The JSON data model of Couchbase benefits Jam City by providing database schema flexibility and increased application speed

## Media

Broadcasting/media considerations:

- Sign-up and sign-in platform
- Fluctuating user numbers - i.e. tea-time peak and peak during the Coronation
- Frequent content updates
- Potentially millions of users (depending on the company)

## Use case: Sky

Sky is the largest TV broadcaster and media company in Europe, and has over 22 million users

Couchbase offered Sky increased scalability and performance in comparison with Oracle RDBMS, which is particularly important during viewing peaks

### Identity platform

- _Sky_ moved its identity platform - which enables user sign-up and sign in - from Oracle RDBMS to Couchbase
- XDCR ensures there is always a backup of data if there are issues with one data centers, ensuring data availabilty and resilience
- XDCR tends to operate at the speed of network and/or memory with low latency
- Moving the platform provided Sky with a 50% reduction in sign-in response time due to XDCR

### Disaster recovery

- Disaster recovery is setup with unidirectional XDCR from the primary cluster to a disaster recovery cluster
- In disaster recovery, the Disaster Recovery cluster is promoted to be the Primary cluster, and the old Primary cluster is demoted the new Disaster Recovery cluster
- Moving to Couchbase reduced recovery time from hours to minutes
