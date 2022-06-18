---
title: Basic Concepts
parent: Concurrency
grand_parent: Go
---

# goroutine

- Is the smallest executable go entity
- More lightweight than a thread
- Allow to execute a function

# channel

- Mechanism for routines to exchange data
- Data goes written in, data gets read out
- Safe out of the box (no sync mechanism or mux necessary)