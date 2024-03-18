---
title: Convert J2K JPEG 2000 Images to PDF
linktitle: Convert J2K JPEG 2000 Images to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 28
url: /net/convert-files-to-pdf/convert-j2k-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert J2K file into PDF format.
    /// For more details about JPEG 2000 Image (.j2k) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-j2k-to-pdf
    /// </summary>
    internal static class ConvertJ2kToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "j2k-converted-to.pdf");
            
            // Load the source J2K file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_J2K))
            {
                var options = new PdfConvertOptions();
                // Save converted PDF file
                converter.Convert(outputFile, options);
            }

            Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
        }
    }
}

```
