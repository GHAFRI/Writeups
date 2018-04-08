#Forever Alone - 100
```
You used to call the Forever Alone daemon on its cell phone. Late night when you needed its love. Now it just sends out blobs of characters with only one unique character per blob. Send back that one unique character.
The service is at services.opcde-ctf.propervilla.in on port 10001/tcp.
Flag is in format: flag{...}
Hint: Try first connecting manually to the service, e.g:

$ nc -v services.opcde-ctf.propervilla.in 10001
```
If run it with netcat we get

```
ghafri@DESKTOP-A2T99C4:/mnt/c/Users/GHAFRI$ nc -v services.opcde-ctf.propervilla.in 10001
DNS fwd/rev mismatch: services.opcde-ctf.propervilla.in != ec2-52-57-139-149.eu-central-1.compute.amazonaws.com
services.opcde-ctf.propervilla.in [52.57.139.149] 10001 (?) open
Forever Alone :(  Generating blobs.
--> A Huge Garbage Characters <--
```
## Solution	

In `--> A Huge Garbage Characters <--` there is a large paragraph of characters that looks weird on github so I removed it.
As simple as it is, we just need to create a program that fetches that garbage -> string and then use an algorithm that compares the first charachter with the rest, if there is a duplicate, the index of the first character goes to the next and so on. If index comparision reaches the end with no duplicates, it just sends its character to the server and recieve the next set of garbage. After almost 20 loops we get

### What I learned

Nothing, simple challange.
