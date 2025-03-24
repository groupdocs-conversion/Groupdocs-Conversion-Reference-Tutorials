---
title: Convert CDR Vector Graphics to PDF
linktitle: Convert CDR Vector Graphics to PDF
second_title: GroupDocs.Conversion .NET API
description: Effortlessly convert CorelDRAW (CDR) vector graphics files to PDF format using GroupDocs.Conversion for .NET. Streamline your document conversion process.
weight: 12
url: /net/file-conversion-to-pdf/convert-cdr-to-pdf/
---

# Convert CDR Vector Graphics to PDF

## Introduction
GroupDocs.Conversion for .NET is a powerful document conversion library that allows developers to seamlessly convert various document formats to PDF, Word, HTML, and many more. In this tutorial, we will focus on converting CorelDRAW (CDR) vector graphics files to PDF format using GroupDocs.Conversion for .NET. By the end of this guide, you'll be equipped with the knowledge to effortlessly perform this conversion in your .NET applications.
## Prerequisites
Before we dive into the conversion process, ensure you have the following prerequisites set up:
### Install GroupDocs.Conversion for .NET
To get started, you need to download and install GroupDocs.Conversion for .NET. You can download the library from the [download page](https://releases.groupdocs.com/conversion/net/).
### Obtain a License
To utilize the full potential of GroupDocs.Conversion for .NET, you'll need a valid license. You can obtain a license from [GroupDocs](https://purchase.groupdocs.com/buy) or request a temporary license for testing purposes [here](https://purchase.groupdocs.com/temporary-license/).

## Import Namespaces
Ensure you have imported the necessary namespaces in your .NET project to utilize GroupDocs.Conversion functionalities. Here's how you can do it:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Step 1: Define Output Folder and File Name
First, specify the output folder where the converted PDF file will be saved, along with the desired file name.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "cdr-converted-to.pdf");
```
Make sure to replace `"Your Document Directory"` with the path to your desired output folder.
## Step 2: Load the Source CDR File
Next, load the source CDR file that you want to convert to PDF using GroupDocs.Conversion.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_CDR))
{
    // Conversion logic will go here
}
```
Replace `Constants.SAMPLE_CDR` with the path to your actual CDR file.
## Step 3: Specify Conversion Options
Define the conversion options, such as specifying the output format (PDF) and any additional settings.
```csharp
var options = new PdfConvertOptions();
```
You can customize conversion options according to your requirements.
## Step 4: Perform the Conversion
Execute the conversion process with the specified options.
```csharp
converter.Convert(outputFile, options);
```
This command will convert the CDR file to PDF and save it to the specified output folder with the provided file name.
## Step 5: Confirm Conversion Completion
Lastly, display a message confirming the successful completion of the conversion process.
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```
This message will inform you about the location where the converted PDF file is saved.

## Conclusion
In this tutorial, we've learned how to convert CorelDRAW (CDR) vector graphics files to PDF format using GroupDocs.Conversion for .NET. By following the outlined steps, you can seamlessly integrate document conversion capabilities into your .NET applications, enhancing their functionality and usability.
## FAQ's
### Is GroupDocs.Conversion for .NET compatible with all versions of CorelDRAW files?
GroupDocs.Conversion for .NET supports a wide range of CorelDRAW versions, ensuring compatibility with most CDR files.
### Can I convert multiple CDR files simultaneously using GroupDocs.Conversion for .NET?
Yes, you can batch convert multiple CDR files to PDF or other formats using GroupDocs.Conversion for .NET, improving efficiency and productivity.
### Does GroupDocs.Conversion for .NET require an internet connection for document conversion?
No, GroupDocs.Conversion for .NET performs document conversion locally on your machine, eliminating the need for an internet connection during the conversion process.
### Can I customize the conversion settings according to my specific requirements?
Yes, GroupDocs.Conversion for .NET provides extensive customization options, allowing you to tailor the conversion process to meet your exact needs.
### Is technical support available for GroupDocs.Conversion for .NET?
Yes, GroupDocs offers comprehensive technical support for its products, including GroupDocs.Conversion for .NET. You can seek assistance from the [support forum](https://forum.groupdocs.com/c/conversion/11) for any queries or issues.
