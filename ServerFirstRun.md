# Congratulations! #

The server is available immediately after boot in a basic configuration.

Find it's IP address, drop that in a browser and start to play!

The servers initial IP will be displayed below the banner on the VM console. See screenshot [on this page](ServerInstall.md).

Or query it directly if logged-in:
```
$ ifconfig eth0
```

## Default BabelRoom Accounts ##
The system is pre-installed with 1 user account as follows:

```
email: default@bademail.bad
password: default
```
This user is also the owner of the default conference /demo

```
email: apitest@example.com
password: default
```
API examples and keys are associated with this user in for tutorials and samples to work without further configuration.

These passwords should be changed as soon as possible as they are (obviously) public.

## Next ##
Go to [ServerNextSteps](ServerNextSteps.md)