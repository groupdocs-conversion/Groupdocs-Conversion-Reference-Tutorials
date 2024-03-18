---
title: Convert CDR Vector Graphics to PDF
linktitle: Convert CDR Vector Graphics to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 12
url: /net/file-conversion-to-pdf/convert-cdr-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert CDR file into PDF format.
    /// For more details about CorelDraw Vector Graphic Drawing (.cdr) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-cdr-to-pdf
    /// </summary>
    internal static class ConvertCdrToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "cdr-converted-to.pdf");
            
            // Load the source CDR file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_CDR))
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
