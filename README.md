# Documentation

Documentation and releases of UBports for Tadiphone TP1803.

This port is based on the UBports GSI image by @erfanoabdi.

# Installation

1. Flash custom `abl` and `recovery` on your Tadiphone. If you want to use Anbox, make sure to flash the one provided in the [Releases](https://github.com/tadiphone-ubports/documentation/releases) page of this repository.
2. If you are coming from a ROM newer than Android Q, restore your `modem` partition to the stock one.
3. In bootloader, flash `halium-boot.img`, `dtbo.img` and `vendor.img` from the [Releases](https://github.com/tadiphone-ubports/documentation/releases) page of this repository.
4. Reboot into recovery, __FORMAT__ data.
5. Sideload `ubports_GSI_installer_XX.zip` (replace XX with the latest version) from <https://build.lolinet.com/file/halium/GSI/>
6. Sideload `ubports_firmware_mount_patcher.zip` from the [Releases](https://github.com/tadiphone-ubports/documentation/releases) page of this repository.
7. Reboot into system and enjoy.

# Update

Unfortunately there is no OTA update support for ubports GSI yet.

## Updating halium-boot.img and vendor.img

Just flash the two images in bootloader mode and reboot

## Updating UBports GSI

Download the new `ubports_GSI_installer_XX.zip`, sideload it and `ubports_firmware_mount_patcher.zip` again in recovery.

# Known Issues

1. Mobile network works but can sometimes be quirky. For example, it sometimes shows an empty signal bar even when you are connected to mobile network. If your mobile network does not work, try switching to 2G/3G mode and switching back to 4G mode.
2. Reboot / Power Off can take quite a while. Sometimes you will need to force-reboot by long-pressing power button.
3. If the rotation sensor does not work, make sure you have restored the stock `modem` partition.
