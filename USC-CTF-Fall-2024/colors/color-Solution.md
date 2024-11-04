# colors
Liam Reidy

**Instructions:** Can you decode the message?

Message:
```
MzAgMzEgMzAgMzAgM...MzEgMzEgMzAgMzE=%
```

The message is long, but very clearly in base64 format. Converting it using Cyberchef (https://gchq.github.io/CyberChef) gives us what looks like hex/ascii characters:
```
30 31 30 30 30 30...30 20 30 31 31 31 31 31 30 31
```

Converting that from hex, we get a string of binary:
```
01000011 01011001...01111101
```

From binary, we get the flag:
```
CYBORG{tR...d}
```