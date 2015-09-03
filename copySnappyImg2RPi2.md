# Snappy

## Install Snappy  

### Use Window + Ubuntu VM  
* Download SDFormatter, format SD card, with option ON.

* Without plugging usb,
use `df -h`

```
rkuo@maple:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        19G   13G  4.9G  72% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            727M  4.0K  727M   1% /dev
tmpfs           148M  904K  147M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            738M  160K  737M   1% /run/shm
none            100M   60K  100M   1% /run/user
rkuo@maple:~$
```  

With usb plugged in, in VirtualBox Terminal dropdown menu `Device`, select the new usb device.

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        19G   13G  4.9G  72% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            727M  4.0K  727M   1% /dev
tmpfs           148M  956K  147M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            738M  160K  737M   1% /run/shm
none            100M   60K  100M   1% /run/user
/dev/sdb1        30G   32K   30G   1% /media/rkuo/RPI2SNAPPY0    <<--
rkuo@maple:~$
```

find image,

```
rkuo@maple:~$ ls ~/Downloads/
2015-04-06-ubuntu-trusty.bmap
2015-04-06-ubuntu-trusty.img
2015-04-06-ubuntu-trusty.zip
dropbox_2015.02.12_amd64.deb
gedit-markdown-master
ubuntu-15.04-snappy-armhf-rpi2.img    <<--
ubuntu-15.04-snappy-armhf-rpi2.img.xz
ubuntu-mate-15.04-desktop-armhf-raspberry-pi-2.img
ubuntu-mate-15.04-desktop-armhf-raspberry-pi-2.img.bz2
ubuntu-mate-15.04-desktop-i386.iso
rkuo@maple:~$
```

umount/unmount (osx/linux) usb partition, `sdb1`, so we can copy to usb or SD, `sdb`.

```
rkuo@maple:~$ sudo umount /dev/sdb1
```

copy img to drive, not partition,
```
rkuo@maple:~$ sudo dd bs=4M if=~/Downloads/ubuntu-15.04-snappy-armhf-rpi2.img of=/dev/sdb
929+1 records in
929+1 records out
3900000000 bytes (3.9 GB) copied, 649.524 s, 6.0 MB/s
rkuo@maple:~$
```

or use

```
rkuo@maple:~$ sudo ddrescue -d -D --force ~/Downloads/ubuntu-15.04-snappy-armhf-rpi2.img /dev/sdb


GNU ddrescue 1.17
Press Ctrl-C to interrupt
rescued:   501874 kB,  errsize:       0 B,  current rate:    2949 kB/s
   ipos:   501874 kB,   errors:       0,    average rate:    3196 kB/s
   opos:   501874 kB,    time since last successful read:       0 s
Copying non-tried blocks...rkuo@maple:~$ sudo ddrescue -d -D --force ~/Downloads/ubuntu-15.04-snappy-armhf-rpi2.img /dev/sdb

```


`sudo sync` before eject SD card.
Uncheck usb Device in vm, disconnect in Window, then pull.

### Use Mac  
* Download [ApplePi Baker][5], and follow the on screen instructions.

## Install Docker  

```
(amd64)ubuntu@ubuntu-core-stable-4:~$ sudo snappy install docker
sudo: unable to resolve host ubuntu-core-stable-4
Installing docker
Starting download of docker
8.36 MB / 8.36 MB [======================================] 100.00 % 550.18 KB/s
Done
Name          Date       Version   Developer
ubuntu-core   2015-07-29 4         ubuntu
docker        2015-08-31 1.6.2.003 canonical
generic-amd64 2015-07-29 1.4       canonical
(amd64)ubuntu@ubuntu-core-stable-4:~$ docker info
Containers: 0
Images: 0
Storage Driver: aufs
 Root Dir: /var/lib/apps/docker/1.6.2.003/aufs
 Backing Filesystem: extfs
 Dirs: 0
 Dirperm1 Supported: true
Execution Driver: native-0.2
Kernel Version: 3.19.0-23-generic
Operating System: <unknown>
CPUs: 1
Total Memory: 993.1 MiB
Name: ubuntu-core-stable-4
ID: ZU7W:GNQR:3KOC:EI6C:NGXQ:2VE5:V5SR:KMJE:HEBQ:4IDA:AGDK:SKWI
WARNING: No swap limit support
(amd64)ubuntu@ubuntu-core-stable-4:~$
```

[References]:
[0]:https://developer.ubuntu.com/en/snappy/start/#snappy
[1]:https://www.raspberrypi.org/downloads/
[2]:https://www.raspberrypi.org/documentation/installation/installing-images/linux.md
[3]:http://elinux.org/RPi_Easy_SD_Card_Setup
[4]:https://ubuntu-mate.org/raspberry-pi/
[5]:http://www.tweaking4all.com/hardware/raspberry-pi/macosx-apple-pi-baker/
