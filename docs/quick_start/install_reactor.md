# 安装 Reactor

安装 Reactor 是[总体目标](/docs/introduction/getting_started.md/#总体目标)的第二步。

这是 Reactor 模组（Reactor.dll），不要和反应堆框架搞混。

## 如何安装

- 从 [NuclearPowered/Reactor/releases](https://github.com/NuclearPowered/Reactor/releases) 下载 Reactor 。
- 复制 `Reactor.dll` 到 `BepInEx/plugins` 文件夹。这个文件夹是 BepInEx 之前生成的。

## 测试是否成功加载模组

打开游戏，如果操作无误，你应该能够看到 **BepInEx 版本** 及 **Reactor 版本** 在左上角，就像这样：

![reactor-test.png](/static/img/reactor-test.png)


如果没有出现，请重复[安装 BepInEx](/docs/quick_start/install_bepinex.md)的步骤，或者（有能力的）在 [Reactor 的 Discord 服务器](https://reactor.gg/discord)寻求帮助。

### 目录

- 总介绍
  - [准备开始](/docs/introduction/getting_started.md)
- 快速开始
  - [安装 BepInEx](/docs/quick_start/install_bepinex.md)
  - 安装 Reactor
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