# Turn On/Off Bluetooth Stack

## Turn On Bluetooth

1. Start Bluetooth daemon:

```bash
/libexec/bluetooth/bluetoothd &
```

2. Reset HCI interface:

```bash
hciconfig hci0 down
hciconfig hci0 up
```

3. Power on the Bluetooth adapter:

```bash
dbus-send --system --print-reply \
    --dest=org.bluez \
    /org/bluez/hci0 \
    org.freedesktop.DBus.Properties.Set \
    string:org.bluez.Adapter1 \
    string:Powered \
    variant:boolean:true
```

## Turn Off Bluetooth

1. Power off the adapter:

```bash
dbus-send --system --print-reply \
    --dest=org.bluez \
    /org/bluez/hci0 \
    org.freedesktop.DBus.Properties.Set \
    string:org.bluez.Adapter1 \
    string:Powered \
    variant:boolean:false
```

2. Stop Bluetooth daemon:

```bash
killall bluetoothd
```
