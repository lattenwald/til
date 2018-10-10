# UDEV

## Источники

1. [ArchWiki](https://wiki.archlinux.org/index.php/udev)

## Информация об устройстве

### Поиск устройства

    $ lsusb
    Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
    Bus 001 Device 003: ID 0cf3:e300 Qualcomm Atheros Communications
    Bus 001 Device 009: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
    Bus 001 Device 004: ID 1bcf:2b95 Sunplus Innovation Technology Inc.
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

    $ udevadm info -q path -n /dev/bus/usb/001/009
    /devices/pci0000:00/0000:00:14.0/usb1/1-2

### Информация

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

### Тестирование правил

    $ udevadm test $(udevadm info -q path -n /dev/bus/usb/001/012) 2>&1 | less

    calling: test
    version 239
    Load module index
    Parsed configuration file /usr/lib/systemd/network/99-default.link
    Created link configuration context.
    Reading rules file: /usr/lib/udev/rules.d/10-dm.rules
    Reading rules file: /usr/lib/udev/rules.d/11-dm-lvm.rules
    ...
    rules contain 196608 bytes tokens (16384 * 12 bytes), 29148 bytes strings
    19890 strings (160491 bytes), 17296 de-duplicated (133938 bytes), 2595 trie nodes used
    ...
    MODE 0664 /usr/lib/udev/rules.d/50-udev-default.rules:45
    RUN '/usr/share/virtualbox/VBoxCreateUSBNode.sh $major $minor $attr{bDeviceClass} vboxusers' /usr/lib/udev/rules.d/60-vboxdrv.rules:6
    PROGRAM '/usr/lib/udev/mtp-probe /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1 1 12' /usr/lib/udev/rules.d/69-libmtp.rules:2465
    starting '/usr/lib/udev/mtp-probe /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1 1 12'
    '/usr/lib/udev/mtp-probe /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1 1 12'(out) '0'
    Process '/usr/lib/udev/mtp-probe /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1 1 12' succeeded.
    RUN '/usr/lib/udev/tlp-usb-udev %p' /usr/lib/udev/rules.d/85-tlp.rules:10
    MODE 0666 /usr/lib/udev/rules.d/99-gamesir-g4s.rules:5
    ...
    ACTION=add
    BUSNUM=001
    ...
    run: '/usr/share/virtualbox/VBoxCreateUSBNode.sh 189 11 00 vboxusers'
    run: '/usr/lib/udev/tlp-usb-udev /devices/pci0000:00/0000:00:14.0/usb1/1-1'
