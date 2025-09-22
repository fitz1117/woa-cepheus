<img align="right" src="https://github.com/n00b69/woa-cepheus/blob/main/cepheus.png" width="350" alt="Windows 11 running on a Xiaomi Mi 9">

# Running Windows on the Xiaomi Mi 9

## Dualboot guide (DualbootKernelPatcher)
> There are two methods listed below, the first one requires root, the second one does not. Use whichever method suits you the most, as they both do the same.

### Prerequisites (method 1: root required)
- [WOA Helper app](https://github.com/n00b69/woa-helper/releases/tag/APK)

### Setup - Android
- Download and install the **WOA Helper** app, then open it and grant it root access.
- Open **WOA Toolbox**, then press the **DUALBOOT KERNEL PATCHER** button.
- Wait for it to finish, then reboot your device.

#### Booting into Windows 
- Press and hold the **assistant button** and reboot (or turn on) your device.

#### Booting into Android
- Reboot (or turn on) your device while not holding or pressing the **assistant button**.

## Finished!


### Prerequisites (method 2: no root required)
- [Modified recovery](https://github.com/n00b69/woa-cepheus/releases/tag/Recovery)

- [Magiskboot](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/1.0/magiskboot.exe)

- [DualBoot Kernel Patcher](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/1.0/DualBootKernelPatcher.zip)

- [cepheus.fd file](https://github.com/n00b69/woa-everything/releases/download/Files/cepheus.fd)

### Opening CMD as an admin
> Open CMD as an **administrator**, then run the below command, replacing `path\to\platform-tools` with the actual path to the platform-tools folder, for example **C:\platform-tools**.
>
> Do not close this window. You will need to use it throughout this entire guide.
```cmd
cd path\to\platform-tools
```

### Boot the modded recovery
> While in fastboot mode, replace `path\to\recovery.img` with the actual path of the recovery image
```cmd
fastboot boot path\to\recovery.img
```

#### Back up your boot image
> This will back up your boot image in the current directory (for example `C:\platform-tools`).
```cmd
adb pull /dev/block/by-name/boot boot.img
```

#### Setting up required files
- Download **magiskboot.exe** and move it into the `platform-tools` folder.
- Download **DualBootKernelPatcher.zip** and extract the **DualBootKernelPatcher** folder into the `platform-tools` folder.
- Download **cepheus.fd** and move it into the `platform-tools` folder.

### Unpacking your boot image
> Make sure **boot.img** is in the `platform-tools` folder.
```cmd
magiskboot unpack boot.img
```

### Patching your boot image
```cmd
DualBootKernelPatcher\bin\Windows\DualBootKernelPatcher-x86_64.exe kernel cepheus.fd output DualBootKernelPatcher\Config\DualBoot.Sm8150.cfg DualBootKernelPatcher\ShellCode\ShellCode.Cepheus.bin
```

### Renaming the kernel file
- Delete or rename the **kernel** file in the `platform-tools` folder, then rename the **output** file to `kernel`

### Repacking your boot image
> This will repack your patched boot image into a new file called **new_boot.img**
```cmd
magiskboot repack boot.img
```

### Reboot to fastboot
```cmd
adb reboot bootloader
```

### Flashing the patched boot image
> Replace `path\to\new_boot.img` with the actual path of the image
```cmd
fastboot flash boot path\to\new_boot.img
```

#### Reboot your device
```cmd
fastboot reboot
```

#### Booting into Windows 
- Press and hold the **assistant button** and reboot (or turn on) your device.

#### Booting into Android
- Reboot (or turn on) your device while not holding or pressing the **assistant button**.

## Finished!

















