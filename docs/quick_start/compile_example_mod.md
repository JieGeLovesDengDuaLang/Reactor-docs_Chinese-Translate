# 编译示例模组


编译示例模组是[总体目标](/docs/introduction/getting_started.md/#总体目标)的第四步。


## 编译

在 IDE 中，你可以直接按下生成按钮来编译模组。如果你的编辑器并不支持，可以在
[此文件夹](/docs/quick_start/install_netsdk_template.md/#生成新模组模板文件)里面的你所命名的文件夹（有 .sln 的文件夹）下使用命令提示符进行编译。

使用此命令进行编译：

```shell
dotnet build
```

.dll 文件应该输出在 `bin/Debug/net6.0/你的模组名称.dll`，把它复制到游戏根目录下的 `BepInEx/plugins` 文件夹下或者使用命令直接输出到 `BepInEx/plugins` 下：

```shell
dotnet build -p:AmongUs="文\件\夹\路\径"
```

### 目录

- 总介绍
  - [准备开始](/docs/introduction/getting_started.md)
- 快速开始
  - [安装 BepInEx](/docs/quick_start/install_bepinex.md)
  - [安装 Reactor](/docs/quick_start/install_reactor.md)
  - [安装 .NET SDK 和模板](/docs/quick_start/install_netsdk_template.md)
  - [安装并配置 IDE](/docs/quick_start/install_configure_ide.md)
  - 编译示例模组
  - [加载模组和更多资源](/docs/quick_start/launch_more_resources.md)
- 指南
  - [BepInEx 指南](/docs/guides/bepinex_guide.md)
  - [Harmony 指南](/docs/guides/harmony_guide.md)
  - [调试](/docs/guides/debugging.md)
  - [自定义 RPC](/docs/guides/custom_rpcs.md)
  - [私服](/docs/guides/custom_server.md)
  - [握手（Handshake）](/docs/guides/handshake.md)
