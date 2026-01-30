# Fedora系统相关优化配置

```
## 1. 视频编码问题解决
# RPM Fusion 仓库配置
sudo dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
sudo dnf install https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm

# Switch to full ffmpeg
sudo dnf swap ffmpeg-free ffmpeg --allowerasing

# Hardware codecs with AMD (mesa)
# AMD 显卡硬件编码开启，因为AMD适配问题需要单独搞
sudo dnf swap mesa-va-drivers mesa-va-drivers-freeworld
sudo dnf swap mesa-vdpau-drivers mesa-vdpau-drivers-freeworld
```

## 2. 电源优化配置（使用 TLP 延长笔记本电脑的电池续航时间）

```
sudo dnf install tlp -y
sudo systemctl enable tlp
```
