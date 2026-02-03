Date: 2026-01-18
Tags: {
#W
}


# SSH

what is secure shell protocol?

A protocol for having a secure and encrypted connection with remote server/maschine

You are going to SSH intp a sever. Youre going to get dropped into a login shell, bash, zsh, etc, and you will be able to execute commands in that shell, as if you were sitting at that server with a keyboard

What is the point of Ssh?

its intented to provide secure encrypted communications between two potentionally untrusted hosts over an insecure network. Thats why it was created in order to replace previously insecure and uncrypted protocols.
What a protcol is can be read here [[Protocol]].

You have a ssh client, which is going to be what youre going to use to connect to an Ssh server and the ,ssh server, called damon is what youre going to run in order to have that server be up

### The Syntax:

```sh
ssh user@host
```
the user being the username on the computer youre trying to connect to.
The host being either the literal host name or a DNS or an Ip adress 

```sh
ssh bread@192.168.1.241 "cat /etc/hostname"

-> giraffe
```
you can also execute commands without even entering it really.

But you didnt enter a password right? 
Like everyone would need normally when logging in. 
Thats because of SSH keys

SSH Key Pairs, youre going to generate a pair of ssh keys. That pair is going to be a public key and its going to be a private key 
As the name implies the public key gets shared arount to whatever server you want, on the contractory to the private key, which is only for your eyes and wont be shared

When having a server you wanna automatically connect to with using your keys as auth, you are going to initialize your public key with that sever. youre going to send your key to that server, which will hold on it. Every time in the future where you wanna connect with that server, the server with your public key is going to send a puzzle back to you, your client that youre using to connect, and that puzzle is going to be able to be solved by your private key, wthout actually exposing what the pribate key is. 2 / 3 challenges of [[Zero-Knowledge Proof]].   
The private key will solve the puzzle and tell the server : "Look, I solved the puzzle. Here you go".
Then the server will let you in.
And this is how oversimplified the authentication works 
This is named challenge-response-authetication.
And the major advantage of key-based authentication is that, in contrast to password auth, it is not prone to brute-force-attacks, and you do not expose valid credentials if the sever has been compromised

### Creating an SSH key pair

Creation is pretty simple, just run one command:
```sh
ssh-keygen
```
The output contains the private and public key and will look along the lines of this:
```sh
Generating public/private ed25519 key pair.
Enter file in which to save the key (/home/_username_/.ssh/id_ed25519):
Created directory '/home/_username_/.ssh'.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/_username_/.ssh/id_ed25519
Your public key has been saved in /home/_username_/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:RLy4JBv7jMK5qYhRKwHB3af0rpMKYwE2PBhALCBV3G8 _username_@_hostname_
The key's randomart image is:
+--[ED25519 256]--+
|%oooo. ..        |
|== ..o.o.        |
|==  . +o..       |
|+ o o.ooE        |
|...  *.oS        |
| o..o ..         |
|o=.. +o          |
|+o*..+o          |
|+.o+. .          |
+----[SHA256]-----+
```
You can share your public key, but *never* should you share your private one.
The public can be shared like this:
```sh
ssh-copy-id user@host
```
And fill in the credentials of the server you wanna share them too. Then go along the procidure and finish the connection.

This is obviously more secure than just email and password system, espaccialy over remote non-local login,












# References