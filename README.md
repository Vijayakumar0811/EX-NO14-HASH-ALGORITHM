# EX-NO14-HASH-ALGORITHM
### NAME: VIJAYAKUMAR S
### REG NO: 212224040359
## AIM:
To implement HASH ALGORITHM

## ALGORITHM:

1. Hash Algorithm is used to convert input data (message) into a fixed-size string, typically a hash value, which uniquely represents the original data.

2. Initialization:
   - Choose a hash function \( H \) (e.g., SHA-256, MD5, etc.).
   - The message \( M \) to be hashed is input.

3. Message Preprocessing:
   - Break the message \( M \) into fixed-size blocks. If necessary, pad the message to make it compatible with the block size required by the hash function.
   - For example, in SHA-256, the message is padded to ensure that its length is a multiple of 512 bits.

4. Hash Calculation:
   - Process the message block by block, applying the hash function \( H \) iteratively to produce an intermediate hash value.
   - For SHA-256, each block is processed through a series of logical operations, bitwise manipulations, and modular additions.

5. Output:
   - After all blocks are processed, the final hash value (digest) is produced, which is a fixed-size output (e.g., 256-bit for SHA-256).
   - The resulting hash is unique to the input message, meaning even a small change in the message will result in a completely different hash.

6. Security: The strength of the hash algorithm lies in its collision resistance, ensuring that it is computationally infeasible to find two different messages that produce the same hash value.


## Program:
```
#include <stdio.h>
#include <string.h>

#define KEY 7

// XOR Encryption
void encrypt(char text[], char encrypted[]) {
    int i;

    for (i = 0; text[i] != '\0'; i++) {
        encrypted[i] = text[i] ^ KEY;
    }

    encrypted[i] = '\0';
}

// XOR Decryption
void decrypt(char encrypted[], char decrypted[]) {
    int i;

    for (i = 0; encrypted[i] != '\0'; i++) {
        decrypted[i] = encrypted[i] ^ KEY;
    }

    decrypted[i] = '\0';
}

// Simple hash function
unsigned long hashFunction(char text[]) {
    unsigned long hash = 5381;
    int i;

    for (i = 0; text[i] != '\0'; i++) {
        hash = ((hash << 5) + hash) + text[i];
    }

    return hash;
}

int main() {
    char message[100];
    char encrypted[100];
    char decrypted[100];
    unsigned long hash;

    printf("Enter the message: ");
    fgets(message, sizeof(message), stdin);

    // Remove newline
    message[strcspn(message, "\n")] = '\0';

    // Generate hash
    hash = hashFunction(message);

    // Encryption
    encrypt(message, encrypted);

    // Decryption
    decrypt(encrypted, decrypted);

    printf("Original Message : %s\n", message);

    printf("Hash Value       : %lu\n", hash);

    printf("Encrypted Message: ");
    for (int i = 0; encrypted[i] != '\0'; i++) {
        printf("%02X ", (unsigned char)encrypted[i]);
    }

    printf("\nDecrypted Message: %s\n", decrypted);

    return 0;
}
```

## Output:

<img width="740" height="280" alt="image" src="https://github.com/user-attachments/assets/d7972a77-ab45-4fae-97a3-683f7a067ab9" />

## Result:
The program is executed successfully.
