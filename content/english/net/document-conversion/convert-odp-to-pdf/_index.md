---
title: Convert ODP to PDF
linktitle: Convert ODP to PDF
second_title: GroupDocs.Conversion .NET API
description: Learn how to convert ODP to PDF using GroupDocs.Conversion for .NET. Follow our step-by-step guide for seamless document conversion.
type: docs
weight: 28
url: /net/document-conversion/convert-odp-to-pdf/
---
## Introduction
GroupDocs.Conversion for .NET is a powerful API that allows developers to seamlessly convert various document formats in their .NET applications. In this tutorial, we'll guide you through the process of converting an ODP (OpenDocument Presentation) file to PDF format using GroupDocs.Conversion for .NET.
## Prerequisites
Before we begin, make sure you have the following prerequisites:
1. GroupDocs.Conversion for .NET SDK: Ensure that you have downloaded and installed the GroupDocs.Conversion for .NET SDK. You can download it from the [download page](https://releases.groupdocs.com/conversion/net/).
2. .NET Development Environment: You should have a .NET development environment set up on your machine.
3. Source ODP File: Prepare the ODP file that you want to convert to PDF.

## Import Namespaces
First, import the necessary namespaces to your C# code:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Step 1: Define Output File Path
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "odp-converted-to.pdf");
```
Replace `"Your Document Directory"` with the path where you want to save the converted PDF file.
## Step 2: Load the Source ODP File
```csharp
using (var converter = new GroupDocs.Conversion.Converter("path/to/your/source.odp"))
{
    // Conversion code will go here
}
```
Replace `"path/to/your/source.odp"` with the actual path to your source ODP file.
## Step 3: Set Conversion Options
```csharp
var options = new PdfConvertOptions();
```
Here, you can customize conversion options according to your requirements. For example, you can set PDF conversion settings like page size, margins, quality, etc.
## Step 4: Perform the Conversion
```csharp
converter.Convert(outputFile, options);
```
This line of code initiates the conversion process from ODP to PDF using the specified options.
## Step 5: Display Success Message
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```
This line displays a success message along with the output folder where the converted PDF file is saved.

## Conclusion
In this tutorial, we learned how to convert an ODP file to PDF using GroupDocs.Conversion for .NET. By following the provided steps, you can easily integrate document conversion capabilities into your .NET applications.
## FAQ's
### Can GroupDocs.Conversion for .NET handle other document formats?
Yes, GroupDocs.Conversion for .NET supports a wide range of document formats including Word, Excel, PowerPoint, PDF, and more.
### Is there a free trial available for GroupDocs.Conversion for .NET?
Yes, you can avail of a free trial from the [website](https://releases.groupdocs.com/).
### How can I get technical support for GroupDocs.Conversion for .NET?
You can get technical support from the [support forum](https://forum.groupdocs.com/c/conversion/11).
### Can I customize the conversion options according to my requirements?
Yes, GroupDocs.Conversion for .NET provides extensive options for customization to meet your specific needs.
### Where can I purchase a license for GroupDocs.Conversion for .NET?
You can purchase a license from the [purchase page](https://purchase.groupdocs.com/buy).
