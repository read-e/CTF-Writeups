# Simpler RSA
Liam Reidy

***Instructions:** RSA is so complicated! I made it simpler.

```
from secret import flag
from Crypto.Util.number import bytes_to_long, getPrime

flag = bytes_to_long(flag)
p = getPrime(2048)
q = getPrime(2048)
c = pow(flag, p, q)  # i believe this is the fancy rsa encryption?
print(f'{p=}')
print(f'{q=}')
print(f'{c=}')
```

```
c = (flag^p) % q
```


```
wwf{ju57_u53_l1br4r135}
```


