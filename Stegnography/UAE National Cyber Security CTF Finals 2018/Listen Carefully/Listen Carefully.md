# Listen Carefully

![0](https://github.com/GHAFRI/Writeups/blob/master/Stegnography/UAE%20National%20Cyber%20Security%20CTF%20Finals%202018/Listen%20Carefully/Listen%2Bcarefully.jpg)

We are given an Image file that is large enough to have something hidden in it.
So we start of by using `HxD` to look for anything hidden in the hex code, as we scroll down we find this.

![1](https://github.com/GHAFRI/Writeups/blob/master/Stegnography/UAE%20National%20Cyber%20Security%20CTF%20Finals%202018/Listen%20Carefully/1.PNG)

It's `WAVE` file signature so we extract everything beggining with `RIFFX` to the end and we end up with a sound file. To deal with sound files, we use `Audacity`.
So we start of by switching from `Waveform` to `Spectogram` of the file and we find a hash.

![2](https://github.com/GHAFRI/Writeups/blob/master/Stegnography/UAE%20National%20Cyber%20Security%20CTF%20Finals%202018/Listen%20Carefully/2.png)

Turns out that this is the flag.

![3](https://github.com/GHAFRI/Writeups/blob/master/Stegnography/UAE%20National%20Cyber%20Security%20CTF%20Finals%202018/Listen%20Carefully/3.png)








