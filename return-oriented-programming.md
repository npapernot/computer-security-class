# Return-oriented programming

Two steps in control flow exploitation: 

1. attacker gets control of program flow.
For instance return address or function 
pointer. This can be done using vulnerabilities
like stack (buffer), heap, format string.

2. attacker uses control to launch attacks.
This can be done using code injection (e.g.,
on stakc or other data region). 

Return oriented programming claims arbitrary 
exploitation without code injection or 
whole-function reuse.

This goes against an assumption that any code
that belonged to the application was safe
to execute, and that adversaries could only
achieve their goals by injecting new code. 

Instead, with ROP, any sufficiently large
code base should be the only requirement to
perform arbitrary exploitation. 

Generalization of return-into-libc, which 
could for instance be used to call `system()`.

Only requirement is to have either access 
to the stack, as well
as capability to rewrite it. However, an 
alternative is to move the stack to an area
in memory that the adversary can write. 
