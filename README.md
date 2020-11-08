# Documentation

Documentation and releases of UBports for Tadiphone TP1803.

This port is based on the UBports GSI image by @erfanoabdi.

# Status

If installed correctly, most features should be working. See "Known Issues" for a list of known bugs.

# Installation

1. Flash custom `abl` and `recovery` on your Tadiphone. If you want to use Anbox, make sure to flash the one provided in the [Releases](https://github.com/tadiphone-ubports/documentation/releases) page of this repository.
2. If you are coming from a ROM newer than Android Q, restore your `modem` partition to the stock one.
3. In bootloader, flash `halium-boot.img`, `dtbo.img` and `vendor.img` from the [Releases](https://github.com/tadiphone-ubports/documentation/releases) page of this repository.
4. Reboot into recovery, __FORMAT__ data.
5. Sideload `ubports_GSI_installer_XX.zip` (replace XX with the latest version) from <https://build.lolinet.com/file/halium/GSI/>
6. Sideload `ubports_firmware_mount_patcher.zip` from the [Releases](https://github.com/tadiphone-ubports/documentation/releases) page of this repository.
7. Reboot into system and enjoy.

Note: the default user and password is `phablet`. For more details, see the ubports GSI wiki at <https://github.com/ubports/porting-notes/wiki/Generic-system-image-(GSI)>

# Anbox

Currently, Anbox needs some manual configuration to get working.

First of all, remount `/` as read-write

```bash
sudo mount -o remount,rw /
```

Then install `anbox-ubuntu-touch`

```bash
sudo apt-get update && sudo apt-get install anbox-ubuntu-touch
```

After this, create `~/anbox-data` and `~/anbox-data/.enable`, then download <http://cdimage.ubports.com/anbox-images/android-armhf-64binder.img> to `~/anbox-data/android.img`.

```bash
sudo start -q anbox-container
start -q anbox-session
```

Wait for a minute or so you should see Anbox apps start popping out in application list.

# Update

Unfortunately there is no OTA update support for ubports GSI yet.

## Updating halium-boot.img and vendor.img

Just flash the two images in bootloader mode and reboot

## Updating UBports GSI

Download the new `ubports_GSI_installer_XX.zip`, sideload it and `ubports_firmware_mount_patcher.zip` again in recovery.

## Updating via apt-get (Unsupported)

You can actually update via `apt-get update && apt-get upgrade` after re-mounting the rootfs as read-write. However, this method of upgrading is unsupported by UBports and may cause issues, though generally it should be fine as long as you stay in the same LTS version of Ubuntu. Just keep in mind that whatever you change in the rootfs will be overwritten if you flash the UBports GSI image again, and you won't get new fixes from Erfan GSI by upgrading this way (because those fixes are not in software packages but in overlaid configs). You could always update erfan's config manually according to his rootfs builder updates, though.

Updates via this way may also overwrite some changes introduced in `ubports_firmware_mount_patcher.zip`. Of course, you could always re-flash that zip to get them back.

# Known Issues

1. Mobile network works but can sometimes be quirky. For example, it sometimes shows an empty signal bar even when you are connected to mobile network. If your mobile network does not work, try switching to 2G/3G mode and switching back to 4G mode.
2. Reboot / Power Off can take quite a while. Sometimes you will need to force-reboot by long-pressing power button.
3. If the rotation sensor does not work, make sure you have restored the stock `modem` partition.
