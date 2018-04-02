# Don't be a Kiddie

`Reverse Me`

## Solution

We start of by checking file format by `file <name>` and we get ` ELF 32-bit LSB executable`
We run it and we get 
```
You're supposed to give me something...
```
It needs `args` so we wrote `./<name> hello`
```
You gave me: hello 

		...I'm waiting for something different...
```

So, we begin by importing it to `IDA 32`. This is the `main` function by excuting `F5`.
```
int __cdecl main(int argc, const char **argv, const char **envp)
{
  char dest; // [esp+13h] [ebp-7A5Dh]
  char v5; // [esp+14h] [ebp-7A5Ch]
  char v6; // [esp+15h] [ebp-7A5Bh]

  if ( argc == 1 )
  {
    puts("\n\tYou're supposed to give me something...\n");
    exit(1);
  }
  strncpy(&dest, argv[1], 0x7A5Du);
  if ( dest != 107 || v5 != 101 || v6 != 121 )
    printf("\n\t You gave me: %s \n", &dest);
  else
    key();
  printf("\n\t\t...I'm waiting for something different...");
  arith((char *)argv[1], &dest);
  puts("\n");
  return 0;
}
```
Everything that happens in the `main` function is useless and wont generate anything. 
Even when we check the functions on the rightsuch as `key`, `footsteps` and `skull` are just text jokes.
The real key is the function `reveal` and the function that calls it is `flag` so we had to call it in the main function.
In `main` we see `puts("\n");` so lets replace that with the function, to do that we swithc back to the `IDA View-A` tab then we look up the `call    _puts`.
The we go to `Edit -> Patch Program -> Assemble` and change it to `call    flag`.
Now we need to save by `Edit -> Patch Program -> Apply Patches to input file.`
Lets run it again and we see
```
	 You gave me: hello 

		...I'm waiting for something different...
	     ___                             
	     \_/                             
	      |._                            
	      |'."-._.-""--.-"-.__.-'/       
	      |  \       .-.        (        
	      |   |     (@.@)        )       
	      |   |   '=.|m|.='     /        
	 jgs  |  /    .='`"``=.    /         
	      |.'                 (          
	      |.-"-.__.-""-.__.-"-.)         
	      |                              
	      |                              
	      |                              
	**********************************
	******** I'mNotAKiddie ***********
	**********************************
```

There, the flag is `I'mNotAKiddie`.
