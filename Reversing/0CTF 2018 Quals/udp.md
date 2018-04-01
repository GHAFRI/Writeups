# UDP

too many [udp]()

## Under Progress

So we get the `udp` file which is an `ELF 64-bit LSB executable`
We open the file in `IDA` and we see that there are alot of exits

When we attemp to run the file using `./udp` we get

```
setup worker 0
setup worker 1
setup worker 2
...
setup worker 63
setup worker 64
[ERROR]
```

Then we look back at `main` code in `IDA` we can see

![1](https://github.com/GHAFRI/Writeups/blob/master/Reversing/0CTF%202018%20Quals/1.png)

which means the flag is a `long integer` however to get to this point we have alot of Errors and Exists


