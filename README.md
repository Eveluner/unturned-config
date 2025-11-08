# unturned-config
unturned config save

关于安装steamcmd
一般的Ubuntu系统 **没有启用 i386 架构支持**，因此 apt 找不到任何以 `:i386` 结尾的 32 位库。SteamCMD 依赖 32 位运行库，所以必须先启用它。下面是完整修复步骤 👇

---

## 🧩 一、启用 i386 架构

运行：

```bash
dpkg --add-architecture i386
apt update
```

这一步让 apt 支持安装 32 位软件包。更新完后再安装依赖。

---

## 🧰 二、安装 SteamCMD 所需的 32 位库

执行：

```bash
apt install -y lib32gcc-s1 libc6:i386 libstdc++6:i386
```

> ✅ 如果你是 **Debian 12 / Ubuntu 22.04 或更新版本**，正确包名是：
>
> * `lib32gcc-s1`
> * `libstdc++6:i386`
> * `libc6:i386`

（旧系统用 `libgcc1:i386`）

---

## ⚙️ 三、确认成功

检查 32 位库是否装好：

```bash
dpkg -l | grep i386
```

你应该看到：

```
ii  libc6:i386
ii  libstdc++6:i386
ii  lib32gcc-s1
```

---

## 🚀 四、重新运行 SteamCMD

然后再执行：

```bash
cd /root/steamcmd
./steamcmd.sh
```

应正常启动并显示：

```
Redirecting stderr to '/root/Steam/logs/stderr.txt'
[----] Verifying installation...
Steam>
```

---

如果运行上面命令后还是提示 “No such file or directory”，运行

```bash
uname -m
ls /root/steamcmd
ls /root/steamcmd/linux32
```


