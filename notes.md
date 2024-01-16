# Background

- distributed
  - subject to the CAP theorem

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
