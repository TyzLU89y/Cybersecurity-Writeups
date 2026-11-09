# Client-side-again

- **Platform:** CyLab academy(PicoCTF)
- **Category:** Web
- **Difficulty:** Medium

## Challenge

Can you break into this super secure portal?

## Solution

1. After accessing the website, we can see a textbox that requires us to submit a password. After trying some common passwords with little results. I decided to inspect the source code, and we can see a big chunck of obfuscated js code:
```
 var _0x5a46=['7f88c}','_again_1','this','Password\x20Verified','Incorrect\x20password','getElementById','value','substring','academy{','not_this'];(function(_0x4bd822,_0x2bd6f7){var _0xb4bdb3=function(_0x1d68f6){while(--_0x1d68f6){_0x4bd822['push'](_0x4bd822['shift']());}};_0xb4bdb3(++_0x2bd6f7);}(_0x5a46,0x1b3));var _0x4b5b=function(_0x2d8f05,_0x4b81bb){_0x2d8f05=_0x2d8f05-0x0;var _0x4d74cb=_0x5a46[_0x2d8f05];return _0x4d74cb;};function verify(){checkpass=document[_0x4b5b('0x0')]('pass')[_0x4b5b('0x1')];split=0x4;if(checkpass[_0x4b5b('0x2')](0x0,split*0x2)==_0x4b5b('0x3')){if(checkpass[_0x4b5b('0x2')](0x7,0x9)=='{n'){if(checkpass[_0x4b5b('0x2')](split*0x2,split*0x2*0x2)==_0x4b5b('0x4')){if(checkpass[_0x4b5b('0x2')](0x3,0x6)=='dem'){if(checkpass[_0x4b5b('0x2')](split*0x3*0x2,split*0x4*0x2)==_0x4b5b('0x5')){if(checkpass['substring'](0x6,0xb)=='y{not'){if(checkpass[_0x4b5b('0x2')](split*0x2*0x2,split*0x3*0x2)==_0x4b5b('0x6')){if(checkpass[_0x4b5b('0x2')](0xc,0x10)==_0x4b5b('0x7')){alert(_0x4b5b('0x8'));}}}}}}}}else{alert(_0x4b5b('0x9'));}}
```
2. We can see above that we have a interesting array with hints of a flag like string scattered accross. We could just simply piecethem together and get our flag. 

3.That being said, let's inspect this code. After deobfuscating the code and renaming functions using a [deobfuscator](https://deobfuscate.io/), we can get the following code:
```
var donene = ["7f88c}", "_again_1", "this", "Password Verified", "Incorrect password", "getElementById", "value", "substring", "academy{", "not_this"];
(function (tanishi, noris) {
  var jarmain = function (marranda) {
    while (--marranda) {
      tanishi.push(tanishi.shift());
    }
  };
  jarmain(++noris);
}(donene, 435));
var zafirah = function (jahyr, anapaola) {
  jahyr = jahyr - 0;
  var tiembra = donene[jahyr];
  return tiembra;
};
function verify() {
  checkpass = document[zafirah("0x0")]("pass")[zafirah("0x1")];
  split = 4;
  if (checkpass[zafirah("0x2")](0, split * 2) == zafirah("0x3")) {
    if (checkpass[zafirah("0x2")](7, 9) == "{n") {
      if (checkpass[zafirah("0x2")](split * 2, split * 2 * 2) == zafirah("0x4")) {
        if (checkpass[zafirah("0x2")](3, 6) == "dem") {
          if (checkpass[zafirah("0x2")](split * 3 * 2, split * 4 * 2) == zafirah("0x5")) {
            if (checkpass.substring(6, 11) == "y{not") {
              if (checkpass[zafirah("0x2")](split * 2 * 2, split * 3 * 2) == zafirah("0x6")) {
                if (checkpass[zafirah("0x2")](12, 16) == zafirah("0x7")) {
                  alert(zafirah("0x8"));
                }
              }
            }
          }
        }
      }
    }
  } else {
    alert(zafirah("0x9"));
  }
}
```
We can see that the `verify()` takes substrings of the password and check it with the values in the array. After walking through the function, we can also piece together the password: `academy{not_this_again_17f88c}` which is also the flag. 
## Flag

`academy{not_this_again_17f88c}`

## Key Takeaway

Client side checking is not very secure since the client can inspect and modify the code. Obfuscating the code provides a sence of security but it is still possible to decode. 

## References

- [https://learn.cylabacademy.org/library/69]
