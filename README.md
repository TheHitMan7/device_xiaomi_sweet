## Device Tree for Redmi Note 10 Pro (sweet/sweetin)

The Redmi Note 10 Pro (codenamed "sweet/sweetin") is a mid-range smartphone from Xiaomi. It was announced and released in March 2021.

## Features

- ADB
- Decryption of /data
- Screen brightness settings
- Correct screenshot color
- MTP
- Flashing (OpenGApps, ROMs, Images and so on)
- Backup/Restore
- USB OTG
- Vibration support

## Compile

First checkout minimal twrp with aosp tree:

```
repo init -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp -b twrp-12.1
repo sync -c --force-sync --optimized-fetch --no-tags --no-clone-bundle --prune -j$(nproc --all)
```

Then add these projects to .repo/manifest.xml:

```xml
<project path="device/xiaomi/sweet" name="TheHitMan7/device_xiaomi_sweet" remote="github" revision="12.1" />
```

In order to successfully build in this branch, the following patch(es) will need to be cherry-picked:

```
git pull https://gerrit.twrp.me/android_bootable_recovery refs/changes/05/5405/35
git pull https://gerrit.twrp.me/android_system_vold refs/changes/40/5540/13
```

Finally execute these:

```
source build/envsetup.sh
export ALLOW_MISSING_DEPENDENCIES=true
export LC_ALL=C
lunch twrp_sweet-eng
make -j$(nproc --all) recoveryimage
```

## Downloads

* [TWRP-3.6.2_12-0-sweet.img](https://github.com/TheHitMan7/device_xiaomi_sweet/releases/download/v1.1/twrp-3.6.2_12-0-sweet.img)
* [TWRP-3.6.2_11-0-sweet.img](https://github.com/TheHitMan7/device_xiaomi_sweet/releases/download/v1.0/twrp-3.6.2_11-0-sweet.img)
