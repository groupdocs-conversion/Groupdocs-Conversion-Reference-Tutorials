---
title: Convert DGN CAD Files to PDF
linktitle: Convert DGN CAD Files to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 17
url: /net/file-conversion-to-pdf/convert-dgn-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert DGN file into PDF format.
    /// For more details about MicroStation Design File (.dgn) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-dgn-to-pdf
    /// </summary>
    internal static class ConvertDgnToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "dgn-converted-to.pdf");
            
            // Load the source DGN file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_DGN))
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
