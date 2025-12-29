# Connected Device Information

When connected, the Kobo Remote appears as:

```
Device Path: /dev/input/event5
Device Name: "Kobo Remote"
Bus Type: 0005 (Bluetooth HID)
Handlers: kbd event5
```

### Verification Commands

Check input devices:

```bash
# List all input devices
ls -la /dev/input/event*

# Check device information
cat /proc/bus/input/devices | grep -A5 -B5 "Kobo Remote"

# Get device name
cat /sys/class/input/event5/device/name
```

## Symlink Structure

The device symlink reveals it's a Bluetooth device:

```bash
$ ls -la /sys/class/input/event5
lrwxrwxrwx 1 root root 0 Dec 17 11:38 /sys/class/input/event5 ->
../../devices/virtual/misc/uhid/0005:000D:0000.0019/input/input29/event5
```

The presence of `uhid` in the path identifies it as a Bluetooth HID device.

## Input Event Monitoring

Monitor key presses from the device:

```bash
# Show raw input events
hexdump -C /dev/input/event5

# Example output for button presses:
# 00000000  a3 86 42 69 ce b7 05 00  04 00 04 00 51 00 07 00  |..Bi........Q...|
# 00000010  a3 86 42 69 ce b7 05 00  01 00 6c 00 01 00 00 00  |..Bi......l.....|
```

## Key Code Mapping

Common key codes from Kobo Remote:

- `0x6c` (108) = `KEY_RIGHT` - Right button
- `0x67` (103) = `KEY_UP` - Up button
- Other buttons map to standard Linux input key codes

This allows button remapping and isolated input handling separate from the device's built-in
controls.
