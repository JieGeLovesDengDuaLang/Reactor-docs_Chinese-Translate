# Custom server

sidebar_position: 4

Custom server is required to send [Custom RPCs](guides/custom_rpcs.md) and generally is strongly recommended over playing on official servers.

## Impostor

[Impostor](https://github.com/Impostor/Impostor) is a C# implementation of Among Us server with 1st party Reactor support.

1. Install Impostor following their [docs](https://github.com/Impostor/Impostor/blob/master/docs/Running-the-server.md)
2. Download Reactor.Impostor.dll from [NuclearPowered/Reactor.Impostor/releases](https://github.com/NuclearPowered/Reactor.Impostor/releases) and copy it to the server's `plugins` folder
3. Your server now supports modded handshake and custom rpcs! :tada:

Reactor.Impostor provides an API that you can use in your Impostor plugins to handle the custom rpcs on the server side.

## Hindenburg
[Hindenburg](https://github.com/SkeldJS/Hindenburg) is another option, written in TypeScript NodeJS although not supported officialy by us.

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
  - [调试](/docs/guides/debugging.md)
  - [自定义 RPC](/docs/guides/custom_rpcs.md)
  - 私服
  - [握手（Handshake）](/docs/guides/handshake.md)