---
title: Lambda 表达式 - C# 编程指南
ms.date: 07/29/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: b86fe4fd91b395498926512650490f8d3a0383a1
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761832"
---
# <a name="lambda-expressions-c-programming-guide"></a>Lambda 表达式（C# 编程指南）

“Lambda 表达式”有如下两种形式：

- [表达式 lambda](#expression-lambdas)，表达式为其主体：

  ```csharp
  (input-parameters) => expression
  ```

- [语句 lambda](#statement-lambdas)，语句块作为其主体：

  ```csharp  
  (input-parameters) => { <sequence-of-statements> }
  ```

使用 [lambda 声明运算符`=>`](../../language-reference/operators/lambda-operator.md) 从其主体中分离 lambda 参数列表。 若要创建 Lambda 表达式，需要在 Lambda 运算符左侧指定输入参数（如果有），然后在另一侧输入表达式或语句块。

任何 Lambda 表达式都可以转换为[委托](../../language-reference/builtin-types/reference-types.md#the-delegate-type)类型。 Lambda 表达式可以转换的委托类型由其参数和返回值的类型定义。 如果 lambda 表达式不返回值，则可以将其转换为 `Action` 委托类型之一；否则，可将其转换为 `Func` 委托类型之一。 例如，有 2 个参数且不返回值的 Lambda 表达式可转换为 <xref:System.Action%602> 委托。 有 1 个参数且不返回值的 Lambda 表达式可转换为 <xref:System.Func%602> 委托。 以下示例中，lambda 表达式 `x => x * x`（指定名为 `x` 的参数并返回 `x` 平方值）将分配给委托类型的变量：

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

表达式 lambda 还可以转换为[表达式树](../concepts/expression-trees/index.md)类型，如下面的示例所示：

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

可在需要委托类型或表达式树的实例的任何代码中使用 lambda 表达式，例如，作为 <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> 方法的参数传递应在后台执行的代码。 用 C# 编写 [LINQ](../../linq/index.md) 时，还可以使用 lambda 表达式，如下例所示：

[!code-csharp-interactive[lambda is argument in LINQ](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

如果使用基于方法的语法在 <xref:System.Linq.Enumerable?displayProperty=nameWithType> 类中（例如，在 LINQ to Objects 和 LINQ to XML 中）调用 <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> 方法，则参数为委托类型 <xref:System.Func%602?displayProperty=nameWithType>。 如果在 <xref:System.Linq.Queryable?displayProperty=nameWithType> 类中（例如，在 LINQ to SQL 中）调用 <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> 方法，则参数类型为表达式树类型 [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>)。 在这两种情况下，都可以使用相同的 lambda 表达式来指定参数值。 尽管通过 Lambda 创建的对象实际具有不同的类型，但其使得 2 个 `Select` 调用看起来类似。
  
## <a name="expression-lambdas"></a>表达式 lambda

表达式位于 `=>` 运算符右侧的 lambda 表达式称为“表达式 lambda”。 表达式 lambda 广泛用于[表达式树](../concepts/expression-trees/index.md)的构造。 表达式 lambda 会返回表达式的结果，并采用以下基本形式：

```csharp
(input-parameters) => expression
```

仅当 lambda 只有一个输入参数时，括号才是可选的；否则括号是必需的。

使用空括号指定零个输入参数：  

[!code-csharp[zero parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

括号内的两个或更多输入参数使用逗号加以分隔：

[!code-csharp[two parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

有时，编译器无法推断输入类型。 可以显式指定类型，如下面的示例所示：

[!code-csharp[explicitly typed parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

输入参数类型必须全部为显式或全部为隐式；否则，便会生成 [CS0748](../../misc/cs0748.md) 编译器错误。

表达式 lambda 的主体可以包含方法调用。 不过，若要创建在 .NET 公共语言运行时的上下文之外（如在 SQL Server 中）计算的表达式树，不得在 lambda 表达式中使用方法调用。 在 .NET 公共语言运行时上下文之外，方法将没有任何意义。

## <a name="statement-lambdas"></a>语句 lambda

语句 lambda 与表达式 lambda 表达式类似，只是语句括在大括号中：

```csharp  
(input-parameters) => { <sequence-of-statements> }
```

语句 lambda 的主体可以包含任意数量的语句；但是，实际上通常不会多于两个或三个。

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

语句 lambda 也不能用于创建表达式目录树。
  
## <a name="async-lambdas"></a>异步 lambda

通过使用 [async](../../language-reference/keywords/async.md) 和 [await](../../language-reference/operators/await.md) 关键字，你可以轻松创建包含异步处理的 lambda 表达式和语句。 例如，下面的 Windows 窗体示例包含一个调用和等待异步方法 `ExampleMethodAsync`的事件处理程序。

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += button1_Click;
    }

    private async void button1_Click(object sender, EventArgs e)
    {
        await ExampleMethodAsync();
        textBox1.Text += "\r\nControl returned to Click event handler.\n";
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

你可以使用异步 lambda 添加同一事件处理程序。 若要添加此处理程序，请在 lambda 参数列表前添加 `async` 修饰符，如下面的示例所示：

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += async (sender, e) =>
        {
            await ExampleMethodAsync();
            textBox1.Text += "\r\nControl returned to Click event handler.\n";
        };
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

有关如何创建和使用异步方法的详细信息，请参阅[使用 Async 和 Await 的异步编程](../concepts/async/index.md)。

## <a name="lambda-expressions-and-tuples"></a>lambda 表达式和元组

自 C# 7.0 起，C# 语言提供对[元组](../../tuples.md)的内置支持。 可以提供一个元组作为 Lambda 表达式的参数，同时 Lambda 表达式也可以返回元组。 在某些情况下，C# 编译器使用类型推理来确定元组组件的类型。

可通过用括号括住用逗号分隔的组件列表来定义元组。 下面的示例使用包含三个组件的元组，将一系列数字传递给 lambda 表达式，此表达式将每个值翻倍，然后返回包含乘法运算结果的元组（内含三个组件）。

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

通常，元组字段命名为 `Item1`、`Item2` 等等。但是，可以使用命名组件定义元组，如以下示例所示。

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

若要详细了解 C# 元组，请参阅 [C# 元组类型](../../tuples.md)。

## <a name="lambdas-with-the-standard-query-operators"></a>含标准查询运算符的 lambda

在其他实现中，LINQ to Objects 有一个输入参数，其类型是泛型委托 <xref:System.Func%601> 系列中的一种。 这些委托使用类型参数来定义输入参数的数量和类型，以及委托的返回类型。 `Func` 委托对于封装用户定义的表达式非常有用，这些表达式将应用于一组源数据中的每个元素。 例如，假设为 <xref:System.Func%602> 委托类型：  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

可以将委托实例化为 `Func<int, bool>` 实例，其中 `int` 是输入参数，`bool` 是返回值。 返回值始终在最后一个类型参数中指定。 例如，`Func<int, string, bool>` 定义包含两个输入参数（`int` 和 `string`）且返回类型为 `bool`的委托。 下面的 `Func` 委托在调用后返回布尔值，以指明输入参数是否等于 5：

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

参数类型为 <xref:System.Linq.Expressions.Expression%601> 时，也可以提供 Lambda 表达式，例如在 <xref:System.Linq.Queryable> 类型内定义的标准查询运算符中提供。 指定 <xref:System.Linq.Expressions.Expression%601> 参数时，lambda 编译为表达式树。
  
下面的示例使用 <xref:System.Linq.Enumerable.Count%2A> 标准查询运算符：

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

编译器可以推断输入参数的类型，或者你也可以显式指定该类型。 这个特殊 lambda 表达式将计算那些除以 2 时余数为 1 的整数的数量 (`n`)。

下面的示例生成一个序列，其中包含 `numbers` 数组中位于 9 之前的所有元素，因为这是序列中第一个不符合条件的数字：

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

以下示例通过将输入参数括在括号中来指定多个输入参数。 此方法返回 `numbers` 数组中的所有元素，直至遇到值小于其在数组中的序号位置的数字为止：

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a>Lambda 表达式中的类型推理

编写 lambda 时，通常不必为输入参数指定类型，因为编译器可以根据 lambda 主体、参数类型以及 C# 语言规范中描述的其他因素来推断类型。 对于大多数标准查询运算符，第一个输入是源序列中的元素类型。 如果要查询 `IEnumerable<Customer>`，则输入变量将被推断为 `Customer` 对象，这意味着你可以访问其方法和属性：  

```csharp
customers.Where(c => c.City == "London");
```

lambda 类型推理的一般规则如下：

- Lambda 包含的参数数量必须与委托类型包含的参数数量相同。

- Lambda 中的每个输入参数必须都能够隐式转换为其对应的委托参数。

- Lambda 的返回值（如果有）必须能够隐式转换为委托的返回类型。
  
请注意，lambda 表达式本身没有类型，因为通用类型系统没有“lambda 表达式”这一固有概念。 不过，有时以一种非正式的方式谈论 lambda 表达式的“类型”会很方便。 在这些情况下，类型是指委托类型或 lambda 表达式所转换到的 <xref:System.Linq.Expressions.Expression> 类型。

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a>捕获 lambda 表达式中的外部变量和变量范围

lambda 可以引用外部变量。 这些变量是在定义 lambda 表达式的方法中或包含 lambda 表达式的类型中的范围内变量。 以这种方式捕获的变量将进行存储以备在 lambda 表达式中使用，即使在其他情况下，这些变量将超出范围并进行垃圾回收。 必须明确地分配外部变量，然后才能在 lambda 表达式中使用该变量。 下面的示例演示这些规则：

[!code-csharp[variable scope](~/samples/snippets/csharp/programming-guide/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

下列规则适用于 lambda 表达式中的变量范围：  

- 捕获的变量将不会被作为垃圾回收，直至引用变量的委托符合垃圾回收的条件。

- 在封闭方法中看不到 lambda 表达式内引入的变量。

- lambda 表达式无法从封闭方法中直接捕获 [in](../../language-reference/keywords/in-parameter-modifier.md)、[ref](../../language-reference/keywords/ref.md) 或 [out](../../language-reference/keywords/out-parameter-modifier.md) 参数。

- lambda 表达式中的 [return](../../language-reference/keywords/return.md) 语句不会导致封闭方法返回。

- 如果相应跳转语句的目标位于 lambda 表达式块之外，lambda 表达式不得包含 [goto](../../language-reference/keywords/goto.md)、[break](../../language-reference/keywords/break.md) 或 [continue](../../language-reference/keywords/continue.md) 语句。 同样，如果目标在块内部，在 lambda 表达式块外部使用跳转语句也是错误的。

## <a name="c-language-specification"></a>C# 语言规范

有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)中的 [匿名函数表达式](~/_csharplang/spec/expressions.md#anonymous-function-expressions)部分。

## <a name="featured-book-chapter"></a>特别推荐书籍章节

[C# 3.0 手册（第三版）：面向 C# 3.0 程序员的超过 250 个解决方案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)中的[委托、事件和 Lambda 表达式](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29)  
  
## <a name="see-also"></a>请参阅

- [C# 编程指南](../index.md)
- [LINQ（语言集成查询）](../concepts/linq/index.md)
- [表达式树](../concepts/expression-trees/index.md)
- [本地函数与 Lambda 表达式](../classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions)
- [Visual Studio 2008 C# 示例（请参阅 LINQ 示例查询文件和 XQuery 程序）](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [递归 lambda 表达式](https://docs.microsoft.com/archive/blogs/madst/recursive-lambda-expressions)
