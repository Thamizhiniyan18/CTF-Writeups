# CanYouSee

## Challenge Description

How about some hide and seek?

Download this file [here](https://artifacts.picoctf.net/c\_titan/129/unknown.zip).

***

## Solution

Download the given file and extract it. Use `exiftool` to extract the metadata from the given image.

<figure><img src="../../../.gitbook/assets/image (53).png" alt=""><figcaption></figcaption></figure>

In the Attribution URL Property there is a base64 encoded string, which is the flag.

<figure><img src="../../../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>

Flag: `picoCTF{ME74D47A_HIDD3N_b32040b8}`
