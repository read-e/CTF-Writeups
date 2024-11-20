# FindAndOpen
Liam Reidy

**Instructions:** Someone might have hidden the password in the trace file. Find the key to unlock this file. This tracefile might be good to analyze.

We are given a zip file and packet capture. I tried to find the zip password from the hash of it with `zip2john` and `john` but it kept exiting early, no easy way out this time.

The packet capture is pretty short, which made searching through it quite easy. Packet `48` has this as its data:

`VGhpcyBpcyB0aGUgc2VjcmV0OiBwaWNvQ1RGe1IzNERJTkdfTE9LZF8=`

This is very clearly a string encoded with base64. It translates to

```
This is the secret: picoCTF{R34DING_LOKd_
```

Expecting to find more base64 strings in the packet capture I kept looking through packets. Some of the later packets suggested looking at "the other file". Having nothing else to go off, I used `picoCTF{R34DING_LOKd_` as the password for the zip, and sure enough it opened.

```bash
$ ~/Downloads unzip flag.zip
Archive:  flag.zip
[flag.zip] flag password:
 extracting: flag
$ ~/Downloads cat flag
picoCTF{R34DING_LOKd_fil56_succ3ss...2}
```