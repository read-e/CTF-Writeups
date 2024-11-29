# mus1c
Liam Reidy

**Instructions:** I wrote you a song. Put it in the picoCTF{} flag format.

Hint: Do you think you can master rockstar?

The hint indicates that 'rockstar' is a method of encoding. A quick google search shows that it's actually a programming language.

https://codewithrockstar.com/

```
Pico's a CTFFFFFFF
my mind is waitin
It's waitin

Put my mind of Pico into This
my flag is not found
put This into my flag

...

shout it
shout it

build it up, up
shout it
shout Pico
```

I used the website to decode the 'rockstar' code, and got this as the output:

```
114 114 114 111 99 107 110 114 110 48 49 49 51 114
```

Looks like ascii, and it is. Here's what it translates to:

```
rrrocknrn0113r
```

So the flag is `picoCTF{rrrocknrn0113r}`
