#Liar (50 Points)
## Problem
I may or may not have illegally bought this [file](https://www.easyctf.com/static/problems/png/secret) from someone who claims that it contains secret pictures of my friend and her fiancé. Unfortunately, I can't open it, and I already paid $4096 for it. Can you help me find out if the seller was lying?

## Hint:
I feel like something is missing . . .

## Solution:
I first opened the file in this [hex editior](http://mh-nexus.de/en/hxd/). The header of the file, `50 4B 03 04`, was revealed to be for a PKZIP file by a quick search at this great [file signature list](http://www.garykessler.net/library/file_sigs.html). Renaming the file to a .zip file. Inside the zip file we see the secret.png file, but it won't open. I opened the image in the same hex editor. In the editor, we see that it has the trailer for a .png file, `49 45 4E 44 AE 42 60 82`, but the header is missing four bits. Add `89 50 4E 47` to the very beginning of the file and save it. The image opens correctly now, to a picture of a troll with the flag painted on. Funny.



## Flag: easyctf{troll3d}
