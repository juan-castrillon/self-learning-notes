---
title: Timescale DB
has_children: true
---

# What is a database

Organized collection of data
Postgres, timescale -> DBMS (Database management system)
    Interact with the db
    Manage data
    Manage access

# Background

Memory vs Storage
    Memory
        Much faster
        VOlatile (Gets lost after power loss)
        Expensive
    Storage
        Slower
            Random or Sequential blocks (Where in the disk is data stored)
            BLock = smallest data size fetchable in the disk (pages in filesystem)
        NOn Volatile
        Cheap
Normallly Storage -> Memory -> Processing -> Memory -> Storage

# ACID Guarantees

Atomic
    All or nothing
Consistent
    The DB has to move from one valid state to another
    No junk data, constaints
Isolated
    Multiple concurrent users modifying at the same time is the same as if they did it sequentially
Durable
    Non volatile
    Crash safe

# Keys and indexes

Index helps find data quickly (like in books)
Common: B-tree
            Generalization of binary search tree
            Minimizes random reads



