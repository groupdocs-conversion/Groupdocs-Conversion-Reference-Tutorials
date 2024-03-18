---
title: Convert XLAM to PDF
linktitle: Convert XLAM to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 21
url: /net/converting-file-types-to-pdf/convert-xlam-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert XLAM file into PDF format.
    /// For more details about Microsoft Excel Macro-Enabled Add-In (.xlam) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-xlam-to-pdf
    /// </summary>
    internal static class ConvertXlamToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "xlam-converted-to.pdf");
            
            // Load the source XLAM file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_XLAM))
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
