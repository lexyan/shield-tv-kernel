# README #

This repo shows a stripped down version of the official nvidia shield tv open source package
(ref: https://developer.nvidia.com/shield-open-source) which still allows building a bootimage 
(=KERNEL+initial ramdisk) for Experience 5.0.2/5.1 

It's based on work from nopnop9090  https://bitbucket.org/nopnop9090/shieldtv-kernel/overview

### How to compile? ###
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

### Anything else? ###
Check the official thread on XDA-dev for more information http://forum.xda-developers.com/shield-tv/general/dvb-c-t-t2-s-pvr-running-tvheadend-t3303424
