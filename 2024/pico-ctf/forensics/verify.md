# Verify

## Challenge Description

People keep trying to trick my players with imitation flags. I want to make sure they get the real thing! I'm going to provide the SHA-256 hash and a decrypt script to help you know that my flags are legitimate.

You can download the challenge files here:

* [`challenge.zip`](https://artifacts.picoctf.net/c\_rhea/21/challenge.zip)

Additional details will be available after launching your challenge instance.

***

## Solution

First start the instance and login via ssh to the given instance. We are given with two files and a folder.

<figure><img src="../../../.gitbook/assets/image (47).png" alt=""><figcaption></figcaption></figure>

The `checksum.txt` file contains the hash sum of some file.

<figure><img src="../../../.gitbook/assets/image (52).png" alt=""><figcaption></figcaption></figure>

The `decrypt.sh` file is a bash script, which tries to decrypt a file.

<figure><img src="../../../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>

Next I checked the files directory. It has a lot of files. One of these files has the flag in encrypted form. We have to decrypt that file using the `decrypt.sh` file. We have to decrypt each file in this directory to find the flag.

<figure><img src="../../../.gitbook/assets/image (49).png" alt=""><figcaption></figcaption></figure>

I used a bash while loop to get the job done. Use the following command to get the flag.

```bash
ls -R | while read filename; do ./decrypt.sh ./files/$filename 2>/dev/null; done | grep picoCTF
```

<figure><img src="../../../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>

Flag: `picoCTF{trust_but_verify_e018b574}`
