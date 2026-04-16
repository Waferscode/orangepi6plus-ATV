# Release Template

Use this as a starting point for GitHub Releases.

## Orange Pi 6 Plus Android TV 14 vX.Y

Experimental Android TV 14 image for Orange Pi 6 Plus.

### Download

- `orangepi6plus-atv14-vX.Y-fastboot.zip`
- `orangepi6plus-atv14-vX.Y-fastboot.zip.sha256`

### Flashing

Fastboot flashing is the recommended installation method.

Recommended target: NVMe SSD.

Linux:

```bash
chmod +x android_flush_images.sh
./android_flush_images.sh -t nvme -d sky1
```

Windows:

```bat
android_flush_images.bat nvme sky1
```

Raw USB / Balena Etcher images are experimental for this board.

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
- Balena Etcher / raw USB images are experimental
- microSD slot boot is not currently supported

### Recommended Display Setup

Enable enhanced HDMI mode on the TV input before first boot:

```text
Enhanced HDMI / HDMI 2.0 / HDMI Ultra HD Deep Color / Input Signal Plus
```

### Checksums

```text
<paste sha256sum here>  orangepi6plus-atv14-vX.Y-fastboot.zip
```
