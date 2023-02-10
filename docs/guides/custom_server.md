# 私服

私服便于对[自定义 RPC](/docs/guides/custom_rpcs.md) 的处理，但是通常建议在官方服务器上游玩。

## Impostor

[Impostor](https://github.com/Impostor/Impostor) 是 Among Us 服务器的 C# 实现，并且有对 Reactor 的第一方支持。

1. 根据他们的[文档说明](https://github.com/Impostor/Impostor/blob/master/docs/Running-the-server.md)来对 Impostor 进行安装。

2. 从 [NuclearPowered/Reactor.Impostor/releases](https://github.com/NuclearPowered/Reactor.Impostor/releases) 下载 Reactor.Impostor.dll，把它放到 `plugins` 文件夹中。

3. 你的服务器现在支持 Handshake 和自定义 RPC 了！🎉

Reactor.Impostor 提供了一个 API，你可以用 Impostor 来处理服务器端的自定义 RPC。

## Hindenburg
[Hindenburg](https://github.com/SkeldJS/Hindenburg) 是另一个选择，使用 TypeScript NodeJS 编写，虽然并不支持 Reactor。

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
