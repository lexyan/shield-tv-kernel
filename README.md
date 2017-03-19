This repo shows a stripped down version of the official nvidia shield tv open source package
(ref: https://developer.nvidia.com/shield-open-source) which still allows building a bootimage 
(=KERNEL+initial ramdisk) for Experience 5.0.2/5.1 

It's based on work from nopnop9090  https://bitbucket.org/nopnop9090/shieldtv-kernel/overview

```diff
-Flash at your own risk!
-Not responsible for any damage you may do by attempting to modify stock software!

+Succesfully tested on my Shield[2015] 16gb
```

### How to compile ? ###
```
#!bash

cd shield-tv_kernel
export TOP=`pwd`
cd vendor/nvidia/licensed-binaries
./extract-nv-bins.sh
cd $TOP
. build/envsetup.sh 
setpaths
lunch foster_e-userdebug # (use "lunch foster_e_hdd-userdebug" if you got the shield tv pro)
mp bootimage -j9 # (change j9 to j<number-of-cpu-cores+1> for optimal build speed)

``` 

### How to test ? ###


```
# restart Shield in bootloader mode
adb reboot bootloader

# boot on the kernel
fastboot boot boot.img

# Shield reboot automatically on the new kernel, if you reboot the shield the old kernel boot
```

### How to flash ? ###

Once you're sure all is working, you can flash the kernel you compile 

```
# restart Shield in bootloader mode
adb reboot bootloader

# flash the kernel
fastboot flash boot boot.img
fastboot reboot
```

### Anything else? ###
Check the official thread on XDA-dev for more information http://forum.xda-developers.com/shield-tv/general/dvb-c-t-t2-s-pvr-running-tvheadend-t3303424

