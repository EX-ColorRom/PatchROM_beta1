PatchROM_beta1
==============

## Usage

Rename the available OTA or full package as update.zip, and put it under /device.

Then into this patchrom project root directory,  execute: 
```
. build/envsetup.sh
```
Now build your patch project

```
cd device; make firstpatch
```

Then handle the reject smali codes under the dir device/temp/reject. If the size of smali/framework.jar.out is too big, that might cause repackage failed, separate it into two jar files.

When complete and want to make a ColorRom package, do 

```
make fullota
```

Finally, a new zip file named "color-update.zip" will be generated, which can use recovery mode to flash the device.

## NOTICE
1. modify the boot.img if necessary
2. if the original update.zip has two framework jar files， then need to rewrite /device/makefile
                ORGIN_SECOND_FRAMEWORK_NAME：fill the  secondary-framework.jar's file name
                COLOR_FRAMEWORK_JARS： add the secondary-framework.jar's file name behind
3. when separation for framework.jar as the STEP 4 says， make a new folder named as xx.jar.out
4. "device/custom-update": is the final folder to be packaged，add or delete things like /system/app or something else
5.  turn odex to jar， use "deodex.sh update.zip" ,  or " deodex.sh -a 17 update.zip"
PatchRom for Ex-ColorRom
