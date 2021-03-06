---
ms.openlocfilehash: 3d1dc8dec18212afd815aa3de7fc82c8a1f680dc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617791"
---
### <a name="hwndhost-now-correctly-resizes-child-hwnd-during-dpi-changes"></a>HwndHost 现可在 DPI 更改期间正确重设子 HWND 的大小

#### <a name="details"></a>详细信息

在 .NET Framework 4.7.2 和更低版本中，WPF 在预监测感知模式下运行时（例如，将应用程序从一个监视器移动到另一个监视器时），在 DPI 发生更改后，<xref:System.Windows.Interop.HwndHost> 中托管的控件的大小不正确。 此修复程序可确保托管控件的大小适当。

#### <a name="suggestion"></a>建议

为了使应用程序能够从这些更改中受益，它必须在 .NET Framework 4.7.2 或更高版本上运行，并且必须选择加入此行为，方法是将应用配置文件的 `<runtime>` 部分中的以下 [AppContext 开关](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element)设置为 `false`，如以下示例所示。

<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| 名称    | “值”       |
|:--------|:------------|
| 范围   | 主要       |
| Version | 4.8         |
| 类型    | 重定目标 |
