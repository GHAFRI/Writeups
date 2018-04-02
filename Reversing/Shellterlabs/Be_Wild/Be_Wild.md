# Be Wild

Easy. Analyze the binary and find the flag

## Solution

We look at the file format with `file <name>` and we see `ELF 64-bit LSB executable`.
Then we run it using `./<name>` and we see `Authenticate:` if we type anything in we get `AUTHENTICATION FAILED! Intrusion Alert!`
Now, lets try to debug it by `IDA 64`.
If we look at the `main` function by pressing `F5` we see
``` 
printf(
    "Authenticate: ",
    argv,
    envp,
    446676598899LL,
    463856468069LL,
    498216206444LL,
    489626271845LL,
    489626271867LL,
    416611827813LL,
    450971566180LL,
    442381631598LL,
    511101108269LL,
    429496729705LL,
    193273528421LL,
    446676598883LL,
    489626271841LL,
    536870912115LL,
    *(_QWORD *)&v18);
  fgetws(&ws, 29, _bss_start);
  if ( !wcscmp(s1, &ws) )
    printf("Welcome!\n\t The FLAG is: %ls\n", s1);
  else
    puts("\tAUTHENTICATION FAILED! Intrusion Alert!");
  return 0;
}
```
Which the flag is the output of `%ls` which is a `wide char`. We tried looking everywhere in the debugger for any signs of the flag but we couldnt detect it.
Instead, we used the `NOP` solution. We thought of removing the `if ( !wcscmp(s1, &ws) )` by `Edit -> Patch Program -> Assemble` then we just replace the `jnz     short loc_400784` with 2 `nop`.
This basically just removes the comparision out of the way and display's the flag for us.
```
  fgetws(&ws, 29, _bss_start);
  wcscmp(s1, &ws);
  printf("Welcome!\n\t The FLAG is: %ls\n", s1);
  return 0;
```
Now we just `Edit -> Patch Program -> Apply Patches to input file.` Then we just run the excutble again. No matter what you type, you'll get the flag
```
Authenticate: I need some sleep
Welcome!
         The FLAG is: shellter{reading-wide-chars}
```
   
