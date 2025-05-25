# HILL CIPHER
HILL CIPHER
EX. NO: 3 AIM:
 

IMPLEMENTATION OF HILL CIPHER
 
## To write a C program to implement the hill cipher substitution techniques.

## DESCRIPTION:

Each letter is represented by a number modulo 26. Often the simple scheme A = 0, B
= 1... Z = 25, is used, but this is not an essential feature of the cipher. To encrypt a message, each block of n letters is  multiplied by an invertible n × n matrix, against modulus 26. To
decrypt the message, each block is multiplied by the inverse of the m trix used for
 
encryption. The matrix used
 
for encryption is the cipher key, and it sho
 
ld be chosen
 
randomly from the set of invertible n × n matrices (modulo 26).


## ALGORITHM:

STEP-1: Read the plain text and key from the user. STEP-2: Split the plain text into groups of length three. STEP-3: Arrange the keyword in a 3*3 matrix.
STEP-4: Multiply the two matrices to obtain the cipher text of length three.
STEP-5: Combine all these groups to get the complete cipher text.

## PROGRAM 
```

#include <stdio.h>

int main() 
{
    unsigned int key[3][3] = {{6, 24, 1}, {13, 16, 10}, {20, 17, 15}};
    unsigned int inverseKey[3][3] = {{8, 5, 10}, {21, 8, 21}, {21, 12, 8}};

    char msg[4];  // Holds 3 characters + null terminator
    unsigned int enc[3] = {0}, dec[3] = {0};

    printf("Enter plain text (3 letters): ");
    scanf("%3s", msg);
    msg[3] = '\0';  // Ensure null termination

    // Convert characters to uppercase (if needed)
    for (int i = 0; i < 3; i++) {
        if (msg[i] >= 'a' && msg[i] <= 'z') {
            msg[i] -= 32;  // Convert lowercase to uppercase
        }
    }

    // Encryption: Multiply key matrix with plaintext vector
    for (int i = 0; i < 3; i++) {
        enc[i] = 0;
        for (int j = 0; j < 3; j++) {
            enc[i] += key[i][j] * (msg[j] - 'A');
        }
        enc[i] = enc[i] % 26;  // Apply modulo after summation
    }

    printf("Encrypted Cipher Text: %c%c%c\n", enc[0] + 'A', enc[1] + 'A', enc[2] + 'A');

    // Decryption: Multiply inverseKey matrix with encrypted text
    for (int i = 0; i < 3; i++) {
        dec[i] = 0;
        for (int j = 0; j < 3; j++) {
            dec[i] += inverseKey[i][j] * enc[j];
        }
        dec[i] = (dec[i] % 26 + 26) % 26;  // Ensure positive modulo
    }

    printf("Decrypted Cipher Text: %c%c%c\n", dec[0] + 'A', dec[1] + 'A', dec[2] + 'A');

    return 0;
}
```

## OUTPUT
![image](https://github.com/user-attachments/assets/1a01e8f1-91ac-43e6-b428-233233516e73)
## RESULT

The program is executed successfully
