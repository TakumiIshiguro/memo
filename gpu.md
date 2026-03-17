# GPU Setup Memo (Ubuntu)

## 1. NVIDIA Driver

### Ubuntu 20.04

```bash
ubuntu-drivers devices
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install nvidia-driver-<>
```

### Ubuntu 22.04

```bash
ubuntu-drivers list
sudo ubuntu-drivers install nvidia:<>
```

## 2. CUDA Toolkit
https://developer.nvidia.com/cuda-12-1-0-download-archive?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu
```bash
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-keyring_1.1-1_all.deb
sudo dpkg -i cuda-keyring_1.1-1_all.deb
sudo apt-get update
sudo apt-get -y install cuda-toolkit-<>
```

### PATH設定

```bash
echo 'export PATH=/usr/local/cuda/bin:$PATH' >> ~/.bashrc
echo 'export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH' >> ~/.bashrc
source ~/.bashrc
```

### CUDA確認

```bash
nvcc -V
```

## 3. GPU使用状況確認

```bash
watch -n 0.5 nvidia-smi
```

## 4. PyTorch + CUDA確認

```python
python3
>>> import torch
>>> torch.__version__
>>> torch.version.cuda
>>> torch.cuda.is_available()
>>> torch.cuda.current_device()
```

## 5. メモ

- `<>` は環境に合わせてバージョン番号に置き換える
- ドライバ更新後は再起動してから確認すると確実
