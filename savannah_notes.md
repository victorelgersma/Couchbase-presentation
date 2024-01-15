# Overview of the design and architecture of the system

## Data

- Data is stored as items in document
- Each item has a key and a value, and is identified by a unique Document ID
- Keys and values are stored as JSON documents
- CREATE, RETRIEVE, UPDATE AND DELETE (CRUD) operations can be performed on document

## Storage

- Items are stored in buckets, which are named data containers
- Most deployments have two or three buckets and generally no more than five

## Data management

- Couchbase Server provides multiple ways of accessing data via _Services_
  Key services:
- _Data service_ is used to store and retrieve data-items by key
- _Index service_ is used to create indices
- _Query service_ is used to retrieve data-items via queries, and uses the Data and Index services

## Cluster management

- A cluster is one or more nodes which are each running a Couchbase Server
- Additional nodes can be initialised and join a cluster
- Couchbase data is
- The cluster manager is written in Erlang, a virtual machine based language

# Use cases of the database

# Consider a demo if that's possible
