# 握手（模组开发者）

如果你想让你的模组能够检测玩家是否安装（正确的）模组，你需要做以下几件事：

1. 如果你没有将 Reactor 依赖项添加，请向模组的 `.csproj` 文件里添加以下内容： `<PackageReference Include="Reactor" Version="2.0.0" />`。

2. 在 main 类中，添加特性： `[ReactorModFlags(ModFlags.RequireOnAllClients))]`。

3. 确定你的新版本模组版本号不会和老版本模组版本号一样（比如，都是0.0.0.1），如果你fork了别人的模组，记得把他的版本号改一下。Handshake 通过插件 ID 和版本号来确定是否安装（正确的）模组 

现在，Reactor 已经帮你处理好了 Handshake。

[返回](/docs/guides/handshake.md)