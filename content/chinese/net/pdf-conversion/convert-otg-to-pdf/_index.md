---
title: 将 OTG 转换为 PDF
linktitle: 将 OTG 转换为 PDF
second_title: GroupDocs.Conversion .NET API
description: 了解如何使用 GroupDocs.Conversion for .NET 将 OTG 文件转换为 PDF。简单、高效、无缝地集成您的项目。
type: docs
weight: 13
url: /zh/net/pdf-conversion/convert-otg-to-pdf/
---
## 介绍
将 OTG（OpenDocument Graphics）文件转换为 PDF 格式可能是一项至关重要的任务，尤其是在处理文档管理系统或跨不同平台共享文件时。在本教程中，我们将指导您完成使用 .NET 的 GroupDocs.Conversion 库将 OTG 文件转换为 PDF 的过程。让我们深入了解吧！
## 先决条件
在我们开始之前，请确保您满足以下先决条件：
1. 适用于 .NET 的 GroupDocs.Conversion：确保您已安装适用于 .NET 的 GroupDocs.Conversion 库。您可以从以下位置下载：[这里](https://releases.groupdocs.com/conversion/net/).
2. OTG 文件：在文档目录中准备好要转换为 PDF 的 OTG 文件。

## 导入命名空间
首先，您需要将必要的命名空间导入到您的 .NET 项目中。 
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## 第1步：设置输出目录和文件名
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "otg-converted-to.pdf");
```
在此步骤中，您定义将保存转换后的 PDF 文件的输出目录。代替`"Your Document Directory"`以及所需输出目录的路径。
## 第 2 步：加载源 OTG 文件并转换为 PDF
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_OTG))
{
    var options = new PdfConvertOptions();
    //保存转换后的 PDF 文件
    converter.Convert(outputFile, options);
}
```
在这里，我们实例化一个新的`Converter`来自 GroupDocs.Conversion 库的对象，传递源 OTG 文件的路径。然后，我们创建`PdfConvertOptions`指定转换选项。最后，我们调用`Convert`方法将 OTG 文件转换为 PDF 格式。
## 第 3 步：检查转换完成情况
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
此步骤通知用户转换过程已成功完成，并提供转换后的 PDF 文件的保存路径。

## 结论
使用 .NET 的 GroupDocs.Conversion 库可以轻松将 OTG 文件转换为 PDF 格式。通过遵循本教程中概述的步骤，您可以将此功能无缝集成到您的 .NET 应用程序中，从而增强文档的互操作性和可访问性。
## 常见问题解答
### GroupDocs.Conversion 可以将 OTG 以外的其他文件格式转换为 PDF 吗？
是的，GroupDocs.Conversion 支持多种文件格式的转换，包括 DOCX、XLSX、PPTX、HTML 等。
### GroupDocs.Conversion适合商业用途吗？
绝对地！ GroupDocs.Conversion 为希望利用其强大的文档转换功能的企业和组织提供商业许可证。
### GroupDocs.Conversion 是否提供技术支持？
是的，GroupDocs 提供专门的技术支持，以帮助用户解决在实施过程中可能遇到的任何疑问或问题。
### 我可以在购买许可证之前尝试 GroupDocs.Conversion 吗？
是的，您可以免费试用 GroupDocs.Conversion 来探索其功能以及与您的要求的兼容性。
### 如何获得 GroupDocs.Conversion 的临时许可证？
您可以通过访问临时许可证从 GroupDocs 获取用于评估目的或短期项目的临时许可证[执照](https://purchase.groupdocs.com/temporary-license/).