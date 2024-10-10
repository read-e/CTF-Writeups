# Sans Alpha
Liam Reidy

**Instructions:** The Multiverse is within your grasp! Unfortunately, the server that contains the secrets of the multiverse is in a universe where keyboards only have numbers and (most) symbols. \
Additional details will be available after launching your challenge instance.

We can't use the regular alphabet for this challenge, so I started by seeing what each special character did when input, but most of them didn't do anything. After playing with `*`, I found that it acted like the regular `*` wildcard in bash. For example:
```
SansAlpha$ /*
bash: /bin: Is a directory
```

I played with filepaths a bit, then I wanted to see what was in the current directory
```
SansAlpha$ ./*
bash: ./blargh: Is a directory

SansAlpha$ */*
bash: blargh/flag.txt: Permission denied
```

Well, there's the flag. I couldn't find anything else in this directory so I went back to the root, maybe there's something else there, or maybe I could use `/bin/cat` to print the file. I attempted to find files using `*`s and `?`s, but I kept getting `awk`. I tried executing `awk` but I kept getting an error, because even when trying to pipe the flag file into it, the wildcards forced it to run every 3 letter executable. I tried to see what else was in `/bin`, so I tested `/???/*( I tested 0-9)`, and I found a `base64` executable. I didn't know this was something that existed, but sure enough on *my* machine, it could print a file in base64.
```
liam$ base64 -i test.txt 
dGhpcyBpcyBhIHRlc3QgbWVzc2FnZQoK
```

All I needed to do now was call the executable with the flag as the argument:
```
SansAlpha$ /*/????64 */*
/bin/base64: extra operand '/bin/x86_64'
Try '/bin/base64 --help' for more information
```

That didn't work. It was doing the same thing that `awk` did, the wildcards returned more than one executable and was trying to use them both at once. I needed to keep the 64, but I wanted to get the string WITHOUT the 86. Using a wildcard cheatsheet (https://tldp.org/LDP/GNU-Linux-Tools-Summary/html/x11655.htm), I found that '[!]' is the logical NOT. So:
```
SansAlpha$ /*/?[!8][!6]?64 */*
/bin/base64: extra operand 'blargh/flag.txt'
Try '/bin/base64 --help' for more information.

SansAlpha$ /*/?[!8][!6]?64 */????????
...........djNyNTNfMTVfbTRkbjM1NV84YjNkODNhZH0=
```

And there's the flag in base64.
