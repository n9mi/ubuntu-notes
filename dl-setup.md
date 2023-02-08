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
sudo apt-get -y install cuda-toolkit-11-8
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

### Conda installation
Please download from the official source and
```
sudo chmod 755 <conda_installer>
```

Add conda to path
```
sudo mousepad ~/.bashrc

export PATH=~/anaconda3/bin:$PATH

source ~/.bashrc
```

Check the installation. You may change to new terminal to see the differences.
```
conda --version
```

### Create conda env
```
conda create -n new_env
```

### If above command doesn't work, please try
```
source ~/anaconda3/etc/profile.d/conda.sh
```
Then recreate it

### Activate env
```
conda activate new_env
```

### Deactivate env
```
conda deactivate new_env
```

### Turn off the default (base) in terminal
```
conda config --set auto_activate_base False
```
Then restart the terminal.

### Installing pytorch via Pip
```
sudo apt-get install -y python3-venv
python -m venv torch_gpu
source torch_gpu/bin/activate
pip3 install torch torchvision torchaudio
```

### Check the installed pytorch
```
python3
>>> import torch
>>> torch.cuda.is_available() // will print ex: True
>>> torch.cuda.get_device_name(0) // will print ex: 'NVIDIA GeForce GTX 950M'
```

### Error related libcudnn.8
```
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-ubuntu2004.pin
sudo mv cuda-ubuntu2204.pin /etc/apt/preferences.d/cuda-repository-pin-600
sudo apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/3bf863cc.pub
sudo add-apt-repository "deb https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64/ /"
sudo apt-get update
sudo apt-get install libcudnn8
sudo apt-get install libcudnn8-dev
```
