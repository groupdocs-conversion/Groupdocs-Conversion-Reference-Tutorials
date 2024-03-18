---
title: Convert MPP to PDF
linktitle: Convert MPP to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 23
url: /net/document-conversion/convert-mpp-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert MPP file into PDF format.
    /// For more details about Microsoft Project File (.mpp) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-mpp-to-pdf
    /// </summary>
    internal static class ConvertMppToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "mpp-converted-to.pdf");
            
            // Load the source MPP file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_MPP))
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
