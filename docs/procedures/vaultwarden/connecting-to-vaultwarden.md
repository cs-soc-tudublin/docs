---
title: Connecting to VaultWarden
created: 2025-09-02T17:07:23
modified: 2025-09-02T17:18:27
tags:
   - procdure
   - committee
---

# **VAULTWARDEN** - Connecting to Our Password Manager

At CS++, we self-host our own password manager using the secure and open-source [VaultWarden](https://github.com/dani-garcia/vaultwarden).

This allows us a secure, single location to store all password for all accounts used by the soc, and control account access based on committee role.

!!! danger "NOT FOR PERSONAL USE!"

	The VaultWarden is configured to not let you save your own passwords.

	You should NOT use VaultWarden as your own password manager, as your account is DELETED when you leave the committee!

	BitWarden offers free accounts with 99% of the features that VaultWarden has. The premium subscription is just €10 a year!

For this procedure, make sure you have an account created on the VaultWarden. If you're not sure, you can ask a Sysadmin or the Chairperson to check for you!

## **METHOD ONE** - Using the Web UI

The VaultWarden can be connected by the UI.

While this works, you will almost always have to use your 2FA login, which makes it clunky.

The Web UI is good when configuring your account, or if you only need one-time access to the passwords on a device.

To do this, go to [vault.cspp.ie](https://vault.cspp.ie), and log in.

## **METHOD TWO** - Using the Extension

Nearly all browsers have a BitWarden extension (BitWarden is the upstream application that VaultWarden is based off of, and they are interoperable!).

Install the BitWarden extension, and when you first open, you should be asked to enter your email.

This is to connect to the official BitWarden servers, which is **not what we want**! In the bottom, where it says `accessing: Bitwarden.com`, click on `bitwarden.com` and select `Self-Hosted`. Fill in `https://vault.cspp.ie` as the Server URL and click `Save`.

Now you can log in with your email and password!

If you have your own BitWarden account outside of the CS++ one, you can click on your profile picture in the top right, and add an account. Make sure you're accessing the correct server when doing this!

## **METHOD THREE** - Using an App

On mobile or desktop devices you can install the official BitWarden app.

You log in to this the same way you log in when connecting with an Extension.
