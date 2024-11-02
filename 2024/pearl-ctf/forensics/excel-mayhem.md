# Excel Mayhem

## Challenge Description

This excel sheet is troubling me a lot !! help me find the flag . Enclose the flag in pearl{}

### Attachments

{% file src="../../../.gitbook/assets/flags.xlsx" %}

***

## Solution

I used the python pandas to read the `xlsx` file. I used regex to extract all valid words. Then used for loop to look out for strings that doesn't start with "fake\_flag" and is not a digit and found the flag.

### Python Script

```python
# import pandas lib as pd
import pandas as pd
import re

dataframe1 = pd.read_excel('/content/flags.xlsx')

for each in re.findall(r'\b[\w_]+?\b', dataframe1.to_string()):
  if not each.startswith("fake_flag") and not each.isdigit():
    print(each)
```

### Output

<figure><img src="../../../.gitbook/assets/image (110).png" alt=""><figcaption></figcaption></figure>

Flag: `pearl{`h3ll\_0f\_4n\_3xc3l`}`
