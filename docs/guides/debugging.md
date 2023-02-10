# 调试

## 如何调试模组

在启动模组前，我们强烈建议你打开 BepInEx 控制台以便于调试。

请打开 Among Us 游戏根目录，接着进入 `BepInEx/config` 文件夹。

你应该能够看见文件 `BepInEx.cfg` 。打开并找到`[Logging.Console]` 下的 `Enabled = false` ，把它改成 `Enabled = true`。

## Reactor.Debugger
如果你希望可以少于四个玩家就能启动游戏，请使用 `Reactor.Debugger` 。

下载 [Reactor.Debugger.dll](https://nightly.link/NuclearPowered/Reactor/workflows/main/master/Reactor.Debugger.dll) ，并把它复制到 `BepInEx/plugins` 文件夹中。

### 目录

- 总介绍
  - [准备开始](/docs/introduction/getting_started.md)
- 快速开始
  - [安装 BepInEx](/docs/quick_start/install_bepinex.md)
  - [安装 Reactor](/docs/quick_start/install_reactor.md)
  - [安装 .NET SDK 和模板](/docs/quick_start/install_netsdk_template.md)
  - [安装并配置 IDE](/docs/quick_start/install_configure_ide.md)
  - [编译示例模组](/docs/quick_start/compile_example_mod.md)
  - [加载模组和更多资源](/docs/quick_start/launch_more_resources.md)
- 指南
  - [BepInEx 指南](/docs/guides/bepinex_guide.md)
  - [Harmony 指南](/docs/guides/harmony_guide.md)
  - 调试
  - [自定义 RPC](/docs/guides/custom_rpcs.md)
  - [私服](/docs/guides/custom_server.md)
  - [握手（Handshake）](/docs/guides/handshake.md)