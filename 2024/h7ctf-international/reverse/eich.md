# Eich

## Challenge Description

"Technology is only as good as the people behind it" - Brendan Eich

Author: **Abu**

[ File-1: shutthefrontdoor](https://ctf.h7tex.com/files/851fea4b1217493d7ee86c6796b16ad4/shutthefrontdoor?token=eyJ1c2VyX2lkIjoxMzU4LCJ0ZWFtX2lkIjo2NDQsImZpbGVfaWQiOjIwfQ.ZvjZWw.ZExEEXLOozCmm6\_7sLXFo7xU1IQ)[   File-2: trap](https://ctf.h7tex.com/files/e0bab2d9d0958d179c1e52bfbfcb742a/trap?token=eyJ1c2VyX2lkIjoxMzU4LCJ0ZWFtX2lkIjo2NDQsImZpbGVfaWQiOjIxfQ.ZvjZWw.\_YeE9a5QfT2134qh573hP7t8HAE)

***

## Solution



[https://jsfuck.com/](https://jsfuck.com/)



[https://enkhee-osiris.github.io/Decoder-JSFuck/](https://enkhee-osiris.github.io/Decoder-JSFuck/)



```javascript
function A(D, length) {
  let key = "";
  for (let i = 0; i < length; i++) {
    key += D.charAt(i % D.length);
  }
  return key;
}
function B(F, D) {
  let key = A(D, F.length);
  let G = "";
  for (let i = 0; i < F.length; i++) {
    let charCode = F.charCodeAt(i);
    let keyCode = key.charCodeAt(i);
    let GChar = String.fromCharCode(charCode ^ keyCode);
    G += GChar;
  }
  return G;
}
const fs = require("fs");
let C = fs.readFileSync("C.txt", "utf8");
let D = "6aef677b2c8b645384e713aece4322b045a79f48";
let E = B(C, D);
console.log("Reward: ", E); // b3BlbnlvdXJleWVzYW5kbG9va2F0dGhlbWtleXNwcm9wZXJseQ==
```



<figure><img src="../../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>



```
Base64 Encoded Version:
b3BlbnlvdXJleWVzYW5kbG9va2F0dGhlbWtleXNwcm9wZXJseQ==

Base64 Decoded Version:
openyoureyesandlookatthemkeysproperly

Separated words with spaces
open your eyes and look at the m keys properly
```

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image 2.png" alt=""><figcaption></figcaption></figure>

```python
def generate_key(characters, length):
    key = ""

    for i in range(0, length):
        key += characters[i % len(characters)]

    return key

def decrypt(encrypted_text, characters):
    key = generate_key(characters, len(encrypted_text))

    decrypted = ""

    for i in range(0, len(encrypted_text)):
        decrypted += chr(ord(key[i]) ^ ord(encrypted_text[i]))

    return decrypted
        

if __name__ == "__main__":
    encrypted_text = open('trap', 'r').read()  
    characters = "whatthehelldoyouthinkyouaredoing"

    decrypted_text = decrypt(encrypted_text, characters)

    print(decrypted_text)
```

<figure><img src="../../../.gitbook/assets/image 3.png" alt=""><figcaption></figcaption></figure>



