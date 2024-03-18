---
title: Convert FODP OpenDocument Presentations to PDF
linktitle: Convert FODP OpenDocument Presentations to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 19
url: /net/convert-files-to-pdf/convert-fodp-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert FODP file into PDF format.
    /// For more details about OpenDocument Flat XML Presentation (.fodp) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-fodp-to-pdf
    /// </summary>
    internal static class ConvertFodpToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "fodp-converted-to.pdf");
            
            // Load the source FODP file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_FODP))
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
