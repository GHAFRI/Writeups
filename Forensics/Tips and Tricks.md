# Tips and tricks for forensics challanges:
## Compressed Files
### Gz
`tar -xvf file.gz`
## Binwalk
### Binwalk All
`binwalk --dd='.*'`
## Grep
### Grep Everything
To `grep flag` from a folder, we use:  
`grep -rl "flag" folder` or `grep -Hrn "flag" folder`  
### Grep Above and Below
To grep above and below, use `C1`:  
`strings file | grep flag C1`
