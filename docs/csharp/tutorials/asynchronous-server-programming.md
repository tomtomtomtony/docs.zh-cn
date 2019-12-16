---
title: "异步服务器编程 - C# 指南"
description: "了解如何使用异步编程技术卸载服务器工作负载"
keywords: "C#, 异步, 占用大量 CPU, 网络倾向"
ms.date: 08/24/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 7402b29b-1093-456d-be4c-f60ecb8926bb
redirect_url: /dotnet/csharp/tutorials/index
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 390d0eb2c8416165984ffe6c80ed6977e61a2845
ms.contentlocale: zh-cn
ms.lasthandoff: 07/28/2017

---

# <a name="-asynchronous-server-programming"></a><span data-ttu-id="1dbb4-104">🔧 异步服务器编程</span><span class="sxs-lookup"><span data-stu-id="1dbb4-104">🔧 Asynchronous Server Programming</span></span>

> <span data-ttu-id="1dbb4-105">**注意**</span><span class="sxs-lookup"><span data-stu-id="1dbb4-105">**Note**</span></span>
> 
> <span data-ttu-id="1dbb4-106">尚未编写此主题！</span><span class="sxs-lookup"><span data-stu-id="1dbb4-106">This topic hasn’t been written yet!</span></span> 
>
> <span data-ttu-id="1dbb4-107">欢迎提供建议，以帮助我们确定范围和方法。</span><span class="sxs-lookup"><span data-stu-id="1dbb4-107">We welcome your input to help shape the scope and approach.</span></span> <span data-ttu-id="1dbb4-108">可在 GitHub 处跟踪有关此[问题](https://github.com/dotnet/docs/issues/952)的状态并提供相关建议。</span><span class="sxs-lookup"><span data-stu-id="1dbb4-108">You can track the status and provide input on this [issue](https://github.com/dotnet/docs/issues/952) at GitHub.</span></span>
> 
> <span data-ttu-id="1dbb4-109">如果想要查看此主题的早期草稿和概述，请就此问题留下包含联系信息的备注。</span><span class="sxs-lookup"><span data-stu-id="1dbb4-109">If you would like to review early drafts and outlines of this topic, please leave a note with your contact information in the issue.</span></span>
>
> <span data-ttu-id="1dbb4-110">了解如何参与 [GitHub](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md) 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="1dbb4-110">Learn more about how you can contribute on [GitHub](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>
>
