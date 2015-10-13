## What? ##
|Region|us-west-2 (N. California)|
|:-----|:------------------------|
|AMI ID| ami-e5cde3a0            |
|Name  |403854088795/brcs-2-37-182|

### Need an AMI in a different region? ###
We build AMIs off CentOS images from bashton http://www.bashton.com/blog/2012/centos-6-3-ec2-ami/, we then apply some of the steps in [from minimal](MinimalToSetups.md) and [setups](Setups.md).

If possible we'll make an image in your region if you [contact us](SubscribeToTheNewsgroup.md)

## Running It ##
  * Run it with 1 IP address
  * You can fire this up on a micro instance and it will work just fine. Expect audio to be a little choppy.
  * For production use you'll need to make sure the instance gets enough quality CPU -- otherwise audio will be degraded. This is a requirement of the FreeSWITCH soft PBX. Some recommend a high CPU instance (m1.medium). Refer to http://wiki.freeswitch.org/wiki/Amazon_ec2

<a href='Hidden comment: 
== Example ==
There"s a micro instance running here: http://54.215.134.5/demo
'></a>

## Security Groups ##
You'll need to open the following
|tcp|22|optional, run sshd however you wish|
|:--|:-|:----------------------------------|
|tcp|80|                                   |
|tcp|443|optional                           |
|tcp|1935|                                   |
|tcp|1936|                                   |
|tcp|3001|(Temporary) for file upload / my account access|
|tcp|5060|Not sure this is needed -- TODO verify|
|udp|5060|Direct connections from SIP clients|
|udp|5080|Connections from SIP trunking providers for PSTN interconnects|
|tcp|10843|                                   |
|udp|16384 - 32768|                                   |

## Access ##
Access it in the usual way using key pairs. Access the server remotely using user ec2-user and -i option to ssh.
Once logged-in, change to user br (no password)
```
ec2-user$ su - br
```

## Next ##
Go to [First Boot](ServerFirstRun.md)

##### How do we build it? #####
We follow the rough checklist here: https://github.com/babelroom/clouds/blob/master/clouds/vm_prep_steps.txt