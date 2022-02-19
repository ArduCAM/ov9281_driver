# Build the kernel driver on the Raspberry Pi

### Download the kernel source code
```Bash
cd ~
sudo apt update && sudo apt install git bc bison flex libssl-dev
sudo wget https://raw.githubusercontent.com/RPi-Distro/rpi-source/master/rpi-source -O /usr/local/bin/rpi-source && sudo chmod +x /usr/local/bin/rpi-source && /usr/local/bin/rpi-source -q --tag-update
mkdir $(uname -r)
rpi-source -d $(uname -r)
```

### Build ov9281.ko and install ov9281

```Bash
cd ov9281_driver
make clean && make 
sudo cp ov9281.ko /lib/modules/$(uname -r)/kernel/drivers/media/i2c
sudo depmod
sudo modprobe ov9281
```
