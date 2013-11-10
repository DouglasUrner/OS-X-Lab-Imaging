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
-----------------

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

Configuration:
* Configure network.
* System Preferences > Sharing enable remote management (Apple Remote Desktop) with all options and remote login. Configure allowed users.
* System Preferences > Date & Time
* Launch and add license keys to applications
* Update system and applications
