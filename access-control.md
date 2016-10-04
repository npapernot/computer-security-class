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

File UID indicates its owner and group UID indicated 
the ID of group.  Process UID indicates the 
owner of the process. Process may run with multiple
group UIDs.

To switch UIDs, setuid is a special bit in the mode 
bits that enables a user to escalate privilege when 
the file is executed. Downside is that users define
execution environment: so the setuid can be used as 
an attack vector (e.g., confused deputy). 

In windows, permissions are also associated with files. 
ACLs are called access control entry. Contains the 
principal SID, access mask (containing the rights), 
and also a type (positive and negative permissions are 
supported). Authorization is granted if all required
permissions are matched for the SIDs. As soon as a right encountered
is negative (deny), the access is denied. 


