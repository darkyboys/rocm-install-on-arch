# rocm-install-on-arch
This repository shows the commands we can use to install rocm on arch linux.
Please open your terminal and paste these commands (Only for Arch Linux)
Commands:
```bash
sudo pacman -S \
rocm-core \
rocm-hip-runtime \
rocm-hip-sdk \
rocm-device-libs \
rocminfo
```

**Add the rocm path (if nore already)**
Add these to your `~/.bashrc` or any shell file you have after the packages are installed:
```bash
export LD_LIBRARY_PATH=/opt/rocm/lib:/opt/rocm/lib64:$LD_LIBRARY_PATH
# ROCm / HIP setup
export ROCM_PATH=/opt/rocm
export HIP_PATH=/opt/rocm
export HIP_PLATFORM=amd

export PATH=/opt/rocm/bin:$PATH
export PATH=/opt/rocm/llvm/bin:$PATH

export CC=/opt/rocm/llvm/bin/clang
export CXX=/opt/rocm/llvm/bin/clang++

```

## Select a default device (Recommended)
If you have multiple ROCm Devices and you want to use just one then run

```bash
rocminfo
```

And then carefully look for the device once you find it as (Agent X, eg: Agent 2)
Write down this in the `bachrc` or `zshrc` file

```
export HIP_VISIBLE_DEVICES=Index
```

example:

```bash
export HIP_VISIBLE_DEVICES=0
```

## Optional
After installation make sure to lock the ROCM Packages.
You can execute this command directly to do that
```bash
sudo sh -c 'cat >> /etc/pacman.conf <<EOF

# Lock ROCm packages
IgnorePkg = rocm-core rocm-hip-runtime rocm-hip-sdk rocm-device-libs rocminfo
EOF'
```
