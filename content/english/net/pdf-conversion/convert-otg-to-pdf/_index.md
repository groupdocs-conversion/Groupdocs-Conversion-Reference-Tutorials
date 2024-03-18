---
title: Convert OTG to PDF
linktitle: Convert OTG to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 13
url: /net/pdf-conversion/convert-otg-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert OTG file into PDF format.
    /// For more details about OpenDocument Graphic Template (.otg) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-otg-to-pdf
    /// </summary>
    internal static class ConvertOtgToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "otg-converted-to.pdf");
            
            // Load the source OTG file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_OTG))
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
