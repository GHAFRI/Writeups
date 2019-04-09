# Here is the list of tips I used for networking:

## Kindle SP01
If you spot a header in a pcap file under the word `SP01` that means you need to use [This](https://github.com/NiLuJe/KindleTool):
```
kindletool dm file.pcap out
```
Then we just `binwalk` it to find what we need.

## SSL:

If an SSL `key` file exists in the `pcap` file, add it to the `Edit->Preferences->Protocols->SSL` key list and specify a certain `IP`, `port` and `protocol` to decrypt the SSL.
