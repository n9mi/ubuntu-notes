### Prerequities
```
sudo apt-get install build-essentials
```

### Add PPA GPU Drivers Repository to the System
```
sudo add-apt-repository ppa:graphics-drivers/ppa
```

### Identify GPU Model and Available Drivers
```
ubuntu-drivers devices // search for the 'recommended'
```

### Install Nvidia Driver
```
sudo apt install nvidia-driver-525 // or please install it on Additional Drivers
```

### Installing cuda toolkit by network
```
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-keyring_1.0-1_all.deb
sudo dpkg -i cuda-keyring_1.0-1_all.deb
sudo apt-get update
sudo apt-get -y install cuda
```
### Add to path
```
sudo mousepad ~/.bashrc
```

```
export PATH=$PATH:/usr/local/go/bin
export PATH=/usr/local/cuda/bin${PATH:+:${PATH}}$ 
export LD_LIBRARY_PATH=/usr/local/cuda/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
```

```
source ~/.bashrc
```

then reboot the machine.

### Verify the installation
```
nvidia-smi
nvcc -V
```
