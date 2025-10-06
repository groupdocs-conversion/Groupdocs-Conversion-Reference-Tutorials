---
title: Convert PPTX to PDF
linktitle: Convert PPTX to PDF
second_title: GroupDocs.Conversion .NET API
description: Learn how to convert PowerPoint presentations (PPTX) to PDF format using GroupDocs.Conversion for .NET. Easy and efficient conversion process.
weight: 29
url: /net/pdf-conversion/convert-pptx-to-pdf/
type: docs
---
# Convert PPTX to PDF

## Introduction
In this tutorial, we'll walk through the process of converting a PowerPoint presentation (PPTX) file to a Portable Document Format (PDF) using the GroupDocs.Conversion library for .NET. Follow the steps below to achieve this conversion.
## Prerequisites
Before we begin, ensure you have the following prerequisites:
1. GroupDocs.Conversion for .NET Library: Make sure you have installed the GroupDocs.Conversion for .NET library. You can download it from [here](https://releases.groupdocs.com/conversion/net/).
2. Development Environment: Set up a development environment with the necessary tools like Visual Studio or any other .NET IDE.

## Import Namespaces
Include the necessary namespaces in your project to access the GroupDocs.Conversion functionalities.
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Step 1: Set Output Folder and File Name
First, define the output folder where the converted PDF file will be saved, and specify the name of the output PDF file.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "pptx-converted-to.pdf");
```
## Step 2: Load the Source PPTX File
Load the source PowerPoint presentation (PPTX) file using the GroupDocs.Conversion library.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PPTX))
{
    // Conversion logic will be placed here
}
```
## Step 3: Specify Conversion Options
Define the conversion options. In this case, we're converting to PDF format, so create an instance of `PdfConvertOptions`.
```csharp
var options = new PdfConvertOptions();
```
## Step 4: Perform the Conversion
Execute the conversion process using the `Convert` method and pass the output file path along with the conversion options.
```csharp
converter.Convert(outputFile, options);
```
## Step 5: Check Output
After conversion is completed successfully, display a message indicating the completion and the location of the output file.
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusion
In this tutorial, we learned how to convert a PowerPoint presentation (PPTX) file to a Portable Document Format (PDF) using the GroupDocs.Conversion library for .NET. By following the steps outlined above, you can easily perform this conversion in your .NET applications.
## FAQ's
### Q: Is GroupDocs.Conversion compatible with all versions of .NET?
A: Yes, GroupDocs.Conversion supports .NET Framework 2.0 and higher, including .NET Core and .NET Standard.
### Q: Can I convert files to formats other than PDF?
A: Yes, GroupDocs.Conversion supports a wide range of document formats for conversion, including Word, Excel, HTML, and more.
### Q: Does GroupDocs.Conversion offer any free trial?
A: Yes, you can access a free trial of GroupDocs.Conversion from [here](https://releases.groupdocs.com/).
### Q: How can I get support for GroupDocs.Conversion?
A: You can get support from the GroupDocs community forum [here](https://forum.groupdocs.com/c/conversion/11).
### Q: Is there a temporary license available for GroupDocs.Conversion?
A: Yes, you can obtain a temporary license for GroupDocs.Conversion from [here](https://purchase.groupdocs.com/temporary-license/).
