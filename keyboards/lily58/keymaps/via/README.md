# Lily58 R2G Via

```shell
# 1. Put keeb into bootloader using reset (underside) + power

# 2. Get USB device ID
❯ sudo lsusb
Bus 010 Device 021: ...

# 3. Build (qmk repo); output goes to .build/
# @TODO using qmk_userspace_via repo
❯ ./util/docker_cmd.sh qmk compile -kb lily58/r2g -km via

# 4. Erase, flash, reset
❯ sudo dfu-programmer atmega32u4:10,21 erase --force
❯ sudo dfu-programmer atmega32u4:10,21 flash --force .build/lily58_r2g_via.hex
❯ sudo dfu-programmer atmega32u4:10,21 flash reset

# 5. Enjoy!
```
