---
title:  Installation
parent: Nomad
nav_order: 3
---

# Instalation

Nomad is a single binary.
To install in a linux system there is two options

1. Use the repository (for example in Ubuntu, more [here](https://www.nomadproject.io/downloads))
    ```bash
    curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
    sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
    sudo apt-get update && sudo apt-get install nomad
    ```

2. Dowload the binary, unzip it and move it to the path. 

    Afterwards use this command to test it:
    ```bash
    nomad --help
    ```

## `dev` mode

Agent runs as both server and client
NOT TO BE USED IN PRODUCTION (data is in memory)

```
nomad agent -dev
```


## UI

- Nomad has a web UI, exposed in port `4646`
- Clients and servers can be seen
- Run and view jobs