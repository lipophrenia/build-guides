# NVIDIA DRIVERS+CUDA LINUX

You can follow [Official CUDA Linux Guide](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/).

I will describe my method:

### Adding APT repo

<summary>UBUNTU 24.04 NOBLE NUMBAT</summary>

```bash
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2404/x86_64/cuda-keyring_1.1-1_all.deb
sudo dpkg -i cuda-keyring_1.1-1_all.deb
```
<summary>UBUNTU 22.04 JAMMY JELLYFISH</summary>

```bash
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-keyring_1.1-1_all.deb
sudo dpkg -i cuda-keyring_1.1-1_all.deb
```

<summary>UBUNTU 20.04 FOCAL FOSSA</summary>

```bash
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64/cuda-keyring_1.1-1_all.deb
sudo dpkg -i cuda-keyring_1.1-1_all.deb
```

### Installation

Check CUDA compatibility of your GPU and select supported CUDA Toolkit version.

Install [required](https://docs.nvidia.com/cuda/cuda-toolkit-release-notes/index.html#id6) NVIDIA driver through `Additional Drivers`.
  
I used proprietary `nvidia-driver-550`, `cuda-toolkit-12-6` and `cudnn9` for it. 

```bash
sudo apt install cuda-toolkit-12-6
sudo apt install libcudnn9-static-cuda-12 libcudnn9-dev-cuda-12 libcudnn9-cuda-12 cudnn9-cuda-12-6

# for cuda-12-5 I had to install and keep older versions of packages due to dependency conflict:
# sudo apt install libcudnn9-static-cuda-12=9.2.1.18-1 libcudnn9-dev-cuda-12=9.2.1.18-1 libcudnn9-cuda-12=9.2.1.18-1 cudnn9-cuda-12-5
# sudo apt-mark hold cudnn9-cuda-12 libcudnn9-cuda-12 libcudnn9-dev-cuda-12 libcudnn9-static-cuda-12
```

Added lines to `.bashrc`.
```
export PATH=/usr/local/cuda-12.6/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda-12.6/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
export CUDA_HOME=/usr/local/cuda-12.6
```

Reload enviroment and verify installation.
```bash
source .bashrc
nvcc --version
```

# Video Codec SDK

### Download.

[Latest Version](https://developer.nvidia.com/nvidia-video-codec-sdk/download)

[Old Versions](https://developer.nvidia.com/video-codec-sdk-archive)

### Install.

```bash
unzip Video_Codec_SDK_12.2.72.zip
cd Video_Codec_SDK_12.2.72
cp -r ./Lib/linux/stubs /usr/local/cuda-12.6/lib64
cp -r ./Interface/* /usr/local/cuda-12.6/include
```
