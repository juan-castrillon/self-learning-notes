---
title:  Introduction
parent: Nomad
nav_order: 1
---

# What is nomad?

Is a  workload scheduler: 
  - Place workloads where is more efficient in a pool of nodes
  - Can handle Containers, traditional vm, binaries
  - Uses job config files to coordinate deployment
  - Supports Rolling, canary and blue/green deployment(upgrades)
  - Fully Automated failure recovery

# Why Nomad? 

- Single binary
- Flexibility (not only containers)
- Scalable


# Architecture

Binary runs in two mode
Client: Run tasks
Server: Runs the client and manages jobs, runs evaluations and allocate tasks in clients



# Service Discovery - Consul

- Applications need to talk to each other. Especially in micro-service architectures where services are connected via network
- Fixed IPs, load balancers or DNS can not cope

Consul is a service discovery tool
- Services regster in a central catalog when they startup
- Application can query this catalog via API or DNS
- They send healthchecks to it






