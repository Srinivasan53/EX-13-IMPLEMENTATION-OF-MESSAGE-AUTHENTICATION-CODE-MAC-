## EX 13 : IMPLEMENTATION OF MESSAGE AUTHENTICATION CODE(MAC)


## AIM:

To implement a Message Authentication Code (MAC) using a shared secret key and a hash function to verify the integrity and authenticity of a message.

## NAME: SRINIVASAN S
## REGISTER NO: 212224220105
## ALGORITHM:

1.	Choose a shared secret key that will be known to both the sender and the receiver.
2.	Define the message that needs to be authenticated.
3.	Concatenate the message and the secret key to form a new string.
4.	Apply a hash function (e.g., simple XOR-based hash or any secure hashing function like SHA) to the concatenated string to generate the MAC.
5.	Send the message along with the generated MAC.
6.	For verification, the receiver uses the same shared key, concatenates it with the received message, and applies the hash function to generate a new MAC.
7.	Compare the generated MAC with the received MAC. If they match, the message is authentic; otherwise, it has been tampered with.


## PROGRAM:
```
#include <stdio.h> 
#include <string.h>
#define KEY "secretkey" // Shared secret key
// Function to calculate a simple MAC using XOR
unsigned int calculate_mac(const char *message, const char *key) 
{ 
unsigned int mac = 0;
int i;
for (i = 0; i < strlen(message); i++)

{ mac ^= message[i];
}
for (i = 0; i < strlen(key); i++) 
{ mac ^= key[i];
}
return mac;
}
int main() 
{
char message[256];
unsigned int mac_sent, mac_received;
// Input message from user printf("Enter the message: "); 
fgets(message, sizeof(message), stdin);
message[strcspn(message, "\n")] = '\0'; // Remove newline character
// Sender generates MAC
mac_sent = calculate_mac(message, KEY); 
printf("Generated MAC (sent): %u\n", mac_sent);
// Simulate receiver calculating MAC using same key 
mac_received = calculate_mac(message, KEY); 
printf("Calculated MAC (received): %u\n", mac_received);
// Check if the MACs match
if (mac_sent == mac_received) { 
printf("Message is authentic.\n");
} 
else 
{

printf("Message integrity check failed.\n");
}
return 0;
}
```
## OUTPUT:
 <img width="523" height="127" alt="image" src="https://github.com/user-attachments/assets/92441f08-61da-49cf-b355-3fa83cf8ac68" />

## RESULT:

The Message Authentication Code (MAC) was implemented successfully, allowing the verification	of	message	integrity	and	authenticity	using	a	shared	secret	key.
