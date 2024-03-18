---
title: Convert OTT to PDF
linktitle: Convert OTT to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 16
url: /net/pdf-conversion/convert-ott-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert OTT file into PDF format.
    /// For more details about Open Document Template (.ott) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-ott-to-pdf
    /// </summary>
    internal static class ConvertOttToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "ott-converted-to.pdf");
            
            // Load the source OTT file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_OTT))
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
