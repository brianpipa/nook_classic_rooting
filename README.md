# How to root and install APKs on your Nook Classic 1st generation BNRV100 

**Instructions**  
I did this from linux. Steps for Windows/mac will differ.
Follow the instructions on the pages below, specifically, https://xdaforums.com/t/q-rooting-nook-classic-nook-first-edition.2395798/ ), but here are the things that weren't clear for me...
* to get my Nook's IP, I made note of the Nook's MAC address on the settings page, then I logged into my router and found the connected device with that MAC address and copied the IP address.
* I included the modified (correct) init.rc in this repo, so you don't have to do the pull and edit of the init.rc. You can just use this copy when you get to the step where you push it back to the device. NOTE: I did not verify there is nothing device-specific in the init.rc.
* Once you run ratc.bin and it succeeds, do NOT restart the Nook. Try crashing the browser again so you can push the init.rc.
* The entire process took me MANY MANY tries. I think all told it took me about 2 hours.

**Reference links:**
* https://www.mobileread.com/forums/showthread.php?t=119553
* https://xdaforums.com/t/q-rooting-nook-classic-nook-first-edition.2395798/
* https://github.com/ruediste-zz/NookPDFViewer/wiki/Installation
* https://github.com/AnotherKamila/nook-revival
* https://code.google.com/archive/p/nookdevs/downloads
* https://www.mobyware.org/android-os/system-utilities-tag/mynook-ru-launcher-download-13128.html
* http://twll.blogspot.com/p/nook-firmware-improvements.html

**APK notes:**
