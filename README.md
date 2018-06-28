<<<<<<< HEAD
COSMO Post Install Script
==========================

### Important note

Since from July the 1st (tentative) Ubuntu **16.04** will be officially offered a migration to the next LTS release (**18.04**), a new branch is progressively been updated to reflect packages' changes & related stuff.
Before that date, the two releases will coexist. If you are installing Ubuntu 18.04 from scratch, please change to the `1804LTS` branch before running the script.

---

This project provides a set of shell scripts to be run after a fresh install of an Ubuntu(-based) OS. It will install your favourite applications, set your preferred settings, etc.

The scripts have been modified to setup all the things needed to have a working COSMO workstation. It is just a guided version of the manual procedure described in the document "Deployment of a new COSMO machine".

Feel free to copy, improve and distribute.

You can get the latest version:

    git clone https://github.com/edoardob90/cosmo-post-install.git


## Usage
=======
Ubuntu Post Install Scripts
===========================

A semi-automatic and interactive set of post-installation scripts for Ubuntu and its derivatives. You can use this project to install your favourite apps, set your preferred settings, and do minor housekeeping.

This project is free software; you can redistribute it and/or modify it under the terms of the [GNU General Public License](/LICENSE). If you have improvements, contributions to the [original](https://github.com/snwh/ubuntu-post-install) are much appreciated.

## Organization

This project is designed to be fairly modular (and not be one huge script) so you can easily delete or exclude bits/functions that you don't want to use.

 * [`data`](/data): files which are lists of packages<sup>&dagger;</sup> read by various functions.
 * [`functions`](/functions): the main functions of this scriptset. They should require little user-preference modification.
 * [`apps`](/functions/apps): functions for installing third-party applications. They are called in the [`install_thirdparty`](/functions/install_thirdparty) function.
>>>>>>> upstream/master

*<sup>&dagger;</sup>These lists are preferential and you should to update them with packages you prefer*

```
./cosmo-post-install-script.sh
```

**Remember:** the script has to be run after the OS installation by the user "local" created during installation (because many parts need root permissions).

## LDAP interactive configuration

### WARNING

Before going through the configuration of shared HOMES and LDAP authentication, you **must** be sure to use the correct DNS servers. You can check them with following command

```
nmcli dev show | grep DNS
```
You could have 2 or 3 servers. Check that these servers are either `127.178.15.[227-229]` or `127.178.15.[7-8]`. If you are not using these servers, than be aware that you could face problem with the Kerberos authentication setup by the script. _Forewarned is forearmed..._


To configure shared homes & use the central NAS, choose “System configuration” in the main menu of the configuration script; then choose “Setup remote HOMES and LDAP authentication”.
During installation of required packages, an interactive setup will be prompted (**twice**, it's not an error). The settings are the following:

1. **Kerberos realm**

    Default realm: `INTRANET.EPFL.CH` (*careful to the uppercase*)

2. **LDAP configuration**

    - LDAP server: `ldap://ldap.epfl.ch/`
    - Distinguished names: `o=epfl,c=ch`
    - LDAP version: 3
    - LDAP auth configuration: answer **no** to the following two questions

Everything else is managed by the script.

## Adding Functions

Adding additional functions is as easy as editing one of the many already included functions and simply changing the variables. When you do add (or remove) functions be sure to update any main function (such as [`thirdparty`](/functions/thirdparty)) to reflect those changes.

## TODO
- [x] TeXLive installation (from official repository)
- [ ] Automated installation of EPFL printers (printers' pool MyPrint)
