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

Download archive:
https://developer.nvidia.com/cuda-12-1-0-download-archive?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu

```bash
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-keyring_1.1-1_all.deb
sudo dpkg -i cuda-keyring_1.1-1_all.deb
sudo apt-get update
sudo apt-get -y install cuda-toolkit-<>
```

### PATH / LD_LIBRARY_PATH

```bash
echo 'export PATH=/usr/local/cuda/bin:$PATH' >> ~/.bashrc
echo 'export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH' >> ~/.bashrc
source ~/.bashrc
```

### CUDA version check

```bash
nvcc -V
```

## 3. GPU usage check

```bash
watch -n 0.5 nvidia-smi
```

## 4. PyTorch + CUDA check

```bash
pip install torch==2.4.1 torchvision==0.19.1 torchaudio==2.4.1 --index-url https://download.pytorch.org/whl/cu121
```

```python
python3
>>> import torch
>>> torch.__version__
>>> torch.version.cuda
>>> torch.cuda.is_available()
>>> torch.cuda.current_device()
```

## 5. Uninstall NVIDIA Driver + CUDA

```bash
sudo apt --purge remove '*nvidia*' '*cuda*' 'nsight*'
sudo apt autoremove --purge
```

## 6. Uninstall PyTorch

```bash
python3 -m pip uninstall -y torch torchvision torchaudio
```

## 7. Notes

- `<>` は環境に合わせてバージョン番号に置き換える
- ドライバ更新後は、再起動してから確認すると確実
