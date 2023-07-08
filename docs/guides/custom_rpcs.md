# 自定义 RPC

## 什么是 RPC?

RPC 是一个通过网络来调用方法的方法。在 Among Us 中，你可以自定义 RPC ，可以向其它玩家发送数据并让他们也能调用方法。

## 如何自定义 RPC？

使用 Reactor，你有以下方法来使用 RPC：

- RPC 方法 - 最简单和快捷的方法

- 扩展 `CustomRpc` 类 - 最灵活但笨重的方法

两种情况下，你都需要一个枚举，例如 `CustomRpcCalls` （可自定义名称）来存储 RPC 的 ID。 

```csharp
public enum CustomRpcCalls : uint
{
    SayHello = 0
}
```

### RPC 方法

定义一个 RPC 方法，按照以下代码去操作：

```csharp
[MethodRpc((uint) CustomRpcCalls.SayHello)]
public static void RpcSayHello(PlayerControl player, string text)
{
    Logger<ExamplePlugin>.Info($"{player.Data.PlayerName} said: {text}");
}
```

调用方法：

```csharp
RpcSayHello(PlayerControl.LocalPlayer, "Hello from docs.reactor.gg!");
```
---

#### 提示

RPC 方法可以是扩展方法

---


### RPC 类

---

#### 小心

如果你要使用这个方法，请确保你对 Hazel 足够熟练，并且 `MessageConverter` api 对你来说太具有局限性。

---

定义一个类：

```csharp
[RegisterCustomRpc((uint) CustomRpcCalls.SayHello)]
public class SayHelloRpc : PlayerCustomRpc<ExamplePlugin, SayHelloRpc.Data>
{
    public SayHelloRpc(ExamplePlugin plugin, uint id) : base(plugin, id)
    {
    }

    public override RpcLocalHandling LocalHandling => RpcLocalHandling.Before;

    public readonly struct Data
    {
        public readonly string Message;

        public Data(string message)
        {
            Message = message;
        }
    }

    public override void Write(MessageWriter writer, Data data)
    {
        writer.Write(data.Message);
    }

    public override Data Read(MessageReader reader)
    {
        return new Data(reader.ReadString());
    }

    public override void Handle(PlayerControl player, Data data)
    {
        Logger<ExamplePlugin>.Info($"{player.Data.PlayerName} said: {data.Message}");
    }
}
```

调用类：

```csharp
Rpc<SayHelloRpc>.Instance.Send(new SayHelloRpc.Data("Hello from docs.reactor.gg!"));
```
---

#### 提示

`Rpc<T>.Instance` 返回 T 的实例，方便在 RPC 上调用与访问成员。你可以用它来创建 Helper 方法。

---

译者注：本教程对RPC的解释并不全面，因此在这里添加几个注释：
RPC：远程过程调用，通过对一个客户端发送消息以远程执行对方客户端的一个方法
例：客户端1向客户端2发送了数据“0”，而0在程序中定义为“开始游戏”，客户端2接受数据0后会执行用于开始游戏的函数Start()。


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
  - 自定义 RPC
  - [私服](/docs/guides/custom_server.md)
  - [握手（Handshake）](/docs/guides/handshake.md)
