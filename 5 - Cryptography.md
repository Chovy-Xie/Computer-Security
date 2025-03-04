# Cryptography
> Specific Techniques

## Types of (Symmetric) Ciphers

### Block Ciphers

 - Must be given a minimum amount of data. 
 - Typical symmetric cipher blocks: 64 or 128 bits. 
 - If not enough data to fill a block, must either: 
	- wait for more data, or
	- pad with block with extra bit

AES - Most popular block cipher 
 - 128-bit keys for SECRET
 - 192- or 256-bit for TOP SECRET

Block Cipher Modes - or How to encrypt multiple blocks
> How to use a block cipher to encrypt multiple blocks 

Four modes introduced with DES standard in 1977
 - Electronic Codebook (ECB): Intuitive, but insecure (don't use)
 - Cipher Block Chaining (CBC): okk for most applications
 - Cipher Feedback (CFB)
 - Output Feedback (OFB)

ECB and CBC modes must encrypt full blocks of plaintext!
 - Technique 1 (bit padding): 
	- no matter how long the plaintext, always append a 1 bit, followed by as many 0's as needed to fill out block.
	- e.g., 10111010 110 becomes -> 10111010 110<ins>10000</ins>
 - Technique 2 (byte count padding):
	- ??????????????

Additional modes introduced (standardization with AES)
 - Counter (CTR)
 - Galois Counter Mode (GCM): Include integrity protection

CTR-mode weaknesses: 
 - Attackers can flip bits as they wish, called "malleabiliy" of the cipher
	- can counteract this problem by including integrity protection (GCM)
 - Reusing counter values in disastrous

### Stream Ciphers 

 - Work in small units: bits or bytes
 - Bit-oriented stream cipher: one bit in, one bit out
 - Consider interactive terminal session... 


### Public Key Crypto 

Symmetric Ciphers 
 - Randomness(R) -> Secret Key (SK)

Public Key Crypto 
 - Randomness(R) -> KeyPair Generator (KPG) -> PubKey(PU), PrivKey(PR)

Mathematical/Computational Properties
 - KPG(R) -> (PU, PR) is efficiently computable (polynomial time) 
 - For all messages M, D(PR, E(PU, M)) = M (decryption works)


## Cryptographic Hash Functions
> map to fixed-length bit-vectors, sometimes called "message digests"

<strong>H: {0,1}* → {0,1}^n</strong>

For cryptographic applications, satisfy one or more of these goals: 
 - Preimage resistance
	- Given h, it's infeasible to find x such that H(x)=h 
	- e.g., Strong passwords for users
 - Second preimage resistance
	- Given x, it's infeasible to find y!=x such that H(x)=H(y)
	- e.g., Testing executables against known-good digests 
 - Collision resistance
	- It's infeasible to find any two x and y such that x!=y and H(x)=H(y)
	- e.g., Non-repudiation of message

### Standard Hash Algorithm - SHA


## Summary

Classes of Algorithm: 
 - Symmetric ciphers and good hash functions
	- (Seem to) require brute force attacks - 128 bits (double for hash) is very strong. 
 - Public key algorithms (encryption and signature)
	- Cryptanalytic attacks depend on algorithmic/mathematical assumptions
	- Type 1: Based on factoring and discrete log
	- Type 2: Based on ellitic curves 

Important to Remember: 
 - ALL practical cryptographic algorithms rely on <ins>assumptions</ins> for security. 
 - ALL of the public-key algs we discussed broken with quantum computers. 