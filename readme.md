## How get the index.html file
cmd
```bash
# close the network
sudo ifconfig en0 down
# open the network
sudo ifconfig en0 up

# use pandoc
cd /Users/apple/Downloads/01
pandoc -s 02.tex -o 02.html --mathjax -c style.css --self-contained --toc
pandoc -s 02.tex -o 02.html --mathjax -c style.css --toc --embed-resources --standalone
cp ./02.html ../UnifiedFieldTheory/index.html

# split
pandoc -s 02.tex -o 02/02.html --mathjax -c style.css --toc --embed-resources --standalone --split-level=2
# Unknown option --split-level.
```

## mac如何通过shell断开网络连接
在 macOS 上，可以通过终端（Terminal）使用 shell 命令来断开网络连接。以下是一些方法：

### 1. **禁用 Wi-Fi**
要通过 shell 命令禁用 Wi-Fi，可以使用 `networksetup` 命令。

```bash
sudo networksetup -setairportpower en0 off
```

其中 `en0` 是 Wi-Fi 接口的名称。如果你的 Wi-Fi 接口名称不同，可以使用以下命令查找：

```bash
networksetup -listallhardwareports
```

### 2. **断开特定网络连接**
如果你只想断开当前连接的 Wi-Fi 网络，而不完全关闭 Wi-Fi，可以使用：

```bash
sudo networksetup -removepreferredwirelessnetwork en0 <Network Name>
```

将 `<Network Name>` 替换为你当前连接的 Wi-Fi 网络的名称。

### 3. **禁用以太网**
如果你使用有线网络，可以使用以下命令禁用以太网：

```bash
sudo ifconfig en0 down
```

同样，`en0` 是以太网接口的名称。可以使用 `ifconfig` 命令列出所有接口并找到对应的接口名称。

### 4. **启用飞行模式（关闭所有网络接口）**
如果你希望关闭所有网络接口（包括 Wi-Fi 和以太网），可以使用以下命令：

```bash
sudo ifconfig en0 down
sudo ifconfig en1 down  # 关闭第二个网络接口（如果存在）
```

要重新启用网络接口，可以使用以下命令：

```bash
sudo ifconfig en0 up
sudo ifconfig en1 up  # 重新启用第二个网络接口（如果存在）
```

这些命令可以帮助你通过 shell 控制 macOS 上的网络连接。