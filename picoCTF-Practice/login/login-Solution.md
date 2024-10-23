# login
Liam Reidy
**Instructions:** My dog-sitter's brother made this website but I can't get in; can you help? login.mars.picoctf.net

Viewing the page source mdae it clear there was javascript code being run locally. Viewing the file produced the following:
```
(async()=>{await new Promise((e=>window.addEventListener("load",e))),document.querySelector("form").addEventListener("submit",(e=>{e.preventDefault();const r={u:"input[name=username]",p:"input[name=password]"},t={};for(const e in r)t[e]=btoa(document.querySelector(r[e]).value).replace(/=/g,"");return"YWRtaW4"!==t.u?alert("Incorrect Username"):"cGljb0NURns1M3J2M3JfNTNydjNyXzUzcnYzcl81M3J2M3JfNTNydjNyfQ"!==t.p?alert("Incorrect Password"):void alert(`Correct Password! Your flag is ${atob(t.p)}.`)}))})();
```

As a part of the password check, it validates that `cGljb0NURns1M3J2M3JfNTNydjNyXzUzcnYzcl81M3J2M3JfNTNydjNyfQ` is the password. Translating this from Base64 produces the flag. `picoCTF{53rv3r_53rv3r...`
