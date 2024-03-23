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
### 译者注释
#### 重要！RPC的Id不要过小（因为可能会错误地与原版游戏RPC的Id重合）！推荐Id大于等于50
本教程对RPC的解释并不全面，因此在这里添加几个注释：<br/>
RPC：远程过程调用，通过对一个客户端发送消息以远程执行对方客户端的一个方法。<br/>
就拿刚才的例子来说，玩家向本地写入了“0”（CustomRpcCalls.SayHello）这个代表打招呼Rpc的Id。紧接着，玩家继续写入要发送的消息，最后玩家将存入本地的消息发送出去。<br/>这样各位可能不理解，那么我们使用树懒提供的原版RPC函数举例：
```csharp
MessageWriter writer = AmongUsClient.Instance.StartRpcImmediately(PlayetControl.LocalPlayer.NetId, (byte)CustomRpcCalls.SayHello, SendOption.Reliable, -1);//用于启动一个RPC的函数，返回一个消息写入器
//第一个参数：发送者的NetId
//第二个参数：RPC的Id
//第三个参数：发送的消息是否可信
//第四个参数：接受者的PlayerId，-1代表所有人，-2代表无
writer.Write(/*要发送的字符串*/);//向本地写入数据
AmongUsClient.Instance.FinishRpcImmediately(writer);//发送RPC
```
##### 注意：下方内容仅适用于无Reactor的模组！Reactor会帮你处理好下面的问题的！
我们既然发送了RPC，别的客户端又应该如何接收RPC呢？<br/>答案是Patch一下接收RPC的方法。（需要一定的Harmony经验，请参考Harmony官方文档）
```csharp
[HarmonyPatch(typeof(PlayerControl), nameof(PlayefControl.HandleRpc))]//标记Patch的目标方法
class ReceiveRpcPatch
{
     static void Postfix/*名称必须为Postfix，意为在原方法执行后执行*/(PlayerControl __instance, [HarmonyArgument(0)] byte callId, [HarmonyArgument(1)] MessageReader reader)//获取接受消息的玩家、RPC的Id以及消息接收器
     {
          CustomRpcCalls rpc = (CustomRpcCalls)callId;//转换RPC的Id至枚举
          switch (rpc)//switch语句选择RPC要执行的内容
          {
                case CustomRpcCalls.SayHello:
                      string msg = reader.ReadString();//获取字符串
                      Logger<ExamplePlugin>.Info($"{__instance.Data.PlayerName} said: {message}");//输出玩家名称及内容
                      break;
          }
     }
}
```
在这段代码中，我们Patch了接收RPC的方法，获取了原方法的两个参数，并转换Id为枚举，通过switch语句进行判断，如果RPC是打招呼，那么在控制台输出消息。

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
