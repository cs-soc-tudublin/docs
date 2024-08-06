---
title: SSH
created: 2024-07-07T11:35:18
modified: 2024-08-06T16:47:54
tags:
  - how-to
  - easy
  - joining
---

# *How To*: SSH

We connect to our servers for many reasons:

- Updating the server or services
- Starting new services
- Other maintenance
- Investigations
- etc.

To do this, we use a piece of software called [Secure Shell (SSH)](https://en.wikipedia.org/wiki/Secure_Shell).

The way SSH works is by essentially creating a terminal (Think Command Prompt) on the server that a terminal on your computer connects to. Cool, huh?

Before we continue, please make sure you have followed the [Setting up Technically Guide](./joining-committee.md).

# Your First Connection

With your generated SSH key (For this doc, let's say my SSH Private Key is `/home/bitflip/.ssh/cspp`), open a terminal, like Terminal for MacOS or PowerShell for Windows.

We're going to connect to our cloud server, `Huey Dewey Louie`!

Then type the following command:

```bash
ssh USERNAME@hdl.cspp.ie -i /home/bitflip/.ssh/cspp

# Don't forget to change the path of the key with your path!
```

You'll see this big scary message that reads something like this:

```
The authenticity of host 'hdl.cspp.ie (158.220.114.253)' can't be established.
ED25519 key fingerprint is SHA256:AMbW9QGVEgxijwaoAgZijtzkS4RiHUpL80XVpluZCR0.
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

Type the word `yes` and press `ENTER` to continue! This is you just confirming that you trust the server.

Assuming your key was configured correctly, you'll see something like this:

```bash
Welcome to Ubuntu 22.04.4 LTS (GNU/Linux 5.15.0-25-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

     _/_/_/    _/_/_/      _/          _/
  _/        _/            _/          _/
 _/          _/_/    _/_/_/_/_/  _/_/_/_/_/
_/              _/      _/          _/
 _/_/_/  _/_/_/        _/          _/

Welcome CS++ Administrator!

Last login: Fri Jul 5 17:19:39 2024 from ███.███.███.███
bitflip@huey-dewey-louie:~$
```

## Updating Your Password

Since your account was just created, the Sysadmin should have given you a **TEMPORARY PASSWORD**. This password will require you to change it on first log in.

It'll look like this:

```bash
You are required to change your password immediately (administrator enforced).
Changing password for USERNAME.
Current password:
```

Enter your temporary password in `Current password:`

Then enter a new password for your user.

!!! note "The password section will remain blank as you type!"

You just made your first SSH connection to CS++ infrastructure, congrats!

# But How Do I Get Out?

To disconnect, you can type the following:

```bash
bitflip@huey-dewey-louie:~$ exit
```

You'll then see this in your terminal:

```bash
logout
Connection to hdl.cspp.ie closed.
```

You have now logged out!

# Connecting Made Simple

If you're going to SSH regularly, then you can create a config file for SSH.

Go to where your `.ssh` folder is. On MacOS / Linux, it is normally `/home/[USERNAME]/.ssh`, for Windows, you'll find it in `/c/Users/[USERNAME]/.ssh`

Create a file called `config`, and open it in a text editor.

If you want to connect to `Huey Dewey Louie` regularly, add the following:

```bash
Host huey
        Hostname hdl.cspp.ie
        User [USERNAME]
        IdentityFile [path/to/key]
```

Fill in the placeholders with your username on the server, and the path to your key, then save and close the file.

Now open a terminal again and type:

```bash
ssh huey
```

You'll be prompted to trust the server again, just type `yes` again, and you'll be greeted with the same CS++ Logo!

It's so much easier to type than having to enter your username, domain of the server, and where your key is stored.

# Connecting to Other Servers

Head on over to the [hardware](../hardware/index.md) section of these docs to get the domain / IP of the server you wish to connect to!

Happy SSHing!
