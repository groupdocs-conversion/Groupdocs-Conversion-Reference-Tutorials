---
title: Convert VSDM to PDF
linktitle: Convert VSDM to PDF
second_title: GroupDocs.Conversion .NET API
description: Learn how to convert VSDM files to PDF format using GroupDocs.Conversion for .NET. Follow our step-by-step guide for seamless conversion.
weight: 26
url: /net/file-format-conversion-tutorials/convert-vsdm-to-pdf/
---

# Convert VSDM to PDF

## Introduction
In this tutorial, we'll guide you through the process of converting VSDM (Visio Macro-Enabled Drawing) files to PDF format using the GroupDocs.Conversion library for .NET. We'll break down each step into detailed instructions to ensure a smooth conversion process.
## Prerequisites
Before we begin, make sure you have the following prerequisites:
1. GroupDocs.Conversion for .NET: You need to have the GroupDocs.Conversion library installed in your .NET environment. You can download it from [here](https://releases.groupdocs.com/conversion/net/).
2. Visual Studio: Ensure you have Visual Studio or any other compatible IDE installed for .NET development.

## Import Namespaces
Before writing the code, import the necessary namespaces to access the required classes and methods.
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Step 1: Set Output Folder and File Name
First, define the output folder where the converted PDF file will be saved, and specify the output file name.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "vsdm-converted-to.pdf");
```
## Step 2: Load the Source VSDM File
Next, load the source VSDM file using the GroupDocs.Conversion library.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_VSDM))
{
    // Code for conversion will be inserted here
}
```
## Step 3: Set Conversion Options
Define the conversion options, in this case, we are converting to PDF format.
```csharp
var options = new PdfConvertOptions();
```
## Step 4: Perform the Conversion
Perform the actual conversion from VSDM to PDF format and save the converted PDF file.
```csharp
converter.Convert(outputFile, options);
```
## Step 5: Display Success Message
Finally, notify the user that the conversion process has been completed successfully and provide the path to the output file.
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusion
In this tutorial, we've learned how to convert VSDM files to PDF format using the GroupDocs.Conversion library for .NET. By following the step-by-step guide, you can efficiently perform this conversion process in your .NET applications.
## FAQ's
### Can GroupDocs.Conversion convert other file formats besides VSDM to PDF?
Yes, GroupDocs.Conversion supports conversion between a wide range of file formats including Word, Excel, PowerPoint, and more.
### Is there a trial version available for GroupDocs.Conversion?
Yes, you can get a free trial version from [here](https://releases.groupdocs.com/).
### How can I get support if I encounter any issues during conversion?
You can seek assistance from the GroupDocs.Conversion community forum [here](https://forum.groupdocs.com/c/conversion/11).
### Can I purchase a temporary license for GroupDocs.Conversion?
Yes, you can purchase a temporary license from [here](https://purchase.groupdocs.com/temporary-license/).
### Where can I find the full documentation for GroupDocs.Conversion?
The complete documentation can be found [here](https://tutorials.groupdocs.com/conversion/net/).
