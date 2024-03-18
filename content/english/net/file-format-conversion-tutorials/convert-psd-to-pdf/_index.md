---
title: Convert PSD to PDF
linktitle: Convert PSD to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 10
url: /net/file-format-conversion-tutorials/convert-psd-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert PSD file into PDF format.
    /// For more details about Adobe Photoshop Document (.psd) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-psd-to-pdf
    /// </summary>
    internal static class ConvertPsdToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "psd-converted-to.pdf");
            
            // Load the source PSD file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PSD))
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
