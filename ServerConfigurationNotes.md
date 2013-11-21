Server Configuration Notes
==========================

Configuring an OS X server using Server.app has proven itself to be far more difficult than I would like.

These are notes on setting up OS X 10.9 (Mavericks) with Server 3 for use in a school lab setting. One of the quirks of this environment is that there is no "appropriate" DNS.

Steps
-----

Fresh install of OS – boot from flash drive, format boot partition and install. Currently using about 70 GB for the boot partition.

Basic OS X Configuration:
_________________________
* Defaults for keyboard, language, etc.
* Skip Apple ID (unless you have one you want to use for the machine)
* Skip registration (optional, this machines been registered more times than it can count…)
* Initial user is classroom administrative user account (not personal account of the teacher or other administrative user)
* Tidy up the account as you see fit
* Launch Software Update / App Store and install Server and any available updates
* Enable (or not) automatic updates as you see fit

Network Configuration
_____________________
* Configure the network interface that will be used for the server with a fixed IP address. However you need to do that. Make sure you have a workable netmask and – if at all possible – a working DNS server that will do forward and reverse resolution.

* If you can't get this set up right at this point you might consider editing /etc/hosts and configuring it there. Have not tested this idea.

Confirm that you have DNS working correctly with:

sudo /Applications/Server.app/Contents/ServerRoot/usr/sbin/changeip -checkhostname

Get this right before you proceed any further. If DNS is not working correctly (forward and reverse resolution for the server) it will bite you.

If you have multiple network interfaces it appears that OS X or the server tools will prefer an interface that can reach the Internet over the first one in the service order. If that is not the interface that will be providing the server's services you are likely to see changeip fail.

Before Launching Server:
________________________
* Set host name, "sudo scutil --set HostName foo.bar.baz". This is the FQDN of the machine. It must be at least three parts. It must not end in .local (that causes mDNS to serve the name and it supposedly leads to problems). The name can be made up, I use a name ending in .pri just because the rest of the district uses that internally (Microsoft shop).
* Set the local host name, "sudo scutil --set LocalHostName foo". Not sure what this is used for. I used the host name portion of the "HostName" (previous step).
* Set the computer name "sudo scutil --set ComputerName 'Foo'". Set this to a "pretty" version of the LocalHostName, with a space. I think this is the Bonjour name, some people set this to the same value as the "HostName". Not sure if that is necessary or provides any benefit.

Launch Server.app:
__________________
* Confirm that the host name and IP address(es) are what you expect. Fix it if necessary.
* On the Settings tab of the machine page, enable all of the options for remote management and push notifcations. Push notifications will require an Apple ID, create one if necessary. This requires an Internet connection.
* If necessary, configure the Mac OS X DNS server (and clean up anything necessary).
* Confirm that DNS is working correctly (changeip) and then turn on Open Directory, this can take a really long time – don't know if that is a bad sign or not.
* Turn on Web Sites. Confirm that you can connect to the web site.
* Set up Profile Manager
-- Enable device management, use Code Signing certificate
-- Check Sign configuration profiles
-- Turn on

Client Configuration
--------------------

It is essential that the client be configured to use DNS that correctly resolves the server (forward and reverse). Don't even think of proceeding until this is working.

Bind the client to Open Directory on the server.

Enroll the client to be managed by the server:
______________________________________________
