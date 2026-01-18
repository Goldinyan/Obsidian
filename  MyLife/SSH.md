Date: 2026-01-18
Tags: {
#W
}


# SSH

what is secure shell protocol?

A protocol for having a secure and encrypted connection with remote server/maschine

You are going to SSH intp a sever. Youre going to get dropped into a login shell, bash, zsh, etc, and you will be able to execute commands in that shell, as if you were sitting at that server with a keyboard

What is th epoint of Ssh?

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

When having a server you wanna automatically connect to with using your keys as auth, you are going to initialize your public key with that sever. youre going to send your key to that server, which will hold on it. Every time in the future where you wanna connect with that server, the server with your public key is going to send a puzzle back to you, your client that youre using to connect, and that puzzle is going to be able to be solved by your private key, wthout actually exposing what the pribate key is.  


# References