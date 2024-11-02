# No Paste

## Challenge Description

"If you spend too much time thinking about a thing, you'll never get it done. Paste it up, cut it out, and just do it" — Unknown

[Link](https://paste.h7tex.com/)

Author - **Abu**

***

## Solution



<figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (122).png" alt=""><figcaption></figcaption></figure>



<figure><img src="../../../.gitbook/assets/image (121).png" alt=""><figcaption></figcaption></figure>

```python
import requests

wordlist = [
                '1324128AFJEVv',
                '7068GqiGjD',
                'challengeInput',
                '2125DmXkHA',
                'result',
                'textContent',
                'value',
                'POST',
                '5588288xDHxaF',
                'bypass123',
                'then',
                'addEventListener',
                'getElementById',
                '/submit?input=',
                'Flag:\x20',
                'error',
                '1026jodAtA',
                '393500Fwnrwo',
                'paste',
                '793504lbHmgC',
                '32613VrGzuS',
                'flag',
                '801iQqFPw',
                'success',
                'keydown',
                '965970xJmNwA'
            ]

url = "https://paste.h7tex.com/submit?input="

for word in wordlist:
    response = requests.post(url + word)

    response_json = response.json()

    if 'flag' in response_json:
        print(f"Valid Input: {word}")
        print(f"Payload: POST {url + word}")
        print(f"Flag: {response_json['flag']}")

        break
```

<figure><img src="../../../.gitbook/assets/image (123).png" alt=""><figcaption></figcaption></figure>



**Flag:** `H7CTF{h@ck_th3_sy$t3m}`
