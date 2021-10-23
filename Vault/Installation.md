---
title:  Installation
parent: Vault
nav_order: 3
---

# Instalation

Vault is a single binary.
To install in a linux system there is two options

1. Use the repository (for example in Ubuntu, more [here](https://www.vaultproject.io/downloads))
    ```bash
    curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
    sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
    sudo apt-get update && sudo apt-get install vault
    ```

2. Dowload the binary, unzip it and move it to the path. 

    Afterwards use this command to test it:
    ```bash
    vault --help
    ```

## `dev` mode

Vault server can be initated in `-dev` mode
Is not secure but allows to interact locally with vault

To run it
```bash
vault server -dev
...
vault status
```

Afterwards, in order to run a client, the following environment variables and data should be present

```bash
export VAULT_ADDR='http://127.0.0.1:8200'
export VAULT_TOKEN="s.aG0eAygkOQB7pITOH9xF5uln"
Unseal Key: vvP1DiOAjUoxDS4lm+bvFKewbAOieB3B1R6g6nEdzRU=
```

In the `-dev` mode, vault gives this data in a non secure manner. 
- `$VAULT_ADDR` is used by the CLI to determine to which instance of vault to connect
- `$VAULT_TOKEN` is need to authenticate the CLI to vault. By setting it as env variable, there is no need for `vault login`

## UI

Running on `-dev` mode, an UI is exposed at port `8200`
