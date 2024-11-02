# Secret of the Polyglot

## Challenge Description

The Network Operations Center (NOC) of your local institution picked up a suspicious file, they're getting conflicting information on what type of file it is. They've brought you in as an external expert to examine the file. Can you extract all the information from this strange file?

Download the suspicious file [here](https://artifacts.picoctf.net/c\_titan/97/flag2of2-final.pdf).

***

## Solution

Download the given file and extract it. You are provided with a pdf file.

<figure><img src="../../../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

I opened the pdf file, it contained the second part of the flag.

<figure><img src="../../../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>

Since the challenge name has the word is polyglot, which means polyglots are files that are a valid form of multiple different file types. So I checked the file type of the given pdf using the file command.

<figure><img src="../../../.gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure>

From the output of the file command we can see that the given file is a image file. So I renamed the given pdf file to `.png` using the `cp` command.

<figure><img src="../../../.gitbook/assets/image (63).png" alt=""><figcaption></figcaption></figure>

On opening the renamed file, got the first part of the flag.

<figure><img src="../../../.gitbook/assets/image (61).png" alt=""><figcaption></figcaption></figure>

Flag: `picoCTF{f1u3n7_1n_pn9_&_pdf_724b1287}`
