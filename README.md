# Ubuntu Server 20.04 LTS Autoinstaller configurations for bare metal K8s cluster

Automating the OS installation of Ubuntu Server 20.04 LTS on a cluster of 4 Intel NUC machines requires two elements:

- A local web server holding cloud init configuration files for each machine
- An USB flash drive with the Ubuntu ISO and a modified `grub.cfg` file with menu entries for each machine

More information at [https://ubuntu.com/server/docs/install/autoinstall-quickstart](https://ubuntu.com/server/docs/install/autoinstall-quickstart)

## Autoinstall web server

Simply execute `./serve.sh` to start the webserver on port `3003`. Requires Python3 to be preinstalled.

Configuration files will be made available available at `http://<your-ip-address>:3003/nuca/user-data`.

User data `user-data` configuration information at [https://ubuntu.com/server/docs/install/autoinstall-reference](https://ubuntu.com/server/docs/install/autoinstall-reference)

## Custom USB Flash drive

Challenge is to create a custom USB installer with easy to select configurations for each of the machines. This requires the following steps:

- Use a Linux GUI VM such as Ubuntu Desktop 20.04
- Install Ubuntu Cubic [https://launchpad.net/cubic](https://launchpad.net/cubic)
- Download the Ubuntu 20.04 LTS iso file
- Use Cubic to replace the `/boot/grub/grub.cfg` file with the one in this repository
- Save and build the custom Bootable ISO and write to a USB flash drive

A nice Cubic tutorial at [https://www.techrepublic.com/article/how-to-create-a-custom-ubuntu-iso-with-cubic/](https://www.techrepublic.com/article/how-to-create-a-custom-ubuntu-iso-with-cubic/)
