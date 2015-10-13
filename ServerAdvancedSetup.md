## Overview ##

The BabelRoom cloud server is CentOS (linux) based server software. It will be familiar ground to any experienced linux administrator or developer.

It makes sense to write an introductory level tool to aid configuration by novices and those new to BabelRoom. That is the purpose of the _br_ program. On the other hand it makes no sense to attempt to provide a one-size-fits-all advanced configuration tool.

So this section documents enough of BabelRoom standard startup mechanism and _br_ program so that you can disable those startup mechanisms fully.

Once disabled the conference server will have a working but static configuration. You can then apply configurations and software from the broad and varied pool of linux server resources augmented by your own imagination.

## Steps ##
  * Disable `/etc/init.d/babelroom-prime` and `/etc/init.d/babelroom-run` from running on startup. Delete them, move them or use `chkconfig`.

  * Read the _startup_ line in `/home/br/config`:
```
...
startup: mysqld freeswitch node_app mongrel_my estream red5 netops <other>
...
```
Each of the listed entries were started on boot by `babelroom-run`. Since you've disabled that you should make alternate arrangements

  * `babelroom-prime` re-generates all the configurations from `/home/br/config`. Be aware that if it runs it will overwrite your changes.