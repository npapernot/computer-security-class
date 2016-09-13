# Security protocols

protocols are often defined using common characters: alice, bob

adversaries may have varying behaviors: eavesdropping, 
active manipulation of data

properties seeked:
* authenticity: identity of prinvipals communicating
* integrity: data transmitted is not modified
* confidentiality: only recipient can read
* non-repudiation: impossible to deny later

## Authentication

Basic authentication suffers ftom replay attacks
and the recipient can impersonate the originator.

Hashed passwords prevent the recipient from 
recovering the plaintext password due to the
one way property of hash functions.

Challenge and response allow to prevent 
replay attacks. The recipient sends a 
challenge and the originator responds
by hashing it along with the concatenated password.

## Integrity

Simplest way is to send a hash of the data. 
To orevent adversaries from tampering with the
data, the hash needs to be encrypted. 

Can use both symmetric and public key crypto. 
That corresponds to hmac or signing with a 
private key. 

## Non repudiation

hmac: shared key does not provide non repudiation
because eithet principals can compute the hmac

public key crypto: provides non repudiation since
originator is only principal with the private key

## Confidentiality

Several options. Easiest is to assume a shared secret
and used it as private shared key in symmetric cipher.
however key distribution is hard. 

Assuming authenticity had been previously established,
oroginator can encrypt randomly generated secret 
using the recipient public key. The recipient private 
key is required to read random secret. 

## Key distribution

warning: these protocols are vulnerable to man in 
the middle attacks 

Needham Schroeder protocol on untrusted network, other
nodes of network may be untrusted. need a trusted 
third party to act as the authentication server.
cf. *using encryption for authentication in large 
networks of computers*

the protocol was assumed to be right for several years
until the Gavin Lowe attack. It's an active man in the
middle attack. this allows one to impersonate the 
originator. the attack basically uses two parralel
sessions and swapping of public keys to recover the 
nonce. protocol is safe if there is at most one 
session at a time.

this discovery led to new protocol analysis tools 
like the lowes fdr. analyzing multiple sessions
is undecidable. Manual induction and expert 
analysis are required. 

real systems thus typically reuse primitive protocols. 
