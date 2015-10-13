


---

# Introduction #
For historical reasons BabelRoom is divided functionality into a front-end peer database with users, invitations and conferences and a back-end database managing softpbx's, telephone interconnects and back-end integration. They are called _my_ (or _provisioning_, for conference provisioning) and _netops_

Code examples for inspecting database tables assume you are at a shell prompt as user _br_ on a [private server](ServerInstall.md).

# Provisioning #
## Users ##
```
$ echo "describe my.users;" | mysql -uroot 
```
### Ephemeral vs. Permanent Users ###
Every interaction in BabelRoom requires a valid user id. This is because any user could potentially interact with the system creating resources (e.g. files) and establishing a history.

It's not reasonable to force every user to go through a sign-up process. This is particularly true for third-party front-end integrations with environments such as Moodle and Elgg where the user has their account of record and BabelRoom merely adds a specific conferencing oriented featureset.

So BabelRoom has the concept of an _ephemeral_ user. This is an emerging system design pattern driven by the need to provide _progressive registration_ functionality. BabelRoom distinguishes ephemeral and permanent users by the presence of non-null for the _email\_address_ field. A separate field _email_ exists to record the email address of all users. The email\_address field is only set for permanent users.

It is important to understand ephemeral users when considering first generating plugins to other CMS and LMS systems. Typically every enter of a user into a conference from those systems is achieve by creating a new ephemeral user. This can lead to unexpected results where telephone pin codes and uploaded file permissions change for a user in the source system because they are assigned different ephemeral users in BabelRoom.

This area of the system will continue to evolve. In particular there is current exploration of the concept of "owned" ephemeral users, where they are _owned_ by other users or conferences. So when created by other users or for a specific conference they would always get the same ephemeral user id.


## Conferences ##
## Invitations ##

# Netops #
These are backend / internal objects in the _netops_ database. They are not accessed directly via APIs and are largely concerned with configuration of the system how it integrates with other systems on the back-end and how the system scales across multiple servers and regions.