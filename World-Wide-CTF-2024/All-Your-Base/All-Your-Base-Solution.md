# All your base are belong to us
Liam Reidy

**Instructions:** Base 32? Sure.
Base 64? Yeah I know that one.
Base 2^16? ?????????

`MkpIbmdFcWs4MzVjR3BHRXFVVnZtZWJUQWtSTlNNamE1dGZYQTdwR25ac203SnJQV2FyTUdHQnA3Uk1XZDNZVFlTNTJjemVya1BCN0dBY2NBNkN4U1VBS29TalVBOU1tR1EyYUF0UVlHZTFYOXp1TThWS2o1OHdKRFJaVXhzTGRaZUpaTGV6NUFWc2JHdm5CbTdjV28yNTRyWGpzQURYdEhkSmJmWmtGREVEQWZWeEhFeDNYanNNODZMZVo2cnM2NExGbU5QeG1mUXBqQ3BoY3pCczlRa3kySnFZb1JzSnFtUnk0cW02WFgyOU50N1g2Vg`

2^16 is 65536, and base65536 is something that exists!

https://github.com/Parkayun/base65536

```python
>>> import base65536
>>> a = base65536.encode(b"Hello World")
>>> print(a)
驈ꍬ啯ꍲᕤ
>>> print(base65536.decode(a))
Hello World
```

I tried the input with this program and got "not valid base65536 input error". That made a little sense, the examples of base65536 that it displayed had a lot of Chinese characters. Back to old reliable.

In cyberchef, going from `Base64` > `Base58` > `Base32` > `Base85`
`𔕷𠅦𖥣桢顲桨鑦敤𓅥𓉮鵟𔐴鐳ꌴ鑬鵴鐳𐘴𔕳𓀳鑳𔔴敧栴鬲ᕽ` 


The new string looks like test from the example (it has Chinese characters)

```python
b = "𔕷𠅦𖥣桢顲桨鑦敤𓅥𓉮鵟𔐴鐳ꌴ鑬鵴鐳𐘴𔕳𓀳鑳𔔴敧栴鬲ᕽ"
>>> print(base65536.decode(b))
b'wwf{cyb3rch3f_d0esnt_h4v3_4ll_th3_4nsw3rs_4wg0432f}'
```