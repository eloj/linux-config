# Linux configuration for MSI B450M Mortar (Titanium)

This is a fairly cut-down kernel configuration, tailored for this B450 AM4 board,
and _my_ system in particular.

It should work with most distributions, but definitely Debian, Ubuntu, Linux Mint.

* Configured to only support AMD CPUs, and build with `-march=native`.
* Filesystems: ext4, btrfs and VFAT + NTFS3. Also builds FUSE (req. for AppImages).
* Graphics: Only `amdgpu` is built. If you have an Intel dGPU you'll need to enable that (e.g xe2 or whatever).
* Ethernet: Via `r8169` driver for the Realtek RTL8111/8168/8211/8411 Controller [10ec:8168]
* SuperIO: Builds `NCT6775` driver for NCT6797 superIO chip, so sensors work... kinda. Fan speeds and main temps seem correct.
* USB: Contains additional configuration for Corsair and Logitech USB devices.
* Most CPU vulnerability mitigations are enabled, except Vmscape.
* Configured with `CONFIG_RD_ZSTD` and `CONFIG_MODULE_COMPRESS_ZSTD`, so zstd required.

As a result, compared to Ubuntu mainline:

* The kernel is ~8MiB (~50%) smaller,
* The initrd.img is ~44MiB (~50%) smaller,
* The system map file is ~7MiB (~70%) smaller, and
* The .config is less than half the size.

Your mileage may vary.

If you want to use docker, xen, advanced networking, etc you will probably have to add to the configuration.

## Building

Note: First run 'make oldconfig' to adapt the configuration to your setup and current kernel.

```bash
make -j4 bindeb-pkg LOCALVERSION=-yourname
```

## Extra info

Example `/etc/modules-load.d/msi-b450m-mortar.conf`:
```
# Seems to not autoload
snd_usb_audio
# Motherboard SuperIO Chip
nct6775
# Add /dev/ntsync for use with Proton
ntsync
```

## Links

* MSI Support: [B450M MORTAR](https://www.msi.com/Motherboard/B450M-MORTAR/support) ([TITANIUM](https://www.msi.com/Motherboard/B450M-MORTAR-TITANIUM/support))
