# Public key cryptography

Public key cryptography requires different keys for encryption and decryption. 

Public key is typically distributed through public key certificates. 
Message can be encrypted by anyone using public key, but can only
be decrypted by you using the private key. 

The public key distribution service needs to be trusted. 

SSL communication based on public key cryptography to authenticate the server.
A symmetric key is setup and used to communicate securely with the server.

**Trapdoor function** has two property: 
* easy to compute
* difficult to invert, unless you have the secret

Hash functions are not trapdoors since there is no possible inversion, even 
with knowledge of some secret. For the same reason, MAC functions are not
trapdoors either.

# Diffie-Hellman key agreement

Diffie-Hellman introduced crypto to the research community (vs. DES, which 
was an industrial effort). Goal is to agree on key value in the clear. 
The solution is based on computing discrete logarithms. 

Public information: prime p and base g
Private value: a for A and b for B

A and B compute: y=g^x mod p where x=a,b
A and B compute: z=y^x mod p where x=a,b

z is the common value on which they agree. 

This protocol is however vulnerable to man-in-the-middle attacks.

In practice the Diffie-Hellman exchange should be authenticated. 

# Key distribution and agreement

**Key distribution**: assign and transfer keys to a participant:
* out of band: passwords
* during authentication: Kerberos
* as part of communication: skip-encryption

**Key agreement**: two parties negotiate a key. Invovles at least 
2 participants. 

Having more than one participant coming up with the key allows to 
introduce more randomness in the process. 

Key distribution and agreement occurs in conjunction with or after
authentication.

Since public key cryptography is slow, eventually the parties
want to generate a symmetric key that can be used with symetric
cryptography. 

# Rivest Shamir Adelman RSA

The security of RSA comes from number theory. It is based on the 
hardness of factoring the product of two large prime numbers. 

Current standard 2048 bit RSA keys

* Two large primes p and q
* Calculate n=pq
* pick e such that it is relatively prime to Euler's Totient function: `phi(n) = (q-1)(p-1)`
* `d~=e^{-1} mod phi(n)`

The Totient guarantees that encryption uses the entire possible 
target domain.

Public key is set of e and n 
Private key is d and n

In RSA, trapdoor function is prime product factoring and trapdoor 
secret the private key (for encryption) and the public key 
(for signature--authenticity). 

Bad implementations of RSA: reuse n for multiple users then anyone
can factor, blinding misuse by signing message product of malicious
message modulo something.

# Digital signatures

Asserts document is authentic and non-reputable. To sign a document,
one encrypts it with its private key. To validate the signature, 
anyone can use the public key. 

The document is first hashed before encryption for signing to validate
authenticity. This is provided by the properties of hash functions:
one way and collision free. It makes it harder for an adversary to 
craft a different message that would have the same signature and would
decrypt correctly.

# Using public key crypto

No need to use public key crypto if a private symetric key was 
already established.

# Timing attacks

timing attacks are examples of side channel attacks

a possible defense is binding: ensure the computation always takes the same time

other side channel: analysis of power consumption.
a direct interpretation of power measurements can reveal
the instructions executed. 

threat model differs from previously: the hardware is not 
assumed to be trust worthy anymore


