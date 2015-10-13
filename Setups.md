## User _br_ ##
From this point forward you'll login and initiate every step as the user _br_.

New instances are created without a password for the br user.

This means you will not be able to login as user br remotely (other than using VM console).

If you need to be able to login remotely as user br then set a password or configure ssh keys.

## All Setups Run From Here ##

Change directory and run setups. All setups run from here:

```
$ cd ~/gits/clouds/clouds
$ ls setup_*
setup_all.sh          setup_fs.sh            setup_nginx.sh          setup_red5.sh
setup_base.sh         setup_gen.sh           setup_node.sh           setup_short.sh
setup_buildtools.sh   setup_mysql_client.sh  setup_openssl_devel.sh
setup_extra_utils.sh  setup_mysqld.sh        setup_perl.sh
setup_fail2ban.sh     setup_netops.sh        setup_rails.sh
```

You can install one or all of these subsystem setups. Dependent setups are automatically run as necessary. However, we recommend you start by installing everything:

```
$ ./setup_all.sh
```

A smart way to run setups is to preserve output for later reference:
```
$ ./setup_all.sh 2>&1 | tee /tmp/setup_all.out
```

Problems? see [troubleshooting](Trouble.md)

The software has been installed, if you are running in a VM you may wish to snapshot at this point. If so then _halt_ and snapshot. If not you should reboot.

Next go to [First Boot](ServerFirstRun.md)