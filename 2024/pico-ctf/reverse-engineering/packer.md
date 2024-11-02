# Packer

## Challenge Description

Reverse this linux executable?

[binary](https://artifacts.picoctf.net/c\_titan/101/out)

***

## Solution

First download the given file. I used the `file` command to check the file type. The given file is a linux executable.

<figure><img src="../../../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

Next I run the application to check what its up to.

<figure><img src="../../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>

The given application prompts for password to unlock the file. Since, the challenge name is packer I just used the `strings` command and looked out for the keyword packer.

<figure><img src="../../../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>

From the output of the `strings` command, we can see that the give file is packer using `upx` packer.

So I used the `upx` tool to decompress the given file. The command is `upx -d out`.

<figure><img src="../../../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

After unpacking the file, I opened the file with [Cutter](https://github.com/rizinorg/cutter), to view the decompiled source code. In the main function, I found the hex encoded flag.

<figure><img src="../../../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>

I used CyberChef to decode the hex string to get the flag.

<figure><img src="../../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

Flag: `picoCTF{U9X_UnP4ck1N6_B1n4Ri3S_e190c3f3}`
