# Alpine Linode Bootstrap

A simple script that can be executed in recovery mode to bootstrap Alpine Linux on a Linode server.

## Creating a Linode

This script assumes your Linode will have three disks for boot, root, and swap, assigned to /dev/sda, /dev/sdb, /dev/sdc, respectively. If you decide not to use a swap disk, you will need to manually delete the relevant parts from the script (which should be fairly easy).

Once the disks have been created, make a new configuration profile. It can be labeled anything you would like, but the following options should be changed: **Kernel** to GRUB 2; **Block Device Assignment**s to the order specified above; all **Filesystem/Boot Helpers** to *No*. Everything else should be left as the default. 

Boot the Linode into recovery mode with the disks assigned as above.

## Executing the Script

Connect to the Linode with Lish either via SSH or the browser console. To download and run the script:

    curl -o- https://raw.githubusercontent.com/jac0/alpine-linode-bootstrap/master/alpine-linode-bootstrap.sh | bash

Once that finishes, shut the Linode down from recovery mode and, staying in the Lish console, run:
  
    boot 1

After a bit, you should be at the Alpine login screen. The root user, by default, does not have a password. At this point, you can install an SSH server, which pretty much completes the installation.

## Credit

This script is basically [Andy Leap's guide](https://github.com/andyleap/docs/blob/master/docs/tools-reference/custom-kernels-distros/install-alpine-linux-on-your-linode.md) written as a working script (with fixed networking!), so big thanks to him.
