# OCI Foundations:
Oracle Cloud Infrastructure Foundations

## Security

### Vault:

Vault is a managed service that lets you centrally manage encryption **keys** and **secret** credential. Vault removes the need to store encryption keys and secrets in configuration files or in code.

So what are these things called keys and secrets?

A key specifies how to transform plaintext into ciphertext during encryption and how to transform ciphertext into plain text during decryption. 

Secrets are credentials such as passwords, certificates, SSH-keys, or authentication tokens that you can use with Oracle Cloud Infrastructure services. 

Vau;t - So this particular service lets you centrally manage these encryption keys and credential.

#### Algorithm:

**AES** is a *symmetric algorithm*. The same key *encrypts* and *decrypts* the data.

**RSA** is a algorithm. public encription key and private decryption key.

**ECDSA** .. 

## IAM

IAM = Identity and Access Management

Used for:
  - Fine grained Access Control
  - Role Based Access Control

AuthN - Who are you?
AuthZ - What permissions do you have?
Authentication has to deal with identity or who someone is, while authorization has to deal with permission or what someone is allowed to do.


Identity Domains: A container for your users and groups.

An identity domain represents:
 - a user population in OCI
 - security settings and associated configurations

So how does this work in practice? Well, what we do first is we create an identity domain, and then we create users and groups within that identity domain. And then we write policies against those groups, and policies are scoped to a tenancy, an account, or a compartment.

And of course, the resources are available within a compartment. And again, compartment is kind of a logical isolation for resources. This is how the whole service works. 

So you put these groups in one of the pre-determined roles, and then you assign some permissions against those roles. So this is how the service works in a nutshell.

Now anything you create in the Cloud, all these objects, whether it's a block storage, it's a compute instance, it's a file storage, it's a database, these are all resources. And if these things are resources, there has to be a unique identifier for these resources, is how are you going to operate on these resources?

So what OCI does is it provides its own assigned identifier, which is called Oracle Cloud ID, OCID. You don't have to provide this. We do this automatically for all the resources.

<img width="1174" height="620" alt="image" src="https://github.com/user-attachments/assets/ef797a93-e64b-42e4-b96f-06c3f68e3860" />

