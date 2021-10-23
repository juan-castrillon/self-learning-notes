---
title:  Secret Engines
parent: Vault
nav_order: 5
---

Secrets engines are Vault components which store, generate or encrypt secrets. 
They behave like plugins to vault allowing it to interact with different secret and environments (awsm for example)
The read/write/delete/list operations are forwarded to the corresponding secrets engine, and the secrets engine decides how to react to those operations

# Paths

Secret engines are enabled at a certain path.
In `-dev` mode, for example, a `kv` secret engine is enabled by default at `/secret`

Any secret engine can be put in any path with
```bash
vault secrets enable -path=kv kv #Here we create a kv secret engine in /kv
```

All engines can be listed with 
```bash
vault secrets list
```

Finally, a secret can be disabled (path freed and configuration deleted) with
```bash
vault secrets disable kv/
```


# Key / Value (v2)

Key/Value secrets engine is a generic key-value store used to store arbitrary secrets within the configured physical storage for Vault. Secrets written to Vault are encrypted and then written to backend storage. Therefore, the backend storage mechanism never sees the unencrypted value and doesn't have the means necessary to decrypt it without Vault.

Key/Value secrets engine has version 1 and 2. The difference is that v2 provides versioning of secrets and v1 does not.

Use the vault kv <subcommand> [options] [args] command to interact with K/V secrets engine.

Available subcommands:

Subcommand	kv v1	kv v2	Description
delete	x	x	Delete versions of secrets stored in K/V
destroy		x	Permanently remove one or more versions of secrets
enable-versioning		x	Turns on versioning for an existing K/V v1 store
get	x	x	Retrieve data
list	x	x	List data or secrets
metadata		x	Interact with Vault's Key-Value storage
patch		x	Update secrets without overwriting existing secrets
put	x	x	Sets or update secrets (this replaces existing secrets)
rollback		x	Rolls back to a previous version of secrets
undelete		x	Restore the deleted version of secrets

# Dynamic Secrets

Generated when accessed
Cna be revoked whenever

Example
    Using AWS Secret engine (has to be configured with access tokens before)
    WIth the right role configuration, vault can generate IAM credentials on demand
    Roles are saved to `aws/roles/:name`, and credentials are accessed with `vault read aws/cred/:name`
    This ouputs
    ```bash
    Key                Value
    ---                -----
    lease_id           aws/creds/my-role/0bce0782-32aa-25ec-f61d-c026ff22106e
    lease_duration     768h
    lease_renewable    true
    access_key         AKIAJELUDIANQGRXCTZQ
    secret_key         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
    security_token     <nil>
    ```
    The credentials are good for 768h (32 days) by default, but can be revoked earlier
    FOr revoking, editing and general operations, the `lease_id` is needed
    for revoking `vault lease revoke lease_id`

DIfferent secret engines offer the dynamic secret integration, like clouds (AWS, GPC) or databases