# EncryptDecryptFile
Liam Reidy

**Instructions:** My brother deleted an important file from the encrypt-decrypt-file repository

After opening the zip, I noticed that there was `.hg` directory. Google told me this has to do with Mercurial, a version control software like git. Reverting all the changes created a file named `flag.enc`.

```
$ hg revert --all
reverting flag.enc
```
\
The python program required some specific arguments:
```
$ python3 ./main.py
usage: main.py [-h] [--encrypt] [--decrypt] --input INPUT --output OUTPUT
main.py: error: the following arguments are required: --input, --output
```
so to unencrypt the file I used:
```
python3 ./main.py --decrypt --input flag.enc --output out
```

\
This still looked like a jumbled encrypted mess, so I tried running unencrypt on it again, but the "block size" didn't match. Instead, I wanted to see what type of file `out` was, so I trired the file command:
```
$ file out
out: PNG image data, 1000 x 100, 8-bit/color RGBA, non-interlaced
```

Well, that saved some time from not having to brute force the file extensions. Renaming the `out` file to have a `.png` file extension revealed an image with the flag visible.

For me, the hardest part of this challenge was running the python program. Not because I can't read arguments, but because python on my laptop is all messed up. I have to use Anaconda for a class and I think it's messing with my regular installation, I couldn't get the Crypto library to work without reinstalling it and going through Anaconda.
