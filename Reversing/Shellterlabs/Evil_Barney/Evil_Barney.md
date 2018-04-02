# Evil Barney


[Evil Barney](https://shellterlabs.com/en/questions/4-hnr-salve-vilma/evil-barney/)

## Solution

We start off by checking the file format by `file <name>` which is `ELF 64-bit LSB executable, x86-64`
Then we try to execute it by `./<name>` and we see this

![1](https://github.com/GHAFRI/Writeups/blob/master/Reversing/Shellterlabs/Evil_Barney/1.png)
![2](https://github.com/GHAFRI/Writeups/blob/master/Reversing/Shellterlabs/Evil_Barney/2.png)

Which seems like useless information to find the flag so we import it on `IDA 64`
We check on the `main` function C code by pressing `F5` and we can see 
```
int __cdecl main(int argc, const char **argv, const char **envp)
{
  _BYTE *v3; // rax

  v3 = malloc(0x1EuLL);
  p = (__int64)v3;
  *v3 = 67;
  *(_BYTE *)(p + 1) = 111;
  importantInfo();
  importantInfo2();
  importantInfo3();
  importantInfo4();
  importantInfo5();
  scramble();
  return reveal();
}
```

Which is a bunch of function calls, so we go deeper in each.
We see that each have the sentence that is shown before but if we look closer at `importantinfo` function we see

```
  *(_BYTE *)(p + 2) = 100;
  *(_BYTE *)(p + 3) = 101;
  result = p + 10;
  *(_BYTE *)(p + 10) = 97;
  return result;
```

This is ASCII where 100 -> d , 101 -> e , 97 -> a
Then we looked back at the main function and we can see 

```
*v3 = 67;
  *(_BYTE *)(p + 1) = 111;
```

67 -> C , 111 -> o
Then we continue on to each function then we discover `CodeaNanmey_Bre` which is not the flag.
We look back at the question and translate it back to english we see `I never liked Barney. It messes everything up!`
So when we look back to `importantinfo` we see that the order is distributed within each fucntion.
Instead of having 2,3,10 then 4,5,11 we arrange everything inorder and we get `CodeName_Barney` which is the flag.




