# Client-side-again
Liam Reidy

**Instructions:** Can you break into this super secure portal? https://jupiter.challenges.picoctf.org/problem/56816/ (link) or http://jupiter.challenges.picoctf.org:56816

Inspecting the page's source code reveals (unsurprisingly) javascript code.
```js

  var _0x5a46=['37115}','_again_3','this','Password\x20Verified','Incorrect\x20password','getElementById','value','substring','picoCTF{','not_this'];(function(_0x4bd822,_0x2bd6f7){var _0xb4bdb3=function(_0x1d68f6){while(--_0x1d68f6){_0x4bd822['push'](_0x4bd822['shift']());}};_0xb4bdb3(++_0x2bd6f7);}(_0x5a46,0x1b3));var _0x4b5b=function(_0x2d8f05,_0x4b81bb){_0x2d8f05=_0x2d8f05-0x0;var _0x4d74cb=_0x5a46[_0x2d8f05];return _0x4d74cb;};function verify(){checkpass=document[_0x4b5b('0x0')]('pass')[_0x4b5b('0x1')];split=0x4;if(checkpass[_0x4b5b('0x2')](0x0,split*0x2)==_0x4b5b('0x3')){if(checkpass[_0x4b5b('0x2')](0x7,0x9)=='{n'){if(checkpass[_0x4b5b('0x2')](split*0x2,split*0x2*0x2)==_0x4b5b('0x4')){if(checkpass[_0x4b5b('0x2')](0x3,0x6)=='oCT'){if(checkpass[_0x4b5b('0x2')](split*0x3*0x2,split*0x4*0x2)==_0x4b5b('0x5')){if(checkpass['substring'](0x6,0xb)=='F{not'){if(checkpass[_0x4b5b('0x2')](split*0x2*0x2,split*0x3*0x2)==_0x4b5b('0x6')){if(checkpass[_0x4b5b('0x2')](0xc,0x10)==_0x4b5b('0x7')){alert(_0x4b5b('0x8'));}}}}}}}}else{alert(_0x4b5b('0x9'));}}

```

This looks really messy, but combing through it shows that the code is simply checking the password string a little bit at a time. It's calling random functions with a few different values. I thought the values were hex at first, but they only go from `0x0` to `0x7` All of these function calls together is:

`_0x4b5b('0x0') _0x4b5b('0x1') _0x4b5b('0x2') _0x4b5b('0x3') _0x4b5b('0x2') _0x4b5b('0x2') _0x4b5b('0x4') _0x4b5b('0x2') _0x4b5b('0x2') _0x4b5b('0x5') _0x4b5b('0x2') _0x4b5b('0x6') _0x4b5b('0x2') _0x4b5b('0x7')`

Let's translate each of these function calls, because several of them are the same: \
`_0x4b5b('0x0')` = "getElementById"\
`_0x4b5b('0x1')` = "value" \
`_0x4b5b('0x2')` = "substring" \
`_0x4b5b('0x3')` = "picoCTF{" \
`_0x4b5b('0x4')` = "not_this" \
`_0x4b5b('0x5')` = "3....}" \
`_0x4b5b('0x6')` = "_again_3" \
`_0x4b5b('0x7')` = "this"

Calls 0 to 2 don't look like a flag, but the rest do. They can be assembled into the final flag, `picoCTF{not_this...}`