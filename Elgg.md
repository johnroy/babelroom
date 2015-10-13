## BabelRoom and Elgg ##
Elgg is a popular open-source framework for social networking websites. It supports enhance and customization via a plugin modules.

BabelRoom has developed a plugin for Elgg:

  * [on elgg.org](http://community.elgg.org/plugins/1410681/latest/babelroom)
  * [source on github](https://github.com/babelroom/elgg-mod_babelroom)

## Using Elgg with BabelRoom 2.38 ##
In 2.38 the simple "Join" elgg widget was replaced with group chat, peer-to-peer video conferencing and host presentations functions, amoungst others.

![http://community.elgg.org/plugins/icon/1553751/icon.jpg](http://community.elgg.org/plugins/icon/1553751/icon.jpg)

To setup a BabelRoom widget on a profile page, do the following steps
  * Ensure BabelRoom plugin is installed as outlined under #Installation and Plugin Settings -- "BabelRoom" should appear as an available widget to add on profile page.
  * Add a BabelRoom widget to the page.
  * Click on "cog" icon on widget top to edit settings.
  * Select the "sub widget-type" to the required function from the dropdown. Optionally set widget height.
  * Save the settings.
  * Reload profile page.



![http://community.elgg.org/plugins/icon/1553798/icon.jpg](http://community.elgg.org/plugins/icon/1553798/icon.jpg)

## Installation and Plugin Settings ##
### Installation ###
Refer to your elgg documentation for details on the process of adding plugins to your elgg instance. The zipfile for the BabelRoom plugin is [here](http://community.elgg.org/plugins/1410681/2.38.2a/babelroom)

After installing, activate the plugin. Optionally change the default configuration as outlined below.

### Plugin Settings ###
BabelRoom work out-of-the-box by creating conference rooms using a default user on the shared hosted server bblr.co

The plugin settings allows an alternate user account or even a private server instance to be configured.

![http://community.elgg.org/plugins/icon/1553753/icon.jpg](http://community.elgg.org/plugins/icon/1553753/icon.jpg)

### Using ###
It is necessary to reload the full page whenever a BabelRoom widget settings are changed.
#### Peer to Peer ####
This widget allows 2 users to videochat using webrtc. WebRTC must be supported by the users browsers. Newer versions of google chrome and firefox browsers support WebRTC.

You should be able to see an entry for every other user regardless of webRTC support level or their availability. A _call_ link will indicate when other users may accept a call.

### Group Chat ###
This is a simple shared group text chat. It will be initially empty until somebody says something ...

### Conference ###
This is a jumping point to entry full conference. It may contain detail on current conference status (number of users) and access information.

### Presentation ###
Present or view a presentation. Most document formats can be uploaded as a presentation including a single image or text file. It may take a view seconds or minutes for documents to be prepared for display. Large documents should be uploaded ahead of time in order to ensure presentations are available before meeting.