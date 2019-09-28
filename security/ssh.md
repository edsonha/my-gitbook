---
description: Secure Shell
---

# SSH

It is a protocol, similar to HTTPS, and it is a way for machines to communicate with one another. 

Three uses cases are SSH to Github, remote computer and server. 

The advantage of SSH is the use of encryption to ensure secure transfer of information between host and client. Host refers to the remote server you are trying to access and client is the the computer you are using to access the host

The foundation of SSH are

1. Diffie-Hellman Key Exchange - used only to share secret key
2. Arrive at symmetric key and use this for communication because it is faster than asymmetric encryption
3. Hashing to make sure no message is tampered
4. Authentication using password or get authenticated using RSA which allows us to provide the identity of a person without a password.

SSH commands:

Open Gitbash and enter into shell

```
$ cd ~/.ssh
```

Create a new ssh key, using the provided email as a a label

```
$ ssh-keygen -t rsa -b 4096 -C "your_email@email.com"
```

You will be prompted to create a key and you may create different key for different platform. Passphrase is optional. For example, /c/Users/Your\_Name/.ssh/id\_rsa\_github

```
Enter file in which to save the key (/c/Users/Your_Name/.ssh/id_rsa):
```

