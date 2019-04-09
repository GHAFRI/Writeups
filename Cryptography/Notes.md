# Tips and Tricks for cryptography:

## Messy Text:
if you come across messy text such as this  
`A7]^gF*(u(BkVO)1MV#U/oPWADf.4LBQ&)IE+j2TD.GLe2e4XS@q%-(3+b!&3+=g#AMcDXAMuMZ@:V/M2e4jY`  
use a good source software such as `cyberchef` to decode it, and the method to do so is using `Base85`  

## Useful python code:
### Read from a file and store as a string:  
```
with open('bin.txt','r') as f:
	data = f.read()
```
### Replacing data in a string:
```
data = data.replace("ZERO","0").replace("ONE","1")
```
