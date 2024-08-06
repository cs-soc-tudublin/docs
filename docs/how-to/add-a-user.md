---
title: Add A User
created: 2024-07-06T00:00:00
modified: 2024-08-06T16:47:54
tags:
  - how-to
  - easy
  - sysadmin
---

# *How To:* Add A User

Occasionally, you'll need to add users to a server. This doc will help you create a user, give them admin permission, add a user's SSH key, and let them run docker commands.

# Adduser

Once you're SSH'd into the correct server (If you do not know how to SSH, read [this](./ssh.md)), run the following command:

```bash
sudo adduser [USERNAME]
```

You will be prompted to enter your password (As you are running this command with `sudo`, which is administrator privileges.)

You should then see the following output:

```
Adding user `[USERNAME]' ...
Adding new group `USERNAME' (1234) ...
Adding new user `USERNAME' (1234) with group `USERNAME' ...
Creating home directory `/home/USERNAME' ...
Copying files from `/etc/skel' ...
New password: 
```

Set a simple password, with the following structure:

`Day-Object-####`

Replace the day with the Day of the week AND actual date, i.e. `Saturday06`, replace an the object with a random object in the room, such as `Charger`, and replace the hashtags with a 4 random numbers or letters.

!!! note "The password will not appear as you type it!"

## Filling in Their Details

Enter their full name, i.e. `Ruán Murgatroyd` and leave the rest of the options blank (by just pressing enter.)

Then verify the information is correct and type `Y`.

## Expiring Their Password

**BEFORE YOU GIVE THE TEMPORARY PASSWORD TO THE USER**

You need to set the password to expire on first log in, to do this, run the following:

```bash
sudo passwd --expire [USERNAME]

# That is not a typo, it is passwd
```

It should output the following:

```
passwd: password expiry information changed.
```

# Adding an SSH Key

CS++ mandates SSH Key login for all committee. To make this possible, Sysadmins need to add their public key to the user.

To do this, run the following commands:

```bash
# Go to the User's home directory
cd /home/[USERNAME]/.ssh

# Create a new file called authorized_keys (Yes, with a 'z')
touch authorized_keys
```

Now, get the public key from the user, it should look something like this:

```
ssh-ed25519 AAAAC3NzaC1GHDI1NTE5AAAAIFCSjHARHARGZFpRqFREdDyFaZBeaRhoATlk/+y01NKy bitflip@fun-machine
```

Copy that to your clipboard, go back to the terminal and run the following command:

```
# Add they key to the user's authorised keys
echo [PASTE_PUBLIC_KEY_HERE] > authorized_keys
```

# Giving Admin to a User

In Linux, an administrator account is called a `sudoer`, as the commend you use to run something as an administrator is `sudo`.

!!! WARNING

	This will give the user the ability to run ANY command with FULL permissions, only do this if you are **CERTAIN** you are adding the right person, and have permission to add them.

If you want to make a user a sudoer, you add them to the '`sudo` group'!

To do this, run the following command:

```bash
sudo adduser [USERNAME] sudo
```

You may be prompted to enter your password.

# Letting a User Run Docker Commands

If you want to make it easier for a user to run Docker commands without having to preface it with `sudo`, you can add the user to the Docker group:

```bash
# Before adding them to the Docker group:
sudo docker images

# Adding them to the Docker Group:
sudo usermod -aG docker [USERNAME]

# Now they can do this:
docker images
```

!!! warning "Like giving `sudo`, only give this to people who should be allowed to run Docker commands!"

Happy adding!
