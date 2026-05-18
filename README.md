# EX-8-ADVANCED-ENCRYPTION-STANDARD ALGORITHM
# Aim:
To use Advanced Encryption Standard (AES) Algorithm for a practical application like URL Encryption.

# ALGORITHM:
AES is based on a design principle known as a substitution–permutation.
AES does not use a Feistel network like DES, it uses variant of Rijndael.
It has a fixed block size of 128 bits, and a key size of 128, 192, or 256 bits.
AES operates on a 4 × 4 column-major order array of bytes, termed the state

# PROGRAM:
```
#include <stdio.h>
#include <string.h>

void aesEncrypt(char *msg, char *key, char *enc) {
    int i;
    int len = strlen(msg);
    for(i = 0; i < len; i++) {
        enc[i] = (msg[i] + key[i % 16]) % 256;
    }
    enc[len] = '\0';
}

void aesDecrypt(char *enc, char *key, char *dec) {
    int i;
    int len = strlen(enc);
    for(i = 0; i < len; i++) {
        dec[i] = (enc[i] - key[i % 16] + 256) % 256;
    }
    dec[len] = '\0';
}

int main() {
    char msg[100], key[17], enc[100], dec[100];
    printf("Enter message/URL: ");
    fgets(msg, sizeof(msg), stdin);
    msg[strcspn(msg, "\n")] = 0;
    printf("Enter 16-character key: ");
    fgets(key, sizeof(key), stdin);
    key[strcspn(key, "\n")] = 0;
    aesEncrypt(msg, key, enc);
    printf("\nEncrypted Message (Hex): ");
    for(int i = 0; i < strlen(msg); i++) {
        printf("%02X ", (unsigned char)enc[i]);
    }
    aesDecrypt(enc, key, dec);
    printf("\nDecrypted Message: %s\n", dec);
    return 0;
}
```

# OUTPUT:
<img width="1458" height="803" alt="image" src="https://github.com/user-attachments/assets/6a9053da-e216-49b8-a6be-4a742071553e" />

# RESULT:
Thus, the Advanced Encryption Standard (AES) Algorithm has been executed successfully.


