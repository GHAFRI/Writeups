# [Banana Shopping](https://shellterlabs.com/en/questions/shx-4/shx4-banana-shopping/)
```
I bet you can't buy 72 bananas and pay 0 for it!
```

## Solution

We have this page:

![1](https://github.com/GHAFRI/Writeups/blob/master/Web/Shellterlabs/banana_shopping/1.png)

We try putting 72 in banana we get a total of 216. When we tried other fruits, we get a higher result. Also, when we insert a negative or high value we always get a higher result.
We start inspecting the code and enter `fruit.js`. Inside we have 
```
function DoSubmit(){
      document.getElementById("apple").value = Math.abs(parseInt(document.getElementById("apple").value));
      document.getElementById("banana").value = Math.abs(parseInt(document.getElementById("banana").value));
      document.getElementById("grape").value = Math.abs(parseInt(document.getElementById("grape").value));
      document.getElementById("lemon").value = Math.abs(parseInt(document.getElementById("lemon").value));
      document.getElementById("mango").value = Math.abs(parseInt(document.getElementById("mango").value));
      document.getElementById("watermelon").value = Math.abs(parseInt(document.getElementById("watermelon").value));
      return true;
}
```
Looks like the script takes our input, parse it to Int and the make it poitive by `Math.abs`. However, this only works within the broswer.
If we look into [Burp Suite](https://portswigger.net/burp/communitydownload), we can take the positive values from the `POST request` and change them to negative.
So when we tried `-72` for banana we got total of `-216`, so with simple maths, we look into lemon to be `-216` and hopefully the total will be 0.
we get

![2](https://github.com/GHAFRI/Writeups/blob/master/Web/Shellterlabs/banana_shopping/2.png)
