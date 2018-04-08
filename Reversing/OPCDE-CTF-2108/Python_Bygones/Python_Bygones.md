# Python Bygones - 400
```
It's only 3 lines of code.

Flag is in format: flag{...}
```

## Solution

At first look, this looks very hard for begginers but for us, it was pretty simple. One suggested way was to solve it was to run the python code into `IDLE and shell`, then just attempt to get the flag using a `print function` in the code. But we figured we just debug it using `ltrace` or `dbg`. So we first run `ltrace` to see what is happening, when we reached the end we know that the flag's begining is `flag` so we inputed `flag` and clicked `ENTER`. Once we reached the end we looked through the interface backwards until we reached this

```
emcpy(0x7f4a777c3c6c, "t", 1)                                            = 0x7f4a777c3c6c
memcpy(0x7f4a777c3c6d, "t3rs_and_numb3rs_are_ov3rrat3d}", 31)             = 0x7f4a777c3c6d
memcpy(0x7f4a777c3c24, "3", 1)                                            = 0x7f4a777c3c24
memcpy(0x7f4a777c3c25, "tt3rs_and_numb3rs_are_ov3rrat3d}"..., 32)         = 0x7f4a777c3c25
memcpy(0x7f4a777c3c6c, "l", 1)                                            = 0x7f4a777c3c6c
memcpy(0x7f4a777c3c6d, "3tt3rs_and_numb3rs_are_ov3rrat3d"..., 33)         = 0x7f4a777c3c6d
memcpy(0x7f4a777c3c24, "{", 1)                                            = 0x7f4a777c3c24
memcpy(0x7f4a777c3c25, "l3tt3rs_and_numb3rs_are_ov3rrat3"..., 34)         = 0x7f4a777c3c25
memcpy(0x7f4a77703464, "g", 1)                                            = 0x7f4a77703464
memcpy(0x7f4a77703465, "{l3tt3rs_and_numb3rs_are_ov3rrat"..., 35)         = 0x7f4a77703465
memcpy(0x7f4a777034b4, "a", 1)                                            = 0x7f4a777034b4
memcpy(0x7f4a777034b5, "g{l3tt3rs_and_numb3rs_are_ov3rra"..., 36)         = 0x7f4a777034b5
memcpy(0x7f4a77703464, "l", 1)                                            = 0x7f4a77703464
memcpy(0x7f4a77703465, "ag{l3tt3rs_and_numb3rs_are_ov3rr"..., 37)         = 0x7f4a77703465
memcpy(0x7f4a777034b4, "f", 1)                                            = 0x7f4a777034b4
memcpy(0x7f4a777034b5, "lag{l3tt3rs_and_numb3rs_are_ov3r"..., 38)         = 0x7f4a777034b5
free(0x7fffee869a20)                                                      = <void>
memcpy(0x7f4a778d2c30, "\0\0\0\0\0\0\0\0\300MpwJ\177\0\0\376\377\377\377\377\377\377\377\001\0\0\0\0\0\0\0"..., 496) = 0x7f4a778d2c30
memset(0x7f4a777cf158, '\0', 64)                                          = 0x7f4a777cf158
memset(0x7f4a777093b8, '\0', 24)                                          = 0x7f4a777093b8
memset(0x7f4a777095a8, '\0', 32)                                          = 0x7f4a777095a8
strcmp("_", "_")                                                          = 0
memset(0x7f4a77701728, '\0', 8)                                           = 0x7f4a77701728
```
We couldn't believe it was that simple. Yet, even after 2 days, nobody was able to solve. Any person who played reversing problems before could have also solved it that easily.

So, the flag is `flag{l3tt3rs_and_numb3rs_are_ov3rrat3d}`
### What I learned

Nothing, it was pretty simple. One could say `well, its also 1 line of code solved` ;P
