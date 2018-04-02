# Todo

`What is the next mission?`

## Solution

We start of by checking file format with `file <name>` and we see `ELF 64-bit LSB executable, x86-64`
Now lets run it by `./<name>` and we get
```
 ./todo <...>
```
It needs an `args` so we add `./todo hello` we get back `Bem vindo!` and we exit.
Now, we import it to `IDA 64`.
We see over 1000 functions on the right, the `main` function is useless, but if we look a little down we see 3 human named functions such as `vai`, `tacertu` and `numvai`.
If we inspect those we see words like `H@c|<Ers_C@n_|3e_Ev3rYw]-[eRe` which is not the flag.
However, function `numvai` has a sentence `\tMISSAO: Kissy Goldfinger-Spying Santa` so the flag is `Kissy Goldfinger-Spying Santa`.
```
