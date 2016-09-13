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
