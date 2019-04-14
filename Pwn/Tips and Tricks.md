# Tips and tricks used to solve pwn challanges:
## Python Help
Try using `help(flag)` in python pwn script, maybe it will give you `No Python documentation found for 'flag{flag_here}`
## Scripting:
### eval()
`eval()` can help in compution equations without specifiying the terms.

## checksec
`apt-get install checksec`  
This helps to check the protection on executables.  
-- https://github.com/slimm609/checksec.sh  

## import pexpect
Its an intresting python library that can be used instead of `import pwn` that could potentionally help in solving some future challanges.
