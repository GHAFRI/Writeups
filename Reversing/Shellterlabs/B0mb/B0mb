# B0mb

Once more we need your help to deactivate a bomb. We got the software that is being executed inside the bomb.
Can you figure out the sequence of numbers to defuse the bomb? Be careful!

#Solution

We check the file format by `file <name>` and we see `ELF 64-bit LSB shared object, x86-64`
Now, we run it by `./<name>` and we get this

```
[*] Defuse the bomb with the right sequece of secret numbers
[+] Enter the first number:
```

If we enter a random number we get
`[BOOM] You're dead x.x!`
and then we exit.

So, we import it to `IDA 64` and we inspect the `main` function by pressing `F5`

```
  int result; // eax
  unsigned int v4; // [rsp+4h] [rbp-Ch]
  unsigned int v5; // [rsp+8h] [rbp-8h]
  unsigned int v6; // [rsp+Ch] [rbp-4h]

  puts("[*] Defuse the bomb with the right sequece of secret numbers ");
  printf("[+] Enter the first number: ", argv);
  __isoc99_scanf("%d", &v6);
  if ( v6 != 308
    || (printf("[+] Enter the second number: "), __isoc99_scanf("%d", &v5), v5 != 19)
    || (printf("[+] Enter the third number: "), __isoc99_scanf("%d", &v4), v4 != 837) )
  {
    puts("[BOOM] You're dead x.x! ");
    result = 0;
  }
  else
  {
    puts("[+] Bomb defused");
    printf("[+] shellter{yeah_th3_s3qu3nc3_1s:(%d_%d_%d)} \n", v6, v5, v4);
    result = 1;
  }
  return result;
```

If we look down we see the flag `shellter{yeah_th3_s3qu3nc3_1s:(%d_%d_%d)` where each `d` is a double value.
When we look back up we see an if statment that compares each variable with the correct secret numbers.
So if we run the program again with the correct numbers in order 308 -> 19 -> 837 we get

```
[*] Defuse the bomb with the right sequece of secret numbers
[+] Enter the first number: 308
[+] Enter the second number: 19
[+] Enter the third number: 837
[+] Bomb defused
[+] shellter{yeah_th3_s3qu3nc3_1s:(308_19_837)}
```

which is the flag `shellter{yeah_th3_s3qu3nc3_1s:(308_19_837)}`
