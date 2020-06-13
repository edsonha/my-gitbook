---
description: Secure Shell
---

# SSH

It is a protocol, similar to HTTPS, and it is a way for machines to communicate with one another. 

Three uses cases are SSH to Github, remote computer and server. 

The advantage of SSH is the use of encryption to ensure secure transfer of information between host and client. Host refers to the remote server you are trying to access and client is the the computer you are using to access the host

The foundation of SSH are

1. Diffie-Hellman Key Exchange - used only to share public key
2. Arrive at symmetric key and use this for communication because it is faster than asymmetric encryption
3. Hashing to make sure no message is tampered
4. Authentication using password or get authenticated using RSA which allows us to provide the identity of a person without a password.

SSH commands:

Open Gitbash and enter into shell

```
$ cd ~/.ssh
```

Create a new SSH key, using the provided email as a a label

```
$ ssh-keygen -t rsa -b 4096 -C "your_email@email.com"
```

You will be prompted to create a key and you may create different key for different platform. Passphrase is optional.

```
Enter file in which to save the key (/c/Users/Your_Name/.ssh/id_rsa):
/c/Users/Your_Name/.ssh/id_rsa_github
```

Start up the SSH-Agent and add RSA key to the SSH-Agent every time you start the terminal because it won't save them after you close the terminal

```
$ eval $(ssh-agent -s)
```

Add your SSH private key to the SSH-Agent

```
$ ssh-add ~/.ssh/id_rsa_github
```

To check and delete identities associated with the SSH-Agent

```
$ ssh-add -l  => List all identity
$ ssh-add -D  => Delete all identity
```

Add SSH key to the github account, under "Setting =&gt; SSH and GPG keys"

```
$ clip < ~/.ssh/id_rsa_github
```

Testing your SSH connection

```
$ ssh - T git@github.com
```



