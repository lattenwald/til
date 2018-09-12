# UDEV

## Информация об устройстве

    $ lsusb
    Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
    Bus 001 Device 003: ID 0cf3:e300 Qualcomm Atheros Communications
    Bus 001 Device 009: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
    Bus 001 Device 004: ID 1bcf:2b95 Sunplus Innovation Technology Inc.
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

    $ udevadm info -q path -n /dev/bus/usb/001/009
    /devices/pci0000:00/0000:00:14.0/usb1/1-2

    $ udevadm info -a -p $(udevadm info -q path -n /dev/bus/usb/001/009) | less

    Udevadm info starts with the device specified by the devpath and then
    walks up the chain of parent devices. It prints for every device
    found, all possible attributes in the udev rules key format.
    A rule to match, can be composed by the attributes of the device
    and the attributes from one single parent device.

      looking at device '/devices/pci0000:00/0000:00:14.0/usb1/1-2':
        KERNEL=="1-2"
        SUBSYSTEM=="usb"
        ...
        ATTR{idProduct}=="c408"
        ATTR{idVendor}=="046d"
