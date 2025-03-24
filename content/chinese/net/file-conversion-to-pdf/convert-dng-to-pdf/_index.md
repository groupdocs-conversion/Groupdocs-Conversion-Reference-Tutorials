---
title: 将 DNG 图像转换为 PDF
linktitle: 将 DNG 图像转换为 PDF
second_title: GroupDocs.Conversion .NET API
description: 了解如何使用 GroupDocs.Conversion for .NET 将 DNG 图像轻松转换为 PDF。请按照我们的分步指南进行无缝转换。
weight: 21
url: /zh/net/file-conversion-to-pdf/convert-dng-to-pdf/
---

# 将 DNG 图像转换为 PDF

## 介绍
在本教程中，我们将指导您完成使用 GroupDocs.Conversion for .NET 将 DNG 图像转换为 PDF 的过程。 DNG（数字负片）是一种用于数码摄影的文件格式。通过将 DNG 图像转换为 PDF，您可以轻松地以更普遍接受的格式共享或存储它们。
## 先决条件
在开始之前，请确保您具备以下条件：
1.  GroupDocs.Conversion for .NET：下载并安装适用于 .NET 的 GroupDocs.Conversion 库[这里](https://releases.groupdocs.com/conversion/net/).
2. 源 DNG 文件：您需要一个要转换为 PDF 的 DNG 图像文件。
3. 开发环境：确保您已设置 .NET 开发环境。

## 导入命名空间
首先，您需要将必要的命名空间导入到您的项目中。将以下 using 指令添加到您的代码文件中：
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## 第 1 步：加载源 DNG 文件
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "dng-converted-to.pdf");
//加载源 DNG 文件
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_DNG))
{
    //继续转换过程
}
```
在此步骤中，您定义将保存转换后的 PDF 文件的输出文件夹。确保更换`"Your Document Directory"`以及您所需目录的路径。然后，指定输出 PDF 文件的名称和路径。
## 步骤 2：将 DNG 转换为 PDF
```csharp
var options = new PdfConvertOptions();
//保存转换后的 PDF 文件
converter.Convert(outputFile, options);
```
在这里，您创建一个实例`PdfConvertOptions`如果需要，可以设置 PDF 转换的任何特定选项。然后，您调用`Convert`的方法`converter`对象，传递输出文件路径和转换选项。
## 第 3 步：处理转换完成
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
转换过程完成后，您将显示一条成功消息以及转换后的 PDF 文件所在的目录。

## 结论
总之，使用 GroupDocs.Conversion for .NET 可以轻松地将 DNG 图像转换为 PDF。通过遵循本教程中概述的简单步骤，您可以有效地将 DNG 文件转换为 PDF 格式，使它们更易于访问和共享。
## 常见问题解答
### GroupDocs.Conversion for .NET 是否与所有版本的 .NET 兼容？
是的，GroupDocs.Conversion for .NET 与 .NET Framework 4.6.1 及更高版本以及 .NET Core 2.0 及更高版本兼容。
### 我可以同时将多个 DNG 文件转换为 PDF 吗？
是的，您可以通过迭代每个文件并对每个文件执行转换过程，将多个 DNG 文件转换为 PDF。
### 可转换的 DNG 文件的大小有限制吗？
GroupDocs.Conversion for .NET 对可转换的 DNG 文件的大小没有具体限制。但是，性能可能会根据输入文件的大小和复杂性而有所不同。
### 我可以自定义 PDF 输出的转换选项吗？
是的，您可以使用以下命令自定义各种选项，例如页面大小、方向、压缩等`PdfConvertOptions`由 GroupDocs.Conversion for .NET 提供的类。
### GroupDocs.Conversion for .NET 是否提供技术支持？
是的，可以通过 GroupDocs 论坛获得技术支持[这里](https://forum.groupdocs.com/c/conversion/11)，您可以在这里提出问题并获得专家的帮助。