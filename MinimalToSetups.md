## Introduction ##
How to get from bare minimal ISO to ready to run setup scripts.

## Which ISO? ##
We use this:

```
CentOS-6.3-x86_64-minimal-EFI.iso
size: 381681664
md5sum: 4dd1ff9a521823e033dde6b152196de7
```

If you want to use something else, please read [this](WhyUseStandard.md) first.

Find and download the ISO. Google is your friend, _hint_: it may be quicker to search using the md5sum

Here's one location (good at time of writing):
http://mirror.symnds.com/distributions/CentOS-vault/6.3/isos/x86_64/CentOS-6.3-x86_64-minimal-EFI.iso

Verify it's the correct ISO
```
$ md5sum CentOS-6.3-x86_64-minimal-EFI.iso  
4dd1ff9a521823e033dde6b152196de7  CentOS-6.3-x86_64-minimal-EFI.iso
```

If you can't easily run md5sum (e.g. not on a linux host) at least verify the filesize matches that given above.

## Install from ISO ##

There are no specific instructions and requirements here. But note:

  * The sum of all current BR software is not more than about 1GB. A lot less if necessary and depending on whether all subsystems are needed.

  * Add more disk space as needed, but consider that media files are typically stored on cloud services (i.e. Amazon S3). So no reason to use the petabyte SAN

  * It's not necessary to do anything special. Defaults are fine.

  * Finish installation, remove installation media (if necessary), reboot, log in as root then continue with the next step below.

## Get a Network ##
This CentOS minimal install will not activate networking on boot. You'll need network access to continue this phase.

```
$ sudo ifup eth0
```

The scripts for this phase will automatically adjust _/etc/sysconfig/network-scripts/ifcfg-eth0_ so no need to finalize your network just yet. This _adjustment_ sets the _ONBOOT_ flag and also clears out the MAC (HWADDR) field to avoid later problems with udev renaming the device.

## From Bare Install ##
  * obtain _from\_minimal.sh_ and run it
```
$ curl https://raw.githubusercontent.com/babelroom/clouds/master/clouds/from_minimal.sh >./from_minimal.sh
$ sh ./from_minimal.sh
```

  * The last step of this script does some yum cleanup of older kernel firmware modules and a networking related step. Both of these can take a while (1-10 minutes) so if things appear stuck at this point please be patient.

  * Your indication that this phase has completed will be the following message:
```
    *** READY FOR SETUPS ***
```

  * If something went wrong please refer to [Trouble](Trouble.md)

  * Reboot

  * Continue to [Setups](Setups.md)
