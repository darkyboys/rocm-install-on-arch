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
After installation make sure to lock the ROCM Packages.
You can execute this command directly to do that
```bash
sudo sh -c 'cat >> /etc/pacman.conf <<EOF

# Lock ROCm packages
IgnorePkg = rocm-core rocm-hip-runtime rocm-hip-sdk rocm-device-libs rocminfo
EOF'
```
