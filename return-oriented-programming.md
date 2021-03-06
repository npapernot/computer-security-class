# Return-oriented programming

Two steps in control flow exploitation: 

1. attacker gets control of program flow.
For instance return address or function 
pointer. This can be done using vulnerabilities
like stack (buffer), heap, format string.

2. attacker uses control to launch attacks.
This can be done using code injection (e.g.,
on stack or other data region). 

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

## Take aways

ROP catches most of the attention when it 
comes to finding defenses against control
flow exploitation. 

## Control flow integrity

Build control flow graphs

Insert nops to tag function, and check it
when making the call. 

zig-zag imprecision can be solved by duplicating code

CFI cannot have false positives: block 
control flow transfers intended by the 
programmer 

Challenges:
* returns that are used as jumps.
* exceptions and multi-threaded 
* dynamic shared libraries can lead to 
runtime generation of indirect jumps

CFI is a principled approach to stop
control-glow attacks, but challenges 
remain. 

## Alternatives

make it hard for adveraries to find
gadgets by randomizing the execution
of the program. 

Address space randomization: Given a secret key
and a program address space, the address
space is encrypted. 

## Address Space Layout Randomization

makes it hard to inject code on the stack
(for buffer overflow attacks) as well
as jumping to malcode (return address). 

Makes it harder for the attacker to 
predict the absolute addresses.
