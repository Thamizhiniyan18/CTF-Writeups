# Blame Game

## Challenge Description

Someone's commits seems to be preventing the program from working. Who is it?

You can download the challenge files here:

* [challenge.zip](https://artifacts.picoctf.net/c\_titan/157/challenge.zip)

***

## Solution

Download the given file and extract it. You can find .git directory in the given folder, which means git has been initialised. According to the given description, someone have changed the code and have committed without fixing it.&#x20;

To see all the changes to a file in all the commits in a Git repository, you can use the following command:

```bash
git log -p -- <file>
```

This command will display the commit history along with the changes made to the specified file. Each commit will be shown with a patch that illustrates the modifications made to the file.

<figure><img src="../../../.gitbook/assets/image (73).png" alt=""><figcaption></figcaption></figure>

Flag: `picoCTF{@sk_th3_1nt3rn_cfca95b2}`
