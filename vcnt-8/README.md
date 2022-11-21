The Telstra VCNT-8 (Smart Modem Gen 3) uses the U-Boot bootloader (instead of the usual Technicolor bootloader), and uses ubifs filesystems rather than the normal jffs2.

The tar file contain 2 bank_dumps:
* bootfs: contains the bootable kernel
* rootfs: the normal firmware filesystem, which maybe ubifs, or ubifs within squashfs, depending upon the firmware version.

The matching bootfs and rootfs must be flashed together into bootfs1\rootfs1 or bootfs2\rootfs2 partitions as required.

Direct writes to the mtd device will not work. Partitions must be flashed using the `ubiupdatevol` command to the correct ubi device.

Partitions with ubifs filesystems *cannot* be updated when the partition is mounted.
