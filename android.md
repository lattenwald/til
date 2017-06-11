# Android

## Тонкости обновления ##

### [Secure Settings](https://play.google.com/store/apps/details?id=com.intangibleobject.securesettings.plugin) с Systemless root ###

    $ su
    # mount -o remount,rw /system
    # touch /system/xbin/su
    # mount -o remount,ro /system

После этих действий Secure Settings увидит рут.

### Обновление рутованых Самсунгов ###

[XDA-developers forum](https://forum.xda-developers.com/apps/supersu/2014-09-02-supersu-v2-05-t2868133/post70618589#post70618589)

>The only way I seem to reliably get both TWRP and SuperSU working right now is:
>
> * Flash TWRP (3.0.2-5) to recovery
> * Immediately boot into TWRP
> * If you were encrypted, format /data (ext4) and reboot into TWRP again
> * Flash SuperSU v2.79-SR3 in TWRP
> * Reboot into Android
>
>The first boot will take a while if you performed that format, but for me it ultimately completes. Note that your device will be running unencrypted at this point!
>
>Of course, if you format /data, you will lose all your data (including contents of internal storage!). Before I flashed the new version, I used FlashFire v0.54-PRE to create a backup of /data and internal storage to the removable sdcard, and restore that backup after flashing DPLT, rooting, and reinstalling FlashFire. This worked fine for me, and all my settings - including fingerprints and system settings - transferred fine. I came from the first Nougat beta, but I've seen others reporting success doing the same thing coming from Marshmallow. As always, your mileage may vary.
>
>Unfortunately, due to this boot-loop issue with DPLT and encrypted data, it is also impossible to use FlashFire to upgrade the firmware itself to DPLT while keeping root if you started with an encrypted device.
