# Bluetooth Device Operations

## Device Discovery

### Start Discovery

```bash
dbus-send --system --print-reply \
    --dest=org.bluez \
    /org/bluez/hci0 \
    org.bluez.Adapter1.StartDiscovery
```

### Stop Discovery

```bash
dbus-send --system --print-reply \
    --dest=org.bluez \
    /org/bluez/hci0 \
    org.bluez.Adapter1.StopDiscovery
```

### List Discovered Devices

```bash
dbus-send --system --print-reply \
    --dest=org.bluez \
    / \
    org.freedesktop.DBus.ObjectManager.GetManagedObjects
```

## Connecting and Disconnecting

### Connect to Device

Connect to a paired device (example with Kobo Remote):

```bash
dbus-send --system --print-reply \
    --dest=org.bluez \
    /org/bluez/hci0/dev_A4_3C_D7_6D_0D_3B \
    org.bluez.Device1.Connect
```

### Disconnect Device

```bash
dbus-send --system --print-reply \
    --dest=org.bluez \
    /org/bluez/hci0/dev_A4_3C_D7_6D_0D_3B \
    org.bluez.Device1.Disconnect
```
