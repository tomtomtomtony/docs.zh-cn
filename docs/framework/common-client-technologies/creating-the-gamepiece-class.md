---
title: "创建 GamePiece 类"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37a27a86-ac1c-47be-b477-cb4b819459d3
caps.latest.revision: 9
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7ac9884766812cd635b5a70c028cf15c19838511
ms.contentlocale: zh-cn
ms.lasthandoff: 07/28/2017

---
# <a name="creating-the-gamepiece-class"></a><span data-ttu-id="6478b-102">创建 GamePiece 类</span><span class="sxs-lookup"><span data-stu-id="6478b-102">Creating the GamePiece Class</span></span>
<span data-ttu-id="6478b-103">GamePiece 类封装加载 Microsoft XNA 游戏块图像、跟踪与游戏块相关的鼠标状态、捕获鼠标、提供操作和惯性处理以及在游戏块达到视区限制时提供弹跳功能所需的所有功能。</span><span class="sxs-lookup"><span data-stu-id="6478b-103">The **GamePiece** class encapsulates all the functionality required to load a Microsoft XNA game piece image, track the state of the mouse in relation to the game piece, capture the mouse, provide manipulation and inertia processing, and provide bouncing capability when the game piece reaches the limits of the view port.</span></span>  
  
## <a name="private-members"></a><span data-ttu-id="6478b-104">私有成员</span><span class="sxs-lookup"><span data-stu-id="6478b-104">Private Members</span></span>  
 <span data-ttu-id="6478b-105">在 GamePiece 类的顶部，声明了多个私有成员。</span><span class="sxs-lookup"><span data-stu-id="6478b-105">At the top of the **GamePiece** class, several private members are declared.</span></span>  
  
 <span data-ttu-id="6478b-106">[!code-csharp[ManipulationXNA#_GamePiece_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_privatemembers)]</span><span class="sxs-lookup"><span data-stu-id="6478b-106">[!code-csharp[ManipulationXNA#_GamePiece_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_privatemembers)]</span></span>  
  
## <a name="public-properties"></a><span data-ttu-id="6478b-107">公共属性</span><span class="sxs-lookup"><span data-stu-id="6478b-107">Public Properties</span></span>  
 <span data-ttu-id="6478b-108">这些私有成员中的三个是通过公共属性公开的。</span><span class="sxs-lookup"><span data-stu-id="6478b-108">Three of these private members are exposed through public properties.</span></span> <span data-ttu-id="6478b-109">Scale 和 PieceColor 属性使应用程序能够分别指定块的比例和颜色。</span><span class="sxs-lookup"><span data-stu-id="6478b-109">The **Scale** and **PieceColor** properties enable the application to specify the scale and the color of the piece, respectively.</span></span> <span data-ttu-id="6478b-110">公开 Bounds 属性从而使一个块可以使用另一个块的边界来呈现自身，例如当一个块应覆盖另一个块时。</span><span class="sxs-lookup"><span data-stu-id="6478b-110">The **Bounds** property is exposed to enable one piece to use the bounds of another to render itself, such as when one piece should overlay another.</span></span> <span data-ttu-id="6478b-111">下面的代码显示公共属性的声明。</span><span class="sxs-lookup"><span data-stu-id="6478b-111">The following code shows the declaration of the public properties.</span></span>  
  
 <span data-ttu-id="6478b-112">[!code-csharp[ManipulationXNA#_GamePiece_PublicProperties](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_publicproperties)]</span><span class="sxs-lookup"><span data-stu-id="6478b-112">[!code-csharp[ManipulationXNA#_GamePiece_PublicProperties](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_publicproperties)]</span></span>  
  
## <a name="class-constructor"></a><span data-ttu-id="6478b-113">类构造函数</span><span class="sxs-lookup"><span data-stu-id="6478b-113">Class Constructor</span></span>  
 <span data-ttu-id="6478b-114">GamePiece 类的构造函数接受以下参数：</span><span class="sxs-lookup"><span data-stu-id="6478b-114">The constructor for the **GamePiece** class accepts the following parameters:</span></span>  
  
-   <span data-ttu-id="6478b-115">[SpriteBatch](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) 类型。</span><span class="sxs-lookup"><span data-stu-id="6478b-115">A [SpriteBatch](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) type.</span></span> <span data-ttu-id="6478b-116">在此处传递的引用被分配给私有成员 `spriteBatch`，并在游戏块呈现自身时用于访问 [SpriteBatch.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.draw.aspx) 方法。</span><span class="sxs-lookup"><span data-stu-id="6478b-116">The reference passed here is assigned to the private member `spriteBatch`, and is used to access the [SpriteBatch.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.draw.aspx) method when the game piece renders itself.</span></span> <span data-ttu-id="6478b-117">此外，[GraphicsDevice](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.graphicsdevice.aspx) 属性用于创建与游戏块关联的 [Texture](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.texture.aspx) 对象，及获取视区大小，从而检测出游戏块遇到窗口边界的时间，实现游戏块回弹。</span><span class="sxs-lookup"><span data-stu-id="6478b-117">In addition, the [GraphicsDevice](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.graphicsdevice.aspx) property is used to create the [Texture](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.texture.aspx) object associated with the game piece, and to obtain the size of the view port in order to detect when the game piece encounters a window boundary so that the piece can bounce.</span></span>  
  
-   <span data-ttu-id="6478b-118">指定要用于游戏块的图像的文件名的字符串。</span><span class="sxs-lookup"><span data-stu-id="6478b-118">A string that specifies the file name of the image to use for the game piece.</span></span>  
  
 <span data-ttu-id="6478b-119">构造函数还创建 <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> 对象和 <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> 对象，并为它们的事件建立事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="6478b-119">The constructor also creates a <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> object and an <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> object, and establishes event handlers for their events.</span></span>  
  
 <span data-ttu-id="6478b-120">下面的代码显示了 GamePiece 类的构造函数。</span><span class="sxs-lookup"><span data-stu-id="6478b-120">The following code shows the constructor for the **GamePiece** class.</span></span>  
  
 <span data-ttu-id="6478b-121">[!code-csharp[ManipulationXNA#_GamePiece_Constructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_constructor)]</span><span class="sxs-lookup"><span data-stu-id="6478b-121">[!code-csharp[ManipulationXNA#_GamePiece_Constructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_constructor)]</span></span>  
  
## <a name="capturing-mouse-input"></a><span data-ttu-id="6478b-122">捕获鼠标输入</span><span class="sxs-lookup"><span data-stu-id="6478b-122">Capturing Mouse Input</span></span>  
 <span data-ttu-id="6478b-123">UpdateFromMouse 方法负责检测在鼠标位于游戏块边界内时按下鼠标按钮的时间，并且用于检测释放鼠标按钮的时间。</span><span class="sxs-lookup"><span data-stu-id="6478b-123">The **UpdateFromMouse** method is responsible for detecting when a mouse button is pressed while the mouse is within the boundaries of the game piece, and for detecting when the mouse button has been released.</span></span>  
  
 <span data-ttu-id="6478b-124">按下鼠标左键时（鼠标位于块边界内），此方法设置标志以指示此游戏块已捕获鼠标并开始操作处理。</span><span class="sxs-lookup"><span data-stu-id="6478b-124">When the left mouse button is pressed (while the mouse is inside the piece boundaries), this method sets a flag to indicate that this game piece has captured the mouse, and begins manipulation processing.</span></span>  
  
 <span data-ttu-id="6478b-125">通过创建 <xref:System.Windows.Input.Manipulations.Manipulator2D> 对象的数组并将它们传递给 <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> 对象来启动操作处理。</span><span class="sxs-lookup"><span data-stu-id="6478b-125">Manipulation processing is started by creating an array of <xref:System.Windows.Input.Manipulations.Manipulator2D> objects and passing them to the <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> object.</span></span> <span data-ttu-id="6478b-126">这将导致操作处理器评估操控器（在这种情况下为单操控器），并引发操作事件。</span><span class="sxs-lookup"><span data-stu-id="6478b-126">This causes the manipulation processor to evaluate the manipulators (in this case a single manipulator), and raise manipulation events.</span></span>  
  
 <span data-ttu-id="6478b-127">此外，将保存发生拖动的点。</span><span class="sxs-lookup"><span data-stu-id="6478b-127">In addition, the point at which the drag is occurring is saved.</span></span> <span data-ttu-id="6478b-128">随后会在 <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> 事件期间使用它来调整增量转换值，以便游戏块波动成拖动点之后的线。</span><span class="sxs-lookup"><span data-stu-id="6478b-128">This is used later during the <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> event to adjust the delta translation values so that the game piece swings into line behind the drag point.</span></span>  
  
 <span data-ttu-id="6478b-129">最后，此方法返回鼠标捕获的状态。</span><span class="sxs-lookup"><span data-stu-id="6478b-129">Finally, this method returns the state of the mouse capture.</span></span> <span data-ttu-id="6478b-130">这使 [GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md) 对象可在存在多个游戏块时管理捕获。</span><span class="sxs-lookup"><span data-stu-id="6478b-130">This enables the [GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md) object to manage capturing when there are multiple game pieces.</span></span>  
  
 <span data-ttu-id="6478b-131">下面的代码显示了 UpdateFromMouse 方法。</span><span class="sxs-lookup"><span data-stu-id="6478b-131">The following code shows the **UpdateFromMouse** method.</span></span>  
  
 <span data-ttu-id="6478b-132">[!code-csharp[ManipulationXNA#_GamePiece_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_updatefrommouse)]</span><span class="sxs-lookup"><span data-stu-id="6478b-132">[!code-csharp[ManipulationXNA#_GamePiece_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_updatefrommouse)]</span></span>  
  
## <a name="processing-manipulations"></a><span data-ttu-id="6478b-133">处理操作</span><span class="sxs-lookup"><span data-stu-id="6478b-133">Processing Manipulations</span></span>  
 <span data-ttu-id="6478b-134">操作开始时，引发 <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Started> 事件。</span><span class="sxs-lookup"><span data-stu-id="6478b-134">When manipulation begins, the <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Started> event is raised.</span></span> <span data-ttu-id="6478b-135">此事件的处理程序将停止惯性处理（如果发生惯性处理），并将 processInertia 标记设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="6478b-135">The handler for this event stops inertia processing if it is occurring, and sets the *processInertia* flag to `false`.</span></span>  
  
 <span data-ttu-id="6478b-136">[!code-csharp[ManipulationXNA#_GamePiece_OnManipulationStarted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationstarted)]</span><span class="sxs-lookup"><span data-stu-id="6478b-136">[!code-csharp[ManipulationXNA#_GamePiece_OnManipulationStarted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationstarted)]</span></span>  
  
 <span data-ttu-id="6478b-137">由于与操作关联的值发生变化，将引发 <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> 事件。</span><span class="sxs-lookup"><span data-stu-id="6478b-137">As the values associated with the manipulation change, the <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> event is raised.</span></span> <span data-ttu-id="6478b-138">此事件的处理程序使用事件自变量中传递的增量值来对游戏块的位置和旋转值进行更改。</span><span class="sxs-lookup"><span data-stu-id="6478b-138">The handler for this event uses the delta values passed in the event arguments to make changes to the position and rotation values of the game piece.</span></span>  
  
 <span data-ttu-id="6478b-139">[!code-csharp[ManipulationXNA#_GamePiece_OnManipulationDelta](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationdelta)]</span><span class="sxs-lookup"><span data-stu-id="6478b-139">[!code-csharp[ManipulationXNA#_GamePiece_OnManipulationDelta](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationdelta)]</span></span>  
  
 <span data-ttu-id="6478b-140">删除所有与操作关联的操控器（这种情况下为单个操控器）后，操作处理器将引发 <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> 事件。</span><span class="sxs-lookup"><span data-stu-id="6478b-140">When all of the manipulators (in this case, a single manipulator) that are associated with a manipulation are removed, the manipulation processor raises the <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> event.</span></span> <span data-ttu-id="6478b-141">此事件的处理程序通过将惯性处理器的初速度设置为事件自变量报告的初速度来开始惯性处理，并将 processInertia 标志设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="6478b-141">The handler for this event begins inertia processing by setting the initial velocities of the inertia processor to those reported by the event arguments, and sets the *processInertia* flag to `true`.</span></span>  
  
 <span data-ttu-id="6478b-142">[!code-csharp[ManipulationXNA#_GamePiece_OnManipulationCompleted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationcompleted)]</span><span class="sxs-lookup"><span data-stu-id="6478b-142">[!code-csharp[ManipulationXNA#_GamePiece_OnManipulationCompleted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationcompleted)]</span></span>  
  
## <a name="processing-inertia"></a><span data-ttu-id="6478b-143">处理惯性</span><span class="sxs-lookup"><span data-stu-id="6478b-143">Processing Inertia</span></span>  
 <span data-ttu-id="6478b-144">当惯性处理为角速度和线速度、位置（转换）坐标和旋转外推新值时，引发 <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> 事件。</span><span class="sxs-lookup"><span data-stu-id="6478b-144">As inertia processing extrapolates new values for angular and linear velocities, position (translation) coordinates, and rotation, the <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> event is raised.</span></span> <span data-ttu-id="6478b-145">此事件的处理程序使用事件参数中传递的增量值来修改游戏块的位置和旋转。</span><span class="sxs-lookup"><span data-stu-id="6478b-145">The handler for this event uses the delta values passed in the event arguments to modify the position and rotation of the game piece.</span></span>  
  
 <span data-ttu-id="6478b-146">如果新坐标导致游戏块移到视区边界外，则惯性处理速度将被反转。</span><span class="sxs-lookup"><span data-stu-id="6478b-146">If the new coordinates result in the game piece moving beyond the view port boundaries, the velocity of the inertia processing is reversed.</span></span> <span data-ttu-id="6478b-147">这将导致游戏块弹出已遇到的视区边界。</span><span class="sxs-lookup"><span data-stu-id="6478b-147">This causes the game piece to bounce off the view port boundary that it has encountered.</span></span>  
  
 <span data-ttu-id="6478b-148">运行外推法时，不能更改 <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> 对象的属性。</span><span class="sxs-lookup"><span data-stu-id="6478b-148">You cannot change the properties of an <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> object while it is running extrapolation.</span></span> <span data-ttu-id="6478b-149">因此，反转 X 或 Y 速度时，事件处理程序首先通过调用 <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Complete%2A> 方法停止惯性。</span><span class="sxs-lookup"><span data-stu-id="6478b-149">Therefore, when reversing the X or Y velocity, the event handler first stops inertia by calling the <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Complete%2A> method.</span></span> <span data-ttu-id="6478b-150">然后，它将新的初速度值指派为当前速度值（为 sponge 行为进行调整），并将 processInertia 标记设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="6478b-150">It then assigns the new initial velocity values to be the current velocity values (adjusted for sponge behavior), and sets the *processInertia* flag to `true`.</span></span>  
  
 <span data-ttu-id="6478b-151">下面的代码显示 <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> 事件的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="6478b-151">The following code shows the event handler for the <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> event.</span></span>  
  
 <span data-ttu-id="6478b-152">[!code-csharp[ManipulationXNA#_GamePiece_OnInertiaDelta](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_oninertiadelta)]</span><span class="sxs-lookup"><span data-stu-id="6478b-152">[!code-csharp[ManipulationXNA#_GamePiece_OnInertiaDelta](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_oninertiadelta)]</span></span>  
  
 <span data-ttu-id="6478b-153">惯性处理完成后，惯性处理器将引发 <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Completed> 事件。</span><span class="sxs-lookup"><span data-stu-id="6478b-153">When inertia processing is complete, the inertia processor raises the <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Completed> event.</span></span> <span data-ttu-id="6478b-154">此事件的处理程序将 processInertia 标记设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="6478b-154">The handler for this event sets the *processInertia* flag to `false`.</span></span>  
  
 <span data-ttu-id="6478b-155">[!code-csharp[ManipulationXNA#_GamePiece_OnInertiaCompleted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_oninertiacompleted)]</span><span class="sxs-lookup"><span data-stu-id="6478b-155">[!code-csharp[ManipulationXNA#_GamePiece_OnInertiaCompleted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_oninertiacompleted)]</span></span>  
  
 <span data-ttu-id="6478b-156">没有任何迄今存在的逻辑实际导致惯性外推的发生。</span><span class="sxs-lookup"><span data-stu-id="6478b-156">None of the logic presented so far actually causes inertia extrapolation to occur.</span></span> <span data-ttu-id="6478b-157">这是在 ProcessInertia 方法中完成的。</span><span class="sxs-lookup"><span data-stu-id="6478b-157">This is accomplished in the **ProcessInertia** method.</span></span> <span data-ttu-id="6478b-158">从游戏更新循环中反复调用的这一方法（[Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) 方法）检查是否已将 processInertia 标志设置为 `true`，如果是，则调用 <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Process%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="6478b-158">This method, which is called repeatedly from the game update loop (the [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) method) checks to see if the *processInertia* flag is set to `true`, and if so, calls the <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Process%2A> method.</span></span> <span data-ttu-id="6478b-159">调用此方法会导致发生外推，并引发 <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> 事件。</span><span class="sxs-lookup"><span data-stu-id="6478b-159">Calling this method causes extrapolation to occur, and raises the <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> event.</span></span>  
  
 <span data-ttu-id="6478b-160">[!code-csharp[ManipulationXNA#_GamePiece_ProcessInertia](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_processinertia)]</span><span class="sxs-lookup"><span data-stu-id="6478b-160">[!code-csharp[ManipulationXNA#_GamePiece_ProcessInertia](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_processinertia)]</span></span>  
  
 <span data-ttu-id="6478b-161">直到调用了 Draw 方法重载之一，才会实际呈现游戏块。</span><span class="sxs-lookup"><span data-stu-id="6478b-161">The game piece is not actually rendered until one of the Draw method overloads is called.</span></span> <span data-ttu-id="6478b-162">程序会反复从游戏绘制循环中调用此方法的第一个重载（[Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) 方法）。</span><span class="sxs-lookup"><span data-stu-id="6478b-162">The first overload of this method is called repeatedly from the game draw loop (the [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) method).</span></span> <span data-ttu-id="6478b-163">这会使游戏块呈现当前的位置、旋转和比例因子。</span><span class="sxs-lookup"><span data-stu-id="6478b-163">This renders the game piece with the current position, rotation, and scale factors.</span></span>  
  
 <span data-ttu-id="6478b-164">[!code-csharp[ManipulationXNA#_GamePiece_Draw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_draw)]</span><span class="sxs-lookup"><span data-stu-id="6478b-164">[!code-csharp[ManipulationXNA#_GamePiece_Draw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_draw)]</span></span>  
  
## <a name="additional-properties"></a><span data-ttu-id="6478b-165">其他属性</span><span class="sxs-lookup"><span data-stu-id="6478b-165">Additional Properties</span></span>  
 <span data-ttu-id="6478b-166">GamePiece 类使用三个专用属性。</span><span class="sxs-lookup"><span data-stu-id="6478b-166">Three private properties are used by the **GamePiece** class.</span></span>  
  
1.  <span data-ttu-id="6478b-167">Timestamp - 获取操作和惯性处理器将要使用的时间戳值。</span><span class="sxs-lookup"><span data-stu-id="6478b-167">**Timestamp** – Gets a timestamp value to be used by the manipulation and inertia processors.</span></span>  
  
2.  <span data-ttu-id="6478b-168">X - 获取或设置游戏块的 X 坐标。</span><span class="sxs-lookup"><span data-stu-id="6478b-168">**X** – Gets or sets the X coordinate of the game piece.</span></span> <span data-ttu-id="6478b-169">设置时，调整用于命中测试和操作处理器的枢轴位置的边界。</span><span class="sxs-lookup"><span data-stu-id="6478b-169">When setting, adjusts the bounds used for hit testing and the pivot location of the manipulation processor.</span></span>  
  
3.  <span data-ttu-id="6478b-170">Y - 获取或设置游戏块的 Y 坐标。</span><span class="sxs-lookup"><span data-stu-id="6478b-170">**Y** – Gets or sets the Y coordinate of the game piece.</span></span> <span data-ttu-id="6478b-171">设置时，调整用于命中测试和操作处理器的枢轴位置的边界。</span><span class="sxs-lookup"><span data-stu-id="6478b-171">When setting, adjusts the bounds used for hit testing and the pivot location of the manipulation processor.</span></span>  
  
 <span data-ttu-id="6478b-172">[!code-csharp[ManipulationXNA#_GamePiece_PrivateProperties](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_privateproperties)]</span><span class="sxs-lookup"><span data-stu-id="6478b-172">[!code-csharp[ManipulationXNA#_GamePiece_PrivateProperties](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_privateproperties)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6478b-173">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6478b-173">See Also</span></span>  
 <span data-ttu-id="6478b-174">[操作和惯性](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md) </span><span class="sxs-lookup"><span data-stu-id="6478b-174">[Manipulations and Inertia](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md) </span></span>  
 <span data-ttu-id="6478b-175">[在 XNA 应用程序中使用操作和惯性](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md) </span><span class="sxs-lookup"><span data-stu-id="6478b-175">[Using Manipulations and Inertia in an XNA Application](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md) </span></span>  
 <span data-ttu-id="6478b-176">[创建 GamePieceCollection 类](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md) </span><span class="sxs-lookup"><span data-stu-id="6478b-176">[Creating the GamePieceCollection Class](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md) </span></span>  
 [<span data-ttu-id="6478b-177">创建 Game1 类</span><span class="sxs-lookup"><span data-stu-id="6478b-177">Creating the Game1 Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)
