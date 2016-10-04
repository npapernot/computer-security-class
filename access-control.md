# Access control

restricting the operations that 
processes may perform on a system

access control is useful for: 
protection (prevent errors) and 
security (prevent unauthorized 
access under all conditions)

two dimensions: protecting the 
process (limit other access to 
your resources) and protecting
ressources from your process. 

security policy defines the rules: some
statement of secure procedure or configuration
that parameterizes the operation of a system.

a policy is a set of acceptable
behaviors. 

`Check whether a process is authorized to
perform operations on an object`.

Object + operations = permission

Set of permissions generally defines the
access control policy. 

**Protection domain**: describes all permissions
that are available to a particular domain. 

access matrix is represented either
as an access control lists, or as 
capabilities

## OS Security

in UNIX, mode bits describe permissions for each file.
This is an ACL encoding an access matrix. Permissions 
are set on three operations: read, write, execute. 
Users are groupes in 3 possible types: owner, group,
world.

Directories are treated differently: permissions define
whether you can list files in directory, but need
additional permissions to read the files themselves.

UNIX permissions are **monotonic**: absence of right
does not mean you do not get access: having one
identity (user, group, or world) has access, you 
have access.
