---
title: 将 PPTX 转换为 PDF
linktitle: 将 PPTX 转换为 PDF
second_title: GroupDocs.Conversion .NET API
description: 了解如何使用 GroupDocs.Conversion for .NET 将 PowerPoint 演示文稿 (PPTX) 转换为 PDF 格式。简单高效的转换过程。
type: docs
weight: 29
url: /zh/net/pdf-conversion/convert-pptx-to-pdf/
---
## 介绍
在本教程中，我们将逐步介绍使用 .NET 的 GroupDocs.Conversion 库将 PowerPoint 演示文稿 (PPTX) 文件转换为可移植文档格式 (PDF) 的过程。请按照以下步骤来实现此转换。
## 先决条件
在我们开始之前，请确保您满足以下先决条件：
1.  GroupDocs.Conversion for .NET 库：确保您已安装 GroupDocs.Conversion for .NET 库。您可以从以下位置下载：[这里](https://releases.groupdocs.com/conversion/net/).
2. 开发环境：使用必要的工具（例如 Visual Studio 或任何其他 .NET IDE）设置开发环境。

## 导入命名空间
在项目中包含必要的命名空间以访问 GroupDocs.Conversion 功能。
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## 第 1 步：设置输出文件夹和文件名
首先，定义保存转换后的 PDF 文件的输出文件夹，并指定输出 PDF 文件的名称。
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "pptx-converted-to.pdf");
```
## 第 2 步：加载源 PPTX 文件
使用 GroupDocs.Conversion 库加载源 PowerPoint 演示文稿 (PPTX) 文件。
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PPTX))
{
    //转换逻辑将放置在这里
}
```
## 步骤 3：指定转换选项
定义转换选项。在本例中，我们要转换为 PDF 格式，因此创建一个实例`PdfConvertOptions`.
```csharp
var options = new PdfConvertOptions();
```
## 第 4 步：执行转换
使用以下命令执行转换过程`Convert`方法并传递输出文件路径以及转换选项。
```csharp
converter.Convert(outputFile, options);
```
## 第 5 步：检查输出
转换成功完成后，显示一条消息，指示完成和输出文件的位置。
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## 结论
在本教程中，我们学习了如何使用 .NET 的 GroupDocs.Conversion 库将 PowerPoint 演示文稿 (PPTX) 文件转换为可移植文档格式 (PDF)。通过执行上述步骤，您可以在 .NET 应用程序中轻松执行此转换。
## 常见问题解答
### 问：GroupDocs.Conversion 是否与所有版本的 .NET 兼容？
答：是的，GroupDocs.Conversion 支持 .NET Framework 2.0 及更高版本，包括 .NET Core 和 .NET Standard。
### 问：我可以将文件转换为 PDF 以外的格式吗？
答：是的，GroupDocs.Conversion 支持多种文档格式转换，包括 Word、Excel、HTML 等。
### 问：GroupDocs.Conversion 提供免费试用吗？
答：是的，您可以访问 GroupDocs.Conversion 的免费试用版：[这里](https://releases.groupdocs.com/).
### 问：如何获得 GroupDocs.Conversion 的支持？
答：您可以从 GroupDocs 社区论坛获得支持[这里](https://forum.groupdocs.com/c/conversion/11).
### 问：GroupDocs.Conversion 是否有可用的临时许可证？
答：是的，您可以从以下位置获取 GroupDocs.Conversion 的临时许可证：[这里](https://purchase.groupdocs.com/temporary-license/).