# Dumped

## Question

Sam has JTAG mobile Extraction for a handset in a forensic case.

***

## Given File

{% file src="../../../.gitbook/assets/dump.7z" %}

Extract the above file using 7zip to get the challenge file.

***

## Solution

{% code overflow="wrap" %}
```bash
binwalk -D="_*" dump.bin

# Where,
#  -D : Extract <type> signatures (regular expression), give the files an extension of <ext>, and execute <cmd>
```
{% endcode %}

<figure><img src="../../../.gitbook/assets/Untitled (1).png" alt=""><figcaption></figcaption></figure>

The above command extracted the files to a folder named `_dump.bin.extracted`.

<figure><img src="../../../.gitbook/assets/Untitled 1 (1).png" alt=""><figcaption></figcaption></figure>

Found the flag in a file named `9ABFF`.

**Flag:** `Flag{Remember_header_then_footer}`
