Manifest for building CyanogenMod 13 (Marshmallow) and Resurrection Remix (Marshmallow) for:

1. Galaxy Ace 3 LTE GT-S7275R/B/T (loganreltexx) --> http://goo.gl/L4WSqe

2. Galaxy Express GT-i8730/T (expressltexx) --> http://goo.gl/x1KJl0

3. Galaxy Express 2 SM-G3815 (wilcoxltexx) --> http://goo.gl/Fi2K3M


Instructions to build alone:

Before anything follow this excellent guide to prepare building environment. Ubuntu 16.04 is preferred:

http://forum.xda-developers.com/chef-central/android/guide-how-to-setup-ubuntu-16-04-lts-t3363669

Only note to ignore these commands from the tutorial above, we will replace those commands with others:

A. mkdir ~/android

B. cd ~/android

C. repo init -u https://github.com/CyanogenMod/android.git -b cm-13.0

Now that you have done everything else from this guide except the commands above, open a new terminal:

1. mkdir ~/cm13

2. cd ~/cm13

3. repo init -u https://github.com/CyanogenMod/android.git -b cm-13.0

4. mkdir .repo/local_manifests

5. cd .repo/local_manifests

6. wget https://github.com/MSM8930-Samsung/android_manifest/raw/cm-13.0/local_manifest.xml

7. cd ~/cm13

8. repo sync --force-sync

When the process is finished, you will have fetched CyanogenMod source code, under $HOME/cm13 directory 

Optinal step is to setup our enabled in ~/.bashrc ccache (for faster build on second time):

1. cd ~/cm13

2. prebuilts/misc/linux-x86/ccache/ccache -MXG, where X = Size in Gigabytes

Now it is compile time ;) :

1. cd ~/cm13

2. repo sync --force-sync -jX, where X = Number of CPU cores on PC + 1

3. . build/envsetup.sh

4. lunch cm_loganreltexx-userdebug or lunch cm_expressltexx-userdebug or lunch cm_wilcoxltexx-userdebug (depending on what device you are building for)

5. time mka bacon -jX, where X = Number of CPU cores on PC + 1

When this very long (especially on low-end PC) finishes, then you will find the flashable zip on ~/cm13/out/target/product/devicename/

Note: This process can be done only on 64bit systems, with 4GB RAM as minimum
