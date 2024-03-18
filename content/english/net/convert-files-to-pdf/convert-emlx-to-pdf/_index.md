---
title: Convert EMLX Apple Mail Email Messages to PDF
linktitle: Convert EMLX Apple Mail Email Messages to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 15
url: /net/convert-files-to-pdf/convert-emlx-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert EMLX file into PDF format.
    /// For more details about Apple Mail Message (.emlx) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-emlx-to-pdf
    /// </summary>
    internal static class ConvertEmlxToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "emlx-converted-to.pdf");
            
            // Load the source EMLX file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_EMLX))
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
