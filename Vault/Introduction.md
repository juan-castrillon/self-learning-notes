---
title:  Introduction
parent: Vault
nav_order: 1
---

# Secrets

Something that would increase risk if an athorized person got it
Secret is used for auth and autentication and sensitive data is confidential (gates to sensitiyive data)

# Vault

Secret management solution
  Centralize secrets (all secrets in one place)
  Encryption at rest and in transit
  Access control to secrets (who access what)
  Identity based auth
  Automatic secret rotation
  Gives audit logs (what is going on, who accessed what)


# Application

Vault has "dynamic secrets"
Credentials for apps expire after some time, and each is unique for each app client


Encrypt-as-a-service
  Vault allows creation of keys (named)
  Vault exposes a high level API to do cryptography
  App just tells vault to encrypt something with the keys stored in vault
  Encryption is guaranteed by vault


Applications can authenticate to vault using different type of auth providers (nomad, k8s, aws, etc)
Vault stores data in a "persistent storage" which might be Consul or a Database

Vault comes with various pluggable components called secrets engines and authentication methods allowing you to integrate with external systems

Vault has a client-server architecture
  Server part is the only one that interacts with the secrets
  All operations via the CLI interact with the server via a TLS connection
  







