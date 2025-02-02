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
> Effective access control ensures that only authorized subjects can perform specific actions on objects, 
preventing unauthorized access or security breaches

 - <b>Subjects</b> interact with <b>Objects</b>
 - <b>Actions</b> define interactions between <b>Subjects</b> and <b>Objects</b>
 - <b>Permissions</b> control what <b>Actions</b> are allowed


## Access Control Matrix and Access Control Lists (ACLs)
> Both are models used to define and enforce who can access what in a system

### Access Control Lists (ACLs) - 访问控制列表
> An ACL is a list associated with an object that defines which 
subjects (users, groups, processes) are allowed or denied access and what actions they can perform.

Structure of an ACL - Each object has an associated list of <b>subjects</b> and their <b>permission</b>

Advantages
 - Simple & straightforward for managing permissions on individual objects.
 - Efficient for checking access to a specific resource

Disadvantages
 - Difficult to manage at scale—if there are many objects, each requires its own ACL
 - Not user-centric—hard to see what access a specific user has across different resources

### Access Control Matrix - 访问控制矩阵

A Table where: 
 - Rows represent subjects (users, processes)
 - Columns represent objects (files, databases)
 - Cells contain permissions (read, write, execute)

Advantages
 - Comprehensive view of access rights in a system
 - Easier to audit—clearly shows what each user can access

Disadvantages
 - Not memory efficient—large matrices can be hard to store and manage
 - Not scalable—managing access control across thousands of users and objects can be difficult

### Key Takeaway

 - Use ACLs when managing permissions per object (e.g., file system security)
 - Use an Access Control Matrix when auditing system-wide access (e.g., centralized user management)