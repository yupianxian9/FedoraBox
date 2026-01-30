在Linux系统中，Chrome的桌面启动器（快捷方式）通常位于几个标准位置。为了让你能快速定位，我先用一个表格总结这些常见路径，然后再详细说明如何确认和使用它们。

| 路径                             | 说明                                    | 适用用户 |
| ------------------------------ | ------------------------------------- | ---- |
| `/usr/share/applications/`     | **最常见的系统级位置**。系统安装Chrome时自动创建，所有用户可见。 | 所有用户 |
| `~/.local/share/applications/` | **用户级目录**。如果只想为当前用户修改或创建启动器，可以放在这里。   | 当前用户 |

### 🔍 如何找到并确认启动器

你可以通过以下方式精准定位：

1. **使用文件管理器**：打开文件管理器，导航到上述路径（例如 `/usr/share/applications/`），然后寻找名为 `google-chrome.desktop`或类似名称的文件。

2. **使用终端命令**：打开终端，使用 `ls`命令进行搜索，这非常高效。
   
   ```
   # 搜索系统级的启动器
   ls /usr/share/applications/ | grep -i chrome
   ```

3. **识别正确的启动器**：一个典型的 `.desktop`文件内容如下，其中 `Exec`行指明了Chrome可执行文件的实际路径，这是关键信息。
   
   ```
   [Desktop Entry]
   Version=1.0
   Type=Application
   Name=Google Chrome
   Exec=/usr/bin/google-chrome-stable %U
   Icon=google-chrome
   Categories=Network;WebBrowser;
   ```
   
   从 `Exec`行你可以确认Chrome主程序的安装路径，通常是 `/usr/bin/google-chrome-stable`或 `/opt/google/chrome/google-chrome`。

### ⚙️ 启动器的常见用途

找到启动器后，你通常可以做两件事：

- **修改启动参数**：这是最常见的需求。例如，为了让Chrome在root用户下也能正常运行，或者用于自动化测试，需要禁用沙盒模式。
  
  1. 使用文本编辑器（如 `gedit`或 `nano`）以管理员权限打开 `.desktop`文件。

```
sudo gedit /usr/share/applications/google-chrome.desktop
```

1. 找到以 `Exec=`开头的行，在命令末尾添加所需的参数。例如，添加 `--no-sandbox`和 `--disable-background-networking`：

```
# 修改前
Exec=/usr/bin/google-chrome-stable %U
# 修改后
Exec=/usr/bin/google-chrome-stable %U --no-sandbox --disable-background-networking
```

  **注意**：修改系统级的启动器（在 `/usr/share/applications/`下）需要管理员权限。修改前最好备份原文件。


