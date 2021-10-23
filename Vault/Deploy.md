---
title:  Deploying in real environment
parent: Vault
nav_order: 8
---

1. Vault should be configured using a `config.hcl` file.
    - This file is written in HCL
    - Example:
        ```hcl
        storage "raft" {
        path    = "./vault/data"
        node_id = "node1"
        }

        listener "tcp" {
        address     = "127.0.0.1:8200"
        tls_disable = "true"
        }

        api_addr = "http://127.0.0.1:8200"
        cluster_addr = "https://127.0.0.1:8201"
        ui = true
        ```
    - Has two primary configurations
      - `storage` determines the physical backend that vault will use (in `-dev` mode is memory, but e.g. `raft` is more suitable to production)
      - `listener`One or more listeners determine how Vault listens for API requests. 
    - `api_addr` determines where the api can be reached, `cluster_addr` determines the port for internal communication between vault nodes in a cluster

2. Physical storage needs to be created
   - In the case of `raft`, the folder `./vault/data` needs to exist
  
3. Server is started with `vault server -config=<path_to_config_file>`
4. Once is created, the env variable `$VAULT_ADDR` should be set
5. `vault operator init` allows for a first time only unauthorized access to initate vault
   - Outputs the 5 unseal keys and a initial root token
6. A number of keys (normally 3/5) are required to unseal vault
   - They are each input after `vault operator unseal`
   - Ideally not one person has all unseal keys, and the process is done from different machines each with a key
7. Once unsealed , one can login with the initial root token