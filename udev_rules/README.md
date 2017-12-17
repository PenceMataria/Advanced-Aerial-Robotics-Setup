# udev
###### Udev uses rules files that determine how it identifies devices and creates device names. The udev daemon ( udevd ) reads the rules files at system startup and stores the rules in memory.

#### How to find rule files
    cd /etc/udev/rules.d
#### How do they look 
   ###### type
    vim /etc/udev/rules.d/99-usb-serial.rules
   ###### this is it
    KERNEL=="1-2",SUBSYSTEMS=="usb",ATTRS{idProduct}=="0061",ATTRS{idVendor}=="04ca",SYMLINK+="optmouse"

#### How to write 
   ###### type 
    lsusb
   
    Bus 001 Device 007: ID 04ca:0061 Lite-On Technology Corp.
   ###### now we know device has been mounted 
    /dev/bus/usb/001/003
    #type
    udevadm info -a -p $(udevadm info -q path -n /dev/bus/usb/001/007
    #output
       Udevadm info starts with the device specified by the devpath and then
    walks up the chain of parent devices. It prints for every device
    found, all possible attributes in the udev rules key format.
    A rule to match, can be composed by the attributes of the device
    and the attributes from one single parent device.

      looking at device '/devices/pci0000:00/0000:00:14.0/usb1/1-2':
        KERNEL=="1-2"
        SUBSYSTEM=="usb"
        DRIVER=="usb"
        ATTR{authorized}=="1"
        ATTR{avoid_reset_quirk}=="0"
        ATTR{bConfigurationValue}=="1"
        ATTR{bDeviceClass}=="00"
        ATTR{bDeviceProtocol}=="00"
        ATTR{bDeviceSubClass}=="00"
        ATTR{bMaxPacketSize0}=="8"
        ATTR{bMaxPower}=="100mA"
        ATTR{bNumConfigurations}=="1"
        ATTR{bNumInterfaces}==" 1"
        ATTR{bcdDevice}=="0100"
        ATTR{bmAttributes}=="a0"
        ATTR{busnum}=="1"
        ATTR{configuration}==""
        ATTR{devnum}=="7"
        ATTR{devpath}=="2"
        ATTR{idProduct}=="0061"
        ATTR{idVendor}=="04ca"
        ATTR{ltm_capable}=="no"
        ATTR{manufacturer}=="PixArt"
        ATTR{maxchild}=="0"
        ATTR{product}=="USB Optical Mouse"
        ATTR{quirks}=="0x0"
        ATTR{removable}=="removable"
        ATTR{speed}=="1.5"
        ATTR{urbnum}=="15"
        ATTR{version}==" 2.00"
        
        #### Now you can write udev rules for every usb by using above output
        #### type
          ls /dev/
          #output
          acpi_thermal_rel  input               rtc0      tty27  tty59      ttyS31
          autofs            kfd                 sda       tty28  tty6       ttyS4
          block             kmsg                sda1      tty29  tty60      ttyS5
          bsg               kvm                 sda2      tty3   tty61      ttyS6
          btrfs-control     lightnvm            sda5      tty30  tty62      ttyS7
          bus               log                 sg0       tty31  tty63      ttyS8
          cdrom             loop0               sg1       tty32  tty7       ttyS9
          cdrw              loop1               shm       tty33  tty8       uhid
          char              loop2               snapshot  tty34  tty9       uinput
          console           loop3               snd       tty35  ttyprintk  urandom
          core              loop4               sr0       tty36  ttyS0      userio
          cpu               loop5               stderr    tty37  ttyS1      v4l
          cpu_dma_latency   loop6               stdin     tty38  ttyS10     vcs
          cuse              loop7               stdout    tty39  ttyS11     vcs1
          disk              loop-control        tty       tty4   ttyS12     vcs2
          dri               mapper              tty0      tty40  ttyS13     vcs3
          drm_dp_aux0       mcelog              tty1      tty41  ttyS14     vcs4
          dvd               media0              tty10     tty42  ttyS15     vcs5
          dvdrw             mei0                tty11     tty43  ttyS16     vcs6
          ecryptfs          mem                 tty12     tty44  ttyS17     vcsa
          extweb            memory_bandwidth    tty13     tty45  ttyS18     vcsa1
          fb0               mqueue              tty14     tty46  ttyS19     vcsa2
          fd                net                 tty15     tty47  ttyS2      vcsa3
          full              network_latency     tty16     tty48  ttyS20     vcsa4
          fuse              network_throughput  tty17     tty49  ttyS21     vcsa5
          hidraw0           null                tty18     tty5   ttyS22     vcsa6
          hpet              optmouse            tty19     tty50  ttyS23     vfio
          hugepages         port                tty2      tty51  ttyS24     vga_arbiter
          hwrng             ppp                 tty20     tty52  ttyS25     vhci
          i2c-0             psaux               tty21     tty53  ttyS26     vhost-net
          i2c-1             ptmx                tty22     tty54  ttyS27     video0
          i2c-2             pts                 tty23     tty55  ttyS28     zero
          i2c-3             random              tty24     tty56  ttyS29
          i2c-4             rfkill              tty25     tty57  ttyS3
          initctl           rtc                 tty26     tty58  ttyS30

Refrences :-</br>
https://docs.oracle.com/cd/E37670_01/E41138/html/ch07s03.html</br>
http://weininger.net/how-to-write-udev-rules-for-usb-devices.html
