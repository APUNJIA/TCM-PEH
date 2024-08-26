It is a directory service developed by Microsoft to manage windows domain networks

It stores information related to objects, such as Computers, Users, Printers, etc. Think of it like a phone book for Windows

It authenticates using kerberos tickets. Non Windows devices such as Linux machines, firewalls, etc. can also authenticate to active directory via RADIUS or LDAP

Why Active Directory?

Active Directory is the most commonly used identity management service in the world. 95% of fortune 1000 companies implement the service in their networks

It can be exploited without ever attacking patchable exploits. Instead, we can abuse features, trusts, components and more.

Physical Active Directory Components:

1) Data Store
	The AD DS data store contains the database files and processes that store and manage directory information for users, services, and applications. It:
	1) Consists of the Ntds.dit file. It is used to store password hashes.
	2) Is stored by default in the %SystemRoot%\\NTDS folder on all domain controllers
	3) Is accessible only through the domain controller processes and protocols.
2) Domain Controllers
	A domain controller is a server with the AD DS server role installed that has specifically been promoted to a domain controller. They:
	1) Host a copy of the AD DS directory store
	2) Provide authentication and authorization services
	3) Replicate updates to other domain controllers in the domain and forest
	4) Allow administrative access to mange user accounts and network resources.
3) Global Catalog Server
4) Read Only domain controller

Logical Active Directory Components:

1) Partitions
2) Schema 
	The AD DS schema:
	1) Defines every type of object that can be stored in the directory
	2) Enforces rules regarding object creation and configuration.

![[Pasted image 20240827001202.png]]

3) Domains
	Domains are used to group and manage objects in an organization. They are:
	1) An administrative boundary for applying policies to groups of objects.
	2) A replication boundary for replicating data between domain controllers
	3) An authentication and authorization boundary that provides a way to limit the scope of access to resources.
4) Domain Trees
	A domain tree is a hierarchy of domains in AD DS. All domains in the tree:
	1) Share a contiguous namespace with the parent domain.
	2) Can have additional child domains.
	3) By default create a two-way transitive trust with other domains.
5) Forests
	A forest is a collection of one or more domain trees. They:
	1) Share a common schema.
	2) Share a common configuration partition.
	3) Share a common global catalog to enable searching.
	4) Enable trusts between all domains in the forest.
	5) Share the Enterprise Admins and Schema Admins groups.
6) Sites
7) Organizational Units
	OUs are Active Directory containers that can contain users, groups, computers and other OUs. OUs are used to:
	1) Represent your organization hierarchically and logically.
	2) Manage a collection of objects in a consistent way
	3) Delegate permissions to administer groups of objects
	4) Apply policies
8) Trusts
	Trusts provide a mechanism for users to gain access to resources in another domain. All domains in a forest trust all other domains in the forest. Trusts can extend outside the forest.

![[Pasted image 20240827002331.png]]

9) Objects

![[Pasted image 20240827002517.png]]