# List3n!

## Question

Given a pcap file called l1st3n.cap. Your primary goal is to find the hidden flag within the provided PCAP (Packet Capture) file.

***

## Given File

{% file src="../../../.gitbook/assets/Packets.cap" %}

***

## Solution

<figure><img src="../../../.gitbook/assets/Untitled 0 (1).png" alt=""><figcaption></figcaption></figure>

Follow TCP Stream → `Ctrl + Alt + Shift + T`

<figure><img src="../../../.gitbook/assets/Untitled 1 (3).png" alt=""><figcaption></figcaption></figure>

```
Hey, how do you decrypt this file again?
You're serious?
Yeah, I'm serious
*sigh* openssl des3 -d -salt -in file.des3 -out file.txt -k supersecretpassword123
Ok, great, thanks.
Let's use Discord next time, it's more secure.
C'mon, no one knows we use this program like this!
Whatever.
Hey.
Yeah?
Could you transfer the file to me again?
Oh great. Ok, over 9002?
Yeah, listening.
Sent it
Got it.
You're unbelievable
```

<figure><img src="../../../.gitbook/assets/Untitled 2 (2).png" alt=""><figcaption></figcaption></figure>

Select packet no 57 as it contains the file.

Select the Data field and Right Click → Export Packet Bytes (`Ctrl + Shift + x`).

I saved the export file named `file.des3`.

<figure><img src="../../../.gitbook/assets/Untitled 3 (2).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/Untitled 4 (2).png" alt=""><figcaption></figcaption></figure>

**Flag:** `C3iCenter{N3tw0rkN1nj4}`
