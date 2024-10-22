# Search source
Liam Reidy

**Instructions:** The developer of this website mistakenly left an important artifact in the website source, can you find it? Additional details will be available after launching your challenge instance.

The website had too many scripts and style sheets for me to parse through, so I downloaded all it's data with:
```
wget --mirror http://saturn.picoctf.net:62130
```

Searching all the files with `grep` got me the flag:
```
grep pico -r *

css/style.css:/** banner_main picoCTF{1nsp3ti0n......} **/
```