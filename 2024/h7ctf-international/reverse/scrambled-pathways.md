# Scrambled Pathways

## Challenge Description

In this challenge, characters follow a hidden pattern as they traverse columns. Figure out how to untangle the message and reveal the flag!

Author : **PattuSai**

[ chall1](https://ctf.h7tex.com/files/bba2cefb4252b6f68cc673c4594cb79a/chall1?token=eyJ1c2VyX2lkIjoxMzU4LCJ0ZWFtX2lkIjo2NDQsImZpbGVfaWQiOjI2fQ.ZvjZww.96F8dWWkls3TzLqIEK5hQypBjHo)[ out1.txt](https://ctf.h7tex.com/files/58ee91b70755aa33359f1d0050fee1b1/out1.txt?token=eyJ1c2VyX2lkIjoxMzU4LCJ0ZWFtX2lkIjo2NDQsImZpbGVfaWQiOjI3fQ.ZvjZww.nN0wsvzWzkRhniVVeCh50KSm8wA)

***

## Solution

```python
# Got from the out1.txt file
encrypted_flag = "HT859092947c87F4cff7727181C{872a2ba640}"

len_encrypted_flag = len(encrypted_flag)

decrypted_flag = [0] * len_encrypted_flag

positions = []

for i in range(0, 3):
    for j in range(i, len_encrypted_flag, 3):
        positions.append(j)

for i, j in enumerate(positions):
    decrypted_flag[j] = encrypted_flag[i]

print("".join(decrypted_flag))
```



<figure><img src="../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>
