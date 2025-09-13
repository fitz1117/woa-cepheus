<img align="right" src="https://github.com/n00b69/woa-cepheus/blob/main/cepheus.png" width="350" alt="Windows 11 running on a Xiaomi Mi 9">

# Running Windows on the Xiaomi Mi 9

## Updating drivers

### Prerequisites
- [Modified TWRP](https://github.com/n00b69/woa-cepheus/releases/tag/Recovery) (should already be installed)

- [Drivers & UEFI](https://github.com/qaz6750/XiaoMi9-Drivers/releases/latest)

### Boot into TWRP
> If your recovery has been replaced by the stock recovery, flash it again using
```cmd
fastboot flash recovery path\to\moddedtwrp.img reboot recovery
```

#### Execute the msc script
> If it asks you to run it once again, do so
```cmd
adb shell msc
```

### Diskpart
```cmd
diskpart
```

#### Select the Windows volume of the phone
> Use `list volume` to find it, replace "$" with the actual number of **WINCEPHEUS**
```diskpart
select volume $
```

#### Assign the letter X
```diskpart
assign letter x
```

#### Exit diskpart
```diskpart
exit
```

### Installing drivers
> [!Note]
> This process will take +- 20 minutes. Do not worry, this is normal.

- Unpack the driver archive, then open the `OfflineUpdater.cmd` file (if an error shows up, run `OfflineUpdaterFix.cmd` instead)

> If it asks you to enter a letter, enter the drive letter of **WINCEPHEUS** (which should be **X**), then press enter

### Reboot your device
> Make sure to also change the UEFI image in Android, otherwise you may face a "blue screen of death" (BSoD) when booting Windows later.
```cmd
adb reboot
```

## Finished!
