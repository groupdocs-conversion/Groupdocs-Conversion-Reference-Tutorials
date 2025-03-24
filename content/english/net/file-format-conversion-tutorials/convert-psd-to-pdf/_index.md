---
title: Convert PSD to PDF
linktitle: Convert PSD to PDF
second_title: GroupDocs.Conversion .NET API
description: Learn how to convert PSD files to PDF effortlessly using GroupDocs.Conversion for .NET. Follow our step-by-step guide.
weight: 10
url: /net/file-format-conversion-convert-psd-to-pdf/
---

# Convert PSD to PDF

## Introduction
In this tutorial, we'll guide you through the process of converting PSD (Photoshop Document) files to PDF format using the GroupDocs.Conversion library for .NET. By following these step-by-step instructions, you'll be able to seamlessly convert your PSD files to PDFs with ease.
## Prerequisites
Before we begin, ensure that you have the following prerequisites set up:
1. Installation of GroupDocs.Conversion Library: Make sure you have installed the GroupDocs.Conversion library for .NET. You can download it from the [website](https://releases.groupdocs.com/conversion/net/).
2. Access to PSD Files: Have access to the PSD files that you want to convert to PDF.

## Import Namespaces
Before diving into the conversion process, import the necessary namespaces:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Step 1: Define Output Folder and File
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "psd-converted-to.pdf");
```
In this step, specify the output folder where you want to save the converted PDF file. Ensure that you replace `"Your Document Directory"` with the actual directory path.
## Step 2: Load the Source PSD File
```csharp
using (var converter = new GroupDocs.Conversion.Converter("Path_to_your_PSD_file.psd"))
{
    var options = new PdfConvertOptions();
    // Save converted PDF file
    converter.Convert(outputFile, options);
}
```
Here, you'll initialize the `Converter` object with the path to your PSD file. Replace `"Path_to_your_PSD_file.psd"` with the actual path to your PSD file. Then, create an instance of `PdfConvertOptions` to specify conversion settings. Finally, call the `Convert` method to convert the PSD file to PDF and save it to the specified output file.
## Step 3: Check Conversion Completion
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```
This step simply prints a message to the console confirming the successful completion of the conversion process and indicates the location where the converted PDF file is saved.

## Conclusion
In this tutorial, we've demonstrated how to convert PSD files to PDF format using the GroupDocs.Conversion library for .NET. By following the provided steps, you can effortlessly convert your PSD files to PDFs, enabling easier sharing and viewing of your documents.
## FAQ's

### Can I convert multiple PSD files at once using GroupDocs.Conversion?
Yes, you can batch convert multiple PSD files to PDF or other formats using GroupDocs.Conversion.

### Does GroupDocs.Conversion support other output formats apart from PDF?
Yes, GroupDocs.Conversion supports a wide range of output formats including DOCX, XLSX, PPTX, JPEG, PNG, and more.

### Is GroupDocs.Conversion compatible with different versions of .NET?
Yes, GroupDocs.Conversion is compatible with various versions of .NET including .NET Core and .NET Framework.

### Can I customize the conversion options for more control over the output?
Yes, GroupDocs.Conversion provides extensive options for customization such as specifying page size, orientation, quality, and more.

### Is there a trial version available for testing before purchasing?
Yes, you can get a free trial version of GroupDocs.Conversion from the [website](https://releases.groupdocs.com/conversion/net/) to test its features before making a purchase.
