---
title: Convert JPEG to PDF
linktitle: Convert JPEG to PDF
second_title: GroupDocs.Conversion .NET API
description: Convert JPEG to PDF seamlessly using GroupDocs.Conversion for .NET. Follow our step-by-step guide for efficient file format transformation.
type: docs
weight: 12
url: /net/document-conversion/convert-jpeg-to-pdf/
---
## Introduction
In the world of software development, converting files from one format to another is a common task. Whether it's converting images to PDFs, documents to images, or any other file format transformation, having a reliable tool to accomplish this task efficiently is crucial. One such tool is GroupDocs.Conversion for .NET, a powerful library that provides developers with the capability to convert various file formats seamlessly.
## Prerequisites
Before diving into the conversion process using GroupDocs.Conversion for .NET, there are a few prerequisites you need to have in place:
### 1. Install GroupDocs.Conversion for .NET
First and foremost, you need to install the GroupDocs.Conversion for .NET library. You can download the library from the [download page](https://releases.groupdocs.com/conversion/net/) and follow the installation instructions provided.
### 2. Basic Understanding of C#
You should have a basic understanding of the C# programming language as we'll be using it to write code snippets for the conversion process.
### 3. Integrated Development Environment (IDE)
You'll need an IDE such as Visual Studio or JetBrains Rider to write, compile, and run the code examples.
### 4. Source File(s) to Convert
Ensure that you have the source file(s) ready in the format you want to convert from. For example, if you're converting from JPEG to PDF, have the JPEG file(s) available.

## Import Namespaces
Before we delve into the step-by-step process of converting JPEG to PDF using GroupDocs.Conversion for .NET, let's import the necessary namespaces:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

## Step 1: Define Output Folder and File Name
First, define the output folder where the converted PDF file will be saved, and specify the name of the output file:
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "jpeg-converted-to.pdf");
```
## Step 2: Load the Source JPEG File
Next, load the source JPEG file using the `Converter` class provided by GroupDocs.Conversion:
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_JPEG))
{
    // Conversion code will go here
}
```
## Step 3: Set Conversion Options
Set the conversion options according to your requirements. In this case, since we're converting JPEG to PDF, we'll use `PdfConvertOptions`:
```csharp
var options = new PdfConvertOptions();
```
## Step 4: Perform the Conversion
Perform the actual conversion by calling the `Convert` method and passing the output file path along with the conversion options:
```csharp
converter.Convert(outputFile, options);
```
## Step 5: Display Completion Message
Finally, display a message indicating that the conversion process is completed successfully:
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusion
In this tutorial, we've learned how to convert JPEG to PDF using GroupDocs.Conversion for .NET. By following the step-by-step guide and understanding the prerequisites, you can seamlessly integrate file format conversion capabilities into your .NET applications.
## FAQ's
### Is GroupDocs.Conversion for .NET compatible with all .NET frameworks?
Yes, GroupDocs.Conversion for .NET is compatible with various .NET frameworks, including .NET Core and .NET Framework.
### Can I convert multiple files simultaneously using GroupDocs.Conversion for .NET?
Yes, you can convert multiple files simultaneously by implementing parallel processing techniques in your code.
### Does GroupDocs.Conversion for .NET support conversion between all file formats?
GroupDocs.Conversion for .NET supports a wide range of file formats, including but not limited to images, documents, spreadsheets, presentations, and more.
### Is there a trial version available for GroupDocs.Conversion for .NET?
Yes, you can avail of a free trial version from the [website](https://releases.groupdocs.com/).
### Where can I seek help or support regarding GroupDocs.Conversion for .NET?
You can visit the [GroupDocs.Conversion forum](https://forum.groupdocs.com/c/conversion/11) for assistance and support from the community.
