# 安装 BepInEx

安装 BepInEx 是[总体目标](/docs/introduction/getting_started.md/#总体目标)的第一步。


## 如何下载

BepInEx 以 zip 文件发布。文件名将会标注它的一些信息。
  - 下载 `BepInEx-Unity.IL2CPP-win-x86-....zip` from [builds.bepinex.dev](https://builds.bepinex.dev/projects/bepinex_be).


### 安装 BepInEx

把压缩包解压至 Among Us 游戏根目录下。目录应该就像这样：

```
.
├── Among Us_Data
├── Among Us.exe
├── BepInEx
│   └── core/
├── doorstop_config.ini
├── GameAssembly.dll
├── dotnet/
├── UnityCrashHandler32.exe
├── UnityPlayer.dll
└── winhttp.dll
```

然后，请根据[首次启动游戏](#首次启动游戏)中的方法进行操作。

---

## 警告：

如果你使用 Linux，你应该将 winhttp 添加到你的 wine 配置覆盖中，在安装 Among Us 的 wine 前缀中。如果你使用 Proton，参考[这个](https://docs.bepinex.dev/master/articles/advanced/steam_interop.html#open-winecfg-for-the-target-game)教程来操作。如果你不这么做，BepInEx 将**不会**工作！

---

## 首次启动游戏

当你装上 BepInEx 启动游戏，启动时间将会延长数十秒甚至数分钟。不用担心，BepInEx 只是在生成更多需要的文件。当你之后启动游戏，将不会像第一次时间这么长。BepInEx 将会生成以下文件夹：
`cache`, `config`, `patchers` 和 `plugins` 文件夹。`interop/` 文件夹（可能没有）将会生成许多 `.dll` 文件，当然还会有更多，这些都是正常的。

接下来，你的文件夹应该像这样

```
.
├── Among Us_Data
├── Among Us.exe
├── BepInEx
│   ├── cache/
│   ├── config/
│   ├── core/
│   ├── patchers/
│   ├── plugins/
│   ├── interop/
│   └── unity-libs/
├── doorstop_config.ini
├── GameAssembly.dll
├── dotnet/
├── UnityCrashHandler32.exe
├── UnityPlayer.dll
└── winhttp.dll
```

### 目录

- 总介绍
  - [准备开始](/docs/introduction/getting_started.md)
- 快速开始
  - 安装 BepInEx
  - [安装 Reactor](/docs/quick_start/install_reactor.md)
  - [安装 .NET SDK 和模板](/docs/quick_start/install_netsdk_template.md)
  - [安装并配置 IDE](/docs/quick_start/install_configure_ide.md)
  - [编译示例模组](/docs/quick_start/compile_example_mod.md)
  - [加载模组和更多资源](/docs/quick_start/launch_more_resources.md)
- 指南
  - [BepInEx 指南](/docs/guides/bepinex_guide.md)
  - [Harmony 指南](/docs/guides/harmony_guide.md)
  - [调试](/docs/guides/debugging.md)
  - [自定义 RPC](/docs/guides/custom_rpcs.md)
  - [私服](/docs/guides/custom_server.md)
  - [握手（Handshake）](/docs/guides/handshake.md)