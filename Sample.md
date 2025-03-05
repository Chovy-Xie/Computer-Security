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

 - Least Privilege: means that each user, process, or system component should be granted only the minimum set of permissions necessary to perform its functions. This minimizes the potential damage if a user or process is compromised and limits the risk of accidental or malicious misuse of privileges.
- e.g., A company where a junior accountant needs to generate financial reports. Instead of gaining a read-only access, the accountant is given full administrative privileges on the financial system. It means they can not only view data but also modify or delete sensitive financial information.


> Consider the following scenario: An attacker steals a password to the CFO's account at a major company, and in the day before a financial report is release the attacker changes numbers to make it look like the company far more successful than it was. The next day the modified report gets released and stock market price soars, making a big profit for the attacker. For each of the "big three" security goals, explain whether this was a significant impact on that goal.

1. Confidentiality: The attacker stole the CFO's password, which granted unauthorized access to sensitive financial data.

2. Integrity: The attacker altered financial figures before the report's release, making it appear that the company was more successsful than it actually was. This violated data integrity because the financial report no longer reflected the true state of the company, misleading stakeholders and investors. 

3. Availability: Not affected. The report was still released on time and accessible to users, meaning availability was not a primary target in this scenario.


> The two main styles of encryption are public-key encryption and symmetric encryption, and each has its advantages and disadvantages. For each style, give an advantage it has over the other. 
```
# Symmetric Encryption
+ Fast! Up to 1000x faster than PK
+ (Seem to) require brute force to break
- Must have shared secret (key mgmt)

# Public-Key Encryption
+ Communicate with stranger (key mgmt)
- Slow (100-1000 times slower)
- Mathematical breaks (larger keys req'd)
```


> The uses of cryptography for integrity protection, we talked about three different types based on what keys were used (or not used). Each type had a specific name--give the name for each description:

1. An authenticator with no key
 - Hash Function (e.g., SHA-256)
 - These provide integrity verification by computing a fixed-length hash from data, but they do not use a secret key. Since anyone can compute the same hash, they do not provide authentication.

2. An authenticator that uses the same secret for sender and receiver
 - Message Authentication Code (MAC) (e.g., HMAC)
 - A MAC ensures both integrity and authenticity by requiring a shared secret key between sender and receiver to generate and verify the authentication code. 

3. An authenticator that uses different keys to authenticate and verify
 - Digital Signature (e.g., RSA)
 - Digital signatures use a private key for signing and a corresponding public key for verification, providing both integrity and authentication without requiring a shared secret.


> A digital certificate plays a vital role in the distribution of public keys. Describe what a certificate does, what it protects against, and how it does this. 

What a Digital Certificate Does: 
 - It binds a public key to an entity (e.g., a website, person, or organization) through a trusted third party known as a Certificate Authority (CA).
 - It ensures that a given public key actually belongs to the entity claiming it, preventing impersonation or fraudulent key usage.

What a Digital Certificate Protects Against:
 - Man-in-the-Middle (MITM): Prevents attackers from intercepting and substituting a fake public key to trick users into communicating with a fraudulent entity.

How a Digital Certificate Works: 
 - Issued by a Trusted CA: A trusted entity (e.g., Let's Encrypt, DigiCert) issues the certificate, verifying the requester’s identity before binding the public key.
 - Contains Important Information: Includes the public key, entity details, expiration date, and CA’s digital signature.
 - Verification Process: When a user or device encounters a certificate, it:
	- Checks the CA’s digital signature using the CA’s public key.
	- Verifies that the certificate is valid, unexpired, and not revoked.
	- Confirms that the public key belongs to the expected entity.


> How long would a brute-force attack on a symmetric cipher with a 56-bit key take, in the worst case, if you could test around a trillion keys per second? What if the cipher used 80-bit keys?
```
2^10 ~ a thousand
2^20 ~ a million
2^30 ~ a billion
2^40 ~ a trillion

2^12 ~ sec/hr
2^16 ~ sec/day
2^25 ~ sec/yr

# 56-bit key
2^56 / 2^40 = 2^16 (a day)

# 80-bit key
2^80 / 2^40 = 2^40
```


>  Briefly describe why no deterministic encryption system can be IND-CPA secure. You don’t need to define IND-CPA or present a complete proof – your description should be as if you were talking to someone who was already familiar with the definition.

No deterministic encryption system can be IND-CPA secure because encrypting the same plaintext always produces the same ciphertext. This allows an attacker to recognize repeated encryptions of the same message, leading to pattern leakage.

For IND-CPA security, encryption must be probabilistic (e.g., using random IVs or nonces) so that encrypting the same message multiple times results in different ciphertexts. Deterministic encryption lacks this randomness, making it inherently vulnerable to chosen-plaintext attacks.


> What is a “biometric” and how is it used for authentication? Give a general description and one specific example. Give one advantage and one disadvantage of using biometrics for authentication.

A biometric is a unique physical or behavioral characteristic of a person that can be used for authentication.

1. Capturing the biometric feature (e.g., scanning a fingerprint).
2. Converting it into a digital template. 
3. Comparing the captured templated with stored templates in a database. 
4. Granting or denying access based on whether a match is found. 

Advantage: Biometrics are unique to an individual and cannot be easily stolen, guessed, or shared. 
Disadvantage: If a biometric is stolen or copied, it cannot be changed like password, making security breaches more severe.


> What is two-factor authentication, and give an example.

Two-Factor Authentication (2FA): A security mechanism that requires users to provide two different types of authentication factors to verify their identity.

Three Main Types of Authentication Factors: 
1. Sth you know: a password, PIN, or security question. 
2. Sth you have: a smartphone, security token, or smart card. 
3. Sth you are: a biometric, such as a fingerprint or facial recognition.