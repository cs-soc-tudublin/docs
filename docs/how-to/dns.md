---
title: DNS
created: 2024-07-06T00:00:00
modified: 2025-02-05T20:45:43
tags:
  - how-to
  - sysadmin
  - hard
---

# *How To:* Modify DNS

This document will go over what DNS and Domains are, and how to add a subdomain to cspp.ie and host something on it, or have the domain redirect!

DNS, or Domain Name System is a system which converts IP Addresses to the URLs that we all know and love, for example:

```bash
nslookup
Default Server: UnKnown
Address: 1.1.1.1

> google.com
Name:    google.com
Addresses:  2a00:1450:4009:826::200e
          142.250.200.14
```

In this case, the IP Address for `google.com` is `142.250.200.14`.

# A Short(ish) Introduction to DNS and Domains

CS++ currently owns the `cspp.ie` domain. This domain is broken down in two parts:

**TOP LEVEL DOMAIN:** `.ie`, this is the two-letter code for Irish Websites.

**DOMAIN NAME:** `cspp`, this is our unique domain name.

You can add a thing called 'subdomains' to a domain, for example, this website is `docs.cspp.ie`, which is a Subdomain.

# What Do We Use Domains and DNS For?

We use it to make it easy to access our services, such as our website, documentation, password manager, etc.

The `cspp.ie` domain identifies everything using it as ours.

We also sometimes use subdomains to make the lives of our members easier! The Discord server can be accessed at [discord.cspp.ie](https://discord.cspp.ie/), and so on!

# Where is All of This Stored?

The `cspp.ie` domain is bought from [Smarthost](https://smarthost.ie/) and paid for annually. As of right now, it is in the name of Ruán Murgatroyd.

We control our DNS records using [Cloudflare](cloudflare.com). There are many options for this service, but cloudflare provides a lot of additional extras like DDOS protection and caching.

# Adding a Subdomain

!!! danger "BE REALLY CAREFUL!!!"

	Changes to DNS can cause long downtimes!

	Make sure you know what you're doing, and don't touch anything you're not actively working on!

	If possible, get a second set of eyes to go over everything you're doing!!!!

1. Log in to [Cloudflare](https://dash.cloudflare.com/login/) with the CS++ account.

2. Navigate to `DNS` through the sidebar

Here you'll see a list of all of our DNS info for `cspp.ie`. Let's add another!

3. Click '+ Add record'

4. Enter the subdomain in the `Name` field and in the `Ipv4 address` field, put the IP Address of the server/computer you want to point at.

**What Do These Fields Mean?**

`Type`: The type of record. The simplest is an `A` record which translates a domain or subdomain to an IPv4 address. 

`name`: The subdomain name. E.g. in `docs.cspp.ie`, `docs` is the subdomain. `@` refers to the 'root' or `cspp.ie` in this case.

`Priority:` The priority, used for mail records only.

`Data/IPv4 Address`: The data field. For `A` records this is the IPv4 address you want to point at.

`TTL`: Time-To-Live - How long the record will be stored by DNS servers before they go and ask again for the data.

Learn more here: [Cloudflare Docs - What are DNS records?](https://www.cloudflare.com/en-gb/learning/dns/dns-records/).

5. Once you have filled out all the data, click `save`.

You have now created your first record, congrats! Right now it's pointing at a server, but the server doesn't respond with anything!

## Running a Service on the Subdomain

Now that we have a subdomain, we need to have something that we want to serve to people on it.

For this example, we will run a basic NGINX container.

SSH into the server you pointed the subdomain at (If you do not know how to SSH, read [this](./ssh.md)).

Now, run the following command:

```bash
docker run -d -p [PORT]:80 -p [PORT_2]:443 --name SUBDOMAIN nginx
```

This will create an NGINX container (NGINX is a webserver). Replace `[PORT]` and `[PORT_2]` with port numbers, make sure these port numbers are not in use elsewhere on the system!

This will then create an NGINX container, running on `PORT` and `PORT_2`. We now need to point the subdomain at these ports. This is called a 'Reverse Proxy'.

### Setting up a Reverse Proxy

To set up the reverse proxy, run the following command:

```bash
cd /etc/nginx/sites-available
sudo cp rp_template [SUBDOMAIN].cspp.ie
```

You may be prompted to enter your user password.

Then open this file in a text editor like `nano` or `vim`.

It will look like this:

```nginx
server {
    server_name SUBDOMAIN.cspp.ie;

    location / {
        proxy_pass http://localhost:PORT;
        include proxy_params;
    }

    listen 80;
}
```

Replace SUBDOMAIN and PORT with the subdomain and `PORT` configured earlier, then save and exit the file.

!!! note "Make sure the `server_name` matches the name of the file!"

Now we need to enable this site.

## Having the Subdomain Redirect

For some cases, we don't want to host a service on this subdomain, but instead have it redirect. This may be for sites like `discord.cspp.ie` which redirects to our Discord server.

In this case, the subdomain still points to the server, but we just redirect them.

To set this up run the following:

```
cd /etc/nginx/sites-available
sudo cp redirect_template [SUBDOMAIN].cspp.ie
```

When opening this new file in `nano` or `vim` (you will need to sudo), it will look like this:

```nginx
server {

    server_name SUBDOMAIN.cspp.ie;

    location / {

    rewrite ^/(.*) https://google.com/bla redirect;

    }

    listen 80;

}
```

Change the server_name to match the filename (aka the subdomain that will redirect), then update the `https://google.com/bla` with the COMPLETE URL that you wish to redirect users to.

Once this is done, continue following the instructions below.

### Enabling the Domain

We use `sites-available` and `sites-enabled` in NGINX for our domain configs.

**`sites-available`:**

This stores the config files for each domain we serve.

**`sites-enabled`:**

This allows the domain to be served.

To do this, run the following command:

```bash
sudo ln -s /etc/nginx/sites-available/[SUBDOMAIN].cspp.ie /etc/nginx/sites-enabled/
```

Make sure to use the FULL paths, instead of short-hand.

Now, make sure the config works correctly with:

```bash
sudo nginx -t
```

If the config is correct, it will return:

```
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```

Then reload NGINX with:

```bash
sudo systemctl reload nginx
```

You can now navigate to the site, but it will warn about no certificate! We need to enable HTTPS!

## Enabling HTTPS

We use `certbot` from [Let's Encrypt](https://letsencrypt.org/) for free TLS (that means HTTPS) certificates!

Before you get started, if you are adding a new root domain, e.g. for another society, you'll need to switch `SSL encryption mode` to `Full` for that domain on the cloudflare dashboard.

Run the following:

```bash
sudo certbot --nginx
```

Which will output something like the following:

```
Saving debug log to /var/log/letsencrypt/letsencrypt.log

Which names would you like to activate HTTPS for?
We recommend selecting either all domains, or all domains in a VirtualHost/server block.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
1: cspp.ie
2: discord.cspp.ie
3: www.cspp.ie
4: [SUBDOMAIN].cspp.ie
...
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Select the appropriate numbers separated by commas and/or spaces, or leave input
blank to select all options shown (Enter 'c' to cancel):
```

You will want to generate a certificate for `[SUBDOMAIN].cspp.ie`, so type the number its number in (in this case `4`), and press enter.

Assuming everything goes correctly, the following should display:

!!! note "This may take a while to actually run, please be patient!"

```
Requesting a certificate for [SUDBDOMAIN].cspp.ie

Successfully received certificate.
Certificate is saved at: /etc/letsencrypt/live/[SUBDOMAIN].cspp.ie/fullchain.pem
Key is saved at:         /etc/letsencrypt/live/[SUBDOMAIN].cspp.ie/privkey.pem
This certificate expires on 2024-10-04.
These files will be updated when the certificate renews.
Certbot has set up a scheduled task to automatically renew this certificate in the background.

Deploying certificate
Successfully deployed certificate for [SUBDOMAIN].cspp.ie to /etc/nginx/sites-enabled/[SUBDOMAIN].cspp.ie
Congratulations! You have successfully enabled HTTPS on https://[SUBDOMAIN].cspp.ie

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
If you like Certbot, please consider supporting our work by:
 * Donating to ISRG / Let's Encrypt:   https://letsencrypt.org/donate
 * Donating to EFF:                    https://eff.org/donate-le
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
```

This TLS cert will automatically renew, so no need to worry!

Navigate to your subdomain and see the 'Welcome to nginx!' page.

Congratulations! You have successfully created your first subdomain!

Happy domaining!
