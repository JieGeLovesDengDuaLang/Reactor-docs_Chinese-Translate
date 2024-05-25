# Harmony 教程

## 前置补丁（Prefix）与后置补丁（Postfix）的介绍

Harmony 补丁分为前置与后置补丁。
更详细的 Harmony 补丁文档请点[这里](https://harmony.pardeike.net/articles/patching.html).

前置补丁在原方法执行前执行。它可以用来：
- 访问并修改原方法的参数。
- 设置原方法的返回值。
- 跳过原方法的执行。
- One key difference to keep in mind is that while in true Harmony, patched prefixes can cancel out
  other prefixes, this is **NOT THE CASE** with HarmonyX, the fork of Harmony that BepInEx uses.
  With HarmonyX, you cannot cancel out other prefixes when returning `false` and attempting to skip the original method.
  -  Detailed rationale and implementation differences found here https://github.com/BepInEx/HarmonyX/wiki/Prefix-changes

后置补丁在原方法执行后执行。它可以用来：
- 读取或修改原方法的返回值。
- 访问原方法的参数。
- 在原方法的代码逻辑执行后执行自定义代码。

这些包含名为`Prefix`或`Postfix`静态方法补丁类通常会被**特性**标记。你可以通过向不定方法添加一个名为`__instance`且类型为补丁目标类型的参数以访问当前实例。
- 除了 `__instance`, 还有许多能被加入补丁方法的特殊参数。要了解更多，请访问 https://github.com/BepInEx/HarmonyX/wiki/Patch-parameters.

## 例子

下方是一个示例。
In particular, we call which class we want to detect, for instance, we will use the `PlayerControl` class.
After that, we would like to define what method we want to detect in that class. In this scenario, we will
use the `FixedUpdate` method which runs every time the engine updates physics.

In order for us to patch this class and method, we can use the following line:
```csharp
// 在 typeof() 中的类是将要被修补的类
// 在 nameof() 中的方法是将要被修补的方法
[HarmonyPatch(typeof(PlayerControl), nameof(PlayerControl.FixedUpdate))]
```
*确保特性在你的类的上方*

之后我们便可以定义一个名为 Postfix 的方法 since it is not necessary to use a Prefix
It is easy practice to make sure your method is public, static, and that your variable is called `__instance`
You then can access the `PlayerControl` from the variable `__instance`

```csharp
using HarmonyLib;

namespace ExampleMod
{
    [HarmonyPatch(typeof(PlayerControl), nameof(PlayerControl.FixedUpdate))]
    public static class PlayerControlPatch
    {
        public static void Postfix(PlayerControl __instance)
        {
            // 这将修改所有人都名字为“Apollo was here”（仅自己可见）
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
