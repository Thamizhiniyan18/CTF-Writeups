# interencdec

## Overview

Can you get the real meaning from this file.

Download the file [here](https://artifacts.picoctf.net/c\_titan/109/enc\_flag).

***

## Solution

The give string is a base64 decoded string. I used Cyber chef to decode the given string.

<figure><img src="../../../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

```url
https://gchq.github.io/CyberChef/#recipe=From_Base64('A-Za-z0-9%2B/%3D',true,false)Find_/_Replace(%7B'option':'Regex','string':'%5Bb%5C'%5D'%7D,'',true,false,true,false)From_Base64('A-Za-z0-9%2B/%3D',true,false)ROT13(true,true,false,19)&input=WWlka00wSnhaR3R3UWxSWWRIRmhSM2cyWVVoc1ptRjZUbkZsVkd3eldWUk9jbGd5TUhkTmFrVjVUbnBWTkdaUlBUMG5DZz09
```

Flag: `picoCTF{caesar_d3cr9pt3d_f0212758}`
