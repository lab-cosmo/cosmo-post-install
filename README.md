COSMO Post Install Script
==========================

This project provides a set of shell scripts to be run after a fresh install of an Ubuntu(-based) OS. It will install your favourite applications, set your preferred settings, etc.

The scripts have been modified to setup all the things needed to have a working COSMO workstation. It is just a guided version of the manual procedure described in the document "Deployment of a new COSMO machine".

Feel free to copy, improve and distribute.

You can get the latest version:

    git clone https://github.com/edoardob90/cosmo-post-install.git


## Usage

Run from source folder:

```
./cosmo-post-install-script.sh
```

**Remember:** the script has to be run after the OS installation by the user "local" created during installation (because many parts need root permissions).

## LDAP interactive configuration

To configure shared homes & use the central NAS, choose “System configuration” in the main menu of the configuration script; then choose “Setup remote HOMES and LDAP authentication”.
During installation of required packages, an interactive setup will be prompted. The settings are the following:

1. **Kerberos realm**

    Default realm: `INTRANET.EPFL.CH` (*careful to the uppercase*)

2. **LDAP configuration**

    - LDAP server: `ldap://ldap.epfl.ch/`
    - Distinguished names: `o=epfl,c=ch`
    - LDAP version: 3
    - LDAP auth configuration: answer **no** to the following two questions

Everything else is managed by the script.

## TODO
- [x] TeXLive installation (from official repository)
- [ ] Automated installation of EPFL printers (printers' pool MyPrint)
