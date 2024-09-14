---
tags:
  - ✅
published: true
sr-due: 2025-10-22
sr-interval: 477
sr-ease: 248
---

⬅️ [[CS50 Week 10 - Ethics]]
 ## Security
- keeping someone out of your resources 🕵️‍♀️

### Password strength
When length of password is 4:
- 10 x 10 x 10 x 10 for just digits - 10k options
- 52 x 52 x 52 x 52 for just letters (upper and lower) - around 7 million
- 94 x 94 x 94 x 94 all characters (digits, letters, symbols) - around 78 million

Iterating through all possible passcodes with python:
```python
from string import ascii_letters, digits, punctuation
from itertools import product

for passcode in product(ascii_letters + digits + punctuation, repeat=4):
    print("".join(passcode))
```

If you use an 8-character password instead, it's six quadrillions (six followed by fifteen zeroes) 💡

### Encryption
- Encryption is the scrambling of information so that it can’t be read without a key to decrypt it.
- **End-to-end encryption** means that the messages between the two parties involved are encrypted. So even if we are using a third-party chat or video service, the companies running them cannot decrypt or read the contents of our communications.