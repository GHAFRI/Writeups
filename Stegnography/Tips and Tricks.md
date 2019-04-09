# Set of tips and tricks I used to solve some challanges:
## [Python Steganography](https://pypi.org/project/steganography/0.1.1/)
I used this tool to solve a challange:  
`steganography -d file.jpg`

## RBG Planes
If you have an image opened in `stegsolve` and you see a small portion of it visible in a set of planes like in only `red plane 0`, `blue plane 0` and `green place 0` then you can create a preview regarding those bit planes and find the flag in the header.

## Whitespace
if you come across a challange that has white space in it, then its not a couincidence, use this tool:  
`http://vii5ard.github.io/whitespace/`  
it will save you big time.

## Thumbnail:
If you come accross an image that has a thumbnail using `exiftool` then you can simple extract it using  
`exiftool -b -ThumbnailImage image.jpg > thumb1.jpg`  
if the new image also has another thumbnail then repeat the above command.

## Video that shows text:
### There Are 2 ways to solve this:
### #1:
use `ffmpeg` tool to extract each frame image of the video:  
`ffmpeg -i video.mp4 -vf "fps=1" out%0d.png`  
then we use `tesseract`, an OCR engine to extract text from the image:  
```
for file in $(ls . | grep png); do
    echo "image:${file}";
    tesseract $file - | grep -i flag
done
```

### #2:
we use `mplayer` that uses `ffmpeg` to extract each frame image.   
`mplayer -vf framestep=60 -framedrop -nosound video.mp4 -speed 100 -vo jpeg:outdir=video`  
and then we OCR it to text files  
`cd video; ls *.jpg | xargs -t -i tesseract {} {}`  
and finally we `grep flag`  
`grep -Ri "flag" *.txt`
