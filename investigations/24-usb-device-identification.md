# Investigation 24 – USB Device Identification

## Question

What was the name of the USB key inserted by Bob Smith?

## Investigation

I started by looking for USB-related activity across the BOTS v1 dataset to identify which logs contained information about removable devices.

```spl
index=botsv1 ("USB" OR "USBSTOR" OR "Removable")
| stats count by sourcetype
| sort - count
```

The results showed USB-related activity across several sourcetypes, including `winregistry`.

Since Windows stores information about previously connected USB storage devices in the registry, I focused the investigation on the registry events from Bob Smith's workstation, `we8105desk`.

I searched the USB-related registry paths and looked at the values stored in them.

```spl
index=botsv1 sourcetype=winregistry host="we8105desk"
| search key_path="*usb*"
| stats values(data) AS data by key_path
| search data!=""
```

This revealed a USB storage entry containing the value `MIRANDA_PRI`.

To confirm that this was the device's friendly name, I narrowed the search specifically to `USBSTOR` registry entries containing `FriendlyName`.

```spl
index=botsv1 sourcetype=winregistry host="we8105desk"
| search key_path="*usbstor*" key_path="*friendlyname*"
| table _time, key_path, data
| dedup data
```

The result showed:

`MIRANDA_PRI`

## Finding

The Windows registry evidence shows that the USB storage device connected to Bob Smith's workstation had the friendly name:

**MIRANDA_PRI**

## Answer

**MIRANDA_PRI**
