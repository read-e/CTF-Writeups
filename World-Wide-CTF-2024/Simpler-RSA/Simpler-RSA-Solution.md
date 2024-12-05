# Simpler RSA
Liam Reidy

**Instructions:** RSA is so complicated! I made it simpler.

Here's the "RSA" we have to undo:

```python
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

Given that, we need to reverse it.

```python
c = (flag^p) % q
```

My incredibly short solution script is found in [sol.py](./sol.py)

Flag:

```
wwf{ju57_u53_l1br4r135}
```


