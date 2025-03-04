# Security Models
> Access-Control Models

## Basic Terminology
> Subject(主体), Object(客体), Action(动作), Permission(权限)

 - Subjects -> Entities that perform actions
	- Subjects initiate actions on objects.
	- A <b>user</b> logging into a system.
	- A <b>web application</b> accessing a database.
	- A <b>process</b> modifying a file.
 - Objects -> Entities that actions are performed upon
	- Objects store or contain information and are passive in the access control process.
	- Files (documents, images, videos)
	- Databases (customer records, transaction logs)
	- Network resources (servers, APIs, printers)
 - Actions -> What subjects can do with objects
	- Actions must be allowed or restricted based on access control policies.
	- Read (viewing a file or database record)
	- Write (modifying or updating data)
	- Execute (running a program or script)
	- Delete (removing files or records)
 - Permissions -> Mapping subject/object pairs to actions
	- They are defined by access control models.
	- Allowed
	- Denied

### Key Takeaway
> Effective access control ensures that only authorized subjects can perform specific actions on objects, preventing unauthorized access or security breaches

 - <b>Subjects</b> interact with <b>Objects</b>
 - <b>Actions</b> define interactions between <b>Subjects</b> and <b>Objects</b>
 - <b>Permissions</b> control what <b>Actions</b> are allowed


## Access Control Matrix and Access Control Lists (ACLs)
> Both are models used to define and enforce who can access what in a system

### Access Control Lists (ACLs) - 访问控制列表
> An ACL is a list associated with an object that defines which subjects (users, groups, processes) are allowed or denied access and what actions they can perform.

Structure of an ACL - <b>Each object</b> has an associated list of <b>subjects</b> and their <b>permission</b>

Advantages
 - Simple & straightforward for managing permissions on individual objects.
 - Efficient for checking access to a specific resource
 - Can store rights with each object (easy to delete) 

Disadvantages
 - Difficult to manage at scale—if there are many objects, each requires its own ACL
 - Not user-centric—hard to see what access a specific user has across different resources
 - Hard to enumerate(列举) user rights

### Access Control Matrix - 访问控制矩阵
> Matrix--rows for subjects, and cols for objects

A Table where: 
 - Rows represent subjects (users, processes)
 - Columns represent objects (files, databases)
 - Cells contain permissions (read, write, execute)

Advantages
 - Comprehensive view of access rights in a system
 - Easier to audit—clearly shows what each user can access
 - User-focused view allows for caching(缓存) and efficient lookups (高效查找). 

Disadvantages
 - Not memory efficient—large matrices can be hard to store and manage
 - Not scalable—managing access control across thousands of users and objects can be difficult
 - Lots of shared (public) files cause lots of entries. 
 - Deleting a file is difficult--must remove from all users' lists. 

### Key Takeaway

 - Use ACLs when managing permissions <b>per object</b> (e.g., file system security)
 - Use an Access Control Matrix when auditing <b>system-wide access</b> (e.g., centralized user management)


## Security Policy and Models

### Bell-La Padula Model 

Defined with respect to a lattice: 
 - Subject S has a clearance L(S) in the lattice
 - Object O has a classification L(O) in the lattice

Simple Security Property: 
 - Terminology: No "read-ups"
 - S may read O only if L(O) <= L(S)
 - Terminology: No "write-downs"
 - S may write to O only if L(S) <= L(O) for all objects O which S has read access

### Biba Integrity Model 

Read rule: Subject S can read O only if I(S) <= I(O)
 - Effect: S is affected only by "reliable-enough" data 

Integrity Property: Subject S, with read rights to P, can modify object O only if I(P) >= I(O)
 - Effect: Unreliable data can't corrupt reliable data

### Security Policy 
> defines "what" must be protected and enforced

Key Characteristics 
 - Defines security goals (e.g., prevent unauthorized access, detect threats)
 - Establishes rules for access control, encryption, authentication, and auditing
 - Helps enforce legal and regulatory compliance (e.g., GDPR, HIPAA, ISO 27001)

### Security Models 
> provides the "how" by implementing these rules in a structured way

Key Characteristics
 - Provides formal rules and structures for implementing a security policy
 - Helps in system design, evaluation, and verification
 - Defines how data access, integrity, and confidentiality are controlled

### Mandatory Access Control (MAC) - 强制访问控制
> a centrally controlled access model where only the system administrator or security policy defines access permissions

Key Characteristics
 - Enforces confidentiality using classification levels (e.g., Top-Secret, Secret, Confidential, Unclassified)
 - Uses security labels (both subjects and objects are assigned sensitivity levels)
 - Users cannot change permissions—only system administrators control access
 - Prevents data leakage through strict enforcement

### Discretionary Access Control (DAC) - 自主访问控制
> a flexible access model where owners of objects can set permissions at their discretion

Key Characteristics
 - Users own files and can grant or revoke permissions 
 - Uses Access Control Lists (ACLs) to define who can access what
 - More user-friendly but less secure than MAC 