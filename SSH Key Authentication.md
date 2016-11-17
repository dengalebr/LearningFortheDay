## What is SSH Key-Based Authentication on Linux | How to configure

###### **Introduction:**
SSH or Secured Shell is encrypted protocol used to connect to server terminal remotely. There are few different methods of authentications to login to terminal, like password, SSH key etc.
SSH keys provide easy and secure approach to logging to your server.

###### **How Do SSH Keys work?**
Most common and easier approach to authenticate to terminal is password. Although passwords are sent to the server in a secure manner, they are generally not complex or long enough for attackers to break it. Modern processing compute power can easily break simple passwords with brute force approach. So with this approach SSH prove to be reliable and secure alternative.

SSH key pairs are two cryptographically secure keys that can be used to authenticate client to an SSH server. Each key consists of public key and private key.

The associated public key can be shared freely without any negative consequences. The public key can be used to encrypt messages that only the private key can decrypt. 

The public key is uploaded to a remote server that you want to be able to log into with SSH. The key is added to a special file within the user account you will be logging into called *~/.ssh/authorized_keys*.

When a client attempts to authenticate using SSH keys, the server can test the client on whether they are in possession of the private key. The session is spawned or requested command is executed after authentication.
 
###### How to create SSH keys:
We need to generate SSH key pairs on any server/computer. There is utility called *ssh-keygen* which is OpenSSH standard. Bydefault this will create 2048 bit RSA key pair.
```
stack@dev-cp1-lcm-m1-mgmt:/tmp$ ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/home/stack/.ssh/id_rsa): /tmp/bala
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /tmp/bala.
Your public key has been saved in /tmp/bala.pub.
The key fingerprint is:
d9:4b:f0:e2:20:e3:b1:6f:13:40:20:97:04:df:a7:a9 stack@dev-cp1-lcm-m1-mgmt
The key's randomart image is:
+---[RSA 2048]----+
|oo+o             |
| +...            |
|  ... . .        |
|    .+   =       |
|    *.. S +      |
|   o =.o o .     |
|  E o  .. .      |
|     .o          |
|     ...         |
+-----------------+
```
This utility will ask for details like location to store key, and passphrase for the same.
The private key is never exposed on the network. The passphrase is only used to decrypt the key on the local machine. 
###### Copy Public key to Server
Once the key pair is generated, it’s time to place the public key on the virtual server that we want to use. You can copy SSH pubic key with one of the following approach.
```
sh-copy-id user@123.45.56.78
```
Alternatively, you can paste in keys using SSH.
```
cat ~/.ssh/id_rsa.pub | ssh user@123.45.56.78 "mkdir -p ~/.ssh && cat >>  ~/.ssh/authorized_keys"
```

Source: (https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2)
