title: Terms
parent: ScyllaDB
---

# Node
A Node is a unit of storage in ScyllaDB. It is comprised of the ScyllaDB database server software running on a computer server — a physical machine — and all its subsystems (CPUs, memory, storage, network interfaces, and so on), or, in a virtualized environment, a subset of a server’s resources assigned to a container.

# Cluster
A minimum Cluster typically consists of at least three nodes. Data is replicated across the Cluster, depending on the Replication Factor.

# Table
A Table is how ScyllaDB stores data and can be thought of as a set of rows and columns.

# Keyspace
A Keyspace is a collection of tables with attributes that define how data is replicated on nodes. It defines several options that apply to all the tables it contains, most prominently of which is the replication strategy used by the Keyspace. A Cluster can have multiple Keyspaces. 

# CQL
A query language for interacting with the ScyllaDB (or Cassandra) database.

# CQL Shell
A command-line interface for interacting with ScyllaDB through the Cassandra Query Language (CQL)

# Replication
The process of replicating data across Nodes in a Cluster.

# Consistency Level
A configurable setting that dictates how many Cluster replicas must acknowledge read or write operations.

# Tunable Consistency
The possibility for unique, per-query, Consistency Level settings. These are incremental and override fixed database settings intended to enforce data consistency. Such settings may be set directly from a CQL statement when response speed for a given query or operation is more important.

# Replication Factor
The total number of replica Nodes across a given Cluster. A Replication Factor of 1 means that the data will only exist on a single Node in the Cluster, and this setup will not have any fault tolerance. The Replication Factor is set for each Keyspace. All replicas share equal priority; there are no primary or master replicas.

# CAP Theorem
The CAP Theorem is a concept that states that a distributed database system can only have 2 of the 3: Consistency, Availability, and Partition Tolerance.