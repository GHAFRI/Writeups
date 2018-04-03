# Access Pass

```
Review the binary and find out how to circumvent your password verification.

password: shellter
format: shellter{flag}
```

## Solution

We start of by checking file format with `file <name>` and we see `ELF 32-bit LSB shared object`
Now lets run it by `./<name>` and we get
```
Uso: ./brn [senha]
```
It needs an `args` so we add `./brn hello` we get back `Sai daqui, porra!` and we exit.
Now, we import it to `IDA 32`.
We check the `main` function by excuting `F5`.
Inside we see
``` 
v17 = &argc;
  v14 = 7746418;
  v12 = 17236;
  v13 = 0;
  v11 = 7565875;
  v9 = 18043;
  v10 = 0;
  v8 = 3366707;
  v6 = 21825;
  v7 = 0;
  v4 = 26478;
  v5 = 0;
  v16 = 666;
  if ( argc > 1 )
  {
    v15 = atoi(argv[1]);
    if ( v16 == v15 )
      printf("Tome sua flag: %s%s%s%s\n", &v14, &v11, &v8, &v4);
    else
      puts("Sai daqui, porra!");
    result = 0;
  }
  else
  {
    printf("Uso: %s [senha]\n", *argv);
    result = 1;
  }
  return result;
```

We see an if statment that compares what we `input` as `args` with variable `v16` which equals `666`. 
Therefore, if we run `./brn 666` we get `Tome sua flag: r3v3rs3_3ng`. The flag simply is `shellter{r3v3rs3_3ng}`
