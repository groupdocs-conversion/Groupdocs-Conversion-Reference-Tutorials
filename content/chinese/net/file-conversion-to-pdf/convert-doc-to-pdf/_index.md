---
title: 将 DOC Word 文档转换为 PDF
linktitle: 将 DOC Word 文档转换为 PDF
second_title: GroupDocs.Conversion .NET API
description: 使用 GroupDocs.Conversion for .NET 轻松将 DOC Word 文档转换为 PDF。请按照我们的分步指南进行无缝文档转换。
weight: 23
url: /zh/net/file-conversion-to-pdf/convert-doc-to-pdf/
---
## 介绍
在当今的数字时代，将文档从一种格式无缝转换为另一种格式的能力对于企业和个人都至关重要。无论您是处理 Word 文档、PDF 还是其他文件类型，拥有正确的工具都可以发挥重要作用。 GroupDocs.Conversion for .NET 就是这样一个工具，它是一个功能强大的库，使开发人员能够轻松转换文档。
## 先决条件
在使用 GroupDocs.Conversion for .NET 深入了解转换过程之前，请确保满足以下先决条件：
1. 下载并安装 GroupDocs.Conversion for .NET：导航至[下载链接](https://releases.groupdocs.com/conversion/net/)并按照提供的安装说明进行操作。
2. 获取许可证：您需要许可证才能在应用程序中使用 GroupDocs.Conversion for .NET。如果您刚刚开始，您可以利用[临时执照](https://purchase.groupdocs.com/temporary-license/)用于测试目的或购买用于生产使用的许可证。
3. 熟悉 .NET 环境：建议具备 .NET 框架和 C# 编程语言的基本知识并跟随示例进行操作。
4. 访问源文档：确保您拥有要转换的源文档。出于演示目的，我们将 DOC Word 文档转换为 PDF 格式。

## 导入命名空间
在开始转换过程之前，让我们将必要的命名空间导入到我们的 .NET 项目中：
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## 第 1 步：定义输出文件夹和文件
首先，指定要保存转换后的 PDF 文件的输出文件夹以及所需的输出文件名。
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "doc-converted-to.pdf");
```
## 第2步：加载源DOC文件
接下来，使用 GroupDocs.Conversion.Converter 类加载源 DOC 文件。
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_DOC))
```
## 步骤 3：配置转换选项
根据您的要求配置转换选项。为了将 DOC 转换为 PDF，我们将使用 PdfConvertOptions。
```csharp
var options = new PdfConvertOptions();
```
## 第 4 步：执行转换
通过调用转换器对象的 Convert 方法，传递输出文件路径和转换选项来执行转换过程。
```csharp
converter.Convert(outputFile, options);
```
## 第 5 步：验证转换是否完成
转换完成后，将显示成功消息以及输出文件夹位置。
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

## 结论
GroupDocs.Conversion for .NET 简化了在各种格式之间转换文档的过程。通过遵循本教程中概述的步骤，您可以轻松地将 DOC Word 文档无缝转换为 PDF。
## 常见问题解答
### GroupDocs.Conversion for .NET 是否与所有版本的 .NET 兼容？
GroupDocs.Conversion for .NET 与 .NET Framework 2.0 及更高版本兼容，包括 .NET Core 和 .NET 5+。
### 我可以使用 GroupDocs.Conversion for .NET 同时转换多个文档吗？
是的，GroupDocs.Conversion for .NET 支持批量转换，允许您一次性转换多个文档。
### GroupDocs.Conversion for .NET 是否需要互联网连接？
不需要，GroupDocs.Conversion for .NET 在您的计算机上本地运行，不需要 Internet 连接即可进行转换。
### 我可以根据特定要求自定义转换选项吗？
是的，GroupDocs.Conversion for .NET 提供了广泛的选项来自定义转换过程以满足您的特定需求。
### GroupDocs.Conversion for .NET 是否提供技术支持？
是的，可通过以下方式获得 GroupDocs.Conversion for .NET 的技术支持：[论坛](https://forum.groupdocs.com/c/conversion/11)您可以在这里寻求社区和专家的帮助和指导。