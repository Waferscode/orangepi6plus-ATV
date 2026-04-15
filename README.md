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
- microSD slot boot is not currently supported by this release image
- First boot may take several minutes

## Download

Images will be published from the GitHub Releases page:

https://github.com/Waferscode/orangepi6plus-ATV/releases

Recommended release format:

```text
orangepi6plus-atv14-vX.Y.img.xz
orangepi6plus-atv14-vX.Y.img.xz.sha256
```

## Flashing With Balena Etcher

1. Download the latest image from Releases.
2. Open Balena Etcher.
3. Select the downloaded image.
4. Select the target drive.
5. Click Flash.
6. Safely eject the drive when flashing completes.
7. Insert the drive into the Orange Pi 6 Plus and boot.

Recommended target: NVMe SSD.

USB storage may also work when the board firmware is set to boot from USB storage.

Do not flash this release image to a microSD card for the board's microSD slot. The current Android boot path is prepared for NVMe or USB storage, not SD-slot boot.

Flashing will erase the selected drive. Double-check the target before writing the image.

## Flashing From Linux

Replace `/dev/sdX` with the actual target drive. Do not use a partition such as `/dev/sdX1`.

```bash
xz -dk orangepi6plus-atv14-vX.Y.img.xz
sudo dd if=orangepi6plus-atv14-vX.Y.img of=/dev/sdX bs=16M status=progress conv=fsync
sync
```

Optional checksum verification:

```bash
sha256sum -c orangepi6plus-atv14-vX.Y.img.xz.sha256
```

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
