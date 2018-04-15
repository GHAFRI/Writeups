# Q.R.E.A.M. - 400
```
I can't think of a clever description. 
Just follow the trail -- but there's no telling how deep the rabbit hole goes.

Flag is in format: flag{...}
```

## Solution

Basically, here we see `QR code` image file that we just need to scan.
This redirects us to an `Imgur` link, which also has another `QR` which also redirects to an `Imgur` link that also has another `QR` code and so on. As simple as it looks, new players will just go down the rabbit hole manually and from experience I know how far that rabbit hole can go when they coded the question.

So to reverse this, we created a very simple QR python code that downloads the `Imgur` image and reads it then go to that link again in a loop.
```Python
from pyzbar.pyzbar import decode
from PIL import Image
import numpy as np
from urllib import request

while True:
    x = decode(Image.open(r'C:\1.jpg'))
    y = ''.join(map(str,x))
    z = y.split("'")
    img = z[1]
    request.urlretrieve(img,r"C:\1.jpg")
```

After this code, we will recieve a URL error
```Python
    raise ValueError("unknown url type: %r" % self.full_url)
ValueError: unknown url type: 'flag{QR_Rules_Everything_Around_Me_QREAM}'
```

Simply, the flag is `flag{QR_Rules_Everything_Around_Me_QREAM}`

### What I learned

Nothing, it's so simple.


