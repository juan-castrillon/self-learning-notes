---
title:  Concept Definitions
parent: Nomad
nav_order: 2
---

# Job

- Unit of work for Nomad
- Is a file provided by the user that declares work for Nomad to do
- One job file has only **one** job
- One job has many task groups

# Task Group

- Groups tasks that run in the same node
- One task group can have many tasks

# Task

- Smallest unit of work
- Specify a driver to perform the work, and the definition of it (variables, resources, binaries, etc.)

# Resources

- Describes the requirements a task needs to execute such as memory, network, CPU and more.

# Node

# Allocation

- Mapping between task groups in a job and a client node
- Effectively, machine where task will run

# Evaluation

- Process trouough which nomad takes scheduling decisions

# Bin Packing

- Optimizes resources by putting tasks into client machines to max utilization