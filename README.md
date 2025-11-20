# VIGENERE-CIPHER

## NAME: HARISH S

## REG NO: 212224040105


 

## IMPLEMETATION OF VIGENERE CIPHER
 

## AIM:

To implement the Vigenere Cipher substitution technique using C program.

## DESCRIPTION:

To encrypt, a table of alphabets can be used, termed a tabula recta, Vigenère square,or Vigenère table. It consists of the alphabet written out 26 times in differnt rows, each
 
alphabet shifted cyclically to the left compared to the previous alphabet, corresponding to the 26 possible Caesar ciphers. At different points in the encryption process, the cipher uses adifferent alphabet from one of the rows. The alphabet used at each point repeating keyword.depends on a Each row starts with a key letter. The remainder of the row holds the letters A to Z. Although there are 26 key rows shown, you will only use as many keys as there are unique letters in the key string, here just 5 keys, {L, E, M, O, N}. For successive letters of the message, we are going to take successive letters of the key string, and encipher each message letter using its corresponding key row. Choose the next letter of the key, go along that row to find the column heading that	atches the message character; the letter at the intersection of
[key-row, msg-col] is the enciphered letter.


## ALGORITHM:

STEP-1: Arrange the alphabets in row and column of a 26*26 matrix.
STEP-2: Circulate the alphabets in each row to position left such that the first letter is attached to last.
STEP-3: Repeat this process for all 26 rows and construct the final key matrix.
STEP-4: The keyword and the plain text is read from the user.
STEP-5: The characters in the keyword are repeated sequentially so as to match with that of the plain text.
STEP-6: Pick the first letter of the plain text and that of the keyword as the row indices and column indices respectively.
STEP-7: The junction character where these two meet forms the cipher character.
STEP-8: Repeat the above steps to generate the entire cipher text.


## PROGRAM

```
#include <stdio.h>
#include <string.h>

void encryptVigenere(char *plaintext, char *key, char *ciphertext) {
    int textLength = strlen(plaintext);
    int keyLength = strlen(key);

    for (int i = 0, j = 0; i < textLength; i++) {
        if (plaintext[i] >= 'A' && plaintext[i] <= 'Z') {
            ciphertext[i] = ((plaintext[i] - 'A' + (key[j % keyLength] - 'A')) % 26) + 'A';
            j++;
        } else {
            ciphertext[i] = plaintext[i];
        }
    }
    ciphertext[textLength] = '\0';
}

void decryptVigenere(char *ciphertext, char *key, char *plaintext) {
    int textLength = strlen(ciphertext);
    int keyLength = strlen(key);

    for (int i = 0, j = 0; i < textLength; i++) {
        if (ciphertext[i] >= 'A' && ciphertext[i] <= 'Z') {
            plaintext[i] = ((ciphertext[i] - 'A' - (key[j % keyLength] - 'A') + 26) % 26) + 'A';
            j++;
        } else {
            plaintext[i] = ciphertext[i];
        }
    }
    plaintext[textLength] = '\0';
}

int main() {
    char plaintext[100], key[100], ciphertext[100], decryptedText[100];

    printf("Enter the plaintext (uppercase letters only): ");
    scanf("%s", plaintext);
    printf("Enter the key (uppercase letters only): ");
    scanf("%s", key);

    encryptVigenere(plaintext, key, ciphertext);
    printf("Encrypted Text: %s\n", ciphertext);

    decryptVigenere(ciphertext, key, decryptedText);
    printf("Decrypted Text: %s\n", decryptedText);

    return 0;
}
```

## OUTPUT

<img width="456" alt="Screenshot 2025-03-27 091535" src="https://github.com/user-attachments/assets/4108c72c-efae-45d6-9dcf-5e3c58127819" />

## RESULT
THUS THE PROGRAM IS SUCCESSFULLY IMPLEMENTED.
