# Need a Slave

`Reverse me`

## Solution

We check the file format by `file <name>` and we see `ELF 32-bit LSB executable`.
Then we run it by `./<name>` and we get `cannot execute binary file: Exec format error`, so we can't run it.
Now, lets import it to `IDA 32`.
If we look at `main` function using `F5` we see multiple function calls
```
int __cdecl main(int argc, const char **argv, const char **envp)
{
  palindrome();
  diamond();
  dectobin();
  floydstriangle();
  armstrong();
  fibonacci();
  foo();
  return 0;
}
```
If we look at `armstrong`,`fibonacci` and `foo` functions we can see hidden code that contain ASCII code.
If we look back at the first 2 they contain garbage ASCII but `foo` has genuine ASCII.
We convert the ASCII in order we get `fIW!unY0IB3vcom3MySl@e` but if we order it like this
```
byte_804A313 = 117;
byte_804A310 = 110;
byte_804A311 = 89;
byte_804A312 = 48;
```
As 
```
byte_804A310 = 117;
byte_804A311 = 110;
byte_804A312 = 89;
byte_804A313 = 48;
```
And we get
```
 byte_804A30B = 73;
 byte_804A30C = 102;
 byte_804A30D = 73;
 byte_804A30E = 87;
 byte_804A30F = 33;
 byte_804A310 = 110;
 byte_804A311 = 89;
 byte_804A312 = 48;
 byte_804A313 = 117;
 byte_804A314 = 66;
 byte_804A315 = 51;
 byte_804A316 = 99;
 byte_804A317 = 111;
 byte_804A318 = 109;
 byte_804A319 = 51;
 byte_804A31A = 77;
 byte_804A31B = 121;
 byte_804A31C = 83;
 byte_804A31D = 108;
 byte_804A31E = 64;
 byte_804A31F = 118;
 byte_804A320 = 101
 byte_804A321 = 10;
```
Which is the flag `IfIW!nY0uB3com3MySl@ve`