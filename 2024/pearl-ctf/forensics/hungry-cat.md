# hungry-cat

{% embed url="https://pearlctf.in/challenges#hungry-cat-8" %}

## Challenge Description

Your friend's system crashed just as he was about to access crucial instructions on what to feed his cat on internet. He's now turned to you for help in retrieving this information from the system dump. Can you assist him in piecing together the lost instructions for feeding his feline friend?

### Attachments

{% embed url="https://store.pearlctf.in/hungry-cat.7z" %}

***

## Solution

Extract the given 7zip file using 7zip.

{% embed url="https://www.7-zip.org/download.html" %}

In my case I used the command: `7z e hungry-cat.7z`.

After Extracting the file, I used `strings` command on the file and piped it to the grep command looking out for strings starting with `pearl` and found the flag successfully.

<figure><img src="../../../.gitbook/assets/image (116).png" alt=""><figcaption></figcaption></figure>
