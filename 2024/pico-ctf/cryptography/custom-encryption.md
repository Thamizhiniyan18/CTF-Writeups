# Custom encryption

## Overview

Can you get sense of this code file and write the function that will decode the given encrypted file content.

Find the encrypted file here [flag\_info](https://artifacts.picoctf.net/c\_titan/93/enc\_flag) and [code file](https://artifacts.picoctf.net/c\_titan/93/custom\_encryption.py) might be good to analyze and get the flag.

***

## Solution

First download the given files.&#x20;

The custom\_encryption.py has the code that they used to encrypt the flag and the output file contains the values they used to do so and the final cipher.

I have made the following python script to decrypt the given cipher. After running the below script, you will get the flag.

```python
p = 97
g = 31
a = 88
b = 26
cipher = [97965, 185045, 740180, 946995, 1012305, 21770, 827260, 751065, 718410, 457170, 0, 903455, 228585, 54425, 740180, 0, 239470,
          936110, 10885, 674870, 261240, 293895, 65310, 65310, 185045, 65310, 283010, 555135, 348320, 533365, 283010, 76195, 130620, 185045]


def generator(g, x, p):
    return pow(g, x) % p


def decrypt(encryptedText, key):
    return [chr(each // (key * 311)) for each in encryptedText]


def dynamic_xor_decrypt(encrypted_text, text_key):
    plain_text = ""
    key_length = len(text_key)
    for i, each in enumerate(encrypted_text):
        key_char = text_key[i % key_length]
        plain_text += chr(ord(each) ^ ord(key_char))
    return plain_text[::-1]


u = generator(g, a, p)
v = generator(g, b, p)
key = generator(v, a, p)
b_key = generator(u, b, p)
shared_key = None

if key == b_key:
    shared_key = key
else:
    print("Invalid key")

semi_cipher = decrypt(cipher, shared_key)
plain_text = dynamic_xor_decrypt(semi_cipher, "trudeau")
print(plain_text)
```

Flag: `picoCTF{custom_d2cr0pt6d_019c831c}`
