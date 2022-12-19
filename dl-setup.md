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
sudo apt install nvidia-driver-525
```

### Verify the installation
```
nvidia-smi
```
