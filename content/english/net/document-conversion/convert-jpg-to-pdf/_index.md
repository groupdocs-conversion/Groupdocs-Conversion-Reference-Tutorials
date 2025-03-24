---
title: Convert JPG to PDF
linktitle: Convert JPG to PDF
second_title: GroupDocs.Conversion .NET API
description: Convert JPG to PDF effortlessly using GroupDocs.Conversion for .NET. Follow this step-by-step tutorial for seamless document conversion.
weight: 14
url: /net/document-conversion/convert-jpg-to-pdf/
---

# Convert JPG to PDF

## Introduction

Are you looking to convert JPG files to PDF effortlessly using GroupDocs.Conversion for .NET? This tutorial will guide you through the process step by step. GroupDocs.Conversion for .NET is a powerful API that allows you to seamlessly convert various document formats, including images, to PDF with ease. Let's dive in!

## Prerequisites

Before we begin, ensure you have the following prerequisites:

1. GroupDocs.Conversion for .NET: Make sure you have installed GroupDocs.Conversion for .NET. You can download it from [here](https://releases.groupdocs.com/conversion/net/).
2. Development Environment: Have a development environment set up, such as Visual Studio, along with .NET Framework or .NET Core.
3. Sample JPG File: Prepare a sample JPG file that you want to convert to PDF.

## Import Namespaces

First, let's import the necessary namespaces:

```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

Now, let's break down the conversion process into simple steps:

## Step 1: Define Output Directory and File Name

```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "jpg-converted-to.pdf");
```

Ensure to specify the directory where you want to save the converted PDF file and the desired output file name.

## Step 2: Load the Source JPG File and Convert to PDF

```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_JPG))
{
    var options = new PdfConvertOptions();
    converter.Convert(outputFile, options);
}
```

Initialize the `Converter` object with the path to your sample JPG file. Then, configure conversion options, such as specifying PDF conversion options. Finally, call the `Convert` method, passing the output file path and conversion options.

## Step 3: Display Conversion Completion Message

```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

After the conversion is completed, display a message indicating the successful conversion and the location of the converted PDF file.

## Conclusion

Converting JPG files to PDF using GroupDocs.Conversion for .NET is straightforward with just a few lines of code. By following this tutorial, you can seamlessly integrate document conversion capabilities into your .NET applications.

## FAQ's

### Q: Can I convert multiple JPG files to PDF simultaneously?

A: Yes, you can convert multiple JPG files to PDF by iterating over each file and performing the conversion process described in the tutorial.

### Q: Does GroupDocs.Conversion support other image formats besides JPG?

A: Yes, GroupDocs.Conversion supports various image formats such as PNG, TIFF, BMP, and GIF, among others.

### Q: Can I customize the output PDF file using conversion options?

A: Absolutely! GroupDocs.Conversion provides a wide range of conversion options allowing you to customize the output PDF according to your requirements.

### Q: Is there a trial version available for GroupDocs.Conversion for .NET?

A: Yes, you can access a free trial version of GroupDocs.Conversion for .NET from [here](https://releases.groupdocs.com/).

### Q: Where can I seek help if I encounter any issues during the conversion process?

A: If you encounter any issues or have questions regarding GroupDocs.Conversion for .NET, feel free to visit the [GroupDocs.Conversion forum](https://forum.groupdocs.com/c/conversion/11) for assistance.
