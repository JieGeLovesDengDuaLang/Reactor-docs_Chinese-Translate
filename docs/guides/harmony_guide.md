# Harmony Guide

## Intro to Prefixes and Postfixes

Harmony Patches are defined as Prefixes and Postfixes.
Extensive Harmony patch documentation is [here](https://harmony.pardeike.net/articles/patching.html).

Prefixes run before the original method. It can be used to:
- Access and edit the arguments of the original method.
- Set the result of the original method.
- Skip the original method.
- One key difference to keep in mind is that while in true Harmony, patched prefixes can cancel out
  other prefixes, this is **NOT THE CASE** with HarmonyX, the fork of Harmony that BepInEx uses.
  With HarmonyX, you cannot cancel out other prefixes when returning `false` and attempting to skip the original method.
  -  Detailed rationale and implementation differences found here https://github.com/BepInEx/HarmonyX/wiki/Prefix-changes

Postfixes run after the original method. They can be used to:
- Read or change the result of the original method.
- Access the arguments of the original method.
- Run custom code after the logic of the original method has executed.

They are usually defined as **attributes** above a patch class,
which contains static methods named `Prefix` and/or `Postfix`. You can
access the current instance by adding a `__instance` parameter to the method (with the type
of the class you are patching).
- Aside from `__instance`, there are many more special parameters that can be added to the method,
  such as the ability to access arguments that are passed in from the existing method. They can all
  be found at https://github.com/BepInEx/HarmonyX/wiki/Patch-parameters.

## Understanding how to Patch Classes

An example patch is below.
In particular, we call which class we want to detect, for instance, we will use the `PlayerControl` class.
After that, we would like to define what method we want to detect in that class. In this scenario, we will
use the `FixedUpdate` method which runs every time the engine updates physics.

In order for us to patch this class and method, we can use the following line:
```csharp
// The type in the typeof() is the class being patched.
// The method in the nameof() is the method of the class that is being patched
[HarmonyPatch(typeof(PlayerControl), nameof(PlayerControl.FixedUpdate))]
```
*Make sure that this is above your class*

After that, we can create a Postfix method since it is not necessary to use a Prefix
It is easy practice to make sure your method is public, static, and that your variable is called `__instance`
You then can access the `PlayerControl` from the variable `__instance`

```csharp
using HarmonyLib;

namespace ExampleMod
{
    [HarmonyPatch(typeof(PlayerControl), nameof(PlayerControl.FixedUpdate))]
    public static class PlayerControlPatch
    {
        // It is nice to know that this method runs for all players so all player's names are changed to "Apollo was here"
        public static void Postfix(PlayerControl __instance)
        {
            // This changes all player's name into "Apollo was here"
            __instance.nameText.Text = "Apollo was here";
        }
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
  - [BepInEx 指南](/docs/guides/bepinex_guide.md)
  - Harmony 指南
  - [调试](/docs/guides/debugging.md)
  - [自定义 RPC](/docs/guides/custom_rpcs.md)
  - [私服](/docs/guides/custom_server.md)
  - [握手（Handshake）](/docs/guides/handshake.md)