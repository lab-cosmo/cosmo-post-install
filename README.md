COSMO Post Install Script
==========================

This project provides a set of shell scripts to be run after a fresh install of an Ubuntu(-based) OS. It will install your favourite applications, set your preferred settings, etc.

The scripts have been modified to setup all the things needed to have a working COSMO workstation. It's just a straightforward version of the manual procedure described on the document "Deployment of a new COSMO machine". Only few details have to be set manually (only printer setup and TeXLive installation). For these, please refer to the official document on Google Docs folder.

Feel free to copy, improve and distribute.

You can get the latest version:

    git clone https://github.com/edoardob90/ubuntu-post-install.git

**Remember:** the script has to be run after the OS installation through the users "local" (beacuse many parts need root permissions).

##Usage:

Run from source folder:

    ./COSMO-post-install-script.sh
