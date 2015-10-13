


---


# Introduction #

## What is BabelRoom? ##
BabelRoom is an open source platform for virtual conferencing and classrooms.

The current version is a complete rewrite of an older conferencing system which was written for a commercial start-up venture in 2010-2011. It's labelled version 2.x in acknowledgement of it's predecessor.

We are based in San Francisco, California.

# Connecting To BabelRoom #

## SIP (VoIP) ##
BabelRoom supports direct SIP audio connections from mobile devices, desktops and IP phones. In addition to bypassing the telephone network, the audio quality of SIP connections are significantly higher. This is the preferred way to achieve high-quality audio with BabelRoom.

### Examples of SIP devices: ###
  * [Free iPhone and iPad Apps](https://itunes.apple.com/us/app/linphone/id360065638)
  * [IP Telephones](http://www.amazon.com/Yealink-SIP-T20P-Phone-2-Lines-Voice/dp/B002D10C7K)
  * [Android Apps](https://play.google.com/store/apps/details?id=org.linphone)
  * [Desktop Apps](http://www.zoiper.com/softphone/)
  * [Google it](http://www.google.com/search?q=sip+client)

### Configuration ###
As BabelRoom does not provide SIP accounts no configuration is required. Simply enter a SIP URI of the following format when prompted for a telephone number:
```
sip:<your 6 digit conference PIN>@sip.babelroom.com
```

You will be connected directly to your conference bypassing PIN entry. The hostname (sip.babelroom.com) is for BabelRoom hosted conferences, this will change if you are running a private server.

SIP clients which require a valid SIP account registration cannot be used with BabelRoom. You can ignore any messages such as _unregistered_, _registration failed_, _invalid account_ etc. Most modern SIP clients and even some IP address (such as above) support this mode of operation.

### Mobile SIP ###
Many SIP clients for mobile devices work well with BabelRoom. In particular [Linphone](http://www.linphone.org/) works well on [iOS](https://itunes.apple.com/us/app/linphone/id360065638) and [Android](https://play.google.com/store/apps/details?id=org.linphone) devices. Up-to-date versions for iPhone, iPad and Android are available from the respective App stores.

Disregard the video capabilities of Linphone when using with the current release of BabelRoom.

When running Linphone 2.x for the first time skip the _account setup assistant_ (hit the cancel icon). Enter the SIP URI for your conference as noted above.

[Sipdroid](http://sipdroid.org/) is another compatible SIP client for Android that is worth mentioning.

# Software Development #

## How does the version numbering work? ##
We use the following version convention:
```
<major>.<minor>.<git commit count>
```
Example `2.37.182`

The major number represents a very large change-set, practically a new product. BabelRoom is a complete rewrite of an older conferencing system - hence it's major number is 2.

The minor number denotes larger change-sets that have server-side differences requiring migrations and/or special actions to upgrade.

The last number is the count of git commits on the clouds repository (https://github.com/babelroom/clouds).

There is a branch and set of server products (VM, AMI etc.) for each minor release. Servers are released with source code from their (minor version) branch and are upgradeable via `git pull` on that branch.

# WebRTC #
## What is WebRTC? ##
WebRTC (Web _Real Time Conferencing_) is an emerging technology for peer-to-peer video, audio and data sharing built into the browser. Think _Skype_ but based on open standards with no downloads or plugins.

While it's an exciting technology, it has not yet been standardized and should be considered experimental.

Google chrome current leads in supporting this feature.

http://www.google.com/?q=webrtc

## Does BabelRoom support WebRTC? ##
BabelRoom supports WebRTC for peer-to-peer conferences as of version 2.37.200.

As there is no centralized audio in a peer-to-peer conference, all associated features are hidden. This includes features for telephone network integration.

## How do I change a room to be a WebRTC peer-to-peer conference? ##
A conference room may be changed to the peer-to-peer conference by an admin by changing the WebRTC peer-to-peer settings in the access tab of the room settings dialog. The room settings dialog can be opened via the room menu in the top left corner.

## WebRTC doesn't work on my browser ##
  * Is the conference room a WebRTC peer-to-peer conference? If you can see the dialpad panel (click _Show Panels_ in top right corner) then the room is not a WebRTC room. Contact the room administrator. If you are the room administrator follow the instructions here http://code.google.com/p/babelroom/wiki/FAQ#How_do_I_change_a_room_to_be_a_WebRTC_peer-to-peer_conference? to change the room to a WebRTC peer-to-peer conference.

  * Does your browser support WebRTC? BabelRoom disables the camera icon (under your avatar) or eye icon (under other peoples avatars) when it detects your browser does not support WebRTC. Newer versions of the chrome browser support WebRTC. Other browsers (Mozilla Firefox, bowser) have limited support, often only after enabling special flags. Try one of the many online WebRTC applications such as https://apprtc.appspot.com/ to gauge WebRTC support in your browser.

  * Is there a problem getting access to your camera and/or microphone? Your browser will require you to consent to having your camera and microphone accessed in order to transmit over WebRTC via the camera icon. No consent is required to connect to another persons session via the eye icon. If you see an error such as _camera/microphone access denied_ this indicates the browser is not allowing access to BabelRoom. There are numerious reports that certain browsers (such as chrome) get _stuck_ and deny all access requests until a some form of browser restart clears it. Use your favorite search engine to research the issue. Try one of the many online WebRTC applications such as https://apprtc.appspot.com/ to isolate the issue. Review your browser advanced features settings, for example at chrome://flags

  * Are you pushing the envelope? WebRTC is an emerging technology and should be considered experimental. Browser support is often at Beta (or lower) quality level and implementations change from version to version. BabelRoom allows multi-party (i.e. >2) conferences with WebRTC - we are not aware of another system which allows more than 2 participants; even so you should not expect success with more than 3 or 4 participants all broadcasting at the same time. Use the _pause_ button to disable video streaming while leaving audio channels open. Reduce other programs running on your computer to free up CPU and memory resources.

  * How is your network? The peer-to-peer aspect of WebRTC using various advanced techologies to allow peers to communicate directly with each other despite firewalls between them. In some cases this is not possible. WebRTC will not work at all with certain very restrictive network configurations.

## What can I do to make WebRTC with work best in BabelRoom? ##
  * Have 2 people on the conference. Maybe 3. Max 4
  * If there is more than 2 people then use the _pause video stream_ and _mute_ features to avoid broadcasting unnecessary streams
  * Use a recent version of the google chrome browser and test it with https://apprtc.appspot.com/
  * Close down other applications to free computer resources. In particular close application which access the camera and microphone (such as _skype_)
  * Use a networking environment that has worked for yourself and your peers in the past, i.e. a networking change to a different office or different firewall may introduce a new problem.