android_kernel_lge_x5_zv5
=========================
From the README.txt included in the source package:

1. Android build
  - Download original android source code ( kitkat 4.4.2 ) from http://source.android.com
  - Untar opensource packages of LS740_andoid_KK.tar.gz* into downloaded android source directory
    a) cat LS740_andoid_KK.tar.gz* | tar -xzvf -
  - And, merge the source into the android source code
  - Run following scripts to build android
    a) source build/envsetup.sh
    b) choosecombo 1 generic user
    c) make -j4
  - When you compile the android source code, you have to add google original prebuilt source(toolchain) into the android directory.
  - After build, you can find output at out/target/product/generic

2. Kernel Build  
  - Uncompress using following command at the android directory
        tar xvzf LS740_KK_kernel.tar.gz  
  - When you compile the kernel source code, you have to add google original prebuilt source(toolchain) into the android directory.
  - Run following scripts to build kernel
  - 
    1) cd kernel

    2) mkdir -p out
    3) export ARCH=arm
    4) export TARGET_PRODUCT=x5_spr_us
    5) export DTS_TARGET=msm8226-x5_spr_us
    6) export PATH=$PATH:tools/lz4demo
    7) export CROSS_COMPILE=$(pwd)/../prebuilts/gcc/linux-x86/arm/arm-eabi-4.6/bin/arm-eabi-
    8) make O=./out ARCH=arm x5_spr_us_defconfig
    9) make O=./out -j4
        * "-j4" : The number, 4, is the number of multiple jobs to be invoked simultaneously. 
        * lz4demo : lz4demo is included in kernel/tools/lz4demo(change mode for excuting, chmod 777 lz4demo).
    		More information can be found at "https://code.google.com/p/lz4/"
  - After build, you can find the build image(zImage) at out/arch/arm/boot

3. how  to build chromium_lge (vendor\lge\external\chromium_lge),
   please refer to Buildme.txt at the folder mentioned above.
