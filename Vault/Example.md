---
title:  Example
parent: Vault
nav_order: 4
---

In `dev` mode, the Key/value secrets engine is enabled by default at `secret/`.

1. Verify that the secret does not exist
    ```bash
    vault kv get secret/hello
    ```
2. Put a new key-value pair inside
   ```bash
   vault kv put secret/hello foo=world
   ```
3. If new data is put, old data is replaced
   ```bash
   vault kv put secret/hello new=yes foo=another
   ```
4. To get data inside a secret
   ```bash
   vault kv get secret/hello
   #Returns
   === Data ===
   Key    Value
   ---    -----
   foo    another
   new    yes
   ```
5. To get a specific field
   ```bash
   vault get -field=new secret/hello  #Returns "yes"
   ```
6. Information can also be json
   ```bash
   vault get -format=json secret/hello
   ```
7. To delete all data inside `hello`
   ```bash
   vault kv delete secret/hello
   ```

