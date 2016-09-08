# Pubic key cryptography

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

