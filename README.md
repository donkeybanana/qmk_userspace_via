# donkeybanana's (VIA) QMK Userspace Repository

## Compile

```shell
❯ docker run --rm -v "$HOME/src/github.com/qmk/qmk_firmware.git":/qmk_firmware -v "$PWD":/userspace -w /userspace \
  ghcr.io/qmk/qmk_cli:latest sh -c \
  'qmk config user.qmk_home=/qmk_firmware user.overlay_dir=/userspace >/dev/null && qmk compile -kb lily58/r2g -km via'
```

## Flash

```shell
# 1. Put keeb into bootloader using reset (underside) + power

# 2. Get USB device ID
❯ sudo lsusb
Bus 010 Device 021: ...

# 3. Compile (see above)

# 4. Erase, flash, reset
❯ sudo dfu-programmer atmega32u4:10,21 erase --force
❯ sudo dfu-programmer atmega32u4:10,21 flash --force lily58_r2g_via.hex
❯ sudo dfu-programmer atmega32u4:10,21 flash reset

# 5. Enjoy!
```
