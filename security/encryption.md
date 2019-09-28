# Encryption

## Three methods of encryption:

* **Symmetrical**: Sharing of one secret key in the public space and use it for both encryption and decryption.

Problem: Anyone that intercept in the public spaces and get the key to decrypt the message.

* **Asymmetrical**: ****Key exchange algorithm of public and private key pair, called [_Diffie-Hellman key exchange_](https://www.youtube.com/watch?v=NmM9HA2MQGI). It is essentially a mixing of personal private key, personal public key and other person private key \(and vice versa\) to create identical secret session key in private space between two parties before secure communication.

Problem: It is still prone to attack from man in the middle when he comes in between two parties and  convince them that he is the trusted person and can tamper with the message.

* **Hashing**: ****The idea is not to decrypt the message, but comparison so it is tamper-proof. This is done through HMAC - Hash based Message Authentication Code. 



