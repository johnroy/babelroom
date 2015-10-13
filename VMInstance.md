## Summary of the Summary ##

Get it from [here](Resources.md)

_Note_ We are looking for feedback on this VM. Currently the VM is generated on VMware fusion (version 2.0.8) and the entire VM directory is compressed using zip. We are looking for [feedback](SubscribeToTheNewsgroup.md) on what the best format(s) are. Alternative packaging as well as alternate !VMware and VirtualBox release versions are possible options.

### Run the VM ###

Open your browser and point at the VM (i.e. it's IP address).

You should see a (pretty ugly temporary) landing page with a link to the conference room and account mgmt UI.

_more later ... stay tuned to this channel_!

## Access ##
  * Login to the VM as user _br_ at the VM console prompt
  * The account is passwordless (i.e. _passwd -d_). You will not be prompted for a password to login at VM console.
  * As there is no password you will not be able to access the VM remotely until you change the password or configure some other mechanism (such as ssh key/pairs)
  * The root password is not available
  * Use _sudo_ (when logged in as _br_) to execute privileged commands
  * You can always get a root shell using `sudo bash`

## Next ##
Go to [First Boot](ServerFirstRun.md)

##### How do we build it? #####
We follow the rough checklist here: https://github.com/babelroom/clouds/blob/master/clouds/vm_prep_steps.txt