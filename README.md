# twrp-sggp
Setting up a minimal tree for building TWRP
Android 5.1 branch

This repo is ~2.6GB
To initialize the main repository:

repo init -u https://github.com/ts-root78/twrp-sggp.git

Then add any recovery/device trees/kernels you need to a file (one XML for each device) and add them to the .repo/local_manifests folder of your initialized repo folder.
Make a .repo/local_manifests/local_manifests.xml file and insert the following code:

<?xml version="1.0" encoding="UTF-8"?>
        <manifest>
        <remove-project name="android_bionic" />
        <project path="bionic" name="CyanogenMod/android_bionic" remote="github" revision="cm-12.1" />
        </manifest>


Once added:

repo sync

Done

To build recovery:

. build/envsetup.sh
lunch (select device from list)
make -j5 installclean
time make -j5 recoveryimage
