# Linux kernel - VisionCam XM / VisionSensor PV

This is the Linux Kernel for the [IMAGO](https://www.imago-technologies.com) VisionCam XM and VisionSensor PV.

The VisionCam and the VisionSensor combine both camera and a processor to a freely programmable vision system.

## Key features VisionCam XM
* Processor: TI AM572x, 2x ARM Cortex-A15 1.5 GHz
* 1 GB DDR3 RAM
* CMOS sensors up to 5 MPixels, global shutter
* Line scan sensors up to 8k pixels
* Integrated LED ring light and strobe controller
* Opto-isolated I/Os
* "Real-Time Communication Controller": Controlls I/Os in real-time, operates independently from processor and OS
* Easy-to-use high-level API for C++
* Ethernet 1000BASE-T
* µSD card
* RS-232 interface
* IP65 version available

## Key features VisionSensor PV
* Processor: TI AM437x, 2x ARM Cortex-A9 1.0 GHz
* 512 MB RAM
* CMOS sensor 752 x 480, global shutter
* Ethernet 100BASE-TX
* µSD card
* RS-232 interface
* Digital I/Os
* Integrated LEDs
* Easy-to-use high-level API for C++

## Build instructions

### Setup cross-toolchain
    wget https://releases.linaro.org/components/toolchain/binaries/6.2-2016.11/arm-linux-gnueabihf/gcc-linaro-6.2.1-2016.11-x86_64_arm-linux-gnueabihf.tar.xz
    tar -Jxvf gcc-linaro-6.2.1-2016.11-x86_64_arm-linux-gnueabihf.tar.xz -C $HOME
    export PATH=$HOME/gcc-linaro-6.2.1-2016.11-x86_64_arm-linux-gnueabihf/bin:$PATH
    export ARCH=arm
    export CROSS_COMPILE=arm-linux-gnueabihf-

### Clone kernel source tree
    git clone https://github.com/RalfGoebel/linux-visioncam.git
    cd visioncam-linux

### Build the kernel
    make visioncam-xm_defconfig # or visionsensor-pv_defconfig for the VisionSensor
    make -j4

### Build Debian packages
    export DEBEMAIL="...@..."
    export DEBFULLNAME="..."
    export LOCALVERSION=-x.x.x.x
    make -j4 deb-pkg
