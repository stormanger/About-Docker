# docs/文档

https://github.com/NVIDIA/nvidia-docker#quick-start

https://github.com/NVIDIA/nvidia-docker/wiki/Installation

https://docs.docker.com/engine/installation/linux/docker-ce/ubuntu/#install-using-the-repository

# Prerequisites/前提要求

GNU/Linux x86_64 with kernel version > 3.10
Docker >= 1.9 (official docker-engine, docker-ce or docker-ee only)
NVIDIA GPU with Architecture > Fermi (2.1)
NVIDIA drivers >= 340.29 with binary nvidia-modprobe

# install ubuntu 16.04.3 LTS/安装ubuntu 16.04.3



# install docker-ce in ubuntu/安装docker-ce

Prerequisites packages/安装依赖包

```
$ sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
```

Add Docker’s official GPG key:/加载docker官方GPG key

```
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

Set up the stable repository/设置稳定版本的库

```
$ sudo add-apt-repository \
  	 "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
  	 $(lsb_release -cs) \
 	 stable"
```

Install docker-ce/安装docker-ce

```
$ sudo apt-get update
$ sudo apt-get install docker-ce
```

Verify docker-ce/检查docker-ce

```
$ sudo docker run hello-world
```

# install nvidia drivers/安装nvidia驱动

Update the PCI hardware database/更新PCI硬件数据

```
$ sudo update-pciids
```

Disable nouveau and prepare for nvidia driver install/禁用nouveau驱动

```
$ sudo vim /etc/modprobe.d/blacklist.conf
blacklist nouveau
$ sudo update-initramfs -u && sudo reboot
```

Install nvidia driver with deb packge/使用apt方式安装驱动包

```
$ sudo apt-cache search nvidia |grep 375    ##check new driver(but not beta) to install
$ sudo apt-get install nvidia-modprobe
$ sudo apt-get install nvidia-375 
$ sudo reboot    ##need reboot to let nvidia driver work and can check with next command
$ nvidia-smi	##if it worked,will report all your CUDA-capable devices in the system/这条命令是用来检查驱动是否正常运行的
```

Fix error/问题处理，不过这部分可以跳过了

If error information like this:

​	/sbin/ldconfig.real: /usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link
​	/sbin/ldconfig.real: /usr/lib32/nvidia-375/libEGL.so.1 is not a symbolic link

```
$ sudo mv /usr/lib/nvidia-375/libEGL.so.1 /usr/lib/nvidia-375/libEGL.so.1.org
$ sudo mv /usr/lib32/nvidia-375/libEGL.so.1 /usr/lib32/nvidia-375/libEGL.so.1.org
$ sudo ln -s /usr/lib/nvidia-375/libEGL.so.375.39 /usr/lib/nvidia-375/libEGL.so.1
$ sudo ln -s /usr/lib32/nvidia-375/libEGL.so.375.39 /usr/lib32/nvidia-375/libEGL.so.1
```

# Install nvidia-docker/安装nvidia-docker

```
$ wget -P /tmp https://github.com/NVIDIA/nvidia-docker/releases/download/v1.0.1/nvidia-docker_1.0.1-1_amd64.deb
$ sudo dpkg -i /tmp/nvidia-docker*.deb
$ sudo reboot
```

Verify nvidia-docker/检查nvidia-docker

```
$ nvidia-docker run --rm nvidia/cuda nvidia-smi	#you can see like run nvidia-smi in ubuntu
```



You can run tensorflow-gpu now!
https://store.docker.com/community/images/tensorflow/tensorflow
