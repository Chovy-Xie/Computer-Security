# Cryptography(密码学)

## Basics of Encryption

Encryption Function (Encryption Key) -> Network Interface -> Decryption Function (Decryption Key)

 - Plaintext: The message the sender wants to send.
 - Ciphertext: The data that is transmitted.
 - Goal: Ciphertext should reveal no information about plaintext to anyone who doesn't have the decryption key (semantic security).
 - Or?: Ciphertext can't be tampered with in a meaningful way. (non-malleable security)


Let's simplify the goal to: Passive attacker can't discover plaintext(明文).

What does attacker know?
 - ciphertext(密文)
 - decryption function
 - encryption function

note. encryption key (加密密钥) not necessarily need to be secret.

but. decryption key (解密密钥) MUST be secret!

Keys the same or different?
 - same: "symmetric cipher" (对称密码)
	- best feature: fast (AES-NI gives 5-10 Gbps)
	- worst feature: difficult key management
 - different: "public-key crypto" (公钥加密)
	- best feature: simpler key management (can send to a stranger)
	- worst feature: slow (1-2 Mbps for 2048-bit RSA)

### Symmetric Ciphers
> have been used for millennia(千禧年), but... do they work for modern applications?

Goal: Securely send a credit card number online to store
 - First time: never interacted with the store (no shared secret!)
 - A solution: You and store share keys with key distribution center (KDC)
	- can communicate a shared secret with store through KDC 
	- requires a lot of faith in KDC! (maybe a bank)
	- how do you set up the secret with the KDC 

### Symmetric Ciphers vs. Public-Key Encryption 
```
# Symmetric Ciphers
+ Fast! Up to 1000x faster than PK
+ (Seem to) require brute force to break
- Must have shared secret (key mgmt)

# Public-Key Encryption
+ Communicate with stranger (key mgmt)
- Slow (100-1000 times slower)
- Mathematical breaks (larger keys req'd)
```
Attacks on good <strong>symmetric ciphers</strong> use <b>brute-force</b>
 - Try all keys to see which give "sensible plaintext"
 - Complexity: k-bit key requires on average 1/2 2^k trials
 - Unicity distance: how much ciphertext is needed before we expect a single "sensible plaintext"
	- surprisingly short: 38 characters for English and AES-256
	- can increase (a lot!) by compressing plaintext 

<strong>Public key</strong> relies on "math tricks" and short keys can be broken by "math tricks"
 - Example: factoring breaks RSA 
 - Consequence: need larger keys for security (but PK is secure with larger keys!)

### Hybrid Encryption
```
+ Communicate with strangers (key mgmt)
+ Fast for message (even if huge)
- Mathematical breaks (larger keys req'd)
- Complicates code (using two algorithms)
```


## Cryptography for Integrity Protection

### Cryptographic Hash Functions
```
Hash Function: map to fixed-length bit-vectors, sometimes called "message digests"

H: {0,1}* -> {0,1}^n
```
For cryptographic applications, goals:
 - Preimage resistance: given h, it's infeasible(不可行的) to find x such that H(x)=h 
 - Second preimage resistance: given x, it's infeasible to find y!=x such that H(x)=H(y)
 - Collision resistance: it's infeasible to find any two x and y such that x!=y and H(x)=H(y)

### When hashFunctions aren't good enough - MACs
> Message Authentication Code: use a 2-parameter function called a MAC 

What you should do? use something designed to be a MAC
 - Most common: HMAC
 - Also fine: CMAC or an "encryption+MAC" combo (GCM crypto)

### Digital Signatures

Verification Function (Verification Key) <- Network Interface <- Signing Function (Signing Key)

Anyone can do Verification Function (uses "public" key)

Only person with "signing" key can do Signing Function ("private" key)

Terminology
 - when asymmetric keypairs are used, called a "digital signature"
 - sign operation uses private key (one person can sign)
 - verify operation uses public key (everyone can verify)

Algorithms 
 - key size and speed pros/cons carry over from encryption 
```
+ digital signature key management much easier / more powerful
- digital signature require larger keys than MACs
- digital signature are much slower than MACs
```
 - actual algorithms are quite different

Similar to "Hybrid Algorithms"
 - speed disadvantage countered by "hash then sign"
 - collision resistance means message/hash strongly linked


## Summary

 - Symmetric Encryption
	- fast (AES)
	- provides confidentiality if both sides share secret key 
 - Public-Key Encryption
	- flexible (RSA, ECC)
	- provides confidentiality with secret on one side (keypair)
 - Cryptographic Hash Function
	- fast (SHA-256)
	- integrity protection if no secrets/key necessary 
 - Message Authentication Codes (MACs)
	- fast (HMAC)
	- integrity protection if both sides share secret key 
 - Digital Signatures
	- flexible (RSA, DSA, EC-DSA)
	- Integrity protection with secret on one side 
 - Certificates
	- know who you're talking to (X.509)
	- provides assurance for public keys (with a trusted third party)