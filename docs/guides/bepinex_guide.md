# BepInEx 指南

## 实践一下

这是一个示例 BasePlugin 类。运行后，它先会被 `BepInAutoPlugin` 定义一个 `Id`，然后执行 `Harmony.PatchAll()`。

```csharp
using BepInEx;
using BepInEx.Unity.IL2CPP;
using HarmonyLib;
using Reactor;
using Reactor.Utilities;

namespace Example;

[BepInAutoPlugin]
[BepInProcess("Among Us.exe")]
[BepInDependency(ReactorPlugin.Id)]
public partial class ExamplePlugin : BasePlugin
{
    public Harmony Harmony { get; } = new(Id);

    public override void Load()
    {
        Harmony.PatchAll();
    }
}
```

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
  - BepInEx 指南
  - [Harmony 指南](/docs/guides/harmony_guide.md)
  - [调试](/docs/guides/debugging.md)
  - [自定义 RPC](/docs/guides/custom_rpcs.md)
  - [私服](/docs/guides/custom_server.md)
  - [握手（Handshake）](/docs/guides/handshake.md)