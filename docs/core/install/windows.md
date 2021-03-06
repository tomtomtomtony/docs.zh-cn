---
title: 在 Windows 上安装 .NET Core
description: 了解可在其上安装 .NET Core 的 Windows 版本。
author: adegeo
ms.author: adegeo
ms.date: 06/22/2020
ms.openlocfilehash: e26494de7e9246b241cb965d8d735a781aab5478
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85804448"
---
# <a name="install-net-core-on-windows"></a>在 Windows 上安装 .NET Core

> [!div class="op_single_selector"]
>
> - [在 Windows 上安装](windows.md)
> - [在 macOS 上安装](macos.md)
> - [在 Linux 上安装](linux.md)

在本文中，你将了解如何在 Windows 上安装 .NET Core。 .NET Core 由运行时和 SDK 组成。 运行时用于运行 .NET Core 应用，应用可能包含也可能不包含它。 SDK 用于创建 .NET Core 应用和库。 .NET Core 运行时始终随 SDK 一起安装。

最新版本的 .NET Core 是 3.1。

[下载 .NET Core。](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a>支持的版本

下表列出了当前支持的 .NET Core 版本以及支持它们的 Windows 版本。 这些版本在 [.NET Core 版本达到支持终止日期](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)或 [Windows 版本达到生命周期](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)之前仍受支持。

Windows 10 版本终止服务日期按版本分段。 下表中仅考虑家庭版、专业版、专业教育版和专业工作站版。    查看 [Windows 生命周期事实表单](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)，了解具体的详细信息。

- ✔️ 指示 Windows 或 .NET Core 版本仍受支持。
- ❌ 指示 Windows 或 .NET Core 版本在该 Windows 版本上不受支持。
- 当 Windows 版本和 .NET Core 版本都有 ✔️ 时，支持该 OS 和 .NET 组合。

| 操作系统                      | .NET Core 2.1 | .NET Core 3.1 | .NET 5 预览版 |
|-----------------------------|---------------|---------------|----------------|
| ✔️ Windows 10 版本 2004 | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 预览版 |
| ✔️ Windows 10 版本 1909 | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 预览版 |
| ✔️ Windows 10 版本 1903 | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 预览版 |
| ✔️ Windows 10 版本 1809 | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 预览版 |
| ❌ Windows 10 版本 1803 | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 预览版 |
| ❌ Windows 10 版本 1709 | ❌ 2.1        | ❌ 3.1        | ❌ 5.0 预览版 |
| ❌ Windows 10 版本 1703 | ❌ 2.1        | ❌ 3.1        | ❌ 5.0 预览版 |
| ❌ Windows 10 版本 1607 | ❌ 2.1        | ❌ 3.1        | ❌ 5.0 预览版 |
| ❌ Windows 10 版本 1511 | ❌ 2.1        | ❌ 3.1        | ❌ 5.0 预览版 |
| ❌ Windows 10 版本 1507 | ❌ 2.1        | ❌ 3.1        | ❌ 5.0 预览版 |

## <a name="unsupported-releases"></a>不支持的版本

以下 .NET Core 版本 ❌ 不再受支持。 这些版本的下载仍保持发布状态：

- 3.0
- 2.2
- 2.0

## <a name="runtime-information"></a>运行时信息

运行时用于运行使用 .NET Core 创建的应用。 应用作者发布应用时，可以在其应用中包含运行时。 如果作者未包含运行时，则由用户安装运行时。

可以在 Windows 上安装三个不同的运行时：

*ASP.NET Core 运行时*\
运行 ASP.NET Core 应用。 包括 .NET Core 运行时。

*桌面运行时*\
运行适用于 Windows 的 .NET Core WPF 和 .NET Core Windows 窗体桌面应用。 包括 .NET Core 运行时。

*.NET Core 运行时*\
此运行时是最简单的运行时，不包括任何其他运行时。 强烈建议同时安装 ASP.NET Core 运行时和桌面运行时，以最大限度地提升与 .NET Core 应用的兼容性。 

[下载 .NET Core 运行时。](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a>SDK 信息

SDK 用于生成和发布 .NET Core 应用和库。 安装 SDK 会包含三个[运行时](#runtime-information)：ASP.NET Core、桌面和 .NET Core。

[下载 .NET Core SDK。](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="dependencies"></a>依赖项

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[.NET Core 3.1](#tab/netcore31)

.NET Core 3.1 支持下列 Windows 版本：

> [!NOTE]
> `+` 表示最低版本。

| (OS)                            | Version                        | 体系结构   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows 客户端                | 8.1                            | x64、x86        |
| Windows 10 客户端             | 版本 1609+                  | x64、x86        |
| Windows Server                | 2012 R2+                       | x64、x86        |
| Nano Server                   | 版本 1803+                  | x64、ARM32      |

有关 .NET Core 3.1 支持的操作系统、发行版和生命周期策略的详细信息，请参阅 [.NET Core 3.1 支持的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)。

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

目前不支持 .NET Core 3.0。有关详细信息，请参阅 [.NET Core 支持策略](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。

.NET Core 3.0 支持下列 Windows 版本：

> [!NOTE]
> `+` 表示最低版本。

| (OS)                            | Version                        | 体系结构   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows 客户端                | 7 SP1+、8.1                    | x64、x86        |
| Windows 10 客户端             | 版本 1607+                  | x64、x86        |
| Windows Server                | 2012 R2+                       | x64、x86        |
| Nano Server                   | 版本 1803+                  | x64、ARM32      |

有关 .NET Core 3.0 支持的操作系统、发行版和生命周期策略的详细信息，请参阅 [.NET Core 3.0 支持的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)。

# <a name="net-core-22"></a>[.NET Core 2.2](#tab/netcore22)

目前不支持 .NET Core 2.2。有关详细信息，请参阅 [.NET Core 支持策略](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。

.NET Core 2.2 支持下列 Windows 版本：

> [!NOTE]
> `+` 表示最低版本。

| (OS)                            | Version                        | 体系结构   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows 客户端                | 7 SP1+、8.1                    | x64、x86        |
| Windows 10 客户端             | 版本 1607+                  | x64、x86        |
| Windows Server                | 2008 R2 SP1+                   | x64、x86        |
| Nano Server                   | 版本 1803+                   | x64、ARM32      |

有关 .NET Core 2.2 支持的操作系统、发行版和生命周期策略的详细信息，请参阅 [.NET Core 2.2 支持的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

.NET Core 2.1 支持下列 Windows 版本：

> [!NOTE]
> `+` 表示最低版本。

| (OS)                            | Version                        | 体系结构   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows 客户端                | 7 SP1+、8.1                    | x64、x86        |
| Windows 10 客户端             | 版本 1607+                  | x64、x86        |
| Windows Server                | 2008 R2 SP1+                   | x64、x86        |
| Nano Server                   | 版本 1803+                  | x64            |

有关 .NET Core 2.1 支持的操作系统、发行版和生命周期策略的详细信息，请参阅 [.NET Core 2.1 支持的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a> Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2

如果要在以下 Windows 版本上安装 .NET SDK 或运行时，则需要其他依赖项：

- ❌ Windows 7 SP1
- ❌ Windows Vista SP 2
- ✔️ Windows 8.1
- ✔️ Windows Server 2008 R2
- ✔️ Windows Server 2012 R2

安装以下组件：

- [Microsoft Visual C++ 2015 Redistributable 更新 3](https://www.microsoft.com/download/details.aspx?id=52685)。
- [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

如果遇到一个以下错误，也需要满足上述要求：

> 此程序无法启动，因为计算机上缺少 api-ms-win-crt-runtime-l1-1-0.dll。 尝试重新安装该程序以解决此问题。
>
> \- 或 -
>
> 此程序无法启动，因为计算机上缺少 api-ms-win-cor-timezone-l1-1-0.dll。 尝试重新安装该程序以解决此问题。
>
> \- 或 -
>
> 已找到库 hostfxr.dll，但未能将其从 C:\\\<path_to_app>\\hostfxr.dll 中加载。

## <a name="install-with-powershell-automation"></a>使用 PowerShell 自动化安装

[dotnet-install 脚本](../tools/dotnet-install-script.md)用于运行时的 CI 自动化和非管理员安装。 可从 [dotnet-install 脚本引用页](../tools/dotnet-install-script.md)下载该脚本。

此脚本默认安装最新的[长期支持 (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 版本，即 .NET Core 3.1。 可通过指定 `Channel` 开关以选择特定版本。 包括 `Runtime` 开关以安装运行时。 否则，该脚本安装 [SDK](sdk.md)。

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

通过省略 `-Runtime` 开关来安装 SDK。 在此示例中将 `-Channel` 开关设置为 `Current`，这将安装受支持的最新版本。

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a>使用 Visual Studio 安装

如果你要使用 Visual Studio 开发 .NET Core 应用，请参阅下表，了解不同目标 .NET Core SDK 版本所需的 Visual Studio 最低版本。

| .NET Core SDK 版本 | Visual Studio 版本                      |
| --------------------- | ------------------------------------------ |
| 3.1                   | Visual Studio 2019 版本 16.4 或更高版本。 |
| 3.0                   | Visual Studio 2019 版本 16.3 或更高版本。 |
| 2.2                   | Visual Studio 2017 版本 15.9 或更高版本。 |
| 2.1                   | Visual Studio 2017 版本 15.7 或更高版本。 |

如果你已安装 Visual Studio，则可以使用以下步骤检查你的版本。

01. 打开 Visual Studio。
01. 选择“帮助” > “Microsoft Visual Studio”。
01. 从“关于”对话框中读取版本号。

Visual Studio 可安装最新的 .NET Core SDK 和运行时。

- [下载 Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)。

### <a name="select-a-workload"></a>选择工作负载

安装或修改 Visual Studio 时，根据要生成的应用程序的类型，选择以下一个或多个工作负载：

- “其他工具集”部分中的“.NET Core 跨平台开发”工作负荷 。
- “Web 和云”部分中的“ASP.NET 和 Web 开发”工作负荷 。
- “Web 和云”部分中的“Azure 开发”工作负载 。
- “桌面和移动”部分中的“NET 桌面开发”工作负载 。

[![具有 .NET Core 工作负载的 Windows Visual Studio 2019](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)

## <a name="install-alongside-visual-studio-code"></a>随 Visual Studio Code 一起安装

Visual Studio Code 是一个功能强大的轻量级源代码编辑器，可在桌面上运行。 Visual Studio Code 适用于 Windows、macOS 和 Linux。

虽然 Visual Studio Code 不像 Visual Studio 一样附带自动的 .NET Core 安装程序，但添加 .NET Core 支持非常简单。

01. [下载并安装 Visual Studio Code](https://code.visualstudio.com/Download)。
01. [下载并安装 .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core)。
01. [从 Visual Studio Code 市场安装 C# 扩展](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)。

## <a name="download-and-manually-install"></a>下载并手动安装

除了使用适用于 .NET Core 的 Windows 安装程序，还可以下载并手动安装 SDK 或运行时。 手动安装通常作为持续集成测试的一部分执行。 对于开发人员或用户，一般使用[安装程序](https://dotnet.microsoft.com/download/dotnet-core)会更好。

在下载 .NET Core SDK 和 .NET Core 运行时后，可以手动安装它们。 如果安装 .NET Core SDK，则无需安装相应的运行时。 首先，从以下站点之一下载 SDK 或运行时的二进制版本：

- ✔️ [.NET 5.0 预览版下载](https://dotnet.microsoft.com/download/dotnet/5.0)
- ✔️ [.NET Core 3.1 下载](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- ✔️ [.NET Core 2.1 下载](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [所有 .NET Core 下载项](https://dotnet.microsoft.com/download/dotnet-core)

创建要将 .NET 提取到的目录，例如 `%USERPROFILE%\dotnet`。 然后，将下载的 zip 文件提取到该目录中。

默认情况下，.NET Core CLI 命令和应用不会使用通过这种方式安装的 .NET Core，且你必须显式选择以使用它。 为此，请更改用于启动应用程序的环境变量：

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

使用此方法可以将多个版本安装到不同的位置，然后通过使用指向安装位置的环境变量运行应用程序来明确选择应用程序应使用哪个安装位置。

将 `DOTNET_MULTILEVEL_LOOKUP` 设置为 `0` 时，.NET Core 将忽略任何全局安装的 .NET Core 版本。 删除环境设置，让 .NET Core 在选择用于运行应用程序的最佳框架时考虑默认的全局安装位置。 默认值通常为 `C:\Program Files\dotnet`，这是安装 .NET Core 的安装程序所在的位置。

## <a name="docker"></a>Docker

容器提供了一种将应用程序与主机系统的其余部分隔离的轻量级方法。 同一计算机上的容器只共享内核，并使用为应用程序提供的资源。

.NET Core 可在 Docker 容器中运行。 官方 .NET Core Docker 映像发布到 Microsoft 容器注册表 (MCR)，用户可以在 [Microsoft.NET Core Docker 中心存储库](https://hub.docker.com/_/microsoft-dotnet-core/)中找到这些映像。 每个存储库包含 .NET（SDK 或运行时）和可以使用的操作系统的不同组合的映像。

Microsoft 提供适合特定场景的映像。 例如，[ASP.NET Core 存储库](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/)提供针对在生产环境中运行 ASP.NET Core 应用生成的映像。

有关在 Docker 容器中使用 .NET Core 的详细信息，请参阅 [.NET 和 Docker 简介](../docker/introduction.md)和[示例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)。

## <a name="next-steps"></a>后续步骤

- [如何检查是否已安装 .NET Core](how-to-detect-installed-versions.md?pivots=os-windows)。
- [教程：Hello World 教程](../tutorials/with-visual-studio.md)。
- [教程：使用 Visual Studio Code 创建一个新应用](../tutorials/with-visual-studio-code.md)。
- [教程：使 .NET Core 应用容器化](../docker/build-container.md)。
