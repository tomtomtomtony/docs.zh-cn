---
title: 公共语言运行时中的类型转发
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- cpp
ms.openlocfilehash: f71b56daf5e8a012a66f60805246b4164d1b0a07
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972515"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a><span data-ttu-id="ce9d3-102">公共语言运行时中的类型转发</span><span class="sxs-lookup"><span data-stu-id="ce9d3-102">Type forwarding in the common language runtime</span></span>
<span data-ttu-id="ce9d3-103">使用类型转发可以将类型移到另一个程序集，而不必重新编译使用原始程序集的应用程序。</span><span class="sxs-lookup"><span data-stu-id="ce9d3-103">Type forwarding allows you to move a type to another assembly without having to recompile applications that use the original assembly.</span></span>  
  
 <span data-ttu-id="ce9d3-104">例如，假设应用程序使用名为 Utility.dll 的程序集中的 `Example` 类。</span><span class="sxs-lookup"><span data-stu-id="ce9d3-104">For example, suppose an application uses the `Example` class in an assembly named *Utility.dll*.</span></span> <span data-ttu-id="ce9d3-105">Utility.dll 的开发人员可能决定重构该程序集，并且在重构过程中可能将 `Example` 类移到另一个程序集。</span><span class="sxs-lookup"><span data-stu-id="ce9d3-105">The developers of *Utility.dll* might decide to refactor the assembly, and in the process they might move the `Example` class to another assembly.</span></span> <span data-ttu-id="ce9d3-106">如果旧版本的 Utility.dll 由新版本的 Utility.dll 及其配套程序集取代，则使用 `Example` 类的应用程序会失败，因其无法在新版本的 Utility.dll 中找到 `Example` 类。</span><span class="sxs-lookup"><span data-stu-id="ce9d3-106">If the old version of *Utility.dll* is replaced by the new version of *Utility.dll* and its companion assembly, the application that uses the `Example` class fails because it cannot locate the `Example` class in the new version of *Utility.dll*.</span></span>  
  
 <span data-ttu-id="ce9d3-107">Utility.dll 开发人员可使用 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> 属性转发 `Example` 类的请求，从而避免这种情况。</span><span class="sxs-lookup"><span data-stu-id="ce9d3-107">The developers of *Utility.dll* can avoid this by forwarding requests for the `Example` class, using the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> attribute.</span></span> <span data-ttu-id="ce9d3-108">如果已向新版本的 Utility.dll 应用了该属性，则对 `Example` 类的请求会转发到该类目前所属的程序集。</span><span class="sxs-lookup"><span data-stu-id="ce9d3-108">If the attribute has been applied to the new version of *Utility.dll*, requests for the `Example` class are forwarded to the assembly that now contains the class.</span></span> <span data-ttu-id="ce9d3-109">现有应用程序将继续正常运行，无需重新编译。</span><span class="sxs-lookup"><span data-stu-id="ce9d3-109">The existing application continues to function normally, without recompilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce9d3-110">在 .NET Framework 2.0 版中，无法从使用 Visual Basic 编写的程序集转发类型。</span><span class="sxs-lookup"><span data-stu-id="ce9d3-110">In the .NET Framework version 2.0, you cannot forward types from assemblies written in Visual Basic.</span></span> <span data-ttu-id="ce9d3-111">但是，用 Visual Basic 编写的应用程序可以使用转发的类型。</span><span class="sxs-lookup"><span data-stu-id="ce9d3-111">However, an application written in Visual Basic can consume forwarded types.</span></span> <span data-ttu-id="ce9d3-112">也就是说，如果应用程序使用通过 C# 或 C++ 编码的程序集，并且该程序集中的某类型被转发至另一个程序集，则 Visual Basic 应用程序可以使用该转发的类型。</span><span class="sxs-lookup"><span data-stu-id="ce9d3-112">That is, if the application uses an assembly coded in C# or C++, and a type from that assembly is forwarded to another assembly, the Visual Basic application can use the forwarded type.</span></span>  
  
## <a name="forward-types"></a><span data-ttu-id="ce9d3-113">转发类型</span><span class="sxs-lookup"><span data-stu-id="ce9d3-113">Forward types</span></span>  
 <span data-ttu-id="ce9d3-114">转发类型有四个步骤：</span><span class="sxs-lookup"><span data-stu-id="ce9d3-114">There are four steps to forwarding a type:</span></span>  
  
1. <span data-ttu-id="ce9d3-115">将类型的源代码从原始程序集移到目标程序集。</span><span class="sxs-lookup"><span data-stu-id="ce9d3-115">Move the source code for the type from the original assembly to the destination assembly.</span></span>  
   
2. <span data-ttu-id="ce9d3-116">在类型曾存于的程序集中，为已移动的类型添加 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>。</span><span class="sxs-lookup"><span data-stu-id="ce9d3-116">In the assembly where the type used to be located, add a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> for the type that was moved.</span></span> <span data-ttu-id="ce9d3-117">下面的代码显示名为 `Example` 的被移动类型的属性。</span><span class="sxs-lookup"><span data-stu-id="ce9d3-117">The following code shows the attribute for a type named `Example` that was moved.</span></span>  
   
   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```
   
   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  
   
3. <span data-ttu-id="ce9d3-118">编译该类型目前所属的程序集。</span><span class="sxs-lookup"><span data-stu-id="ce9d3-118">Compile the assembly that now contains the type.</span></span>  
   
4. <span data-ttu-id="ce9d3-119">重新编译该类型原来所属的程序集，其中带有对该类型目前所属的程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="ce9d3-119">Recompile the assembly where the type used to be located, with a reference to the assembly that now contains the type.</span></span> <span data-ttu-id="ce9d3-120">例如，如果从命令行编译一个 C# 文件，则使用 [/reference（C# 编译器选项）](../../csharp/language-reference/compiler-options/reference-compiler-option.md)选项指定包含类型的程序集。</span><span class="sxs-lookup"><span data-stu-id="ce9d3-120">For example, if you are compiling a C# file from the command line, use the [/reference (C# compiler options)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) option to specify the assembly that contains the type.</span></span> <span data-ttu-id="ce9d3-121">在 C++ 中，在源文件中使用 [#using](/cpp/preprocessor/hash-using-directive-cpp) 指令指定包含类型的程序集。</span><span class="sxs-lookup"><span data-stu-id="ce9d3-121">In C++, use the [#using](/cpp/preprocessor/hash-using-directive-cpp) directive in the source file to specify the assembly that contains the type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce9d3-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="ce9d3-122">See also</span></span>

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [<span data-ttu-id="ce9d3-123">类型转发 (C++/CLI)</span><span class="sxs-lookup"><span data-stu-id="ce9d3-123">Type forwarding (C++/CLI)</span></span>](/cpp/windows/type-forwarding-cpp-cli)
- [<span data-ttu-id="ce9d3-124">#using 指令</span><span class="sxs-lookup"><span data-stu-id="ce9d3-124">#using directive</span></span>](/cpp/preprocessor/hash-using-directive-cpp)