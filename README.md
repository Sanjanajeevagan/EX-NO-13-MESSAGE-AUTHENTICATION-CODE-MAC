# EX-NO-13-MESSAGE-AUTHENTICATION-CODE-MAC

## AIM:
To implement MESSAGE AUTHENTICATION CODE(MAC)

## ALGORITHM:

1. Message Authentication Code (MAC) is a cryptographic technique used to verify the integrity and authenticity of a message by using a secret key.

2. Initialization:
   - Choose a cryptographic hash function \( H \) (e.g., SHA-256) and a secret key \( K \).
   - The message \( M \) to be authenticated is input along with the secret key \( K \).

3. MAC Generation:
   - Compute the MAC by applying the hash function to the combination of the message \( M \) and the secret key \( K \): 
     \[
     \text{MAC}(M, K) = H(K || M)
     \]
     where \( || \) denotes concatenation of \( K \) and \( M \).

4. Verification:
   - The recipient, who knows the secret key \( K \), computes the MAC using the received message \( M \) and the same hash function.
   - The recipient compares the computed MAC with the received MAC. If they match, the message is authentic and unchanged.

5. Security: The security of the MAC relies on the secret key \( K \) and the strength of the hash function \( H \), ensuring that an attacker cannot forge a valid MAC without knowledge of the key.

## Program:
``` py
#include <stdio.h>
#include <string.h>

// Simple MAC function
int generateMAC(char message[], char key[]) {
    int mac = 0;

    // Add ASCII values of key
    for(int i = 0; i < strlen(key); i++) {
        mac += key[i];
    }

    // Add ASCII values of message
    for(int i = 0; i < strlen(message); i++) {
        mac += message[i];
    }

    return mac;
}

int main() {
    char message[100], key[100];
    int senderMAC, receiverMAC;

    // Input
    printf("Enter message: ");
    scanf("%s", message);

    printf("Enter secret key: ");
    scanf("%s", key);

    // Sender generates MAC
    senderMAC = generateMAC(message, key);
    printf("Generated MAC (Sender): %d\n", senderMAC);

    // Receiver recomputes MAC
    receiverMAC = generateMAC(message, key);
    printf("Generated MAC (Receiver): %d\n", receiverMAC);

    // Verification
    if(senderMAC == receiverMAC) {
        printf("Message is Authentic\n");
    } else {
        printf("Message is Tampered\n");
    }

    return 0;
}
```


## Output:

<img width="331" height="297" alt="image" src="https://github.com/user-attachments/assets/8502d416-1ea0-4859-9507-0d7f04046425" />

## Result:
The program is executed successfully.
