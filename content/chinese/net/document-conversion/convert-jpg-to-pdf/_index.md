---
title: 将 JPG 转换为 PDF
linktitle: 将 JPG 转换为 PDF
second_title: GroupDocs.Conversion .NET API
description: 使用 GroupDocs.Conversion for .NET 轻松将 JPG 转换为 PDF。按照此分步教程进行无缝文档转换。
weight: 14
url: /zh/net/document-conversion/convert-jpg-to-pdf/
---

# 将 JPG 转换为 PDF

## 介绍

您是否希望使用 GroupDocs.Conversion for .NET 轻松将 JPG 文件转换为 PDF？本教程将逐步指导您完成该过程。 GroupDocs.Conversion for .NET 是一个功能强大的 API，可让您轻松地将各种文档格式（包括图像）无缝转换为 PDF。让我们深入了解吧！

## 先决条件

在我们开始之前，请确保您满足以下先决条件：

1.  GroupDocs.Conversion for .NET：确保您已安装 GroupDocs.Conversion for .NET。您可以从以下位置下载：[这里](https://releases.groupdocs.com/conversion/net/).
2. 开发环境：设置开发环境，例如 Visual Studio，以及 .NET Framework 或 .NET Core。
3. 示例 JPG 文件：准备要转换为 PDF 的示例 JPG 文件。

## 导入命名空间

首先，让我们导入必要的名称空间：

```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

现在，让我们将转换过程分解为简单的步骤：

## 第 1 步：定义输出目录和文件名

```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "jpg-converted-to.pdf");
```

确保指定要保存转换后的 PDF 文件的目录以及所需的输出文件名。

## 第 2 步：加载源 JPG 文件并转换为 PDF

```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_JPG))
{
    var options = new PdfConvertOptions();
    converter.Convert(outputFile, options);
}
```

初始化`Converter`对象，其中包含示例 JPG 文件的路径。然后，配置转换选项，例如指定 PDF 转换选项。最后，致电`Convert`方法，传递输出文件路径和转换选项。

## 步骤 3：显示转换完成消息

```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

转换完成后，显示一条消息，指示转换成功以及转换后的 PDF 文件的位置。

## 结论

使用 GroupDocs.Conversion for .NET 将 JPG 文件转换为 PDF 非常简单，只需几行代码。通过遵循本教程，您可以将文档转换功能无缝集成到您的 .NET 应用程序中。

## 常见问题解答

### 问：我可以同时将多个 JPG 文件转换为 PDF 吗？

答：是的，您可以通过迭代每个文件并执行教程中描述的转换过程，将多个 JPG 文件转换为 PDF。

### 问：GroupDocs.Conversion 是否支持除 JPG 之外的其他图像格式？

答：是的，GroupDocs.Conversion 支持多种图像格式，例如 PNG、TIFF、BMP 和 GIF 等。

### 问：我可以使用转换选项自定义输出 PDF 文件吗？

答：当然！ GroupDocs.Conversion 提供了广泛的转换选项，允许您根据您的要求自定义输出 PDF。

### 问：GroupDocs.Conversion for .NET 是否有试用版？

答：是的，您可以访问 GroupDocs.Conversion for .NET 的免费试用版：[这里](https://releases.groupdocs.com/).

### 问：如果我在转换过程中遇到任何问题，可以到哪里寻求帮助？

答：如果您遇到任何问题或对 GroupDocs.Conversion for .NET 有疑问，请随时访问[GroupDocs.Conversion 论坛](https://forum.groupdocs.com/c/conversion/11)寻求帮助。