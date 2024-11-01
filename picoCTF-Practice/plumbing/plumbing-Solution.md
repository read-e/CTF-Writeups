# plumbing
Liam Reidy

**Instructions:** Sometimes you need to handle process data outside of a file. Can you find a way to keep the output from this program and search for the flag? Connect to jupiter.challenges.picoctf.org 14291.

It doesn't say how to connect, but I assumed it meant netcat `nc jupiter.challenges.picoctf.org 14291`.

On the connection, it printed out so much text that maxed out my terminal's history, it wouldn't let me scroll to the top. Hoping the flag was a part of the output (just further up) I tried piping the output of nc to a file:

```bash
nc nc jupiter.challenges.picoctf.org 14291 > output.txt
```

That seemed to work, looking at the output file it is quite large.
```
-rw-r--r--@ 1 liam  ------  288014 ------- output.txt
```

Sure enough, using grep to search the output file returned the flag!
```
grep 'pico' output.txt
```
