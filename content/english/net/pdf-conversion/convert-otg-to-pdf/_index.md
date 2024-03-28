---
title: Convert OTG to PDF
linktitle: Convert OTG to PDF
second_title: GroupDocs.Conversion .NET API
description: Learn how to convert OTG files to PDF using GroupDocs.Conversion for .NET. Simple, efficient, and seamless integration for your projects.
type: docs
weight: 13
url: /net/pdf-conversion/convert-otg-to-pdf/
---
## Introduction
Converting OTG (OpenDocument Graphics) files to PDF format can be a crucial task, especially when dealing with document management systems or sharing files across different platforms. In this tutorial, we'll guide you through the process of converting OTG files to PDF using the GroupDocs.Conversion library for .NET. Let's dive in!
## Prerequisites
Before we begin, ensure you have the following prerequisites:
1. GroupDocs.Conversion for .NET: Make sure you have installed the GroupDocs.Conversion library for .NET. You can download it from [here](https://releases.groupdocs.com/conversion/net/).
2. OTG File: Have the OTG file that you want to convert to PDF ready in your document directory.

## Import Namespaces
First, you need to import the necessary namespaces to your .NET project. 
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Step 1: Set Output Directory and File Name
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "otg-converted-to.pdf");
```
In this step, you define the output directory where the converted PDF file will be saved. Replace `"Your Document Directory"` with the path to your desired output directory.
## Step 2: Load the Source OTG File and Convert to PDF
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_OTG))
{
    var options = new PdfConvertOptions();
    // Save converted PDF file
    converter.Convert(outputFile, options);
}
```
Here, we instantiate a new `Converter` object from GroupDocs.Conversion library, passing the path of the source OTG file. Then, we create `PdfConvertOptions` to specify conversion options. Finally, we call the `Convert` method to convert the OTG file to PDF format.
## Step 3: Check Conversion Completion
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
This step notifies the user that the conversion process is completed successfully and provides the path where the converted PDF file is saved.

## Conclusion
Converting OTG files to PDF format is made simple with the GroupDocs.Conversion library for .NET. By following the steps outlined in this tutorial, you can seamlessly integrate this functionality into your .NET applications, enhancing document interoperability and accessibility.
## FAQ's
### Can GroupDocs.Conversion convert other file formats apart from OTG to PDF?
Yes, GroupDocs.Conversion supports a wide range of file formats for conversion, including DOCX, XLSX, PPTX, HTML, and more.
### Is GroupDocs.Conversion suitable for commercial use?
Absolutely! GroupDocs.Conversion offers commercial licenses for businesses and organizations looking to leverage its powerful document conversion capabilities.
### Does GroupDocs.Conversion provide technical support?
Yes, GroupDocs offers dedicated technical support to assist users with any queries or issues they may encounter during implementation.
### Can I try GroupDocs.Conversion before purchasing a license?
Yes, you can avail of a free trial of GroupDocs.Conversion to explore its features and compatibility with your requirements.
### How can I obtain a temporary license for GroupDocs.Conversion?
You can obtain a temporary license from GroupDocs for evaluation purposes or short-term projects by visiting the temporary [license](https://purchase.groupdocs.com/temporary-license/).
