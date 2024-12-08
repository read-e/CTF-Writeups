# Special
Liam Reidy

**Insturctions:** Don't power users get tired of making spelling mistakes in the shell? Not anymore! Enter Special, the Spell Checked Interface for Affecting Linux. Now, every word is properly spelled and capitalized... automatically and behind-the-scenes! Be the first to test Special in beta, and feel free to tell us all about how Special streamlines every development process that you face. When your co-workers see your amazing shell interface, just tell them: That's Special (TM)

Pressing tab doesn't show what commands we have available, so let's see where we are.

```bash
Special$ pwd
Pod 
sh: 1: Pod: not found
Special$ ls
Is 
sh: 1: Is: not found
Special$ whoami
Whom 
sh: 1: Whom: not found
```

Great, it doesn't want to let me use normal commands either. What about wildcards?

```bash
Special$ ./*
./* 
sh: 1: ./blargh: Permission denied
```

Okay, do I not have executable permissions, or is this not an executable? Maybe it's a directory?

```bash
Special$ */*
*/* 
sh: 1: blargh/flag.txt: Permission denied
Special$ ./*/*
./*/* 
sh: 1: ./blargh/flag.txt: Permission denied
```

We found the flag, now we just need to view it.

```bash
Special$ /bin/cat */*
Absolutely not paths like that, please!
```

If it doesn't like the absolute filepath, maybe relative will work.

```bash
Special$ ../../../../bin/cat */*
../../../../bin/cat */* 
picoCTF{5p311ch3ck_15_7h3_w0r57_b741d1b1}
```

It did! There's the flag.