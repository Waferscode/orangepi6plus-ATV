# Release Template

Use this as a starting point for GitHub Releases.

## Orange Pi 6 Plus Android TV 14 vX.Y

Experimental Android TV 14 image for Orange Pi 6 Plus.

### Download

- `orangepi6plus-atv14-vX.Y.img.xz`
- `orangepi6plus-atv14-vX.Y.img.xz.sha256`

### Flashing

Flash the image with Balena Etcher, Raspberry Pi Imager, or `dd`.

Recommended target: NVMe SSD.

USB storage may also work when the board firmware is set to boot from USB storage.

Do not flash this image to a microSD card for the board's microSD slot. This release is prepared for NVMe or USB storage, not SD-slot boot.

### Highlights

- Android TV 14
- 4K60 output tested
- HDMI/DP audio working
- Android TV launcher and Google apps layer tested
- YouTube for Android TV working
- On-screen keyboard working
- Expanded userdata tested on 256GB NVMe

### Known Limitations

- Experimental community image
- Bootloader remains unlocked
- Google Play certification is not guaranteed
- Widevine/DRM status is limited and may not satisfy paid streaming apps
- DisplayPort 4K120 output is not currently enabled
- Some 4K50 HEVC Main10 / HDR IPTV streams may stutter across players
- microSD slot boot is not currently supported by this release image

### Recommended Display Setup

Enable enhanced HDMI mode on the TV input before first boot:

```text
Enhanced HDMI / HDMI 2.0 / HDMI Ultra HD Deep Color / Input Signal Plus
```

### Checksums

```text
<paste sha256sum here>  orangepi6plus-atv14-vX.Y.img.xz
```
