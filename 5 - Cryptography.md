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

### Stream Ciphers 

 - Work in small units: bits or bytes
 - Bit-oriented stream cipher: one bit in, one bit out
 - Consider interactive terminal session... 