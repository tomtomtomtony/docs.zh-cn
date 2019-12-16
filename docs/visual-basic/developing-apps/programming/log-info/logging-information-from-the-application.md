---
title: "记录来自应用程序的信息 (Visual Basic)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Log object
- My.Log object
- applications [Visual Basic], logging information from
- logging
- My.Application.Log object
- examples [Visual Basic], logging application information
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 58f21df20425b0164586143ad5af6f363a90c3ef
ms.contentlocale: zh-cn
ms.lasthandoff: 07/28/2017

---
# <a name="logging-information-from-the-application-visual-basic"></a><span data-ttu-id="aa4e7-102">记录来自应用程序的信息 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa4e7-102">Logging Information from the Application (Visual Basic)</span></span>
<span data-ttu-id="aa4e7-103">本节包含的主题介绍如何使用 `My.Application.Log` 或 `My.Log` 对象记录来自应用程序的信息，以及如何扩展应用程序的日志记录功能。</span><span class="sxs-lookup"><span data-stu-id="aa4e7-103">This section contains topics that cover how to log information from your application using the `My.Application.Log` or `My.Log` object, and how to extend the application's logging capabilities.</span></span>  
  
 <span data-ttu-id="aa4e7-104">`Log` 对象提供用于将信息写入应用程序的日志侦听器的方法，而 `Log` 对象的高级 `TraceSource` 属性提供详细的配置信息。</span><span class="sxs-lookup"><span data-stu-id="aa4e7-104">The `Log` object provides methods for writing information to the application's log listeners, and the `Log` object's advanced `TraceSource` property provides detailed configuration information.</span></span> <span data-ttu-id="aa4e7-105">`Log` 对象由应用程序的配置文件配置。</span><span class="sxs-lookup"><span data-stu-id="aa4e7-105">The `Log` object is configured by the application's configuration file.</span></span>  
  
 <span data-ttu-id="aa4e7-106">`My.Log` 对象仅适用于 ASP.NET 应用程序。</span><span class="sxs-lookup"><span data-stu-id="aa4e7-106">The `My.Log` object is available only for ASP.NET applications.</span></span> <span data-ttu-id="aa4e7-107">对于客户端应用程序，请使用 `My.Application.Log`。</span><span class="sxs-lookup"><span data-stu-id="aa4e7-107">For client applications, use `My.Application.Log`.</span></span> <span data-ttu-id="aa4e7-108">有关详细信息，请参阅<xref:Microsoft.VisualBasic.Logging.Log>。</span><span class="sxs-lookup"><span data-stu-id="aa4e7-108">For more information, see <xref:Microsoft.VisualBasic.Logging.Log>.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="aa4e7-109">任务</span><span class="sxs-lookup"><span data-stu-id="aa4e7-109">Tasks</span></span>  
  
|<span data-ttu-id="aa4e7-110">到</span><span class="sxs-lookup"><span data-stu-id="aa4e7-110">To</span></span>|<span data-ttu-id="aa4e7-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="aa4e7-111">See</span></span>|  
|--------|---------|  
|<span data-ttu-id="aa4e7-112">将事件信息写入应用程序日志。</span><span class="sxs-lookup"><span data-stu-id="aa4e7-112">Write event information to the application's logs.</span></span>|[<span data-ttu-id="aa4e7-113">如何：编写日志消息</span><span class="sxs-lookup"><span data-stu-id="aa4e7-113">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)|  
|<span data-ttu-id="aa4e7-114">将异常信息写入应用程序日志。</span><span class="sxs-lookup"><span data-stu-id="aa4e7-114">Write exception information to the application's logs.</span></span>|[<span data-ttu-id="aa4e7-115">如何：日志异常</span><span class="sxs-lookup"><span data-stu-id="aa4e7-115">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)|  
|<span data-ttu-id="aa4e7-116">在应用程序启动和关闭时，将跟踪信息写入应用程序日志。</span><span class="sxs-lookup"><span data-stu-id="aa4e7-116">Write trace information to the application's logs when the application starts and shuts down.</span></span>|[<span data-ttu-id="aa4e7-117">如何：当应用程序启动或关闭时记录消息</span><span class="sxs-lookup"><span data-stu-id="aa4e7-117">How to: Log Messages When the Application Starts or Shuts Down</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|<span data-ttu-id="aa4e7-118">配置 `My.Application.Log`，将信息写入文本文件。</span><span class="sxs-lookup"><span data-stu-id="aa4e7-118">Configure `My.Application.Log` to write information to a text file.</span></span>|[<span data-ttu-id="aa4e7-119">如何：将事件信息写入文本文件</span><span class="sxs-lookup"><span data-stu-id="aa4e7-119">How to: Write Event Information to a Text File</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)|  
|<span data-ttu-id="aa4e7-120">配置 `My.Application.Log`，将信息写入事件日志。</span><span class="sxs-lookup"><span data-stu-id="aa4e7-120">Configure `My.Application.Log` to write information to an event log.</span></span>|[<span data-ttu-id="aa4e7-121">如何：写入应用程序事件日志</span><span class="sxs-lookup"><span data-stu-id="aa4e7-121">How to: Write to an Application Event Log</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)|  
|<span data-ttu-id="aa4e7-122">更改 `My.Application.Log` 写入信息的位置。</span><span class="sxs-lookup"><span data-stu-id="aa4e7-122">Change where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="aa4e7-123">演练：更改 My.Application.Log 写入信息的位置</span><span class="sxs-lookup"><span data-stu-id="aa4e7-123">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="aa4e7-124">确定 `My.Application.Log` 写入信息的位置。</span><span class="sxs-lookup"><span data-stu-id="aa4e7-124">Determine where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="aa4e7-125">演练：确定 My.Application.Log 写入信息的位置</span><span class="sxs-lookup"><span data-stu-id="aa4e7-125">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="aa4e7-126">为 `My.Application.Log` 创建自定义日志侦听器。</span><span class="sxs-lookup"><span data-stu-id="aa4e7-126">Create a custom log listener for `My.Application.Log`.</span></span>|[<span data-ttu-id="aa4e7-127">演练：创建自定义日志侦听器</span><span class="sxs-lookup"><span data-stu-id="aa4e7-127">Walkthrough: Creating Custom Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)|  
|<span data-ttu-id="aa4e7-128">筛选 `My.Application.Log` 日志的输出。</span><span class="sxs-lookup"><span data-stu-id="aa4e7-128">Filter the output of the `My.Application.Log` logs.</span></span>|[<span data-ttu-id="aa4e7-129">演练：筛选 My.Application.Log 输出</span><span class="sxs-lookup"><span data-stu-id="aa4e7-129">Walkthrough: Filtering My.Application.Log Output</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a><span data-ttu-id="aa4e7-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aa4e7-130">See Also</span></span>  
 <span data-ttu-id="aa4e7-131"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="aa4e7-131"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span></span>   
 <span data-ttu-id="aa4e7-132">[使用应用程序日志](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span><span class="sxs-lookup"><span data-stu-id="aa4e7-132">[Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span></span>  
 [<span data-ttu-id="aa4e7-133">疑难解答：日志侦听器</span><span class="sxs-lookup"><span data-stu-id="aa4e7-133">Troubleshooting: Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
