# Orange Pi 6 Plus Android TV 14

Experimental Android TV 14 image for the Orange Pi 6 Plus.

This repository currently provides a complete bootable image only. Source code and build scripts are not included at this time.

## Status

This image is intended as a community alternative to the vendor Android image for users who want an Android TV focused setup.

### Working

- Android TV 14 boots on Orange Pi 6 Plus
- 4K60 output tested
- HDMI/DP audio working
- Android TV launcher working
- Google apps layer tested
- YouTube for Android TV working
- On-screen keyboard working
- Expanded userdata tested on a 256GB NVMe drive

### Known Limitations

- Experimental community image
- Bootloader remains unlocked
- Google Play certification is not guaranteed
- Widevine/DRM status is limited and may not satisfy paid streaming apps
- DisplayPort 4K120 output is not currently enabled
- Some 4K50 HEVC Main10 / HDR IPTV streams may stutter across players
- Balena Etcher / raw USB images are experimental
- microSD slot boot is not currently supported
- First boot may take several minutes

## Download

Images will be published from the GitHub Releases page:

https://github.com/Waferscode/orangepi6plus-ATV/releases

Recommended release format:

```text
orangepi6plus-atv14-vX.Y-fastboot.zip
orangepi6plus-atv14-vX.Y-fastboot.zip.sha256
```

## Flashing With Fastboot

Fastboot flashing is the recommended installation method for this build.

Recommended target: NVMe SSD.

1. Download the latest `fastboot.zip` release.
2. Extract the zip.
3. Put the Orange Pi 6 Plus into fastboot mode.
4. Connect USB from the host computer to the board.
5. Run the flash script from inside the extracted folder.

Linux:

```bash
chmod +x android_flush_images.sh
./android_flush_images.sh -t nvme -d sky1
```

Windows:

```bat
android_flush_images.bat nvme sky1
```

Flashing will erase Android partitions and userdata on the selected target.

## USB / Etcher Images

Raw USB images are experimental for this board. Fastboot works reliably because it talks directly to the CIX bootloader, flashes the GPT and partitions, selects the boot target, and finishes with the board-specific boot command.

Do not flash this release to the board's microSD slot. The current Android boot path is prepared around NVMe/fastboot, not SD-slot boot.

## Display Setup

For 4K60, enable the enhanced HDMI mode for the TV input before first boot. The setting name varies by TV brand:

```text
Enhanced HDMI
HDMI 2.0
HDMI Enhanced Format
HDMI Ultra HD Deep Color
Input Signal Plus
4K Enhanced
```

Without this, many TVs expose only 4K30 to the board.

## First Boot Notes

- The first boot can be slower than later boots.
- If the display is blank, try another HDMI port and confirm enhanced HDMI mode is enabled.
- If using a TV remote, make sure HDMI-CEC is enabled on the TV.
- If an app behaves oddly, reboot once after initial setup before debugging further.

## Reporting Issues

When reporting an issue, include:

- TV or monitor model
- Boot media type, for example NVMe or USB
- Display mode, for example 3840x2160@60
- Whether audio is HDMI/DP, 3.5mm, USB, or Bluetooth
- A short description of what was working before the issue

Useful Android commands:

```bash
adb shell wm size
adb shell wm density
adb shell dumpsys SurfaceFlinger | grep -Ei 'refresh-rate|forceClientComposition|usesDeviceComposition'
adb shell cat /proc/asound/pcm
adb shell df -h /data
```

## Disclaimer

This is an unofficial community image. It is not produced or supported by Orange Pi, CIX, Google, or Radxa.

Use at your own risk. Flashing images can erase data or leave a board temporarily unbootable until reflashed.

The image may include vendor, Android, Google, and third-party components that are governed by their own licenses and terms. The license file in this repository applies only to repository content where applicable, not automatically to every binary component inside the downloadable image.
