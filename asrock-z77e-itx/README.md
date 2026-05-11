# Linux configuration for ASRock Z77E

Fairly random configuration for my semi-retired server setup.

* Filesystems: ext4, btrfs and VFAT.
* Graphics: Only `i915` is built.
* Ethernet: Via `tg3` driver for the Broadcom Inc. and subsidiaries NetLink BCM57781 Gigabit Ethernet PCIe [14e4:16b1]
* Latest Intel microcode. Note that `CONFIG_EXTRA_FIRMWARE="intel-ucode/06-3a-09"`

Your mileage may vary.

## Links

* ASRock Support: [ASRock Z77E-ITX](https://www.asrock.com/mb/Intel/Z77E-ITX/)
