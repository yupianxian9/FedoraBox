# Fedora软件安装

## 0. 软件安装方式

### 0.1 dnf包管理器安装

以VSCode举例。

在线仓库安装：

```bash
# 步骤 1：导入微软官方 GPG 密钥
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# 步骤 2：添加 VS Code 官方仓库配置
sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'

# 步骤 3：安装 VS Code 稳定版
sudo dnf install code
```

离线安装包安装：

```bash
# 下载好rpm安装包
sudo dnf install ~/下载/code-*.x86_64.rpm
```

dnf 卸载软件

```bash
# 1先搜索确定软件包名
# 查RPM/DNF安装的WPS
rpm -qa | grep -i wps

# 2.卸载软件，-y表示自动确认
sudo dnf remove 包名1 包名2

# 3.自动清理卸载后的无用依赖，-y表示自动确认
sudo dnf autoremove -y
```

## 0.2 Flathub 应用商店安装

[Flathub - 适用于 Linux 的应用](https://flathub.org/zh-Hans)

先配置镜像源

```bash
# 配置flathub仓库
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo

# 修改镜像源(中科大)
sudo flatpak remote-modify flathub --url=https://mirrors.ustc.edu.cn/flathub

# 恢复默认源（如需）
sudo flatpak remote-modify flathub --url=https://dl.flathub.org/repo
```

安装方法：去官网搜索软件，找到软件包的下载命令。

备注：建议命令行下载，快一点。

例子：

```bash
flatpak install flathub org.localsend.localsend_app
```

flathub应用卸载：

```bash
# 基础列出所有已装 Flatpak 应用
flatpak list

# 仅筛选 Flathub 源的已装应用（推荐，无冗余）
flatpak list | grep -i flathub

# 常规卸载（保留用户数据，如软件配置 / 缓存）
flatpak uninstall cn.wps.Office

# 彻底卸载（删除所有用户数据，推荐，无残留）

flatpak uninstall --delete-data cn.wps.Office
```

## 0.3 锁定软件版本

```bash
# 1先搜索确定软件包名
rpm -qa | grep -i chrome

sudo dnf install 'dnf-command(versionlock)'

sudo dnf versionlock add chrome
```

## 1. 日常软件安装

## 1.1 WPS Office

描述：## WPS 365 Suite

```bash
flatpak install flathub cn.wps.wps_365
```

## 1.2 mpv

描述：音视频播放器

```
sudo dnf install mpv
```

## 2. 编程相关软件安装

## 2.1 VS Code

描述：Visual Studio Code 是一款全新的工具，既保留了代码编辑器的简洁特性，又集成了开发者完成编辑、构建、调试核心开发流程所需的全部功能。

```bash
# 步骤 1：导入微软官方 GPG 密钥
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# 步骤 2：添加 VS Code 官方仓库配置
sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'

# 步骤 3：安装 VS Code 稳定版
sudo dnf install code
```

## 2.2 MarkText

描述：MarkText 是一款**免费开源**的实时预览型 Markdown 编辑器，兼容 CommonMark 规范与 GitHub 风格 Markdown 规范（GFM）。它是一款简洁的文本编辑器，专为提升你的写作效率而生。

```bash
flatpak install flathub com.github.marktext.marktext
```

## 3. 工具类应用安装

### 3.1 Flatseal

描述：Flatseal 是一款图形化工具，可用来查看和修改 Flatpak 应用的权限。

```bash
flatpak install flathub com.github.tchx84.Flatseal
```

## 3.2 localsend

描述：文件传输

```bash
flatpak install flathub org.localsend.localsend_app
```
## 3.3 unrar

描述：rar压缩包解压工具

```bash
sudo dnf install unrar
```

基本用法：

```
# 解压到当前目录，x表示交互
unrar x archive.rar

# 解压到指定目录
unrar x archive.rar -d /home/user/backup/
```
