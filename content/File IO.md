---
tags:
  - ✅
sr-due: 2026-04-07
sr-interval: 595
sr-ease: 250
---

⬅️ [[CS50 Week 04 - Memory]]

## File I/O

```c
	// C does come with a pointer type FILE
	// that... 🥁 points to a file 
	FILE *file = fopen("phonebook.csv", "a");

	// always check for NULL
    if (file == NULL)
    {
        return 1;
    }
```

This is how you define a `BYTE`:
```c
	typedef uint8_t BYTE;

```

**🤔 How do you recognize a jpg file?**
The first three bytes of any `.jpg` files are: `0xff`, `0xd8` and `0xff`.

**🤔 What is a bitmap?**
A map of bits 🥁

And, finally, this is how you copy a file, one byte at a time:
```c
#include <stdint.h>
#include <stdio.h>
#include <stdlib.h>

typedef uint8_t BYTE;

int main(int argc, char *argv[])
{
    // Ensure proper usage
    if (argc != 3)
    {
        fprintf(stderr, "Usage: copy SOURCE DESTINATION\n");
        return 1;
    }

    // open input file
    FILE *source = fopen(argv[1], "r");
    if (source == NULL)
    {
        printf("Could not open %s.\n", argv[1]);
        return 1;
    }

    // Open output file
    FILE *destination = fopen(argv[2], "w");
    if (destination == NULL)
    {
        fclose(source);
        printf("Could not create %s.\n", argv[2]);
        return 1;
    }

    // Copy source to destination, one BYTE at a time
    BYTE buffer;
    while (fread(&buffer, sizeof(BYTE), 1, source))
    {
        fwrite(&buffer, sizeof(BYTE), 1, destination);
    }

    // Close files
    fclose(source);
    fclose(destination);
    return 0;
}
```