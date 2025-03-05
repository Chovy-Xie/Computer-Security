# Cryptography
> Theory and Practice

## Psedorandom Generation
> A binary pseudorandom number generator (RPNG) f "stretches" an s-bit "seed" to n-bits

<strong>f: {0,1}^s → {0,1}^n</strong>


## Models of Security

### Indistinguishability in Cryptography
> A PRNG is "cryptographically secure" if no polynomial-time attacker can tell the difference between a true RNG and the PRNG. 

How the game works: 
1. "Game master" (GM) picks a random bit b (0 or 1)
	- if b=0: The GM generates a truly random n-bit string
	- if b=1: The GM randomly selects a seed x (from {0,1}^s) and computes PRNG(x) (which produces an n-bit string)
2. The adversary, without knowing b, receives the string r (which is either truly random or the output of the PRNG)
3. The adversary then outputs a guess g for the value of b 
4. The adversary wins if g=b

Security Definition: The PRNG is considered cryptographically secure if no polynomial-time adversary can win this game with a probability significantly greater than 1/2 (the probability of a random guess).