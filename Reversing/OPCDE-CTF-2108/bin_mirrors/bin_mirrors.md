# bin_mirrors - 300
```
A strange character wants to help us escape the Matrix but he is missing a key that will allow him to use a secret phone line that will transport us out of it. Can you give him what he needs to get the flag...I mean...key?

Flag is in format: flag{...}
```
## Solution

We were given a `ELF` file that we needed to reverse so we import it to `IDA`
In `IDA` we see `main` that says
```
puts("*******************************************************************************");
  puts("[*] Hello there...");
  puts(
    "[*] I would like to show you the path that will allow you to exit the Matrix. Unfortunately, I cannot find the file "
    "with the key to the secret phone line");
  if ( argc > 2 )
  {
    if ( argc <= 3 )
    {
      v12 = atoi(argv[1]);
      if ( v12 > 9 )
      {
        puts("[*] Perfect! Let me see if that works...");
        if ( v12 == 31337 )
        {
          v10 = i_func(31337);
          v11 = v4;
          sprintf(&s, "%llu", v10, v4);
          v5 = strlen(argv[2]);
          filename = (char *)malloc(v5);
          filename = (char *)argv[2];
          ptr = (void *)v_func(filename);
          v7 = c_func((int)&s, (char *)ptr);
          if ( v7 )
          {
            puts("[*] I got the tools to read the key, but the pieces are not matching");
          }
          else
          {
            printf("[*] We got it! The flag...I mean...key...is: flag{");
            r_func((char *)ptr);
            puts("}");
            puts("[*] Now let's exit the Matrix");
          }
          puts("*******************************************************************************");
          free(ptr);
          result = 0;
```

So we should have `2` arguments to pass to the flag functions.
As per the `if statements` the first key is `31337` but we couldnt figure out the second key from the `main` function. So we looked into each other function for any hidden values and we find in `r_func` this

```
 v29 = strlen(a1);
    if ( v29 <= i )
      break;
    sprintf(&s, "%llu", v90, v91);
    if ( !i && s == *a1 )
    {
      v88 = i_func(114);
      v89 = v1;
      sprintf(&nptr, "%llu", v88, v1);
      v2 = strtol(&nptr, 0, 2);
      v59[i] = v2;
    }
    if ( i == 1 && v46 == a1[1] )
    {
      v86 = i_func(101);
      v87 = v3;
      sprintf(&v43, "%llu", v86, v3);
      v4 = strtol(&v43, 0, 2);
      v59[i] = v4;
    }
```
If you look closely at `i_func(114)`, `114` is the `ASCII` repsentation of char `r` and `101` is `e`. So, when we look till the end we get `red_pill_truth`, so the flag is `flag{red_pill_truth}`

### What I learned

Check everything first before debugging through the code.
