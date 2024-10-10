# St3go
Liam Reidy

**Instructions:** Download this image and find the flag.

This challenge was simple, it only required use of *zsteg* (https://github.com/zed-0xff/zsteg). *zsteg* is a tool that extracts hidden data from PNG and BMP images.

Using the command:
```
zsteg -a pico.flag.png
```

The flag is immediately produced:
```
b1,rgb,lsb,xy       .. text: "picoCTF{7h3..............}$t3g0"
b1,abgr,lsb,xy      .. text: "E2A5q4E%uSA"
b2,b,lsb,xy         .. text: "AAPAAQTAAA"
b2,b,msb,xy         .. text: "HWUUUUUU"
b2,a,lsb,xy         .. file: Matlab v4 mat-file (little endian) ><?P, numeric, rows 0, columns 0
...
```

Copying the flag without '$t3g0' at the end gives us the correct flag.