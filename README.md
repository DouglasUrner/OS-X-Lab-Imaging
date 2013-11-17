OS-X-Lab-Imaging
================

Instructions for creating an OS X master image and imaging a school computer lab using DeployStudio.

This lab is used to teach digital photography and web design.

Prerequisites
-------------

* DeployStudio (http://www.deploystudio.com)

* An external disk on which to build your images. Configured thusly:
  * A small Boot partition, so that it can be used stand along if necessary, with a minimal OS installed, 20 GB.
  * Additional partition(s) sized to hold the master system(s), 44 GB.
  * The remaining disk space allocated to hold the system images. You will need enough space to hold your images plus twice the size of an image for building images, 90 GB.

Creating the Master System
--------------------------

Mac OS X (10.9)

Remove (or move to a restricted folder):
* Games (Chess, Game Center)
* Photo Booth
* iTunes
* FaceTime (and Messages?)

Add for Photography:
* Adobe Lightroom
* Adobe CS6 (less Flash tools and Fireworks, also for web design)
* EXIFTool

Add for Web Design:
* PhpStorm (free academic license)
* XCode command line tools (primarily for Git) xcode-select --install
* Bash extensions for Git

Configuration:
* Configure network.
* System Preferences > Sharing enable remote management (Apple Remote Desktop) with all options and remote login. Configure allowed users.
* System Preferences > Date & Time
* Launch and add license keys to applications
* Update system and applications

Server Setup & Configuration
----------------------------

Install OS X and the matching version of the Server application.

Server Settings

When you configure the server network interface and host name(s) make sure the server has a fixed IP address and select the "connect to the Internet" option (on the bottom). Getting the host name right seems to improve the stability of the Server application.

On the server launch the Server application, then click on the server's name under SERVER in the sidebar. Go to the Settings tab and check all four check boxes. This will allow for remote management and will enable push notifications. Push notifications are used to update profiles. You can also select the location for the service data (software updates, the mail store, etc).

Certificates

DNS

The server must be configured with a "three-part" domain name that does not end in .local – the .local TLD is served by mDNS and is not supposed to be served by a standard DNS server. For our lab we use the domain "room1215.pri" and set the search path to include our TLD.

DNS must be working correctly (forward and reverse resoltion must work) use "changeip -checkhostname" to verify this. If DNS is not working correctly things are likely to break all over the place in mysterious ways.

Open Directory

Do not configure Open Directory until DNS is working correctly.

Push Notifications

Profile Manager
