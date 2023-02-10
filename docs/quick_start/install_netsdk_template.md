# 安装 .NET SDK 和模板

安装 .NET SDK 和模组模板是[总体目标](/docs/introduction/getting_started.md/#总体目标)的第三步。

## 安装 .NET SDK

微软在[这里](https://dotnet.microsoft.com/download/dotnet/6.0)发布 .NET SDK。根据你的设备自行下载。

![dotnet download](/static/img/netsdk-download.png)

## 测试 .NET SDK 的安装

确定你已经安装 .NET SDK 并执行以下命令来验证是否成功：

```
dotnet --info
```

它将会返回：

```
.NET SDK (reflecting any global.json):
 Version:   6.0.100
 Commit:    9e8b04bbff

Runtime Environment:
 OS Name:     arch
 OS Version:
 OS Platform: Linux
 RID:         arch-x64
 Base Path:   /usr/share/dotnet/sdk/6.0.100/

Host (useful for support):
  Version: 6.0.0
  Commit:  4822e3c3aa

.NET SDKs installed:
  6.0.100 [/usr/share/dotnet/sdk]

.NET runtimes installed:
  Microsoft.NETCore.App 6.0.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]

To install additional .NET runtimes or SDKs:
  https://aka.ms/dotnet-download
```

如果还是不行，请尝试重启命令提示符或重新安装 .NET，并在[Reactor 的 Discord 服务器](https://reactor.gg/discord)求助。


## 安装模组模板

现在， `Reactor.Template` 模组模板需要安装。

使用以下命令安装：

```shell
dotnet new --install Reactor.Template
```

如果没有报错，`Reactor.Template` 便成功地被安装。

## 生成新模组模板文件
找个空文件夹，打开它，打开命令提示符，输入以下内容：

```shell
dotnet new reactor -n 你的模组名称
```

运行后，你的文件夹应该像这样：

```
.
└── 你的模组名称
    ├── 你的模组名称
    │   ├── 你的模组名称.csproj
    │   └── TemplatePlugin.cs
    └── 你的模组名称.sln
```

### 目录

- 总介绍
  - [准备开始](/docs/introduction/getting_started.md)
- 快速开始
  - [安装 BepInEx](/docs/quick_start/install_bepinex.md)
  - [安装 Reactor](/docs/quick_start/install_reactor.md)
  - 安装 .NET SDK 和模板
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