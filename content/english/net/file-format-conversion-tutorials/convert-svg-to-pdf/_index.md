---
title: Convert SVG to PDF
linktitle: Convert SVG to PDF
second_title: GroupDocs.Conversion .NET API
description: Learn how to convert SVG to PDF using GroupDocs.Conversion for .NET effortlessly. Streamline your document management process.
weight: 15
url: /net/file-format-conversion-tutorials/convert-svg-to-pdf/
---

# Convert SVG to PDF

## Introduction
In the world of programming, converting files from one format to another is a common task. Whether you're dealing with images, documents, or other media, being able to seamlessly convert between formats is crucial. In this tutorial, we'll delve into how to convert SVG (Scalable Vector Graphics) files to PDF (Portable Document Format) using GroupDocs.Conversion for .NET.
## Prerequisites
Before diving into the conversion process, make sure you have the following prerequisites set up:
### 1. Install GroupDocs.Conversion for .NET
Ensure you have GroupDocs.Conversion for .NET installed in your development environment. If you haven't already, you can download it from the [website](https://releases.groupdocs.com/conversion/net/).
### 2. Obtain a Sample SVG File
You'll need a sample SVG file to convert to PDF. If you don't have one, you can easily find SVG files online or create one using various graphic design tools.
### 3. Basic Understanding of C#
Familiarize yourself with C# programming language basics, as we'll be using it to write the conversion code.

## Import Namespaces
First, let's import the necessary namespaces:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Step 1: Define Output Folder and File
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "svg-converted-to.pdf");
```
Ensure to replace `"Your Document Directory"` with the path to your desired output directory.
## Step 2: Load the Source SVG File
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_SVG))
{
    // Conversion code goes here
}
```
Replace `Constants.SAMPLE_SVG` with the path to your SVG file.
## Step 3: Set Conversion Options
```csharp
var options = new PdfConvertOptions();
```
Here, we're setting up conversion options specifically for PDF output. You can customize these options based on your requirements.
## Step 4: Perform the Conversion
```csharp
converter.Convert(outputFile, options);
```
This line executes the conversion process, taking the source SVG file and converting it to PDF with the specified options.
## Step 5: Check Conversion Completion
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
This line outputs a message confirming the successful completion of the conversion process, along with the directory where the converted PDF file is located.

## Conclusion
In this tutorial, we've learned how to convert SVG files to PDF using GroupDocs.Conversion for .NET. By following the step-by-step guide and ensuring you have the prerequisites in place, you can seamlessly incorporate file format conversion capabilities into your .NET applications.
## FAQ's
### Is GroupDocs.Conversion for .NET compatible with all .NET frameworks?
Yes, GroupDocs.Conversion for .NET supports multiple .NET frameworks, including .NET Core and .NET Framework.
### Can I customize the conversion options for specific output formats?
Absolutely! GroupDocs.Conversion for .NET provides extensive customization options for each supported output format.
### Does GroupDocs.Conversion for .NET support batch conversion?
Yes, you can convert multiple files simultaneously using GroupDocs.Conversion for .NET.
### Is there a trial version available for testing purposes?
Yes, you can access a free trial version from [here](https://releases.groupdocs.com/).
### Where can I get technical support for GroupDocs.Conversion for .NET?
You can find technical support and assistance on the GroupDocs forum [here](https://forum.groupdocs.com/c/conversion/11).
