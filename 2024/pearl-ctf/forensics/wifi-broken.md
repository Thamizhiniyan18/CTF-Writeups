# Wifi Broken

## Challenge Description

I suspect my former friend is upto something wrong. I tried to access his network but for that, I need the password to his wifi. Enclose the password in pearl{} when you find it.

### Attachments

{% file src="../../../.gitbook/assets/findme.cap" %}

***

## Solution

Basically, aircrack-ng takes each word and tests to see if this is in fact the pre-shared key.

So you can crack the wifi password using `aircrack-ng` using the following command:

`aircrack-ng -w /usr/share/wordlists/rockyou.txt findme.cap`

<figure><img src="../../../.gitbook/assets/image (111).png" alt=""><figcaption></figcaption></figure>

Flag: `pearl{shenoydx}`
