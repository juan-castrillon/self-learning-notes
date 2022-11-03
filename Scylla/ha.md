title: High Availability
parent: ScyllaDB
---

# Replication Factor

ScyllaDB replicates data according to a replication strategy chosen by the user. 

The Replication Factor (RF) is equivalent to the number of nodes where data (rows and partitions) are replicated. 

Data is always replicated automatically. Read or write operations can occur to data stored on any of the replicated nodes.

# Consistency Level

Based on the RF, it determines how many ack from the replicas are needed to call a write or read operation successful and return to the client. 

Possible options are:
- **ANY** – A write must be written to at least one replica in the cluster. A read waits for a response from at least one replica. It provides the highest availability with the lowest consistency.
- **QUORUM** – When a majority of the replicas respond, the request is honored. If RF=3, then 2 replicas respond. QUORUM can be calculated using the formula (n/2 +1) where n is the Replication Factor.
- **ONE** – If one replica responds; the request is honored.
- **LOCAL_ONE** – At least one replica in the local data center responds.
- **LOCAL_QUORUM** – A quorum of replicas in the local datacenter responds.
- **EACH_QUORUM** – (unsupported for reads) – A quorum of replicas in ALL datacenters must be written to.
- **ALL** – A write must be written to all replicas in the cluster, a read waits for a response from all replicas. Provides the lowest availability with the highest consistency.

It can be tuned **per query**, making it easy to balance consistency and low latency
