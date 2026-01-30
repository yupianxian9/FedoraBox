# [Fedora配置Rime中州韵输入法](https://www.cnblogs.com/bearpipy/p/18364767 "发布于 2024-08-17 18:08")

在`Linux`系统上安装`Rime`输入法，常见的有两种底层框架：`ibus`和`fcitx`。

# 选择ibus

在Fedora系统中，默认安装了`ibus`，因此只需要再配置`ibus-rime`：

```bash
sudo dnf install ibus-rime
```

## 配置ibus

编辑`/etc/profile`（影响所有用户，需要`sudo`权限）或者`~/.xprofile`（仅影响当前用户）【如果使用`bash`作为默认`shell`，还可以编辑`~/.bash_profile`】，在文件新增：

```bash
export XMODIFIERS=@im=ibusexport GTK_IM_MODULE=ibusexport QT_IM_MODULE=ibus
```

## 配置ibus-rime

系统**设置-键盘-输入源-添加输入源-汉语(中国)-中文(Rime)**，将`Rime`输入法添加到输入源中。

# 选择fcitx

## 安装fcitx5

```bash
sudo dnf install fcitx5 fcitx5-chinese-addons
```

很多教程上让安装`fcitx5-gtk`和`fcitx5-qt`，但是目前`dnf`在安装`fcitx5`时会自动安装这两个包。

## 安装fcitx5-rime

```bash
sudo dnf install fcitx5-rime
```

## 配置fcitx5

编辑`/etc/profile`（影响所有用户，需要`sudo`权限）或者`~/.xprofile`（仅影响当前用户）【如果使用`bash`作为默认`shell`，还可以编辑`~/.bash_profile`】，在文件新增：

```bash
export XMODIFIERS=@im=fcitx5export GTK_IM_MODULE=fcitx5export QT_IM_MODULE=fcitx5
```

## 配置fcitx5-rime

打开`fcitx5`配置或者执行`fcitx5-configtool`，从左侧删除“拼音”方案，并将右侧的“rime”（或者是“中州韵”）方案添加到左侧。

# 导入Rime拼音方案

- 如果选择了`ibus`，那么配置文件夹为`~/.config/ibus/rime/`
- 如果选择了`fcitx`，那么配置文件夹为`~/.local/share/fcitx5/rime/`

> 建议先备份原配置文件再导入。

选择并执行下列三种方案中的一种（其他拼音方案请独自查询并clone）【请注意最后的**点`.`**】。

> 下载结束后`rime`文件夹下**直接**就是配置文件，没有其他的任何中间的文件夹。

## 雾凇拼音

```bash
git clone https://github.com/iDvel/rime-ice.git .
```

## 薄荷拼音

```bash
git clone https://github.com/Mintimate/oh-my-rime.git .
```

## 四叶草拼音

```bash
git clone https://github.com/fkxxyz/rime-cloverpinyin.git .
```

# 重启或注销系统

配置完成后重启系统即可使用。

# 使用异常

## ibus输入框位置偏移

在使用过程中，出现`ibus`输入法的输入框严重偏移的问题，目前解决方案未知，但是，修改`/etc/profile`为：

```bash
export XMODIFIERS=@im=ibusexport GTK_IM_MODULE=fcitxexport QT_IM_MODULE=fcitx
```

可以**部分**解决偏移的问题。

> 如果修改`XMODIFIERS=@im=fcitx`，可能会导致部分软件无法输入中文。

## fcitx5中文输入框闪烁

这是`Gnome`桌面下的bug，目前没有有效解决方案。

文章来源：https://www.cnblogs.com/bearpipy/p/18364767

©# [皮皮罴](https://www.cnblogs.com/bearpipy)
