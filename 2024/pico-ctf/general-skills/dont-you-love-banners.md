# dont-you-love-banners

## Challenge Description

Can you abuse the banner?

Additional details will be available after launching your challenge instance.

***

## Solution

First start the instance. I used nmap to scan the on the first port that was given and got a suspicious string from the banner of the service.

<figure><img src="../../../.gitbook/assets/image (119).png" alt=""><figcaption></figcaption></figure>

Next I used the given nc command to interact with the challenge instance and it prompted for password. I used the suspicious string we got in the nmap scan as the password and it worked. It asked some more questions and after answering them I got the normal shell prompt. I tried to view the `/root/flag.txt`, but permission denied.

<figure><img src="../../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

To access the flag, we have to escalate our privileges. According to one of the hints given, we have to do some password cracking. So I checked whether `/etc/shadow` was accessible and it was. So I grabbed the root users entry from `/etc/passwd` and put it in a file named `p.txt` in my local machine.

<figure><img src="../../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

Next I grabbed the root users entry from `/etc/shadow` and put it in a file named `s.txt` in my local machine.

<figure><img src="../../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

Now use the `unshadow` command on the files that we created. The `unshadow` tool combines the passwd and shadow files so John can use them. I redirected the output of the `unshadow` command to a file named `hash.txt`.

<figure><img src="../../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

Now use john on the hash.txt file to crack the password.

<figure><img src="../../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

Now use the password we got cracked to escalate our privileges and grab the flag.

<figure><img src="../../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

Flag: `picoCTF{b4nn3r_gr4bb1n9_su((3sfu11y_218ef5d6}`
