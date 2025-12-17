# Device Discovery

## Start Discovery

```bash
dbus-send --system --print-reply \
    --dest=org.bluez \
    /org/bluez/hci0 \
    org.bluez.Adapter1.StartDiscovery
```

## Stop Discovery

```bash
dbus-send --system --print-reply \
    --dest=org.bluez \
    /org/bluez/hci0 \
    org.bluez.Adapter1.StopDiscovery
```

## List Discovered Devices

```bash
dbus-send --system --print-reply \
    --dest=org.bluez \
    / \
    org.freedesktop.DBus.ObjectManager.GetManagedObjects | grep -B20 -A5 "Name"
```