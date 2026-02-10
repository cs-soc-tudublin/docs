---
title: Adding Users to VaultWarden
created: 2025-09-02T18:31:06
modified: 2026-02-10T18:57:10
tags:
   - procedures
   - committee
---

# **VAULTWARDEN** - Adding Users to VW

!!! danger "Risky Business!"

	The VaultWarden contains **ALL** passwords for **EVERY** account that CS++ uses on a day-to-day basis.

	Accidentally adding the wrong person / giving someone the wrong permissions could cause serious problems! Always double check emails and permissions when doing this!

Go to the VaultWarden Web UI and log in with your account. Press the `Admin Console` button in the bottom left and navigate to the `Members` section.

Here you will need to get the **PERSONAL** email address of the person. Microsoft still does not trust `vault.cspp.ie` and if someone uses their student email they will be required to reset the password to that account, and no-one wants that.

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
