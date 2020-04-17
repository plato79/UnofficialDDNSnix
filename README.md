UnofficialDDNSnix
=================

UnofficialDDNSnix is a CentOS 6, Debian 6, and Debian 7, FreeBSD service which provides dynamic DNS for regular registrars. Instead of signing up with a dynamic DNS provider and creating a CNAME record at your registrar to point to your dynamic DNS (for example: homeserver.mydomain.com -> alfred1986.dynamicdnsprovider.info), UnofficialDDNS cuts out the middle man and creates A records directly.


Supported Registrars
--------------------

Currently **Name.com** is the only supported registrar. Go to https://www.name.com/reseller to apply for an API token.
UnofficialDDNSnix needs the following:
* Name.com user name.
* Password (API token).
* The (sub)domain which will point to your server.

It might take a couple of days to get a reply from their customer support with your token.


Supported Platforms
-------------------

Both 32 and 64-bit versions of the following operating systems are supported:
* CentOS 6
* Debian 6 (squeeze)
* Debian 7 (wheezy)
* FreeBSD


Usage for Linux
---------------

Just install the package, edit **/etc/UnofficialDDNS.yaml** with your user/password/domain, and run **service UnofficialDDNS start**. Look at logs in **/var/UnofficialDDNS/** to make sure it started without any errors.

FreeBSD
-------

Copy the **uddns** file to **/etc/rc.d** or **/usr/local/etc/rc.d** folder. Set these sysrc values:

**uddns_enable**: Enables uddns service to execute automatically ( Default NO )
**uddns_user**  : User for pid file  ( Default uddns )
**uddns_group** : Group for pid file ( Default uddns)
**uddns_dir**   : Folder for UnofficialDDNS ( Default **/usr/local/uddns** )
**uddns_config**: Config file for UnofficialDDNS ( Default **uddns_dir/UnofficialDDNS.yaml** )

After setting these values you can start the service like this as root: **service uddns start**
The log file is **/var/log/UnofficialDDNS.log** 

A template file for **UnofficialDDNS.yaml** is available. You need to modify it for your name.com settings.