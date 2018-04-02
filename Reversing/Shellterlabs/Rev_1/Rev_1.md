# Rev 1
```
The flag is in the file. 

Tip1: Ta within 

Format: R00T _ @ _ RSi {su4_fl4g}
```

## Solution:

We start of by checking the file format by `file <name>` and we see `Java archive data (JAR)`.
We run it and we get this

![1]()

It seems like a messaging app that has a login and register form.
To decompile `Jar` files we use [Jadx](https://github.com/skylot/jadx).
If we look at the `Login` class we see 2 classes and a cipher function
```
	public static String m2u(String str) {
        return Login_Page.cipher("ebbg@efv");
    }

    /* renamed from: p */
    public static String m1p(String str) {
        return Login_Page.cipher("c0q33age4ee00g");
    }


    public static String cipher(String str) {
        char[] toCharArray = str.toCharArray();
        for (int i = 0; i < toCharArray.length; i++) {
            char c = toCharArray[i];
            if (c >= 'a' && c <= 'z') {
                c = c > 'm' ? (char) (c - 13) : (char) (c + 13);
            } else if (c >= 'A' && c <= 'Z') {
                c = c > 'M' ? (char) (c - 13) : (char) (c + 13);
            }
            toCharArray[i] = c;
        }
        return new String(toCharArray);
    }
```

We have the username and password but it seems that the `cipher` function `decrypts` them with a `shift` of `13` as indicated.
So, we get `ebbg@efv` -> `root@rsi` and `c0q33age4ee00g` -> `p0d33ntr4rr00t`.
Now, we just login with those and we get the flag `R00T_@_RSi{j4v4_1ts_4_j0k3}`.

