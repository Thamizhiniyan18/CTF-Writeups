# endianness

## Challenge Description

Know of little and big endian?

Additional details will be available after launching your challenge instance.

`nc titan.picoctf.net 62482`. [Source](https://artifacts.picoctf.net/c\_titan/80/flag.c)

***

## Solution

Start the instance and download the given `flag.c` file. Connect to instance via netcat and get the word.

<figure><img src="../../../.gitbook/assets/image (76).png" alt=""><figcaption></figcaption></figure>

I have created a solution in C program, with the functions from the given `flag.c` file, to get the little and big endian values of the given word.

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <stdbool.h>
#include <ctype.h>
#include <time.h>

char *find_little_endian(const char *word)
{
    size_t word_len = strlen(word);
    char *little_endian = (char *)malloc((2 * word_len + 1) * sizeof(char));

    for (size_t i = word_len; i-- > 0;)
    {
        snprintf(&little_endian[(word_len - 1 - i) * 2], 3, "%02X", (unsigned char)word[i]);
    }

    little_endian[2 * word_len] = '\0';
    return little_endian;
}

char *find_big_endian(const char *word)
{
    size_t length = strlen(word);
    char *big_endian = (char *)malloc((2 * length + 1) * sizeof(char));

    for (size_t i = 0; i < length; i++)
    {
        snprintf(&big_endian[i * 2], 3, "%02X", (unsigned char)word[i]);
    }

    big_endian[2 * length] = '\0';
    return big_endian;
}

int main()
{
  char *challenge_word = "kothq";
  
  printf(find_little_endian(challenge_word));
  printf("\n");
  printf(find_big_endian(challenge_word));
}
```

On executing the above script, got the values.

<figure><img src="../../../.gitbook/assets/image (74).png" alt=""><figcaption></figcaption></figure>

Providing the values that we got to the instance, got the flag.

<figure><img src="../../../.gitbook/assets/image (75).png" alt=""><figcaption></figcaption></figure>

Flag: `picoCTF{3ndi4n_sw4p_su33ess_02999450}`
