---
title: Joining the Committee (Infrastructure)
created: 2024-07-06
modified: 2024-07-06
tags:
  - how-to
  - easy
  - joining
  - committee
---
# Joining the Committee - Infrastructure
(This document is designed to be used by incoming CS++ Committee, if you're not that, you don't need to read it!)

If you haven't heard it yet, congratulations! Welcome to the CS++ committee!

This document will get you set up with the ability to connect to CS++ services through SSH. What is SSH? Find out [here!](./ssh.md)

## Generating Your Key
CS++ Committee who wish to connect to infrastructure must do so through key-based authentication.
This key must first be generated.

First open a terminal (Like 'Terminal' on MacOS, or 'PowerShell' on Windows. We will assume you will be using PowerShell if you are on Windows. Please, for your own sanity, do not use Command Prompt!)

Once you open a terminal, run the following command:
```bash
ssh-keygen -t ed25519
```

*But what does this do?*
This runs the SSH key generation app.
The `-t ed25519` tells the key generator to generate an `ed25519` key. You don't need to know what that is, but if [you're curious](https://www.brandonchecketts.com/archives/its-2023-you-should-be-using-an-ed25519-ssh-key-and-other-current-best-practices).

**ANYWAY**
### Where to Save?
One you run the command, the following should appear:
```
Generating public/private ed25519 key pair.
Enter file in which to save the key (some/directory):
```

You first need to tell it where to store the keys. Generally, the default location is fine, they look something like this:
```
MacOS / Linux: /home/[your_name]/.ssh/id_ed25519
Windows: (/c/Users/[your_name]/.ssh/id_ed25519)
```

If you want to leave it there, just press `ENTER`.

### Adding a Password to Your Key
Once you have chosen your location, you will be prompted with the following:
```
Enter passphrase (empty for no passphrase):
```
This allows you to use a password to protect your key.

*But why would I use a password?*
If someone managed to steal your key, and it wasn't password protected, they would be able to log into the servers as you.

*What do you recommend?*
We recommend that you  use a password (That isn't your usual one!)

If you want a password, type it in and press `ENTER`.
If you do not want to use a password (for shame!), just press `ENTER`.

!!! note "The password section will remain blank as you type!"

You will then be prompted to re-enter your password, if you haven't given a password, just press `ENTER` again.

Once that is done, it will tell you where it has saved your identification (Private Key), and your Public Key, and give you a little bit of art as a treat!

## What Next?
Well, here's the first thing you need to know after you generate your key.

!!! danger "__DO NOT SHARE YOUR PRIVATE KEY__"
	Your private key is the one WITHOUT `.pub`. Sharing your private key means anyone can use it to do whatever they like as you on CS++ infrastructure! Treat it like you do your passport, bank account, and passwords. Not even sysadmins or the chair need your private key!

Okay, what do you *really* do next?

### Getting it Added to CS++ Infrastructure
Go to one of the Sysadmins, and send them two things:
- A username you want to go by
- Your public key (That's the file with the `.pub` file type!)

The Sysadmin will then go somewhere, do funny magic, and let you know you can connect to CS++ services, ain't that just neat!

### Connecting to Your First Server
With all that done, you can now connect to your first server. To do this, read [THIS guide](./ssh.md).

Happy joining!