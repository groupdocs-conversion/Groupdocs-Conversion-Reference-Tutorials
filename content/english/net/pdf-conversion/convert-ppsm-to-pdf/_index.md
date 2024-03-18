---
title: Convert PPSM to PDF
linktitle: Convert PPSM to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 24
url: /net/pdf-conversion/convert-ppsm-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert PPSM file into PDF format.
    /// For more details about Microsoft PowerPoint Slide Show (.ppsm) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-ppsm-to-pdf
    /// </summary>
    internal static class ConvertPpsmToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "ppsm-converted-to.pdf");
            
            // Load the source PPSM file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PPSM))
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
