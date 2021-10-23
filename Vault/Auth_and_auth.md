---
title:  Authentication and authorization
parent: Vault
nav_order: 7
---

# Authentication

Refers to how the client (e.g. CLI) validates its identity to the vault server
Can be done trough Token Authentication, although github credentials also work. (Also other auth methods)

## Token Authentication

A token is needed for a client to use vault
Vault client reads the token from the `$VAULT_TOKEN` environment variable
When deploying vault in `-dev` mode, the root token is given. This allows any operation (`root` policy)
Childs from the root token (created while logged in with `vault token create` inherit the `root` policy)
Each token is unique

When a token is no longer needed it can be revoked with `vault token revoke <TOKEN>`


# Authorization

Refers to the permits each client has once is authenticated
What is X client **authorized** to do


## Policies

Policies determine the permits avaiable
Are authored in HCL
For example
    ```hcl
    path "secret/data/*" {
    capabilities = ["create", "update"]
    }

    path "secret/data/foo" {
    capabilities = ["read"]
    }
    ```
    Is a policy that gives a client writing rights to all paths in a KVv2 secrets enginge except `/data/foo` where the user can only read
There are builtin policies:
    `default` Included in all tokens by default
    `root` gives a token super admin permissions
To view `vault policy read default`
To write `vault policy write <name> <path>`

Policies might also be associated to certain authentication methods. For example, default policies can be given to clients using a certain method always.

