A few quick things you may wish to do after you've gotten a private server up and running.

### Cycle Keys (Recommended) ###
Various BabelRoom subsystems uses random hex data as input into salts, API keys and session data. The way we build and distribute amazon AMI's and virtual machines means all servers start out initially using the same set of secrets and keys. Until new keys are generated it would be pretty easy for a dedicated hacker to guess your session keys, API keys and generally impersonate and hijack any BabelRoom user account.

Cycling the keys generates a new set of secrets and seed data at random.

```
$ br --cyclekeys
```

_Note_ this step keys will invalidate all current sessions and API keys!

### Set an Internal IP Address (Optional) ###
Skip this if you are going to assign an external IP address or hostname. If you're running an amazon instance you will skip this step.

By default the server VM gets it's IP address via DHCP. Before locking in the IP address in this step you should ensure the address will not change by assigning a static address or configuring your DHCP server to always assign the same IP. The system will not function correctly if it is assigned a different IP address after configuring with `br --setip`.

If you will only access the server using an internal IP address then it's best to set it using --setip. The system will operate without this step but some of the hyperlinks between the room dashboard and account management UI will not function correctly until you perform this step.
```
[br@2-37 ~]$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:50:56:24:0D:C8  
          inet addr:192.168.66.127  Bcast:192.168.66.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fe24:dc8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:158615 (154.8 KiB)  TX bytes:1111074 (1.0 MiB)

[br@2-37 ~]$ br --setip 192.168.66.127
Configuration written
[br@2-37 ~]$ sudo reboot
```

### Set an External IP Address (Optional) ###
The external IP address is the publicly routable address for the server. Most of the time this will be the IP address of your firewall.

You must assign the external IP address if you wish to connect BabelRoom to the telephone network using FreeSWITCH, even if you assign a public hostname.

At present the --setip command is used to set the external IP address.
```
$ br --setip www.xxx.yyy.zzz
Configuration written
$ sudo reboot
```

### Set a Hostname (Optional) ###
```
$ br --sethost videochat.awesomeness.com
Configuration written
$ sudo reboot
```

### Setup SSL (Optional) ###
SSL is supported and active by default on port 443 using dummy self-signed certs. The process of enabling SSL just involves setting a hostname and installing valid certs. Further documentation pending, [complain here](SubscribeToTheNewsgroup.md).

### Simulate a Reboot ###
The following should have the same effect as a reboot in terms of how BabelRoom restarts.
```
# stop all BR services
$ br --offline

# restart all BR services
$ br --online
```

# Next #
[Advanced Setup](ServerAdvancedSetup.md)