# EX-7-ADVANCED-ENCRYPTION-STANDARD-DES-ALGORITHM

## Aim:
  Implementation of Pseudorandom Number Generation Using Standard library.
  
## ALGORITHM: 
1.Get the input and convert it as block cipher.
2.The plain text is initially permuted and split into 2 equal halves.
3.It undergoes 16 rounds of encryption.
4.These 2 halves are finally rejoined to give cipher text.
5.The same happens in decryption process but in an inverse manner.

## PROGRAM: 
```c
#include <stdio.h>
#include <string.h>
void encrypt(char *message, char *key, char *encryptedMessage, int messageLength) {
    int keyLength = strlen(key);

    for (int i = 0; i < messageLength; i++) {
        encryptedMessage[i] = message[i] ^ key[i % keyLength];
    }
    encryptedMessage[messageLength] = '\0';  
}

void decrypt(char *encryptedMessage, char *key, char *decryptedMessage, int messageLength) {
    int keyLength = strlen(key);

    for (int i = 0; i < messageLength; i++) {
        decryptedMessage[i] = encryptedMessage[i] ^ key[i % keyLength];
    }
    decryptedMessage[messageLength] = '\0';  
}

int main() {
    char message[100];
    char key[100];
    
    printf("\n      *****Simulation of DES encryption and decryption*****\n\n");
    printf("Enter the message to encrypt: ");
    fgets(message, sizeof(message), stdin);
    message[strcspn(message, "\n")] = '\0';

    printf("Enter the encryption key: ");
    fgets(key, sizeof(key), stdin);
    key[strcspn(key, "\n")] = '\0';  
    
    int messageLength = strlen(message);
    char encryptedMessage[100];
    char decryptedMessage[100];
    encrypt(message, key, encryptedMessage, messageLength);
    printf("Original Message: %s\n", message);
    printf("Encrypted Message: ");
    for (int i = 0; i < messageLength; i++) {
        printf("%02X ", (unsigned char)encryptedMessage[i]);
    }
    printf("\n");
    decrypt(encryptedMessage, key, decryptedMessage, messageLength);
    printf("Decrypted Message: %s\n", decryptedMessage);
    
    return 0;
}
```
## OUTPUT:
![image](https://github.com/user-attachments/assets/21d9fc49-82fd-4f10-b6bd-49d86a078593)


## RESULT: 
Hence, for the given input text and key the DES algorithm is successfully simulated.
