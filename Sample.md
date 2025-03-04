# Sample Mid-Term Exam

> For the following classes of attacks given in the book, describe which basic goal is violated, and give a specific example of such an attack: alteration, denial-of-service, eavesdropping.

1. Alteration 
 - Violated Goal: Integrity
 - Explanation: Alteration attacks involve unauthorized changes to data. Integrity ensures that data remains unmodified from its original state. 
 - MitM (Man-in-the-Middle): An attacker intercepts messages between two parties--such as an online banking transaction--and modifies the transaction details (for example, changing the transfer amount or destination account) before forwarding the message. This alteration compromises the integrity of the transaction.

2. Denial-of-Service (DoS)
 - Violated Goal: Availability
 - Explanation: Denial-of-Service attacks prevent legitimate users from accessing a system or service. Availability ensures that data and services are accessible when needed. 
 - DDoS (Distributed Denial-of-Service): An attacker (or group of attackers) floods a website with an overwhelming amount of traffic (such as the famous 2016 Dyn attack) so that the server is overloaded and cannot respond to legitimate requests, rendering the website inaccessible.

3. Eavesdropping 
 - Violated Goal: Confidentiality
 - Explanation: Eavesdropping attacks involve secretly listening to or capturing data as it is transmitted. Confidentiality ensures that sensitive information is only accessible to authorized parties. 
 - WiFi Sniffing: An attacker uses a packet sniffer to intercept unencrypted traffic over an open or poorly secured WiFi network, capturing sensitive data such as login credentials, emails, or credit card numbers, thereby breaching confidentiality.


> While an Access Control Matrix is the most complete way to describe what permissions each subject in a system has for each object, it is much more common for systems to use Access Control Lists (ACLs). Give one advantage and one disadvantage of using ACLs. 

 - Advantage: ACLs are object-centric, meaning that permissions for each object are stored directly with the object. This makes it efficient and straightforward to check what access is allowed for that particular object when a requrest is made. 
 - Disadvantage: ACLs are not subject-centric. It can be difficult to quickly determine all the permissions a single user or subject has across multiple objects because that information is spread out over many different ACLs. 


> What does the security principle of "least privilege" mean? Give an example in which the principle of least privilege has not been followed. 

 - Least Privilege: means that every user, process, or system component should be given only the minimal level of access--or permissions--necessary to perform its function, and nothing more. This principle reduces the risk of accidental or malicious misuse of privileges and limits the damage potential if a user account or process is compromised. 