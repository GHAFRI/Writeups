# Flagsync - 200
```
Developers have a history of combining code and data.
Flag is in format: flag{...}
```

## Soltion

We are given a folder that has a `python code.py`, a `README.cd` and a hidden folder `.git`
In the `python.py` we see this
```
# Read connection details for host and port
	# DO NOT hardcode the flag here
        host = str(os.environ['FLAG_HOST'])
        port = int(os.environ['FLAG_PORT'])
        flag = str(os.environ['FLAG_FLAG'])

        # Connect to remote service
        s = socket.socket()
        s.connect((host, port))

        # Send flag and close the connection
        s.send(flag)
        s.close()
```
So, we thought that we needed to look around for the `host` and the `port` of the connection and retrieve the flag from the `server`.
But, this is a `forensics problem`, this cant be it, so we started looking around for the flag.
We didnt find it, but we found a `clue`. In .git/logs/HEAD.md we find this
```
Moved to using git -- mercurial was Peter's idea anyways.
```

A good program for `Mercurial` we know of is `Tortoise Workbench`. 
So, we imported the directory of the flagsync to the program and we see

![1](https://github.com/GHAFRI/Writeups/blob/master/Forensics/OPCDE-CTF-2018/flagsync/1.png)

It looks like the `commitment history list` of what is happening.
If we look at what `commit` peter placed before he was fired, we see

![2](https://github.com/GHAFRI/Writeups/blob/master/Forensics/OPCDE-CTF-2018/flagsync/2.png)

so, the flag is `flag{Develop3rs_Dev3l0pers_D3velop3rs_Devl0p3rs!}`
 
### What I learned

You can find previous commitments if you look hard enough or used the right tools.
