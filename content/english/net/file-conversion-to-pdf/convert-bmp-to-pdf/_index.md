---
title: Convert BMP Images to PDF
linktitle: Convert BMP Images to PDF
second_title: GroupDocs.Conversion .NET API
description: Convert BMP images to PDF seamlessly using GroupDocs.Conversion for .NET. Customizable options for optimal output.
weight: 11
url: /net/file-conversion-to-pdf/convert-bmp-to-pdf/
type: docs
---
# Convert BMP Images to PDF

## Introduction
GroupDocs.Conversion for .NET provides a powerful solution for converting BMP images to PDF format seamlessly. This tutorial will guide you through the process step by step.
### Prerequisites
Before we begin, ensure you have the following:
1. GroupDocs.Conversion for .NET: Install the library by downloading it from the [download link](https://releases.groupdocs.com/conversion/net/).
2. Source BMP File: Prepare the BMP image file that you want to convert.

## Import Namespaces
First, import the necessary namespaces to access the required classes and methods:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Step 1: Set Output Folder and File Name
Define the output folder path and the name for the converted PDF file:
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "bmp-converted-to.pdf");
```
## Step 2: Load Source BMP File
Load the source BMP file using the `Converter` class:
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_BMP))
{
    // Conversion logic goes here
}
```
## Step 3: Configure Conversion Options
Specify the conversion options. In this case, we'll use `PdfConvertOptions` for converting to PDF format:
```csharp
var options = new PdfConvertOptions();
```
## Step 4: Convert BMP to PDF
Perform the conversion and save the converted PDF file:
```csharp
converter.Convert(outputFile, options);
```
## Step 5: Verify Conversion
Check if the conversion is successful and display the output folder path:
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
Congratulations! You've successfully converted a BMP image to PDF using GroupDocs.Conversion for .NET.

## Conclusion
In conclusion, GroupDocs.Conversion for .NET offers a simple yet powerful solution for converting BMP images to PDF format. By following the steps outlined in this tutorial, you can seamlessly integrate this functionality into your .NET applications.
## FAQ's
### Is GroupDocs.Conversion for .NET compatible with all BMP image formats?
GroupDocs.Conversion for .NET supports a wide range of BMP image formats, ensuring compatibility with most BMP files.
### Can I customize the conversion options for more control over the output PDF?
Yes, you can customize various conversion options such as DPI, page size, orientation, and more to tailor the output PDF according to your requirements.
### Does GroupDocs.Conversion for .NET require any additional dependencies?
No, GroupDocs.Conversion for .NET is a standalone library that does not require any additional dependencies for basic conversion tasks.
### Is there a trial version available for testing before purchasing?
Yes, you can download a free trial version from the [releases page](https://releases.groupdocs.com/) to evaluate the library's features before making a purchase.
### Where can I get support or assistance if I encounter any issues?
You can visit the [GroupDocs.Conversion forum](https://forum.groupdocs.com/c/conversion/11) for assistance from the community or contact support directly for personalized help.
