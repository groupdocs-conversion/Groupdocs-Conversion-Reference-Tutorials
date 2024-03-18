---
title: Convert J2C JPEG-LS Compressed Images to PDF
linktitle: Convert J2C JPEG-LS Compressed Images to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 27
url: /net/convert-files-to-pdf/convert-j2c-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert J2C file into PDF format.
    /// For more details about JPEG 2000 Image File (.j2c) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-j2c-to-pdf
    /// </summary>
    internal static class ConvertJ2cToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "j2c-converted-to.pdf");
            
            // Load the source J2C file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_J2C))
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
