# How to root and install APKs on your Nook Classic 1st generation BNRV100 

**Reference links:**
* https://www.mobileread.com/forums/showthread.php?t=119553
* https://xdaforums.com/t/q-rooting-nook-classic-nook-first-edition.2395798/
* https://github.com/ruediste-zz/NookPDFViewer/wiki/Installation
* https://github.com/AnotherKamila/nook-revival
* https://code.google.com/archive/p/nookdevs/downloads
* https://www.mobyware.org/android-os/system-utilities-tag/mynook-ru-launcher-download-13128.html
* http://twll.blogspot.com/p/nook-firmware-improvements.html

**Instructions**  
I did this from linux. Steps for Windows/mac will differ.
Follow the instructions on the pages above, specifically, https://xdaforums.com/t/q-rooting-nook-classic-nook-first-edition.2395798/ ), but here are the things that weren't clear for me...
* to get my Nook's IP, I made note of the Nook's MAC address on the settings page, then I logged into my router and found the connected device with that MAC address and copied the IP address.
* I had to put the "crash webpage" onto a server I control that can run http. The one they mention, http://nookadb.suspended-chord.info/ was trying to redirect to https. I ended up using my own at http://gruntbug.com/n
* I included the modified (correct) init.rc in this repo, so you don't have to do the pull and edit of the init.rc. You can just use this copy when you get to the step where you push it back to the device. NOTE: I did not verify there is nothing device-specific in the init.rc.
* Once you run ratc.bin and it succeeds, do NOT restart the Nook. Try crashing the browser again so you can push the init.rc.
* The entire process took me MANY MANY tries. I think all told it took me about 2 hours.

**In a nutshell**
* all files neederd are in the rooting folder. unzip ratc.bin from ratc.zip
* crash the Nook browser then immediately try and connect with adb connect YOUR_NOOK_IP:5555
* if it says it couldn't connect, recrash the browser
* Once it does connect, run 1pushandrunratc - that will upload and runratc.bin so the next time you crash the browser, you will be root when transferring init.rc it will look like this:
* Eventually if you keep fialing, the Nook will become unstable and you will have to restart it. At that point you are back to square one and you have to start over)
```
>./1pushandrunratc
--push
ratc.bin: 1 file pushed. 0.2 MB/s (5392 bytes in 0.022s)
--shell execute
$ /system/bin/chmod 777 /sqlite_stmt_journals/ratc.bin
/sqlite_stmt_journals/ratc.bin
$ [*] CVE-2010-EASY Android local root exploit (C) 2010 by 743C

[*] checking NPROC limit ...
[+] RLIMIT_NPROC={1920, 1920}
[*] Searching for adb ...
[+] Found adb as PID 2047
[*] Spawning children. Dont type anything and wait for reset!
[*]
[*] If you like what we are doing you can send us PayPal money to
[*] 7-4-3-C@web.de so we can compensate time, effort and HW costs.
[*] If you are a company and feel like you profit from our work,
[*] we also accept donations > 1000 USD!
[*]
[*] adb connection will be reset. restart adb server on desktop and re-login.
$ 
--kill server
--restart server
* daemon not running; starting now at tcp:5037
* daemon started successfully
RECRASH BROWSER
```

* Now crash the browser again and each time it crashes, _immediately_ run 2connectandpushinit
* it will probably fail so recrash and keep trying
* eventually 2connectandpushinit will succeed like so:
```
 >./2connectandpushinit
--reconnect
connected to YOUR_NOOK_IP:5555
--push init
init.rc: 1 file pushed. 0.2 MB/s (14356 bytes in 0.057s)
```
and at that point you have succeeded. Now you can install APKs.

**APK notes:**
I'll put specific notes for each APK into https://github.com/brianpipa/nook_classic_rooting/tree/main/APKs but here is some general info:
* adb connect to your Nook. Once you are connected you can install with adb install THE_APK_YOU_WANT_TO_INSTALL.apk
* install the ru.mynook.launcher.apk so that you can run the other APKs you install. Once yuou install it and are running it, swipe up on any of the icons to get to the menu where you can add/remove/move the icons.
* I haven't figured out how to make the new launcher the default. It always asks if I want to use Home or Launcher.
* The main one I wanted was the new library so I could see covers of the epubs that I sideload. Install nookLibrary-0.1.7.apk for that (then in the launcher, add it so you can use it. Then remove the old library app from teh new launcher)
