---
title: Development Vision
created: 2024-08-12T18:05:26
modified: 2024-08-12T18:17:44
tags:
   - development
   - easy
---

# Developing for CS++

Developing software for CS++ provides a unique opportunity to develop active production code.

Nearly all bespoke software developed for the society goes on to be used actively.

As such, it is important to have a universal development policy which ensures that the development and deployment process remain secure, but also convenient.

## Open Source, Free as in Freedom

We actively attempt to contribute to Open Source, and most projects we develop (unless they contain secrets that cannot be abstracted away) are public on the GitHub Organisation.

In-Dev projects are normally set to private until they are more feature-complete.

## Licensing

By default, most CS++ projects will be GNU GPL V3.0 licensed.

This is normally called a 'copyleft' license. It allows the user of the software to do whatever they like, so long as the project they are using our software with is ALSO distributed with the GNU GPL V3.0 license.

Software that is also GNU GPL V3.0 licensed, must have the source code available for download.

## Continuous Integration / Continuous Deployment

We've implemented CI/CD on some of our software to make it easier for code to be deployed. Once code is committed to the master or main branch, it is deployed to the correct server.

This makes deployment very simple, but presents a few possibilities for errors to be introduced into the project.

## Master/Main Commit Protection

For any repository with CI/CD implemented, it is a requirement that direct commits to the main/master (Which I will just call 'master' from now on) are DISALLOWED.

If this rule was not implemented, broken code could be deployed to production, which can cause outages, data loss, or a damage to brand image.

In this case where the master branch is protected, development should occur in a different branch, and code commits should be done through Pull Requests.

Here are some suggested rules for CI/CD branch protection:

- For core services (CS++ Bot, Website, etc.), should require a code review by someone who isn't the Pull Request owner
- The following voters should also be added:
	- SonarQube
	- Spell Check
	- Link Resolution
	- File Resolution

## Testing

We do not require any Unit or End-to-End tests on services, but there is no restriction on developing tests should you deem it necessary.

If you have Unit and E2E tests, it would be advisory to add a test running step as a check in a PR.
