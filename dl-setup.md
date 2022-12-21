### Prerequisites
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

###  Install CUDNN
Please download the local installers from https://developer.nvidia.com/rdp/cudnn-download. They may ask you to make Nvidia developer account and accept the agreement license before downloading, but it's completely free. 
![image](https://user-images.githubusercontent.com/113373725/209017145-8d667e13-aad8-468a-b1f2-f12bf3d8b37f.png)

```
sudo cp /var/cudnn-local-repo-ubuntu2204-8.7.0.84/cudnn-local-BF23AD8A-keyring.gpg /usr/share/keyrings/
sudo dpkg -i cudnn-local-repo-ubuntu2204-8.7.0.84_1.0-1_amd64.deb
```
And wait until the installation is finished.

### Verify the cudNN installation
```
sudo apt search cudnn | grep installed
```
