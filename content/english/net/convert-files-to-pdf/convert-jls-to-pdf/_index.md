---
title: Convert JPEG-LS (.JLS) Files to PDF
linktitle: Convert JPEG-LS (.JLS) Files to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 29
url: /net/convert-files-to-pdf/convert-jls-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert JLS file into PDF format.
    /// For more details about JPEG Lossless Image File (.jls) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-jls-to-pdf
    /// </summary>
    internal static class ConvertJlsToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "jls-converted-to.pdf");
            
            // Load the source JLS file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_JLS))
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
