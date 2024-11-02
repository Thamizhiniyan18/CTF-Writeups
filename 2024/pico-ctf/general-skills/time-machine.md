# Time Machine

## Challenge Description

What was I last working on? I remember writing a note to help me remember...

You can download the challenge files here:

* [challenge.zip](https://artifacts.picoctf.net/c\_titan/161/challenge.zip)

***

## Solution

Download the file and extract it. You can find a `.git` file in the current directory.

<figure><img src="../../../.gitbook/assets/image (70).png" alt=""><figcaption></figcaption></figure>

On viewing the contents of the `message.txt`, it seems like we have to check the history.

<figure><img src="../../../.gitbook/assets/image (71).png" alt=""><figcaption></figcaption></figure>

We can view the git history by using the `git log` command.

<figure><img src="../../../.gitbook/assets/image (72).png" alt=""><figcaption></figcaption></figure>

Flag: `picoCTF{t1m3m@ch1n3_8defe16a}`
