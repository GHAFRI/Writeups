# Tips and tricks for forensics challanges:
## Grep
### Grep Everything
To `grep flag` from a folder, we use:  
`grep -rl "flag" folder` or `grep -Hrn "flag" folder`  
### Grep Above and Below
To grep above and below, use `C1`:  
`strings file | grep flag C1`
