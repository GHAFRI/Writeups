# MacRevEngER

`We need experts looking into this binary. Can you help us figure this flag out?`

## Solution

We check the file format by `file <name>` and we see its `Mach-O 64-bit x86_64 executable`
Now we know its not possible to excute this in Lunix without having the Mach library so we import it staright up in `IDA 64`.
Looking at the `main` function by pressing `F5` we see
```
puts("\nChallenger Basic for Criptorave 2017");
  memcpy(&v51, &unk_1000016B0, 0x2AuLL);
  memcpy(&v50, &unk_1000016E0, 0x2CuLL);
  memcpy(&v49, &unk_100001710, 0x2AuLL);
  memcpy(&v48, &unk_100001740, 0x2AuLL);
  memcpy(&v47, &unk_100001770, 0x2AuLL);
  memcpy(&v46, &unk_1000017A0, 0x2AuLL);
  memcpy(&v45, &unk_1000017D0, 0x2AuLL);
  memcpy(&v44, &unk_100001800, 0x2AuLL);
  memcpy(&v43, &unk_100001830, 0x2AuLL);
  memcpy(&v42, &unk_100001860, 0x2AuLL);
  memcpy(&v41, &unk_100001890, 0x2AuLL);
  memcpy(&v40, &unk_1000018C0, 0x2AuLL);
  memcpy(&v39, &unk_1000018F0, 0x2AuLL);
  memcpy(&v38, &unk_100001920, 0x2AuLL);
  memcpy(&v37, &unk_100001950, 0x2AuLL);
  puts("\nWelcome to RTFM (Red Team Freakin' Maniacs) Challenger Level-1 N00b.\n");
  memcpy(&v36, &unk_100001980, 0x2AuLL);
  memcpy(&v35, &unk_1000019B0, 0x2AuLL);
  memcpy(&v34, &unk_1000019E0, 0x2AuLL);
  memcpy(&v33, &unk_100001A10, 0x2AuLL);
  memcpy(&v32, &unk_100001A40, 0x2AuLL);
  memcpy(&v31, &unk_100001A70, 0x2AuLL);
  memcpy(&v30, &unk_100001AA0, 0x2AuLL);
  memcpy(&v29, &unk_100001AD0, 0x2AuLL);
  memcpy(&v28, &unk_100001B00, 0x2AuLL);
  memcpy(&v27, &unk_100001B30, 0x2AuLL);
  memcpy(&v26, &unk_100001B60, 0x2AuLL);
  memcpy(&v25, &unk_100001B90, 0x2AuLL);
  memcpy(&v24, &unk_100001BC0, 0x2AuLL);
  memcpy(&v23, &unk_100001BF0, 0x2AuLL);
  memcpy(&v22, &unk_100001C20, 0x2CuLL);
  memcpy(&v21, &unk_100001C50, 0x2AuLL);
  memcpy(&v20, &unk_100001C80, 0x2AuLL);
  memcpy(&v19, &unk_100001CB0, 0x2AuLL);
  memcpy(&v18, &unk_100001CE0, 0x2AuLL);
  memcpy(&v17, &unk_100001D10, 0x2AuLL);
  memcpy(&v16, &unk_100001D40, 0x2AuLL);
  memcpy(&v15, &unk_100001D70, 0x2AuLL);
  memcpy(&v14, &unk_100001DA0, 0x2AuLL);
  memcpy(&v13, &unk_100001DD0, 0x2AuLL);
  memcpy(&v12, &unk_100001E00, 0x2AuLL);
  memcpy(&v11, &unk_100001E30, 0x2AuLL);
  memcpy(&v10, &unk_100001E60, 0x2AuLL);
  memcpy(&v9, &unk_100001E90, 0x2AuLL);
  memcpy(&v8, &unk_100001EC0, 0x2AuLL);
  memcpy(&v7, &unk_100001EF0, 0x2AuLL);
  puts("Please Show me your Skills in Reversing and Debbugers.\n");
  memcpy(&v6, &unk_100001F20, 0x2CuLL);
  memcpy(&v5, &unk_100001F50, 0x2AuLL);
  memcpy(&v4, &unk_100001F80, 0x2AuLL);
  if ( __stack_chk_guard != v52 )
    __stack_chk_fail(&v4, &unk_100001F80);
  return 0;
}
```
So we see a bunch of memory copy of some sort but what we find intresting is that all are `0x2AuLL` which are empty but 3 are `0x2CuLL` 
If we look at each of the 3 `&unk_100001???` location we find
```
x
0
0

x
0
0

etc..

```
And then we take each as a normal line we get
```
x00 x00 x00 x70 x61 x73 x74 x65 x62 x69 x00
x00 x00 x00 x6e x2e x63 x6f x6d x2f x36 x00
x00 x00 x00 x4e x51 x70 x51 x48 x73 x78 x00
```
which is hex, so we convert it to text we get `pastebin.com/6NQpQHsx` (remove the invalid characters inbetween)
If we check the site we get `rev_basic_c_cryptorave2017` which is not the flag. Cryptorave has a flag format so the correct flag is CR2017{rev_basic_c_cryptorave2017}.




