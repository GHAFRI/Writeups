# Rev 2
```
The pyc file is a token generator that only gives the correct token at a given time. Use this correct token to find the flag. 

Tip1: You need to run multiple times quickly. 

Format: R00T _ @ _ RSi {SU4_FL4G}
```

## Solution

We extract the `zip` file and we see `randomscript.pyc`file, its `python`.
We attempt to use `strings randomscript.pyc` to get any leads and we get
```
GHnx
GHnI
GHn^
GHn/
login:user,senha:P0RT44B3RT4i
R00T_@RSi{t
3NG3NH4R1A_R3V3RS4_1T'S_C00L%si
timet
hashlibt
base64t
```

Simply, the flag is `R00T_@_RSi{3NG3NH4R1A_R3V3RS4_1T'S_C00L}`