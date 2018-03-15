---
title: Enable Let's encrypt wildcard certificate in CentOS 7
date: 2018-03-15 14:00:00
tags: [linux, nginx, dns]
---

Let's encrypt was support wildcard certificate now,

trying update my development server to support it, 

in this case server use [certbot](https://github.com/certbot),

here is note for more detail.

<!--more-->

* certbot version need >= 0.22.0

* you need admin permission that can modify dns config

1. check certbot version
```
# certbot --version

certbot 0.22.0
```

2. run commend then add txt record to your domain and to prove you have own it.
```
#certbot -d *.wico.cc \
--manual \
--preferred-challenges \
dns certonly \
--server https://acme-v02.api.letsencrypt.org/directory

```

you will see the value that you need add to dns
```
-------------------------------------------------
Please deploy a DNS TXT record under the name
_acme-challenge.wico.cc with the following value:

PKNhsaOWpAUT-hLxoP1dNQum6in________________

Before continuing, verify the record is deployed.
-------------------------------------------------
```

add value to your dns
{% asset_img 1.png "image description" %}


btw if you not have do this step you will get a error message blow this.
```
Client with the currently selected authenticator does not support 
any combination of challenges that will satisfy the CA. 
You may need to use an authenticator plugin that can do challenges over DNS.
```

3. setting up your wildcard domain 
```
# certbot \
--authenticator standalone \
--installer nginx \
--pre-hook "systemctl stop nginx.service" \
--post-hook "systemctl start nginx.service" \
--server https://acme-v02.api.letsencrypt.org/directory
```

```
Saving debug log to /var/log/letsencrypt/letsencrypt.log
Plugins selected: Authenticator standalone, Installer nginx
Starting new HTTPS connection (1): acme-v02.api.letsencrypt.org
No names were found in your configuration files. Please enter in your domain
name(s) (comma and/or space separated)  (Enter 'c' to cancel): *.wico.cc
Cert not yet due for renewal

You have an existing certificate that has exactly the same domains or certificate name you requested and isn't close to expiry.
(ref: /etc/letsencrypt/renewal/wico.cc.conf)

What would you like to do?
-------------------------------------------------------------------------------
1: Attempt to reinstall this existing certificate
2: Renew & replace the cert (limit ~5 per 7 days)
-------------------------------------------------------------------------------
Select the appropriate number [1-2] then [enter] (press 'c' to cancel): 1
Keeping the existing certificate

Which server blocks would you like to modify?
-------------------------------------------------------------------------------
1: File: /etc/nginx/nginx.conf
Addresses: 80
Names: localhost
HTTPS: No
-------------------------------------------------------------------------------
Select the appropriate numbers separated by commas and/or spaces, or leave input
blank to select all options shown (Enter 'c' to cancel): 1
Deploying Certificate to VirtualHost /etc/nginx/nginx.conf

Please choose whether or not to redirect HTTP traffic to HTTPS, removing HTTP access.
-------------------------------------------------------------------------------
1: No redirect - Make no further changes to the webserver configuration.
2: Redirect - Make all requests redirect to secure HTTPS access. Choose this for
new sites, or if you're confident your site works on HTTPS. You can undo this
change by editing your web server's configuration.
-------------------------------------------------------------------------------
Select the appropriate number [1-2] then [enter] (press 'c' to cancel): 2

Which server blocks would you like to modify?
-------------------------------------------------------------------------------
1: File: /etc/nginx/nginx.conf
Addresses: 443 ssl, 80
Names: localhost
HTTPS: Yes
-------------------------------------------------------------------------------
Select the appropriate numbers separated by commas and/or spaces, or leave input
blank to select all options shown (Enter 'c' to cancel): 1
Redirecting all traffic on port 80 to ssl in /etc/nginx/nginx.conf

-------------------------------------------------------------------------------
Congratulations! You have successfully enabled https://*.wico.cc

You should test your configuration at:
https://www.ssllabs.com/ssltest/analyze.html?d=*.wico.cc
-------------------------------------------------------------------------------

IMPORTANT NOTES:
 - Congratulations! Your certificate and chain have been saved at:
   /etc/letsencrypt/live/wico.cc/fullchain.pem
   Your key file has been saved at:
   /etc/letsencrypt/live/wico.cc/privkey.pem
   Your cert will expire on 2018-06-13. To obtain a new or tweaked
   version of this certificate in the future, simply run certbot again
   with the "certonly" option. To non-interactively renew *all* of
   your certificates, run "certbot renew"
 - If you like Certbot, please consider supporting our work by:

   Donating to ISRG / Let's Encrypt:   https://letsencrypt.org/donate
   Donating to EFF:                    https://eff.org/donate-le
```

now you can see your web site was change to wildcard certificate 
{% asset_img 2.png "image description" %}

