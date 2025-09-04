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


### Identity Domains: A container for your users and groups.

An identity domain represents:
 - a user population in OCI
 - security settings and associated configurations

So how does this work in practice? Well, what we do first is we create an identity domain, and then we create users and groups within that identity domain. And then we write policies against those groups, and policies are scoped to a tenancy, an account, or a compartment.

And of course, the resources are available within a compartment. And again, compartment is kind of a logical isolation for resources. This is how the whole service works. 

So you put these groups in one of the pre-determined roles, and then you assign some permissions against those roles. So this is how the service works in a nutshell.

Now anything you create in the Cloud, all these objects, whether it's a block storage, it's a compute instance, it's a file storage, it's a database, these are all resources. And if these things are resources, there has to be a unique identifier for these resources, is how are you going to operate on these resources?

So what OCI does is it provides its own assigned identifier, which is called Oracle Cloud ID, OCID. You don't have to provide this. We do this automatically for all the resources.

<img width="1174" height="620" alt="image" src="https://github.com/user-attachments/assets/ef797a93-e64b-42e4-b96f-06c3f68e3860" />

ocid1 is just the type of resource, realm is basically set of regions that share the same characteristics. So there's a commercial realm, there is a government realm, etc. Resource type is kind of the type of the resource. It's a compute instance or it's a block storage device or et cetera.

And then region is basically the region code here. It used to be a three-character code, now it's much longer string. And then there is a unique ID here, which is unique to the resource you create.

**So what are some of the examples?**

Well, your account also has an OCID, so you see that here tenancy and you can see the syntax here starting with ocid1.

Now, of course, account is across multiple regions. So you don't have a region identifier here. Its realm is ocid1, and then there is the unique identifier. In case of block volume, you see the region, because block volume is specific to a particular region. So you see the region key here, and then the unique identifier.

<img width="1085" height="594" alt="image" src="https://github.com/user-attachments/assets/08113494-989a-4adc-8da5-a5136a42affc" />

### Compartments

When you open an account in OCI, you get a tenancy. That's another fancy name for an account. And we also give you a Root Compartment. So think of Root Compartment as this logical construct where you can keep all of your cloud resources. And then what you could do is, you could create your own individual compartments, like you see here.

There is a network compartment. There's a storage compartment. And the idea is, you create these for isolation and controlling access. And you could keep a collection of related resources in specific compartments. So the network resource has-- a network compartment has network resources, and storage compartment has storage resources.

Now, keep in mind, Root Compartment, as I said earlier, can hold all of the cloud resources. So it can be sort of a kitchen sink. You could put everything in there. But the best practice is to create dedicated compartments to isolate resources.

<img width="1128" height="645" alt="image" src="https://github.com/user-attachments/assets/0c9b2c86-f0c0-4fba-9197-7b5e37367db3" />

So first thing is, each resource you create belongs to a single compartment. So you create a virtual machine, for example. It goes to Compartment A. It cannot go to Compartment B. Again, you have to move it from Compartment A, or delete, and recreate in Compartment B. Keep in mind, each resource belongs to a single compartment.

<img width="1157" height="588" alt="image" src="https://github.com/user-attachments/assets/a8101235-b3a6-4e05-9cf0-d7b92f30afdd" />

The reason why you want to compartmentalize your resources is exactly shown on this slide. Why you use compartments in the first place is for controlling access and isolation. So the way you do that is, you have the resources, let's say in this case a block storage, kept in Compartment A. You don't want those to be used by everyone. You want those to be used only by the compute admins and storage admins.

So you create those admins as users and groups, write these policies, and they can access these resources in this compartment. So it's very important. Do not put all of your resources in the Root Compartment. Create resource-specific compartments, or whichever way you want to divide your tenancies, and put resources accordingly.

<img width="1010" height="604" alt="image" src="https://github.com/user-attachments/assets/de50b993-4826-487e-828c-8ca1e4985b8a" />

Keep in mind that resources can also be moved from one compartment to another.

 Another concept, which is very important to grasp is the compartments are global constructs, like everything in identity. So resources from multiple regions can be in the same compartment. So when you go to Phoenix, you see this compartment existing. You go to Ashburn, you see the same compartment.

Now, you can write policies to prevent users from accessing resources in a specific region. You could do that. But keep in mind, all of the compartments you create are global, and they are available in every region you have access to.

Compartments can also be nested. So you have up to six levels nesting provided by compartments.

And then, finally, you could set quotas and budgets on compartments. So you could say that, my particular compartment, you cannot create a bare metal machine. Or you cannot create an Exadata resource. So you could control it like that. And then you could also create budgets on compartments. So you could say that, if the usage in a particular compartment goes beyond $1,000, you'd get flagged, and you get notified. So you could do that.

So that's Compartments for you. It's a very unique feature within OCI. We believe it helps keep your tenancies much better organized. And it really supports your current ID hierarchy and design. 
