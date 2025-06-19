---
"description": "了解如何使用 GroupDocs.Conversion for .NET 将 PowerPoint 演示文稿 (PPTX) 转换为 PDF 格式。转换过程简单高效。"
"linktitle": "将PPTX转换为PDF"
"second_title": "GroupDocs.转换 .NET API"
"title": "将PPTX转换为PDF"
"url": "/zh/net/pdf-conversion/convert-pptx-to-pdf/"
"weight": 29
---

# 将PPTX转换为PDF

## 介绍
在本教程中，我们将演示如何使用 .NET 的 GroupDocs.Conversion 库将 PowerPoint 演示文稿 (PPTX) 文件转换为可移植文档格式 (PDF)。请按照以下步骤完成此转换。
## 先决条件
在开始之前，请确保您满足以下先决条件：
1. GroupDocs.Conversion for .NET 库：请确保您已安装 GroupDocs.Conversion for .NET 库。您可以从此处下载 [这里](https://releases。groupdocs.com/conversion/net/).
2. 开发环境：使用必要的工具（如 Visual Studio 或任何其他 .NET IDE）设置开发环境。

## 导入命名空间
在您的项目中包含必要的命名空间以访问 GroupDocs.Conversion 功能。
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## 步骤 1：设置输出文件夹和文件名
首先，定义将保存转换后的 PDF 文件的输出文件夹，并指定输出 PDF 文件的名称。
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "pptx-converted-to.pdf");
```
## 步骤2：加载源PPTX文件
使用 GroupDocs.Conversion 库加载源 PowerPoint 演示文稿 (PPTX) 文件。
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PPTX))
{
    // 转换逻辑将放在这里
}
```
## 步骤 3：指定转换选项
定义转换选项。在本例中，我们将转换为 PDF 格式，因此创建一个 `PdfConvertOptions`。
```csharp
var options = new PdfConvertOptions();
```
## 步骤4：执行转换
使用执行转换过程 `Convert` 方法并传递输出文件路径以及转换选项。
```csharp
converter.Convert(outputFile, options);
```
## 步骤5：检查输出
转换成功完成后，显示一条消息，指示完成和输出文件的位置。
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## 结论
在本教程中，我们学习了如何使用 .NET 的 GroupDocs.Conversion 库将 PowerPoint 演示文稿 (PPTX) 文件转换为可移植文档格式 (PDF)。按照上面概述的步骤，您可以轻松地在 .NET 应用程序中执行此转换。
## 常见问题解答
### 问：GroupDocs.Conversion 是否与所有版本的 .NET 兼容？
答：是的，GroupDocs.Conversion 支持 .NET Framework 2.0 及更高版本，包括 .NET Core 和 .NET Standard。
### 问：我可以将文件转换为 PDF 以外的格式吗？
答：是的，GroupDocs.Conversion 支持多种文档格式转换，包括 Word、Excel、HTML 等。
### 问：GroupDocs.Conversion 提供免费试用吗？
答：是的，您可以从以下网址免费试用 GroupDocs.Conversion [这里](https://releases。groupdocs.com/).
### 问：如何获得 GroupDocs.Conversion 的支持？
答：您可以从 GroupDocs 社区论坛获得支持 [这里](https://forum。groupdocs.com/c/conversion/11).
### 问：GroupDocs.Conversion 有临时许可证吗？
答：是的，您可以从以下位置获取 GroupDocs.Conversion 的临时许可证 [这里](https://purchase。groupdocs.com/temporary-license/).