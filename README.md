COSMO Post Install Script
==========================

### Important notes

#### Ubuntu 'bionic' (18.04 LTS)

This branch is the most up-to-date regarding packages renamed/changed/removed in Ubuntu 18.04.
It can be safely run on the latest Ubuntu LTS, but some errors may arise if using with an older version of Ubuntu.

The script supports to several Ubuntu-based distributions, in particular the compatibility has been tested with: [**Linux Mint**](https://linuxmint.com/), [**elementary OS**](https://elementary.io), **Pop!\_OS** by [System76](https://system76.com/pop).

#### Script reformat

The script has been **globally reformatted**, following the updates of the [original project](https://github.com/snwh/ubuntu-post-install). Now the script is now much more flexible and it is much easier to add new features.


### What is this?

A semi-automatic and interactive set of post-installation scripts for Ubuntu and its derivatives. You can use this project to install your favourite apps, set your preferred settings, and do minor housekeeping.

This project is free software; you can redistribute it and/or modify it under the terms of the [GNU General Public License](/LICENSE). If you have improvements, contributions to the [original](https://github.com/snwh/ubuntu-post-install) are much appreciated.

The scripts have been modified to setup all the things needed to have a working [COSMO](https://cosmo.epfl.ch) workstation. It is just a guided version of the manual procedure described in the document "Deployment of a new COSMO machine".


### Usage

You can get the latest version:

    git clone https://github.com/edoardob90/cosmo-post-install.git

and then run the script with:

```
./cosmo-post-install-script.sh
```

**Remember:** the script has to be run after the OS installation by the user "local" created during installation (because many parts need root permissions).


### Organization

This project is designed to be fairly modular (and not be one huge script) so you can easily delete or exclude bits/functions that you don't want to use.

 * [`data`](/data): files which are lists of packages read by various functions.
 * [`functions`](/functions): the main functions of this scriptset. They should require little user-preference modification.
 * [`apps`](/functions/apps): functions for installing third-party applications. They are called in the [`install_thirdparty`](/functions/install_thirdparty) function.


## LDAP interactive configuration

0. **Preparation** 
### !!! WARNING !!!

Before going through the configuration of shared HOMES and LDAP authentication, you **must** be sure to use the correct DNS servers. You can check them with following command

```
nmcli dev show | grep DNS
```
You could have 2 or 3 servers. Check that these servers are either `127.178.15.[227-229]` or `127.178.15.[7-8]`. If you are not using these servers, than be aware that you could face problems with the Kerberos authentication procedure set up by the script. _Forewarned is forearmed..._

---

To configure shared homes & use the central NAS, choose “System configuration” in the main menu of the configuration script; then choose “Setup remote HOMES and LDAP authentication”.
During installation of required packages, an interactive setup will be prompted (**twice**, it's not an error). The settings are the following:

1. **Configure System**
If you decided to use Ubuntu minimal installation please install the packages xterm and curl before using the script. Then use in the script `Configure System`, then `(1) Install required packages for remote homes & central authentication`

*LDAP configuration*

- LDAP server: `ldap://ldap.epfl.ch/`
- Distinguished names: `o=epfl,c=ch`
- LDAP version: 3
- LDAP auth configuration: answer **no** to the following two questions
- you will be asked again for the same first 2 options, just repeat the instructions above
- LDAP services: tick with **whitespace** the following three services: `passwd`, `groups`, `shadow`

*Kerberos realm*
Default realm: `INTRANET.EPFL.CH` (*careful to the uppercase*)

The installation should be finished and you should be back in the scripts menu, now choose `(2) Setup remote homes`. 

2. **Installation of packages for work**

You can use to script to install common packages, you are not required and can install them by yourself. However it is recommended to install at least `development tools` and `utilities`. For installing the printer, please use the official instruction of EPFL.

## Adding Functions

Adding additional functions is as easy as editing one of the many already included functions and simply changing the variables. When you do add (or remove) functions be sure to update any main function (such as [`install_thirdparty`](/functions/install_thirdparty)) to reflect those changes.

## TODO

- [x] TeXLive installation from official repository (needs to be included in the new script version).
- [ ] Automated installation of EPFL printers (printers' pool MyPrint).
