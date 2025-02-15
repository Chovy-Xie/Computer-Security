# Crypto Concepts, Number Sizes, Randomness, and Entropy

## Cryptography: Threat Model

Kerckhoff's Principle: the security of a cryptographic system should depend only on the secrecy of the key, 
not the secrecy of the algorithm.


## Cryptography(密码学): Randomness

Why is Randomness(随机性) Important?
 - Unpredictability
 - High-Probability Uniqueness (大概率唯一性)
	- Many cryptographic protocols require values that must not repeat.

Key Takeaways
 - Cryptographic security relies on strong random number generators (RNGs).
 - Poor randomness leads to vulnerabilities in encryption, authentication, and gaming systems.
 - Unpredictability + Uniqueness = Stronger Cryptographic Security


## Attacker Information/Access

 - Ciphertext Only (密文)
	- The attacker has access only to the ciphertext, the encrypted message. 
	They do not have access to the plaintext (original message) or the encryption key.
 - Known Plaintext (明文)
	- The attacker has access to both the plaintext and the corresponding ciphertext.
	This allows them to examine how the plaintext is transformed into the ciphertext 
	and attempt to deduce the key or the encryption algorithm.
 - Chosen Plaintext
	- Attacker can choose arbitrary plaintexts to be encrypted and obtain the corresponding ciphertexts. 
	This allows the attacker to analyze how the encryption algorithm transforms different inputs into encrypted outputs.
 - Chosen Ciphertext
	- Attacker has access to a ciphertext and can choose which ciphertexts to decrypt. 
	The attacker can study how the ciphertexts are decrypted to gain information about the encryption key or algorithm.


## Types of Attacks

### Cryptanalysis 密码分析
Cryptanalysis refers to the process of breaking a cryptographic system by analyzing its structure 
and attempting to exploit weaknesses in the encryption algorithm itself.
 
Cryptanalysis goes beyond simply trying all possible keys; it involves leveraging patterns, statistical methods, 
or weaknesses in the algorithm to reduce the computational effort required to break the cipher.

Types: Ciphertext Only, Known Plaintext, Chosen Plaintext, Chosen Ciphertext

### Brute Force 暴力破解
Brute force attacks are based on systematically trying every possible key or password until the correct one is found. 
It is a straightforward, exhaustive method that does not require any insight into the structure of the encryption algorithm, unlike cryptanalysis.

How Brute Force Works?
 - Symmetric Encryption
	- the attacker tries all possible keys to decrypt the ciphertext and checks if the resulting plaintext makes sense
 - Password-Based Systems 
	- the attacker attempts every possible combination of characters in an effort to guess the correct password.

Time Complexity on Symmetric Encryption
	- The time to perform a brute force attack grows exponentially with the length of the key.
	- A 128-bit key would require 2^128 operations, which is infeasible with current computing power.

Time Complexity on Passwords
	- The time it takes to guess a password through brute force depends on the length and complexity of the password. 
	- If a password consists of only lowercase letters (26 characters), there are 26^n possible combinations, where n is the password length.


## Number Sizes

### Some Important Powers of Two
 - 2^10 ~ a thousand
 - 2^20 ~ a million
 - 2^30 ~ a billion
 - 2^40 ~ a trillion

### Seconds
 - 2^12 ~ an hour
 - 2^16 ~ a day
 - 2^25 ~ a year

### Keysizes & Sample Question
Q: "Given a baseline of 1 billion tests/second, how big does the keyspace need to be for brute force to be impractical?"

```
8 yrs = 2^3 * 2^25 = 2^28 sec
1 billion keys every second -> 2^30 * 2^28 = 2^58 keys tested in 8 years

For "on average", keyspace needs to be twice this: |k| >= 2^59
So: { Need to use keys with at least 59 bits }
```