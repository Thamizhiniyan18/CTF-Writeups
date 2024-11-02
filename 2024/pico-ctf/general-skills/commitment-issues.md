# Commitment Issues

## Challenge Description

I accidentally wrote the flag down. Good thing I deleted it!

You download the challenge files here:

* [challenge.zip](https://artifacts.picoctf.net/c\_titan/137/challenge.zip)

***

## Solution

Download the file and extract it. You can find a `.git` file in the current directory.

<figure><img src="../../../.gitbook/assets/image (69).png" alt=""><figcaption></figcaption></figure>

I checked git log for previous commits and found two commits. On reverting to the first commit, got the flag.

<figure><img src="../../../.gitbook/assets/image (68).png" alt=""><figcaption></figcaption></figure>

Flag: `picoCTF{s@n1t1z3_cf09a485}`
