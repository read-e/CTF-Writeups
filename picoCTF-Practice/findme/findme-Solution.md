# findme
Liam Reidy

**Instructions:** Help us test the form by submiting the username as test and password as test! The website running here.

I immediately put the website into burp suite and turned on intercept. Loading the page looked normal, and I decided to try the specified username of `test` and password of `test!`. Because I had intruder on, I noticed two of the following HTTP GET requests started with the following:

```
GET /next-page/id=cGljb0NURntwcm94aWVzX2Fs HTTP/1.1
```
and
```
GET /next-page/id=bF90aGVfd2F5XzAxZTc0OGRifQ== HTTP/1.1
```

Translatig both of the base64 and putting them together give us the flag:
```
picoCTF{proxies_all_the_way_01e748db}
```

After the GET requests were accepted, there was a page where we can "search for flags," but considering I already found it, I think this was a red herring.

This challenge was listed as a medium difficulty challenge, but the only real challenge was knowing to use burp suite and recognize base64.