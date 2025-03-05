# Operating System Security
> An OS provides the interface between the users of a computer and that computer's hardware

Important Features: 
 - Abstracts hardware details for easier programming (API)
 - Manages resources (memory, disk space, CPU time)
 - Keeps programs, users, devices from interfering with each other
	- but also: coordinates sharing/cooperation when necessary
 - Mangages/Authenticates users 
 - Monitors and logs operations

## Separation

Separate processes from each other 
 - One process should not be able to interfere with an independent process
 - One process should not be able to spy on another

Separate applications from OS 
 - Must maintain integrity of OS code and data

Separate applications from hardware
 - For security: Force applications to go through access controls
 - For functionality: Abstract hardware to generic API
