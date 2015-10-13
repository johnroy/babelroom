# Server Update #

It's relatively straightforward to upgrade a server within the same minor release (update the build number). The process essentially involves a `git pull`

## Steps ##

  1. login to the server as user br
```
[ec2-user@ip-10-0-0-210 ~]$ su - br
[br@ip-10-0-0-210 ~]$ pwd
/home/br
```
  1. stop all services
```
[br@ip-10-0-0-210 ~]$ br --offline 
Bring offline...
sudo service babelroom-run stop
Stopping my: e/br/gits/clouds/gen/node/app.js: [  OK  ]
Stopping estream: [  OK  ]
Shutting down red5: 
Terminating...
[  OK  ]
Stopping ./init.pl: 
Stopping mysqld:                                           [  OK  ]
[br@ip-10-0-0-210 ~]$
```
  1. cd to gits/clouds
```
[br@ip-10-0-0-210 ~]$ cd gits/clouds
[br@ip-10-0-0-210 clouds]$ pwd
/home/br/gits/clouds
```
  1. do a `git pull`, make sure this is successful before continuing, if you get an error skip to the troubleshooting section below for hints.
```
[br@ip-10-0-0-210 clouds]$ git pull 
Updating 9a8cccd..c2fd1ee
Fast-forward
 apiary.apib                                        |  261 ++++++
 clouds/bare_instance3.sh                           |    5 +-
 clouds/primers/cdn_conf                            |    3 +-
 clouds/primers/netops_rc                           |    9 +-
 clouds/setup_node.sh                               |    3 +
    [... lots more output ...]
```
  1. regenerate the javascript/CSS packages
```
[br@ip-10-0-0-210 clouds]$ cd gen
[br@ip-10-0-0-210 gen]$ make clean && make
make -C cdn_root/v1 clean
make[1]: Entering directory `/home/br/gits/clouds/gen/cdn_root/v1'
make -C ./c clean
make[2]: Entering directory `/home/br/gits/clouds/gen/cdn_root/v1/c'
rm -f css/gen_workspace.css ws_js/gen.min.js gen-other1.min.js gen-other2.min.js gen.min.js
make[2]: Leaving directory `/home/br/gits/clouds/gen/cdn_root/v1/c'
rm -f br_api.min.js br_api.full.min.js src/tmp.min.js
make[1]: Leaving directory `/home/br/gits/clouds/gen/cdn_root/v1'
rm -f cdn_root/v1/AUTO/conference_options.js rails/my/app/models/* cdn_root/v1/AUTO/conference_options.js node/AUTO_routes.js node/AUTO_gen.tmp node/AUTO_version.js node/AUTO_apiary.tmp
  [... lots more output ...]
```
  1. done, reboot
```
[br@ip-10-0-0-210 gen]$ sudo reboot
```

## Troubleshooting ##
You may encountering this error:
```
error: Your local changes to 'gen/rails/my/db/schema.rb' would be overwritten by merge.  Aborting.
Please, commit your changes or stash them before you can merge
```
This is a temporary problem related to issues in the old rails UI. Just nuke that file as below and attempt the `git pull` again:
```
[br@ip-10-0-0-210 clouds]$ git checkout gen/rails/my/db/schema.rb
```

## Notes ##
Starting with 2.38 server packages will be released with software associated with a specific git release branch. Software for 2.37 is associated with the git master branch.