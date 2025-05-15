# nvidia driver

`ubuntu-drivers devices`

`sudo add-apt-repository ppa:graphics-drivers/ppa`

`sudo apt update`

`sudo apt install nvidia-driver-<>`



# cuda

https://developer.nvidia.com/cuda-12-1-0-download-archive?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu

`export PATH=/usr/local/cuda:/usr/local/cuda/bin:$PATH`
`export LD_LIBRARY_PATH=/usr/local/lib:/usr/local/cuda/lib64:$LD_LIBRARY_PATH`

`nvcc -V`

# nvdia-smi
`watch -n 0.5 nvidia-smi`


# PyTorch

`python3`

`torch.__version__`

`torch.version.cuda`

`torch.cuda.is_available()`

`torch.cuda.current_device()`
