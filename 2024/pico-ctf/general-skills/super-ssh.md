# Super SSH

## Challenge Description

Using a Secure Shell (SSH) is going to be pretty important.

Can you `ssh` as `ctf-player` to `titan.picoctf.net` at port `50832` to get the flag?

You'll also need the password `84b12bae`. If asked, accept the fingerprint with `yes`.If your device doesn't have a shell, you can use: [https://webshell.picoctf.org](https://webshell.picoctf.org/)

If you're not sure what a shell is, check out our Primer: [https://primer.picoctf.com/#\_the\_shell](https://primer.picoctf.com/#\_the\_shell)

***

## Solution

Use the following command to connect to the target machine via SSH to get the flag.

```bash
ssh ctf-player@titan.picoctf.net -p <PORT>
```

<figure><img src="../../../.gitbook/assets/image (67).png" alt=""><figcaption></figcaption></figure>

Flag: `picoCTF{s3cur3_c0nn3ct10n_07a987ac}`
