# Bluetooth Control Investigations

This section documents the technical investigation for Bluetooth control on different Kobo device
types.

## Devices

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
