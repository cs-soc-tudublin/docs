---
title: Onboarding Committee
created: 2025-10-10T12:35:55
modified: 2026-02-10T18:54:19
tags:
   - procedure
   - committee
   - onboarding
---

# **ONBOARDING** - All Committee

Committee onboarding is a multi-step process where both we have to get them added to the correct channels, portals, etc. but also to get their onboarding recognised by the Societies Office.

While some of this process can be done by normal committee, only Discord & VaultWarden administrators (Chairs & Sysadmins) can add people to these. As such, it is probably best that the Systems Administrators do technicall onboarding

## **EMAIL** - Start of the Paper Trail

Send an email to the student email of the member that has just joined the committee to begin onboarding!

Please make sure you go through and make the correct sections *italic*, **BOLD**, and REPLACE ANY PLACEHOLDERS!!!

**Subject Line:**

```
Welcome to CS++! - Your Onboarding Email
```

**Body:**

```
Welcome {{name}} to CS++!

On behalf of the entire committee, I'd like to extend a massive congratulations on your election to CS++

We have to do a little on-boarding to get you into our secret channels and get you put on our website, cspp.ie!

This e-mail is a little long, but we've tried to organise everything as clearly as possible for you.

We've attached your election photo *and* the photo of the whole committee, feel free to post these wherever you want!

You will have to reply to this email with a few things!!!! Please read carefully. For each step, the full list of things you need to send will be at the __END OF THE EMAIL__!

If you're getting lost, that's okay! We're more than happy to help :) I have a bad habit of writing long emails...

# STEP 1 - Committee Channels
We do all of our communications & committee planning on Discord.
You will need to have a Discord account to do this, you can create one [here](https://discord.com)

Once you have an account (or log into your current one), please go to discord.cspp.ie in a browser and join the CS++ Society Discord, enter your Student Number to be verified. You will eventually be given the Committee Role on Discord when you send your Discord username in reply to this email.

# STEP 2 - The Website & Socials
Each Committee Member gets their name, a photo of their choice, and a custom username to go on the official 'Meet the Committee' section of our custom website, and our Instagram / LinkedIn post!

You need to send us a few things for this, see these at the bottom!

# STEP 3 - Socs Portal

I know we're emailing you to your student email, but we just wanna get everything right, so to add you as committee to the portal, send us your student number!

Being on the portal lets everyone see your name, you can add events, take attendance and get reimbursed for any expenses!!!

# STEP 4 - Registering With the Office

This is something you absolutely HAVE to do. The socs office will not reimburse you or respond to your emails if you aren't registered with them! You can do that [here](!replace with form of this year!).

If you run into issues, let us know and we can help!
The date for your AGM is DD/MM/YYYY

Please reply to this email confirming that you have submitted the registration form

**WHAT TO REPLY TO THIS EMAIL WITH:**
Step 1:
- Your Discord Username

Step 2:
- The name you want used (I.e. Ruán Murgatroyd)
- A photo you are comfortable going on the website & social media (See my photo)
- A custom username you want to appear on the website (It doesn't have to be your social media handle! I use @rjm for CS++)
- Your course & year
- Up to 2 fun facts about yourself!
  
Step 3:
- Your student number
  
Step 4:
- Confirmation of you completing the registration form
```

We normally take photos of those who have joined the committee and a final full committee photo, don't forget to attach them!

## **REPLY** - Getting Things Done

Once they reply with everything attached it's time to get them added to all they need

### **PORTAL** - Molasses+

Go to the Student Life Portal, log in, go to the CS++ Dashboard, click 'Committee' and 'Add Committee'. 

Set the correct role and make sure it is set to 'active'!

### **WEBSITE** - Plumage

This will probably be done by a Sysadmin but they will take their chosen name, image and username to put on the website.

Do not forget to add their names to the wordlist so it doesn't fail the Spellcheck voters

Resize the image so it's about 500px across or less, and convert to webp!

## **DISCORD** - Where We Chat

If they were elected in the AGM, give them 'Incoming Committee' immediately. This will give them access to just one channel in the Committee category.

If they're filling a role immediately (At an EGM, or by co-option), immediately give them the `Operating System //Committee` role as well as their relevant role (`Chairperson`, `First Year Rep`, etc.) which will give them full access to the Committee category as well as basic moderation permissions.

It is always nice to welcome them in `#committee-general` once they have been given access.

# **GITHUB** - Get Coding

It is good to get everyone on the committee into the GitHub org, even if they aren't planning on contributing to any projects at the moment. Ask for their GitHub account name and using the `Invite Member` in the `People` tab of the organisation, send them an invite.

Set the relevant permissions & Teams as follows:

| Committee Position | Role  | Teams                            |
| ------------------ | ----- | -------------------------------- |
| Chairperson        | Owner | Committee                        |
| Vice Chair         | User  | Committee                        |
| Treasurer          | User  | Committee                        |
| Secretary          | User  | Committee                        |
| HSO                | User  | Committee                        |
| PRO                | User  | Committee                        |
| Sysadmin           | Owner | Committee, System Administrators |
| TEO                | User  | Committee                        |
| SEO                | User  | Committee                        |
| First Year Rep     | User  | Committee                        |
| Second Year Rep    | User  | Committee                        |
| Events Rep         | User  | Committee                        |

Once you've sent the invite, send the following message:

```
You've been invited to the GitHub Organisation and should've recieved an email from GitHub, you might need to check spam. It will have instructions on how to accept the invite.
```

## **VAULTWARDEN** - Access Granted

This is the super important one, because without access to the password manager, they will not be able to log into any accounts.

Go to the VaultWarden web UI and log in with your account. Press the `Admin Console` button in the bottom left and navigate to the `Members` section.

Here you will need to get the **PERSONAL** email address of the person. Microsoft still does not trust `vault.cspp.ie` and if someone uses their student email they will be required to reset the password to their college email.

Once you have that email address, Press the `Invite member` button in the `Members` section, enter their email and set the relevant permissions & collections as follows:

| Committee Position | Role  | Collections                                                                                   |
| ------------------ | ----- | --------------------------------------------------------------------------------------------- |
| Chairperson        | Owner | N/A (Automatically given full access)                                                         |
| Vice Chair         | User  | Archive, Core, General, Holding Accounts, Public Relations, Purchasing, System Administration |
| Treasurer          | User  | Archive, Core, General, Public Relations, Purchasing                                          |
| Secretary          | User  | Archive, Core, General, Holding Accounts, Public Relations, Purchasing                        |
| HSO                | User  | Archive, Core, General, Public Relations, Purchasing                                          |
| PRO                | User  | Archive, Core, General, Public Relations, Purchasing                                          |
| Sysadmin           | Owner | N/A (Automatically given full access)                                                         |
| TEO                | User  | Archive, General, Public Relations, Purchasing                                                |
| SEO                | User  | Archive, General, Public Relations, Purchasing                                                |
| First Year Rep     | User  | Archive, General, Public Relations                                                            |
| Second Year Rep    | User  | Archive, General, Public Relations                                                            |
| Events Rep         | User  | Archive, General, Public Relations                                                            |

Once that has been set, press `Save` and they will be sent an email, then send them the following message:

```
You've been invited to the password manager and should've recieved an email from the password manager, please DM me again when you've completed onboarding for the Password manager so I can finalise it for you!
```

One they have confirmed that they've finished the onboarding, return to the `Members` section and go to the `Needs Confirmation` tab, and using the three dots, add the member. Then, send them this message to help them install the password manager:

```
You should be confirmed on that now You can use this docs page to help you install & connect the Bitwarden browser extension to our servers https://docs.cspp.ie/procedures/vaultwarden/connecting-to-vaultwarden
```
