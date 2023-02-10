# 安装并配置 C# IDE

安装并配置 C# IDE 是[总体目标](/docs/introduction/getting_started.md/#总体目标)的第四步。

## 安装 C# IDE

下载 Rider 或 Visual Studio。当然，你也可以使用文本编辑器类的轻量级环境，比如 Visual Studio Code。

## 项目的初始配置

现在，使用 IDE 或文本编辑器打开项目。如果你的 IDE 报错，不用担心，本章末尾将会解决它。

请遵循以下步骤：

- 打开 `.csproj` 文件。
  - 如果你使用 Rider，右键项目并找到 `编辑 > 编辑 .csproj 文件`。应该跟下图一样：

    ![open_csproj_rider](https://i.stack.imgur.com/uj5yP.png)

  - 在 Visual Studio Code 中，从资源管理器视图打开 `.csproj` 文件。

  - 当然，你也可以手动更改它。

---

## 提示：

如果你找不到 `.csproj` 文件，确定你所在的目录无误。

包含 `.csproj` 的文件夹应该在你执行 `dotnet new reactor -n 你的模组名称` 的文件夹的深处。这是一张目录结构图，应该大概像这样。

---

```
.
└── 你的模组名称
    ├── 你的模组名称
    │   ├── 你的模组名称.csproj
    │   └── TemplatePlugin.cs
    └── 你的模组名称.sln
```

### 在 .csproj 文件里面

在 `.csproj` 文件内，有许多重要的东西：
  - `GameVersion` 定义了 Reactor 将会下载的游戏版本。
  - `Description` 是你对模组的介绍。
  - `Authors` 是制作者的名称。
```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net6.0</TargetFramework>
    <LangVersion>latest</LangVersion>
    <DebugType>embedded</DebugType>

    <VersionPrefix>1.0.0</VersionPrefix>
    <VersionSuffix>dev</VersionSuffix>
    <Description>Mod generated using Reactor Template</Description>
    <!-- <Authors>your name</Authors> -->
  </PropertyGroup>

  <PropertyGroup>
    <GamePlatform Condition="'$(GamePlatform)' == ''">Steam</GamePlatform>
    <GameVersion Condition="'$(GamePlatform)' == 'Steam'">2021.6.30</GameVersion>
    <GameVersion Condition="'$(GamePlatform)' == 'Itch'">2021.6.30</GameVersion>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Reactor" Version="2.0.0" />
    <PackageReference Include="BepInEx.Unity.IL2CPP" Version="6.0.0-be.662" Private="false" ExcludeAssets="runtime;native" />
    <PackageReference Include="AmongUs.GameLibs.Steam" Version="2022.10.25" PrivateAssets="all" />

    <PackageReference Include="BepInEx.AutoPlugin" Version="1.1.0" PrivateAssets="all" />
    <PackageReference Include="BepInEx.IL2CPP.MSBuild" Version="2.0.1" PrivateAssets="all" ExcludeAssets="runtime" />
  </ItemGroup>

  <Target Name="Copy" AfterTargets="Build" Condition="'$(AmongUs)' != ''">
    <Copy SourceFiles="$(TargetPath)" DestinationFolder="$(AmongUs)/BepInEx/plugins/" UseSymboliclinksIfPossible="true" />
  </Target>
</Project>
```

## 故障排除

如果 IDE 仍然报错，请尝试刷新或重启 IDE。

### 目录

- 总介绍
  - [准备开始](/docs/introduction/getting_started.md)
- 快速开始
  - [安装 BepInEx](/docs/quick_start/install_bepinex.md)
  - [安装 Reactor](/docs/quick_start/install_reactor.md)
  - [安装 .NET SDK 和模板](/docs/quick_start/install_netsdk_template.md)
  - 安装并配置 IDE
  - [编译示例模组](/docs/quick_start/compile_example_mod.md)
  - [加载模组和更多资源](/docs/quick_start/launch_more_resources.md)
- 指南
  - [BepInEx 指南](/docs/guides/bepinex_guide.md)
  - [Harmony 指南](/docs/guides/harmony_guide.md)
  - [调试](/docs/guides/debugging.md)
  - [自定义 RPC](/docs/guides/custom_rpcs.md)
  - [私服](/docs/guides/custom_server.md)
  - [握手（Handshake）](/docs/guides/handshake.md)