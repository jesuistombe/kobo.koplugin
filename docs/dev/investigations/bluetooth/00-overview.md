# Bluetooth Control Investigations

This section documents the technical investigation and implementation details for Bluetooth control
on different Kobo device types.

## Device Support

### MTK Devices

- Uses MTK-specific Bluetooth implementation
- D-Bus service: `com.kobo.mtk.bluedroid`
- Custom command set and initialization sequence
- See [MTK Documentation](./mtk/00-overview.md)

### Non-MTK Devices (Libra 2, etc.)

- Uses standard Linux BlueZ stack
- D-Bus service: `org.bluez`
- Standard Bluetooth operations
- See [Libra 2 Documentation](./libra-2/00-overview.md)

## Architecture Overview

The plugin automatically detects the device type and uses the appropriate implementation:

1. **Device Detection**: Checks for MTK vs standard Bluetooth hardware
2. **Service Discovery**: Uses appropriate D-Bus service (`com.kobo.mtk.bluedroid` vs `org.bluez`)
3. **Command Adaptation**: Executes device-specific command sequences
4. **Input Handling**: Manages HID input devices consistently across platforms

## Common Features

Both implementations support:

- Bluetooth on/off control
- Device scanning and pairing
- Connection management
- Input device handling for remotes/keyboards
- Button remapping and key binding
- Auto-restoration after sleep/wake cycles

The plugin maintains full backwards compatibility while extending support to additional device
types.
